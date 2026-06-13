# Git & GitHub: The Lifecycle of Collaboration

## Why We Use It at Federated Engineers
At Federated Engineers, code is never written in a vacuum. We are a highly integrated, collaborative engineering organization. Every single feature, infrastructure change, data pipeline, and bug fix passes through Git and GitHub. 

Mastering Git isn't just about knowing `git commit` and `git push`. It’s about maintaining code quality, ensuring a clean and readable repository history, and respecting your team’s velocity. A sloppy Git workflow introduces bugs, breaks CI/CD pipelines, and slows everyone down. Conversely, a clean Git workflow is the catalyst for rapid, safe deployment.

---

## Core Concepts You Must Master

To be fully effective on our team, you must move past basic commands and be comfortable with the following concepts:

1. **The Three States:** Understand how files move between your *Working Directory*, the *Staging Area* (Index), and the *Commit History* (HEAD).

2. **Feature Branching:** We never commit directly to `main`. Every task gets its own short-lived branch named using our convention (e.g., `feature/jira-ticket-id` or `fix/issue-name`).

3. **The Power of Rebase:** We prefer keeping a clean, linear commit history. You should know how to use `git rebase` to bring changes from `main` into your feature branch without introducing messy merge commits.

4. **Peer Reviews & Pull Requests (PRs):** Your PR is your canvas. It should clearly explain *what* you changed and *why*. It triggers automated tests, and must be reviewed by at least one peer before merging.

---

## Fast-Track Resources (Curated YouTube Videos)

We highly recommend watching these videos to solidify your mental model before jumping into production repositories:

*  [Git & GitHub Crash Course for Beginners (freeCodeCamp)](https://www.youtube.com/watch?v=RGOj5yH7evk) — A phenomenal, comprehensive foundation covering local vs. remote workflows.

*  [Git Merge vs. Rebase: What's the Difference?](https://www.youtube.com/watch?v=0chZFIZLR_0) — A visually clear breakdown of when and why to use rebase over merge to maintain a clean history.

*  [How to Handle Git Merge Conflicts with Confidence](https://www.youtube.com/watch?v=JtIX3HJKwfo) — Merge conflicts are a daily reality in collaborative teams. Learn how to diagnose and fix them using your IDE safely.

---

## The Acceleration Exercise

To prove you are comfortable with our collaborative workflow, navigate to the `01-local-essentials/exercises/` directory and complete the **Merge Conflict Resolution** exercise. 

## Objective: 

You will simulate a real-world scenario where a teammate has modified the exact same file as you on the `main` branch. You will be tasked with pulling their changes, encountering a conflict, resolving it locally without losing data, and prepping a clean commit to push.

## Steps to execute:

1. Open your terminal and create a new local branch: 
   ```bash
   git checkout -b feature/yourname-git-practice
