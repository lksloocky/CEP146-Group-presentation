## Shorter project version
Topic
# When Trusted Code Turns Dangerous: Software Supply-Chain Attacks in 2026
The project focuses on one simple question:
How are recent software supply-chain attacks changing the way developers use npm, GitHub Actions, and open-source dependencies?

GitHub reported in July 2026 that recent supply-chain attacks have targeted package repositories and CI/CD systems to steal credentials and spread malware. The GitHub Blog GitHub and npm have since introduced protections including publish-time npm malware scanning, approval holds for certain suspicious Actions workflows, and safer pull_request_target checkout behavior. The GitHub Blog
4-slide presentation
1. When trusted code turns dangerous
   Introduce software supply-chain security and why dependencies matter.
2. How the attack spreads
   stolen credential → malicious package/workflow → execution → stolen secrets → more repositories
3. GitHub and npm changed the defaults
   npm scanning, suspicious-workflow approval, safer GitHub Actions checkout.
4. Secure the chain, not just the app
   Protect dependencies, credentials, and CI/CD automation.

   ---
## 2-minute video idea: “Break the Chain”
0:00–0:08
Show a terminal typing:
npm install trusted-package

Then flash:
> TRUST?

0:08–0:28: Speaker 1 introduces the problem.
0:28–0:59: Speaker 2 explains the five-step attack chain.
0:59–1:31: Speaker 3 explains the 2026 GitHub/npm response.
1:31–1:55: Speaker 4 gives the developer takeaway.
1:55–2:00: Finish with:
**Secure the chain, not just the app.**

----
# Project topic per member
| Member | Main research area | Main GitHub task | Video section |
|---|---|---|---|
| Member 1 | What software supply-chain security is | Research notes + intro | Slide 1 |
| Member 2 | How npm/GitHub attacks work | Attack-flow research + diagram | Slide 2 |
| Member 3 | GitHub/npm response in 2026 | Security-response research | Slide 3 |
| Member 4 | Developer impact + prevention | Conclusion + final review | Slide 4 |

---
## Member 1: Background and definition
### Research question:
What is a software supply chain, and why is it important to developers?
Research:
- What a software supply chain is
- Dependencies and third-party libraries
- npm packages
- GitHub repositories
- CI/CD pipelines
- GitHub Actions
- Why modern applications depend on code developers did not write themselves
- Why this creates security risks
  
A useful concept to explain:

```
Developer's Code
      +
Dependencies
      +
Repository
      +
CI/CD Tools
      =
Final Application
```

### Create:
- branch: research-background
- file: `research/software-supply-chain-background.md`

### commits ideas:
- Add software supply-chain definition
- Add notes about dependencies and CI/CD
- Add background research sources

### Content ideas
# What Is a Software Supply Chain?

A software supply chain includes the code, libraries, tools,
services, and automated systems used to build and deliver software.

Modern developers rarely write every component of an application
themselves. They often depend on open-source libraries, packages,
GitHub repositories, build tools, and CI/CD services.

For example, a JavaScript application may use npm packages created
and maintained by other developers.

This makes software development faster, but it also creates a chain
of trust. If one component in that chain is compromised, the final
application may also be affected.

Software supply-chain security therefore focuses on protecting not
only an application's source code, but also the tools and
dependencies used to create it.

### Presentation main idea:
Modern applications are not built only from the code developers write. They also depend on packages, repositories, and automated development tools.

---
## Member 2: How the attacks work
### Research question:
How can attackers use npm packages or GitHub workflows to compromise software projects?
Research:
- Compromised developer or maintainer accounts
- Stolen authentication credentials
- Malicious package updates
- Malicious npm packages
- Repository access tokens
- GitHub Actions workflows
- How attacks can spread between repositories
- Why CI/CD systems are valuable targets
The attack flow can be simplified to:
```
Attacker
   ↓
Steals credentials
   ↓
Compromises package/workflow
   ↓
Developer or CI/CD executes it
   ↓
Tokens / secrets stolen
   ↓
Attack spreads
```

### Content ideas
# How Software Supply-Chain Attacks Work

Instead of attacking the final application directly, an attacker
may target one of the tools or dependencies used to build it.

One possible attack begins when an attacker steals credentials
belonging to a package maintainer or developer.

The attacker may then gain access to a repository, package
publishing account, or CI/CD system.

If a malicious version of a trusted package is published, developers
may install it believing it is legitimate.

The malicious code may then attempt to steal additional credentials,
API keys, or repository tokens.

Those credentials can potentially be used to compromise additional
projects.

#### A simplified attack chain is:

```
Attacker -> Stolen Credentials -> Malicious Package or Workflow
-> Execution -> Stolen Secrets -> Additional Compromise
```
### Create:
- file: research/how-attacks-work.md
- branch: research-attack-flow

### Commit ideas
- Document supply-chain attack process
- Add credential theft research
- Add attack-flow diagram

