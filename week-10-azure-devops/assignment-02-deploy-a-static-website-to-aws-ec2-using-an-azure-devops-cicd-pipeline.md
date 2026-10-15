# Assignment 2 — Deploy A Static Website to AWS EC2 Using an Azure DevOps CI/CD Pipeline

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

In this assignment, you will import and personalize the Static Website, provision and configure an AWS EC2 instance using Terraform and Ansible, and create an Azure DevOps CI/CD pipeline that automatically deploys the website to Nginx through an SSH Service Connection.

---

# Task 0 — Verify the Existing Tooling and Self-Hosted Agent

## Goal

Confirm that Terraform, Ansible, AWS CLI, SSH, and the self-hosted Azure Pipelines agent are ready.

No submission screenshot is required for this task.

---

# Task 1 — Import and Personalize the Azure Static Website Repository

## Goal

Import the Azure Static Website into Azure Repos and add your Full Name to the website.

## Evidence

### Screenshot 1 — Azure Static Website in Azure Repos

Add a screenshot of Azure Repos showing:

* Imported Azure Static Website repository
* Project files
* `index.html`

![alt text](screenshots/As2T1ss1.png)

---

# Task 2 — Provision and Configure the Target EC2 Instance

## Goal

Provision the AWS EC2 instance using Terraform and configure Nginx, SSH access, and deployment permissions using Ansible.

No additional submission screenshot is required for this task.

---

# Task 3 — Create the SSH Service Connection

## Goal

Create an Azure DevOps SSH Service Connection that can connect to the target EC2 instance using your selected SSH authentication method.

## Evidence

### Screenshot 2 — SSH Service Connection

Add a screenshot of the saved SSH Service Connection **Overview** page showing:

* Service Connection name
* SSH connection type

![alt text](screenshots/As2T3ss2.png)

> Do not expose a password, SSH private key, passphrase, or another credential.

---

# Task 4 — Create the Azure DevOps YAML Pipeline

## Goal

Create an Azure DevOps YAML pipeline that deploys the Azure Static Website to the target EC2 instance after a commit is pushed.

## Evidence

### Screenshot 3 — Azure Pipelines YAML

Add a screenshot of `azure-pipelines.yml` open in the Azure Repos editor showing:

* Push trigger
* Selected self-hosted agent pool
* Pipeline variables
* Repository checkout step
* Pipeline information step
* `CopyFilesOverSSH@0` task
* `SSH@0` verification task

![alt text](screenshots/As2T4ss3.png)

> Ensure that no password, SSH private key, PAT, or AWS credential is visible.

---

# Task 5 — Create, Authorize, and Run the Pipeline

## Goal

Run the Azure DevOps pipeline and confirm that the website files are transferred and verified successfully.

## Evidence

### Screenshot 4 — Successful Pipeline Run

Add a screenshot of the successful pipeline run and log summary showing:

* Overall pipeline status as **Succeeded**
* Pipeline information step completed
* File-copy step completed
* Remote-verification step completed
* Your Full Name visible in the pipeline output

![alt text](screenshots/As2T5ss4.png)

---

# Task 6 — Verify the Website and Automatic Trigger

## Goal

Confirm that the website is accessible through the EC2 public IP address and that a new pushed commit automatically triggers another deployment.

## Evidence

### Screenshot 5 — Deployed Azure Static Website

Add a browser screenshot showing:

* Deployed Azure Static Website
* EC2 public IP address in the browser address bar
* Your Full Name
* Updated website content after the automatic deployment

![alt text](screenshots/As2T6ss5.png)

## Final Website URL

`http://51.21.219.24>`

Replace the placeholder with your actual website URL:

[Paste your final website URL here]

---

# Assignment Summary

Write a short summary of the completed CI/CD workflow.

