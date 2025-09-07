# Creating Files and Directories
step1: lets create a new directory called 'linux_practice'<br>
```bash
    mkdir linux_practice
```
step2: move to the new directory we created
```bash
    cd linux_practice
```
Note: we can also create sub-directories by using the following code<br>
```bash
mkdir -p books/hemmingway/fav
```
step3: create empty file called 'hello.txt'
```bash
    touch hello.txt
```
output:<br>
<img width="250" height="250" alt="Screenshot from 2025-09-07 12-01-16" src="https://github.com/user-attachments/assets/a7918de7-8459-4209-9fbb-f97afd2eeb0f" /><br>
step4: lets confirm our file was created or not.
```bash
ls
```
output:<br>
<img width="416" height="91" alt="Screenshot from 2025-09-07 12-04-13" src="https://github.com/user-attachments/assets/c40bdead-0461-4b80-b60e-589e1053d573" /><br>
step5: lets add some text to our file.
```bash
echo "Hello Linux" > hello.txt
```
`>` tells linux to put the output into a file instead of displaying it into screen.<br>
step6: viewing the contents of our file.
```bash
cat hello.txt
```
output:<br>
<img width="537" height="91" alt="Screenshot from 2025-09-07 12-11-18" src="https://github.com/user-attachments/assets/1bd68e77-26c0-4312-9170-098319ab5cdd" /><br>

# using wild cards
-wildcards are special characters that help you work with multiple files at once.<br>
-they are search patterns for file names.<br>
-search patterns mean systematic methods or algorithms used to fine specific information within a larger dataset,area or problem<br>
&nbsp;&nbsp;&nbsp; 1) lets create few more files.
```bash
touch file1.txt file2.txt file3.txt
```
●creates 3 new empty files<br>
&nbsp;&nbsp;&nbsp; 2) list all files ending with '.txt'
```bash
ls *.txt
```
●`*txt` mean any file ending with ".txt".<br>
output:<br>
<img width="589" height="122" alt="Screenshot from 2025-09-07 13-38-38" src="https://github.com/user-attachments/assets/5c2ac5fe-3e57-49de-a659-93b763070078" /><br>
&nbsp;&nbsp;&nbsp; 3)We can also create number of files using range.
```bash
touch note_(1..5).txt
```
&nbsp;&nbsp;&nbsp; 4)listing the files starting with 'note'
```bash
ls note*
```
output:<br>
<img width="451" height="122" alt="Screenshot from 2025-09-07 13-44-58" src="https://github.com/user-attachments/assets/d8e6cec6-0570-4784-8e13-f7aaf2b1df96" /><br>
Note: Wildcards are powerful tools for working with group files. THe most common wildcards are:-<br>
`*` : matches any number of characters.<br>
`?` : matches single character.<br>
`[abc]` : matches any one character listed in the [ ].

# Basic file operations
## 1)copy
- cp command is used to copy the files and directorties to another file or directory.
  ```bash
  cp hello.txt hello_copy.txt
  ```
- we can also copy all the .txt files or .png files to a drectory by using wildcards like:
  ```bash
  cp *.jpg /home/user/document
  ```
## 2)move
- mv command is used for moving files and also renamming them.<br>
- Quiet similar t `cp` command in terms of flag and functionality<br>
  ```bash
  mv hello_copy.txt ..
  ```
  ● `..` means parent directory one level up.<br>
  ● for detailed explanation refer to the basic-commands repository<br>
## 3)remove 
- `rm` command is used to remove the files and directories.<br>
- now lets remove the file.txt we created before.<br>
```bash
rm file1.txt
```
-now lets remove a directory.<br>
```bash
rmdir directory_name
```

-we have some options we can use in the rm command.<br>
like<br>
```bash
rm -i file1.txt
```
-gives prompt on whether you want to actually remove the files or directories.<br>
```bash
rm -r directory
```
-removes all the subdirectories recursively.<br>
NOTE: be careful with this linux command because the deleted files don't go the bin.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Now finall we have to check whether the directories or the files are removed or not.<br>
to do that we don't have to go to our system Home we can check it in our terminal we are currently working on.<br>
just use the command `ls` to check whether the directory is deleted or not.<br>

# Using command Line shortcuts
● To make command line experience more efficient linux provides several helpful shortcuts.<br>
## up arrowkey(↑): 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; to recall the last commands you typed.<br>
## Tab completion:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; type `cat h` and then press Tab key.<br>
auto completes `cat hello.txt`
## ctrl+c:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; to interrupt running command<br>
Example:<br>
``` bash
tail -f /dev/null
```
here `tail` is used to display last part of the file.<br>
`-f` option mean follows.<br>
`/dev/null` specific file that discards all data written to it.(i.e., a blackhole).<br>
## ctrl+l:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; to clear the screen<br>
