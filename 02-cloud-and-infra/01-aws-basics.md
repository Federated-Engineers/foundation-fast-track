# AWS Cloud Fundamentals: Bedrock of Our Infrastructure

## Upstream Curriculum Reference ( VERY IMPORTANT!!!! )

> **Core Reading Material:** This module builds directly upon the foundational cloud architecture curriculum maintained by the **CoreDataEngineers Bootcamp**.
 
> For deep-dive theoretical explanations, architectural diagrams, and foundational lab notes, review their upstream repository:

>  [CoreDataEngineers CDE-BOOTCAMP - AWS Cloud Module](https://github.com/coredataengineers/CDE-BOOTCAMP/tree/main/09_aws_cloud)

---

## Why We Use It at Federated Engineers
Amazon Web Services (AWS) is the absolute bedrock of our cloud infrastructure. We don't maintain physical servers; everything we build, orchestrate, and deliver lives inside AWS. 

As an Engineer in our pool, you cannot build resilient data platforms or deploy services blindly. You need to understand how the underlying network flows, how security permissions are tightly locked down, and where your compute power actually executes. Whether you are writing an Airflow DAG or optimizing a container image, your code interacts with AWS resources constantly. Mastering these cloud basics is entirely non-negotiable.

---

## The Non-Negotiable Pillars of Our Cloud Footprint

To comfortably operate on our team, you must possess a functional mental model of these three core AWS services:

### 1. IAM (Identity & Access Management) : *Security & Permissions*

We operate under a strict **Least-Privilege Principle**. No service, application, or engineer is granted more access than absolutely necessary to execute its job. 

* **Users vs. Roles:** We rarely use long-lived IAM Users with permanent access keys. Instead, we rely heavily on **IAM Roles**, which grant temporary security credentials. 

* **Policies:** JSON documents that explicitly state *who* (Principal) can do * what* (Action) to *which resource* (Resource). You must know how to read an IAM Policy to debug access-denied errors in your application workloads.

### 2. VPC (Virtual Private Cloud) : *Networking & Isolation*

When bootstrapping data platforms or deploying clusters, solving networking challenges is a daily reality. A VPC is your isolated private network slice in the AWS cloud.

* **Public vs. Private Subnets:** Our web-facing entry points live in Public subnets, while our databases, Airflow workers, and core data platforms are locked away in Private subnets.

* **Gateways & Routing:** You must understand how **Internet Gateways** allow public access, and how **NAT Gateways** allow our isolated private backend containers to securely download dependencies from the internet without exposing themselves to inbound threats.

### 3. EC2 (Elastic Compute Cloud) : *The Compute Server*

Despite running modern serverless tools, EC2 instances (Virtual Servers) are the fundamental compute nodes that power nearly all our heavy workloads. When we run container orchestration platforms like **Amazon EKS** or **Amazon ECS**, those containers are ultimately scheduled onto clusters of EC2 instances. Understanding instance types, security groups (virtual firewalls), and how storage volumes attach to EC2 is critical to performance tuning.

---

## Fast-Track Resources (Curated YouTube Videos)

To supplement the CoreDataEngineers repository notes, watch these videos to solidify your understanding of cloud architecture:

Note: Please watch it in this order below

* 📺 [AWS IAM Explainer (Understand Roles, Policies, and Users)](https://www.youtube.com/watch?v=bO25vbkoJlA).

* 📺 [AWS VPC Tutorial for Beginners](https://www.youtube.com/watch?v=43tIX7901Gs) — A fantastic step-by-step mapping of VPC, subnets, route tables, and gateways.

* 📺 [AWS EC2 Deep dive](https://www.youtube.com/watch?v=4dscVzCaXCU) — *Note: You don't need to watch all.*

