## grep - global regular expression print
Searches for pattern and returns that pattern. The pattern searched is referred to as the "regular expression". Two grep options used:
- `-n` dispalys the matched lines and their numbers
- `-E` treats pattern as an extended regular expression

Three Main Match Types:
1. `Literal Matches` -character-for-character match
2. `Anchor Matches` -specify where in the line a match must occur to be valid.
3. `Matching Any Character` -any single character can exist at the specified location.


### Pipe command `|`
Form of redirection, combines two or more commands, sends output of command to another command
- `command1 | command2 | command3`
### Regular Expression
Special characters or set of characters that help us to search data. Symbols:
- `.` replaces any character
- `^` matches start of string or beginning of line
- `$` matches end of string or end of a line
- `\` represents special characters, use when done want treat as wildcard such as `\.`
- `()` groups regular expressions
- `?` matches up exactly one character
- `[]` contains a range of text
- `(?: ... )` This is a non-capturing group, which means it groups the contained regular expression without storing what was matched.
- `[0-9]{1,3}` This matches any sequence of digits (0-9) that is at least 1 digit long but no more than 3 digits long.
- `\.` This matches a literal dot. It's escaped with a backslash because a dot has special meaning in regular expressions (it matches any single character).
- `{3}` This specifies that the preceding element should be repeated exactly 3 times.


### Cat command of head and tail
#### head
Display first few lines of text
- `cat error.txt | tail -n 10`

#### tail
Display last few lines of text
- `cat error.txt | head -n 5`

Extra example of first 5 lines of last 20 lines
- `cat error.txt | tail -n 20 | head -n 5`

### Grep Practice
Search for letter 'a'
~~~bash
cat sample | grep a
~~~

Search for content that starts with 'a'
~~~bash
cat sample | grep ^a
~~~

Search for the letter 't' in the file with grep
~~~bash
cat sample | grep t
~~~


**FILL IN HERE LATER**
## tar
Create, Zip, and Extract.

Stands for tape archive. Create by converting a group of files into archive. Archive is one or more files along with metadata. 

Tar can also:
- extract tar archives
- display list of the files included in the archive
- add additional files to existing archive
- compress or un-compress archive files

Syntax is `tar [options] [archive-file] [file or directory to be archived]`

#### Tar Options
Don't flag these
- `c` creates archive IMPORTANT
- `x` extract archive IMPORTANT
- `f` creates archive with given name
- `t` list (or tree) contents of tar
- `z` creates tar file using zip
- `r` update/add to an existing tar file
- `v` adds verbose to show results of running command
- `delete` remote file from tar

Create a uncompressed tar archive with the `cvf` option and have it be named `file.tar` from the directory dir1.
~~~bash
tar -cvf file.tar dir1/
~~~

To create a compressed archive use with the `zvf` option.  
~~~bash
tar -zvf file.tar dir1
~~~

### Archive Types
#### tar
Simple uncompressed tar file with `.tar` extension. Will preserve all file attributes including ACLs and SELinux security context.
#### gzip -z
Medium compression file with `.tar.gz` extension
#### bzip -j
Highly compressed file with `.tar.bz2` extension
#### xzip -J
Super compressed file with `.tar.xz` extension

### Commands 
- `cf`: Creates a tar file.
- `tf`: Looks at the contents of a tar file.
- `rf`: Adds a file to a tar file.
- `xf`: Extracts a non-compressed tar file.
- `czf`: Creates a compressed tar file using gzip (.tgz file extension).
- `xzf`: Extracts a compressed tar file.

![image](https://github.com/dpweldo/DEVOTC/assets/102386243/d9b52639-deef-4f7a-b1da-e78e92f5e27f)



