# - Introduction to Virtualization

#### Virtualization is a technology that allows you to create multiple simulated or virtual environments from a single physical machine, making more efficient use of the machine's resources. Using specialized software—commonly called a hypervisor—virtualization divides a single physical system’s components such as processors, memory, storage, and networks into multiple virtual machines (VMs), each behaving like an independent computer with its own operating system and applicationa

#### Key concepts:

- Virtual Machine (VM): A VM is a software-created computing environment that acts just like a separate physical device; it runs its own OS and applications independently from other VMs, even if they all share the same physical hardware.

- Hypervisor: This is the software layer that manages multiple VMs, ensuring each gets its required resources and is isolated from the others. There are two main types: Type 1 (runs directly on hardware) and Type 2 (runs inside an existing operating system).

- Benefits: Virtualization enables organizations and individuals to optimize hardware use, increase IT flexibility and scalability, reduce operational costs, and improve disaster recovery and security by isolating environments from one another.

- Use cases: Virtualization is foundational in enterprise IT, powering modern data centers and cloud services, and is used in server consolidation, desktop virtualization, test and development, and more

- # - Virtualization vs Cloud

## Comparison Table

| Aspect            | Virtualization                                                                 | Cloud Computing                                                                                 |
|-------------------|----------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| **Definition**     | Technology that creates multiple virtual machines from one physical system       | Service model delivering IT resources over the internet, built on virtualization                 |
| **Primary Purpose**| Maximizing hardware utilization and system isolation                             | Providing scalable, flexible, on-demand services, infrastructure, and platforms                  |
| **How it Works**   | Uses a hypervisor to divide and manage hardware among virtual machines           | Pools virtualized resources and makes them available via self-service portals                    |
| **Control**        | High degree of control by the user over virtual environments                     | Control over underlying hardware is abstracted; users manage only consumed resources             |
| **Example**        | Running multiple operating systems on one server                                 | Using AWS EC2, Google Drive, or Office 365 services                                              |
| **Scalability**    | Scaling limited by physical hardware (“scale up”)                                | Highly scalable, can “scale out” by pooling multiple resources automatically                     |
| **Flexibility**    | Less flexible, more manual configuration                                         | Very flexible, automated provisioning and orchestration                                          |
| **Cost Structure** | Lower ongoing costs, but potential higher upfront investment                     | Pay-as-you-go or subscription, may reduce hardware costs, but OPEX can scale with use           |
| **Tenancy**        | Usually single-tenant (dedicated per user/system)                                | Often multi-tenant (shared resources among many users)                                           |
| **Typical Deployment** | On-premises servers or data centers                                      | Public, private, or hybrid deployments via remote/cloud providers                                |
| **Storage**        | Limited to physical server’s capacity                                            | Practically unlimited, pooled across many data centers/providers                                 |

## Summary

- **Virtualization** is ideal for maximizing existing hardware and creating isolated environments.
- **Cloud Computing** builds on virtualization, offering greater scalability, automation, and service accessibility via the internet.

# - Cloud Models (IAAS, PAAS, SAAS)

#### Cloud models in computing are categorized primarily into three service models: IaaS (Infrastructure as a Service), PaaS (Platform as a Service), and SaaS (Software as a Service). These models differ by the level of control, management, and the delivered resources.

## Comparison Table

| Model   | What it Delivers                                            | Managed By Provider                       | Managed By User                          | Example Uses                            | Typical Examples                                      |
|---------|--------------------------------------------------------------|-------------------------------------------|------------------------------------------|------------------------------------------|--------------------------------------------------------|
| **IaaS** | Virtualized infrastructure: servers, storage, networking     | Physical infrastructure                    | OS, middleware, applications, data        | Hosting virtual machines, storage, network management | AWS EC2, Google Cloud Compute, Azure VMs               |
| **PaaS** | Application development platform, runtime, tools            | Infrastructure, OS, platform, runtime      | Applications, data                        | Application development, web app hosting | Google App Engine, Heroku, Microsoft Azure App Service |
| **SaaS** | Fully functional software over the internet                 | Everything (infrastructure, app)           | Only configuration and user data          | Email, CRM, office suites                 | Gmail, Salesforce, Dropbox, Google Workspace           |

## Summary

- **IaaS**: Offers maximum control over infrastructure. Ideal for system administrators and developers who want to manage VMs, networks, and storage.
- **PaaS**: Offers a pre-configured platform for developers to build and deploy applications without managing underlying systems.
- **SaaS**: Delivers fully operational software directly to end users. No infrastructure or platform management required.

# - AWS Account creation

To create an AWS account, follow these structured steps—these apply whether you're using the Free Tier or starting a business account, and are current as of 2025:

Go to the AWS Signup Page

Visit aws.amazon.com and click "Create an AWS Account".

Enter Your Account Details

Provide a valid email address, set an AWS account name, and create a strong root user password. You’ll then receive an email verification code—enter this to proceed.

Add Contact Information

Choose between "Personal" or "Business" account type. Enter full name, contact number, address, and other required details. Accept the AWS Customer Agreement to continue.

Payment Method

Add your billing information. Even for Free Tier, a valid payment card is required for verification (AWS won’t charge unless usage exceeds Free Tier limits).

Identity Verification

Choose a verification method (usually your phone). Receive a verification code by text or call, and enter the code as prompted.

Select a Support Plan

Choose from available support plans. The Basic Support plan is free and sufficient for most new users.

Complete Signup

Submit the form. Account activation may take a few minutes to 24 hours. AWS will send a confirmation email when activation is complete
