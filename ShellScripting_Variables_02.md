# Variables in Shell Scripting

Variables are used to store data or values that can be referenced and manipulated throughout the script.

---

## Variable Naming and Assignment

### Variable Naming Rules
- Variable names can contain letters (`a-z`, `A-Z`), digits (`0-9`), and underscores (`_`).
- They **must start** with a letter or an underscore.
- Variable names are **case-sensitive** (`myVar` ≠ `MYVAR`).
- Variable names **cannot** start with a number.

### Variable Assignment
Assign values using `=` **without spaces**.

Example:
```bash
myVar="Hello, World!"
````

Quotes preserve spaces and special characters.

### Accessing Variables

Use `$` before variable name.

```bash
echo "The value of myVar is: $myVar"
```

### Variable Expansion

```bash
name="Alice"
echo "Hello, $name!"
```

### Concatenation

```bash
greeting="Hello"
target="World"
echo "$greeting, $target!"
```

---

## Types of Variables

### 1. Environment Variables (System Defined Variables)

These are inherited from the shell environment or exported using `export`.

```bash
env
printenv
```

Example:

```bash
echo "Current user: $USER"
```

#### `export`

Used to override or set environment variables.

```bash
echo $HISTSIZE
export HISTSIZE=300
echo $HISTSIZE
```

**Note:** This change lasts only for the current session.

To make it permanent:

```bash
vim ~/.bash_profile
export HISTSIZE=300
```

---

### 2. Local Variables (User Defined Variables)

Defined inside a script and accessible only within the script.

Example:

```bash
a=10
b=90
name="kkfunda"

echo $a
echo $b
echo $name
```

---

### 3. Special Variables

| Variable | Meaning                              |
| -------- | ------------------------------------ |
| `$#`     | Number of arguments passed to script |
| `$@`     | All arguments as separate words      |
| `$*`     | All arguments as one string          |
| `$$`     | Script/process ID (PID)              |
| `$?`     | Previous command exit status         |

Status Codes:

```text
0     → Success
127   → Command not found
```

---

## Naming Conventions

* File name max length = **255 characters**
* File name can contain alphabets, numbers, dot (`.`), and underscore (`_`)
* **Cannot use Linux reserved keywords**
* Linux file system is **case-sensitive**

Examples of reserved words:

```
if
fi
for
mkdir
pwd
```

---

## Command Line Arguments in Shell Scripting

Used to pass values when running a script.

| Parameter | Meaning         |
| --------- | --------------- |
| `$0`      | Script name     |
| `$1`      | First argument  |
| `$2`      | Second argument |

For arguments beyond 9, use braces:

```
${10}
```

### Example Script

```bash
#!/bin/bash
echo "Script name: $0"
echo "First argument: $1"
echo "Second argument: $2"
```

Execution:

```bash
sh Demo.sh Prasanth reddy
```

### 🧾 How to Read a Value at Runtime in Shell Scripting

---

## 1️⃣ Read Basic Input

```bash
#!/bin/bash

# Prompt user to enter their name
echo "Enter your name:"
read name

echo "Hello, $name! Welcome to the script."
````

---

## 2️⃣ Using `-p` Option for Prompt

`read -p` allows you to display the prompt and take the input on the same line.

```bash
#!/bin/bash

# Prompt user for input with a custom prompt
read -p "Enter your age: " age

echo "You entered: $age years old."
```

---

## 3️⃣ Read Input One After Another (Sequential Reading)

```bash
#!/bin/bash

# Reading multiple values
echo "Please enter your name:"
read name

echo "Please enter your age:"
read age

echo "Hello, $name! You are $age years old."
```

---

## 4️⃣ Read Multiple Values in One Line

```bash
#!/bin/bash

# Reading multiple values at once
echo "Please enter your name and Age:"
read name age1

echo "Hello, $name! You are $age1 years old."
```

---

## 5️⃣ Reading Input with Timeout

```bash
#!/bin/bash

# Prompt user for input with a timeout
read -t 10 -p "Enter your password within 10 seconds: " password

if [ -z "$password" ]; then
    echo "No password entered within 10 seconds."
else
    echo "Password entered: $password"
fi
```

---

## 6️⃣ Reading Input Silently (Password Input - Secure)

```bash
#!/bin/bash

# Prompt user for password input (silent)
read -s -p "Enter your password: " password
echo    # Moves to the next line

echo "Password entered."
```
