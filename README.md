# ☁️ Scalable 3-Tier Web Application Architecture on AWS

## 📝 Project Overview
This project demonstrates a highly available, fault-tolerant 3-tier architecture (Web, Application, and Database tiers) deployed on Amazon Web Services (AWS). It integrates AWS Auto Scaling, Amazon RDS, and Amazon CloudWatch to ensure optimal performance, dynamic elasticity, and comprehensive system monitoring.

## 🏗️ Architecture Components

<img width="931" height="711" alt="Project" src="https://github.com/user-attachments/assets/2175fb93-0c33-4fa8-acaf-86062d86cd2b" />


### 1. Web Tier (Frontend)
* **Compute:** EC2 Instances managed by an Auto Scaling Group (ASG).
* **Networking:** Deployed across Public Subnets spanning multiple Availability Zones.
* **Traffic Distribution:** Handled via Load Balancing to ensure even request routing across instances.

### 2. Application Tier (Backend)
* **Compute:** Scalable, stateless EC2 Instances managed by a dedicated ASG.
* **Networking:** Provisioned within Public Subnets.

### 3. Data Tier (Database)
* **Database Engine:** Amazon RDS configured for Multi-AZ deployment (One Primary, One Standby).
* **Networking:** Isolated within Private Subnets to maximize data security.

### 4. Monitoring & Alerting
* **Metrics & Logging:** AWS CloudWatch continuously tracks system performance and logs.
* **Notification System:** Amazon Simple Notification Service (SNS) configured to dispatch critical alerts directly via Email (Gmail).

## 🚀 Deployment Lifecycle

1. **Network Infrastructure Provisioning:**
   * Create a Virtual Private Cloud (VPC).
   * Distribute 4 Public and 2 Private subnets across 2 distinct Availability Zones.
2. **Web & App Tiers Setup:**
   * Launch EC2 instances with designated Auto Scaling Groups.
   * Attach strict Security Groups to control inbound and outbound traffic.
3. **Database Tier Initialization:**
   * Provision a Multi-AZ RDS instance.
   * Map the database to a private subnet group.
4. **Observability Configuration:**
   * Define CloudWatch Alarms (e.g., triggering when CPU Utilization > 70%).
   * Integrate alarms with SNS topics and subscribe target email addresses.

## 🔐 Security Posture
* **Network Isolation:** Database resources are strictly confined to private subnets, completely shielding them from direct internet access.
* **Access Control:** Public subnets are tightly restricted to allow only necessary web and application port traffic.
* **Identity Management:** EC2 instances assume secure IAM Roles to interact with other AWS services safely, eliminating the need for hardcoded credentials.

## 💡 Key Business Benefits
* **High Availability (HA):** Multi-AZ deployments, Load Balancing, and ASG work together to guarantee minimal downtime and continuous business operations.
* **Elastic Scalability:** Infrastructure dynamically expands or contracts based on real-time traffic demands.
* **Cost Optimization:** Auto Scaling prevents over-provisioning, ensuring computing expenses align strictly with actual usage.
* **Robust Security:** A defense-in-depth approach utilizing IAM, Security Groups, and VPC network isolation.

## 🧠 Additional Notes
* The entire infrastructure is designed to operate in High Availability (HA) mode, providing a highly reliable and cost-efficient foundation for web applications.
* **IaC Ready:** This architecture is fully compatible with Infrastructure as Code (IaC) tools such as **Terraform** or **AWS CloudFormation** for automated, repeatable deployments.
