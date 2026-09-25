# Capstone Assignment — Deploy the Book Review App Using Terraform and Claude Code Agentic AI

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Student Details

**Full Name:** Atoyebi Micheal Ademola
**Cloud Platform:**Azure  
**GitHub Repository URL:**  https://github.com/Fhelobanty
**Public Application URL / Load-Balancer DNS:**http://40.123.241.116/ 

---

## Purpose

Deploy the Book Review App using Terraform on AWS or Azure in a secure, highly available, production-style three-tier architecture. Use Claude Code, specialized subagents, Terraform MCP, and validation hooks to support the engineering workflow while keeping all infrastructure-changing operations under human control.

---

# Task 0 — Prepare the Project and Agentic AI Environment

## Goal

Prepare the Book Review App project and configure the provided Claude Code Agentic AI starter kit with project context, specialized subagents, Terraform MCP, validation hooks, and safety guardrails.

## Evidence

### Screenshot 1 — Project `CLAUDE.md`

Add a screenshot of the project `CLAUDE.md` showing the three-tier architecture, security boundaries, Terraform requirements, and human-approval rules.

![alt text](screenshots/As5t0ss1.png)
![alt text](screenshots/As5t0ss11.png)
![alt text](screenshots/As5t0ss111.png)
![alt text](screenshots/As5t0ss1111.png)
![alt text](screenshots/As5t0ss11111.png)
![alt text](screenshots/As5t0ss111111.png)

---

### Screenshot 2 — Terraform Engineer Subagent

Add a screenshot showing the Terraform Engineer subagent configuration.

![alt text](screenshots/As5T0ss2.png)
![alt text](screenshots/As5T0ss22.png)
![alt text](screenshots/As5T0ss222.png)

---

### Screenshot 3 — Architecture and Security Reviewer Subagent

Add a screenshot showing the Architecture and Security Reviewer subagent configuration.

![alt text](screenshots/As5t0ss3.png)
![alt text](screenshots/As5T0ss33.png)

---

### Screenshot 4 — Terraform MCP Connection

Add a screenshot showing Terraform MCP connected and available.

![alt text](screenshots/As5t0ss4.png)

---

### Screenshot 5 — Validation Hooks

Add a screenshot showing the configured Claude Code validation hooks.

![alt text](screenshots/As5t0ss5.png)

---

# Task 1 — Design the Three-Tier Architecture

## Goal

Design the required secure, highly available three-tier architecture and create an architecture diagram before building the infrastructure.

The diagram must show:

- VPC or VNet
- Availability Zones or equivalent availability locations
- Six subnets
- Internet connectivity
- NAT or outbound design
- Public load balancer
- Web Tier
- Internal load balancer
- Application Tier
- Managed MySQL
- Read replica
- Main traffic flow

## Architecture Diagram

![alt text](screenshots/As5T1Architecture.jpg)

---

# Task 2 — Build the Terraform Networking and Security Layers

## Goal

Create the modular Terraform project and implement the network and security layers across the required public and private subnets.

## Evidence

### Screenshot 6 — Modular Terraform Project Structure

Add a screenshot showing the modular Terraform project structure.

![alt text](screenshots/As5T2ss6.png)

---

### Screenshot 7 — Six-Subnet Architecture

Add a screenshot showing the six-subnet architecture across two availability locations.

![alt text](screenshots/As5T2ss7.png)

---

### Screenshot 8 — Public and Private Tier Separation

Add a screenshot showing the public and private tier separation, including routing and security boundaries.

![alt text](screenshots/As5T2ss8.png)
![alt text](screenshots/As5T2ss88.png)

---

# Task 3 — Build the Load-Balancing and Compute Layers

## Goal

Deploy the public and internal load balancers and the Web and Application compute resources required by the Book Review App.

## Evidence

### Screenshot 9 — Web and Application Compute

Add a screenshot showing the Web and Application compute resources in their required subnets.

![alt text](screenshots/As5T3ss9.png)

---

### Screenshot 10 — Public Load Balancer

Add a screenshot showing the internet-facing public load balancer.

![alt text](screenshots/As5T3ss10.png)

---

### Screenshot 11 — Internal Load Balancer

Add a screenshot showing the private internal load balancer.

![alt text](screenshots/As5T3ss11.png)

---

### Screenshot 12 — Healthy Targets

