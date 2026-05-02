# Linux Blog and Commands

### Basic Commands

- **pwd** 
    - print working directory
    - shows the current working directory

- **cd**
    - change directory
    - **Shortcuts**
        - cd / (to the root)
        - cd (to the home directory)
        - cd ~ (to the home directory)
            - example: cd ~/Desktop (to the Desktop)

- **mkdir**
    - creates a new directory
    - nested directories
        - mkdir -p f1/f2/f3

- **touch**
    - creates a new file
    - example: 'touch file.txt'

- **cat**
    - concatenate
    - used to combine text from multiple files into a new or existing file
    - used to display the contents of a file
    - you can also create a new file with 'cat > f.txt'

- **rm**
    - used to remove files
    - **rmdir** to remove the directory
    - **rm -r dirname** to remove even if there are files in the directory

- **wc**
    - word count
    - **wc -l** counts the lines

- **sort** 
    - default sort is ascending order
    - **sort -r filename**
    - groups duplicates together

- **uniq**
    - removes duplicate lines (adjacent only)

### Commands That I Have Learned on 7/4/2026

- **grep** 
    - used to find content in files
    - mostly used to scan text files
    - format: grep [pattern] [file]
    - -i case insensitive
    - -n shows line numbers
    - -r recursive search
    - -rin most common real-world usage

- **find**
    - unlike 'grep' which is used to find patterns in files, 'find' is used to locate directories/files in the filesystem
    - example commands 
        - 'find . -name "*.log"'
        - 'find . -type d'
        - 'find . -size +10M'
        - 'find . -mtime -2'

- **| (pipe operator)**
    - passes the standard output (stdout) of one command as the standard input (stdin) of another command

- **xargs**
    - takes input from stdin and converts it into command-line arguments for another command
    - used because some commands do not accept stdin directly

- **exec**
    - -exec is an option used in 'find' that allows you to run another command on the files that 'find' matches
    - **Difference between pipe and -exec**
        - Pipe (|) 
            - sends output (text/stream) of one command to another 
            - works through stdin
        - exec 
            - passes file paths as arguments directly to a command
            - does NOT use stdin
    - when using pipe it passes text, but exec passes actual file paths
    - example:
        - 'find . -name "*.log" -exec grep "error" {} +'
        - {} holds the file names 
        - '+' executes in 
        
# CHMOD & CHOWN Commands

### CHMOD - Chnnge Mod

- CHMOD is usually used to change the permissions of file or directory in linux system.
- ls -l command is used to check permissions of file.
- There are three users of file and directory in linux (user, group and all other excluding o and g)
    - u - user (owner)
    - g - group
    - o - others
- there are three main permissions in Linux 
    - r - read (4)
    - w - write (2)
    - x - Execute (1)
- You can assign permission to the file via
    - example : `sudo chmod u+x script.sh` (this grants execute permission to user)
    - example : `sudo chmod a+x script.sh` (this grants execute permission to all three u,g,o)
    - example : `sudo chmod  +x script.sh` (this command is also used to grant permission to all three u,g,o simultaneously)

- **Numeric method / Octal Method**
    - Example : sudo chmod 764 script.sh (permissions granted u:rw , g:rw , o:r)
    - It is not advised to use 777 as it gives permission to all (u,g,o) and it is not safe.



### Creating users and groups

- Command used to create an new user is `adduser` 
    - Example : `sudo adduser newUser` `and sudo passwd newUser` is the command used to set password
- Command to create an new group is `addgroup`
- Example : `sudo addgroup newGroup` 

### CHOWN - Change Owner

- Command to used to change the owner or group assigned of file, directory or etc 
- Command : `sudo chown newuser: script.sh` (This command changes the owner of file script.sh to newUser)
- Command : `sudo chown :newGroup script.sh` (This command changes the group of the file script.sh to newGroup)
- Command : `sudo chown newuser:newGroup scriptNew.sh` (This command changes both the group and file of file scriptNew.sh to newuser & newGroup respectively)