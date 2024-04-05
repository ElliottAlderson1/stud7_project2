How to create a nano  user specific ".nanorc" file.

# Configuration File of Nano Text Editor:

You can configure Nano text editor system wide using the /etc/nanorc file.

You can also do user specific configuration of Nano text editor. In that case, you will have to create a .nanorc file in the HOME directory of the user you want to configure Nano for.

Using ~/.nanorc File for User Specific Configuration of Nano:

The ~/.nanorc file does not exist in your login users HOME directory by default. But, you can create one very easily with the following command:

## Task 1 Create the user specific .nanorc file.

### Step 1 - create and edit the **.nanorc** file using the nano text editor.

 ```md
nano ~/.nanorc
```
Do not exit the text editor

### Step 2 - Displaying Line Numbers in Nano

```md
set linenumbers
```

### Step 3 - Setting Tab Size in Nano

```md
set tabsize 2
```

### Step 4 - Auto indentation

```md
set autoindent
```

### Step 5 Save the file

- Once you’re done, you have to save the file. 
 - To save the file, press **Ctrl + x**. Then, press **y**.
 - Hit **Enter** to **save** file

### Step 6 view the file

- Display the content of the file using cat

```md
cat .nanorc
```
- Expected output

```
[stud1x@studx-admin-node ~]$ cat .nanorc
set linenumbers
set tabsize 2
set autoindent
[studx@studx-admin-node ~]$
```


