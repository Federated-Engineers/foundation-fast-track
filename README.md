# Foundation Fast-Track

Welcome to **Federated Engineers**! 

Welcome! This repository serves as your Acceleration Resources hub. You will need these materials to complete our `2-Hour Live Implementation Interview (LII)`, the final technical benchmark before joining our engineering team.

At Federated Engineers, we design high-performance, scalable, and deeply interconnected systems. To maintain our operational excellence, every engineer, regardless of their specialization must be thoroughly fluent in the core tools and architectural patterns housed in this repository.

Consider this curriculum your fast track to understanding our production landscape, empowering you to ship your first lines of code with absolute confidence.

## ⚠️⚠️⚠️ IMPORTANT !!!!!! ⚠️⚠️⚠️
Our `Live Implementation Interview (LII)` ensures that every engineer entering our talent pool possesses the strong technical fundamentals required to thrive in our environment.

- `No Multiple Choice:` This is not a theoretical quiz.

- `Beyond Just Talking:` We value technical communication, but this conversation happens in the IDE.

- `Purely Hands-On:` You will be building, debugging, and deploying in real time.

- `Target Scope:` The core challenges will directly test the 4 architectural layers structured inside this repository.
  - `01-local-essentials`
  - `02-cloud-and-infra`
  - `03-data-and-orchestration`
  - `04-delivery`

---

## Why This Fast-Track Matters

At Federated Engineers, we don't just write code in isolation; we architect interconnected ecosystems. This fast-track curriculum is designed to help you narrow what you need and connect the dots between spinning up a local script and watching it scale seamlessly in a production cloud environment.

A superficial understanding of these tools leads to team friction, deployment bottlenecks, and severe security vulnerabilities. We expect you to be comfortable with these stacks, because it forms the foundational language our team speaks every single day. Completing this preparation ensures you won't just survive our onboarding, you will as well thrive in it.

---

## Repository Structure & How to Use It

The repository is structured into `four` sequential phases. Each module provides dedicated engineering notes, curated video masterclasses, and a `hands-on Exercise` to validate your practical understanding.

```text
foundation-fast-track/
├── README.md                     # This onboarding roadmap
├── 01-local-essentials/          # Module 1: Git, GitHub, & Docker
├── 02-cloud-and-infra/           # Module 2: AWS Basics & Terraform
├── 03-data-and-orchestration/    # Module 3: Apache Airflow & DBT
└── 04-delivery/                  # Module 4: CI/CD Pipelines
```

## How to Make the Best Out of It:

#### Don't Skip the "Why":
Before diving into the videos or writing any code, carefully read the Why We Use It section in each module. Grasping the business use case and architectural context is far more critical than memorizing code syntax.

#### Watch then Do:
Use the linked YouTube resources to establish your baseline mental model. As you watch, actively experiment test the limits of the configurations and deliberately break things to understand how they fail. Once you grasp the mechanics, immediately tackle the challenge task at the end of the module.

## The Pillars of Our Stack (The "Why")

### 01-local-essentials

#### Git & GitHub:
Federated Engineers is fundamentally a collaborative pool. Mastery of Git is a `massive`, `non-negotiable` must-have. You must be comfortable managing branches, resolving complex merge conflicts, and conducting clean Peer Reviews via Pull Requests. If our Git workflow stalls, our entire engineering shipping velocity stalls.

#### Docker:
The majority of our production workloads run on container orchestration platforms like Amazon `EKS (Elastic Kubernetes Service)` and `Amazon ECS (Elastic Container Service)`. To understand how code behaves on EKS/ECS, you must first master Docker locally. You need to know how to containerize applications, manage multi-container environments, optimize image sizes, dcoker volume and understand docker networks a.

### 02-cloud-and-infra

#### AWS (Core Infrastructure):
`Amazon Web Services - AWS` is the absolute bedrock of our cloud infrastructure. You cannot build here without mastering three core areas:

#### IAM (Identity and Access Management):
We enforce strict least-privilege principles. You must understand how roles, policies, and users grant secure permissions to our services.

#### VPC (Virtual Private Cloud):
When bootstrapping data platforms, networking is at the core of systems communication, solving complex networking challenges (subnets, routing, NAT gateways) is a daily reality. VPC knowledge is strictly non-negotiable at Federated Engineers.

#### EC2 (Elastic Compute Cloud):
This is the fundamental compute server underlying our workloads. Understanding how EC2 instances operate, scale, and connect is critical. No data movemnet without a server at the end.

#### Terraform:
We never click around the UI console of our platforms to deploy infrastructure. Everything is declared as code. You will use Terraform to safely provision, modify, and track infrastructure changes safely.

### 03-data-and-orchestration

#### Apache Airflow: 
This is the centralized "brain" of our data platform. We rely heavily on Airflow to schedule, automate, and orchestrate complex workflow pipelines, managing dependencies across various systems seamlessly.

#### DBT (Data Build Tool):
While Airflow handles the orchestration, DBT handles our data transformations inside our warehouses. You need to understand how DBT allows us to write modular SQL, run data quality tests, and generate documentation automatically.

### 04-delivery

#### CI/CD Pipelines:
Continuous Integration and Continuous Delivery sit at the corner of nearly every single repository at Federated Engineers. Automation is embedded as a strict standard across all our deliverable projects. Having a strong base knowledge of CI/CD pipelines will massively benefit you, enabling you to automate testing, linting, and cloud deployments the second your code is merged.

## Ready to Start?
Dive into your first module now !!!!!!!
