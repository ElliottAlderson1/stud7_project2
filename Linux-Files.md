### Relevant Commands
`touch` `echo` `cat` `rm` and `cp`
#### Command options
- `touch -c` used to check whether file is created, avoids creating file, and only checks if it exists. normal `touch` creates a file.
- `rm -rf` force remove a file
- `cp -b` creates a backup of the file in the same folder with a different name and in a different format.

## Redirection
Captures input of Three types of redirection operators.
1. Overwrite
- `>` used for standard output, will create a file
- `<` used for standard input
2. Appends
- `>>` standard output, will create a file
- `<<` standard input
3. Merge
- `p>&q` merges output p with q
- `p<&q` merges input p with q

### Standard Output
Using `ls` prints output of files of the `pwd`, so `ls > file.txt` would save to file and not print on screen. You can append with the `>>` operators. 
### Standard Input
Usually used to process the contents of a file. So `wc -l < file.txt` would get the number of lines as an output because `file.txt` is the input. It does not wait for the keyboard to input lines, kind of like a reverse pipe. 
### Standard Error
`2>` redirects the error of an output file. The error messages are redirected.

`2>&1` is used both standard error and output redirect

### Touch Command
Creates a file without any content, can create single or multiple files at once `touch filename1 filename2`. Will just update if the file already exists.

### Echo and Cat
To create a file both echo and cat must use a redirect.
- `echo "hello world" > file.txt`
- `cat "hello world" > file.txt`
or
- `echo "hello world" >> file.txt`
- `cat "hello world" >> file.txt`

## Manipulating Files
### cp
- `cp file1 file2` contents of file1 to file2, if file2 does not exist it will be created
- multiple files `cp file1 file2 (destination directory)`

### rm 
- `*` is a wildcard so `rm *` removes all
To remove an empty directory use `rmdir` or 'rm -r' for recursive removal. Can delete empty directory with 'rm -d' too.




