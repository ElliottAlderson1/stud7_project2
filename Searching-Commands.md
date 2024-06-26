**Commands:**

- **grep:** searches a file for a particular pattern of characters and displays all lines that contain
     - **grep -n:** display the matched lines and their line numbers
     - **grep -E:** treats pattern as an extended regular expression (ERE)
- **Regular Expression:** Special characters that help search for data and match complex pattern
     - **.:** replaces any character
     - **^:** matches start of a string
     - **$:** matches end of string
     - **\:** represents special characters
     - **():** groups regular expressions
     - **?:** matches up exactly one char
- **head:** used to display the first few lines of text
     - cat error.txt | head -n 5 (first 5 lines)
- **tail:** used to display the last few lines of text
     - cat error.txt | tail -n 10 (last 10 lines)
- **tar:** creates tar files by converting a group of files into an archive
     - [options][archive-file][file or directory to be archived]
     - **-c:** creates the archive
     - **-x:** extract the drive
     - **-f:** creates archive with given name
     - **-t:** list (or tree) contents of tar
     - **-z:** creates tar file using zip
     - **-r:** update/add to an existing tar file
     - **-delete:** remote file from tar
     - **tar -cvf file.tar dir1/:** create an uncompressed tar archive (creates a tar file called file.tar with the 'dir1' directory
     - **tar -cf:** creates a tar file
     - **tar -tf:** looks at the contents of a tar file
     - **tar -rf:** adds a file to a tar file
     - **tar -xf:** extracts a non-compressed tar file
     - **tar -czf:** creates a compressed tar file using gzip (.tgz file extension)
     - **tar -xzf:** extracts a compressed tar file