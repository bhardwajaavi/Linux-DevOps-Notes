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




## Module 15: Interactive Rebasing (Rewriting History)

### What is Interactive Rebasing?
A powerful tool to clean up your local commit history before pushing to a shared remote repository. It allows you to pause time and modify commits that have already been made.
* **⚠️ Golden Rule:** NEVER rebase commits that have already been pushed to a public branch.

### Core Rebase Commands
* **`git rebase -i HEAD~3`:** Opens an interactive editor for the last 3 commits.
  * Change `pick` to `reword` (or `r`) to change a commit message.
  * Change `pick` to `squash` (or `s`) to meld a commit into the previous one.
  * Change `pick` to `drop` (or `d`) to completely delete a commit.




# Phase 2: DevOps Packaging & Containerization

## Module 1: Build Tools & Artifacts (Python)

### Core Concepts
* **Package Manager (`pip`, `npm`, `Maven`):** The tool that downloads external libraries (dependencies) from the internet into your project.
* **Virtual Environment (`venv`):** An isolated "clean room" on your server. Packages installed here will not break the rest of your computer.
* **Artifact:** The final, deployable package or recipe. In standard Python, this is your `requirements.txt` file.
* **Artifact Repository:** The digital warehouse (like Nexus or Docker Hub) where finished artifacts are stored for production servers to download.

### Python Build Commands
| Command | What It Does |
| :--- | :--- |
| `python3 -m venv my_env` | Creates an isolated virtual environment named `my_env`. |
| `source my_env/bin/activate` | Enters the virtual environment (activates the clean room). |
| `pip install <package>` | Downloads and installs a package *only* inside the active environment. |
| `pip freeze > requirements.txt` | Takes a snapshot of all installed packages and saves it as an artifact. |
| `deactivate` | Exits the virtual environment and returns to the normal Linux terminal. |

---

## Module 2: Docker Fundamentals

### Core Concepts
* **Docker Image:** The read-only blueprint or template. It contains your OS, code, and dependencies perfectly packaged together.
* **Docker Container:** The running, isolated steel box created from the Image. You can run hundreds of identical containers from one single image.
* **Containers vs. VMs:** Virtual Machines require an entire heavy Operating System to run. Docker containers are lightweight because they share the host server's Linux kernel.
* **Docker Daemon:** The background manager on your server that actually builds, runs, and downloads containers.
* **Docker Registry:** The global internet warehouse (Docker Hub) where you download official images.

### Docker Installation & Setup Commands
| Command | What It Does |
| :--- | :--- |
| `sudo apt install docker.io -y` | Installs the core Docker engine on an Ubuntu server. |
| `sudo usermod -aG docker parallels` | Grants your specific user VIP permission to command the Docker Daemon without typing `sudo` every time. |
| `newgrp docker` | Refreshes your terminal permissions instantly to activate the VIP pass. |
| `docker --version` | Verifies the Docker engine is installed and running. |
| `docker run hello-world` | Reaches out to the internet, pulls the official `hello-world` image, and runs it inside a secure container. |




## Module 3: Docker Commands & Debugging

### Core Operations
* **`docker pull <image>`:** Downloads a blueprint from Docker Hub without running it.
* **`docker images`:** Lists all downloaded blueprints sitting in your local warehouse.
* **`docker ps`:** The active radar. Lists all currently running containers.
* **`docker ps -a`:** Lists ALL containers, including ones that have crashed or stopped.
* **`docker run -d -p 8080:80 --name my_website nginx`:** * `-d`: Runs the container in the background (detached).
  * `-p 8080:80`: Drills a hole mapping your host machine's port 8080 to the container's port 80.
  * `--name`: Gives the container a human-readable name instead of a random hash.

### Debugging & Hacking
* **`docker logs <container_name>`:** Prints the internal server logs (errors, print statements, web traffic).
* **`docker exec -it <container_name> bash`:** Infiltrates a running container and opens an interactive root terminal inside it.











# 🐳 Docker — Complete DevOps Cheatsheet

---

