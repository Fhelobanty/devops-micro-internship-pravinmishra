# Assignment 5 — Open-Source Collaboration: Fork, Sync & Pull Request

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will fork the upstream repository, authenticate GitHub access, clone your fork, configure remotes, create a feature branch, update `pull_request.md`, synchronize with upstream, push your branch, and create a Pull Request.

---

# Task 0 — Fork the Upstream Repository

## Goal

Create a copy of the upstream repository under your GitHub account.

### Evidence

#### Screenshot 1 — Your fork page with your username and `devops-micro-internship-interviews` visible in the browser URL

Add your screenshot here.

---

# Task 1 — Authenticate GitHub from the Terminal

## Goal

Configure one secure authentication method so you can push changes from your terminal to your GitHub fork. Complete only one method: HTTPS with a Personal Access Token or SSH authentication.

### Evidence — Choose One

#### Screenshot 2 (HTTPS) — Output of `git config --global --get credential.helper`

Add your screenshot here if you used HTTPS. Do not show your Personal Access Token.

**OR**

#### Screenshot 2 (SSH) — Output of `ssh -T git@github.com` showing successful authentication and your own GitHub username

Add your screenshot here if you used SSH.

---

# Task 2 — Clone Your Fork Locally and Configure Remotes

## Goal

Create a local working copy where `origin` points to your fork and `upstream` points to the original repository.

### Evidence

#### Screenshot 3 — Output of `git remote -v` showing `origin` and `upstream` correctly

Add your screenshot here.

---

# Task 3 — Create a Feature Branch and Make Your Change

## Goal

Create the required `feature-readme-update` branch and add only your own entry to `pull_request.md`.

### Evidence

#### Screenshot 4 — Output of `git status` showing `pull_request.md` modified before staging

Add your screenshot here.

---

#### Screenshot 5 — Output of `git commit -m "docs: add my name to student list"`

Add your screenshot here.

---

# Task 4 — Synchronize with Upstream and Push to Your Fork

## Goal

Update your local default branch from upstream, rebase the feature branch, and push it to `origin`.

### Evidence

#### Screenshot 6 — Output of `git push -u origin feature-readme-update` showing a successful push

Add your screenshot here.

---

#### Screenshot 7 — Your fork on GitHub showing `feature-readme-update` in the branch selector or a Compare & pull request banner

Add your screenshot here.

---

# Task 5 — Create a Pull Request to Upstream

## Goal

Open a Pull Request from your fork’s feature branch to the upstream `main` branch.

### Required Pull Request Details

- Base repository: `pravinmishraaws/devops-micro-internship-interviews`
- Base branch: `main`
- Head repository: `<yourusername>/devops-micro-internship-interviews`
- Compare branch: `feature-readme-update`
- PR Title: `docs: add my name to student list`
- PR Body: `This PR adds my name to the Student List in pull_request.md as part of the DMI GitHub collaboration assignment.`

### Evidence

#### Screenshot 8 — Pull Request creation page showing the correct base repository, base branch, head repository, compare branch, and title

Add your screenshot here.

---

#### Screenshot 9 — Successfully created Pull Request page with the PR number visible

Add your screenshot here.

---

# Required URLs

#### Fork URL

`Add your fork URL here`

#### Pull Request URL

`Add your Pull Request URL here`

---

# LinkedIn Post (Mandatory)

Create a short LinkedIn post including:

- Your GitHub fork URL
- A 3–5 line explanation of what you contributed and what you learned
- One screenshot of your successfully created Pull Request

## Evidence

#### LinkedIn Post URL

`Add your URL here`

---

#### Screenshot — LinkedIn post showing the successfully created Pull Request

Add your screenshot here.

---

# Submission Instructions

- Add Screenshots 1–9 in the correct task sections
- Add your fork URL and successfully created Pull Request URL
- Show that `origin` points to your fork and `upstream` points to the original repository
- Add the mandatory LinkedIn post URL and screenshot
- Never expose a Personal Access Token, SSH private key, password, recovery code, or authentication secret

---

# Completion Checklist

- [ ] Upstream repository forked to your GitHub account
- [ ] GitHub authentication configured securely
- [ ] Your fork cloned locally
- [ ] `origin` points to your fork
- [ ] `upstream` points to `pravinmishraaws/devops-micro-internship-interviews`
- [ ] `feature-readme-update` created and used
- [ ] Only `pull_request.md` modified
- [ ] Your entry added at the end of the Student List
- [ ] Required commit message used
- [ ] Local `main` synchronized with `upstream/main`
- [ ] Feature branch rebased and pushed to `origin`
- [ ] Pull Request targets the correct upstream repository and `main` branch
- [ ] Screenshots 1–9 included and readable
- [ ] Mandatory LinkedIn post completed and linked
- [ ] No PAT, password, private key, or authentication secret exposed

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
