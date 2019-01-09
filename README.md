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

- To not have \$ treated as a special character denoting a variable inside echo, use backslash `\`

```sh
echo "\$greeting" # $greeting
```

Useful for printing things like 'Amount : \$200.00'

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
MY_ARRAY=('apple' 'banana' 'orange')

# All items of the array
echo ${MY_ARRAY[@]} # apple banana orange

# Length of an array
echo ${#MY_ARRAY[@]} # 3

# Get value by index
echo ${MY_ARRAY[2]} # banana
```

### Strings

```sh
# Define
MY_STRING="Hi! I am a String"

# Print entire string
echo $MY_STRING
echo $MY_STRING[@]

# Length
echo $#MY_STRING # 17

# Get substring
# Syntax: ${STRING:START_POSITION:LENGTH}
echo ${MY_STRING:0:3} # Hi!
# If LENGTH is removed, substring till end of string.
echo ${MY_STRING:4} # I am a String

# Replacing
# First occurence
echo ${MY_STRING[@]/a/o} # Hi! I om a String
# All occurences
echo ${MY_STRING[@]//a/o} # Hi! I om o String
# with another variable or expression
TEMP='an Idiot'
echo ${MY_STRING/a String/${TEMP}} # Hi! I am an Idiot
echo ${MY_STRING/String/String on $(date)} # Hi! I am a String at Wed Jan  9 17:03:09 IST 2019
```