## Module 1: What is Docker & How It Works

### Core Concepts

* **The Problem Docker Solves:** Eliminates the "It works on my machine" problem by packaging your app together with everything it needs — OS layer, runtime, libraries, config — into one portable, isolated unit.
* **Docker Image:** The read-only blueprint or recipe. It describes exactly what the container should contain. Sits there and does nothing on its own.
* **Docker Container:** The live, running instance created from an image. One image can run hundreds of identical containers simultaneously.
* **Docker Engine:** The complete background service installed on your machine that makes everything work.
* **Docker Daemon (`dockerd`):** The actual server process inside the Engine that does the heavy lifting — building, running, and managing containers.
* **Docker Client (`docker`):** The CLI tool you type commands into. Sends your instructions to the Daemon and returns the result.
* **Docker Hub:** The global public library (registry) of pre-built images. The Daemon pulls from here automatically when an image isn't found locally.

### Containers vs. Virtual Machines

| | Virtual Machine | Docker Container |
| --- | --- | --- |
| **Includes** | Full OS + your app | Just your app + its dependencies |
| **Size** | GBs | MBs |
| **Startup Time** | Minutes | Seconds |
| **Isolation** | Complete (hypervisor) | Process-level (shared kernel) |

### The Restaurant Analogy

* **You** = Docker Client (you place the order)
* **Waiter** = Docker Daemon (takes the order to the kitchen)
* **Kitchen** = Docker Engine (produces the result)

---

## Module 2: Images vs. Containers

### Core Concepts

* **Image:** A static, read-only blueprint. Like a `.exe` installer file — it just sits there.
* **Container:** A live, running process built from the image. Like the installed, running application.
* **Key Rule:** One image → infinite containers. You can run 5, 10, or 1000 containers from a single image simultaneously.

### Essential Image Commands

| Command | What It Does |
| --- | --- |
| `docker images` | Lists all images downloaded on your local machine. |
| `docker pull <image>` | Downloads an image from Docker Hub without running it. |
| `docker rmi <image>` | Deletes a downloaded image from your machine. |
| `docker image prune` | Deletes all unused (dangling) images at once. |

---

## Module 3: Essential Container Commands

### Viewing Containers

| Command | What It Does |
| --- | --- |
| `docker ps` | Lists ONLY currently running containers. |
| `docker ps -a` | Lists ALL containers — running AND stopped. |

### Reading `docker ps` Output

| Column | Meaning |
| --- | --- |
| `CONTAINER ID` | Unique short ID for that specific instance. |
| `IMAGE` | The blueprint it was built from. |
| `COMMAND` | The exact process running inside it. |
| `STATUS` | `Exited (0)` = success. `Exited (1)` = crashed. |
| `PORTS` | Port mappings between host and container. |
| `NAMES` | Human-readable name (auto-assigned if not set). |

### Starting & Stopping

| Command | What It Does |
| --- | --- |
| `docker start <name>` | Restarts a stopped container. |
| `docker stop <name>` | Gracefully stops a running container. |
| `docker restart <name>` | Stops and starts a container in one command. |

### Cleaning Up

| Command | What It Does |
| --- | --- |
| `docker rm <name>` | Deletes a stopped container permanently. |
| `docker rm -f <name>` | Force-deletes a container even if it's running. |
| `docker container prune` | Deletes ALL stopped containers at once. |

### Inspecting & Debugging

| Command | What It Does |
| --- | --- |
| `docker logs <name>` | Prints everything the container has ever printed to stdout. |
| `docker inspect <name>` | Returns a deep JSON dump of all container configuration details. |

---

## Module 4: `docker run` — Flags You Must Know

### The Most Important Command

`docker run` creates and starts a brand new container from an image. Almost always used with flags in real DevOps work.

### Core Flags

