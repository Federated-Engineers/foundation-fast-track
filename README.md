# Foundation Fast-Track

Welcome to **Federated Engineers**! 

This repository is your acceleration pad. At Federated Engineers, we build high-performing, scalable, and highly collaborative systems. To maintain our velocity, every engineer—regardless of their specific role—must be thoroughly comfortable with the core tools and architectural patterns found in this repository. 

Consider this curriculum your shortcut to understanding our production environment so you can push your first lines of code with absolute confidence.

---

## Why This Fast-Track Matters

At Federated Engineers, we don't just write code in isolation; we build interconnected ecosystems. This fast-track exists to help you **connect the dots** between writing a script locally and seeing it scale in a production cloud environment. 

Being "just okay" with these tools leads to friction, deployment bottlenecks, and security vulnerabilities. We expect you to be deeply comfortable with this stack because it forms the baseline language our team speaks every single day. Completing this curriculum ensures you won't just survive our onboarding—you will thrive in it.

---

## Repository Structure & How to Use It

The repository is divided into four chronological phases. Each folder contains dedicated markdown notes, curated YouTube resources, and a hands-on **Acceleration Exercise**.

```text
foundation-fast-track/
├── README.md                     # This onboarding roadmap
├── 01-local-essentials/          # Module 1: Git, GitHub, & Docker
├── 02-cloud-and-infra/           # Module 2: AWS Basics & Terraform
├── 03-data-and-orchestration/    # Module 3: Apache Airflow & DBT
└── 04-delivery/                  # Module 4: CI/CD Pipelines
```

# How to Make the Best Out of It:
Don't Skip the "Why": Before watching videos or writing code, read the Why We Use It section in each module. Understanding the business and engineering context is more important than memorizing syntax.

Watch then Do: Watch the linked YouTube videos to establish your mental model, then immediately open the /exercises folder inside that module to practice.

Break Things Safely: This repository is a sandbox. Tweak the Dockerfiles, break the Terraform code, and cause Git conflicts on purpose to learn how to fix them here, rather than in production.

# The Pillars of Our Stack (The "Why")
📁 01-local-essentials
Git & GitHub: Federated Engineers is fundamentally a collaborative tool. Mastery of Git is a massive, non-negotiable must-have. You must be comfortable managing branches, resolving complex merge conflicts, and conducting clean Peer Reviews via Pull Requests. If our Git workflow stalls, our entire engineering shipping velocity stalls.

Docker: The majority of our production workloads run on heavy-duty container orchestration platforms like Amazon EKS (Elastic Kubernetes Service) and Amazon ECS (Elastic Container Service). To understand how code behaves on EKS/ECS, you must first master Docker locally. You need to know how to containerize applications, manage multi-container environments, and optimize image sizes.

# 📁 02-cloud-and-infra
AWS (Core Infrastructure): Amazon Web Services is the absolute bedrock of our cloud footprint. You cannot build here without mastering three core areas:

IAM (Identity and Access Management): We enforce strict least-privilege principles. You must understand how roles, policies, and users grant secure permissions to our services.

VPC (Virtual Private Cloud): When bootstrapping data platforms, solving complex networking challenges (subnets, routing, NAT gateways) is a daily reality. VPC knowledge is strictly non-negotiable.

EC2 (Elastic Compute Cloud): This is the fundamental compute server underlying our workloads. Understanding how EC2 instances operate, scale, and connect is critical.

Terraform: We never click around the AWS UI console to deploy infrastructure. Everything is declared as code. You will use Terraform to safely provision, modify, and track infrastructure changes safely.

# 📁 03-data-and-orchestration
Apache Airflow: This is the centralized "brain" of our data platform. We rely heavily on Airflow to schedule, automate, and orchestrate complex workflow pipelines, managing dependencies across various systems seamlessly.

DBT (Data Build Tool): While Airflow handles the orchestration, DBT handles our data transformations inside our warehouses. You need to understand how DBT allows us to write modular SQL, run data quality tests, and generate documentation automatically.

# 📁 04-delivery
CI/CD Pipelines: Continuous Integration and Continuous Delivery sit at the corner of nearly every single repository at Federated Engineers. Automation is embedded as a strict standard across all our deliverable projects. Having a strong base knowledge of CI/CD pipelines will massively benefit you, enabling you to automate testing, linting, and cloud deployments the second your code is merged.

# Ready to Start?
Let's get moving. Open up your terminal, clone this repository, and dive into your first module:
