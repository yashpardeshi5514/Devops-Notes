# - Introduction to AWS Dashboard

#### The AWS Dashboard—more formally known as the AWS Management Console—is the web-based user interface you use to interact with Amazon Web Services. It is the starting point for managing all your AWS resources and services.

#### Homepage Overview

- Shows frequently used services, recent activity, account information, and any important notifications.

#### Service Navigation

- All AWS services (like EC2, S3, IAM, Lambda, RDS, etc.) are listed and searchable from the “Services” menu at the top.

- You can also group and pin your favorite services for quick access.

#### Global Controls

- Easily switch between AWS Regions (geographical server locations) from the top-right menu. This is essential because many services are region-specific.

- Access account settings, billing, support, and user information from the upper-right menu as well.

#### Service Dashboards

- Each AWS service has its own dedicated dashboard for management and monitoring (for example, the EC2 dashboard shows running instances, S3 dashboard shows buckets, etc.).

- These dashboards provide “Create,” “Manage,” “Delete,” and “Monitor” actions for respective resources.

#### Resource Search

- Powerful search bar at the top to quickly locate services, documentation, or specific resources.

#### Additional Tools

- CloudShell: Browser-based command-line terminal to manage resources using AWS CLI.

- Resource Groups & Tag Editor: Lets you organize and manage resources across services and regions.

- Billing Dashboard: One-stop place for monitoring costs, setting budgets, and checking usage.

#### Security & Notifications

- View security alerts, compliance notifications, and service health at a glance.

#  Benefits

- Ease of Use: No command-line knowledge is needed; point-and-click interface with helpful wizards.

- Centralized Management: Manage all cloud resources, billing, monitoring, security, and user permissions from one place.

- Real-time Updates: Get live status of all your resources and service health.

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

- Once running, connect using SSH with the provided .pem key file. Example command:
  
      ssh -i /path/to/my-key.pem ubuntu@your-ec2-public-ip

