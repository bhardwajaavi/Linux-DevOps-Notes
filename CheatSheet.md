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
