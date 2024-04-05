### Used commands
- `mkdir` creates a directory
- `tree` poduces a depth-indented listing of files
- `mv` used to move one or more files or directories from one place to another. Also can be used to rename.
#### Command Options
- `mkdir -v` - displays a message for every directory created
- `mkdir -p` enables create of parent directories as necessary 
- `mv -f` forces does not prompt before overwriting
- `mv -i` interactive makes the command ask the user if it is going to overwrite a file
- `mv -r` remove a non empty directory
#### mkdir
Use to make multiple directories at once, and can be used to set permissions. Such as `mkdir -p first/second/third`
#### tree command
Recursive directory listing that produces depth-indented listing of files.
- `tree -a` all files are printed
- `tree -d` list directories only
- `tree -f` prints the full path prefix for each file
## Absolute and Relative Paths
A path is a unique location of a file or folder in an OS, a path to a file is a combo of forward slashes / and characters.

`echo $PATH` gives your paths to bins so you can run as if you are in that directory

You can change with relative (`..`) or with absolute (/).
### Absolute Path /
The specified location of a file from the root directory (/). So a command to save on an absolute path is `mv receipts.txt /user/joe/work/receipts.txt`
### Relative Path
A relative path is in reference to the working directory. It starts with current directory and **NEVER** begins with forward slash.
- `~` is the home directory
- `.` is the current working directory
- `..` moves up on directory (parent) so `../..` would move you up 2 directories.
## Symbolic Links
A link as a pointer to a file.

### Soft Link
Merely a string that is a symbol for the path, does not contain the contents. Removing file makes the link become 'dangling' pointing to nonexistent file. Can link to a directory to. To create it, use the `ln -s [original filename] [link name]`.

### Hard Link
Remains linked after files are moved around or name change, contains actual file content almost a copy - takes up space. If removed, hard link will still show it. Can not create for directory, special files, or different file systems. Changes made will reflect in other files. Create with `ln  [original filename] [link name]`.

