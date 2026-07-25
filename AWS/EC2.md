# - Introduction to EC2 service

#### Amazon Elastic Compute Cloud (EC2) is a core service from Amazon Web Services (AWS) that provides scalable, on-demand computing capacity in the cloud. EC2 allows users to launch and manage virtual servers—known as "instances"—which can run a wide range of operating systems and applications

#### Amazon EC2 enables scalable computing in AWS cloud environments by providing on-demand access to virtual servers (instances) that can be easily launched, terminated, or adjusted in resources as workload demands change

# - Security Group (SSH and RDP Port)

#### To allow SSH and RDP access to your Ubuntu (or Windows) instance, you must configure your security group with inbound rules for the relevant ports:

- SSH (Linux): TCP port 22

- RDP (Windows): TCP port 3389

#### Recommended Configuration:

- In your AWS EC2 dashboard, create or select a security group for your instance.

- Add inbound rules as follows:

| Type | Protocol | Port Range | Source (Recommended) | Purpose |
|------|----------|------------|-----------------------|---------|
| SSH  | TCP      | 22         | YOUR_PUBLIC_IP/32     | Linux   |
| RDP  | TCP      | 3389       | YOUR_PUBLIC_IP/32     | Windows |


#### How to add the rules:

1. Go to "Security Groups" in the EC2 Console.

2. Select your security group or create a new one.

3. Under "Inbound rules," click "Edit inbound rules."

4. Add two rules:

- Type: SSH, Protocol: TCP, Port: 22, Source: Your IP (or trusted range)

- Type: RDP, Protocol: TCP, Port: 3389, Source: Your IP (or trusted range)

5. Save the rules

# - Create first Instance of Ubuntu

#### Creating an Ubuntu cloud instance (e.g., AWS EC2):

- Log in to your AWS account.

- Go to the EC2 dashboard and click “Launch Instance.”

- Choose the Ubuntu Amazon Machine Image (AMI).

- Select an instance type (e.g., t2.micro for free tier).

- Configure key pair (for SSH), networking, storage (default usually suffices for first-time users).

- Launch the instance.

# - Instance Types

#### Amazon EC2 offers a wide range of instance types grouped into families based on their optimized use cases, balancing CPU, memory, storage, and networking capabilities for different workloads. The primary instance families include:

- General Purpose: Balanced CPU and memory for diverse applications. Examples: T series (T2, T3, T4g) with burstable performance, and M series (M4, M5, M6) suitable for web servers, small/medium databases, and enterprise applications.

- Compute Optimized: Designed for compute-intensive tasks requiring high CPU performance, such as batch processing and high-performance web servers. Example: C series (C4, C5, C6).

- Memory Optimized: Tailored for memory-intensive workloads like high-performance databases, big data analytics, and in-memory caches. Examples: R series (R5, R6) and X series (X1, X1e).

- Accelerated Computing: Equipped with GPUs or FPGAs for machine learning, graphics processing, and scientific simulations.

- Storage Optimized: Optimized for high, sequential disk throughput and I/O intensive applications like big data and distributed file systems. Examples: I3, D2.

- High Performance Computing (HPC) Optimized: Provide the highest price-performance for workloads needing extreme CPU and memory, such as simulations or molecular modeling.

Each family has different sizes (small to 32xlarge+), allowing flexible scaling based on workload needs. It's recommended to choose based on your application requirements and test different types for optimal performance and cost-efficiency.



- Once running, connect using SSH with the provided .pem key file. Example command:
  
      ssh -i /path/to/my-key.pem ubuntu@your-ec2-public-ip

# - Instance Types

#### Amazon EC2 offers a wide range of instance types grouped into families based on their optimized use cases, balancing CPU, memory, storage, and networking capabilities for different workloads. The primary instance families include:

- **General Purpose:** Balanced CPU and memory for diverse applications. Examples: T series (T2, T3, T4g) with burstable performance, and M series (M4, M5, M6) suitable for web servers, small/medium databases, and enterprise applications.

