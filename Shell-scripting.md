**Commands:**

- _**vi:**_
     - **vi:** opens vi text editor
     - **i:** enters insert mode (press esc to exit)
     - **:setnu :** views line numbers
     - **:wq :** saves file and exits
     - **:q! :** does not save and exits
     - ![VI_Cheat_Sheet]
![VI_Cheat_Sheet](uploads/f54fccccfbc754c3f834d6a001d058ef/VI_Cheat_Sheet.png)
- _**nano:**_
     - **nano:** opens nano text editor
     - **ctrl + o:** saves file and gives option to rename
     - **ctrl + x:** exits out of nano editor
     - ![Nano_Cheat_Sheet]
![Nano_Cheat_Sheet](uploads/1ae04a68ab962aa575784a4083df06d3/Nano_Cheat_Sheet.png)
- **Create bash script:** (text editor command, either vi or nano) (name of file).sh
     1.  **#!/bin/bash:** called 'SHEBANG', needs to put as the first line
     2.  **chmod 755: ** allows for bash script to be executed, will not work otherwise
     3.  **./(name of bash script) (any input to be passed to the script)**: executes bash script
     - **passing parameters:** use &1_&2_...etc within scripts to pass parameters
- **Logic based on input:**
```shell
if [ $1 == '1' ]
    then
    echo "The argument entered was 1"
    exit
fi

if [ $1 == '2' ]
then
  echo "The argument entered was 2"
  exit
else
  echo "The argument entered was not 2"
  exit
fi
```
![Bash_Cheatsheet]![Bash_Cheatsheet](uploads/fe5388bb0c0920d6eebe3abf4b642964/Bash_Cheatsheet.png)

- **chmod:** chmod[reference][operator][mode] file
     - **Owner (-u):** file's owner
     - **Group (-g):** members of the file's group
     - **Other (-o):** users not apart of the file group or owner
     - **All (-a):** all three
     - **+:** add a permission from the class
     - **-:** remove a permission from the class
     - **=:** exact modes for the class
     - **r:** read
     - **w:** write
     - **x:** execute
     - ![chmod_permissions]
![chmod_permissions](uploads/d5caa7f78ebceb8a8eaeaa07ea0dd375/chmod_permissions.png)