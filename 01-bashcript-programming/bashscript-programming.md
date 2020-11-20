# Comments
```bash
# this is a comment
```

# Variables
```bash
#!/usr/bin/env bash

# Note that spaces cannot be used around the `=` assignment operator

whom_variable="World"
printf "Hello, %s\n" "$whom_variable"
```

# User Input
```bash
#!/usr/bin/env bash
echo "Who are you?"
read name
echo "Hello, $name."
```

# Arrays
**Create and array**
```bash
array=('first element' 'second element' 'third element')

# Explicit element indexes
array=([3]='fourth element' [4]='fifth element')

# Assignment
array[0]='first element'
array[1]='second element'

# Length
echo "${#array[@]}"

# Keys
echo "${!array[@]}"
```

```bash
# Associative array
declare -A array
array[first]='First element'
array[second]='Second element'
```

**Accessing elements in array**
```bash
# Print element at index 0
echo "${array[0]}"

# Print last element using substring expansion syntax
echo "${array[@]: -1 }"

# Print last element using subscript syntax
echo "${array[-1]}"

# Print all elements, each quoted separately
echo "${array[@]}"

# Print all elements as a single quoted string
echo "${array[*]}"

# Print all elements from index 1, each quoted separately
echo "${array[@]:1}"

# Print 3 elements from index 1, each quoted separately
echo "${array[@]:1:3}"
```

**Array Modification**
```bash
# Change Index
array[10]="elevenths element" # because it's starting with 0

# Append
array+=('fourth element' 'fifth element')

# Replace the entire array with a new parameter list.
array=("${array[@]}" "fourth element" "fifth element")

# Add an element at the beginning:
array=("new element" "${array[@]}")

# Insert an element at a given index:
arr=(a b c d)
# insert an element at index 2
i=2
arr=("${arr[@]:0:$i}" 'new' "${arr[@]:$i}")
echo "${arr[2]}" #output: new

# Delete array indexes using the unset builtin:
arr=(a b c)
echo "${arr[@]}" # outputs: a b c
echo "${!arr[@]}" # outputs: 0 1 2
unset -v 'arr[1]'
echo "${arr[@]}" # outputs: a c
echo "${!arr[@]}" # outputs: 0 2

# Merge
array3=("${array1[@]}" "${array2[@]}")
# This works for sparse arrays as well.

# Re-indexing an array
array=("${array[@]}")
```

**Array Iteration**
```bash
a=(1 2 3 4)
# foreach loop
for y in "${a[@]}"; do
  echo "$y"
done

# classic for-loop
for (( i = 0; i < ${#a[@]}; ++i )); do
  echo "${a[$i]}"
done
```

# Associative Arrays
```bash
# Declare an associative array
declare -A aa=([hello]=world [ab]=cd ["key with space"]="hello world")

echo "${!aa[@]}" # keys
echo "${#aa[@]}" # length

# Assignment
aa[hello]=world
aa[ab]=cd
aa["key with space"]="hello world"
```

```bash
# Iterate over associative array keys and values
for key in "${!aa[@]}"; do
  echo "Key: ${key}"
  echo "Value: ${array[$key]}"
done
```

# Control Structures
| Parameter | Details |
|-----------|---------|
| **File Operators Details** |
| -e "$file" | Returns true if the file exists. |
| -d "$file" | Returns true if the file exists and is a directory |
| -f "$file" | Returns true if the file exists and is a regular file |
| -h "$file" | Returns true if the file exists and is a symbolic link |
|-------------------------------|
| **String Comparators Details**|
| -z "$str" | True if length of string is zero |
| -n "$str | True if length of string is non-zero |
| "$str" = "$str2" | True if string $str is equal to string $str2. Not best for integers. It may work but will be inconsitent |
| "$str" != "$str2" | True if the strings are not equal |
|-------------------------------|
| **Integer Comparators Details** |
|"$int1" -eq "$int2" | True if the integers are equal |
|"$int1" -ne "$int2" | True if the integers are not equals |
|"$int1" -gt "$int2" | True if int1 is greater than int 2 |
|"$int1" -ge "$int2" | True if int1 is greater than or equal to int2 |
|"$int1" -lt "$int2" | True if int1 is less than int 2 |
|"$int1" -le "$int2" | True if int1 is less than or equal to int2 |

