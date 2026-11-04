# Assignment 10 — Capstone: Deploy the Book Review App to Kubernetes

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

Deploy the Book Review App as a production-style three-tier application using Kubernetes manifests or Helm charts, with an accessible frontend, an internal backend, and a managed or persistent MySQL database.

---

## Submission Details

**Full Name:** Atoyebi Micheal Ademola

**Kubernetes Platform:** Amazon Elastic Kubernetes Service (Amazon EKS) – AWS, us-east-2 (Ohio).

**Namespace:** book-review

**Frontend URL or IP:** http://a99f2983adbe94ea4a83b9bf9281512d-317492553.us-east-2.elb.amazonaws.com

**Access Method:** Public LoadBalancer Service provisioned through AWS. The application is accessible through its external load balancer endpoint over HTTP.

**GitHub Manifests or Helm Chart URL:** https://github.com/pravinmishraaws/book-review-app

**Architecture Diagram:**
![alt text](screenshots/As10TDiagram.jpg)

---

# Task 1 — Prepare the Kubernetes Cluster and Project

## Goal

Prepare the cluster, application source, container images, and tooling needed for the deployment.

### Evidence

#### Screenshot 1 — Active Kubernetes context and Ready nodes

![alt text](screenshots/As10T1ss1.png)

---

#### Screenshot 2 — If using Helm: Output of `helm version`

Required only if you choose Helm. Skip this screenshot if using YAML manifests.

Not applicable — using YAML manifest.

---

# Task 2 — Design the Three-Tier Kubernetes Architecture

## Goal

Document the workloads, networking, configuration, storage, and permitted communication paths before deployment.

### Evidence

#### Screenshot 3 — Completed Kubernetes architecture diagram

![alt text](screenshots/As10TDiagram.jpg)

---

# Task 3 — Create ConfigMaps and Secrets

## Goal

Provide application configuration and credentials without embedding sensitive values in images or committing them to Git.

### Evidence

#### Screenshot 4 — ConfigMap configuration or describe output showing non-sensitive values

![alt text](screenshots/As10T3ss4.png)

---

#### Screenshot 5 — Secret references or describe output showing names and keys without sensitive values

![alt text](screenshots/As10T3ss5.png)

---

# Task 4 — Deploy and Configure the MySQL Data Tier

## Goal

Provide persistent MySQL storage and allow the backend to connect without exposing the database publicly.

### Evidence

#### Screenshot 6 — Managed MySQL status or MySQL StatefulSet and PVC status

![alt text](screenshots/As10T4ss6.png)

---

#### Screenshot 7 — Successful database connectivity or schema verification with credentials hidden

![alt text](screenshots/As10T4ss7.png)

---

# Task 5 — Deploy the Backend Application Tier

## Goal

Run one or two Node.js/Express backend replicas on port 3001 and expose them through an internal ClusterIP Service.

### Evidence

#### Screenshot 8 — Backend Deployment, ready Pods, and internal Service

![alt text](screenshots/As10T5ss8.png)

---

#### Screenshot 9 — Backend startup logs and database connectivity evidence

If the application does not log successful database connections, provide a successful database-backed request alongside the startup logs.

![alt text](screenshots/As10T5ss9.png)

---

# Task 6 — Deploy the Frontend and Configure Nginx

## Goal

Run the Next.js frontend behind Nginx on port 80 and proxy API requests to the internal backend Service.

### Evidence

#### Screenshot 10 — Frontend Deployment and Ready Pods

![alt text](screenshots/As10T6ss10.png)

---

#### Screenshot 11 — Nginx reverse-proxy configuration showing the internal backend Service name and port 3001

![alt text](screenshots/As10T6ss11.png)

---

# Task 7 — Configure External and Internal Networking

## Goal

Expose the frontend and enforce the intended communication path between application tiers.

### Evidence

#### Screenshot 12 — Frontend LoadBalancer or Ingress configuration and assigned endpoint, or documented local access method

![alt text](screenshots/As10T7ss12.png)

---

#### Screenshot 13 — Internal backend Service and NetworkPolicy or equivalent restriction, with access-test evidence

![alt text](screenshots/As10T7ss131.png)
![alt text](screenshots/As10T7ss132.png)

---

# Task 8 — Validate the Application End to End

## Goal

Prove that the frontend, backend, and MySQL database work together and collect operational evidence.

### Evidence

#### Screenshot 14 — `kubectl get all` output for the book-review namespace

![alt text](screenshots/As10T8ss14.png)

---

