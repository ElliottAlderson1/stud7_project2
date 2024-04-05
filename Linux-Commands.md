## Commands
- `hostname` displays host name
- `whoami` - display current user
- `ip address show` displays IP address `ip a` is short way to type it
- `su` - switch user, the default user is root, and requires the su account password
- `sudo` - allows user to execute system commands with root privileges users are in the `/etc/sudoers` file.
- `usermod` command to add user to group
- `ls` list all files and directories is working directory
- `cd` navigates directory
- `pwd` displays current directory the user is in
- `echo` - displays line of string/text that are passed as an argument, if no arguments, the input becomes the output
- `cat` display line of text/string 
- `mkdir <-p first/second/third>` the -p flag enables the command to create parent directories as necessary.
- `>` command will overwrite any contents currently in the file.
- `>>` command will append file

### Command Line Syntax
- Specific Synax you must follow - `CommandName [option(s)][parameters]
- Case sensitivity is important (with flags too `-A` vs `-a`)
- Multiple commands can be seperated by a semi-colon `;`

### Command Options and Arguments
`ls`
- `-l` displays long format - details
- `-a` lists all files and directories
- `-la` combines the two
- `-h` makes it human readable
- `R` lists sub directories recursively
`cd`
- `cd ~/` Navigates to home directory
- `cd ..` Navigates to previous directory
- `cd /` Navigates to root directory
- `echo`
- Quotations ("") and backslash (\) allow the use of special characters in a line.
- `echo` dispaly a line of text/string that can be passed as argument, if no arguments, input becomes output

### MAN Pages 
Manual pages that are the references. Installed with package `/usr/share/man directory`.Use the command `man [command]` to get the pages. Written by devs and self contained. Also for the version you have installed.

### Info Pages
More like a book.

Navigate through the pages with the following commands: `p` previous page, `n` next page, `q` exit.


