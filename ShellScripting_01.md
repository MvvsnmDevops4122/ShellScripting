# Shell Scripting

## What is shell?

-> shell refers to a user interface that allows users to interact with the operating system (OS) or execute commands.

-> It acts as a command interpreter, taking commands entered by the user (via a command-line interface or graphical interface) and executing them by communicating with the OS kernel.

-> In most of Linux OS BASH[Bourne Again SHell] is the default shell type.

```

```
            Shell
```

User   ----------------------------> Kernal

````

## There are other shell programs are there,

1. Korn shell  
2. Bash  
3. C Shell (csh)  
4. Z Shell (zsh), etc

---

## How to check How many shells are there in my Linux server?

```bash
cat /etc/shells
````

---

## How to install csh?

```bash
sudo yum install csh -y
sudo yum install zsh -y
sudo yum install ksh -y
```

---

## How to check which shell we are using now?

```bash
echo $SHELL
echo $0
ps -p $$
```

---

## How switch to another shell?

Step 1: Check available shells:

```bash
cat /etc/shells
```

Step 2: Switch to another shell:

```bash
/bin/sh
ps -p $$
```

Step 3: Come back to bash:

```bash
/bin/bash
```

---

## What is shell scripting?

--> It is a file, contains collections of commands, Whatever the order we provided based on that order it will be executed.

---

## Extension of shell scripting

`.sh`

---

## Why we need to learn shell scripting?

Ans: To automate manual tasks.

---

## Is it only for DevOps Engineers?

Ans: NO

Examples:

1. serverresourseutilization.sh
2. dbbackup.sh

---

## Prerequisites

1. Linux commands
2. Basic programming knowledge (depends)
3. Commitment
4. Problem solving skills

---

## How to write a shell script?

```bash
vi Demo.sh
```

Content:

```bash
#!/bin/bash  --> #! --> shebang line
echo "Welcome to shellscript KK FUNDA"
echo "Today date is"
date
pwd
```

---

## Ways to run shell script

```bash
sh Demo.sh
./Demo.sh   # chmod u+x Demo.sh
. Demo.sh
bash Demo.sh
```

---

## Will the script work on Windows?

NO

Linux server → shell scripting (platform dependent)
Windows server → PowerShell (platform dependent)
Python → platform independent

---

## Debug Mode

Full script debug:

```bash
sh -x Demo.sh
```

Debug part of script:

```bash
set -x
echo "Welcome to shellscript KK FUNDA"
echo "Today date is"
set +x
date
```

---

## Shebang line

```bash
#!/bin/bash x
```

---

## Comments in shell scripting

* Improve code readability
* Documentation
* Explain commands

### Single-line comment:

```bash
# This is a single-line comment
```

### Inline comment:

```bash
command1  # This command does something
```

### Multi-line style comment:

```bash
# This is
# a multi-line
# comment
```

### Here Document:

```bash
<< satya
echo "Welcome to shellscript KK FUNDA"
echo "Today date is"
satya
```

---

## Comments in java/terraform/groovy

```
// single line
/*
 multi line
*/
```

---

## XML comments

```xml
<!-- comment -->
```

```