| Flag | Purpose | Example |
| --- | --- | --- |
| `-d` | Detached mode — runs in background, gives terminal back. | `docker run -d nginx` |
| `--name` | Assigns a human-readable name instead of a random one. | `--name my_webserver` |
| `-p host:container` | Maps a port on your machine to a port inside the container. | `-p 8080:80` |
| `-it` | Interactive terminal — drops you inside the container with a live shell. | `docker run -it ubuntu bash` |
| `-v` | Volume mount — connects a folder on your host to a folder in the container. | `-v ~/data:/app/data` |
| `--rm` | Automatically deletes the container when it stops. | `docker run --rm nginx` |
| `-e` | Sets an environment variable inside the container. | `-e DB_PASSWORD=secret` |

### The Full Production-Style Command

```bash
docker run -d \
  --name my_webserver \
  -p 8080:80 \
  -v ~/mydata:/usr/share/nginx/html \
  nginx
#     ^
#   Image name always goes last
```

### Port Mapping Explained

```
-p 8080:80
    ^    ^
    |    └── Port INSIDE the container (where the app listens)
    └─────── Port on YOUR machine (what you type in the browser)
```

---

## Module 5: `docker exec` — Getting Inside a Running Container

### Core Concept

* **`docker exec`:** Runs a command inside an **already running** container. Essential for live debugging.

### `exec` vs `run`

| | `docker run` | `docker exec` |
| --- | --- | --- |
| **Creates** | A brand new container from an image. | Nothing — uses an existing running container. |
| **Needs** | An image name. | A running container name/ID. |
| **Use case** | Starting fresh. | Debugging a live container. |

### Core Commands

| Command | What It Does |
| --- | --- |
| `docker exec -it <name> bash` | Opens an interactive bash shell inside the container. |
| `docker exec -it <name> sh` | Use `sh` if the container doesn't have `bash` (e.g. Alpine Linux). |
| `docker exec <name> <command>` | Runs a single command and returns the output without entering. |

### ⚠️ Important

* Container names are **case-sensitive** and **exact**. `my_web_server` and `my_webserver` are completely different containers. Docker will throw `No such container` on the slightest typo.

---

## Module 6: Volumes — Keeping Data Alive

### The Problem

Containers are disposable by design. When a container is deleted, **everything written inside it is gone forever** — database records, uploaded files, logs. This is catastrophic for stateful applications.

### The Solution

A Volume connects a folder on your host machine to a folder inside the container. The app writes data normally, but the data physically lives on your host — safe from container deletion.

```
Your Host Machine              Container
~/mydata/          <──────>   /app/data/
     ↑
Data lives here — survives container death
```

### The Golden Rule

> **Anything you cannot afford to lose must live in a Volume.** Databases, user uploads, logs, config files.

### Two Types of Volumes

| Type | Command Style | Best For |
| --- | --- | --- |
| **Bind Mount** | `-v /absolute/host/path:/container/path` | Development — you see exactly where files are. |
| **Named Volume** | `-v my_volume_name:/container/path` | Production — Docker manages the location for you. |

### Essential Volume Commands

| Command | What It Does |
| --- | --- |
| `docker volume ls` | Lists all named volumes managed by Docker. |
| `docker volume create <name>` | Creates a named volume manually. |
| `docker volume inspect <name>` | Shows where Docker stored the volume data on your host. |
| `docker volume rm <name>` | Deletes a named volume permanently. |
| `docker volume prune` | Deletes all unused named volumes at once. |

### Path Rules for `-v`

* Docker's `-v` flag **always requires an absolute path** on the host side.
* Use `~` as a shortcut for `/home/your_username/` — it's always absolute.
* Use `$(pwd)/folder` to reference a folder relative to your current directory.

```bash
# These are all valid absolute paths:
-v ~/mydata:/app/data
-v /home/parallels/mydata:/app/data
-v $(pwd)/mydata:/app/data
```

---

## Module 7: Docker Networking

### Core Concept

By default, every container runs in complete network isolation. Containers cannot talk to each other or the outside world unless you explicitly connect them.

### Default Network Drivers

| Driver | What It Does |
| --- | --- |
| `bridge` | The default. Creates a private internal network. Containers on the same bridge can talk to each other by IP. |
| `host` | Removes isolation. Container shares your machine's network directly. |
| `none` | Completely disables all networking for the container. |

