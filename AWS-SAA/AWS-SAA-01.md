## 🚀 General Exam Strategy & "Pro Tips for AWS SAA exam"

[AWS SAA-C03 Exam Guides](https://docs.aws.amazon.com/aws-certification/latest/examguides/solutions-architect-associate-03.html)

### 1. The "Keyword" Elimination Method

AWS questions are scenarios. Use the process of elimination by looking for these specific modifiers in the question:

* **"Least operational overhead"**: Look for **Managed Services** (RDS over EC2 DB) or **Serverless** (Lambda, Fargate, S3).
* **"Most cost-effective"**: Look for **Spot Instances**, **S3 Intelligent-Tiering**, or **Reserved Instances**. If the workload is "predictable," think RI/Savings Plans.
* **"Highly available"**: Look for **Multi-AZ**.
* **"Fault-tolerant"**: Look for architectures that can lose a whole component (or AZ) and continue without a performance drop.

### 2. Think like a Well-Architected Framework

The exam is 100% based on the **AWS Well-Architected Framework**. When in doubt, choose the answer that:

* Decouples components (SQS/SNS).
* Uses a "Defense in Depth" security posture.
* Automates recovery (Auto Scaling).

### 3. Quick-Fire Service Differentiators

* **Global Accelerator vs. CloudFront**: Global Accelerator improves performance for **TCP/UDP** traffic using Anycast IPs; CloudFront is a **CDN** for caching content at the Edge.
* **NLB vs. ALB**: NLB is for **Extreme Performance/Static IPs/TCP/UDP**; ALB is for **HTTP/HTTPS/Layer 7** smart routing.
* **SQS vs. SNS**: SQS is **Pull** (1-to-1 processing); SNS is **Push** (Fan-out/1-to-many).

---

## 🏛️ Domain Breakdown: High-Level Focus

| Domain | Weight | Key Focus Areas |
| --- | --- | --- |
| **1. Secure Architectures** | 30% | IAM (Roles/Policies), KMS, Secrets Manager, VPC (NACLs vs SG), AWS Organizations (SCP). |
| **2. Resilient Architectures** | 26% | Multi-AZ RDS, Auto Scaling, Route 53 (Failover), SQS (Decoupling), Storage Durability (S3). |
| **3. High-Performing** | 24% | EBS types (io2 vs gp3), ElastiCache, Aurora Serverless, Global Accelerator, Enhanced Networking. |
| **4. Cost-Optimized** | 20% | S3 Lifecycle policies, Spot Instances, Compute Optimizer, Aurora Scaling, Data Transfer costs. |

---

## 🎮 Keyword Association Game

*In the exam, when you see **Word A**, your brain should immediately think of **Service B**.*

| If the question says... | You think... |
| --- | --- |
| **"Long-term, digital vellum, compliance"** | **S3 Glacier Deep Archive** |
| **"Sub-millisecond latency, NoSQL"** | **DynamoDB + DAX** |
| **"Millisecond latency, SQL/Relational"** | **Amazon Aurora** (or RDS with ElastiCache) |
| **"Shared storage, Windows, SMB"** | **FSx for Windows** |
| **"Shared storage, Linux, POSIX/NFS"** | **EFS** |
| **"HPC (High Performance Computing), Lustre"** | **FSx for Lustre** |
| **"Decouple, asynchronous, buffer"** | **SQS** |
| **"Fan-out, push notifications"** | **SNS** |
| **"Real-time streaming, video/data"** | **Kinesis** |
| **"Audit API calls, 'Who did what?'"** | **CloudTrail** |
| **"Performance metrics, 'Is it up?'"** | **CloudWatch** |
| **"Automatic rotation of DB secrets"** | **Secrets Manager** (Not Parameter Store) |

---

## 🧩 Trick Scenarios: "This or That?"

AWS loves to give you two options that *both* work, but one is "Better" based on the question's constraints.

### 1. The "Cheap vs. Fast" Data Migration

* **Snowball Edge:** Use if the data is massive (PBs) and the internet is slow. (Keywords: **Offline**, **Petabytes**, **Weak connectivity**).
* **AWS DataSync:** Use for online transfers over the internet or Direct Connect. (Keywords: **Online**, **Automated**, **NFS/SMB to S3**).

### 2. The "Global Speed" Battle

* **Global Accelerator:** Optimizes the **network path** (Layer 4) using Anycast IPs. Good for non-HTTP or gaming (UDP/TCP).
* **CloudFront:** Optimizes **content delivery** (Layer 7) via caching. Good for static/dynamic web content.

### 3. The "Database Failover" Difference

* **RDS Multi-AZ:** High Availability. One DB is active, one is standby. Failover is automatic via **DNS change**.
* **RDS Read Replicas:** Performance scaling. Used for **Read-heavy** workloads. Manual failover (usually).

---

## 🛠️ Pro Strategy: The "Constraint" Filter

Every SAA-C03 question has a hidden **primary constraint**. Before looking at answers, identify which "Pillar" the question is testing:

1. **"Least Operational Overhead"**  Delete any answer that involves "Managing an EC2 instance" or "Installing software." (Pick Lambda, RDS, Fargate).
2. **"Most Cost-Effective"**  S3 Intelligent-Tiering and Spot Instances are your best friends.
3. **"Business Continuity / RPO / RTO"**  Look for Pilot Light, Warm Standby, or Multi-Region.

---

