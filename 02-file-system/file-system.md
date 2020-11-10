# Navigating directories
```bash
# Absolute path
cd /home/username/project/abc

# Relative path
# suppose you already in `/home/username/project`
cd abc
# or
cd ./abc

# Go up one level
cd ..

# Go back to the previous directory
cd -

# Go to the $HOME directory
cd
# or
cd $HOME
# or
cd ~

# Go to the the directory of the script
cd "$(dirname "$(readlink -f "$0")")"
```

# List files
The ls command's -l option prints a specified directory's contents in a long listing format. If no directory is
specified then, by default, the contents of the current directory are listed.

|     Option      |  Description              |
|-----------------|---------------------------------------------------------|
| -a, --all       | List all entries including ones that start with a dot   |
| -A, --almost-all        | List all entries excluding . and ..   |
| -c        | Sort files by change time   |
| -d, --directory       | List directory entries    |
| -h, --human-readable        | Show sizes in human readable format (i.e. K, M)   |
| -H        | Same as above only with powers of 1000 instead of 1024    |
| -l        | Show contents in long-listing format    |
| -o        | Long -listing format without group info   |
| -r, --reverse       | Show contents in reverse order    |
| -s, --size        | Print size of each file in blocks   |
| -S        | Sort by file size   |
| --sort=WORD       | Sort contents by a word. (i.e size, version, status)    |
| -t        | Sort by modification time   |
| -u        | Sort by last access time    |
| -v        | Sort by version   |
| -1        | List one file per line    |

```bash
# list all files in the current directory
ls -al

# list the content inside directory `/etc`
ls -l /etc

# Sample result
#
# total 1204
# drwxr-xr-x 3 root root 4096 Apr 21 03:44 acpi
# -rw-r--r-- 1 root root 3028 Apr 21 03:38 adduser.conf
# drwxr-xr-x 2 root root 4096 Jun 11 20:42 alternatives
# ...
```
| Column No. | Example | Description |
|------------|---------|-------------|
1.1     |       d     |        File type (see table below)|
1.2     |       rwxr-xr-x     |        Permission string|
2     |       3      |       Number of hard links|
3     |       root      |        Owner name|
4     |       root      |        Owner group|
5     |       4096      |        File size in bytes|
6     |       Apr 21 03:44      |        Modification time|
7     |       acpi      |        File name|

# File Type
| Character | FileType |
|---|-----------------|
| - | Regular file  |
| b | Block special file  |
| c | Character special file  |
| C | High performance ("contiguous data") file |
| d | Directory |
| D | Door (special IPC file in Solaris 2.5+ only)  |
| l | Symbolic link |
| M | Off-line ("migrated") file (Cray DMF) |
| n | Network special file (HP-UX)  |
| p | FIFO (named pipe) |
| P | Port (special system file in Solaris 10+ only)  |
| s | Socket  |
| ? | Some other file type  |
|---|-----------------|

#  List Files Without Using `ls`
Use the Bash shell's filename expansion and brace expansion capabilities to obtain the filenames:
```bash
# display the files and directories that are in the current directory
printf "%s\n" *
# display only the directories in the current directory
printf "%s\n" */
# display only (some) image files
printf "%s\n" *.{gif,jpg,png}
```

#  List Files in a Tree-Like Format
```bash
tree -L 1 -d /tmp
```

# View the files
```bash
# recipe: cmd + _path_to_the_file_
cat

tail

head

more

less

ls
```

# Searching
**Searching for word inside the files**
```bash
# To find the word foo in the file bar :
grep foo ~/Desktop/bar

# To find all lines that do not contain foo in the file bar :
grep –v foo ~/Desktop/bar

# To use find all words containing foo in the end (Wildcard Expansion):
grep "*foo" ~/Desktop/bar
```

**Searching for a file by name or extension**
```bash
# To find files/directories with a specific name, relative to pwd:
find . -name "myFile.txt"

# To find files/directories with a specific extension, use a wildcard:
find . -name "*.txt"

# To find files/directories which name begin with abc and end with one alpha character following a one digit:
find . -name "abc[a-z][0-9]"

# The `or` flag
find . -name "*.txt" -o -name "*.sh"

# Find all files in the directory `/opt`
find /opt -type f
```

```bash
which java

which npm

which node
```

# Auth

chown
chmod

# Redirection
**Redirecting standard output**
```bash
# Write the output of the command `ls` to the file `file.txt`
ls > file.txt
# or
> file.txt ls
# or
# The default redirection descriptor is the standard output or 1 when none is specified.
ls 1> file.txt
```

**STDIN, STDOUT and STDERR explained**

- STDIN: Standard input is used to provide input to a program. (Here we're using the read builtin to read a line from STDIN.)
```bash
read
# Type some text here
```

- STDOUT: Standard output is generally used for "normal" output from a command. For example, ls lists files, so the files are sent to STDOUT.
```bash
ls file
# files...
```

- STDERR: Standard error is (as the name implies) used for error messages. Because this message is not a list of files, it is sent to STDERR.
```bash
ls anotherfile
# ls: cannot access 'anotherfile': No such file or directory
```

STDIN, STDOUT and STDERR are the three standard streams. They are identified to the shell by a number rather
than a name:
- 0 = Standard in
- 1 = Standard out
- 2 = Standard error

Check if the last cmd is error.
```bash
echo $?
# 0 indicate OK
```

# Append vs Truncate
Truncate >
```bash
echo "first line" > /tmp/lines
echo "second line" > /tmp/lines

cat /tmp/lines
# result
# second line
```

```bash
echo "second line" >> /tmp/lines
echo "second line" >> /tmp/lines

cat /tmp/lines
# result
# first line
# second line
```

# Here documents and here strings
```bash
cat > fruits.txt << EOF
apple
orange
lemon
EOF
```
```bash
awk '{ print $2 }' <<< "hello world - how are you?"
```

# References
[Bash Notes for Professionals book](https://goalkicker.com/BashBook/)