# Securing the Software Supply Chain: npm and GitHub Actions Attacks in 2026

## Software Development Current Event Project

This repository contains the research, planning, script, presentation materials, and collaboration history for our Software Development Current Event project.

## Team Members

| Team Member | Student Number | Primary Role |
|---|---|---|
| [NAME 1] | [STUDENT NUMBER] | Research: supply-chain attacks |
| [NAME 2] | [STUDENT NUMBER] | Research: GitHub/npm security response |
| [NAME 3] | [STUDENT NUMBER] | Script and presentation structure |
| [NAME 4] | [STUDENT NUMBER] | Slides, media, and video editing |

> Roles represent each member's primary responsibility. All team members participate in research, reviews, pull requests, and project discussions.

---

## Topic

### Software Supply-Chain Attacks on npm and GitHub Actions

Modern software applications depend on more than the code written directly by developers. They also rely on open-source packages, repositories, automated builds, CI/CD pipelines, and third-party development tools.

Recent software supply-chain attacks have targeted package repositories and CI/CD systems to distribute malicious code and steal developer credentials. During 2026, GitHub and npm introduced several security changes designed to reduce these risks.

Our project examines how these attacks work, why they matter to software developers, and how platforms such as GitHub and npm are responding.

---

## Research Question

**How are recent software supply-chain attacks changing the way developers use npm, GitHub Actions, and open-source dependencies?**

---

## Main Argument

Software security is no longer limited to protecting the final application.

Because modern applications depend on third-party packages, automated workflows, repositories, credentials, and CI/CD systems, developers must also protect the software-development process itself.

---

## Current Event

During 2026, GitHub introduced multiple changes designed to reduce software supply-chain attacks.

Examples include:

- automatic npm malware scanning before newly published packages become available for installation;
- GitHub Actions protections that can hold potentially malicious workflow runs for review;
- safer defaults for `actions/checkout`;
- additional protections against unsafe use of `pull_request_target`;
- stronger controls around workflow execution and credentials.

These changes demonstrate how software-development platforms are adapting to attacks that target the tools developers use to build software.

---

## Why This Topic Matters

Developers frequently use:

- open-source dependencies;
- npm and other package managers;
- GitHub repositories;
- automated testing;
- CI/CD pipelines;
- GitHub Actions;
- API keys and access tokens.

A vulnerability or compromised account somewhere in this chain can affect projects that did not contain an original security vulnerability themselves.

This makes software supply-chain security an important part of modern software engineering.

---

## Simplified Attack Flow

```text
Attacker
   |
   v
Compromises developer or maintainer credentials
   |
   v
Modifies package or automated workflow
   |
   v
Malicious code enters software supply chain
   |
   v
Developer installs package or workflow executes
   |
   v
Credentials / tokens / secrets may be stolen
   |
   v
Attack can spread to additional repositories
```

---

## Presentation

**Format:** Pre-recorded YouTube presentation

**Required Length:** 2:30-3:00 minutes

**YouTube Video:**  
[PUBLIC YOUTUBE LINK WILL BE ADDED HERE]

---

## Repository Structure

```text
software-supply-chain-project/
|
|-- README.md
|
|-- research/
|   |-- research-notes.md
|   |-- sources.md
|   `-- terminology.md
|
|-- script/
|   |-- draft-script.md
|   `-- final-script.md
|
|-- slides/
|   |-- slide-outline.md
|   |-- presentation.pptx
|   `-- presentation.pdf
|
|-- media/
|   |-- diagrams/
|   `-- screenshots/
|
|-- project/
|   `-- collaboration-plan.md
|
`-- video/
    `-- youtube-link.md
```

---

## Team Contributions

### [NAME 1]

Primary responsibilities:

- researched recent software supply-chain attacks;
- documented attack techniques;
- contributed research notes and sources;
- reviewed team pull requests.

### [NAME 2]

Primary responsibilities:

- researched GitHub and npm security changes;
- verified technical information;
- contributed security-response research;
- reviewed team pull requests.

### [NAME 3]

Primary responsibilities:

- organized the presentation structure;
- prepared and edited the video script;
- checked presentation timing;
- reviewed research for clarity.

### [NAME 4]

Primary responsibilities:

- designed presentation slides and diagrams;
- organized media assets;
- edited the final video;
- coordinated publication to YouTube.

---

## GitHub Collaboration

Our team uses GitHub as a collaboration platform rather than only as file storage.

The project includes:

- GitHub Issues for task planning;
- separate branches for project tasks;
- regular descriptive commits;
- Pull Requests before merging into `main`;
- peer reviews and comments;
- GitHub Discussions for project decisions and feedback.

Typical workflow:

```text
Issue
  |
  v
Branch
  |
  v
Commits
  |
  v
Pull Request
  |
  v
Peer Review
  |
  v
Revision if required
  |
  v
Merge into main
  |
  v
Issue Closed
```

---

## Sources

Research for this project uses sources including:

1. GitHub Blog - *Disrupting supply chain attacks on npm and GitHub Actions*, July 28, 2026.
2. GitHub Changelog - *npm publish-time malware scanning and dual-use metadata*, July 28, 2026.
3. GitHub Changelog - *GitHub Actions holds potentially malicious workflows for approval*, July 28, 2026.
4. GitHub Changelog - *Safer pull_request_target defaults for GitHub Actions checkout*, June 18, 2026.
5. OWASP - *Software Supply Chain Security Cheat Sheet*.
6. NIST - *Strategies for the Integration of Software Supply Chain Security in DevSecOps CI/CD Pipelines*, SP 800-204D.

Complete research notes and source information are available in the `research/` directory.

---

## Project Status

- [ ] Topic approved
- [ ] Research completed
- [ ] Sources reviewed
- [ ] Presentation outline completed
- [ ] Script drafted
- [ ] Script peer-reviewed
- [ ] Slides completed
- [ ] Presentation recorded
- [ ] Video edited
- [ ] YouTube video uploaded publicly
- [ ] YouTube link added to README
- [ ] Final repository review completed
