# - Region vs Availability Zone (AZ)

## Comparison Table

| Feature              | AWS Region                                                                     | AWS Availability Zone (AZ)                                                  |
|----------------------|----------------------------------------------------------------------------------|------------------------------------------------------------------------------|
| **Geographic Scope** | Broad geographic area (e.g., a state, country, or large region)                 | Smaller distinct locations within a Region (multiple data centers)           |
| **Number**           | AWS has multiple Regions worldwide                                              | Each Region has multiple AZs (typically 3 or more)                           |
| **Purpose**          | Geographic distribution for latency, compliance, disaster recovery              | Fault isolation and high availability within a Region                       |
| **Isolation**        | Fully isolated from other Regions                                               | Isolated from other AZs but connected via low-latency links                  |
| **Use Case**         | Deploy data and services closer to users globally                               | Deploy redundant systems for high availability and failover within a Region |

## Why It Matters

- **Use Regions** to:
  - Distribute applications globally.
  - Reduce latency for international users.
  - Meet data residency and compliance requirements.

- **Use AZs** to:
  - Increase **fault tolerance** and **high availability**.
  - Deploy redundant infrastructure within the same Region.
  - Minimize the impact of failures isolated to a single data center or AZ.

## Related Questions

- How do Regions and AZs impact application latency and fault tolerance?
- Is there a practical limit to deploying across multiple AZs within a Region?
- How do inter-region communication features challenge AWS's "complete isolation" claim?
- What are the operational differences between managing resources in a Region versus an AZ?
- How does the geographic distribution of AZs affect disaster recovery planning?

---

# 🌐 CIDR Calculation for Subnets

---

## 🔹 What is CIDR?
- **CIDR (Classless Inter-Domain Routing)** defines IP address allocation and routing.  
- Format:

Example: `192.168.1.0/24`  

Here `/24` means **24 bits** for the network and the rest for hosts.

---

## 🔹 Subnetting Basics
- Each subnet is created by **borrowing host bits** to use as **network bits**.  
- The **prefix length (/n)** determines:  
- **Number of subnets**  
- **Number of hosts per subnet**

---

## 🔹 Formula for Hosts

- `-2` because the first address = **Network ID** and the last = **Broadcast Address**.

---

## 🔹 Example Calculations

### Example 1: `192.168.1.0/24`
- Prefix length = `/24` → 32 - 24 = 8 host bits  
- Hosts = 2^8 - 2 = **254**  
- Subnet Mask = `255.255.255.0`  
- Network ID = `192.168.1.0`  
- First Usable = `192.168.1.1`  
- Last Usable = `192.168.1.254`  
- Broadcast = `192.168.1.255`  

---

### Example 2: `10.0.0.0/16`
- Prefix length = `/16` → 32 - 16 = 16 host bits  
- Hosts = 2^16 - 2 = **65,534**  
- Subnet Mask = `255.255.0.0`  
- Network ID = `10.0.0.0`  
- First Usable = `10.0.0.1`  
- Last Usable = `10.0.255.254`  
- Broadcast = `10.0.255.255`  

---

### Example 3: `172.16.0.0/20`
- Prefix length = `/20` → 32 - 20 = 12 host bits  
- Hosts = 2^12 - 2 = **4,094**  
- Subnet Mask = `255.255.240.0`  
- Network ID = `172.16.0.0`  
- First Usable = `172.16.0.1`  
- Last Usable = `172.16.15.254`  
- Broadcast = `172.16.15.255`  

---

## 📊 Quick Reference Table

| CIDR | Subnet Mask     | Hosts/Subnet |
|------|-----------------|--------------|
| /30  | 255.255.255.252 | 2            |
| /29  | 255.255.255.248 | 6            |
| /28  | 255.255.255.240 | 14           |
| /27  | 255.255.255.224 | 30           |
| /26  | 255.255.255.192 | 62           |
| /24  | 255.255.255.0   | 254          |
| /20  | 255.255.240.0   | 4,094        |
| /16  | 255.255.0.0     | 65,534       |

---

## ✅ Summary
- CIDR defines **network vs host bits**.  
- **Smaller prefix (/30, /29)** → fewer hosts per subnet.  
- **Larger prefix (/16, /12)** → more hosts per subnet.

- `-2` because the first address = **Network ID** and the last = **Broadcast Address**.

---

## 🔹 Example Calculations

