# Loops in Shell Scripting (SS)

A **loop** is used to repeat a set of commands multiple times in shell scripting. It helps automate repetitive tasks efficiently.

---

## 📌 6. **for Loop**

The **for loop** is used to iterate over a list of values.

### **Syntax**

```bash
for variable in list
do
    # Commands to execute for each item in the list
done
```

---

### **Example 1: Iterating Over a List of Numbers**

```bash
#!/bin/bash

for num in 1 2 3 4 5
do
    echo "Number: $num"
done
```

---

### **Example 2: Iterating Over Files in a Directory**

```bash
#!/bin/bash

echo "Files in current directory:"
for file in *
do
    echo "$file"
done
```

---

### **Example 3: Processing Arguments Passed to a Script**

```bash
#!/bin/bash

echo "Arguments passed to the script:"
for arg in "$@"
do
    echo "$arg"
done
```

---

### **Example 4: Generating a Sequence of Numbers**

```bash
#!/bin/bash

echo "for loop example"
for (( i=1; i<=5; i++ ))
do
    echo "Iteration: $i"
done
```

---

### **Example 5: Nested for Loop (Multiplication Table)**

```bash
#!/bin/bash

echo "Multiplication Table (1 to 5):"

for (( i=1; i<=5; i++ ))
do
    echo "Multiplication table for $i:"
    for (( j=1; j<=5; j++ ))
    do
        echo "$i * $j = $((i * j))"
    done
    echo "----------------------"
done
```

---

### **Increment & Decrement Operators**

```
j++
++j
j--
--j
```

---

## 📌 7. **while Loop**

Runs **as long as a condition is true**.

### **Syntax**

```bash
while [ condition ]
do
    # Code block
done
```

---

### **Example 1: Counting Down from 5 to 1**

```bash
#!/bin/bash

counter=5

echo "Counting down:"
while [ $counter -gt 0 ]; do
    echo "$counter"
    (( counter-- ))
done

echo "You are a good automation engineer"
```

---

### **Example 2: Reading Lines from a File**

```bash
#!/bin/bash

filename="d6.sh"

echo "Contents of file:"
while IFS= read -r line    # IFS: Internal Field Separator
do
    echo "$line"
done < "$filename"

echo "you are a great"
```

---

### **Example 3: Processing User Input Until 'exit'**

```bash
#!/bin/bash

echo "Enter names (type 'exit' to quit):"

while :
do
    read -p "Name: " name
    if [ "$name" = "exit" ]; then
        break
    fi

    echo "Hello ---> $name!"
done

echo "you are exited"
```

---

### **Example 4: Calculating Factorial**

```bash
#!/bin/bash

echo "Enter a number to calculate its factorial:"
read num

if [ $num -gt 0 ]; then

factorial=1
counter=$num

while [ $counter -gt 0 ]
do
    factorial=$(( factorial * counter ))
    (( counter-- ))
done

echo "Factorial of $num is: $factorial"

else

echo "invalid input"

fi
```

---

## 📌 8. **until Loop**

Runs **until the condition becomes true** (opposite of while loop).

---

### **Example 1: Counting Up from 1 to 10**

```bash
#!/bin/bash

counter=1

echo "Counting up:"
until [ $counter -gt 10 ]
do
    echo "$counter"
    (( counter++ ))
done

echo "Done counting!"
```