- **Compute Optimized:** Designed for compute-intensive tasks requiring high CPU performance, such as batch processing and high-performance web servers. Example: C series (C4, C5, C6).

- **Memory Optimized:** Tailored for memory-intensive workloads like high-performance databases, big data analytics, and in-memory caches. Examples: R series (R5, R6) and X series (X1, X1e).

- **Accelerated Computing:** Equipped with GPUs or FPGAs for machine learning, graphics processing, and scientific simulations.

- **Storage Optimized:** Optimized for high, sequential disk throughput and I/O intensive applications like big data and distributed file systems. Examples: I3, D2.

High Performance Computing (HPC) Optimized: Provide the highest price-performance for workloads needing extreme CPU and memory, such as simulations or molecular modeling.

Each family has different sizes (small to 32xlarge+), allowing flexible scaling based on workload needs. It's recommended to choose based on your application requirements and test different types for optimal performance and cost-efficiency.


# - EBS Volumes and its Types

- Amazon EBS is a block storage service provided by AWS.
- It provides persistent storage volumes that can be attached to EC2 instances.
- Unlike instance store (ephemeral storage), EBS volumes persist even after the EC2 instance stops or terminates (unless explicitly deleted).
- Data is automatically replicated within the same Availability Zone (AZ) for durability.

  # Amazon EBS Volume Types – Differences

Amazon **EBS (Elastic Block Store)** provides persistent block storage for EC2.  
Different volume types are available depending on performance and cost.  

---

## 📊 EBS Volume Types Comparison

| Volume Type | Category | Performance | Use Case | Cost |
|-------------|----------|-------------|----------|------|
| **gp2** (General Purpose SSD – Old Gen) | SSD | 3 IOPS/GB, up to 16,000 IOPS, 250 MB/s | General workloads (boot volumes, dev/test, low-latency apps) | 💲💲 |
| **gp3** (General Purpose SSD – Current Default) | SSD | Baseline: 3,000 IOPS & 125 MB/s (independent of size). Scales to 16,000 IOPS & 1,000 MB/s | Same as gp2 but cheaper and more flexible | 💲 |
| **io1** (Provisioned IOPS SSD – Old Gen) | SSD | Provision up to 64,000 IOPS, 1,000 MB/s | Large relational DBs, critical apps needing consistent high IOPS | 💲💲💲 |
| **io2** (Provisioned IOPS SSD – Current Gen) | SSD | Same as io1, but more durable (99.999% durability) | Enterprise-grade critical DBs (Oracle, SAP, SQL) | 💲💲💲 |
| **io2 Block Express** | SSD | Ultra-high: 256,000 IOPS, 4,000 MB/s | Extremely I/O intensive workloads (SAP HANA, High-frequency trading) | 💲💲💲💲 |
| **st1** (Throughput Optimized HDD) | HDD | Max 500 MB/s, not designed for high IOPS | Big Data, Data Warehouses, Streaming logs | 💲 |
| **sc1** (Cold HDD) | HDD | Max 250 MB/s, lowest performance | Archival, cold/infrequent data | 💲 (cheapest) |

---

## 🔑 Key Differences
- **SSD vs HDD**:  
  - SSD → Low latency & IOPS-heavy workloads (Databases, apps).  
  - HDD → Sequential throughput workloads (Big Data, logs).  

- **gp2 vs gp3**: gp3 is **newer, cheaper, and decouples performance from size** (gp2 ties IOPS to volume size).  

- **io1/io2 vs gp series**: io series is for **mission-critical DBs** with provisioned IOPS. gp is general-purpose.  

- **st1 vs sc1**:  
  - st1 → **frequently accessed** throughput-heavy workloads.  
  - sc1 → **cold/infrequent access** (archival).  

---

# 📂 Introduction to NFS (Network File System)