### Example 1: `192.168.1.0/24`
- Prefix length = `/24` → 32 - 24 = 8 host bits  
- Hosts = 2^8 - 2 = **254**  
- Subnet Mask = `255.255.255.0`  
- Network ID = `192.168.1.0`  
- First Usable = `192.168.1.1`  
- Last Usable = `192.168.1.254`  
- Broadcast = `192.168.1.255`  

---

### Example 2: `10.0.0.0/16`
- Prefix length = `/16` → 32 - 16 = 16 host bits  
- Hosts = 2^16 - 2 = **65,534**  
- Subnet Mask = `255.255.0.0`  
- Network ID = `10.0.0.0`  
- First Usable = `10.0.0.1`  
- Last Usable = `10.0.255.254`  
- Broadcast = `10.0.255.255`  

---

### Example 3: `172.16.0.0/20`
- Prefix length = `/20` → 32 - 20 = 12 host bits  
- Hosts = 2^12 - 2 = **4,094**  
- Subnet Mask = `255.255.240.0`  
- Network ID = `172.16.0.0`  
- First Usable = `172.16.0.1`  
- Last Usable = `172.16.15.254`  
- Broadcast = `172.16.15.255`  

---

## 📊 Quick Reference Table

| CIDR | Subnet Mask     | Hosts/Subnet |
|------|-----------------|--------------|
| /30  | 255.255.255.252 | 2            |
| /29  | 255.255.255.248 | 6            |
| /28  | 255.255.255.240 | 14           |
| /27  | 255.255.255.224 | 30           |
| /26  | 255.255.255.192 | 62           |
| /24  | 255.255.255.0   | 254          |
| /20  | 255.255.240.0   | 4,094        |
| /16  | 255.255.0.0     | 65,534       |

---

## ✅ Summary
- CIDR defines **network vs host bits**.  
- **Smaller prefix (/30, /29)** → fewer hosts per subnet.  
- **Larger prefix (/16, /12)** → more hosts per subnet.

---

# 🌐 Create Internet Gateway (IGW) and Route

---

## 🔹 What is an Internet Gateway (IGW)?
- **Internet Gateway (IGW)** is a VPC component that allows communication between **VPC instances** and the **Internet**.  
- It provides **NAT (Network Address Translation)** for instances with public IPs.  
- Required for creating **public subnets**.

---

## 🔹 Steps to Create IGW and Route

### **Step 1: Create Internet Gateway**
1. Open **VPC Console** in AWS.  
2. Navigate to **Internet Gateways → Create internet gateway**.  
3. Provide a **Name tag** (e.g., `My-IGW`).  
4. Click **Create**.  

---

### **Step 2: Attach IGW to VPC**
1. Select the created **IGW**.  
2. Go to **Actions → Attach to VPC**.  
3. Choose your **VPC** (e.g., `My-VPC`).  
4. Click **Attach**.  

---

### **Step 3: Create Route to Internet**
1. Open **Route Tables**.  
2. Select the **Route Table** associated with your **Public Subnet**.  
3. Edit Routes → **Add Route**:  
   - **Destination:** `0.0.0.0/0` (for IPv4)  
   - **Target:** Select the **Internet Gateway (IGW)**  
4. Save changes.  

---

### **Step 4: Associate Route Table with Public Subnet**
1. Select the **Route Table**.  
2. Open **Subnet Associations → Edit subnet associations**.  
3. Select your **Public Subnet** (e.g., `Subnet-1`).  
4. Save.  

---

## ✅ Result
- Instances in the **Public Subnet** with a **public IP** can now access the Internet.  
- Traffic flows **outbound and inbound** through the **IGW**.  

---

## 📊 Quick Reference

| Component            | Purpose                                         |
|----------------------|-------------------------------------------------|
| **Internet Gateway** | Enables internet access for the VPC             |
| **Route Table**      | Defines traffic flow (e.g., `0.0.0.0/0` → IGW) |
| **Public Subnet**    | Subnet with route to IGW via Route Table        |

---

# 🌐 NAT Gateway in AWS

---

## 🔹 What is a NAT Gateway?
- **NAT (Network Address Translation) Gateway** is an AWS-managed service that allows **private subnet instances** to connect to the Internet **outbound only**.  
- Prevents direct inbound traffic from the Internet, ensuring **security**.  
- Highly available within an **Availability Zone (AZ)**.  

---

## 🔹 Why NAT Gateway?
- Instances in **private subnets** cannot access the Internet directly.  
- NAT Gateway enables:
  - Downloading patches/updates from the Internet.  
  - Accessing external APIs securely.  

---

