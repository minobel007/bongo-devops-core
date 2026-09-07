# 🚀 DevOps & Version Control Core Missions

This repository documents the completion of Phase 1 and Phase 2 DevOps version control missions using Git Bash and VS Code.

---

## Phase 1: The Foundations (Basics)

### Task 01: The "First Impression" (Identity & Setup)
* **Objective:** Initialize a repository and set global author credentials.
* **Commands Used:**

  git config --global user.name "minobel007"
  git config --global user.email "minobelcuet@gmail.com"

  mkdir bongo-devops-core
  cd bongo-devops-core
  git init
  touch README.md
  git add README.md
  git commit -m "chore: initial repository setup"

* **Verification:** Verified initial commit history using git log.

---

### Task 02: The "Safe Space" (.gitignore)
* **Objective:** Prevent sensitive files (API keys/passwords) from being tracked by Git.
* **Commands Used:**

  echo "PASSWORD=mysecretpassword123" > .env
  echo ".env" > .gitignore

  git add .gitignore
  git commit -m "chore: add .gitignore to untrack sensitive files"

* **Verification:** Ran git status to ensure .env was ignored and untracked.

---

### Task 03: The "Parallel Universe" (Branching)
* **Objective:** Isolate feature development from the production branch (main).
* **Commands Used:**

  git checkout -b feature/system-optimization

  echo "kernel.sched_latency_ns = 18000000" > kernel_tuning.txt
  git add kernel_tuning.txt
  git commit -m "feat: add kernel tuning settings"

  git checkout main

* **Verification:** Verified that kernel_tuning.txt disappears on main branch and reappears on feature branch.

---

### Task 04: The "Selective Memory" (Staging)
* **Objective:** Stage and commit modified files separately for clean commit history.
* **Commands Used:**

  touch web_fix.conf db_fix.conf

  git add web_fix.conf
  git commit -m "fix: resolve web configuration issue"

  git add db_fix.conf
  git commit -m "fix: resolve database configuration issue"

* **Verification:** Confirmed two distinct commit entries in git log.

---

### Task 05: The "Cloud Connection" (GitHub Integration)
* **Objective:** Link the local repository to GitHub and push all branches.
* **Commands Used:**

  git remote add nobel https://github.com/minobel007/bongo-devops-core.git

  git branch -M main
  git push -u nobel main
  git push -u nobel feature/system-optimization

* **Verification:** Checked the GitHub browser interface to verify remote branches and history.

---

## Phase 2: The Engineer's Workflow (Intermediate)

### Task 06: The "History Detective" (Investigation)
* **Objective:** Track line-by-line file changes and locate who introduced a configuration change.
* **Commands Used:**

  git log -p -S "port"

  git blame config.txt

* **Verification:** Identified the exact Commit Hash (ea9b6d5) and Author (minobel007) responsible for updating config.txt.

---

### Task 07: The "Safety Net" (Context Switching with Stash)
* **Objective:** Temporarily shelter uncommitted work to fix an urgent production bug.
* **Commands Used:**

  echo "print('Work in progress')" > feature.py
  git stash -u

  echo "print('Production Bug Fixed')" > main.py
  git add main.py
  git commit -m "resolve critical production bug"

  git stash pop

* **Verification:** Confirmed feature.py was restored to working directory while main.py remained committed.

---

### Task 08: The "Clean Merge" (Squash Merge)
* **Objective:** Combine multiple small "fix" commits into a single clean commit on main.
* **Commands Used:**

  git checkout feature/system-optimization

  echo "change 1" >> kernel_tuning.txt && git commit -am "fix: typo 1"
  echo "change 2" >> kernel_tuning.txt && git commit -am "fix: typo 2"
  echo "change 3" >> kernel_tuning.txt && git commit -am "fix: typo 3"

  git checkout main
  git merge --squash feature/system-optimization
  git commit -m "feat: optimize system kernel settings"

* **Verification:** Ran git log --oneline on main to confirm commits were squashed into one.

---

### Task 09: The "Conflict Resolution" (Branch Management)
* **Objective:** Intentionally trigger, inspect, and manually resolve a merge conflict.
* **Commands Used:**

  echo "Main branch modification" >> optimization.txt
  git commit -am "update optimization in main"

  git checkout feature/conflict-test
  echo "Feature branch modification" >> optimization.txt
  git commit -am "update optimization in feature"

  git checkout main
  git merge feature/conflict-test
  
  git add optimization.txt
  git commit -m "fix: resolve merge conflict manually"

* **Verification:** Ensured working copy contained clean, unified code without Git conflict markers.

---

### Task 10: The "Time Machine" (Reflog Recovery)
* **Objective:** Recover a commit deleted by a hard reset.
* **Commands Used:**

  git reset --hard HEAD~1

  git reflog

  git reset --hard a8e73c9

* **Verification:** Confirmed deleted files and commit history were fully restored.