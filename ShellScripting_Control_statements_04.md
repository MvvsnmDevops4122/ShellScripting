# Control Statements in Shell Scripting

Control statements in shell scripting allow you to control the flow of execution based on conditions or loops.  
They are used to make decisions and repeat code blocks.

---

## 1️⃣ if Statement

The `if` statement checks a condition.  
If the condition is true, the code inside the `if` block executes.

### Syntax
```bash
#!/bin/bash
if [ condition ]; then
  # code to execute if true
fi
````

---

## 2️⃣ if-else Statement

Used when you need one block to run if a condition is true and another if false.

### Syntax

```bash
if [ condition ]; then
    # Code when condition is true
else
    # Code when condition is false
fi
```

### Example 1

```bash
#!/bin/bash
a=10

if [ $a -eq 10 ]; then
    echo "Value of a is 10"
else
    echo "Value of a is not 10"
fi
```

### Example 2 (Check if file exists)

```bash
#!/bin/bash
file="demo.sh"

if [ -f "$file" ]; then
    echo "File $file exists."
else
    echo "File $file does not exist."
fi
```

✅ `-f` → Checks if file exists and is a regular file.

### Example 3 (Check Internet Connectivity)

```bash
#!/bin/bash
ping_result=$(ping -c 1 google.com 2>&1)

if [[ $ping_result == *"icmp_seq"* ]]; then
    echo "Internet connectivity is up."
else
    echo "Internet connectivity is down."
fi
```

#### Explanation:

| Part           | Meaning                  |
| -------------- | ------------------------ |
| `-c 1`         | Send only 1 ping         |
| `2>&1`         | Redirect error to output |
| `$(...)`       | Capture command output   |
| `*"icmp_seq"*` | Pattern matching         |

---

## 3️⃣ if-elif-else Statement

Used to check **multiple conditions**.

### Syntax

```bash
if [ condition1 ]; then
    # Code if condition1 true
elif [ condition2 ]; then
    # Code if condition2 true
else
    # Code if all conditions false
fi
```

### Example 1

```bash
#!/bin/bash
a=20

if [ $a -eq 10 ]; then
    echo "Value of a is 10"
elif [ $a -eq 20 ]; then
    echo "Value of a is 20"
else
    echo "Value of a is neither 10 nor 20"
fi
```

### Example 2 (Check Disk Usage)

```bash
#!/bin/bash

threshold_critical=15
threshold_warning=12
current_usage=$(df -h / | awk 'NR==2 {print $5}' | cut -d'%' -f1)

echo "Current disk usage: $current_usage%"

if [ $current_usage -ge $threshold_critical ]; then
    echo "Disk usage is critical ($current_usage%). Taking immediate action!"
elif [ $current_usage -ge $threshold_warning ]; then
    echo "Disk usage is high ($current_usage%). Consider freeing up space."
else
    echo "Disk usage is normal ($current_usage%)."
fi
```

| Command | Meaning              |
| ------- | -------------------- |
| `cut`   | Extract part of text |
| `-d'%'` | Use `%` as delimiter |
| `-f1`   | Extract first field  |

---

### Example 3 (User Input)

```bash
#!/bin/bash
read -p "Enter a number (1-3): " num

if [ "$num" -eq 1 ]; then
    echo "You entered the number one."
elif [ "$num" -eq 2 ]; then
    echo "You entered the number two."
elif [ "$num" -eq 3 ]; then
    echo "You entered the number three."
else
    echo "Invalid input: Please enter a number between 1 and 3."
fi
```

### Example 4 (Network Status Check)

```bash
#!/bin/bash
ping_result=$(ping -c 1 google.com 2>&1)

if [[ $ping_result == *"icmp_seq"* ]]; then
    echo "Internet connectivity is up."
elif [[ $ping_result == *"unknown host"* ]]; then
    echo "Unable to resolve DNS. Check your network configuration."
else
    echo "Internet connectivity is down."
fi
```
----

# 4. Case Statement in Shell Scripting

## 🧾 What is a case statement?

- The `case` statement is used to check **multiple conditions**.
- It allows executing **different blocks of code** based on the value of a variable.
- It works like **switch-case** in other programming languages.

---

## ✅ Case Statement Syntax (Step-by-Step)

```bash
case "$variable" in        # Start of case block to check the value of variable
    pattern1)              # If variable matches pattern1
        command1           # Commands to execute
        ;;                 # End of this case block

    pattern2)              # Another condition
        command2
        ;;                 # End of this case block

    *)                     # Default case (similar to else)
        default_command
        ;;                 
esac                       # End of case block (word 'case' reversed)
````

---

## ✅ When to Use `case` Statement?

| Use Case                 | Example Scenario                           |
| ------------------------ | ------------------------------------------ |
| Menu selection           | Start/Stop/Restart services via user input |
| Script argument handling | `./script.sh start/stop/status`            |
| File extension checking  | Identify `.txt`, `.sh`, `.jpg`, etc.       |
| Day-based automation     | Run tasks on Monday or Friday              |
| Package selection        | Choose between `yum` or `apt`              |

---

## Example 1: Basic Case Statement

```bash
#!/bin/bash

fruit="apple"

case $fruit in
    apple)
        echo "It's a fruit: apple."
        ;;
    banana)
        echo "It's a fruit: banana."
        ;;
    orange | mandarin)
        echo "It's a citrus fruit."
        ;;
    *)
        echo "Unknown fruit."
        ;;
esac
```

---

## Example 2: Checking Days of the Week

```bash
#!/bin/bash

day="Monday"

case $day in
    Monday | Tuesday | Wednesday | Thursday | Friday)
        echo "$day is a weekday."
        ;;
    Saturday | Sunday)
        echo "$day is a weekend day."
        ;;
    *)
        echo "Invalid day."
        ;;
esac
```

---

## Example 3: Menu Driven Program

```bash
#!/bin/bash

echo "Menu:"
echo "====="
echo "1. Display date"
echo "2. Display calendar"
echo "3. Display current directory"
echo "4. Exit"

read -p "Enter your choice: " choice

case $choice in
    1)
        date
        ;;
    2)
        cal
        ;;
    3)
        pwd
        ;;
    4)
        echo "Exiting program."
        exit 0
        ;;
    *)
        echo "Invalid choice: $choice. Please enter a number between 1 and 4."
        ;;
esac
```

