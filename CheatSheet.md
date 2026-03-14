# Module 7: Command Line Basics

### File & Directory Management
* `mkdir folder_name` - Creates a new directory.
* `touch file_name` - Creates a new, empty file.
* `cp source destination` - Copies a file.
* `mv old_name new_name` - Moves or renames a file.
* `rm file_name` - Deletes a file permanently.

### Pipes & Redirects
* `>` (Overwrite) - Puts command output into a file, erasing what was there.
* `>>` (Append) - Adds command output to the bottom of a file safely. 
* `grep "word" file.txt` - Searches inside a file for a specific word.


# Module 8: Shell Scripting Basics

### Script Foundations
* `#!/bin/bash` - The "Shebang". Must be the very first line of every script. Tells the OS to use Bash.
* `chmod 755 script.sh` - The numeric way to make a script executable for the owner, and readable/executable for everyone else.
* `./script.sh` - Runs a script located in your current directory.

### Variables & Arguments
* `NAME="Aavi"` - Assigns a variable (NO spaces around the equals sign!).
* `echo $NAME` - Prints the variable (Must use `$` to call it).
* `$1`, `$2`, `$3` - Positional arguments. `$1` grabs the first word typed after the script name when running it (e.g., `./script.sh argument1`).


# Module 9: Environment Variables

### Managing Variables
* `printenv` - Displays all currently loaded system environment variables.
* `export API_KEY="Secret123"` - Creates a temporary environment variable in the current terminal session.
* `$API_KEY` - How to read an environment variable inside a shell script.

### Security Best Practice
* Never hardcode sensitive data (passwords, API keys, database URLs) directly into your code. Store them as Environment Variables on the server so your code can read them safely!


# Module 10: Networking Essentials

### Essential Networking Commands
* `ip a` - Displays all network interfaces and the private IP address of the server.
* `hostname -I` - Quickly displays only the server's IP address without the extra network clutter.
* `ping -c 3 domain.com` - Tests internet connectivity by sending exactly 3 packets to check for packet loss. 
* `sudo ufw status` - Checks if the Uncomplicated Firewall (UFW) is active or inactive.

### Core Concepts
* **Gateway:** The router connecting your local network (LAN) to the outside internet (WAN).
* **CIDR Notation:** The `/24` at the end of an IP address (like `10.211.55.5/24`) defining the size of the network.
* **Firewalls:** Block all incoming traffic by default when active. Ports must be explicitly opened (e.g., Port 80 for web) to host a website.


# Module 11: Secure Shell (SSH)

### SSH Core Commands
* `ssh user@ip_address` - Connects securely to a remote server.
* `ssh-keygen` - Generates a new Public/Private cryptographic key pair (defaulting to the highly secure Ed25519 curve on modern systems).
* `cat ~/.ssh/id_ed25519.pub` - Displays your public key so you can copy and paste it into GitHub or external servers.

### SSH Architecture
* **Public Key (.pub):** The padlock. Safe to share with the world.
* **Private Key:** The physical key that unlocks the padlock. Stored securely on your local machine with strict `600` permissions. NEVER share, copy, or expose this file!
* `~/.ssh/config` - A configuration file used to create fast shortcuts for connecting to multiple remote servers.




# Git & GitHub Mastery

## Module 1: Introduction to Version Control
### Core Concepts
* **Git:** A local software engine installed on your computer that tracks changes to your code over time. It works 100% offline.
* **GitHub:** A cloud-based hosting service (owned by Microsoft) used to store, share, and collaborate on Git repositories.
* **The `.git` folder:** A hidden directory created when you initialize Git. It acts as the "brain" and database for all your project's version history.

### Essential Setup Commands
* `git config --global user.name "Your Name"` - Sets the author name attached to all your future code snapshots.
* `git config --global user.email "your@email.com"` - Sets the author email.
* `git init` - Transforms a standard directory into a tracked Git repository.
* `git status` - The most used Git command. Tells you the current state of your repository, what branch you are on, and if there are pending changes.



## Module 2: Basic Concepts of Git

### Core Vocabulary
* **Repository:** Your project folder with the hidden `.git` brain attached. Holds all files and version history.
* **Commit:** A permanent "save state" snapshot of your code at a specific moment in time.
* **Branch:** An independent, alternate timeline of your code where you can safely build new features without breaking the main project.
* **HEAD:** A pointer indicating your current location in the repository (The "You Are Here" marker).

### The 3-Step Commit Workflow
* `git status` - Checks the state of your working directory (red = untracked/modified, green = staged).
* `git add filename` - Moves a file to the Staging Area (the loading dock). Use `git add .` to stage ALL changed files at once.
* `git commit -m "Your message here"` - Permanently locks the staged changes into a new commit snapshot.
* `git log` - Displays the timeline history of all commits.



## Module 4: Working with Git

### Creating & Copying Repositories
* `git init` - Initializes a brand new, empty Git repository in your current local directory.
* `git clone <repository-url>` - Downloads an existing repository from a remote server (like GitHub) to your local machine, including all files and its entire `.git` history vault.

### The Golden Rule of Git
* You **must** be `cd`'d inside the specific project folder (the one containing the hidden `.git` directory) to run commands like `git status`, `git commit`, or `git log`. If you are outside the folder, Git will throw a `fatal: not a git repository` error.



## Module 5: Git Branching and Workflow

### The Power of Branching
Branches are isolated, alternate timelines of your code. They allow developers to build and test new features safely without risking the stability of the `main` production code.