## 🔹 Steps to Create a NAT Gateway

### **Step 1: Create an Elastic IP**
1. Go to **VPC Console → Elastic IPs**.  
2. Allocate a new Elastic IP (EIP).  

---

### **Step 2: Create a NAT Gateway**
1. Navigate to **NAT Gateways → Create NAT Gateway**.  
2. Choose a **Public Subnet** (must have IGW attached).  
3. Assign the **Elastic IP (EIP)**.  
4. Click **Create**.  

---

### **Step 3: Update Route Table for Private Subnet**
1. Go to **Route Tables**.  
2. Select the **Route Table** linked with your **Private Subnet**.  
3. Edit Routes → Add Route:  
   - **Destination:** `0.0.0.0/0`  
   - **Target:** Select the **NAT Gateway**  
4. Save.  

---

## ✅ Result
- Instances in **Private Subnet** can access the Internet **outbound only**.  
- Inbound traffic from Internet is **blocked**.  

---

## 📊 Comparison: IGW vs NAT Gateway

| Feature              | Internet Gateway (IGW)              | NAT Gateway                        |
|----------------------|--------------------------------------|------------------------------------|
| Subnet Type          | Public Subnet                       | Private Subnet                     |
| Traffic Direction    | Inbound & Outbound (Public IPs)      | Outbound only (No inbound allowed) |
| Use Case             | Public-facing apps/websites          | Secure internal servers/DBs        |
| Elastic IP Needed?   | No (optional for EC2 public IP)      | Yes                                |

---

# 🔗 VPC Peering in AWS

---

## 🔹 What is VPC Peering?
- **VPC Peering** is a networking connection between **two Virtual Private Clouds (VPCs)** that enables routing of traffic between them.  
- Allows instances in different VPCs to communicate **as if they are in the same network**.  
- Uses **private IP addresses**; traffic does **not go over the Internet**.  

---

## 🔹 Key Features
- Connects **VPCs in same or different AWS accounts/regions**.  
- **One-to-one relationship** (no transitive peering).  
- No bandwidth bottleneck – traffic flows directly.  
- Supports **IPv4 and IPv6**.  

---

## 🔹 Steps to Create VPC Peering

### **Step 1: Create VPC Peering Connection**
1. Open **VPC Console → Peering Connections → Create Peering Connection**.  
2. Enter:  
   - **Requester VPC ID** (your VPC).  
   - **Accepter VPC ID** (peer VPC, same/different account).  
3. Click **Create Peering Connection**.  

---

### **Step 2: Accept Peering Request**
1. Go to **Peering Connections** in the **Accepter VPC** account.  
2. Select the request → **Accept Request**.  

---

### **Step 3: Update Route Tables**
1. Go to **Route Tables** of both VPCs.  
2. Add route:  
   - **Destination:** CIDR block of the peer VPC.  
   - **Target:** VPC Peering Connection.  
3. Save.  

---

### **Step 4: Update Security Groups (if needed)**
- Allow inbound/outbound traffic from the **peer VPC CIDR** in Security Groups.  

---

## ✅ Result
- Instances in both VPCs can now **communicate privately** using their private IPs.  

---