---
## Member 3: GitHub and npm response in 2026
### This is probably the most important current-event section.
Research question:
What did GitHub and npm change in 2026 in response to software supply-chain attacks?
Research these three areas:
1. npm malware scanning
GitHub announced in July 2026 that newly published npm packages can be scanned before they become available for installation.

The process can be represented as:
```
Package Published
       ↓
Malware Scan
    /       \
 Safe     Suspicious
  ↓           ↓
Available   Review / Block
```

2. Suspicious GitHub Actions workflows
GitHub introduced protections that can hold certain potentially malicious workflows for human approval before execution.
```
Workflow
    ↓
Suspicious?
   /    \
 No     Yes
 ↓       ↓
Run     Hold
         ↓
      Review
```
3. Safer pull_request_target
Research why running untrusted code through privileged GitHub Actions workflows can be dangerous.
GitHub introduced safer actions/checkout behavior in June 2026 to reduce this attack pattern.
Content to produce

### Content ideas
**GitHub and npm Security Response in 2026**

GitHub introduced several changes during 2026 to reduce the risk of
software supply-chain attacks.

- npm Malware Scanning:
   - In July 2026, npm introduced publish-time malware scanning.
   - Newly published packages can be scanned before they become available
     for users to install.
   - Suspicious packages may be held for additional review or blocked.

- GitHub Actions Workflow Protection
   - GitHub also introduced protections that can hold potentially
   malicious workflow runs before they execute.
   - A repository collaborator with the appropriate permissions can
   review the workflow before deciding whether it should run.

- Safer GitHub Actions Defaults
   - GitHub also introduced safer behavior for workflows using
   pull_request_target and actions/checkout.
   - This reduces the risk of running untrusted pull-request code with
   privileged repository access.
   - These changes demonstrate how development platforms are adding
   security controls directly into the software-development process.


### Create:
- file: research/github-security-response.md
- Branch: research-security-response

### Commit ideas
- Add npm malware scanning research
- Document GitHub Actions workflow protection
- Add pull_request_target security notes

---
## Member 4: Developer impact and prevention
Research question:
What should software developers learn from these attacks?
Research:
- Why developers should care
- Dependency management
- Multi-factor authentication
- Protecting tokens and secrets
- Least privilege
- Reviewing dependencies
- Reviewing pull requests
- Workflow permissions
- Keeping GitHub Actions updated
- Monitoring automated builds
- Removing unused dependencies

The key argument should be:
Modern Software Security
=
```
Application Security
+
Dependency Security
+
Credential Security
+
Repository Security
+
CI/CD Security
```

## Create:
- file: research/developer-impact.md
- Branch: research/developer-impact
---
Member 4: Developer impact and prevention
Research question:
What should software developers learn from these attacks?
Research:
- Why developers should care
- Dependency management
- Multi-factor authentication
- Protecting tokens and secrets
- Least privilege
- Reviewing dependencies
- Reviewing pull requests
- Workflow permissions
- Keeping GitHub Actions updated
- Monitoring automated builds
- Removing unused dependencies

The key argument should be:
Modern Software Security
=
```
Application Security
+
Dependency Security
+
Credential Security
+
Repository Security
+
CI/CD Security
```

## Content ideas
# Impact on Software Developers

- Software supply-chain attacks show that developers must protect more
than the source code they write.

- A secure application can still become compromised if one of its
dependencies, development tools, credentials, or automated workflows
is compromised.

Developers can reduce these risks by:

- reviewing third-party dependencies;
- removing unnecessary packages;
- enabling multi-factor authentication;
- protecting API keys and access tokens;
- limiting GitHub Actions permissions;
- reviewing pull requests carefully;
- keeping workflows and dependencies updated;
- monitoring automated builds and security alerts.

The important lesson is that software security now includes the
entire development process.

Developers must secure the chain that creates the application, not
only the application itself.

### Additional responsibility
Member 4 could also be responsible for:
- checking the final video is under the required time;
- proofreading slides;
- verifying sources;
- adding the YouTube link to README.md.

### Create:
-branch: developer-impact-and-conclusion
- file: research/impact-and-conclusion.md

### Suggested issue:
Research developer impact and security recommendations

### Commit ideas:
- Add developer security recommendations
- Wrie project conclusion
- Review final script for clarity and timing

---

## Presentation section
About 20–25 seconds.
This member handles Slide 4 and the conclusion:
Securing the final application is no longer enough. Developers must also secure the software supply chain that creates it.

We have to create an issue for each member
- Issue #1 → Member 1 → research-background
- Issue #2 → Member 2 → research-attack-flow
- Issue #3 → Member 3 → research-security-response
- Issue #4 → Member 4 → developer-impact

Then each person:
```
Research
   ↓
Commit notes
   ↓
Push branch
   ↓
Open Pull Request
   ↓
Another member reviews
   ↓
Make changes if required
   ↓
Merge to main
```
