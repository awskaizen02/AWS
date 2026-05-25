# 🐚 Shell Scripting Notes (Basic → Advanced)

## 1. Introduction to Shell

- **[What is Shell](ca://s?q=Explain_what_is_Shell)**: Command interpreter for Unix/Linux.
- **[Why Shell Scripting](ca://s?q=Why_use_Shell_Scripting)**: Automates repetitive tasks, system administration, DevOps workflows.

## **[Types of Shells](ca://s?q=Types_of_Shells)**

| Shell | Description        |
| ------ | ------------------ |
| sh     | Bourne Shell       |
| bash   | Bourne Again Shell |
| ksh    | Korn Shell         |
| csh    | C Shell            |
| zsh    | Z Shell            |

---

## Shell Script File Extension

```sh
.sh
test.sh
```

---

## 2. Basics of Shell Scripting

### **[Script Structure](ca://s?q=Shell_script_structure)**

```bash
#!/bin/bash
echo "Hello World"
```

## Give Permission

```bash
chmod +x test.sh
```

## Execute Script

```bash
./test.sh
```

## Understanding Shebang

```bash
#!/bin/bash
```

### Purpose

- Defines interpreter
- Executes script using Bash shell

---

## Comments

### Single Line Comment

```bash
# This is a comment
```

### Multi Line Comment

```bash
: '
line one
line two
'
```

---

## Variables

```bash
name="Raja"
echo "Welcome $name"
```

---

## User Input

```bash
read -p "Enter your age: " age
echo "You are $age years old"
```

---

# Special Variables

| Variable | Meaning              |
| -------- | -------------------- |
| `$0`     | Script name          |
| `$1-$9`  | Positional arguments |
| `$#`     | Number of arguments  |
| `$*`     | All arguments        |
| `$@`     | Separate arguments   |
| `$$`     | Process ID           |
| `$?`     | Exit status          |

---

# Exit Status

| Code     | Meaning |
| -------- | ------- |
| 0        | Success |
| Non-zero | Failure |

```bash
mkdir test

echo $?
```

---

# Arithmetic Operations

```bash
a=10
b=20

sum=`expr $a + $b`

echo $sum
```

## Using Double Parenthesis

```bash
sum=$((10+20))

echo $sum
```

---

# Arithmetic Operators

| Operator | Meaning        |
| -------- | -------------- |
| +        | Addition       |
| -        | Subtraction    |
| *        | Multiplication |
| /        | Division       |
| %        | Modulus        |

# Relational Operators

| Operator | Meaning          |
| -------- | ---------------- |
| -eq      | Equal            |
| -ne      | Not equal        |
| -gt      | Greater than     |
| -lt      | Less than        |
| -ge      | Greater or equal |
| -le      | Less or equal    |

# String Operators

| Operator | Meaning          |
| -------- | ---------------- |
| =        | Equal            |
| !=       | Not equal        |
| -z       | Empty string     |
| -n       | Non-empty string |

# File Operators

| Operator | Meaning            |
| -------- | ------------------ |
| -f       | File exists        |
| -d       | Directory exists   |
| -r       | Read permission    |
| -w       | Write permission   |
| -x       | Execute permission |

---

# IF Statement

```bash
#!/bin/bash

a=10

if [ $a -gt 5 ]
then
    echo "Greater"
fi
```

# IF ELSE

```bash
#!/bin/bash

a=2

if [ $a -gt 5 ]
then
    echo "Greater"
else
    echo "Smaller"
fi
```

# IF ELIF ELSE

```bash
#!/bin/bash

marks=70

if [ $marks -ge 90 ]
then
    echo "Grade A"
elif [ $marks -ge 60 ]
then
    echo "Grade B"
else
    echo "Grade C"
fi
```

---

# Control Structures

## Conditional Statements

```bash
if [ $age -ge 18 ]; then
  echo "Adult"
else
  echo "Minor"
fi
```

---

# Loops

```bash
for i in {1..5}; do
  echo "Iteration $i"
done
```

## FOR Loop

```bash
#!/bin/bash

for i in 1 2 3 4 5
do
    echo $i
done
```

## WHILE Loop

```bash
#!/bin/bash

count=1

while [ $count -le 5 ]
do
    echo $count
    count=$((count+1))
done
```

## UNTIL Loop

```bash
#!/bin/bash

count=1

until [ $count -gt 5 ]
do
    echo $count
    count=$((count+1))
done
```

---

# Break Statement

```bash
for i in 1 2 3 4 5
do
    if [ $i -eq 3 ]
    then
        break
    fi

    echo $i
done
```

# Continue Statement

```bash
for i in 1 2 3 4 5
do
    if [ $i -eq 3 ]
    then
        continue
    fi

    echo $i
done
```

---

# Functions

```bash
greet() {
  echo "Hello $1"
}

greet Raja
```

## Exit Codes

```text
0 = success
non-zero = error
```

---

# File Handling

- Redirects: `>`, `>>`, `2>`
- Pipes: `ls | grep ".sh"`

```bash
while read line; do
  echo $line
done < file.txt
```

---

# Arrays

```bash
arr=("one" "two" "three")
echo ${arr[1]}
```

- Regular Expressions with `grep`, `sed`, `awk`
- Error Handling using `trap` and `set -e`
- Cron Jobs for automation

---

# Function Syntax

```bash
function hello() {

    echo "Hello World"

}
```

```bash
hello
```

---

# Function with Arguments

```bash
#!/bin/bash

function add() {

    sum=$(($1+$2))

    echo $sum
}

result=$(add 10 20)

echo $result
```

---

# Create Array

```bash
names=("Linux" "DevOps" "AWS")
```

## Access Elements

```bash
echo ${names[0]}
```

## Print All Elements

```bash
echo ${names[@]}
```

---

# Read File Line by Line

```bash
while read line
do
    echo $line
done < file.txt
```

---

# Redirect Operators

| Operator | Purpose          |
| -------- | ---------------- |
| >        | Redirect output  |
| >>       | Append output    |
| <        | Input redirect   |
| 2>       | Redirect error   |

# Standard Streams

| Stream | Description     |
| ------ | --------------- |
| stdin  | Standard Input  |
| stdout | Standard Output |
| stderr | Standard Error  |

---

```bash
#!/bin/bash

mkdir myfolder

echo "Folder created successfully"
```

---

```bash
#!/bin/bash

echo "Enter folder name:"
read folder

mkdir $folder

echo "$folder created successfully"
```

---

```bash
#!/bin/bash

folder="backup_$(date +%Y%m%d_%H%M%S)"

mkdir $folder

echo "Created folder: $folder"
```

---

```bash
#!/bin/bash

project="DevOps_Project"

mkdir -p $project/{scripts,logs,configs,backup}

echo "Project structure created"
```

---

```bash
#!/bin/bash

echo "Enter folder name:"
read folder

if [ -z "$folder" ]; then
    echo "Folder name cannot be empty"
    exit 1
fi

if [ -d "$folder" ]; then
    echo "Folder already exists"
else
    mkdir -p "$folder"
    echo "Folder '$folder' created successfully"
fi
```

---
