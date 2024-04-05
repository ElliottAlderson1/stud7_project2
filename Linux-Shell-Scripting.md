## sh and bash shell
`bash` is `sh` but with more features and better syntax. `shell` is the command line interface to run commands and shell scripts. `bash` supports job controls (stop, start, bring, process to foreground, or send to background).

`GNU Bourne Again SHell`, (`Bash`) Script is just like a simple text file, consisting of a number of commands that we usually write in a command line. In Linux file systems, they are used for doing repetitive tasks. 

`bash` can be invoked by single character command line - option/parameter or multiple. Consists of key bindings or hot-keys, bash provides one dimensional arrays with help we can manipulate lists.

![image](https://github.com/dpweldo/DEVOTC/assets/102386243/3b113793-17ac-4e04-a1c1-b3eec7526c85)

## Elements of a shell script
Shell script has the following:
- **Shell keywords** (if, else, break etc.)
- **Shell commands** (cd, ls, echo, touch etc.)
- **Functions**
- **Control flow** (if..then..else loops etc.)
- **Variables** (letters A-Z, 0-9 or underscore ‘_’)

More Info:
- Every script should begin with “#!/bin/bash” aka “SHEBANG”
- Every new line is a new command
- Comment lines start with a #
- Commands are surrounded by ()
- Scripts must be executable to work when called

### chmod command
Make the script executable:
~~~shell
chmod [reference] [operator] [mode] filename
chmod +x filename 
~~~
Operators
- `+` adds specified modes to the class
- `-` removes specified modes to the class
- `=` modes specified are to be made the exact modes for the specified  classes

- Owner -files owner
- Group - members of the files group
- Other - users not apart of the file group or owner
- All - all three of the above

![image](https://github.com/dpweldo/DEVOTC/assets/102386243/878bfc9f-efff-4f92-b0c7-f7ca6dec5aa0)

#### chmod examples

~~~shell
sudo chmod g+s sharedrive
sudo chmod 770 sharedrive
~~~

#### Octal
- 0 (0+0+0) --- 
- 1 (0+0+1) --x
- 2 (0+2+0) -w-
- 3 (0+2+1) -wx
- 4 (4+0+0) r--
- 5 (4+0+1) r-x
- 6 (4+2+0) rw-
- 7 (4+2+1) rwx

### File Execution
~~~shell
./filename
~~~

## Shell Script Statements
Sequences, Selections, Loops.

Loops: `while`, `for`, `until`, `select`

### While Loop
Execute some command until condtion occurs, usually when need to manipulate variable repeatedly. Useful when need to execute a set of commands while some condition is true

~~~shell
while [condition]
do
  Statement(s) to be executed if command is true
done
~~~

### For Loop
Operate on list of items, need to do something to those items. Repeats for every item in list.

~~~shell
for var in word1 word2 ... wordN
do
    Statement(s) to be executed for every word.
done
~~~

### until loop
Need to execute until condition is true.

~~~shell
until [condition]
do
    Statement(s) to be executed until command is true
done
~~~

### Select Loop
Useful when need user to chose one or more items from a list of choices. 

~~~shell
select var in word1 word2 ... wordN
do
   Statement(s) to be executed for every word.
done
~~~

### Conditional Statements
Given as
- if
- then
- elif
- else
- fi
- case and it’s closing statement esac

### If Else statements
Forms of if statements:
#### If…fi statement
Make decisions and execute statements conditionally.
~~~shell
if [ expression ] 
then 
   Statement(s) to be executed if expression is true 
fi
~~~
#### If…else statement
Allows execution statements in a controlled way and make the right choice.
~~~shell
if [ expression ]
then
    Statement(s) to be executed if expression
is true
else
    Statement(s) to be executed if expression
is not true
fi
~~~

#### If…elif…else…fi statement
Allows shell to make correct decision out of several conditions.
~~~shell
if [ expression 1 ]
then
    Statement(s) to be executed if expression 1 is true
elif [ expression 2 ]
then
    Statement(s) to be executed if expression 2 is true
elif [ expression 3 ]
then
    Statement(s) to be executed if expression 3 is true
else
    Statement(s) to be executed if no expression is true
fi
~~~
#### case...esac statement 
Can perform multipe if..elif statements for multi-way branch, not always best solution, especially when depend on value of single variable. Uses case...esac statement which does it more efficient.
~~~shell
case word in
  pattern1)
       Statement(s) to be executed if pattern1 matches
       ;;
  pattern2)
       Statement(s) to be executed if pattern2 matches
       ;;
  pattern3)
       Statement(s) to be executed if pattern3 matches
       ;;
       *)
       Default condition to be executed
       ;;
esac
~~~

## Shell Script Functions
To reuse code blocks, it is read into the memory and stored for later use, faster than repeating code, organization, and maintenance.

Bash Scripts are implemented two ways:
1. Inside the shell script where function must be before any calls of it
2. Along other bash alias commands and directly in the terminal as a command

~~~shell
<function name> () {
<commands>
}
~~~
~~~shell
function <function name> { <commands>; }
~~~

When writing in one line, the commands must end with a semicolon (;), whether in bash scripts or the terminal directly. The commands between the curly braces `{ <commands> }` are called the function's body. 

Argument is input to command line to process it, to pass arguments to function, add the parameters after the function call separated by spaces. 

![image](https://github.com/dpweldo/DEVOTC/assets/102386243/4bd480f7-15b8-4ad8-9b69-b366eed78453)

You can pass them like:

~~~shell
./logic.sh 1
~~~
The `$1` indicates the first parameter passed to the `logic.sh`

## Best Practices
- Use functions unless writing a very small script, to make readable, maintainable, and reusable
- Document functions sufficiently with purpose and arguments
- Avoid unnecessary pipelines, try to keep them small
- write error messages to stderr, belong in stderr not stdout