Add a screenshot showing healthy target groups or backend pools.

![alt text](screenshots/As5T3ss12.png)

---

# Task 4 — Build the Managed MySQL Database Layer

## Goal

Deploy a private, highly available managed MySQL database with a read replica and restrict database connectivity to the Application Tier.

## Evidence

### Screenshot 13 — Managed MySQL Database

Add a screenshot showing the managed MySQL database deployment.

![alt text](screenshots/As5T4ss13.png)

---

### Screenshot 14 — High Availability

Add a screenshot showing the Multi-AZ or high-availability configuration.

![alt text](screenshots/As5T4ss14.png)

---

### Screenshot 15 — Read Replica

Add a screenshot showing the read replica configuration.

![alt text](screenshots/As5T4ss15.png)

---

### Screenshot 16 — Private Database Access

Add a screenshot showing that the database is private and accepts MySQL traffic only from the Application Tier.

![alt text](screenshots/As5T4ss16.png)
![alt text](screenshots/As5T4ss166.png)

---

# Task 5 — Validate, Review, and Apply the Terraform Configuration

## Goal

Validate the Terraform configuration, review the execution plan using both Agentic AI and human judgment, and apply the infrastructure changes only after all required checks pass.

## Evidence

### Screenshot 17 — Terraform Validation

Add a screenshot showing successful `terraform validate` output.

![alt text](screenshots/As5T5ss17.png)

---

### Screenshot 18 — Terraform Plan

Add a screenshot showing the Terraform plan output.

![alt text](screenshots/As5T5ss18.png)
![alt text](screenshots/As5T5ss188.png)
![alt text](screenshots/As5T5ss1888.png)
![alt text](screenshots/As5T5ss18888.png)

---

### Screenshot 19 — Terraform Apply

Add a screenshot showing successful `terraform apply` completion.

![alt text](screenshots/As5T5ss19.png)

---

# Task 6 — Deploy and Configure the Book Review Application

## Goal

Deploy and configure the Book Review App across the Web, Application, and Database tiers and verify the complete application functionality.

## Evidence

### Screenshot 20 — Homepage

Add a screenshot showing the Book Review App homepage through the public endpoint.

![alt text](screenshots/As5T6ss20.png)

---

### Screenshot 21 — Login or Authentication

Add a screenshot showing successful login or authentication.

![alt text](screenshots/As5T6ss21.png)

---

### Screenshot 22 — Book Data

Add a screenshot showing the book listing or book details.

![alt text](screenshots/As5T6ss22.png)

---

### Screenshot 23 — Review Functionality

Add a screenshot showing the review functionality working successfully.

![alt text](screenshots/As5T6ss23.png)
![alt text](screenshots/As5T6ss233.png)

---

### Screenshot 24 — Backend or API Evidence

Add a screenshot showing that the backend or API is working successfully.

![alt text](screenshots/As5T6ss24.png)

---

### Screenshot 25 — Database Reads and Writes

Add a screenshot showing successful database reads and writes.

![alt text](screenshots/As5T6ss25.png)

## Public Application URL

**Public Application URL / DNS:** http://40.123.241.116/

---

# Task 7 — Demonstrate the Agentic AI Workflow

## Goal

Demonstrate how Claude Code assisted with Terraform generation, architecture and security review, and evidence-based troubleshooting while infrastructure-changing decisions remained under human control.

You do not need to submit your complete Claude Code conversation history. Include only focused evidence.

## Evidence

### Screenshot 26 — AI-Assisted Terraform Generation

Add a screenshot showing one useful example of AI-assisted Terraform generation or improvement.

![alt text](screenshots/As5T6ss26.png)

---

### Screenshot 27 — Architecture or Security Review

Add a screenshot showing one structured architecture or security review result.

![alt text](screenshots/As5T6ss27.png)
![alt text](screenshots/As5T6ss277.png)

---

### Screenshot 28 — AI-Assisted Troubleshooting

Add a screenshot showing one AI-assisted troubleshooting interaction based on collected evidence.

![alt text](screenshots/As5T6ss28.png)

---

# Task 8 — Complete the Final Architecture Review

## Goal

Review the completed infrastructure against the original capstone requirements and resolve significant architecture, security, reliability, and cost issues.

Confirm that the final review covers:

