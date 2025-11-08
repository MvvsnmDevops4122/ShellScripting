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
