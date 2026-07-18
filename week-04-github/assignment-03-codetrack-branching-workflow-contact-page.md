# Assignment 3 — CodeTrack Branching Workflow: Contact Page

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will create a feature branch, add a Contact page through two atomic commits, prove that the default branch remains unchanged before merging, merge the feature, and inspect the Git history.

---

# Task 1 — Confirm Repository State and Default Branch

## Goal

Start from a clean default branch and confirm that you are working in the correct repository.

### Evidence

#### Screenshot 1 — Output of `git status` and `git branch` showing a clean status and that you are on `main` or `master`

Add your screenshot here.

---

# Task 2 — Create and Switch to a Feature Branch

## Goal

Create a branch named exactly `feature/contact-page` and switch to it.

### Evidence

#### Screenshot 2 — Branch creation output and `git branch` showing `* feature/contact-page`

Add your screenshot here.

---

# Task 3 — Add `contact.html` on the Feature Branch

## Goal

Create `contact.html` and record it as a dedicated atomic commit on `feature/contact-page`.

### Evidence

#### Screenshot 3 — Output of `ls` showing `contact.html`

Add your screenshot here.

---

#### Screenshot 4 — Output of `git commit -m "feat(contact): add Contact page"`

Add your screenshot here.

---

#### Screenshot 5 — Output of `git log --oneline -3` showing the new commit

Add your screenshot here.

---

# Task 4 — Add the Contact Link to `index.html`

## Goal

Add the Contact page link to the homepage and record it in a separate atomic commit.

### Evidence

#### Screenshot 6 — Output of `git status` showing `index.html` as modified before staging

Add your screenshot here.

---

#### Screenshot 7 — Output of `git commit -m "feat(nav): add Contact Page link"`

Add your screenshot here.

---

#### Screenshot 8 — Browser showing the Contact Page link on the homepage while on `feature/contact-page`

Add your screenshot here.

---

# Task 5 — Verify Isolation (Prove the Default Branch Is Unchanged)

## Goal

Demonstrate that the feature work does not affect `main` or `master` before it is merged.

### Evidence

#### Screenshot 9 — Terminal showing the checkout command and `ls`, proving that `contact.html` is absent

Add your screenshot here.

---

#### Screenshot 10 — Browser showing that the Contact Page link is not present on the default branch

Add your screenshot here.

---

# Task 6 — Merge the Feature Branch into the Default Branch

## Goal

Merge `feature/contact-page` into `main` or `master` and validate the completed feature.

### Evidence

#### Screenshot 11 — Output of `git merge feature/contact-page`

Add your screenshot here.

---

#### Screenshot 12 — Output of `ls` showing `contact.html` after the merge

Add your screenshot here.

---

#### Screenshot 13 — Browser showing the Contact page opened from the homepage link on the default branch

Add your screenshot here.

---

# Task 7 — Inspect History (Graph View)

## Goal

Display the repository history in graph form and verify the feature commits.

### Evidence

#### Screenshot 14 — Full output of `git log --oneline --graph --decorate --all`

Add your screenshot here.

---

# Task 8 — Optional Cleanup (Delete the Feature Branch)

## Goal

Remove the merged local feature branch to keep the branch list clean.

### Optional Evidence

#### Screenshot 15 (Optional) — Output of `git branch -d feature/contact-page` and `git branch` showing successful branch deletion

Add your screenshot here if you complete this task.

---

# Submission Instructions

- Add Screenshots 1–14 in the correct task sections
- Add optional Screenshot 15 only if you complete Task 8
- Show that `feature/contact-page` was used for both feature commits
- Show that `contact.html` and the homepage link were absent before merging
- Show that the Contact page works after merging
- Include the graph log showing the relevant commit history
- Do not expose sensitive information

---

# Completion Checklist

- [ ] Started from a clean `main` or `master` branch
- [ ] Created and used `feature/contact-page`
- [ ] Added `contact.html` with the exact required content
- [ ] Created the atomic Contact page commit
- [ ] Added the Contact Page link to `index.html`
- [ ] Created the separate atomic navigation commit
- [ ] Verified that the default branch was unchanged before merging
- [ ] Merged `feature/contact-page` successfully
- [ ] Verified that `contact.html` exists after merging
- [ ] Verified that the Contact Page link opens correctly
- [ ] Graph history inspected and captured
- [ ] Screenshots 1–14 included and readable
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