## 🔹 What is NFS?
- **NFS (Network File System)** is a **distributed file system protocol** developed by Sun Microsystems (1984).  
- It allows a **server** to share directories and files with clients over a **network**.  
- Clients can access files on the server **as if they were stored locally**.  

---

## ⚙️ How NFS Works
1. **Server** exports (shares) a directory using NFS.  
2. **Client** mounts that shared directory over the network.  
3. The client can then **read/write/execute** files as if they exist locally.  

**Example:**  
- Server shares: `/data`  
- Client mounts: `/mnt/data`  
- Client uses it like a normal folder.  

---

## ✨ Features of NFS
- Provides **centralized storage** (store once, use anywhere).  
- Supports **file sharing between multiple clients**.  
- Uses **TCP/UDP protocols** (default TCP on port `2049`).  
- Native support in **Linux/Unix systems**.  
- Allows **permissions and access control**.  

---

## ✅ Advantages
- Easy file sharing in **LAN/WAN**.  
- Reduces storage costs (no need to duplicate data).  
- Good for **centralized backups**.  
- Transparent to users (works like a local folder).  

---

## ⚠️ Disadvantages
- Performance depends on **network speed**.  
- Not suitable for **high-performance applications**.  
- If the **NFS server is down**, clients lose access.  
- Security concerns (requires firewall & authentication).  

---

## 📌 Common Use Cases
- Shared **home directories** in enterprises.  
- **Web servers** sharing common content.  
- **Application servers** accessing shared data.  
- Centralized **backup & storage**.  

---

# ⚖️ Introduction to Load Balancer

## 🔹 What is a Load Balancer?
- A **Load Balancer (LB)** is a networking device/service that **distributes incoming traffic** across multiple servers.  
- Ensures **no single server is overloaded**, improving availability and performance.  
- Acts as a **reverse proxy** between users and backend servers.  

---

## 🚀 Why Use a Load Balancer?
1. **High Availability** → Redirects traffic if a server fails.  
2. **Scalability** → Supports more users by adding servers behind the LB.  
3. **Performance** → Balances workload evenly, avoiding bottlenecks.  
4. **Security** → Hides backend servers’ details from users.  

---

## 🛠️ Types of Load Balancers
1. **Hardware Load Balancer**  
   - Dedicated physical devices (expensive, less flexible).  

2. **Software Load Balancer**  
   - Runs on standard servers (e.g., **Nginx, HAProxy**).  

3. **Cloud-based Load Balancer**  
   - Managed by cloud providers (e.g., **AWS ELB, Azure Load Balancer, GCP LB**).  

---

## 📊 Load Balancing Algorithms
- **Round Robin** → Sends requests to servers one by one.  
- **Least Connections** → Sends traffic to the server with fewest active connections.  
- **IP Hash** → Routes requests based on client IP address.  
- **Weighted Round Robin / Least Connections** → Stronger servers get more requests.  

---

## 🌐 Types of Load Balancing (by OSI Layer)
- **Layer 4 (Transport Layer)**  
  - Balances traffic based on IP & TCP/UDP ports.  
  - Example: **AWS NLB (Network Load Balancer)**.  

- **Layer 7 (Application Layer)**  
  - Balances traffic based on application data (HTTP headers, URLs, cookies).  
  - Example: **AWS ALB (Application Load Balancer)**.  

---

## ✅ Advantages
- Increases **availability** and **reliability**.  
- Provides **scalability** for applications.  
- Improves **fault tolerance** (redirects to healthy servers).  
- Enhances **security** (hides backend servers).  

---

## 🌍 Real-World Examples
- **AWS Elastic Load Balancer (ELB)** → ALB, NLB, GLB.  
- **Nginx / HAProxy** → Open-source software LBs.  
- **F5 Big-IP** → Hardware-based LB.  

---

# ⚖️ AWS Load Balancers and Their Differences

