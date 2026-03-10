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
