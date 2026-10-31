# Day 1: Introduction to DevSecOps & Threat Modeling

## 1. What is DevSecOps and Why is it Important?
* **Definition:** DevSecOps is not a separate role or distinct from DevOps. It is simply **DevOps with a security mindset**. Any DevOps engineer who integrates security consideration into every action is practicing DevSecOps.
* **The Backstory:** Early DevOps adoption focused intensely on speed, automation, CI/CD pipelines, Kubernetes, and Infrastructure as Code (IaC), but largely bypassed deep security practices. This separation left infrastructure vulnerable, prompting organizations to push for security to be integrated seamlessly into the existing workflow.

## 2. Scope of DevSecOps
DevSecOps extends far beyond just adding a couple of security stages to a CI/CD pipeline. Its scope covers all core DevOps activities:
* **Git / Source Control:** Implementing pre-commit hooks to detect credentials/secrets before they get pushed, and setting up strict Role-Based Access Control (RBAC).
* **Infrastructure as Code (IaC):** Securing tools like Terraform by pairing them with secret management systems like HashiCorp Vault to keep cloud provider credentials secure.
* **Scripting (e.g., Python):** Checking vulnerability databases to avoid pulling outdated or insecure third-party dependencies (e.g., selecting safe Flask package versions).
* **Containers:** Writing secure Dockerfiles by running processes as non-root users, utilizing distroless images, and incorporating multi-stage builds to limit attack surfaces.
* **Kubernetes:** Designing infrastructure defensively by deploying clusters within a Virtual Private Cloud (VPC) inside private subnets, alongside secret isolation solutions.
* **CI/CD Pipelines:** Adding automated checkpoints like Static Application Security Testing (SAST), container image scanning (using Trivy or Snyk), and dependency validation.

## 3. Core Principles
* **Shift Left Principle:** Traditionally, security was handled on the far right (post-deployment or at the production level). Shift Left moves security considerations to the absolute beginning of the lifecycle—starting at the point of repository creation, architectural design, and initial development.
* **AI Impact on DevSecOps:** As generative AI writes more code (60-80% in many modern teams), it frequently introduces vulnerabilities by suggesting outdated packages, uncompliant code, or buggy logic from external forums like Reddit or Stack Overflow. Developers focus primarily on functionality, leaving a crucial gap. Strong DevSecOps automated pipelines act as the ultimate counter-measure to catch AI-generated security flaws.

## 4. Onboarding DevSecOps & Threat Modeling
* **The Challenge:** Joining a legacy company or MNC often means facing resistance to updating workflows. When pipelines are already functional, management can be hesitant to change them.
* **The Solution:** Use **Threat Modeling** to proactively diagnose and surface existing vulnerabilities in a professional report (PDF) to justify onboarding security practices.
* **Threat Modeling Defined:** A structured process used to identify, analyze, and mitigate potential issues or gaps across existing application systems and architectures.

## 5. Tooling Demo: OWASP Threat Dragon
* **Overview:** While many threat modeling solutions are commercially licensed, **OWASP Threat Dragon** is a completely free, open-source tool used for proof-of-concept visual threat modeling.
* **Core Components:** Architecture flow diagrams are constructed using only four primary elements:
  1. Process components (e.g., a Web Application)
  2. Actor components (e.g., an unauthenticated User)
  3. Data stores (e.g., a MongoDB instance)
  4. Data flows (connecting lines mapping out how traffic navigates components)
* **The STRIDE Framework:** Threat Dragon operates on the Microsoft-designed **STRIDE** security matrix to evaluate risk:
  * **S**poofing
  * **T**ampering
  * **R**epudiation
  * **I**nformation Disclosure
  * **D**enial of Service
  * **E**levation of Privilege
* **Workflow & Mitigation:** 
  * The tool scans the visual architecture and flags context-based vulnerabilities (e.g., unencrypted databases or lack of explicit authorization boundaries).
  * Just like inside an agile board (e.g., Jira), teams can collaboratively drill into vulnerabilities, view official OWASP definitions, adjust severity levels, document resolution steps, and mark risks as "Mitigated."
  * The tool automatically generates a consolidated, downloadable security report summarizing the complete breakdown of identified vulnerabilities.
