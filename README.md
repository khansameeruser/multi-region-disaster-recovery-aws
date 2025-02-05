# Multi-Region Disaster Recovery Architecture in AWS
The architecture consists of two AWS regions (us-east-1 and us-east-2) where the web application is hosted using EC2 instances with Auto Scaling and Elastic Load Balancer (ELB). The primary database (MySQL RDS) is deployed in the first region and continuously replicates data to a cross-region read replica in the second region.
AWS Route 53 is used for traffic routing and failover. If the primary region fails, Route 53 redirects traffic to the secondary region, ensuring business continuity.
# Architecture
![Cloud DR](https://github.com/user-attachments/assets/dc5c0616-be8e-49ce-9083-1409a3a52fb1)
## Architecture Breakdown
This architecture leverages multiple AWS services, each playing a key role in ensuring reliability and performance.

### **1️ Elastic Load Balancer (ELB)**
- **Traffic Distribution** – Distributes incoming traffic across multiple EC2 instances in each region.
- **Failover Handling** – Ensures users are always routed to healthy instances, reducing downtime.

### **2️⃣ Auto Scaling**
- **Dynamic Scaling** – Automatically adjusts the number of EC2 instances based on demand.
- **Fault Tolerance** – Ensures at least the minimum required instances are running in case of failures.

### **3️⃣ VPC & Subnet**
- **Network Isolation** – Provides a secure and isolated environment for resources.
- **Subnet Segmentation** – Separate subnets for web servers and databases enhance security and performance.

### **4️⃣ Amazon RDS (Relational Database Service)**
- **Managed Database** – AWS manages backups, patching, and scaling for the MySQL database.
- **Cross-Region Read Replica** – Replicates data from the primary database to a secondary region for disaster recovery.

### **5️⃣ MySQL Database**
- **Data Storage** – Stores web application data such as user records, transactions, and logs.
- **Replication Support** – Enables automatic data synchronization to a standby replica in another region.

### **6️⃣ Route 53 (DNS & Failover)**
- **Traffic Routing** – Routes user traffic to the nearest or active region using DNS.
- **Automatic Failover** – Detects regional failures and redirects users to the secondary region.

### **7️⃣ AWS IAM (Identity & Access Management)**
- **Access Control** – Restricts permissions for users, applications, and services.
- **Least Privilege Enforcement** – Ensures only authorized resources can access critical components.

### **8️⃣ AWS KMS (Key Management Service)**
- **Data Encryption** – Encrypts sensitive data stored in RDS databases and other AWS services.
- **Key Management** – Provides secure access and rotation policies for encryption keys.

### **9️⃣ Amazon CloudWatch**
- **Monitoring & Alerts** – Tracks application health, server utilization, and database performance.
- **Automated Response** – Can trigger actions (e.g., Auto Scaling, Lambda failover scripts) based on predefined thresholds.

---

## ✅ Benefits

✔ High Availability – The architecture ensures minimal downtime with automatic failover.

✔ Fault Tolerance – EC2 instances and databases are replicated across multiple regions.

✔ Scalability – Auto Scaling adapts dynamically to traffic demand.

✔ Security – IAM policies and KMS encryption enhance data protection.

✔ Performance Optimization – Load balancing and cross-region replication ensure smooth operations.
