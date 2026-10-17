
# GitHub and npm Security Response in 2026

GitHub and npm introduced several security measures in 2026 to reduce the risk of software supply-chain attacks. These changes focus on preventing malicious packages from reaching developers, stopping suspicious GitHub Actions workflows before execution, and reducing the risks of running untrusted pull-request code with privileged access.

## 1. npm Malware Scanning

In July 2026, npm introduced publish-time malware scanning to help prevent malicious packages from reaching users.

Newly published packages can be scanned before they become available for installation. Depending on the scan results, suspicious packages may be held for additional review or blocked.

### How It Works

```
Package Published
       |
       v
  Malware Scan
    /       \
 Safe     Suspicious
  |           |
  v           v
Available   Review / Block
````

### Key Benefits

- Early detection: Packages are scanned before they become available for installation.
- Reduced exposure: Suspicious packages can be held for review or blocked.
- Supply-chain protection: The scanning process helps reduce the risk of malicious dependencies reaching developers and automated build systems.

Publish-time scanning adds an important preventive security layer, although it cannot guarantee that every malicious package will be detected.

## 2. GitHub Actions Workflow Protection

In July 2026, GitHub introduced protections that can hold certain potentially malicious GitHub Actions workflow runs for human approval before execution.

This measure helps address attacks in which compromised accounts or unauthorized workflow changes are used to steal credentials, access secrets, or compromise CI/CD infrastructure.

### How It Works

```
Workflow Triggered
        |
        v
   Suspicious?
    /      \
   No      Yes
   |        |
   v        v
  Run      Hold
             |
             v
           Review
             |
             v
      Approve or Reject
```

### Key Benefits

- Human approval: Suspicious workflow runs can be reviewed before execution.
- Reduced risk: Attackers have a harder time immediately running malicious workflows.
- Credential protection: The approval checkpoint can help prevent unauthorized access to repository secrets and CI/CD resources.

This protection adds a human review step when a workflow is flagged as potentially malicious.

## 3. Safer `pull_request_target` and `actions/checkout`

In June 2026, GitHub introduced safer default behavior for `actions/checkout` to reduce the risk of executing untrusted pull-request code in privileged GitHub Actions workflows.

### Why Is `pull_request_target` Dangerous?

The `pull_request_target` event allows workflows to access the base repository's security context, including its permissions, tokens, and potentially available secrets.

This becomes dangerous when a workflow checks out and executes untrusted code submitted through a pull request, especially from a fork.

For example, an attacker could submit a pull request containing a malicious build script. If a privileged workflow executes that script, the code may gain access to credentials or other resources available to the workflow.

This attack pattern is commonly known as a pwn request.

### Vulnerable Workflow Pattern

```
Pull Request from a Fork
          |
          v
Privileged GitHub Actions Workflow
          |
          v
Checkout Untrusted Code
          |
          v
Execute Malicious Code
          |
          v
Potential Credential Theft
or Repository Compromise
```

### What Changed?

GitHub strengthened `actions/checkout` defaults to refuse common unsafe checkout patterns involving fork pull-request code in privileged workflows.

The protection also applies to certain `workflow_run` workflows originating from pull-request events.

### Safer Workflow Pattern

```
Pull Request from a Fork
          |
          v
Privileged Workflow
          |
          v
Checkout Safety Checks
          |
     +----+----+
     |         |
   Safe      Unsafe
     |         |
     v         v
  Proceed    Refuse
```

### Key Benefits

- Safer defaults: Common unsafe checkout patterns are blocked by default.
- Reduced credential exposure: Untrusted code is less likely to execute with privileged repository access.
- Defense in depth: Developers receive additional protection even if a workflow contains an unsafe checkout configuration.

These changes do not eliminate every possible way to execute untrusted code. Developers should still avoid unnecessary privileged triggers and should never execute untrusted code with secrets or elevated permissions.

## Conclusion

GitHub and npm's 2026 security improvements address three important stages of the software supply chain.

| Security Measure | Main Risk | Protection |
| --- | --- | --- |
| npm malware scanning | Malicious packages reaching developers | Scan packages before installation availability |
| GitHub Actions workflow protection | Suspicious workflows executing automatically | Hold flagged runs for human approval |
| Safer `pull_request_target` defaults | Untrusted code executing with elevated privileges | Block common unsafe checkout patterns |

Together, these measures demonstrate how development platforms are integrating security controls directly into software publishing, CI/CD execution, and code review.

By introducing preventive checks at these stages, GitHub and npm help reduce the opportunity for attackers to distribute malware, abuse automation credentials, and compromise software development environments.

## References

- GitHub Blog: [npm publish-time malware scanning and dual-use metadata](<https://github.blog/changelog/2026-07-28-npm-publish-time-malware-scanning-and-dual-use-metadata/?utm_source=chatgpt.com>)
- GitHub Blog: [GitHub Actions holds potentially malicious workflows for approval](<https://github.blog/changelog/2026-07-28-github-actions-holds-potentially-malicious-workflows-for-approval/?utm_source=chatgpt.com>)
- GitHub Blog: [Safer `pull_request_target` defaults for GitHub Actions checkout](<https://github.blog/changelog/2026-06-18-safer-pull_request_target-defaults-for-github-actions-checkout/?utm_source=chatgpt.com>)
- GitHub Docs: [Securely using `pull_request_target`](<https://docs.github.com/en/actions/reference/security/securely-using-pull_request_target?utm_source=chatgpt.com>)
- GitHub Blog: [Disrupting supply chain attacks on npm and GitHub Actions](<https://github.blog/security/supply-chain-security/disrupting-supply-chain-attacks-on-npm-and-github-actions/?utm_source=chatgpt.com>)

```

```
