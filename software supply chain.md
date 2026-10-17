Part 1
A software supply chain refers to the entire ecosystem of components, tools, services, and processes involved in creating and delivering software.
What makes up a software supply chain?

Dependencies & third-party libraries: Modern applications rely heavily on external code open-source libraries, frameworks, and transitive dependencies (dependencies of dependencies). These are often installed through package managers like npm.

npm packages: JavaScript projects routinely pull thousands of packages from the npm registry, each maintained by different authors and inheriting their own dependency trees.

GitHub repositories: Developers clone, fork, and integrate code from GitHub, relying on maintainers they do not control.

CI/CD pipelines: Automated systems that build, test, and deploy software. They run compilers, package managers, scanners, and deployment scripts.

GitHub Actions: A common CI/CD automation platform that executes workflows, builds artifacts, and pulls dependencies during the build process.
Modern software relies heavily on code that developers did not write themselves because open source libraries and packages dramatically speed up development, reduce complexity, and provide ready made solutions for common problems. However, this reliance introduces significant security risks: any compromised dependency, malicious npm package, vulnerable GitHub repository, or tampered CI/CD workflow can infect the entire application. A compromised supply chain can lead to unauthorized access, data breaches, corrupted builds, production outages, and regulatory compliance failures (e.g., SBOM requirements).
