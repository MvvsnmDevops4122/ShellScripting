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
