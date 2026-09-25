<div align="center"><img src="https://github.com/ksyv/holbertonschool-web_front_end/blob/main/baniere_holberton.png"></div>

# Git - SCM Basics

## Table of Contents :

  - [0. Initial Setup](#subparagraph0)
  - [1. First Commits](#subparagraph1)
  - [2. Push and Pull with Remote Repository](#subparagraph2)
  - [3. Branch Creation](#subparagraph3)
  - [4. Merge and Conflict Resolution](#subparagraph4)
  - [5. Rollback to a Previous Version](#subparagraph5)
  - [6. Complete Workflow](#subparagraph6)
# **Versioning Like a Pro: Introduction to Git and GitHub**

In modern software development, **version control** is a fundamental skill. Git allows developers to record every change, go back in time to stable versions, and experiment safely with new ideas. GitHub extends these capabilities by providing an online platform for collaboration, code review, and team-based workflows.

This project is designed for **beginners with no prior Git knowledge**. Through seven guided tasks, learners will progressively discover how to:

* Set up Git and configure their identity.
* Track files and create commits.
* Connect a local repository to GitHub and exchange changes with it.
* Work with branches, merges, and conflict resolution.
* Perform rollbacks to restore stability.
* Simulate a **complete professional workflow** with Pull Requests, merge conflicts, and rollbacks.

By the end, learners will not only understand the theory but will also have **practical, hands-on experience** with the core Git and GitHub workflow.

---

## **Learning Objectives**

By completing this project, learners will be able to:

1. **Install and configure Git** with a user identity.
2. **Create and manage a repository** locally and remotely on GitHub.
3. **Track changes** using commits, with a clear understanding of the working directory, staging area, and repository history.
4. **Use `.gitignore`** to exclude unnecessary files.
5. **Push and pull** changes between a local and remote repository, authenticating securely with a Personal Access Token.
6. **Work with branches**, isolating development and understanding the branching model.
7. **Merge branches** and handle conflicts effectively.
8. **Perform rollbacks** using both `git reset` and `git revert`.
9. **Apply the complete GitHub Flow**: branch → commit → push → Pull Request → merge → conflict resolution → rollback.

---

## **Competences Developed**

### **Technical Competences**

* Proficiency with essential Git commands: `init`, `add`, `commit`, `status`, `log`, `branch`, `checkout`, `merge`, `push`, `pull`, `reset`, `revert`, `tag`.
* Ability to configure remotes, set upstream branches, and authenticate with tokens.
* Experience with GitHub’s Pull Request workflow and conflict resolution interface.

### **Professional Competences**

* Writing clear and descriptive commit messages.
* Using branching strategies for clean collaboration.
* Solving conflicts in a structured, safe way.
* Applying rollback strategies responsibly depending on context.

### **Transferable Competences**

* Readiness for teamwork in professional software environments.
* Adaptability to different version control platforms (GitHub, GitLab, Bitbucket).
* Problem-solving in real development workflows (conflicts, rollbacks, remote sync).

---

## **Resources**

* **Official Git documentation**:

  * [Pro Git Book](/rltoken/87MA7esG5TqdkDT4xVmNqw)
  * [Git Command Reference](/rltoken/MGxUEpcr56kLJyxbsWm18g)

* **GitHub documentation**:

  * [Getting Started with GitHub](/rltoken/y_b7WxdckNAO02kACOvswA)
  * [GitHub Flow](/rltoken/jUz-IoDSCsT2-SS9JqHGiw)
  * [Managing Merge Conflicts](/rltoken/NSKp5reUQVofwwu9dwYSVw)


## Task
### 0. Initial Setup <a name='subparagraph0'></a>

### **Learning Resources (read before starting)**

* What is Version Control? (Git Book)
* Installing Git
* GitHub – Create a repository

### **Objective**

Install Git, configure your identity, create your first **repository**, and connect it to GitHub.

### **Concepts You Need**

* **Repository**: a folder where Git stores the complete history of your project.
* **Working directory**: the files you see and edit normally in your project folder.
* **Staging area**: a temporary place where you prepare files before committing them.
* In this task, we will only set up the repository — you’ll work with staging and commits later.

### **Step-by-Step Instructions**

1. **Check if Git is installed**
Run:

```bash
git --version
```

If you don’t see a version number, install Git from git-scm.com.

1. **Set up your identity**
Configure your name and email (these will appear in every commit you make):

```bash
git config --global user.name "Your Name"
   git config --global user.email "your@email.com"
```

1. **Create a project folder under /root and initialize Git**

```bash
cd /root
   mkdir git-intro
   cd git-intro
   git init
```

👉 What happens here:

* `git init` creates a **new repository** inside your folder.
* Now Git is ready to track files in this project.
* Run:
`git status`
You’ll see that the repository is empty and waiting for your first file.

1. **Create a remote repository on GitHub**

* Log into GitHub → click **New repository**.
* Name it (e.g., `git-intro`).
* Do **not** add a README or .gitignore yet (we’ll create them locally).

1. **Connect your local repo to GitHub**

```bash
git remote add origin https://github.com/<your-username>/<repo>.git
```

👉 What happens here:

* `origin` is the nickname for your GitHub repository.
* This lets you later **push** your work to GitHub and **pull** updates.
* Run:
`git remote -v`
You should see your GitHub URL listed.

### **Checkpoint**

* `git status` → should say **“No commits yet.”**
* `git log` → will show an error because there are no commits yet (this is expected).
* `git remote -v` → shows the GitHub repo URL under `origin`.

### **Expected Outcome**

* You now have a **local repository** initialized.
* Your repository is linked to **GitHub** with the remote named `origin`.
* You can use `git status` to check the repo state.

---

### 1. First Commits <a name='subparagraph1'></a>

### **Learning Resources (read before starting)**

* Recording Changes to the Repository (Git Book)
* gitignore Documentation

### **Objective**

Create your first files, understand the **staging area**, make your first **commits**, and set up a `.gitignore` file.

### **Concepts You Need**

* **Working directory**: the files you edit normally in your project folder.
* **Staging area**: a preparation zone where you tell Git *which changes* will go into the next commit.
* **Commit**: a snapshot of your project at a specific moment, stored in the repository history.
* **.gitignore**: a file that lists patterns of files Git should ignore (e.g., logs, temporary files, system files).
* **Tracked files**: files that Git is already following and will show up in commits.
* **Untracked files**: files that exist in your folder but Git doesn’t know about yet.

👉 Think of it like this:

* *Working directory = your desk with documents you are editing.*
* *Staging area = a tray where you place the documents you are ready to archive.*
* *Commit = archiving that tray into a permanent cabinet with a label.*
* *.gitignore = a sticky note saying “Don’t archive receipts, drafts, or scratch notes.” In practice, this is where you list things like `*.log` files, system cache files, or temporary editor files that don’t belong in history.*
* *Tracked vs. untracked = tracked are the documents Git is already watching; untracked are the ones lying on your desk that Git hasn’t been told to care about yet.*

### **Step-by-Step Instructions**

1. **Create a README.md file**

```bash
echo "# Git Intro Project" > README.md
   git status
```

👉 You’ll see `README.md` listed as **untracked**, meaning Git sees it but isn’t storing it yet.

1. **Add README.md to staging**

```bash
git add README.md
   git status
```

👉 Now `README.md` is in the **staging area** — ready to be committed.

1. **Commit the staged file**

```bash
git commit -m "Add initial README"
   git log
```

👉 You’ve created your first **commit**. Use `git log` to see the history (currently just one commit).

1. **Create a .gitignore file**

```bash
echo "*.log" > .gitignore
   git status
```

👉 `.gitignore` tells Git to ignore all files ending in `.log`. These will never appear as untracked files.

1. **Stage and commit the .gitignore**

```bash
git add .gitignore
   git commit -m "Add .gitignore for log files"
   git log
```

👉 Now you should see **two commits**: one for the README, one for the .gitignore.

1. **Test that .gitignore works**

```bash
echo "This is a test log" > test.log
   git status
```

👉 `test.log` should **not appear** in the status, because `.gitignore` is telling Git to ignore it.

### **Checkpoint**

* `git status` shows no pending changes (clean working directory).
* `git log` shows **at least two commits** with clear messages.
* `.gitignore` exists, contains `*.log`, and works.
* `test.log` does not appear as tracked or untracked.

### **Expected Outcome**

* You’ve made your **first commits** and understand the flow: *untracked → staging → commit*.
* You know how to exclude unwanted files with `.gitignore`.
* You can confidently use `git status` and `git log` to inspect the state of your repository.

---

### 2. Push and Pull with Remote Repository <a name='subparagraph2'></a>

### Learning Resources (read before starting)

* Working with Remotes (Git Book)
* Creating a Personal Access Token (Classic)

### Objective

Send your local commits to GitHub (**push**) and bring changes (**pull**) while configuring **in-memory credential caching** on Linux so authentication works automatically for a limited time (needed by the **checker**).

### Concepts You Need

* **Remote repository**: the copy of your project hosted on GitHub.
* **Push / Pull**: send local commits to GitHub / fetch and integrate commits from GitHub.
* **Personal Access Token (Classic)**: used instead of a password for HTTPS authentication.
* **Credential cache**: stores your token **temporarily in memory** (not on disk) so future pushes/pulls don’t ask for credentials again.

⚠️ **Warning (about the cache):**

* Credentials are kept **in memory only** and expire after the timeout.
* If you restart the computer or wait too long, you’ll need to re-enter your token.
* This method is safe enough for classroom use, but not ideal for production servers.

### Step-by-Step Instructions (Linux)

1. **Ensure your branch is `main`**

```bash
git branch -M main
   git status   # confirm you’re on main
```

*Why:* GitHub uses `main` as the default branch.

1. **Create a Personal Access Token (Classic)**

* GitHub → **Settings → Developer settings → Personal access tokens → Tokens (classic)**.
* Click **Generate new token (classic)**.
* Scope: select **repo**.
* Copy the token (you’ll only see it once).
 *Why:* GitHub no longer accepts passwords for HTTPS.

1. **Enable credential caching (2-hour timeout)**

```bash
git config --global credential.helper 'cache --timeout=7200'
```

*Why:* This keeps your token in memory for ~2 hours, long enough to complete all tasks and pass the checker.

1. **Do the first authenticated push (saves the token in memory)**

```bash
git push -u origin main
```

When prompted:

* **Username:** your GitHub username
* **Password:** your token
👉 After this, Git will reuse the cached token automatically.

1. **Verify pulling works**

```bash
git pull origin main
```

If nothing has changed on GitHub, it will say *“Already up to date.”*

### Checkpoint

* `git branch -vv` shows `main` tracking `origin/main`.
* `git status` shows a clean working directory.
* `git pull origin main` works without prompting for credentials.
* Pushes and pulls are non-interactive for the next 2 hours (enough for the **checker**).

### Expected Outcome

* Your local `main` is linked to `origin/main` on GitHub.
* Credentials are cached in memory for 2 hours.
* Push/pull operations work non-interactively, enabling the **checker** to validate this task.

---

### 3. Branch Creation <a name='subparagraph3'></a>

### **Learning Resources (read before starting)**

* Branches in a Nutshell (Git Book)
* GitHub – About Branches

### **Objective**

Create a new **branch** to work on a change without affecting the main project, then switch between branches to see the difference.

### **Concepts You Need**

* **Branch**: a separate line of development in your project.
* **Main branch (`main`)**: the “official” version of your project.
* **Feature branch**: a branch where you try new ideas or features without breaking the main one.

👉 Think of it like this:

* *Main branch = the published version of a book.*
* *Feature branch = a draft version where you can experiment with new chapters.*
* Later, you can merge the draft back into the published version if it works well.

### **Step-by-Step Instructions**

1. **Check the current branch**

```bash
git status
```

👉 It should show you are on branch `main`.

1. **Create and switch to a new branch**

```bash
git checkout -b feature-greeting
   git status
```

👉 This creates a new branch called `feature-greeting` and moves you into it.

1. **Add a new file in the feature branch**

```bash
echo "Hello from my feature branch!" > greeting.txt
   git add greeting.txt
   git commit -m "Add greeting.txt in feature-greeting branch"
   git log --oneline --decorate --graph --all
```

👉 You now have a commit that exists **only** in `feature-greeting`.

1. **Switch back to main branch**

```bash
git checkout main
   ls
```

👉 Notice that `greeting.txt` is **not present** in the main branch yet.

### **Checkpoint**

* `git branch` shows at least two branches: `main` and `feature-greeting`.
* On `feature-greeting`, `greeting.txt` exists and is committed.
* On `main`, `greeting.txt` does not appear (since you haven’t merged yet).
* Use `git log --oneline --decorate --graph --all` to visualize both branches.

### **Expected Outcome**

* You understand what a **branch** is and why it’s useful.
* You’ve created your first branch (`feature-greeting`) and added a commit to it.
* You can switch between `main` and `feature-greeting` and see the difference in files.
* You know how to use `git status`, `git branch`, and `git log` to check your branches.

---

### 4. Merge and Conflict Resolution <a name='subparagraph4'></a>

### **Learning Resources (read before starting)**

* Basic Branching and Merging (Git Book)
* GitHub – About Merge Conflicts

### **Objective**

Learn how to combine changes from different branches (**merge**) and practice resolving a **conflict** when two branches change the same file in different ways.

### **Concepts You Need**

* **Merge**: the action of combining work from one branch into another.
* **Fast-forward merge**: when Git can simply move the branch pointer forward (no conflicts).
* **Merge conflict**: happens when two branches edit the same part of a file differently and Git doesn’t know which version to keep.

👉 Think of it like this:

* *If two people edit different pages of the same book, Git can merge automatically.*
* *If two people edit the same sentence differently, Git asks you to decide which version to keep (or to combine them).*

### **Step-by-Step Instructions**

1. **Prepare different changes in main**

```bash
git checkout main
   echo "Message from main branch" > message.txt
   git add message.txt
   git commit -m "Add message.txt in main branch"
```

1. **Make a conflicting change in feature branch**

```bash
git checkout feature-greeting
   echo "Message from feature branch" > message.txt
   git add message.txt
   git commit -m "Add message.txt in feature-greeting branch"
```

1. **Merge feature branch into main**

```bash
git checkout main
   git merge feature-greeting
```

👉 This will produce a **merge conflict**, because both branches changed `message.txt` differently.

1. **Resolve the conflict manually**

* Open `message.txt`. You will see conflict markers like:
`<<<<<<< HEAD
 Messagefrommain branch
 =======
 Messagefromfeature branch
 >>>>>>> feature-greeting`
* Edit the file to decide how the final text should look (you can combine them if you want).
* Stage the resolved file and commit:
`git add message.txt
 git commit -m"Resolve conflict in message.txt"`

1. **Inspect the history**

```bash
git log --oneline --decorate --graph --all
```

👉 You’ll see a **merge commit** joining the two branches.

```bash
# git log --oneline --decorate --graph --all
   *   ba1bfcd (HEAD -> main) Resolve conflict in message.txt
   |\
   | * b06f1ad (feature-greeting) Add message.txt in feature-greeting branch
   | * 61b909b Add greeting.txt in feature-greeting branch
   * | 94adae4 Add message.txt in main branch
   |/
   * 4601ba3 (origin/main) Add .gitignore for log files
   * b6fbf9b Add initial README
```

### **Checkpoint**

* On `main`, `message.txt` exists with the resolved content.
* There are **no conflict markers** (`<<<<<<<`, `=======`, `>>>>>>>`) left in the file.
* `git log --oneline --graph` shows a merge commit.
* `git status` shows a clean working directory.

### **Expected Outcome**

* You’ve learned how to **merge branches**.
* You’ve seen what a **conflict** looks like and how to solve it.
* You can use `git status` and `git log` to confirm the merge was successful.

---

### 5. Rollback to a Previous Version <a name='subparagraph5'></a>

### **Learning Resources (read before starting)**

* Git Tools – Reset Demystified (Git Book)
* Atlassian – Git revert

### **Objective**

Learn how to go back to an earlier version of your project when something goes wrong. You’ll practice using **reset** and **revert**.

### **Concepts You Need**

* **Commit history**: every commit is like a “save point” in your project.
* **Reset**: moves your branch pointer back to an earlier commit, changing history (dangerous if you already pushed to GitHub).
* **Revert**: creates a new commit that undoes the changes of a previous commit (safer when working with others).

👉 Think of it like this:

* *Reset = ripping a page out of your project’s history (others won’t see it anymore).*
* *Revert = writing a new page that says “undo what I wrote before.”*

### **Step-by-Step Instructions**

1. **Check your history**

```bash
git log --oneline
```

👉 You’ll see a list of commits with short hashes (IDs). Example:

```sql
a1b2c3d (HEAD -> main) Introduce breaking change
   e5f6g7h Add message.txt in main branch
   i9j0k1l Add greeting.txt in feature-greeting branch
   m2n3o4p Add .gitignore for log files
   q5r6s7t Add initial README
```

1. **Tag a known good commit**

```bash
git tag -a v1 -m "Stable version"
```

👉 Tags are like bookmarks to easily return to specific versions.

1. **Make a bad change**

```bash
echo "Breaking change" > broken.txt
   git add broken.txt
   git commit -m "Introduce breaking change"
   git tag -a v2 -m "Bad version"
```

1. **Rollback with revert (safe way)**

* Identify the hash of the bad commit, in this example `a1b2c3d`.
* Run:
`git revert a1b2c3d`
* Git will open your editor with a commit message like:
`Revert"Introduce breaking change"`
Save and close.
👉 Check history again:

```bash
git log --oneline
```

Example output:

```sql
z8y7x6w Revert "Introduce breaking change"
   a1b2c3d Introduce breaking change
   e5f6g7h Add message.txt in main branch
   ...
```

Now `z8y7x6w` is a **new commit** that cancels the effects of `a1b2c3d`. The file `broken.txt` is removed from your working directory.

1. **Rollback with reset (alternative way)**

* To forcefully return to the stable version:
`git reset --hard v1`
👉 Now the branch points back to the commit tagged `v1`.
⚠️ Warning: if you had already pushed the bad commit to GitHub, reset will cause problems for others. In that case, prefer revert.

### **Checkpoint**

* `git log --oneline` shows either:
* A **Revert commit** if you used `git revert`, or
* The **HEAD** pointing at `v1` if you used `git reset`.
* The file `broken.txt` is no longer in your working directory.
* `git status` shows a clean working directory.

### **Expected Outcome**

* You understand how to **rollback** to a safe version.
* You know the difference between **reset** (rewrite history) and **revert** (create a new commit to undo).
* You can confidently use `git log` and tags to navigate your history.

---

### 6. Complete Workflow <a name='subparagraph6'></a>

### Learning Resources (read before starting)

* Understanding the GitHub Flow
* Advanced Git Tutorials (Atlassian)

### Objective

Simulate a **real-world workflow**: work on a feature branch, push it to GitHub, create a Pull Request (PR), merge it into `main`, resolve a conflict, and finally perform a rollback if needed.

### Concepts You Need

* **Pull Request (PR)**: a request to merge changes from one branch into another.
* **Merge on GitHub**: combining branches through GitHub’s interface.
* **Conflict resolution**: fixing overlapping edits before merging.
* **Rollback**: undoing a mistake (with `git revert`, safer in collaboration).

⚠️ **Note about credential cache:**

In a previous task you configured the **credential cache** (`cache --timeout=7200`).

* It keeps your token in memory for about 2 hours.
* If the timeout expires or you restart your machine, you’ll need to re-enter your token the next time you push.
* This is normal and expected. Just repeat the push and provide your username/token when asked.

### Step-by-Step Instructions

#### **1. Create a new feature branch and push it**

```bash
git checkout -b feature-improvement
echo "Some improvement" > improvement.txt
git add improvement.txt
git commit -m "Add improvement.txt in feature-improvement"
git push -u origin feature-improvement
```

👉 If your credential cache expired, Git will prompt again for your username and token.

#### **2. Open a Pull Request (PR) on GitHub**

1. Go to your repository on GitHub.
2. Look for the banner: *“feature-improvement had recent pushes. Compare & pull request.”* → click it.

* If it doesn’t appear, go to the **Pull requests** tab → **New pull request**.
* Base = `main`, Compare = `feature-improvement`.

1. Fill out the PR form (title + description).
2. Click **Create pull request**.
3. On the PR page, click **Merge pull request** → **Confirm merge**.
4. Delete the branch on GitHub.

#### **3. Create a conflict intentionally**

* On `main`:

```bash
git checkout main
  echo "Change from main" > message.txt
  git commit -am "Change message in main"
  git push origin main
```

* On `feature-improvement`:

```bash
git checkout feature-improvement
  echo "Change from feature branch" > message.txt
  git commit -am "Change message in feature-improvement"
  git push origin feature-improvement
```

#### **4. Open a new Pull Request with a conflict**

1. On GitHub, open a PR from `feature-improvement` into `main`.
2. You’ll see: *“This branch has conflicts that must be resolved.”*
3. Click **Resolve conflicts**.
4. Edit `message.txt` directly in the browser, removing conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
5. Click **Mark as resolved** → **Commit merge**.
6. Then click **Merge pull request** → **Confirm merge**.

#### **5. Perform a rollback**

1. On your local repo, check history:

```bash
git log --oneline
```

Identify the hash of the bad commit (e.g., `a1b2c3d`).

1. Run:

```bash
git revert a1b2c3d
   git push origin main
```

👉 If the cache expired, Git will prompt again for your username and token.

1. On GitHub, you’ll see a new commit like:
*“Revert 'Introduce breaking change’”*.

### Checkpoint

* `git branch -vv` shows `main` and `feature-improvement`.
* At least one PR is merged in GitHub.
* A conflict was created and resolved.
* A rollback commit appears in `git log` and on GitHub.
* `git status` is clean.

### Expected Outcome

* You’ve gone through the **full GitHub flow**: branch → commit → push → PR → merge → conflict resolution → rollback.
* You understand that the **credential cache may expire** and how to re-enter your token if needed.
* You can confirm each step using `git status`, `git log`, and GitHub’s interface.

---


## Authors
Ksyv - [GitHub Profile](https://github.com/ksyv)