### Core Branching Commands
* `git branch <branch-name>` - Creates a new branch, but leaves you on your current branch.
* `git checkout <branch-name>` - Moves your `HEAD` pointer to an existing branch.
* `git checkout -b <branch-name>` - The Pro Shortcut: Creates a new branch AND immediately switches you to it.
* `git branch -d <branch-name>` - Safely deletes a local branch after you are done with it.



## Module 6: Git Merge and Rebase

### Combining Timelines
* **Merge:** Takes a feature branch and safely ties it back into the `main` branch. It preserves the complete, exact history of everything that happened. 
* **Rebase:** Rewrites history by taking your feature branch commits and placing them directly on top of the `main` branch, creating a perfectly straight, linear timeline. (Warning: Never rebase a public branch!)

### Core Commands
* `git merge <branch-name>` - Merges the specified branch into your *currently active* branch (Always make sure you `git checkout main` before merging a feature into it!).
* `git rebase <branch-name>` - Rebases your current branch onto the target branch.



## Module 7: Undoing Changes with Git

### The 4 "Undo" Buttons of DevOps
1. **`git restore <file>`:** Discards uncommitted, local changes in a file. It pulls the last saved version from the repository and overwrites your working file.
2. **`git reset <commit-hash>`:** A time machine that rewinds your local commit history backward. 
   * `--soft`: Keeps your code changes on the staging area.
   * `--mixed`: Keeps your code changes in your working directory.
   * `--hard`: **DANGER.** Completely deletes the commits AND your code changes.
3. **`git revert <commit-hash>`:** The "Safe Undo" for public branches. Instead of deleting a bad commit, it creates a brand new commit that does the exact mathematical opposite of the mistake.
4. **`git commit --amend`:** Unzips your very last commit so you can add a forgotten file or fix a typo in the commit message, then seamlessly zips it back up.



## Module 8: Resolving Merge Conflicts

### What is a Merge Conflict?
A merge conflict is not an error! It happens when Git pauses a merge because two different branches modified the exact same line of the exact same file. Git halts the process and asks a human to decide which code to keep.

### How to Resolve a Conflict (The 4-Step Process)
1. **Identify:** Git injects alien markers (`<<<<<<<`, `=======`, `>>>>>>>`) into the conflicted file to show you exactly where the collision happened.
2. **Edit:** Open the file in a text editor (like Vim or nano), delete the alien markers, and manually edit the code so it looks exactly how you want the final version to look.
3. **Stage:** Save the file and tell Git you fixed it by running `git add <file-name>`.
4. **Complete:** Finish the paused merge process by running `git merge --continue`.



## Module 9: SSH Keys & Authentication

### What is SSH?
Secure Shell (SSH) provides a highly secure way to authenticate with remote servers (like GitHub) without using a username and password. It uses a cryptographic key pair: a private key (which stays on your local machine) and a public key (which you give to the server).

### Core SSH Commands
* `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"` - Generates a brand new 4096-bit RSA key pair.
* `cat ~/.ssh/id_rsa.pub` - Prints your public key to the terminal so you can copy it to GitHub.
* `ssh -T git@github.com` - Tests your connection to GitHub to verify your keys are working correctly.



## Module 10: Git Clients (CLI vs. GUI)

### The Command Line Interface (CLI)
The industry standard for DevOps and Backend Engineering. It offers total control and is required for managing remote cloud servers where graphical interfaces do not exist.

### Graphical User Interfaces (GUI)
Visual tools that make it easier to see branch histories and complex merges. 
* **GitHub Desktop:** Beginner-friendly, simple commits.
* **SourceTree / GitKraken:** Advanced visualizers for complex enterprise branching (Git Flow).

### The Ultimate CLI Visualizer
* `git log --graph --oneline --all` - Draws a colorful, visual map of all branches and merges directly inside the text terminal, eliminating the strict need for a GUI.



## Module 11: Advanced Git Commands

### The Surgical Tools
* **`git cherry-pick <commit-hash>`:** Duplicates a single, specific commit from one branch and applies it to your current branch without merging the entire timeline. Perfect for emergency hotfixes.
* **`git diff <commit1> <commit2>`:** Outputs a color-coded line-by-line comparison showing exactly what code was added or deleted between two snapshots.
* **`git log --oneline`:** Condenses your commit history so each commit takes up exactly one line, making large repository histories easy to read.
* **`git tag <tag-name>`:** Attaches a permanent, readable label (like `v1.0` or `production-release`) to a specific commit.



## Module 12: The Magical Pocket (Git Stash)

### What is Stashing?
When you are in the middle of working on broken or unfinished code, but you suddenly need to switch branches to fix an emergency, you use `git stash`. It acts as a temporary clipboard that holds your uncommitted changes so you can have a clean working directory.

### Core Stash Commands
* **`git stash`:** Takes all uncommitted modifications and saves them to a temporary pocket, leaving you with a clean working directory.
* **`git stash list`:** Shows you a list of all the different changes you currently have stashed away.
* **`git stash pop`:** Removes the most recently stashed files from the pocket and applies them back into your working directory.
* **`git stash apply`:** Applies the stashed files to your working directory, but keeps a backup copy in the stash pocket.



## Module 13: Advanced Merging (Squash)

### The Problem with Normal Merges
When working on a feature branch, developers often make dozens of small, messy commits ("wip", "fixing typo", "forgot file"). Merging these normally clutters the main repository history.

### The Squash Merge Solution
* **`git merge --squash <branch-name>`:** Takes all the commits from a feature branch, crushes them into a single chunk of changes, and places them on the staging area of your current branch.
* **`git commit -m "Clean feature description"`:** After squashing, you create one single, clean commit to represent all the work, keeping the `main` branch history perfectly linear and professional.
