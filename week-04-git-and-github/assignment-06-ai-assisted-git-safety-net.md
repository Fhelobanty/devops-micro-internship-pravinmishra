# Assignment 6 — Building an AI-Assisted Git Safety Net (PR Ready Check)

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In Week 2 you built Claude Code hooks that block a dangerous action *before* it happens (`PreToolUse`), and a restricted skill that could look but not touch (`allowed-tools` without `Write`). In this assignment you will discover that Git has the exact same idea, decades older: a **pre-commit hook** that blocks a commit before it's created.

You will build both halves of a real "PR Ready" workflow:

1. A **Git hook that follows fixed rules** — scans staged changes for hardcoded secrets and oversized files and refuses the commit. No AI involved, no guessing, just a rule that gives the same answer every time.
2. A **restricted Claude Code skill** (`/pr-ready`) that reads your staged diff and drafts a Pull Request title, description, and a short list of things worth a second look — the kind of judgment a fixed rule can't make (mixed changes, missing context, unclear intent). The skill never commits, pushes, or opens the PR. You do that yourself, using its draft as a starting point.

This mirrors the Agentic Loop from Week 3's Linux triage assignment: **Gather → Analyze → Human Act → Verify**. The hook and the skill both gather and analyze; only you act.

---

# Task 0 — Confirm Your Fork and Create a Feature Branch

## Goal

Confirm you are working in your own fork, then create a dedicated branch for this assignment.

### Evidence

#### Screenshot 1 — Output of git remote -v and git branch showing the new branch

![GitRemote](screenshots/As6T0ss1.png)

---

### Notes

**1. Why create a dedicated branch instead of doing this work on main?**

Working from a dedicated branch keeps this assignment isolated from the main branch, so I can develop, test, and review the changes safely without affecting the existing codebase. It also makes it possible to open a Pull Request that contains only this assignment's work, rather than mixing it in with unrelated changes on main.

---

# Task 1 — Stage a Change With Realistic Risk

## Goal