AWS provides multiple types of Load Balancers under **Elastic Load Balancing (ELB)**.  
Each serves different use cases based on performance, routing, and OSI layer.

---

## 🔹 1. Application Load Balancer (ALB)
- **Layer** → Layer 7 (Application Layer)  
- **Routing** → Content-based (URL path, host, headers, cookies)  
- **Use Cases** → Web apps, APIs, Microservices, Path/Host-based routing  
- **Features** → WebSocket support, HTTP/2, container support (ECS/EKS), WAF integration  

---

## 🔹 2. Network Load Balancer (NLB)
- **Layer** → Layer 4 (Transport Layer – TCP/UDP/TLS)  
- **Routing** → Based on IP & Port  
- **Use Cases** → High-performance apps, Gaming, Financial apps, Real-time traffic  
- **Features** → Handles millions of requests/sec, Low latency, Supports static IP & Elastic IPs  

---

## 🔹 3. Classic Load Balancer (CLB)
- **Layer** → Supports both Layer 4 & Layer 7 (limited features)  
- **Routing** → Basic load balancing for HTTP/HTTPS and TCP  
- **Use Cases** → Legacy apps (older workloads)  
- **Features** → Outdated, lacks advanced routing, not recommended for new apps  

---

## 🔹 4. Gateway Load Balancer (GLB)
- **Layer** → Works at Layer 3 (Network Layer)  
- **Routing** → Routes traffic to **third-party virtual appliances** (firewalls, IDS/IPS, deep packet inspection tools)  
- **Use Cases** → Network security, Intrusion detection, Traffic inspection  
- **Features** → Combines **load balancing + gateway**, integrates with vendor appliances, transparent scaling  

---

## 📊 Comparison Table

| Feature | ALB (Application LB) | NLB (Network LB) | CLB (Classic LB) | GLB (Gateway LB) |
|---------|----------------------|------------------|------------------|------------------|
| **OSI Layer** | Layer 7 | Layer 4 | Layer 4 & 7 | Layer 3 |
| **Traffic Type** | HTTP/HTTPS | TCP/UDP/TLS | HTTP/HTTPS & TCP | All traffic (IP packets) |
| **Routing** | Content-based (host, path, headers) | IP & Port-based | Basic routing | Routes to security appliances |
| **Performance** | High (good for apps) | Ultra-high (millions of req/sec) | Moderate (legacy use) | Depends on appliance |
| **Best For** | Web apps, APIs, Microservices | Real-time apps, Gaming, High-throughput | Legacy apps | Security inspection, Firewalls |
| **Special Features** | WAF, HTTP/2, WebSocket | Static IP, Elastic IP | Legacy only | 3rd-party appliances, transparent scaling |
| **AWS Recommendation** | ✅ Modern web & API apps | ✅ High-performance workloads | ❌ Deprecated | ✅ Security-focused use cases |

---

## ✅ Quick Summary
- Use **ALB** → For web apps, APIs, microservices (content-based routing).  
- Use **NLB** → For ultra-high performance, low-latency apps (IP/port-based routing).  
- Use **CLB** → Only for legacy workloads (not recommended for new apps).  
- Use **GLB** → For deploying security appliances (firewalls, IDS/IPS).  

---

# ⚙️ Auto Scaling and Its Types

---

## 🔹 What is Auto Scaling?
- **Auto Scaling** is the process of **automatically adjusting compute capacity** (number of instances/servers) based on traffic demand.  
- Ensures applications always have the **right resources at the right time**:  
  - **Scale Out** → Add more instances when demand increases.  
  - **Scale In** → Remove instances when demand decreases.  

✅ Helps in **cost optimization, high availability, and performance management**.

---

## 🎯 Benefits of Auto Scaling
- **High Availability** → Replaces unhealthy instances automatically.  
- **Elasticity** → Dynamically adjusts resources as per load.  
- **Cost Efficiency** → Saves money by scaling in during low demand.  
- **Reliability** → Ensures consistent performance under varying workloads.  

