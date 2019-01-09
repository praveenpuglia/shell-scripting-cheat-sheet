# shell-scripting-cheat-sheet
Small, sweet shell things.

## Motivation
I don't know anything about shell scripts. Have always been scared and confused. Currently I am having to process a ton of audio files and had to not repeat myself doing same things over and over again. So here I am, learning shell things!

### Variables
- While assigning a value to a variable, don’t use space around `=`.
```sh
# Good
APPLE='is a fruit'
# Bad
APPLE = 'is a fruit'
```
- Print variables within quotes to preserve their whitespace if they contain any.
```sh
$greeting='Hello      World'
echo $greeting # Hello World
echo "$greeting" # Hello      World
```
- To not have $ treated as a special character denoting a variable inside echo, use backslash `\`
```sh
echo "\$greeting" # $greeting
```
Useful for printing things like 'Amount : $200.00'

- Within quotes, variables can also be printed like `${MY_VARIABLE}`. This is to reduce ambiguity.

- The output of commands can be assigned to variables directly. Use back ticks or `$()` to wrap around the command.
```sh
FILES_LIST=`ls`
FILES_LIST=$(ls)
```
        
### Script/Command Arguments
- Getting arguments passed to a script is easy. `$1` is the first argument. `$2` is the second and so on.
    - TIP: assign the arguments to properly named variables inside scripts. Example - `DIRECTORY=$1`
    
### Arrays
```sh
# Define an array
MY_ARRAY=('apple', 'banana', 'orange')

# Length of an array
${#MY_ARRAY[@]}

# Get value by index
$MY_ARRAY[2]
```