On your own fork of this repository (the one you've been submitting your DMI work in since onboarding), create a new branch and stage a change that a real reviewer should catch: a hardcoded-looking secret and a leftover debug statement.

### Evidence

#### Screenshot 1 — Output of  `git status` showing the staged file on feature/ai-pr-ready

![GitStatus](screenshots/As6T1ss11.png)

---

### Notes

**1. Why does this assignment use an obviously fake key instead of a real one?**

The assignment intentionally uses a fake key, so the pre-commit hook can be tested safely without ever exposing a real credential. This shows that the hook works by detecting secret-shaped patterns, not by checking whether a key is actually valid, meaning no real authentication secret is ever committed or shared in the process

---

# Task 2 — Write a Real Git Pre-Commit Hook

## Goal

Create a tracked, shareable pre-commit hook that blocks a commit containing secret-like patterns or files over 1MB.

### Evidence

#### Screenshot 2 — `hooks/pre-commit` open in VS Code showing the full script

![Hooks](screenshots/As6T2ss2.png)

---

#### Screenshot 3 — Output of `git config core.hooksPath` confirming it points to `hooks`

![GitConfig](screenshots/As6T2ss3.png)

---

### Notes

**1. Why is `hooks/pre-commit` tracked in the repo instead of living only in `.git/hooks/`?**

It is tracked so everyone who clones the repository can use the same hook. Unlike .git/hooks/, the hooks/ folder is version-controlled and can be shared with the team.

---

**2. Compare this to `PreToolUse` from Week 2 Assignment 6. What does each one intercept, and what do they have in common?**

The hooks/pre-commit script intercepts Git commit attempts and checks staged files before a commit is created, blocking commits that contain secret-like patterns or oversized files. PreToolUse from Week 2 Assignment 6 intercepts AI tool requests before the tool is allowed to run. Both serve as preventive safety gates, enforcing rules and stopping risky actions before they occur rather than fixing problems afterward.

---

# Task 3 — Prove the Hook Blocks the Risky Commit

## Goal

Attempt to commit the staged file from Task 1 and show the hook rejecting it.

### Evidence

#### Screenshot 4 — Terminal showing `git commit` rejected with the hook's "BLOCKED" message naming the exact file

![Blocked](screenshots/As6T3ss4.png)

---

### Notes

**1. Which line in `hooks/pre-commit` matched your fake key, and why did it match?**

The match came from the line in the hook that uses `grep` to search staged content for key-like patterns. Specifically, it looks for strings starting with the `AKIA` prefix, followed by a fixed number of uppercase letters and digits. Since my test value, `AKIAABCDEFGHIJKLMNOP`, followed that exact structure, the regular expression matched it and the commit was blocked as expected.


---

**2. Could this hook have caught a poorly-named variable that stores a secret without the `AKIA` prefix? What does that tell you about the limits of a fixed rule like this?**

No. If the secret didn't match one of the hook's predefined patterns, such as the `AKIA` prefix, it would slip through undetected, regardless of how the variable was named. This highlights the core limitation of a fixed-rule approach: it can only flag what it has been explicitly written to recognize. Any secret in an unexpected format, or stored under a misleading name, falls outside its reach.

---

# Task 4 — Build the `/pr-ready` Skill

## Goal

Create a manually invoked Claude Code skill that reads your staged changes and produces a PR-readiness report and a draft PR description — without writing, committing, or pushing anything itself.

### Evidence

#### Screenshot 5 — `SKILL.md` frontmatter showing `allowed-tools: Bash, Read, Grep` (no `Write`) and `disable-model-invocation: true`

![Skill.md](screenshots/As6T4ss5.png)

---

#### Screenshot 6 — `/pr-ready` output while the risky file is still staged, showing it flagged the secret and/or debug statement

![/pr-ready](screenshots/As6T4ss6.png)

---

### Notes

**1. Why does `/pr-ready` have `Bash` and `Read` but not `Write`?**

/pr-ready is allowed to use Bash and Read so it can inspect the repository, run Git commands, and review files when evaluating a Pull Request. It does not have Write permission because its purpose is to provide analysis and recommendations, not to make changes. This ensures the user remains in control of any modifications.

---

**2. The pre-commit hook and `/pr-ready` both looked at the same staged diff. Did they flag the same things? What did one catch that the other didn't?**

No. The pre-commit hook detected rule-based issues, such as the fake secret, while /pr-ready provided a broader review by highlighting overall Pull Request quality, including missing documentation, testing, and readiness for submission.

---

# Task 5 — Fix the Issues and Re-Verify

## Goal

Remove the secret and debug statement, then prove both gates now pass clean.

### Evidence

#### Screenshot 7 — `git commit` succeeding after the fix (no BLOCKED message)

![GitCommit](screenshots/As6T5ss7.png)

---

#### Screenshot 8 — Second `/pr-ready` run showing a clean risk report and a drafted PR title + description

![/pr-ready](screenshots/As6T5ss8.png)

---

### Notes

**1. What exactly did you change to satisfy the pre-commit hook?**

I removed the fake AWS access key I'd intentionally staged to test the hook, then re-staged the change and committed again. The first attempt was correctly blocked — the hook's pattern match flagged the secret-shaped string before it could reach the repository history. After removing it, the same commit passed cleanly, confirming the hook catches credential leaks at commit time rather than after the fact.

---

# Task 6 — Push and Open a Pull Request Using the AI Draft

## Goal

Push your branch and open a real Pull Request, using `/pr-ready`'s drafted title and description as your starting point — read it critically and edit before you use it.

**Important:** Open this Pull Request with base repository set to **your own fork** — not the shared upstream `pravinmishraaws/devops-micro-internship-pravinmishra` repository. This assignment's hook and skill files are your own practice work, not a change meant for the shared class repo.

### Evidence

#### Screenshot 9 — Your Pull Request showing the base repository is your own fork, plus the title and description, with the `/pr-ready` draft visible for comparison (paste it in the PR conversation or your notes below)

![Pull-Request](screenshots/As6T6ss9.png)

---

#### PR Link

https://github.com/pravinmishraaws/devops-micro-internship-interviews/pull/393

---

### Notes

**1. What, if anything, did you edit in the AI's drafted PR description before using it? Why?**

I edited the drafted description to make the PR title reference the specific assignment (Week 04 Assignment 06) rather than leaving it generic, and I tightened the wording around what each safety layer catches, the AI's draft was accurate but slightly vague about the distinction between the pre-commit hook's pattern-based blocking and the pr-ready skill's broader quality review. I wanted anyone reviewing the PR later to immediately understand why both layers exist rather than assuming they were redundant.


---

**2. If you had blindly copy-pasted the AI's draft without reading it, what could go wrong?**

Blindly copy-pasting the AI-generated description could result in submitting inaccurate or misleading information that does not properly represent the actual changes made. This could create confusion for reviewers and reduce the credibility of the contribution. Reviewing the content ensures accuracy, clarity, and professionalism.

---

**3. Why does this PR need to target your own fork instead of the shared upstream repository?**

Opening the PR against my own fork keeps the change isolated until it's reviewed, so I can test and iterate on the pre-commit hook and skill without risking breaking the shared upstream repo or affecting teammates mid-change. It also means any mistakes — like the intentionally fake secret used to test the hook — stay contained to my fork's history rather than being pushed directly into the shared codebase, which matches the same "safety net" principle the assignment is teaching.

---

# Task 7 — Map the Workflow to the Agentic Loop

## Goal

Explain this assignment's workflow using the same Gather → Analyze → Human Act → Verify structure from Week 3.

### Notes

**1. Which step(s) represent Gather?**

Gather corresponds to the stage where the pre-commit hook scans the staged files, and where /pr-ready reads the staged diff and relevant repository information — both occurring before any analysis takes place.

---

**2. Which step(s) represent Analyze?**

Analyze is the step in which /pr-ready evaluates the gathered information and produces findings and recommendations regarding the pull request.

---

**3. Which step is Human Act, and why must a human — not Claude — run `git commit`, `git push`, and open the PR?**

Human Act occurs when I review the AI's recommendations and then manually execute git commit, git push, and open the pull request. These actions must be performed by a human because they directly modify the repository and require explicit approval and accountability that only a human can provide.

---

**4. Which step is Verify?**

Verify is the final step, in which I confirm that the commit succeeds, the branch is pushed correctly, and the pull request is created as expected following the changes.

---

**5. In one or two sentences: why do you need *both* the fixed-rule pre-commit hook and the AI skill? Isn't one enough?**

No — one is not sufficient. The pre-commit hook enforces specific, rule-based checks, while the AI skill offers broader, context-aware review; together, they address different categories of risk and jointly strengthen overall code quality.

---

# Task 8 — LinkedIn Post

## Goal

Publish a LinkedIn post summarizing what you built and what you learned about combining fixed-rule safety checks with AI-assisted review.

### Evidence

#### LinkedIn Post URL

https://www.linkedin.com/posts/aamicheal_devops-gitops-automation-share-7486426890057154560-g8GR/?utm_source=share&utm_medium=member_desktop&rcm=ACoAADFvgDYBsnsyE66xAyq2HzH3Jfsf19WE6JA

---

## Key Learnings

- Set up a Git pre-commit hook that the whole team shares — it was cool seeing how one small script can stop a bad commit before it even happens.
- Realized fixed rules are great at catching obvious stuff like hardcoded secrets, but they can't think — they only catch what they're told to look for.
- Used AI review to catch things rules can't, like whether the code is well documented or the PR actually makes sense.
- Practiced the Agentic Loop — Gather, Analyze, Human Act, Verify — and understood why a human still has to be the one to actually commit and push. The AI can suggest, but it shouldn't have the final say.
- Learned that rules and AI work better together than alone. Rules catch what you already expect. AI catches what you didn't think to check.

---

# Submission Instructions

- Ensure `hooks/pre-commit` and `.claude/skills/pr-ready/SKILL.md` are committed to your GitHub repository
- Add all required screenshots to your submission
- All written answers must be in your own words
- Do not use a real secret or credential anywhere in your submission — the fake key in Task 1 is intentional and must stay clearly fake
- Open your Pull Request against your own fork, not the shared upstream repository
- Push your final changes to your forked repository
- Include your PR link and LinkedIn post URL

---

## GitHub Repository URL

https://github.com/Fhelobanty/devops-micro-internship-pravinmishra

`Add your URL here`

---

# Completion Checklist

- [ ] Branch `feature/ai-pr-ready` created with a staged file containing a fake secret and a debug statement
- [ ] `hooks/pre-commit` created and tracked in the repo (not only in `.git/hooks/`)
- [ ] `core.hooksPath` configured to point at `hooks/`
- [ ] Pre-commit hook shown blocking the risky commit
- [ ] `.claude/skills/pr-ready/SKILL.md` created with correct `allowed-tools` (no `Write`) and `disable-model-invocation: true`
- [ ] `/pr-ready` run against the risky diff and shown flagging issues
- [ ] Risky file fixed; `git commit` succeeds cleanly
- [ ] `/pr-ready` re-run showing a clean report and drafted PR title/description
- [ ] Pull Request opened using the AI draft as a starting point, with your own fork as the base repository (not upstream), PR link included
- [ ] Agentic Loop mapping (Task 7) completed in your own words
- [ ] LinkedIn post published and URL submitted
- [ ] All required screenshots added
- [ ] GitHub repository URL provided

---

## 📌 About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra (The CloudAdvisory) focused on real-world execution, systems thinking, and career readiness.

It helps learners build strong DevOps foundations with hands-on experience.

---

## 📌 Resources

- 🌐 DMI Official Website: https://pravinmishra.com/dmi  
- 🎓 DevOps for Beginners (Udemy): https://www.udemy.com/course/devops-for-beginners-docker-k8s-cloud-cicd-4-projects/  
- 🎓 Agentic AI DevOps with Claude Code: https://www.udemy.com/course/ultimate-agentic-ai-devops-with-claude-code/  
- 🎓 DevOps with Claude Code: Terraform, EKS, ArgoCD & Helm: https://www.udemy.com/course/devops-with-claude-code-terraform-eks-argocd-helm/  
- ▶️ YouTube Playlist: https://www.youtube.com/playlist?list=PLFeSNDtI4Cho  
- 🔗 Pravin Mishra (LinkedIn): https://www.linkedin.com/in/pravin-mishra-aws-trainer/  
- 🏢 CloudAdvisory (LinkedIn): https://www.linkedin.com/company/thecloudadvisory/

---

*This submission is part of DevOps Micro Internship (DMI) Cohort 3 — Agentic AI Track.*
