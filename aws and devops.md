# 🚀 DevOps & AWS Interview Questions
> Curated, deduplicated, and organized by tool and domain. Includes scenario-based and most frequently asked questions sourced from real interviews (2025–26).

---

## 📋 Table of Contents
1. [Kubernetes](#-kubernetes)
2. [Docker & Containers](#-docker--containers)
3. [Helm](#-helm)
4. [Terraform & IaC](#-terraform--infrastructure-as-code)
5. [Ansible & Configuration Management](#-ansible--configuration-management)
6. [CI/CD & Jenkins](#-cicd--jenkins)
7. [GitHub Actions & GitLab CI/CD](#-github-actions--gitlab-cicd)
8. [Git & Release Management](#-git--release-management)
9. [AWS](#-aws)
10. [Monitoring & Observability](#-monitoring--observability)
11. [Security & DevSecOps](#-security--devsecops)
12. [Linux & Troubleshooting](#-linux--troubleshooting)
13. [Scripting & Automation](#-scripting--automation)
14. [Disaster Recovery & Reliability](#-disaster-recovery--reliability)
15. [GCP](#-gcp)
16. [Behavioral & Leadership](#-behavioral--leadership)
17. [Scenario-Based Questions (Cross-Tool)](#-scenario-based-questions-cross-tool)
18. [Quick Reference: Most Frequently Asked](#-quick-reference-most-frequently-asked)

---

## ☸️ Kubernetes

### Core Concepts

1. What is Pod Intent in Kubernetes?
2. What is the role of the control plane and worker nodes in Kubernetes?
3. What is the difference between ClusterIP, NodePort, and LoadBalancer services?
4. How can a ClusterIP service still be accessed from outside the cluster?
5. How do you expose applications to external traffic in Kubernetes?
6. What is the difference between liveness and readiness probes, and when would each fail?
7. How do you define Kubernetes objects — Deployments, Services, ConfigMaps, Secrets?
8. How do you check the version of a running deployment or pod image?
9. How do you exec into a running pod and debug it interactively?
10. What is the difference between a Deployment, StatefulSet, and DaemonSet?
11. What is the purpose of a Kubernetes Namespace?
12. What are Init Containers and when would you use them?

### Deployments & Scaling

13. What is a Canary Deployment and how do you implement it in Kubernetes?
14. How does Rollback Deployment work internally — what commands are involved?
15. How do you implement zero-downtime deployments in Kubernetes?
16. What is HPA (Horizontal Pod Autoscaler) and how does it scale pods?
17. What is VPA (Vertical Pod Autoscaler) and how does it differ from HPA?
18. What is the difference between HPA, KEDA, and Karpenter?
19. Why do we still need HPA if Karpenter is being used?
20. How do rolling updates work internally and how do you tune `maxSurge` and `maxUnavailable`?
21. How do you perform node maintenance (drain, cordon) without impacting running applications?

### Networking & Security

22. How does Service A communicate with Service B inside a Kubernetes cluster?
23. What are the types of Kubernetes Network Policies?
24. How would you restrict pod-to-pod communication using Calico Network Policies?
25. How does a pod securely connect to AWS S3 without hardcoding credentials (IRSA / OIDC)?
26. How do you implement RBAC policies in Kubernetes?
27. How do you restrict developer access across specific namespaces?
28. What is a ServiceAccount and how is it used for fine-grained pod permissions?
29. What is a Pod Security Standard and why does it matter?

### Troubleshooting

30. A pod is stuck in `CrashLoopBackOff`. Walk me through your troubleshooting steps.
31. Pods are in `Pending` state. What are the possible reasons?
32. A deployment rollout failed. How do you identify the issue and roll back safely?
33. A service is running but traffic is not reaching the pods. How do you debug?
34. One node shows `NotReady`. How do you investigate and fix it?
35. A pod is getting `OOMKilled`. How do you analyze and resolve it?
36. What causes `ImagePullBackOff` and how do you resolve it?
37. Logs are missing for a crashing pod. How do you retrieve previous container logs?
38. Cluster CPU usage is high but applications seem normal. How do you troubleshoot?
39. A namespace was accidentally deleted. What is the impact and how do you recover?
40. Where are Kubernetes logs generated and stored, and how does Kubernetes locate them?
41. How do you fetch logs older than the current container's lifecycle (e.g., 1 month+)?

### High Availability & Observability

42. How do you design high availability for stateful applications in Kubernetes?
43. How do you monitor and alert on Kubernetes application health?
44. How do you securely manage secrets and configs in Kubernetes at scale?
45. How do you create and manage Kubernetes clusters using Terraform?
46. How do you set up an alert policy in GKE if any pod crashes?

---

## 🐳 Docker & Containers

1. What are the stages involved in building a Docker image?
2. What is the difference between `ENTRYPOINT` and `CMD` in a Dockerfile?
3. How do multi-stage Docker builds work and why are they used?
4. How do you pass environment variables during Docker image build and at runtime?
5. How do you perform Docker image vulnerability scanning during build time and at the registry level?
6. Which security tools have you used for image scanning (Trivy, Snyk, Clair, Grype)?
7. Which container registries do you use (ECR, Docker Hub, GCR, Harbor)?
8. What is the command used to connect to a running ECS container?
9. How do you reduce the size of a Docker image in production?
10. What is Docker layer caching and how does it affect build performance?
11. Your Docker container keeps restarting after deployment. How do you troubleshoot?
12. What is the difference between `docker stop` and `docker kill`?
13. How do you manage secrets in Docker without baking them into images?

---

## ⚓ Helm

1. Explain the folder structure of a Helm chart.
2. What are `values.yaml`, `Chart.yaml`, and templates — what role does each play?
3. What is the difference between `helm install`, `helm upgrade`, and `helm rollback`?
4. What are Helm hooks and when would you use them?
5. How do you handle deployment failures and rollbacks using Helm?
6. How do you manage environment-specific configs with Helm (dev/staging/prod)?
7. What is Helm chart signing (Provenance) and which tools are used?
8. What is the key difference between Helm 2 and Helm 3 (removal of Tiller)?

---

## 🔧 Terraform & Infrastructure as Code

### Core Concepts

1. What is the difference between Terraform, Ansible, and CloudFormation?
2. What is a Terraform provider and why is it required?
3. What is the Terraform state file and why must it be stored securely?
4. What is `terraform plan` and why should you always run it before `apply`?
5. What are Terraform modules and how do they promote reusability?
6. What is `terraform taint` and when would you use it?
7. What is `terraform import` and in which real-world scenario is it used?
8. How does Terraform handle dependencies between resources?
9. What is the difference between `count` and `for_each` in Terraform?
10. What are Terraform data sources and how are they used?

### State & Workspaces

11. What are Terraform Workspaces and when should you use them?
12. How does Terraform state management work internally?
13. How do you manage Terraform state in a team environment (S3 backend + DynamoDB locking)?
14. What is state drift and how does Terraform detect and remediate it?
15. How do you handle a Terraform state file that becomes corrupted or out-of-sync?

### Advanced & Scenario-Based

16. Your Terraform script fails mid-way through creating AWS resources. How do you debug and recover?
17. How do you implement a blue-green deployment strategy using Terraform?
18. How do you implement `create_before_destroy` and when is it critical?
19. How do you handle sensitive values (passwords, keys) in Terraform configurations?
20. How do you structure Terraform for a large organization with multiple environments and teams?

---

## 🤖 Ansible & Configuration Management

1. What is Ansible and how does it differ from Terraform in scope?
2. What is the difference between a Playbook, a Role, and an Ad-hoc command?
3. What is idempotency in Ansible and why does it matter?
4. What are Ansible Facts and how are they used in playbooks?
5. What is the Ansible inventory file and what are its formats (static vs. dynamic)?
6. What is an Ansible Handler and when does it trigger?
7. What are Ansible Roles and how are they structured?
8. What is Ansible Galaxy and how do you use it to manage collections?
9. How does Ansible use SSH to connect to managed nodes — is an agent required?
10. What is `ansible-vault` and how do you use it to protect sensitive data?
11. What is the difference between `when`, `register`, and `with_items` in a playbook?
12. How do you use Ansible to manage Kubernetes workloads (the `k8s` module)?
13. How would you use Ansible to configure 500 servers simultaneously and safely?
14. **Scenario:** An Ansible playbook runs successfully on 400 out of 500 servers. The remaining 100 fail silently. How do you identify and remediate them?

---

## 🔁 CI/CD & Jenkins

### Pipeline Design

1. Explain your end-to-end CI/CD workflow from code commit to production.
2. Which type of Jenkins pipeline do you use (Declarative vs. Scripted) and why?
3. What is the difference between Declarative and Scripted Jenkins pipelines?
4. How do you define and trigger Jenkins pipelines (SCM polling, webhooks, manual)?
5. What stages do you define to ensure code quality (lint, test, scan, build, deploy)?
6. What is the difference between Continuous Integration, Continuous Delivery, and Continuous Deployment?

### Jenkins Features

7. What are Jenkins Shared Libraries? How are they structured and loaded in Jenkinsfiles?
8. How do you design and reuse Jenkins Shared Libraries across multiple projects?
9. What is a Jenkins agent/slave and how does the master-slave architecture work?
10. What is a webhook and how is it configured in a CI/CD pipeline?
11. If a Jenkins pipeline runs but the build does not trigger, what could be the reasons?
12. How do you pass secrets into a Jenkins pipeline securely (Credentials plugin, Vault)?

### Build & Deployment

13. What types of applications have you deployed using Jenkins pipelines?
14. Which deployment tools have you used (Docker, Kubernetes, Helm, Terraform, Ansible)?
15. How do you implement parallel stages in a Jenkins pipeline?
16. How do you archive artifacts and publish test reports in Jenkins?

### Scenario-Based

17. **Scenario:** Your CI pipeline completes successfully, but artifacts are missing in the repository. How do you debug?
18. **Scenario:** A developer's push broke the main branch build. How do you isolate and fix it without blocking others?
19. **Scenario:** Your Jenkins master is down. How do you recover pipelines and minimize downtime?

---

## ⚙️ GitHub Actions & GitLab CI/CD

1. What is the structure of a GitHub Actions workflow file?
2. What is the difference between a GitHub Actions `job` and a `step`?
3. What are GitHub Actions Runners (hosted vs. self-hosted) and when do you use each?
4. How do you manage secrets in GitHub Actions?
5. What are reusable workflows in GitHub Actions and how do they compare to Jenkins Shared Libraries?
6. How do you implement matrix builds in GitHub Actions for multi-version testing?
7. What is the difference between GitHub Actions and GitLab CI/CD pipelines?
8. How do you use GitLab CI/CD environments (dev/staging/prod) and protection rules?
9. How do you cache dependencies in GitHub Actions to speed up workflows?
10. How do you trigger a GitHub Actions workflow only when specific file paths change?

---

## 🌿 Git & Release Management

1. Which branching strategy do you follow (GitFlow vs. Trunk-based) and how do you avoid breaking the release branch?
2. If a critical bug is found in production, what is your hotfix approach?
3. What is the difference between `git merge`, `git rebase`, and `git cherry-pick`?
4. What is `git bisect` and how do you use it to identify a regression?
5. How do you revert a commit that has already been pushed to a shared branch?
6. What is a Pull Request / Merge Request and what are the best practices around them?
7. How do you enforce commit message conventions and code review policies in a team?
8. What is semantic versioning (SemVer) and how do you apply it in release pipelines?

---

## ☁️ AWS

### Networking

1. What is the difference between ALB and NLB — when do you choose each?
2. What is the difference between NAT Gateway, NAT Instance, Egress-Only Internet Gateway, and Internet Gateway?
3. How do you communicate with AWS services privately without going through the internet (VPC Endpoints)?
4. How would you redirect traffic from `x.company.in` to `company.in/x` using AWS services?
5. What is the difference between a Launch Template and a Launch Configuration?
6. What is the difference between a stateful and a stateless firewall — Security Groups vs. NACLs?
7. What is AWS Route 53 and how does it handle DNS failover?
8. What is a Transit Gateway and when would you use it over VPC Peering?
9. What is AWS PrivateLink and how does it differ from VPC Endpoints?
10. How does AWS Global Accelerator differ from CloudFront?

### Compute & Auto Scaling

11. How does EC2 Auto Scaling work — what triggers a scale-out vs. scale-in event?
12. What is the difference between EC2 On-Demand, Reserved, Spot, and Savings Plans?
13. **Scenario:** Your web app is behind an ALB with Auto Scaling. During peak hours, users report 503 errors and high latency. How do you troubleshoot?
14. **Scenario:** Your EC2 instances in an Auto Scaling Group are being replaced too frequently. What could be wrong?
15. What is the difference between Vertical and Horizontal Scaling in AWS?

### Storage & Database

16. What is the difference between EBS and EFS — when do you use each?
17. What is the difference between RDS, Aurora, and a self-managed database on EC2?
18. How do you perform an RDS database upgrade without downtime?
19. Your database performs well initially but slows down significantly after several months. How do you troubleshoot and fix it?
20. What is the difference between RDS Multi-AZ and Read Replicas?
21. What is AWS DynamoDB and when would you choose it over RDS?
22. What is an S3 lifecycle policy and how does it help with cost optimization?

### IAM & Security

23. How do you securely store and manage AWS credentials in production?
24. What is IAM Role vs. IAM User vs. IAM Group — when do you use each?
25. What is the principle of least privilege and how do you apply it in IAM policies?
26. What is AWS STS (Security Token Service) and when is it used?
27. How does AWS Secrets Manager differ from Systems Manager Parameter Store?
28. What is AWS KMS and how do you use it to encrypt data at rest and in transit?
29. **Scenario:** GuardDuty alerts you to suspicious API calls from an IAM user. What are your immediate steps?

### Lambda & Serverless

30. How do you create and deploy AWS Lambda functions?
31. What are the different ways to package and push artifacts to Lambda (ZIP, container image, S3)?
32. What can trigger a Lambda function (API Gateway, S3, SNS, SQS, EventBridge)?
33. How do you handle Lambda timeout and memory errors in a CI/CD pipeline?
34. What is AWS Step Functions and when would you use it over a single Lambda?

### Monitoring & Operations

35. What CloudWatch metrics and alarms would you configure for a production EC2 workload?
36. How do you enable detailed monitoring on EC2 and what additional metrics does it provide?
37. What is AWS CloudTrail and how does it differ from CloudWatch?
38. What is AWS Config and how does it help with compliance and drift detection?

### EKS

39. How do you set up a production-grade Kubernetes cluster on EKS?
40. How do you authenticate to EKS clusters using `kubeconfig` and IAM?
41. What is IRSA (IAM Roles for Service Accounts) and how does it work in EKS?
42. How do you manage node groups vs. Fargate profiles in EKS?

### Architecture & Design

43. Design a secure and highly available 3-tier infrastructure using AWS services.
44. **Scenario:** Your e-commerce app needs to handle 10x traffic during a flash sale with zero downtime. How do you architect for it?
45. **Scenario:** Your company is migrating a monolith to microservices on AWS. What challenges do you anticipate and how do you address them?
46. How do you implement disaster recovery on AWS — what are RPO and RTO and how do you architect for each?

---

## 📊 Monitoring & Observability

### Prometheus & Grafana

1. How does Prometheus work with Kubernetes — what is its scraping model?
2. How does Prometheus discover targets in Kubernetes (service discovery via annotations and ServiceMonitors)?
3. Who exposes metrics for Prometheus — exporters, sidecar containers, instrumented apps?
4. How do you configure alerting rules in Prometheus and route alerts via Alertmanager?
5. What is PromQL? Give an example query for CPU usage per pod.
6. How do you configure Grafana dashboards to visualize Prometheus data?
7. When would you use Prometheus vs. CloudWatch, and can they coexist?

### Logging (ELK / EFK / Splunk)

8. What is the ELK stack — what is the role of Elasticsearch, Logstash, and Kibana?
9. What is the difference between ELK and EFK (Fluentd vs. Logstash)?
10. How do you ship Kubernetes pod logs to an ELK or Splunk stack?
11. What metrics and logs do you typically expose or hand off to a monitoring team?
12. **Scenario:** CPU usage crosses 90% on a node but no alert fires. How do you investigate the gap?

### Distributed Tracing

13. What is distributed tracing and how does it differ from logging?
14. What tools do you use for distributed tracing (Jaeger, Zipkin, AWS X-Ray)?
15. How does AWS X-Ray integrate with Lambda and API Gateway for end-to-end tracing?

---

## 🔐 Security & DevSecOps

1. How do you secure AWS credentials in production environments?
2. How do you handle secret management in CI/CD pipelines (Vault, Secrets Manager, Parameter Store)?
3. How do you implement least privilege access across dev, staging, and production environments?
4. How do you design a secure CI/CD pipeline — what security gates do you add?
5. How do you establish secure database connections from applications and pipelines?
6. What is SSL/TLS termination and where in the architecture does it happen?
7. Why are SSL certificates important and how do you manage their lifecycle (ACM, cert-manager)?
8. What is SAST vs. DAST and where do you integrate each in a CI/CD pipeline?
9. What is SonarQube and how does it fit into a CI/CD pipeline?
10. What is a WAF (Web Application Firewall) and when would you use AWS WAF?
11. **Scenario:** Your organization faces a DDoS attack on a production application. What is your immediate response using AWS services?
12. **Scenario:** An IAM access key is found in a public GitHub repo. It has been exposed for 2 hours. What are your immediate remediation steps?
13. What is email signing and Helm chart signing (cosign, GPG)? Which tools are used?
14. How do you implement GDPR compliance for data stored in S3 and RDS?

---

## 🐧 Linux & Troubleshooting

1. Describe your daily use of Linux in a production environment.
2. A user cannot write files despite the disk showing free space. How do you troubleshoot (inode exhaustion)?
3. How do you identify which process is consuming the most CPU or memory on a Linux server?
4. How do you find and kill a zombie process in Linux?
5. How do you analyze a server that has become suddenly slow — what is your step-by-step approach?
6. What is the difference between `ps`, `top`, `htop`, and `vmstat`?
7. How do you manage services using `systemd` — start, stop, enable, and check status?
8. How do you set up a cron job and verify it is running correctly?
9. How do you troubleshoot SSH connectivity issues to a remote server?
10. What is the difference between a hard link and a soft (symbolic) link?
11. How do you check open ports on a Linux system (`netstat`, `ss`, `lsof`)?
12. How do you rotate logs in Linux and what tools are used?
13. **Scenario:** A production server's `/var` partition is 100% full and the application is down. How do you recover?

---

## 💻 Scripting & Automation

### Bash

1. Write a Bash script to check if a service is running and restart it if it is not.
2. How do you use `awk`, `sed`, and `grep` to parse log files?
3. What is the difference between `$()` and backticks in Bash?
4. How do you handle errors and set exit codes in a Bash script?
5. How do you schedule and monitor a Bash script using cron?

### Python

6. How have you used Python in DevOps automation (boto3, fabric, Ansible modules)?
7. Write a Python script using `boto3` to list all EC2 instances and their current states.
8. How do you handle exceptions and implement retries in a Python script calling AWS APIs?
9. What is the difference between Python's `subprocess` and `os.system`?
10. How do you use Python to parse JSON or YAML configuration files in automation workflows?

### General

11. How do you pass environment variables to a script running inside a Docker container or Kubernetes pod?
12. What is YAML and what are common pitfalls when writing Kubernetes manifests in YAML?

---

## 🔄 Disaster Recovery & Reliability

1. What is the difference between RTO (Recovery Time Objective) and RPO (Recovery Point Objective)?
2. How do you design a multi-region active-passive failover on AWS?
3. How do you design a multi-region active-active setup for a global application?
4. What is a runbook and why is it important in a DevOps team?
5. What is chaos engineering and how would you implement it (AWS Fault Injection Simulator, Chaos Monkey)?
6. How do you conduct game days or disaster recovery drills?
7. **Scenario:** Your primary RDS instance becomes unavailable. Walk me through the failover process with Multi-AZ.
8. **Scenario:** An entire AWS Availability Zone goes down. How does your architecture respond?
9. How do you implement circuit breakers in a microservices architecture?
10. What is a blameless post-mortem / retrospective and what should it contain?

---

## 🌐 GCP

1. What is Vertex AI in GCP and in what scenarios would you use it?
2. What is GKE Autopilot and how does it differ from a standard GKE cluster?
3. What is the GCP equivalent of AWS IAM, VPC, and CloudTrail?

---

## 🤝 Behavioral & Leadership

1. How do you handle a difficult production outage under pressure?
2. How do you own up to a mistake that caused a production incident?
3. How do you help a teammate who lacks clarity on a complex problem?
4. How do you manage multiple high-priority tasks or simultaneous incidents?
5. How do you lead and communicate during an ongoing outage?
6. How do you ensure infrastructure changes are backward-compatible and future-proof?
7. Describe a time you disagreed with a design decision. How did you handle it?
8. How do you stay updated with rapidly evolving DevOps tools and cloud services?
9. How do you balance speed of delivery with system reliability and security?

---

## 🎯 Scenario-Based Questions (Cross-Tool)

> These are the most likely questions asked in real senior DevOps interviews. Approach each with: **Observe → Diagnose → Fix → Prevent**.

### Infrastructure & Deployment

1. **Scenario:** Your Terraform `apply` partially succeeded — some resources were created, others failed. How do you recover without destroying what was already created?
2. **Scenario:** A new deployment caused a 20% error rate spike in production. You need to rollback within 5 minutes. What is your exact process?
3. **Scenario:** You are asked to migrate a stateful application from one Kubernetes namespace to another with zero downtime. How do you approach it?
4. **Scenario:** A developer accidentally pushed an AWS secret key to a public GitHub repo. It has been exposed for 2 hours. What do you do?
5. **Scenario:** Your staging environment works fine but the same Docker image fails in production. How do you investigate the discrepancy?

### Scaling & Performance

6. **Scenario:** Your application needs to handle 10x traffic during a seasonal sale. How do you architect for this on AWS with minimal over-provisioning?
7. **Scenario:** Your Kubernetes cluster has pods stuck in `Pending` even though nodes appear to have available resources. What do you check?
8. **Scenario:** Database query response time is degrading — from 20ms initially to 800ms now. How do you diagnose and fix it?
9. **Scenario:** Engineers are spending too much time querying the database. How do you reduce load using AWS caching services?
10. **Scenario:** Your Lambda function is timing out intermittently during CI/CD deployments. How do you debug and resolve it?

### Monitoring & Alerting

11. **Scenario:** CPU usage crosses 90% on a node but no alert fires. How do you investigate the alerting gap?
12. **Scenario:** Your application logs are inconsistent across microservices, making it hard to trace distributed failures. How do you standardize logging?
13. **Scenario:** A microservice is returning 502 errors intermittently with no obvious errors in its own logs. Where do you look next?

### Security

14. **Scenario:** GuardDuty sends an alert that an EC2 instance is performing port scanning inside your VPC. What are your steps?
15. **Scenario:** You discover a Jenkins pipeline is running with an IAM role that has `AdministratorAccess`. How do you remediate this safely without breaking the pipeline?
16. **Scenario:** A penetration test reveals that an S3 bucket containing customer data is publicly accessible. What is your immediate and long-term response?

### CI/CD & Automation

17. **Scenario:** A Jenkins build passes all tests but the deployed service fails health checks immediately. How do you debug?
18. **Scenario:** Your CI pipeline takes 45 minutes to run and the team wants it under 10 minutes. How do you optimize it?
19. **Scenario:** You need to deploy to dev, staging, and prod from a single pipeline with different environment configs. How do you design this?
20. **Scenario:** An Ansible playbook is idempotent on first run but causes service restarts on every subsequent run. Why could this be happening?

### Architecture

21. **Scenario:** Your monolithic application is being broken into microservices. How do you design the migration to avoid downtime and data loss?
22. **Scenario:** You need to run a batch job that processes 10 million records nightly. How do you architect this on AWS cost-efficiently?
23. **Scenario:** A client needs SOC 2 and GDPR compliance. What AWS controls and DevOps practices do you put in place?
24. **Scenario:** Your team is deploying to production 10 times a day. What guardrails do you add to maintain stability?

---

## 📝 Quick Reference: Most Frequently Asked

> Based on real interview reports from Pune, Bengaluru, and Hyderabad hiring pools (2025–26).

| Topic | Most Asked Questions |
|-------|---------------------|
| **Kubernetes** | CrashLoopBackOff debug, HPA vs KEDA vs Karpenter, RBAC, IRSA, zero-downtime deploy |
| **Docker** | Multi-stage builds, image size reduction, ENTRYPOINT vs CMD, restarting container debug |
| **Terraform** | State management, remote backend S3+DynamoDB, terraform import, workspace, drift |
| **Ansible** | Idempotency, roles vs playbooks, vault, dynamic inventory, 500-server rollout |
| **Jenkins** | Shared Libraries, pipeline failure scenarios, webhook setup, parallel stages |
| **GitHub Actions** | Reusable workflows, matrix builds, self-hosted runners, secrets management |
| **AWS Networking** | ALB vs NLB, VPC Endpoints, NAT Gateway vs Instance, 3-tier design |
| **AWS Security** | IAM least privilege, GuardDuty response, S3 exposure, Secrets Manager vs SSM |
| **Linux** | inode exhaustion, slow server diagnosis, disk full recovery, cron debugging |
| **Monitoring** | Prometheus scraping model, missing alerts, ELK log shipping, PromQL basics |
| **Security** | Secrets in pipelines, exposed IAM key response, WAF, DDoS mitigation |
| **Behavioral** | Outage handling, mistake ownership, balancing speed vs reliability, staying current |

---

*Last updated: March 2026 | Covers: Kubernetes · Docker · Helm · Terraform · Ansible · Jenkins · GitHub Actions · Git · AWS · GCP · Prometheus · ELK · Linux · Python · Bash · Security · Disaster Recovery*
