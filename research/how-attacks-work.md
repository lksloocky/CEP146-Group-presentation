# How Attackers Compromise Software Projects

Attackers can compromise a software project by stealing a developer’s or package maintainer’s credentials and using that access to modify trusted npm packages, repository code, or automated GitHub workflows. 
When developers install the affected package, or when GitHub Actions executes the altered workflow, malicious code may steal additional tokens, secrets, and API keys. Those credentials can then be reused to 
compromise other repositories or publish more infected packages, allowing the attack to spread through the software supply chain. 
[The GitHub Blog](https://github.blog/security/supply-chain-security/disrupting-supply-chain-attacks-on-npm-and-github-actions/?utm_source=chatgpt.com)

- **Compromised developer or maintainer accounts:** Attackers may obtain control of an account through stolen passwords, phishing, compromised email accounts, or stolen authentication tokens.
  Once inside, they can act as the legitimate maintainer and change packages or repositories. [Docs Npm: threats and mitigations](https://docs.npmjs.com/threats-and-mitigations)

- **Stolen authentication credentials:** npm tokens, GitHub personal access tokens, OAuth tokens, and cloud credentials can give attackers access to publishing systems or repositories,
  depending on the permissions assigned to them.
  [Github: Managing personal access tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens?search-overlay-open=true&utm_source=chatgpt.com)

- **Malicious package updates:** An attacker who gains publishing access can add malicious code to a new version of an existing trusted package. The code may run during installation through npm lifecycle or post-install scripts.
[The GitHub Blog: Our plan for more secure supply chain](https://github.blog/security/supply-chain-security/our-plan-for-a-more-secure-npm-supply-chain/)

- **Malicious npm packages:** Attackers can publish packages with names similar to popular packages, hoping developers install the wrong one. This technique is known as typosquatting; dependency confusion can also cause a
  public malicious package to replace an intended private dependency. [docs.npmjs.com: Threats and mitigations](https://docs.npmjs.com/threats-and-mitigations/)

- **Repository access tokens:** GitHub tokens can be used to authenticate API or repository operations. If a stolen token has write permissions, an attacker may be able to modify code, create releases, change workflows, or
  access additional project resources. [GitHub Docs: Secure use reference](https://docs.github.com/actions/security-guides/security-hardening-for-github-actions)

- **GitHub Actions workflows:** Unsafe workflows may execute untrusted pull-request code while having access to repository secrets or the `GITHUB_TOKEN`. GitHub warns that privileged events such as `pull_request_target` must not be used
  to build or run untrusted code. [GitHub Docs: Securely using pull request target](https://docs.github.com/actions/reference/security/securely-using-pull_request_target)

- **Spreading between repositories:** Malware can search a developer machine or CI/CD runner for additional credentials. Attackers can reuse those credentials to compromise more repositories, alter more packages, and continue the attack.
  [Github blog: Disrupting supply chain attacks on npm and github actions](https://github.blog/security/supply-chain-security/disrupting-supply-chain-attacks-on-npm-and-github-actions/)
---
# Workflow - Attack flow diagram
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


## Sources
1. GitHub Blog, “Disrupting supply chain attacks on npm and GitHub Actions,” July 28, 2026. The GitHub Blog
2. GitHub Blog, “Our plan for a more secure npm supply chain,” September 22, 2025. The GitHub Blog
3. npm Documentation, “npm: Threats and Mitigations.” docs.npmjs.com
4. GitHub Documentation, “Secure use reference.” GitHub Docs
5. GitHub Documentation, “Securely using pull_request_target.”
