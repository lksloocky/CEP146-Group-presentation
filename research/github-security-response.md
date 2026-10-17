# GitHub and npm Security Response in 2026

In 2026, GitHub and npm introduced several security measures to reduce software supply-chain attacks. The changes focus on three critical stages: preventing malicious packages from reaching developers, stopping suspicious CI/CD workflows before they execute, and preventing untrusted pull-request code from running with privileged access.

The GitHub Blog

+3

## 1. npm malware scanning

Announced July 28, 2026

npm introduced automatic malware scanning at publish time. Newly published packages are scanned before they become available for installation, allowing npm to identify suspicious content before it reaches downstream users.

GitHub Changelog

Package published

Automatic malware scan

Safe

Package becomes available for installation.

Suspicious

Package may be held for review or blocked.

Conceptual workflow based on npm's published policy.

### How it works

- Scan before availability: A newly published package is checked before users can install that version.
- Review or block: Depending on the findings, a package may proceed normally, be held for manual review, or be blocked.
- Short publication delay: Most packages experience a delay of around five minutes, although scanning can take 15 minutes or longer during peak periods or for larger packages.
- Additional safeguards for dual-use software: Maintainers of packages with security-sensitive capabilities that could resemble malware must declare the relevant functionality through `contentPolicy` metadata and provide a `DISCLOSURE` file. Additional publishing requirements apply to these packages.
  GitHub Changelog

Why it matters: Previously, a malicious package could become installable as soon as it was published. Publish-time scanning introduces a preventive checkpoint, reducing the opportunity for malware to spread to developers and automated build systems. However, scanning only blocks malware that the detection systems can identify; it is not a guarantee that every published package is safe.

## 2. GitHub Actions workflow protection

Announced July 28, 2026

GitHub introduced automatic protections that hold certain potentially malicious GitHub Actions workflow runs for human approval before execution. The measure responds to supply-chain attacks in which attackers compromise GitHub credentials and introduce malicious workflows to steal CI/CD credentials or launch further attacks.

GitHub Changelog

+1

### How the protection works

Workflow run triggered

Does the run appear potentially malicious?

No

Workflow runs normally.

Yes

Execution is held pending approval.

Human review

A repository collaborator with write access reviews and approves the run through an authenticated web session.

Approval is required only for runs flagged by the protection.

### Key details

- Automatic protection: Repository owners do not need to configure this feature separately.
- Execution is paused: A flagged workflow cannot run until an authorized collaborator approves it.
- Scope: The protection applies to public repositories on GitHub.com. It was not added to GitHub Enterprise Server by this announcement.
- Security benefit: A compromised account is less able to immediately execute a malicious workflow and extract credentials without a human review step.
  GitHub Changelog

Why it matters: GitHub Actions workflows can access repository tokens, secrets, and build infrastructure. Pausing suspicious runs creates an opportunity to identify unauthorized changes before they cause damage.

## 3\. Safer `pull_request_target` and `actions/checkout`

Announced June 18, 2026

GitHub also strengthened the default behavior of `actions/checkout` to reduce the risk of executing untrusted pull-request code inside privileged GitHub Actions workflows. Version 7 introduced the protection, with enforcement subsequently backported to supported versions other than version 1.

GitHub Changelog

+1

### Why `pull_request_target` can be dangerous

The `pull_request_target` event is designed for workflows that need trusted repository access when responding to pull requests, including pull requests from forks. Unlike the standard `pull_request` event, it runs with the base repository's trust level and can access its `GITHUB_TOKEN`, repository or organization secrets, and default-branch cache scope.

GitHub Docs

The danger arises when a workflow checks out untrusted code from a contributor's fork and then executes that code.

For example, an attacker could submit a pull request containing a malicious build script. If a privileged workflow checks out that script and runs a build or test command, the attacker's code may execute with the workflow's credentials. This attack pattern is known as a “pwn request.”

### The vulnerable pattern

Pull request from a fork

Privileged `pull_request_target` workflow

Untrusted code is executed

Potential exposure of repository secrets, tokens, or other privileged resources.

### What changed in June 2026?

GitHub made `actions/checkout` refuse common unsafe patterns by default when a workflow triggered by `pull_request_target` attempts to check out a fork's pull-request code. The protection also covers `workflow_run` workflows when the originating event is a pull-request event.

Examples of unsafe inputs include checking out the pull request's head or merge commit, or explicitly selecting the fork's repository.

GitHub Changelog

+1

The safer behavior can be summarized as follows:

| Workflow situation | Expected behavior |
| --- | --- |
| Trusted default-branch code | Continues to work normally. |
| Fork pull-request code checked out through a protected privileged workflow | Checkout is refused by default. |
| Workflow genuinely needs unsafe checkout behavior | An explicit `allow-unsafe-pr-checkout: true` opt-out is available after reviewing the risks. |

The change does not eliminate every possible route for executing untrusted code. Workflows can still introduce risk by fetching code through other commands or executing untrusted artifacts. GitHub therefore recommends avoiding privileged triggers when they are unnecessary and never executing untrusted code with secrets or elevated tokens.

GitHub Changelog

+1

Why it matters: The protection changes the default from relying entirely on developers to recognize a dangerous configuration to blocking a common vulnerable pattern automatically. It helps prevent a malicious contribution from turning a routine CI task into a compromise of the repository.

## Conclusion

GitHub and npm's 2026 changes address three distinct points in the software supply chain:

| Security measure | Main risk addressed | Preventive control |
| --- | --- | --- |
| npm publish-time scanning | Malicious packages reaching users | Scan packages before installation availability |
| GitHub Actions workflow approval | Compromised accounts launching malicious workflows | Hold suspicious runs for human approval |
| Safer `actions/checkout` defaults | Untrusted pull-request code executing with elevated privileges | Refuse common unsafe fork checkouts by default |

Together, these measures demonstrate a shift toward security controls built directly into development platforms and workflows. Rather than relying exclusively on developers to detect threats after they appear, npm and GitHub add checkpoints that can interrupt attacks before malicious packages become available, workflows execute, or untrusted code gains access to privileged resources.

### Primary sources

1. GitHub — [npm publish-time malware scanning and dual-use metadata](<https://github.blog/changelog/2026-07-28-npm-publish-time-malware-scanning-and-dual-use-metadata/?utm_source=chatgpt.com>).
2. GitHub — [GitHub Actions holds potentially malicious workflows for approval](<https://github.blog/changelog/2026-07-28-github-actions-holds-potentially-malicious-workflows-for-approval/?utm_source=chatgpt.com>).
3. GitHub — [Safer `pull_request_target` defaults for GitHub Actions checkout](<https://github.blog/changelog/2026-06-18-safer-pull_request_target-defaults-for-github-actions-checkout/?utm_source=chatgpt.com>).
4. GitHub Docs — [Securely using `pull_request_target`](<https://docs.github.com/en/actions/reference/security/securely-using-pull_request_target?utm_source=chatgpt.com>).
5. GitHub — [Disrupting supply chain attacks on npm and GitHub Actions](<https://github.blog/security/supply-chain-security/disrupting-supply-chain-attacks-on-npm-and-github-actions/?utm_source=chatgpt.com>).