[Deploy Static Website to AWS EC2 Using an Azure DevOps CI/CD Pipeline
For this assignment, I deployed a static website to an AWS EC2 instance and created an automated CI/CD pipeline using Azure DevOps.
I started by importing the provided GitHub repository into Azure Repos and updating the index.html file to include my full name, Atoyebi Micheal. I then provisioned the AWS infrastructure using Terraform, including a VPC, public subnet, internet gateway, route table, security group, and Ubuntu EC2 instance.
After creating the EC2 instance, I used Ansible to configure the server. Nginx was installed and configured as the web server, SSH access was prepared for deployment, and the /var/www/html directory was configured so that the deployment user could write website files to it. I also verified that Nginx was running correctly and that the server could return an HTTP response.
Next, I created an SSH service connection in Azure DevOps for the EC2 server using SSH key authentication. I then created the Azure DevOps YAML pipeline using the required self-hosted agent pool.
The pipeline was configured to automatically run when changes are pushed to the repository. It checks out the latest source code, displays important pipeline information such as my name, branch, commit ID, self-hosted agent, and prepared files, and then uses CopyFilesOverSSH@0 to transfer the website files to the EC2 server. The .git directory and azure-pipelines.yml file are excluded from deployment.
After the files are copied, the pipeline uses SSH@0 to verify that index.html exists on the server and that Nginx is successfully returning an HTTP response.
During testing, I encountered a WSL issue with the Windows self-hosted Azure DevOps agent. The agent was initially running under the Network Service account, while Ubuntu WSL was configured for my Windows user. I corrected the agent service account and changed the default WSL distribution to Ubuntu. After that, the Bash pipeline step worked correctly and the deployment pipeline completed successfully.
The final successful pipeline run was #20261009.4. It successfully completed the pipeline information, website deployment, and deployment verification stages.
Finally, I accessed the website through the EC2 public IP address and confirmed that the website was being served successfully by Nginx. The deployed page displayed my full name, Atoyebi Micheal, confirming that the website had been successfully deployed from Azure DevOps to AWS EC2.
Final website:
http://51.21.219.24]

---

# LinkedIn Requirement

## LinkedIn Post Screenshot

Add a screenshot of your LinkedIn post containing:

* What you automated
* How Terraform, Ansible, and Azure DevOps worked together
* Three to five lines describing the CI/CD workflow
* A screenshot of the successful pipeline or deployed website

![alt text](screenshots/As2Tlkdn.png)

## LinkedIn Post URL

[https://www.linkedin.com/posts/aamicheal_devops-aws-azuredevops-ugcPost-7514143378553344000-G2Rc/?utm_source=share&utm_medium=member_desktop&rcm=ACoAADFvgDYBsnsyE66xAyq2HzH3Jfsf19WE6JA]

> Do not expose AWS credentials, SSH private keys, passwords, PATs, or other sensitive information.

---

# Submission Instructions

* Include the short assignment summary.
* Include Screenshots 1–5.
* Include the final website URL.
* Include the LinkedIn post screenshot and URL.
* Confirm that the EC2 instance is running during grading.
* Do not expose a password, SSH private key, passphrase, PAT, AWS credential, account ID, or another secret.

---

# Completion Checklist

* The correct Azure Static Website repository was imported into Azure Repos
* `index.html` is visible in Azure Repos
* Your Full Name was added to the website
* The target EC2 instance was provisioned using Terraform
* A suitable Ubuntu image and EC2 size were selected
* Nginx was configured using Ansible
* SSH login works using the selected authentication method
* The SSH user can write to `/var/www/html`
* TCP ports 22 and 80 are configured correctly
* The self-hosted Azure Pipelines agent is online
* The SSH Service Connection was created successfully
* The YAML trigger includes all branches
* The YAML uses the correct self-hosted agent pool
* The copy and remote-verification tasks completed successfully
* The pipeline status is **Succeeded**
* A new pushed commit triggered the pipeline automatically
* The Azure Static Website loads through the EC2 public IP address
* Your Full Name is visible on the deployed website
* Screenshots 1–5 are included and readable
* The final website URL is included
* The LinkedIn post screenshot and URL are included
* No sensitive information is exposed

---

*This submission is part of the DevOps Micro Internship (DMI) — Agentic AI Track.*