### Custom Bridge Networks — The Right Way

Running containers on a custom network allows them to reach each other **by container name** instead of by IP address (which changes every time). This is how production systems are built.

```bash
# Create a custom network
docker network create my_network

# Run containers ON that network
docker run -d --name web --network my_network nginx
docker run -d --name db  --network my_network mysql

# Now 'web' can reach 'db' simply by typing 'db' as the hostname
```

### Essential Networking Commands

| Command | What It Does |
| --- | --- |
| `docker network ls` | Lists all networks on your machine. |
| `docker network create <name>` | Creates a new custom bridge network. |
| `docker network inspect <name>` | Shows all containers connected to a network and their IPs. |
| `docker network connect <network> <container>` | Connects a running container to a network. |
| `docker network rm <name>` | Deletes a network (all containers must be disconnected first). |

---

## Module 8: Dockerfiles — Building Your Own Images

### Core Concept

A **Dockerfile** is a plain text recipe file that tells Docker how to build a custom image for your application. Every line is an instruction that adds a layer to the image.

### Essential Dockerfile Instructions

| Instruction | Purpose | Example |
| --- | --- | --- |
| `FROM` | **Always first.** Sets the base image to build on top of. | `FROM python:3.11-slim` |
| `WORKDIR` | Sets the working directory inside the container. All following commands run from here. | `WORKDIR /app` |
| `COPY` | Copies files from your host machine into the image. | `COPY . .` |
| `RUN` | Executes a shell command **during the build** (installs dependencies, etc.). | `RUN pip install -r requirements.txt` |
| `EXPOSE` | Documents which port the app listens on (informational, doesn't actually open it). | `EXPOSE 5000` |
| `ENV` | Sets an environment variable inside the image. | `ENV DEBUG=False` |
| `CMD` | The default command to run when a container starts. Only one allowed. | `CMD ["python", "app.py"]` |
| `ENTRYPOINT` | Like CMD but harder to override. Sets the container's main executable. | `ENTRYPOINT ["gunicorn"]` |

### A Complete Python Dockerfile

```dockerfile
# 1. Start from an official lightweight Python image
FROM python:3.11-slim

# 2. Set the working directory inside the container
WORKDIR /app

# 3. Copy the requirements file first (for layer caching)
COPY requirements.txt .

# 4. Install dependencies
RUN pip install -r requirements.txt

# 5. Copy the rest of the application code
COPY . .

# 6. Document the port the app uses
EXPOSE 5000

# 7. The command to run when the container starts
CMD ["python", "app.py"]
```

### Build & Run Commands

| Command | What It Does |
| --- | --- |
| `docker build -t my-app .` | Builds an image from the Dockerfile in the current directory and tags it `my-app`. |
| `docker build -t my-app:v1.0 .` | Builds and tags with a version number. |
| `docker run -d -p 5000:5000 my-app` | Runs a container from your freshly built image. |

### Layer Caching — The Performance Rule

Docker builds images **layer by layer** and caches each one. If a layer hasn't changed, Docker reuses the cached version instead of rebuilding it. **Always copy `requirements.txt` and install dependencies BEFORE copying your application code.** This way, a code change doesn't force Docker to reinstall all packages.

---

## Module 9: Docker Compose — Running Multi-Container Apps

### Core Concept

Real applications are never just one container. A typical web app has a web server, a database, and a cache — all as separate containers. **Docker Compose** lets you define and run all of them together with a single file and a single command.

### The `docker-compose.yml` File

```yaml
version: '3.8'

services:

  web:
    build: .                      # Build from Dockerfile in current directory
    ports:
      - "5000:5000"               # Map host port to container port
    volumes:
      - .:/app                    # Mount current directory for live code reload
    environment:
      - DB_HOST=db                # Use the service name 'db' as the hostname
    depends_on:
      - db                        # Wait for db to start first

  db:
    image: mysql:8.0              # Pull official image — no Dockerfile needed
    environment:
      - MYSQL_ROOT_PASSWORD=secret
      - MYSQL_DATABASE=myapp
    volumes:
      - db_data:/var/lib/mysql    # Named volume to persist database data

volumes:
  db_data:                        # Declare the named volume here
```

### Essential Docker Compose Commands

| Command | What It Does |
| --- | --- |
| `docker compose up` | Starts all services defined in `docker-compose.yml`. |
| `docker compose up -d` | Starts all services in the background (detached mode). |
| `docker compose up --build` | Forces a rebuild of images before starting. |
| `docker compose down` | Stops and removes all containers, networks created by Compose. |
| `docker compose down -v` | Same as above, but also deletes the named volumes (⚠️ data loss). |
| `docker compose ps` | Lists all containers managed by the current Compose file. |
| `docker compose logs` | Shows logs from all services combined. |
| `docker compose logs <service>` | Shows logs from one specific service. |
| `docker compose exec <service> bash` | Opens a shell inside a running Compose service. |
| `docker compose restart <service>` | Restarts a single service without stopping others. |

### Key Compose Concepts

* **Services:** Each container in your stack (e.g., `web`, `db`, `redis`).
* **`depends_on`:** Controls startup order — but does not wait for the app inside to be *ready*, only for the container to *start*.
* **Automatic Networking:** Compose automatically creates a shared network for all services. Services reach each other using their **service name** as the hostname (e.g., `db`, `redis`).
* **Named Volumes in Compose:** Declare all named volumes under the top-level `volumes:` key or Docker will throw an error.

---

## Quick Reference: The Most Used Commands

```bash
# ── Images ────────────────────────────────────────────
docker images                          # List all local images
docker pull nginx                      # Download image without running
docker rmi nginx                       # Delete an image

# ── Containers ────────────────────────────────────────
docker ps                              # Running containers
docker ps -a                           # All containers
docker run -d --name web -p 8080:80 nginx   # Run detached with name + port
docker stop web                        # Stop container
docker start web                       # Start stopped container
docker rm -f web                       # Force delete container
docker container prune                 # Delete all stopped containers

# ── Debugging ─────────────────────────────────────────
docker logs web                        # View container logs
docker exec -it web bash               # Shell into running container
docker inspect web                     # Full JSON details

# ── Volumes ───────────────────────────────────────────
docker volume ls                       # List all volumes
docker volume create mydata            # Create named volume
docker volume prune                    # Delete unused volumes

# ── Networks ──────────────────────────────────────────
docker network ls                      # List all networks
docker network create mynet            # Create custom network
docker network inspect mynet          # Inspect network

# ── Build ─────────────────────────────────────────────
docker build -t my-app .               # Build image from Dockerfile
docker build -t my-app:v1.0 .          # Build with version tag

# ── Compose ───────────────────────────────────────────
docker compose up -d                   # Start all services background
docker compose down                    # Stop and remove all
docker compose logs -f                 # Follow live logs
docker compose exec web bash          # Shell into a compose service
```




## Module 4: `docker run` Flags

### The Most Important Command

`docker run` creates and starts a brand new container from an image. Almost always used with flags in real DevOps work. The image name **always goes last**.

### Core Flags

| Flag | Purpose | Example |
| --- | --- | --- |
| `-d` | Detached mode — runs container in the background and gives your terminal back immediately. | `docker run -d nginx` |
| `--name` | Assigns a human-readable name instead of a random auto-generated one like `quirky_feynman`. | `--name my_webserver` |
| `-p host:container` | Port mapping — punches a hole from your machine into the container. | `-p 8080:80` |
| `-it` | Interactive terminal — drops you inside the container with a live shell. | `docker run -it ubuntu bash` |
| `-v` | Volume mount — connects a folder on your host to a folder inside the container. | `-v ~/data:/app/data` |
| `--rm` | Automatically deletes the container the moment it stops. | `docker run --rm nginx` |
| `-e` | Sets an environment variable inside the container at runtime. | `-e DB_PASSWORD=secret` |
| `--network` | Connects the container to a specific custom network. | `--network my_network` |

### Port Mapping — The Mental Model

```
-p 8080:80
    ^    ^
    |    └── Port INSIDE the container (where the app listens)
    └─────── Port on YOUR machine (what you type in the browser)
```

### The Full Production-Style Command

```bash
docker run -d \
  --name my_webserver \
  -p 8080:80 \
  --network my_network \
  -v ~/mydata:/usr/share/nginx/html \
  -e ENV=production \
  nginx
#  ^ Image name always goes last
```

---

## Module 5: `docker exec` — Getting Inside a Running Container

### Core Concept

* **`docker exec`:** Runs a command inside an **already running** container without creating a new one. The most important debugging tool in Docker.
* **`docker run` vs `docker exec`:** `run` creates a brand new container from an image. `exec` enters an existing running container. Use `exec` when the container is already up and you need to investigate it.

### Core Commands

| Command | What It Does |
| --- | --- |
| `docker exec -it <n> bash` | Opens an interactive bash shell inside the container. |
| `docker exec -it <n> sh` | Use `sh` instead of `bash` for lightweight images (e.g., Alpine Linux). |
| `docker exec <n> <command>` | Runs a single one-off command and returns the output without entering. |

### Real World Usage

```bash
# Shell into a running container to debug
docker exec -it my_webserver bash

# Once inside, inspect files and configs
cat /etc/nginx/nginx.conf
ls /usr/share/nginx/html

# Exit and return to your machine
exit
```

### Critical Rule

* Container names are **case-sensitive** and **exact**. `my_web_server` and `my_webserver` are completely different containers to Docker. A single typo throws `Error: No such container`.

---

## Module 6: Volumes — Keeping Data Alive

### The Problem

Containers are **disposable by design**. When a container is deleted, everything written inside it — database records, uploaded files, logs — is gone forever. This is catastrophic for any app that stores data.

### The Solution

A Volume connects a folder on your **host machine** to a folder **inside the container**. The app reads and writes normally, but the data physically lives on your host — completely safe from container deletion.

```
Your Host Machine              Container (can be deleted freely)
~/mydata/          <──────>    /app/data/
     ↑
 Data lives here permanently
```

### The Golden Rule of Volumes

* **Anything you cannot afford to lose must live in a Volume.** Databases, user uploads, logs, and config files must always be mounted.

### Two Types of Volumes

| Type | Syntax | Best For |
| --- | --- | --- |
| **Bind Mount** | `-v /absolute/host/path:/container/path` | Development — you control the exact location and can see the files directly. |
| **Named Volume** | `-v my_volume_name:/container/path` | Production — Docker manages the storage location for you. |

### Path Rules for `-v`

* Docker's `-v` flag always requires an **absolute path** on the host side. Never a relative path.
* Use `~` as a shorthand for `/home/your_username/` — it is always absolute.
* Use `$(pwd)/folder` to reference a folder relative to your current directory.

### Essential Volume Commands

| Command | What It Does |
| --- | --- |
| `docker volume ls` | Lists all named volumes managed by Docker. |
| `docker volume create <n>` | Creates a named volume manually. |
| `docker volume inspect <n>` | Shows the exact location on your host where Docker stored the volume data. |
| `docker volume rm <n>` | Permanently deletes a named volume and all its data. |
| `docker volume prune` | Deletes all named volumes not currently in use by a container. |

---

## Module 7: Docker Networking

### Core Concept

Every container runs in **complete network isolation** by default. Containers cannot see each other or the outside world unless you explicitly connect them through a network.

### Default Network Drivers

| Driver | What It Does |
| --- | --- |
| `bridge` | The default network. Every container joins this unless told otherwise. Containers can only reach each other by IP address — which changes on every restart. |
| `host` | Removes network isolation entirely. Container shares your machine's network stack directly. |
| `none` | Completely disables all networking for the container. |

### Why You Should Always Use a Custom Network

On the default `bridge` network, containers can only reach each other by IP address — and those IPs change every time a container restarts. A custom network gives you **container name resolution for free** — containers reach each other by using the container name as the hostname. No IP addresses needed ever.

```bash
# Create a custom network
docker network create my_network

# Connect containers to it at runtime
docker run -d --name web_app --network my_network nginx
docker run -d --name database --network my_network mysql

# web_app can now reach database simply by name
# curl http://database:3306  ← works perfectly
```

### Essential Networking Commands

| Command | What It Does |
| --- | --- |
| `docker network ls` | Lists all networks currently on your machine. |
| `docker network create <n>` | Creates a new custom bridge network. |
| `docker network inspect <n>` | Shows all containers connected to the network and their assigned IPs. |
| `docker network connect <network> <container>` | Connects an already running container to a network. |
| `docker network rm <n>` | Deletes a network (all containers must be disconnected first). |

---

## Module 8: Dockerfiles — Building Your Own Images

### Core Concept

* **Dockerfile:** A plain text file — literally named `Dockerfile` with no extension — containing step-by-step instructions that tell Docker how to build a custom image for your application. Every instruction adds a new layer to the image.

### Essential Dockerfile Instructions

| Instruction | Purpose | Example |
| --- | --- | --- |
| `FROM` | **Always the first line.** Sets the official base image to build on top of. | `FROM python:3.11-slim` |
| `WORKDIR` | Sets the working directory inside the container. All following commands run from here. | `WORKDIR /app` |
| `COPY` | Copies files from your host machine into the image at build time. | `COPY . .` |
| `RUN` | Executes a shell command **during the build** — used for installing packages. | `RUN pip install -r requirements.txt` |
| `EXPOSE` | Documents which port the app listens on. Informational only — does not actually open it. | `EXPOSE 5000` |
| `ENV` | Sets a permanent environment variable baked into the image. | `ENV DEBUG=False` |
| `CMD` | The default command to run when the container starts. Only one `CMD` is allowed per Dockerfile. | `CMD ["python", "app.py"]` |
| `ENTRYPOINT` | Like `CMD` but harder to override. Sets the container's fixed main executable. | `ENTRYPOINT ["gunicorn"]` |

### A Complete Production-Ready Python Dockerfile

```dockerfile
# 1. Start from an official lightweight Python base image
FROM python:3.11-slim

# 2. Set the working directory inside the container
WORKDIR /app

# 3. Copy requirements FIRST — critical for layer caching
COPY requirements.txt .

# 4. Install all dependencies during the build
RUN pip install -r requirements.txt

# 5. Now copy the rest of the application code
COPY . .

# 6. Document the port the app listens on
EXPOSE 5000

# 7. The command that runs when a container starts
CMD ["python", "app.py"]
```

### Build Commands

| Command | What It Does |
| --- | --- |
| `docker build -t my-app .` | Builds an image from the Dockerfile in the current directory. The `.` means look here. |
| `docker build -t my-app:v1.0 .` | Builds and tags with a specific version number. Best practice in production. |
| `docker run -d -p 5000:5000 my-app` | Runs a container from your freshly built custom image. |

### Layer Caching — The Most Important Performance Rule

Docker builds images layer by layer and **caches every layer**. If nothing changed in a layer since the last build, Docker reuses the cached version and skips rebuilding it. Always copy `requirements.txt` and run `pip install` **before** copying your application code. That way when you change your code, Docker reuses the cached pip install layer and only rebuilds the last two steps instead of reinstalling every package from scratch.

---

## Module 9: Docker Compose — Running Multi-Container Apps

### Core Concept

* **Docker Compose:** A tool that lets you define your entire application stack — every container, network, and volume — in a single `docker-compose.yml` file and control everything with one command.
* **The Problem It Solves:** A real app needs multiple containers (web server, database, cache). Without Compose, you must manually run 5+ `docker run` commands, create networks, and wire everything together by hand every single time.

### The `docker-compose.yml` Structure

```yaml
services:

  web:                              # Service 1 — Your Flask app
    build: .                        # Build from Dockerfile in current directory
    ports:
      - "5000:5000"                 # Same as -p in docker run
    environment:
      - DB_HOST=db                  # Use the service name as the hostname
    depends_on:
      - db                          # Start db container before web

  db:                               # Service 2 — MySQL Database
    image: mysql:8.0                # Pull ready-made image — no Dockerfile needed
    environment:
      - MYSQL_ROOT_PASSWORD=secret
      - MYSQL_DATABASE=myapp
    volumes:
      - db_data:/var/lib/mysql      # Named volume to persist all database data

volumes:
  db_data:                          # Must declare all named volumes at the top level
```

### Essential Docker Compose Commands

| Command | What It Does |
| --- | --- |
| `docker compose up` | Starts all services and attaches to their logs in your terminal. |
| `docker compose up -d` | Starts all services in the background (detached). The command you use most. |
| `docker compose up --build` | Forces Docker to rebuild images before starting. Use when you changed your code. |
| `docker compose down` | Stops and removes all containers and networks created by Compose. |
| `docker compose down -v` | Same as above but also deletes named volumes. ⚠️ Permanently destroys all data. |
| `docker compose ps` | Lists all containers managed by the current Compose file and their status. |
| `docker compose logs` | Shows combined logs from all running services. |
| `docker compose logs <service>` | Shows logs from one specific service only. |
| `docker compose logs -f` | Follows logs live in real time. |
| `docker compose exec <service> bash` | Opens a shell inside a running Compose service. |
| `docker compose restart <service>` | Restarts a single service without touching the others. |

### Key Compose Concepts

* **Services:** Each container in your stack. Every service becomes a running container when you run `docker compose up`.
* **Automatic Networking:** Compose automatically creates a custom bridge network for all services. Every service is reachable by its service name as the hostname — no IP addresses needed.
* **`depends_on`:** Controls startup order — starts `db` before `web`. Note: it only waits for the container to start, not for the app inside to be fully ready.
* **Named Volumes:** All named volumes must be declared under the top-level `volumes:` key at the bottom of the file or Docker will throw an error.
* **`version` key:** Modern Docker Compose no longer requires the `version:` field. If you see a warning saying it is obsolete, simply remove that line.

---

## Quick Reference — Most Used Docker Commands

```bash
# ── Images ─────────────────────────────────────────────────
docker images                           # List all local images
docker pull nginx                       # Download image without running
docker rmi nginx                        # Delete a local image
docker image prune                      # Delete all unused images

# ── Containers ─────────────────────────────────────────────
docker ps                               # Show only running containers
docker ps -a                            # Show ALL containers including stopped
docker run -d --name web -p 8080:80 nginx   # Run detached, named, with port
docker stop web                         # Gracefully stop a container
docker start web                        # Restart a stopped container
docker rm -f web                        # Force delete a container
docker container prune                  # Delete ALL stopped containers

# ── Debugging ──────────────────────────────────────────────
docker logs web                         # View container output logs
docker logs -f web                      # Follow logs live in real time
docker exec -it web bash                # Get a shell inside a running container
docker inspect web                      # Full JSON details of a container

# ── Volumes ────────────────────────────────────────────────
docker volume ls                        # List all named volumes
docker volume create mydata             # Create a named volume
docker volume inspect mydata            # See where Docker stored it on host
docker volume prune                     # Delete all unused volumes

# ── Networks ───────────────────────────────────────────────
docker network ls                       # List all networks
docker network create mynet             # Create a custom bridge network
docker network inspect mynet            # See containers on the network

# ── Build ──────────────────────────────────────────────────
docker build -t my-app .                # Build image from Dockerfile here
docker build -t my-app:v1.0 .           # Build with a version tag

# ── Compose ────────────────────────────────────────────────
docker compose up -d                    # Start all services in background
docker compose up --build               # Rebuild images and start
docker compose down                     # Stop and remove everything
docker compose down -v                  # Also delete volumes ⚠️ data loss
docker compose ps                       # List all compose containers
docker compose logs -f                  # Follow live logs from all services
docker compose exec web bash            # Shell into a compose service
docker compose restart web              # Restart one service only
```
