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
