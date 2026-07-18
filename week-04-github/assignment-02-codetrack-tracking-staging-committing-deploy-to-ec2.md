# Assignment 2 — Tracking, Staging, Committing + Deploy to EC2 (CodeTrack)

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will track and stage project files, create two meaningful Git commits, verify the repository history, and deploy the CodeTrack static website to an EC2 web server using Nginx.

---

# Task 1 — Verify Git Setup and Enter the Repository

## Goal

Confirm that Git works and that you are inside the correct CodeTrack repository.

### Evidence

#### Screenshot 1 — Output of `pwd`

Add your screenshot here.

---

#### Screenshot 2 — Output of `git status`

Add your screenshot here.

---

# Task 2 — Create `index.html` and `style.css`

## Goal

Create the two starter UI files and confirm that both files exist.

### Evidence

#### Screenshot 3 — Commands and output showing `index.html` and `style.css` in the directory listing

Add your screenshot here.

---

# Task 3 — Add Starter Content

## Goal

Add the provided starter HTML and CSS content to the local CodeTrack files.

### Evidence

#### Screenshot 4 — Your editor showing the contents of `index.html` and `style.css`; one screenshot is acceptable if both files are visible

Add your screenshot here.

---

# Task 4 — Track and Stage Files Correctly

## Goal

Identify the untracked files, stage them intentionally, and verify the staging area.

### Evidence

#### Screenshot 5 — Output of `git status` showing both files as untracked

Add your screenshot here.

---

#### Screenshot 6 — Output of `git status` showing both files staged under Changes to be committed

Add your screenshot here.

---

# Task 5 — Create the First Commit (Clean Initial Commit)

## Goal

Create the first commit with the required meaningful message and verify the repository history.

### Evidence

#### Screenshot 7 — Output of `git commit -m "Initial UI scaffold: add index.html and style.css"`

Add your screenshot here.

---

#### Screenshot 8 — Output of `git log --oneline` showing the first commit

Add your screenshot here.

---

# Task 6 — Modify `index.html` and Create a Second Commit

## Goal

Complete a controlled homepage change and record it as a separate, meaningful commit.

### Evidence

#### Screenshot 9 — Browser showing the updated page with visible Student Name and Group Name changes

Add your screenshot here.

---

#### Screenshot 10 — Output of `git status` showing `index.html` as modified

Add your screenshot here.

---

#### Screenshot 11 — Output of `git commit -m "Update homepage content: heading, tagline, CTA button"`

Add your screenshot here.

---

#### Screenshot 12 — Output of `git log --oneline` showing two commits

Add your screenshot here.

---

# Task 7 — Deploy to EC2 with Nginx (Static Website)

## Goal

Deploy the CodeTrack static website to a live Ubuntu or Amazon Linux EC2 instance using Nginx.

### Evidence

#### Screenshot 13 — Nginx status output showing `active (running)`

Add your screenshot here.

---

#### Screenshot 14 — Output of `curl -I http://localhost` showing `HTTP 200 OK`

Add your screenshot here.

---

#### Screenshot 15 — Browser showing the CodeTrack site loaded from `http://<EC2_PUBLIC_IP>`, with the URL, Full Name, and Group Name visible

Add your screenshot here.

---

# Live Application URL

Paste your live CodeTrack application URL here:

`Add your URL here`

---

# LinkedIn Post (Mandatory)

Your post must include:

- Your live CodeTrack application URL
- A 3–5 line explanation of what you deployed and what you learned
- One screenshot of the deployed application showing your Full Name

## Evidence

#### LinkedIn Post URL

`Add your URL here`

---

#### Screenshot — LinkedIn post showing the deployed application

Add your screenshot here.

---

# Submission Instructions

- Add all 15 required screenshots in the correct task sections
- Include `git log --oneline` output showing at least two meaningful commits
- Add the live CodeTrack application URL
- Add the required LinkedIn post URL and screenshot
- Do not expose AWS keys, passwords, private key contents, or other sensitive information

---

# Completion Checklist

- [ ] CodeTrack repository verified with `git status`
- [ ] `index.html` and `style.css` created and populated
- [ ] Starter files staged and committed in the first commit
- [ ] Student Name and Group Name updated in `index.html`
- [ ] Second controlled commit created
- [ ] `git log --oneline` shows at least two commits
- [ ] Nginx is active on the EC2 instance
- [ ] `curl` returns HTTP 200 OK
- [ ] CodeTrack loads through the EC2 public IP
- [ ] All 15 required screenshots included
- [ ] Mandatory LinkedIn post completed and linked
- [ ] No sensitive data exposed

---

# About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra (The CloudAdvisory), focused on real-world execution, systems thinking, and agentic AI workflows.

It helps learners build strong DevOps foundations through hands-on experience.

---

# Resources

* 🌐 DMI Official Website: [https://pravinmishra.com/dmi](https://pravinmishra.com/dmi)
* 🎓 DevOps for Beginners (Udemy): [https://www.udemy.com/course/devops-for-beginners-docker-k8s-cloud-cicd-4-projects/](https://www.udemy.com/course/devops-for-beginners-docker-k8s-cloud-cicd-4-projects/)
* 🎓 Agentic AI DevOps with Claude Code: [https://www.udemy.com/course/ultimate-agentic-ai-devops-with-claude-code/](https://www.udemy.com/course/ultimate-agentic-ai-devops-with-claude-code/)
* 🎓 DevOps with Claude Code: Terraform, EKS, ArgoCD & Helm: [https://www.udemy.com/course/devops-with-claude-code-terraform-eks-argocd-helm/](https://www.udemy.com/course/devops-with-claude-code-terraform-eks-argocd-helm/)
* ▶️ YouTube Playlist: [https://www.youtube.com/playlist?list=PLFeSNDtI4Cho](https://www.youtube.com/playlist?list=PLFeSNDtI4Cho)
* 🔗 Pravin Mishra (LinkedIn): [https://www.linkedin.com/in/pravin-mishra-aws-trainer/](https://www.linkedin.com/in/pravin-mishra-aws-trainer/)
* 🏢 CloudAdvisory (LinkedIn): [https://www.linkedin.com/company/thecloudadvisory/](https://www.linkedin.com/company/thecloudadvisory/)

*This submission is part of DevOps Micro Internship (DMI) Cohort 3 — Agentic AI Track.*