- Tier separation
- Availability
- Public exposure
- Routing
- Security rules
- Load balancing
- Database privacy
- Secrets
- Terraform quality
- Module structure
- Reliability
- Obvious cost risks

Use Screenshot 27 as the focused evidence for the structured architecture or security review.

---

# Task 9 — Answer the Reflection Questions

## Goal

Reflect on the architecture, Terraform implementation, and Agentic AI workflow. Answer each question briefly in your own words.

## Architecture

### 1. Why did you separate the Web, Application, and Database tiers?

I separated the three tiers so each part of the application has a clear responsibility and security boundary. The Web tier handles user traffic, the Application tier handles backend logic, and the Database tier stores application data.

### 2. Why is the Application Tier private?

The Application Tier is private so users on the internet cannot directly access the backend. It only accepts traffic from the Web Tier through the internal Load Balancer.

### 3. Why is MySQL private?

MySQL is private to protect the application's data from direct internet access. Only the Application Tier is allowed to connect to MySQL on port 3306.

### 4. Why are multiple Availability Zones used?

Multiple Availability Zones provide better availability by distributing resources across separate Azure zones. If one zone has a problem, the architecture has resources designed for another zone.

### 5. What is the difference between Multi-AZ/high availability and a read replica?

High availability provides a standby database for availability and failover. A read replica is mainly used to handle additional read traffic and reduce the workload on the primary database.

## Terraform

### 6. How did you divide your Terraform into modules?

I divided Terraform into separate modules for networking, security, load balancing, compute, and database resources. This made the infrastructure easier to organize and maintain.

### 7. How do the modules communicate through variables and outputs?

Modules receive information through input variables and expose information through outputs. For example, the network module provides subnet IDs that are then used by the compute and database modules.

### 8. What did you specifically check in `terraform plan`?

I checked for unexpected resource creation, deletion, or replacement, public IPs, security rules, ports 3001 and 3306, database exposure, Availability Zones, dependencies, and possible cost-related changes.

## Agentic AI

### 9. What was the purpose of `CLAUDE.md`?

CLAUDE.md gave Claude Code the project's architecture, security requirements, Terraform standards, validation rules, and human-approval requirements so it could work within the project's defined guidelines.

### 10. What work did the Terraform Engineer subagent perform?

The Terraform Engineer helped with Terraform design, module configuration, resource improvements, validation, and reviewing infrastructure changes before they were applied.

### 11. What did the Architecture and Security Reviewer identify?

The reviewer checked the three-tier separation, private application and database tiers, load balancers, security boundaries, ports, public exposure, and Terraform changes for possible architecture or security problems.

### 12. Why did you use Terraform MCP instead of relying only on Claude's existing Terraform knowledge?

I used Terraform MCP so Claude could reference current Terraform and provider information instead of relying only on its existing knowledge. This helped reduce the risk of using outdated resource arguments.

### 13. What was the purpose of your validation hooks?

The validation hooks automatically ran terraform fmt and terraform validate after Terraform files were changed. This helped catch formatting and configuration errors early.

### 14. Describe one real issue Claude helped you troubleshoot.

One real issue was the Book Review registration failure. The backend logs showed a CORS error, so the problem was traced to the ALLOWED_ORIGINS configuration. I changed it to the public application URL and restarted the backend.

### 15. Describe one recommendation you reviewed, modified, or rejected instead of accepting blindly.

One example was the Terraform compute configuration. I reviewed the proposed VM configuration against the available Azure capacity and quota instead of blindly applying it. I kept Standard_D1 because it was available within the existing quota and did not request an unnecessary quota increase.

---

# Task 10 — Publish the Mandatory LinkedIn Post

## Goal

Publish a LinkedIn post describing the capstone, the technical work completed, the Agentic AI workflow, and the lessons learned.

Write the post in your own words, include at least one project image or other proof, and ensure that it can be viewed by the submission reviewer.

## LinkedIn Post URL

**LinkedIn Post URL:** https://www.linkedin.com/feed/update/urn:li:activity:7509120099228995584/

---

# Submission Instructions

