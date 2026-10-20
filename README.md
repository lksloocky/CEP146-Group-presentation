# How attacks work.
- Attackers can compromise software projects in several ways, including stolen maintainer accounts, authentication tokens, malicious package updates, and unsafe GitHub Actions workflows. 
- Once an attacker gains publishing or repository access, they can modify trusted packages or workflows. 
- A hidden post-install script may then execute when a developer runs npm install, allowing credentials such as npm, GitHub, or cloud tokens to be stolen. 
- Those credentials can be reused to publish infected package versions and spread the attack to more repositories. 

> The key idea is that attackers target the development process itself, not only the finished application.