#### Screenshot 15 — Functional Book Review App in the browser with the URL visible, including evidence of a successful user flow

![alt text](screenshots/As10T8ss15.png)

---

#### Screenshot 16 — Frontend or Nginx container logs

![alt text](screenshots/As10T8ss16.png)
![alt text](screenshots/As10T8ss161.png)

---

#### Screenshot 17 — Backend logs and evidence of a successful database-backed operation

![alt text](screenshots/As10T8ss17.png)
![alt text](screenshots/As10T8ss171.png)

---

#### Screenshot 18 — Optional: Kubernetes dashboard

Not attempted.The Kubernetes Dashboard was not deployed because the assignment's core objectives were completed using the Kubernetes CLI (kubectl).

Multiple images may be included under a screenshot number when needed to demonstrate the complete user flow.

---

# Task 9 — Optional: Implement Production Improvements

## Goal

Add selected improvements without breaking the required three-tier architecture.

### Evidence

#### Screenshot 19 — Optional: Evidence of selected Helm, HPA, probe, or TLS improvements

![alt text](screenshots/As10T9ss19.png)

---

# Task 10 — Publish Your Book Review App Deployment on LinkedIn

## Goal

Explain your three-tier architecture, demonstrate the working application, and share what you learned.

### Evidence

#### Screenshot 20 — Published LinkedIn post about your Book Review App deployment on Kubernetes

![alt text](screenshots/As10T10ss20Linkdln.jpg.png)

### LinkedIn Post URL

https://www.linkedin.com/posts/aamicheal_aws-amazoneks-kubernetes-share-7523354727519039488-p1s5/?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADFvgDYBsnsyE66xAyq2HzH3Jfsf19WE6JA

---

# Final Summary

## What Worked

Describe the application components and user flows you successfully deployed and tested.

Successfully deployed the Book Review Application on Amazon Elastic Kubernetes Service (EKS) using a three-tier architecture.

The application consists of:

Frontend: Next.js and Nginx, deployed as a Kubernetes Deployment.

Backend: Node.js and Express API, deployed separately and exposed internally through a ClusterIP Service.

Database: MySQL 8.0, deployed using a StatefulSet with persistent storage backed by Amazon EBS.

The frontend was exposed externally through a Kubernetes LoadBalancer Service, allowing users to access the application through an AWS-provisioned load balancer.

The following were successfully verified:

Frontend, backend and MySQL workloads were running.

Frontend successfully retrieved book data through the backend API.

Backend successfully connected to MySQL.

Database contained the Books, Users and Reviews tables with sample records.

Nginx successfully served application pages and forwarded API requests.

Kubernetes health checks and network access restrictions were configured.

## Issues and Fixes

Describe the main issues encountered, their causes, and how you resolved them.

Several technical challenges were encountered during deployment:

Database connection failure: The backend initially attempted to connect to localhost instead of the MySQL service. This was resolved by configuring DB_HOST to use mysql-service and providing the correct database credentials.

Persistent storage configuration: MySQL required the Amazon EBS CSI driver and a suitable StorageClass. The EBS CSI add-on was activated, and an 8Gi persistent volume claim was successfully bound.

Network connectivity: Network access restrictions affected connectivity testing. AWS VPC CNI network policy functionality was enabled, and Kubernetes NetworkPolicies were configured to control access to the backend and database.

Health probe configuration: The backend initially used TCP-based health checks. These were updated to HTTP readiness and liveness probes using the application's health endpoint.

Kubernetes resource constraints: Available compute capacity limited additional worker-node provisioning. The deployment was completed using the existing worker-node capacity without requesting a quota increase.

## Tools and Sources Used

List the documentation and tools that helped you complete the assignment.

Amazon Web Services (AWS)

Amazon EKS

Amazon ECR

Amazon EBS

Kubernetes and kubectl

Docker and Docker Desktop

Node.js and Express

Next.js and Nginx

MySQL 8.0

AWS CLI

Ubuntu on WSL

Visual Studio Code

Git and GitHub

Documentation and Sources:

Book Review Application GitHub repository.

Official AWS documentation for Amazon EKS, ECR and EBS.

Official Kubernetes documentation covering Deployments, Services, StatefulSets, Persistent Volumes, NetworkPolicies and health probes.

## Optional Improvements

Describe any optional improvements implemented, or write “Not attempted.”

Implemented additional production-oriented configurations, including:

HTTP readiness and liveness probes for the backend.

Kubernetes NetworkPolicies to restrict backend and database ingress.

