# 🛠️ Terraform: Infrastructure as Code (IaC)

### Upstream Curriculum Reference ( VERY IMPORTANT !!!!!! ) 
> 📚 **Core Reading Material:** This module relies heavily on the exhaustive Infrastructure as Code (IaC) materials compiled by the **CoreDataEngineers Bootcamp**. You are required to read through their repository thoroughly to understand HCL syntax, provider blocks, and state management:
> 👉 [CoreDataEngineers CDE-BOOTCAMP - Terraform Module](https://github.com/coredataengineers/CDE-BOOTCAMP/tree/main/10_terraform)

---

### 🚨 The Existing Problem: The Danger of "ClickOps"
Before tools like Terraform existed, engineers built cloud environments manually. They would log into the AWS Web Console, click around the UI to spin up an EC2 instance, click more buttons to create a VPC, configure a database, and manually paste in security settings. 

In a production engineering environment like Federated Engineers, this manual approach (affectionately called **ClickOps**) introduces massive operational flaws:
1. **Human Error & Inconsistency:** It is incredibly easy to forget to check a single security box or typo an IP range, creating massive security vulnerabilities.
2. **Configuration Drift:** Over time, people make minor manual tweaks to the cloud console. Eventually, no one actually knows the exact current state of the infrastructure.
3. **Zero Audit Trail:** If a database gets deleted or modified, there is no version history or pull request showing *who* changed it, *when*, or *why*.
4. **Unrepeatable Setups:** If you need to spin up an identical "Staging" environment that mirrors "Production," you have to redo hours of manual clicking from memory.

### 💡 The Solution: Why We Use Terraform
Terraform solves this by turning infrastructure into software code. We write declarative configuration files using HashiCorp Configuration Language (HCL). Instead of clicking buttons, we write down our desired state (e.g., *"I want 1 VPC and 2 EC2 instances"*), and Terraform securely figures out how to build it via cloud APIs.

Because our infrastructure is code, we can store it in Git, peer-review it via Pull Requests, run automated tests on it, and tear down or replicate entire cloud data platforms in seconds. At Federated Engineers, **we have a strict zero-ClickOps policy** for infrastructure production. 

---

## 🧠 Core Building Blocks to Master

As you review the [CoreDataEngineers Terraform Repository](https://github.com/coredataengineers/CDE-BOOTCAMP/tree/main/10_terraform), focus entirely on mastering these core mechanics:

* **Providers:** Plugins that tell Terraform which API to talk to (e.g., AWS, GCP, Docker, or GitHub).
* **Resources:** The actual infrastructure pieces you want to build (e.g., an `aws_vpc`, `aws_iam_role`, or `aws_s3_bucket`).
* **Variables & Outputs:** Variables make your code modular and dynamic; Outputs act like return statements, showing you important data (like a database endpoint) after the infrastructure is built.
* **The State File (`terraform.tfstate`):** The absolute source of truth. Terraform maps your written code to real-world cloud resources using this JSON state file. **Never modify this file manually.**

### The Core Lifecycle Commands
You will use these four commands repeatedly throughout your career:
1. `terraform init`: Downloads the required provider plugins and initializes the working directory.
2. `terraform plan`: Previews the exact changes Terraform is about to make. It will show you exactly what will be created `(+)`, modified `(~)`, or destroyed `(-)`. **Always check your plan.**
3. `terraform apply`: Executes the plan and actually provisions the infrastructure in the cloud.
4. `terraform destroy`: Wipes out every resource tracked by your configuration file.

---

## 📺 Fast-Track Resource (Curated YouTube Video and Documenations)

To supplement your reading of the CDE material, watch these tutorials to see Terraform workflows in live action:

* 📺 [Terraform Deep Dive](https://www.youtube.com/watch?v=OHzZ7KuioMA).
* [Terraform Architecture](https://spacelift.io/blog/terraform-architecture)
  

