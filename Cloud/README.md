
---

## ☁️ Cloud Interview Notes

### 1. **What is Cloud Computing?**

* On-demand access to computing resources (servers, storage, databases, networking, software) via the internet.
* Pay-as-you-go model.

---

### 2. **Service Models**

| Model    | Description                 | Example                       |
| -------- | --------------------------- | ----------------------------- |
| **IaaS** | Infrastructure as a Service | EC2, Azure VM                 |
| **PaaS** | Platform as a Service       | Heroku, AWS Elastic Beanstalk |
| **SaaS** | Software as a Service       | Gmail, Dropbox                |

---

### 3. **AWS Core Services**

#### ✅ **EC2 (Elastic Compute Cloud)**

* Virtual machines in the cloud
* Choose AMI (Amazon Machine Image), instance type
* Attach security groups, key pairs

```bash
# SSH into EC2
ssh -i key.pem ec2-user@<public-ip>
```

#### ✅ **S3 (Simple Storage Service)**

* Object storage service for files, backups, logs
* Features: versioning, lifecycle policies, public/private ACLs

```bash
aws s3 cp file.txt s3://mybucket/
```

#### ✅ **Fargate**

* Serverless compute for containers
* Works with ECS/EKS
* No need to manage EC2 instances
* Just define container specs (CPU, memory)

#### ✅ **ECS vs EKS**

| Feature         | ECS (Elastic Container Service) | EKS (Elastic Kubernetes Service) |
| --------------- | ------------------------------- | -------------------------------- |
| Orchestrator    | AWS proprietary                 | Kubernetes                       |
| Simpler setup   | ✅                               | ❌ (K8s learning curve)           |
| Flexibility     | Less                            | More                             |
| Fargate support | ✅                               | ✅                                |

#### ✅ **VM Readymade Images**

* Use AMIs with pre-installed software (e.g., Python, Node, Docker)
* Custom AMIs can be created and shared

#### ✅ **IAM (Identity and Access Management)**

* Define users, roles, and permissions
* Use least-privilege principle

#### ✅ **Other Useful AWS Services**

* **RDS** – Managed DB instances (Postgres, MySQL, etc.)
* **CloudWatch** – Logs and monitoring
* **Route 53** – DNS and domain management
* **Lambda** – Serverless function execution
* **Elastic Load Balancer (ELB)** – Distribute traffic to EC2 or containers

---

### 4. **Azure Core Services**

#### ✅ **Azure VM**

* Similar to EC2
* Use Marketplace images (e.g., Ubuntu with Docker)
* Manage through Azure Portal or CLI

#### ✅ **Azure Blob Storage**

* Equivalent to AWS S3
* Stores unstructured data (images, videos, files)

#### ✅ **Azure App Service**

* PaaS for web applications
* Supports Python, Node.js, .NET, Java, etc.
* Autoscaling, SSL, CI/CD integration

#### ✅ **Azure Container Instances (ACI)**

* Run containers directly without orchestration
* Similar to Fargate

#### ✅ **Azure DevOps**

* CI/CD pipelines (like Jenkins/GitLab)
* Boards for task tracking
* Repos, Artifacts, and Test Plans included

#### ✅ **ARM Templates / Bicep**

* Infrastructure as Code (like Terraform)
* Define cloud resources in JSON (ARM) or simplified DSL (Bicep)

---

### 5. **Key Interview Concepts**

* Shared Responsibility Model (Cloud vs You)
* What is a VPC, Subnet, Security Group?
* How do you deploy a Python app on EC2?
* Difference between EC2 and Fargate?
* What are IAM roles and policies?
* How is AWS billing managed?
* Difference between S3, EBS, and EFS?
* What is multi-AZ deployment?

---

### 6. **Best Practices**

* Use IAM roles over access keys
* Set up billing alerts
* Use autoscaling groups
* Enable S3 versioning and encryption
* Keep public buckets restricted

---