ConfigMaps and Secrets for application configuration and credentials.

Persistent database storage using Amazon EBS.

Kubernetes Dashboard: Not attempted. It was optional, and the application was managed and validated using kubectl.

## Cleanup or Reuse Plan

State which resources were removed or why the environment is being retained.

Temporary testing resources, including the network connectivity test Pod and temporary MySQL client Pods, were removed after use.

The main AWS and Kubernetes resources have been retained to preserve the working deployment, project evidence and opportunity for further testing or improvements.

The retained environment includes:

Amazon EKS cluster and worker node.

Frontend and backend Deployments.

MySQL StatefulSet.

Kubernetes Services and NetworkPolicies.

Persistent EBS storage.

Amazon ECR repositories.

External LoadBalancer.

---

# Submission Instructions

- Include your Kubernetes manifests or Helm chart in the linked repository.
- Submit Secret examples containing placeholders only.
- Include Screenshot 1, Screenshots 3–17, and Screenshot 20.
- Include Screenshot 2 only if using Helm.
- Screenshots 18–19 are optional.
- Keep screenshot numbering consistent with the guidelines.
- Use clear, readable screenshots showing relevant configuration, commands, and outputs.
- Make your full name visible in required screenshots.
- Complete the submission details and Final Summary.
- Include your published LinkedIn post URL.
- Capture required evidence before cleanup.
- Do not expose passwords, tokens, JWT secrets, actual Secret values, kubeconfig contents, cloud credentials, or confidential account information.

---

# Completion Checklist

- [ ] Selected and configured a supported Kubernetes platform
- [ ] Confirmed the context and Ready nodes (Screenshot 1)
- [ ] Created and selected the book-review namespace
- [ ] Inspected the application repository
- [ ] Prepared images accessible to the cluster
- [ ] Confirmed Helm if using charts (Screenshot 2, conditional)
- [ ] Created the architecture diagram (Screenshot 3)
- [ ] Created ConfigMaps and Secrets (Screenshots 4–5)
- [ ] Excluded actual Secret values from Git and screenshots
- [ ] Provisioned private managed MySQL or persistent Kubernetes MySQL (Screenshot 6)
- [ ] Initialized the required database and schema
- [ ] Verified database connectivity or schema (Screenshot 7)
- [ ] Deployed one or two backend replicas listening on port 3001
- [ ] Created the backend ClusterIP Service (Screenshot 8)
- [ ] Verified backend-to-database connectivity (Screenshot 9)
- [ ] Deployed one or two frontend replicas behind Nginx (Screenshot 10)
- [ ] Configured API proxying through the internal backend Service (Screenshot 11)
- [ ] Configured and documented frontend access (Screenshot 12)
- [ ] Enforced backend access restrictions (Screenshot 13)
- [ ] Confirmed that the backend and database are not publicly exposed
- [ ] Captured resource status for book-review (Screenshot 14)
- [ ] Tested application functionality and database writes (Screenshots 15 and 17)
- [ ] Verified saved data after application restart
- [ ] Captured frontend and backend logs (Screenshots 16–17)
- [ ] Included optional dashboard or improvement evidence if attempted (Screenshots 18–19)
- [ ] Published the LinkedIn post (Screenshot 20)
- [ ] Included the LinkedIn post URL
- [ ] Documented issues, fixes, and useful sources
- [ ] Recorded cleanup status or reuse plans
- [ ] No sensitive data exposed

---

## 📌 About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra (The CloudAdvisory) focused on real-world execution, systems thinking, and career readiness.

It helps learners build strong DevOps foundations with hands-on experience.

---

## 📌 Resources

- 🌐 DMI Official Website: https://dmi.pravinmishra.com?utm_source=github&utm_medium=readme  
- 🎓 University: https://university.pravinmishra.com?utm_source=github&utm_medium=readme  
- 💬 Discord Community: https://discord.pravinmishra.com?utm_source=github&utm_medium=readme  
- 📝 Blog: https://dmi.pravinmishra.com/blog?utm_source=github&utm_medium=readme  
- ▶️ YouTube Playlist: https://www.youtube.com/playlist?list=PLFeSNDtI4Cho  
- 🔗 Pravin Mishra (LinkedIn): https://www.linkedin.com/in/pravin-mishra-aws-trainer/  
- 🏢 CloudAdvisory (LinkedIn): https://www.linkedin.com/company/thecloudadvisory/

---

*This submission is part of DevOps Micro Internship (DMI) — Agentic AI Track.*
