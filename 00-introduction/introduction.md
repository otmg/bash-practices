# Getting started
**Interactive Shell**: The Bash shell is commonly used `interactively`: It lets you enter and edit commands, then executes them when
you press the `Return` key. Many Unix-based and Unix-like operating systems use Bash as their default shell
(notably Linux and macOS). The terminal automatically enters an interactive Bash shell process on startup.

```bash
echo Hello BashScript!
echo "Hello BashScript!"

# `echo` is a builtin command that writes the arguments it receives to the standard output.
# It appends a newline to the output
```

**Non-Interactive Shell**: The Bash shell can also be run non-interactively from a script, making the shell require no human interaction.

1. Use the following command to create a file name `hello-world.sh`
```bash
touch hello-world.sh
```

2. Inside the file `hello-world.sh`
```bash
#!/bin/bash
echo "Hello BashScript!"
```

3. Make the script executable by running `chmod +x hello-world.sh`

4. Execute the hello-world.sh script from the command line using one of the following:
```bash
./hello-world.sh
/bin/bash hello-world.sh
bash hello-world.sh
sh hello-world.sh

# debug mode
bash -x hello.sh
```

# Shebangs
**Env shebang**: To execute a script file with the bash executable found in the `PATH` environment variable by using the executable
env, the first line of a script file must indicate the absolute path to the env executable with the argument bash:

```bash
#!/usr/bin/env bash
```

**Direct shebang**: To execute a script file with the bash interpreter, the first line of a script file must indicate the absolute path to the
bash executable to use:
```bash
#!/bin/bash
```

The shebang is **ignored** when a `bash` interpreter is explicitly indicated to execute a script:
```bash
bash script.sh
```

# Type
```bash
type echo
# result
# echo is a shell builtin
```

# Quoting – single vs double quotes.

# Editor mode
```bash
# enable print all executed commands to the console
set -x
# disable
set +x

# set editor
set -o emacs
set -o vim
```

# Aliasing
```bash
alias ls_with_color='ls --color=auto'
unalias ls_with_color

# list all alias
alias -p
```

# References
[Bash Notes for Professionals book](https://goalkicker.com/BashBook/)