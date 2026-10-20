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
| Member 1: Alexander | What software supply-chain security is | Research notes + intro | Slide 1 |
| Member 2: Cesar | How npm/GitHub attacks work | Attack-flow research + diagram | Slide 2 |
| Member 3: Gustavo | GitHub/npm response in 2026 | Security-response research | Slide 3 |
| Member 4: Jake | Developer impact + prevention | Conclusion + final review | Slide 4 |

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

**Course:** CEP146  
**Project type:** Group presentation  
**Repository:** [CEP146-Group-presentation](https://github.com/lksloocky/CEP146-Group-presentation)

## Overview

This project explores how software supply-chain attacks threaten modern software development, particularly through compromised open-source dependencies, malicious npm packages, stolen credentials, and vulnerable GitHub Actions workflows.

The project examines how these attacks happen, how GitHub and npm are responding to emerging threats, and what developers can do to protect their applications and development environments.

Our central message is:

> Secure the chain, not just the app.

## Objectives

- Explain what a software supply chain is and why it matters.
- Describe how attackers compromise packages, credentials, repositories, and CI/CD pipelines.
- Investigate security protections introduced by GitHub and npm in 2026.
- Present practical recommendations for reducing software supply-chain risks.
- Demonstrate collaborative software development using GitHub branches, commits, issues, and pull requests.

## Presentation Structure

The presentation is organized into four sections.

| Section | Topic | Research Focus |
|---|---|---|
| 1 | Understanding the Software Supply Chain | Dependencies, open-source packages, repositories, and CI/CD |
| 2 | How Supply-Chain Attacks Work | Credential theft, malicious packages, compromised workflows, and attack propagation |
| 3 | GitHub and npm Security Responses | Malware scanning, workflow protections, and safer checkout behavior |
| 4 | Developer Impact and Prevention | Dependency management, secret protection, least privilege, and security practices |

## Team Responsibilities

| Team Member | Responsibility | Presentation Section |
|---|---|---|
| Alex | Background research and definitions | 1 |
| Cesar | Attack research and attack-flow diagram | 2 |
| Gustavo | Research into GitHub and npm security responses | 3 |
| Jake | Developer impact, recommendations, and final review | 4 |

## Repository Structure

```text
CEP146-Group-presentation/
├── README.md
├── projectGuidelines.md
├── LICENSE
└── research/
    ├── software-supply-chain-background.md
    ├── how-attacks-work.md
    ├── github-security-response.md
    └── developer-impact.md
```

The research directory is the planned location for the team's individual research documents. Files should be added as the corresponding work is completed.

## Branch Strategy

The project uses separate branches to organize research and support parallel collaboration.

| Branch | Purpose |
|---|---|
| `main` | Integrate reviewed work and maintain the final project documentation |
| `research-background` | Research software supply-chain concepts and dependencies |
| `research-attack-flow` | Document attack techniques and illustrate the attack chain |
| `research-security-response` | Investigate GitHub and npm security measures |
| `research/developer-impact` | Document developer impact and prevention recommendations |

Branch names in this table describe the intended workflow and should be checked against the branches currently published on GitHub.

## Collaboration Workflow

Each team member should:

1. Review the assigned research question and create or update a GitHub issue.
2. Work in the appropriate research branch.
3. Add research notes and cite reliable sources.
4. Commit changes with clear, descriptive messages.
5. Push the branch to GitHub and open a pull request.
6. Request a review from another team member.
7. Address feedback and merge approved changes into `main`.

The `main` branch should contain the integrated and reviewed version of the project.

## Security Topics

The research focuses on five connected areas:

- **Dependency security:** Review third-party packages and remove unnecessary dependencies.
- **Credential security:** Protect tokens, API keys, and developer accounts.
- **Repository security:** Review changes and restrict access appropriately.
- **CI/CD security:** Limit workflow permissions and inspect automated execution.
- **Developer practices:** Enable multifactor authentication, monitor security alerts, and keep dependencies and workflows updated.

## Deliverables

- [x] Research notes for all four presentation sections.
- [x] Presentation script and supporting visual materials.
- [x] Credible sources supporting the main claims.
- [x] Public YouTube video within the required 2:30–3:00 duration.
- [x] Final video link added to this README.
- [x] Evidence of collaboration through issues, commits, branches, and pull requests.

### Final Presentation

**YouTube video:** _Link to be added._

## Project Guidelines

See [projectGuidelines.md](projectGuidelines.md) for the assignment requirements, deliverables, and grading rubric.

## License

See [LICENSE](LICENSE) for the licensing terms applicable to this repository.

## Final Video
[![Video 2](https://img.youtube.com/vi/vLQOG6sRsyY/0.jpg)](https://www.youtube.com/watch?v=vLQOG6sRsyY)
