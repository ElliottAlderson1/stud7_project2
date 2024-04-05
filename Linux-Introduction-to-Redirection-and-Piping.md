# Lab 03 Introduction to Redirection and Piping

## In this lab you will cover

* [Accessing your student VM from the Command prompt using SSH](#task-1-accessing-your-student-vm-from-the-command-prompt-using-ssh)
* [Redirecting the standard output](#task-2-redirecting-the-standard-output)
* [Redirecting input](#task-3-redirecting-input)
* [Redirecting standard errors](#task-4-redirecting-standard-errors)
* [Passing data between Linux shell commands with piping](#task-5-passing-data-between-linux-shell-commands-with-piping)

### Resources

* See instructional material

### Task 1 - Access your student VM from the Command prompt using SSH

#### Step 1 - Open the Command Prompt program on Windows

#### Step 2 - Remotely connect to your Student Virtual Machine(VM) using SSH

### Task 2 - Redirecting the standard output

#### Step 1 - Create lab Directories and files in the Linux shell

* Change to your home directory:

  ```shell
  cd ~/
  ```
* Change to the `Documents` directory:

  ```shell
  cd Documents
  ```

  > if a `Documents` directory does not exist, create one and change into it.
* Create a new directory `test` in the `Documents` directory:

  ```shell
  mkdir test
  ```
* Change to the `test` directory:

  ```shell
  cd test
  ```
* Create the following files in the `test` directory:

  ```shell
  touch barry.txt
  touch bob
  touch example.png
  touch firstfile
  touch foo1
  touch video.mpeg
  ```
* Verify that the files were created in the `test` directory:

  ```shell
  ls
  ```
* You should see:

  ```shell
  barry.txt  bob  example.png  firstfile  foo1  video.mpeg
  ```

#### Step 2 Write the standard output to a file

Writing from standard output:

* `>` Creates a non-existant file and writes to it, or overwrites an existing file.
* `>>` Creates a non-existant file and writes to it, or appends to an existing file.
* `Redirect` the directory listing to the new file `myoutput`:

  ```shell
  ls > myoutput
  ```
* View the contents of the new `myoutput` file:

  ```shell
  cat myoutput
  ```
* You should see:

  ```shell
  barry.txt
  bob
  example.png
  firstfile
  foo1
  myoutput
  video.mpeg
  ```
* View the number of lines in the `myoutput` file:

  ```shell
  wc -l myoutput
  ```

  > The `wc` command is used for counting words in a file, but has many options that can be viewed in it's `man` page.
* You should see:

  ```shell
  7 myoutput
  ```

#### Step 3 - Redirect the standard output to overwrite existing content in a file

* `Redirect` the output of the `wc -l` command to `write` to the `myoutput` file:

  ```shell
  wc -l myoutput > myoutput
  ```
* View the contents of the `myoutput` file:

  ```shell
  cat myoutput
  ```
* You should see:

  ```shell
  0 myoutput
  ```

  > Just understand that the contents of the `myoutput` file was overwritten.
* Redirect the output of the `ls` command to the `barry.txt` file:

  ```shell
  ls > barry.txt
  ```
* View the contents of the `barry.txt` file:

  ```shell
  cat barry.txt
  ```
* You should see:

  ```shell
  barry.txt
  bob
  example.png
  firstfile
  foo1
  myoutput
  video.mpeg
  ```
* `Overwrite` the contents of the `myoutput` file with the output of the `wc -l` command:

  ```shell
  wc -l barry.txt > myoutput
  ```
* view the contents of the `myoutput` file:

  ```shell
  cat myoutput
  ```
* You should see:

  ```shell
  7 barry.txt
  ```

#### Step 4 - Redirect the standard output to append to an existing file

* `Append` the `myoutput` file with the output of the `wc -l` command:

  ```shell
  wc -l barry.txt >> myoutput
  ```

  > Notice the double greater than signs ">>". This is an append operation.
* Verify that the output of the `wc -l` command was appended to the end of the `myoutput` file:

  ```shell
  cat myoutput
  ```
* You should see:

  ```shell
    7 barry.txt
    7 barry.txt
  ```
* `Append` the directory listing to the `myoutput` file:

  ```shell
  ls >> myoutput
  ```
* Verify that the output of the `ls` command was appended to the end of the `myoutput` file:

  ```shell
  cat myoutput
  ```
* You should see:

  ```shell
  7 barry.txt
  7 barry.txt
  barry.txt
  bob
  example.png
  firstfile
  foo1
  myoutput
  video.mpeg
  ```

### Task 3 - Redirecting input

#### Step 1 - Redirect the contents of a file to the standard input

* View the output of the `wc -l` command when the file `myoutput` is given as a file to be read:

  ```shell
  wc -l myoutput
  ```
* You should see:

  ```shell
  9 myoutput
  ```

  > This output indicates that the `wc -l` command read the file `myoutput` and found 9 lines.
* View the output of the `wc -l` command when the file `myoutput` is given as a `standard input` to be read by using the `<` character:

  ```shell
  wc -l < myoutput
  ```
* You should see:

  ```shell
  9
  ```

  > A filename is not displayed in the results in this example because a file was not given to the `wc -l` command. Instead the contents of the `myoutput` file was read as `standard input` into the `wc -l` command as though the contents of the `myoutput` file was read from the keyboard.

#### Step 2 - Input and output redirection in the same command

* Read the contents of the `barry.txt` file as `standard input` to the `wc -l` command. Then, write the output to the `myoutput` file:

  ```shell
  wc -l < barry.txt > myoutput
  ```
* View the contents of the `myoutput` file:

  ```shell
  cat myoutput
  ```
* You should see:

  ```shell
  7
  ```
* Verify that the \`barry.txt file has 7 line entries:

  ```shell
  cat barry.txt
  ```

  > Counting the lines, you should see that the file contains 7 lines.

#### Step 3 - Input and output redirection in the same command and then append to an existing file

* Read the contents of the `barry.txt` file as `standard input` to the `wc -l` command, and append the output to the `myoutput` file:

  ```shell
  wc -l < barry.txt >> myoutput
  ```
* View the contents of the `myoutput` file:

  ```shell
  cat myoutput
  ```
* You should see:

  ```shell
  7
  7
  ```

### Task 4 - Redirecting standard errors

Writing from standard error:

* `2>` Creates a non-existant file and writes to it, or overwrites an existing file.
* `2>>` Creates a non-existant file and writes to it, or appends to an existing file.

#### Step 1 - Redirecting standard errors to a file

* Attempt to list the `video.mpeg` file, and the non-existant `blah.foo` file:

  ```shell
  ls video.mpeg blah.foo
  ```
* You should see:

  ```shell
  ls: cannot access 'blah.foo': No such file or directory
  video.mpeg
  ```
* Run the same commands as the previous step, but `redirect` the `standard error` messages to the `errors.txt` file:

  ```shell
  ls video.mpeg blah.foo 2> errors.txt
  ```
* You should see:

  ```shell
  video.mpeg
  ```
* Verify that you now have a new `errors.txt` file:

  ```shell
  ls
  ```
* You should see:

  ```shell
  barry.txt  bob  errors.txt  example.png  firstfile  foo1  myoutput  video.mpeg
  ```

  > Notice that the file `errors.txt` was created.
* Verify that any `standard errors` were written to the `errors.txt` file:

  ```shell
  cat errors.txt
  ```
* You should see:

  ```shell
  ls: cannot access 'blah.foo': No such file or directory
  ```

  > Note that this is the contents of the errors.txt file.

#### Step 2 - Redirect standard output and standard errors to a file

* `Redirect` the `standard output` and `standard error` to the same file:

  ```shell
  ls video.mpeg blah.foo > myoutput 2>&1
  ```

  > The `&1` on the the end is a pointer to the standard input. Combining this `&1` with the `2>` command tells the Linux shell to redirect any `standard error` to the `standard input`. Then, any of these `standard errors` that were redirected to the `standard input` are redirected to the `myoutput` file.
* Verify that the `standard input`, and `standard error` messages were both redirected to the `myoutput` file:

  ```shell
  cat myoutput
  ```
* You should see:

  ```shell
  ls: cannot access 'blah.foo': No such file or directory
  video.mpeg
  ```

  > Note that this is the contents of the errors.txt file.

### Task 5 - Passing data between Linux shell commands with piping

Command line pipes: - The output of the first command is used as the input for the second command - Allows for the quick execution of commands performing complex tasks

#### Step 1 - Combine two commands with a pipe

* Combine the `ls` and `head -5` command to view the first five outputs of the `ls` command:

  ```shell
  ls | head -5
  ```
* You should see:

  ```shell
  barry.txt
  bob
  errors.txt
  example.png
  firstfile
  ```

#### Step 2 - Combine three commands with a pipe

* Add a third command `tail -2` to the previous two commands to view only the last two outputs:

  ```shell
  ls | head -5 | tail -2
  ```

  > This command performs a listing of the directory contents, then passes that list to the `head -5` command, which then passes only the first five outputs to the `tail -2` command, which prints only the last two outputs to the terminal output that you see on the screen.
* You should see:

  ```shell
  example.png
  firstfile
  ```

#### Step 3 - Use output redirection with piping

* `Redirect` the output from the previous example into the `directory.txt` file:

  ```shell
  ls | head -5 | tail -2 > directory.txt
  ```
* Verify the contents of the `directory.txt` file:

  ```shell
  cat directory.txt
  ```
* You should see:

  ```shell
  errors.txt
  example.png
  ```

  > The output here is different than in the previous example because the `directory.txt` file has been added to the directory listing and now changes the contents of the first five lines and last two lines of output.