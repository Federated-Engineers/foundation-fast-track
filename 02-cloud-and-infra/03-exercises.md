# CHALLENGE
## 1. The Isolated Network Topology (VPC)
- Provision a custom Virtual Private Cloud (VPC) with a dedicated classless inter-domain routing block - CIDR.
Inside this VPC, partition the address space to create exactly two subnets with 156 IPs each for the subnets:

- Public Subnet: Used for routing external traffic. Configure it to map public IP addresses to resources launched inside it automatically.

- Private Subnet: A completely isolated address tier where our core internal compute workloads reside.

- Deploy an Internet Gateway (IGW) attached to your VPC, and build a custom Route Table that explicitly binds the Public Subnet to the Internet Gateway.
  Ensure the Private Subnet has no direct route out to the IGW.

## 2. Least-Privilege Identity Management (IAM)
- Create an IAM Role designated explicitly for an AWS ec2 to assume it.

- Create a custom `S3 read-only policy` that allow listing all the buckets in s3 to this role.

- Provision an `IAM Instance Profile` that wraps this role so it can be physically attached to a virtual compute instance at launch.

# 3. Network Firewalls & Secure Compute (EC2)
- Create a `Security Group` acting as a network firewall. It must strictly follow these rules:

  - Ingress (Inbound): Permit incoming traffic only from your house IP address. Block all other public access.

  - Egress (Outbound): Allow unrestricted outbound internet access (Port 0-65535, protocol -1) so the machine can run system security updates.

- Provision an EC2 Instance using the latest official Amazon Linux 3 AMI and attach the instance profile you created in `step 2` to it.

- Enter the EC2 instance, confirm if you are able to see the list of s3 buckets on the CLI inside the Instance.
  - If YES, you've successfully solve the problem.
  - If NO, you need to continue troubleshooting.

# 4. Infrastructure as Code Deployment
- Bootstrap a VPC stacks with Terraform
  - VPC
  - 1 Subnet
  - Internet Gateway
  - Route Table
  - Security Group
 
Good Luck !!!!!!!!
