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
        - '+' executes in batch