## 📊 Limitations of VPC Peering
- No **transitive peering** (VPC-A ↔ VPC-B, VPC-B ↔ VPC-C does **not** mean VPC-A ↔ VPC

# 🔌 NIC (ENI) vs 🌐 Elastic IP (EIP) in AWS

---

## 🔹 What is a NIC (ENI)?
- **NIC** = **Elastic Network Interface (ENI)**  
- A **virtual network card** attached to an EC2 instance.  
- Contains:  
  - Private IP(s)  
  - Security groups  
  - MAC address  
  - Elastic IP (optional)  

📌 **Think of ENI like the "LAN card" of your EC2 instance.**

---

## 🔹 What is an Elastic IP (EIP)?
- **Elastic IP** is a **static IPv4 address** allocated by AWS.  
- It can be attached to:  
  - An EC2 instance (via ENI)  
  - A NAT Gateway  
- Remains the same even if instance restarts.  

📌 **Think of EIP like a permanent public IP you can attach/detach.**

---

## 📊 Difference Between NIC (ENI) and Elastic IP (EIP)

| Feature              | NIC (ENI)                                        | Elastic IP (EIP)                          |
|----------------------|--------------------------------------------------|-------------------------------------------|
| Definition           | Virtual network interface card for EC2           | Static public IPv4 address                 |
| Scope                | Private networking inside VPC                    | Public Internet accessibility              |
| Usage                | Attach to EC2 for private/public communication   | Map to ENI/EC2 for fixed public IP         |
| IP Type              | Private IP (mandatory) + Public/EIP (optional)   | Public IPv4 only                           |
| Persistence          | Exists independently of EC2 (can detach/attach)  | Remains with account until released        |
| Example              | Like your **network card** in a laptop           | Like your **static broadband IP** at home |

---

## ✅ Summary
- **ENI (NIC)** = The *device* that holds IPs (private + optional public/EIP).  
- **EIP** = A *fixed public IP* that can be attached to an ENI.

# 🗂️ Placement Groups in AWS

---

## 🔹 What is a Placement Group?
- A **Placement Group** in AWS determines **how EC2 instances are placed** within the underlying hardware.  
- Helps optimize **network performance, fault tolerance, or latency** based on workload needs.  

---

## 🔹 Types of Placement Groups

### 1️⃣ Cluster Placement Group
- Packs instances close together **within a single AZ**.  
- Provides **high throughput & low latency** (10 Gbps+).  
- Best for **HPC (High-Performance Computing)**, **big data**, **real-time analytics**.  
- ❌ Not fault-tolerant (since all in one AZ).  

---

### 2️⃣ Spread Placement Group
- Places instances **across different racks** (different underlying hardware).  
- Ensures **high availability** – no two instances share the same rack.  
- Best for **critical applications** where each instance must be isolated.  
- Supports only a **limited number of instances per AZ** (7 instances per AZ).  

---

### 3️⃣ Partition Placement Group
- Divides instances into **logical partitions**.  
- Each partition has its own set of racks (no overlap).  
- Good for **large distributed workloads** like Hadoop, Cassandra, Kafka.  
- Balances **performance + fault isolation**.  

---

## 📊 Difference Between Placement Groups

| Feature              | Cluster Placement Group               | Spread Placement Group                      | Partition Placement Group              |
|----------------------|---------------------------------------|---------------------------------------------|----------------------------------------|
| Placement Strategy   | Instances close together (1 AZ)       | Instances spread across racks               | Instances divided into logical partitions |
| Performance          | ✅ High (low latency, high throughput)| ❌ Lower than Cluster                       | ⚖️ Medium (depends on partition size)   |
| Fault Tolerance      | ❌ Low (all in one AZ)                 | ✅ Very High (isolated racks)                | ✅ High (partition isolation)            |
| Best Use Case        | HPC, Big Data, Analytics              | Critical small apps (DBs, etc.)             | Large-scale distributed systems         |
| Limitations          | Single AZ only                        | Max 7 instances per AZ                      | Must define partitions                  |

---

## ✅ Summary
- **Cluster** = Performance focus 🚀  
- **Spread** = High availability 🔒  
- **Partition** = Balance of scale + isolation ⚖️

---

# 🔐 NACL vs Security Group in AWS

---

## 🔹 Security Group (SG)
- Acts as a **virtual firewall** for **EC2 instances**.  
- Works at the **instance level**.  
- **Stateful** → If you allow inbound traffic, outbound is automatically allowed.  
- Supports **only allow rules** (no deny).  

---

## 🔹 Network ACL (NACL)
- Acts as a **firewall for subnets** within a VPC.  
- Works at the **subnet level**.  
- **Stateless** → Inbound and outbound rules must be defined separately.  
- Supports **allow and deny rules**.  

---

## 📊 Difference Between NACL and Security Group

| Feature                | Security Group (SG)                        | Network ACL (NACL)                     |
|------------------------|---------------------------------------------|-----------------------------------------|
| Level                  | Instance level (EC2)                       | Subnet level                            |
| Stateful/Stateless     | ✅ Stateful                                | ❌ Stateless                            |
| Rules                  | Only **Allow** rules                       | Both **Allow** and **Deny** rules       |
| Default Behavior       | Deny all inbound, allow all outbound        | Allow all inbound & outbound by default |
| Scope                  | Applied to ENI (NIC) → Instance            | Applied to Subnet (all instances inside)|
| Evaluation Order       | All rules are evaluated together            | Rules evaluated in number order         |
| Best Use Case          | Controlling instance access                 | Controlling subnet-level traffic        |

---

## ✅ Summary
- **Security Groups** = Control traffic at the **instance level** (stateful, allow-only).  
- **NACLs** = Control traffic at the **subnet level** (stateless, allow + deny).  
- Best practice → Use **both together** for layered security.  
