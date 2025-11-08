### Operators in Shell Scripting

Operators in shell scripting are used to perform operations such as arithmetic, comparison, logical checks, and string manipulations.

---

## 1️⃣ Arithmetic Operators

```bash
#!/bin/bash

# Arithmetic Operators
a=20
b=5
echo "Arithmetic Operations:"
echo "Addition of two numbers: $(( a + b ))"
echo "a - b = $(( a - b ))"
echo "a * b = $(( a * b ))"
echo "a / b = $(( a / b ))"
echo "a % b = $(( a % b ))"
````

| Syntax       | Meaning                         |
| ------------ | ------------------------------- |
| `(( ... ))`  | Perform arithmetic operations   |
| `$(( ... ))` | Return the result of arithmetic |

---

### Passing Values from Command Line

Run script:

```
sh open1.sh 20 5
```

#### Script:

```bash
#!/bin/bash

# Access command-line arguments
a=$1
b=$2

echo "Values received: a = $a, b = $b"

# Perform arithmetic operations
echo "Addition: $(( a + b ))"
echo "Subtraction: $(( a - b ))"
echo "Multiplication: $(( a * b ))"
echo "Division: $(( a / b ))"
echo "Modulus: $(( a % b ))"
```

---

## 2️⃣ Comparison Operators

```bash
a=20
b=30

echo "Comparison Operations:"
if [ $a -eq $b ]; then
    echo "a is equal to b"
fi
if [ $a -ne $b ]; then
    echo "a is not equal to b"
fi
if [ $a -gt $b ]; then
    echo "a is greater than b"
fi
if [ $a -lt $b ]; then
    echo "a is less than b"
fi
```

| Operator | Meaning                      |
| -------- | ---------------------------- |
| `-eq`    | Equal to (`==`)              |
| `-ne`    | Not equal (`!=`)             |
| `-gt`    | Greater than (`>`)           |
| `-lt`    | Less than (`<`)              |
| `-ge`    | Greater than or equal (`>=`) |
| `-le`    | Less than or equal (`<=`)    |

---

## 3️⃣ Logical Operators

### AND (`&&`)

| A | B | A && B |
| - | - | ------ |
| T | T | T      |
| T | F | F      |
| F | T | F      |
| F | F | F      |

### OR (`||`)

| A | B | A || B |
|---|---|--------|
| T | T | T      |
| T | F | T      |
| F | T | T      |
| F | F | F      |

```bash
a=30
b=5

echo "Logical Operations:"
if [ $a -eq 20 ] && [ $b -eq 5 ]; then
    echo "Both conditions are true"
fi
if [ $a -eq 10 ] || [ $b -eq 5 ]; then
    echo "At least one condition is true"
fi
if ! [ $a -eq 0 ]; then
    echo "a is not equal to 0"
fi
```

---

## 4️⃣ String Operators

```bash
# String Operators
str1="Hello"
str2="World"

echo "String Operations:"
echo "=================="

if [ "$str1" = "$str2" ]; then
    echo "Strings are equal"
fi

if [ "$str1" != "$str2" ]; then
    echo "Strings are not equal"
fi

str3="$str1 $str2"
echo "Concatenated string: $str3"

length=${#str1}
echo "Length of str1 is $length"
```

| Expression           | Meaning                             |
| -------------------- | ----------------------------------- |
| `"$str1" = "$str2"`  | Checks if two strings are equal     |
| `"$str1" != "$str2"` | Checks if two strings are not equal |
| `${#str1}`           | Returns length of the string        |