**Short-circuit evaluation**
```bash
# this will only print the current directory if the cd command was successful.
cd my_directory && pwd

# this will exit if the cd command fails, preventing catastrophe
cd my_directory || exit
rm -rf *
```

```bash
# use case
my_function () {
  ### ALWAYS CHECK THE RETURN CODE
  # one argument required. "" evaluates to false(1)
  [[ "$1" ]] || return 1
  # work with the argument. exit on failure
  do_something_with "$1" || return 1
  do_something_else || return 1
  # Success! no failures detected, or we wouldn't be here
  return 0
}
```

**If esle statement**
```bash
# The `[[` are not part of the syntax, but are treated as a command; it is the exit code from this command that is being tested.

number=1
if [[ $number -eq 1 ]]; then
  echo "1 was passed in the first parameter"
elif [[ $number -gt 2 ]]; then
  echo "2 was not passed in the first parameter"
else
  echo "The first parameter was not 1 and is not more than 2."
fi
```

```bash
if grep "foo" bar.txt; then
  echo "foo was found"
else
  echo "foo was not found"
fi
```

```bash
# Mathematical expressions

if (( $1 + 5 > 91 )); then
 echo "$1 is greater than 86"
fi
```

```bash
#  These are defined in the POSIX standard and are guaranteed to work in all POSIX-compliant shells including Bash

if [ "$1" -eq 1 ]; then
  echo "1 was passed in the first parameter"
elif [ "$1" -gt 2 ]; then
  echo "2 was not passed in the first parameter"
else
  echo "The first parameter was not 1 and is not more than 2."
fi
```

**Looping**
```bash
# {1..10} expands to "1 2 3 4 5 6 7 8 9 10"

for i in {1..10}; do
  echo $i
done
```

```bash
# looping over an array

arr=(a b c d e f)
for i in "${arr[@]}"; do
  echo "$i"
done
```

```bash
# looping over an array with C-like style

arr=(a b c d e f)
for (( i = 0; i < ${#arr[@]}; i++ )); do
  echo "${arr[$i]}"
done
```

```bash
# looping over an array

arr=(a b c d e f)
i=0
while [ $i -lt ${#arr[@]} ];do
  echo "${arr[$i]}"
  i=$(expr $i + 1)
done
```

```bash
# looping over an array

arr=(a b c d e f)
i=0
while (( $i < ${#arr[@]} ));do
  echo "${arr[$i]}"
  ((i++))
done
```

```bash
i=5
until [[ i -eq 10 ]]; do #Checks if i=10
  echo "i=$i" # Print the value of i
  i=$((i+1)) #Increment i by 1
done
```

`continue` and `break`. It's easy!

**Switch case**
```bash
case "$BASH_VERSION" in
  [34]*)
    echo {1..4}
    ;;
  *)
    seq -s" " 1 4
esac
```

# Functions
```bash
# $@ refer to all arguments
# $1 is the first arguments

greet() {
  local name="$1"
  echo "Hello, $name"
}
greet "John Doe"
```

**Named parameters**
```bash
foo() {
  while [[ "$#" -gt 0 ]]
  do
    case `$1 in
      -f|--follow)
        local FOLLOW="following"
        ;;
      -t|--tail)
        local TAIL="tail=$2"
        ;;
    esac
    shift
  done
  echo "FOLLOW: $FOLLOW"
  echo "TAIL: $TAIL"`
}

# test
foo -f
foo -t 10
foo -f --tail 10
foo --follow --tail 10
```

# Sourcing
Sourcing a file is different from execution, in that all commands are evaluated within the context of the current
bash session - this means that any variables, function, or aliases defined will persist throughout your session.

Create the file you wish to source sourceme.sh
```bash
#!/bin/bash
export A="hello_world"
alias say_hi="echo Hi"
say_hello() {
  echo Hello
}
```

```bash
source sourceme.sh
```

```bash
echo $A
# hello_world
sayHi
# Hi
sayHello
# Hello
```

# References
[Bash Notes for Professionals book](https://goalkicker.com/BashBook/)