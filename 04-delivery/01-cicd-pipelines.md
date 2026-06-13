# 🚀 Continuous Integration & Continuous Delivery (CI/CD)

### Upstream Curriculum & Training Playlists
To establish an enterprise-grade understanding of automated release workflows, cloud credentials isolation, and self-healing deployment design, you are required to complete these curated video modules:
* 📺 **Complete GitHub Actions Course:** [DevOps Directive - From BEGINNER to PRO](https://www.youtube.com/watch?v=Xwpi0ITkL3U) — An exhaustive 3.5-hour masterclass by Sid Palace detailing runner footprints, declarative job configurations, caching pipelines, and secure secret patterns.
* 📋 **Production DevOps Pipeline Series:** [Anton Putra - GitHub Actions & CI/CD Master Playlist](https://www.youtube.com/playlist?list=PLArH6NjfKsUhvGHrpag7SuPumMzQRhUKY) — A multi-part framework breakdown walking through practical microservice orchestration, Kubernetes integrations, and secure container shipping.

---

## 🚨 The Existing Problem: The Operational Risk of Manual Shipping

Before tools like GitHub Actions, GitLab CI, or Jenkins stabilized the industry, shipping software and data platforms to production was a chaotic, manual task handled by specialized release teams. This approach introduced significant failure vectors:

* **The "Works on My Machine" Paradigm:** Developers modified code locally within environments containing hidden dependencies or undocumented package versions. The application ran perfectly on their machine but crashed instantly upon launching on a remote production Linux cluster.
* **Configuration Drift & Code Regressions:** When multiple developers manually merged separate feature sets into a master branch without immediate, isolated testing, syntax breaking bugs or unformatted code anomalies slipped through unnoticed. Bugs were frequently caught by end-users hours or days after release.
* **Security & Insecure Packaging:** Manual deployment required engineers to store highly sensitive cloud infrastructure access keys and production registry passwords locally on their laptops. One accidental commit could leak root credentials to public repositories.
* **Slow, Erratic Release Cadence:** Because building, testing, and pushing code images manually took hours of focus, teams grew afraid to deploy. Releases happened once a month or once a quarter, stacking up massive, high-risk code changes in a single launch day.

---

## 💡 The Solution: Shifting Safety Left via Automated Pipelines

CI/CD entirely eliminates human manual error by translating the integration, validation, and deployment phases into an automated, deterministic lifecycle loop.


### 1. Continuous Integration (CI) — *Quality Assurance & Linting*
CI forces developers to integrate their small code modifications into the shared mainline branch early and often. Every single time a developer pushes a branch or opens a Pull Request, an automated remote system catches the event, boots a sterile sandbox compute runner, and executes predefined tasks:
* Restructures and verifies syntax layouts using **code formatting formatters** and **linters** (like `black`, `flake8`, or `ruff`).
* Installs isolated project dependencies cleanly from scratch.
* Executes unit and integration test frameworks automatically.

If any line of code fails a lint requirement or throws a test exception, the CI pipeline fails immediately. The pull request is automatically blocked from merging, acting as a firewall that keeps the main branch consistently stable.

### 2. Continuous Delivery / Deployment (CD) — *Immutable Artifact Distribution*
Once the CI pipeline certifies that the code is stable and passes all quality benchmarks, the **CD pipeline** assumes control. It automates compilation and distribution:
* Compiles your source code down into an immutable **Docker container image**.
* Programmatically tags the asset with a unique version or Git Commit SHA identification string.
* Authenticates securely with remote cloud registries to execute a `docker push`.
* Instructs compute environments (like AWS ECS, EKS, or Kubernetes clusters) to perform a rolling upgrade with no manual server downtime.

---

## 🏢 Why CI/CD is Mandatory at Federated Engineers

At Federated Engineers, **we treat human operational touchpoints in the deployment cycle as a system flaw.** Our platforms are complex, distributed architectures processing high-velocity data. 

We maintain a strict pipeline enforcement standard:
1. **Zero Direct Production Access:** No engineer possesses local credential privileges to manually push images or modify live cloud containers from their laptop. All changes flow through automated pipelines.
2. **Immutable Traceability:** Every running microservice tag in our environment maps directly back to an explicit Git commit SHA and an associated successful GitHub Action workflow run.
3. **Automated Clean-Up:** By delegating formatting, security vulnerability checking, and image composition to automated workflows, our engineering talent focuses purely on building software, not maintaining release configurations.

---

## 🧠 Core GitHub Actions Architecture

To write custom configurations successfully, you must master the fundamental hierarchical components of GitHub Actions:


* **Workflows:** The top-level automated process defined inside a text configuration file located at `.github/workflows/your-pipeline.yml`.
* **Events (Triggers):** The specific Git event that forces the workflow to execute (e.g., `on: push`, `on: pull_request`, or `on: workflow_dispatch` for manual clicking).
* **Jobs:** Isolated execution containers or virtual machine environments running on GitHub-hosted systems (called **Runners**). Multiple jobs run in parallel by default, but can be forced into a sequential order using the `needs` tag.
* **Steps:** The sequential individual task operations executed inside a specific job. A step can run a basic shell script (`run: pip install -r requirements.txt`) or call reusable complex plugin modules from the GitHub Marketplace (`uses: actions/checkout@v4`).

---

🎯 Challenge
You must create a local codebase that intentionally challenges an automated pipeline's linting and formatting rules. 
Once the pipeline enforces clean standards, it must autonomously build your application into a Docker container image 
and securely ship it to your remote public container registry (Dockerhub).

🛠️ Technical Specifications
1. The Application Component
Create a simple Python script that reads from an API and save the data after some transformation as a parquet file.

2. The Packaging Component
Write a Dockerfile file to containerize your Python application.

3. The Continuous Integration (CI) 
Implement a GitHub Actions workflow that triggers dynamically on any code push or pull request to your branch.

Integrate two explicit quality tools: `flake8` (to assert style and syntax compliance) and `isort` (to assert that import hierarchies are organized cleanly).

The pipeline must be designed to throw an immediate error code and stop running if either of these tools detects structural messiness.

4. The Continuous Delivery (CD)
Establish a separate deployment sequence within the same workflow.

Hard Rule: This deployment sequence must possess an explicit dependency tag. It must never run if the code quality verification step fails or is skipped.

Use secure environment parameters to handle authentication. Your clear-text passwords or secret credentials must never be hardcoded directly into the workflow file.

Upon successful authentication, the workflow must compile the container and push it to your remote registry with a tracking tag.

Good Luck!!!!
