# 🧮 Arrays in Shell Scripting

## ✅ Definition
An array in shell scripting allows you to store and manage multiple values under a single variable name.

- 🔢 Indexing starts at **0**.

---

# 📌 Declaring Arrays

## **Implicit Declaration**
```bash
name_array=("kk" "sai" "raghu")
````

## **Explicit Declaration**

```bash
declare -a name_array
name_array=("kk" "sai" "raghu")
```

---

# 🎯 Accessing Array Elements

```bash
echo "${name_array[0]}"  # Output: kk
echo "${name_array[1]}"  # Output: sai
echo "${name_array[2]}"  # Output: raghu
```

---

# ⚙️ Common Array Operations

## 1️⃣ ➕ Append Elements

```bash
name_array+=("jaswanth")
```

## 2️⃣ 📏 Length of Array

```bash
echo "${#name_array[@]}"  # Output: 4
```

## 3️⃣ 🔁 Iterate Over Array

```bash
name_array=("kk" "sai" "raghu")
for element in "${name_array[@]}"
do
    echo "$element"
done
```

## 4️⃣ ❌ Remove an Element

```bash
unset name_array[1]  # Removes "sai"
```

## 5️⃣ 🧹 Clear Entire Array

```bash
name_array=()
```

---

# 🧪 Practical Examples

## 🧺 Example 1: Basic Array Usage

```bash
#!/bin/bash
declare -a fruits=("Apple" "Banana" "Orange")

echo "All fruits:"
for fruit in "${fruits[@]}"; do
    echo "$fruit"
done

echo "Number of fruits: ${#fruits[@]}"

fruits+=("Grapes")
echo "Updated number: ${#fruits[@]}"

echo "First fruit: ${fruits[0]}"

unset fruits[1]

echo "After removal:"
for fruit in "${fruits[@]}"; do
    echo "$fruit"
done
```

---

## 📄 Example 2: Processing File Names

```bash
#!/bin/bash

# Declare an array to store file names
declare -a files=()

# Populate the array with file names ending in .sh in current directory
files=(*.sh)

# Iterate over each file and perform an operation (e.g., count lines)
for file in "${files[@]}"
do
    line_count=$(wc -l < "$file")
    echo "File: $file has $line_count lines."
done
```

### ✅ What Does It Do?

* **wc**: Stands for word count, a Linux command-line utility.
* **-l**: Tells `wc` to count only the number of lines in a file.
* **< "$file"**: This is input redirection — it passes the contents of `$file` directly to `wc -l` without printing the filename.

---

## 🎤 Example 3: Processing Command-Line Arguments

```bash
#!/bin/bash

# Store command-line arguments in an array
args=("$@")

# Print all arguments
echo "All arguments:"
for arg in "${args[@]}"
do
    echo "$arg"
done

# Print total number of arguments
echo "Length of array: ${#args[@]}"

# Access individual argument
echo "First argument: ${args[0]}"
```

---

## 📜 Example 4: Dynamic Menu with User Selection

```bash
#!/bin/bash

# Array of menu options
declare -a menu=("Option 1: Print Working Directory (pwd)" \
                 "Option 2: Display Calendar (cal)" \
                 "Option 3: Clear Screen (clear)" \
                 "Option 4: Exit")

# Display menu
echo "===== Bash Menu ====="

select option in "${menu[@]}"
do
    case $REPLY in
        1)
            echo "You selected: Print Working Directory"
            pwd
            ;;
        2)
            echo "You selected: Display Calendar"
            cal
            ;;
        3)
            echo "You selected: Clear Screen"
            clear
            ;;
        4)
            echo "You selected: Exit"
            echo "Exiting... Bye!"
            break
            ;;
        *)
            echo "❌ Invalid option. Please choose a number between 1 and 4."
            ;;
    esac
    echo "========================="
done
```