---

## 🔄 Types of Auto Scaling

### 1️⃣ Dynamic Scaling
- Adjusts resources **in real time** based on CloudWatch metrics.  
- Example: Add 2 instances if CPU > 70% for 5 minutes.  

---

### 2️⃣ Predictive Scaling
- Uses **machine learning** to predict future traffic patterns.  
- Proactively scales resources **before demand increases**.  
- Example: E-commerce app scaling up automatically before sales events or daily peak hours.  

---

### 3️⃣ Scheduled Scaling
- Scales resources based on a **fixed schedule**.  
- Useful when traffic patterns are predictable.  
- Example: Scale up to 10 instances every weekday at 9 AM, scale down at 6 PM.  

---

## ☁️ Auto Scaling in AWS
- Managed by **Amazon EC2 Auto Scaling**.  
- Works with **Elastic Load Balancer (ELB)** to distribute traffic.  
- Supports different scaling policies:  
  - **Target Tracking Scaling** → Keep metric (e.g., CPU at 60%).  
  - **Step Scaling** → Add/remove instances in steps when thresholds are crossed.  
  - **Simple Scaling** → Add/remove instances based on single alarm.  

---

## ✅ Quick Summary
- Auto Scaling = Automatically **adds/removes compute resources**.  
- **Types of Auto Scaling:**  
  - **Dynamic Scaling** → Based on real-time metrics.  
  - **Predictive Scaling** → Based on traffic predictions.  
  - **Scheduled Scaling** → Based on time schedules.  

---

# ⚙️ Strategies: Horizontal vs Vertical Auto Scaling

Auto Scaling can be done in **two main ways**:  

---

## 🔹 Horizontal Auto Scaling (Scale Out / Scale In)
- Increases or decreases the **number of instances/servers**.  
- Example: Add more **EC2 instances** behind a Load Balancer when traffic increases.  
- Used with **Auto Scaling Groups (ASG)** in AWS.  

✅ **Advantages:**  
- High availability (multiple instances).  
- No single point of failure.  
- Easy to scale across regions.  
- Works best for **stateless applications** (like web servers, APIs).  

⚠️ **Disadvantages:**  
- Requires load balancing and session management.  
- Applications must be designed to run on multiple nodes.  

---

## 🔹 Vertical Auto Scaling (Scale Up / Scale Down)
- Increases or decreases the **size/capacity of a single instance** (CPU, RAM, Storage).  
- Example: Change an **EC2 instance** from `t2.micro` → `t3.large`.  

✅ **Advantages:**  
- Easy to implement.  
- No need for multiple servers.  
- Works well for **stateful or legacy applications** that cannot run on multiple nodes.  

⚠️ **Disadvantages:**  
- Downtime may be required when resizing.  
- Limited by the **maximum capacity** of the instance type.  
- Not highly fault-tolerant (single point of failure).  

---

## 📊 Horizontal vs Vertical Scaling – Comparison

| Feature             | Horizontal Scaling          | Vertical Scaling                |
|---------------------|-----------------------------|---------------------------------|
| **Approach**        | Add more instances          | Increase instance size           |
| **Example**         | Add more EC2s               | Upgrade EC2 from t2.micro → t3.large |
| **Fault Tolerance** | High (multiple nodes)       | Low (single node)               |
| **Scalability**     | Virtually unlimited         | Limited by hardware             |
| **Cost**            | Pay for multiple small instances | Pay for a bigger instance   |
| **Best For**        | Stateless apps (web servers, APIs) | Stateful apps (databases, legacy apps) |

---

## ✅ Quick Summary
- **Horizontal Scaling** → Add more machines (scale out/in). Best for **modern, distributed, stateless apps**.  
- **Vertical Scaling** → Make machine bigger (scale up/down). Best for **legacy, stateful apps**.

---