- Complete Tasks 0–10 in sequence.
- Include all Screenshots 1–28 exactly as specified.
- Ensure that your full name is visible in the required screenshots.
- Include the selected cloud platform.
- Include the completed architecture diagram.
- Include the modular Terraform project structure.
- Include the working public application URL or public load-balancer DNS.
- Include all required Agentic AI workflow evidence.
- Answer all 15 reflection questions briefly in your own words.
- Include the published LinkedIn post URL.
- Do not expose cloud credentials, database passwords, SSH private keys, JWT secrets, access tokens, account IDs, Terraform state containing sensitive values, or other confidential information.
- Review all screenshots and project files carefully before submitting through GitHub.

---

# Completion Checklist

- [ ] Selected AWS or Azure
- [ ] Added and reviewed the Agentic AI starter files
- [ ] Configured `CLAUDE.md`
- [ ] Configured the Terraform Engineer subagent
- [ ] Configured the Architecture and Security Reviewer subagent
- [ ] Connected Terraform MCP
- [ ] Configured validation hooks and safety guardrails
- [ ] Created the architecture diagram
- [ ] Created the six-subnet design
- [ ] Configured public Web Tier routing
- [ ] Kept the Application Tier private
- [ ] Kept the Database Tier private
- [ ] Configured tier-specific Security Groups or NSGs
- [ ] Restricted backend port `3001`
- [ ] Restricted MySQL port `3306` to the Application Tier
- [ ] Created the public load balancer
- [ ] Created the internal load balancer
- [ ] Configured listeners and health checks
- [ ] Deployed the Web Tier compute resources
- [ ] Deployed the private Application Tier compute resources
- [ ] Provisioned private managed MySQL
- [ ] Configured Multi-AZ or high availability
- [ ] Configured a read replica
- [ ] Created the modular Terraform project
- [ ] Used variables, outputs, and module dependencies
- [ ] Used current Terraform documentation through MCP
- [ ] Used hooks for deterministic validation
- [ ] Completed `terraform fmt`
- [ ] Completed `terraform validate`
- [ ] Reviewed `terraform plan`
- [ ] Completed the Terraform Engineer review
- [ ] Completed the Architecture and Security review
- [ ] Applied the infrastructure only after human approval
- [ ] Deployed and configured the backend
- [ ] Deployed and configured the frontend
- [ ] Configured Nginx where required
- [ ] Configured the internal backend endpoint
- [ ] Configured the public frontend endpoint
- [ ] Verified the homepage
- [ ] Verified login or authentication
- [ ] Verified book data
- [ ] Verified review functionality
- [ ] Verified the backend API
- [ ] Verified database reads and writes
- [ ] Verified healthy load-balancer targets
- [ ] Included AI-assisted Terraform generation evidence
- [ ] Included one architecture or security review
- [ ] Included one AI-assisted troubleshooting example
- [ ] Completed the final architecture review
- [ ] Answered all 15 reflection questions
- [ ] Published the mandatory LinkedIn post
- [ ] Added the LinkedIn post URL
- [ ] Captured all 28 required screenshots
- [ ] Confirmed that my full name is visible in the required screenshots
- [ ] Checked that no secrets or sensitive information are exposed

---

## About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra (The CloudAdvisory), focused on real-world execution, systems thinking, and career readiness.

It helps learners build strong DevOps foundations through hands-on experience.

---

## Resources

- Book Review App Repository: [https://github.com/pravinmishraaws/book-review-app](https://github.com/pravinmishraaws/book-review-app)
- DMI Official Website: [https://dmi.pravinmishra.com](https://dmi.pravinmishra.com)
- University: [https://university.pravinmishra.com](https://university.pravinmishra.com)
- Discord Community: [https://discord.pravinmishra.com](https://discord.pravinmishra.com)
- Blog: [https://dmi.pravinmishra.com/blog](https://dmi.pravinmishra.com/blog)
- YouTube Playlist: [https://www.youtube.com/playlist?list=PLFeSNDtI4Cho](https://www.youtube.com/playlist?list=PLFeSNDtI4Cho)
- Pravin Mishra on LinkedIn: [https://www.linkedin.com/in/pravin-mishra-aws-trainer/](https://www.linkedin.com/in/pravin-mishra-aws-trainer/)
- CloudAdvisory on LinkedIn: [https://www.linkedin.com/company/thecloudadvisory/](https://www.linkedin.com/company/thecloudadvisory/)

---

*This submission is part of the DevOps Micro Internship (DMI) Cohort 3 — Agentic AI Track.*
