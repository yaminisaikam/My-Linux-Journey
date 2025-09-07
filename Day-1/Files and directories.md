# Creating Files and Directories
step1: lets create a new directory called 'linux_practice'<br>
```bash
    mkdir linux_practice
```
step2: move to the new directory we created
```bash
    cd linux_practice
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
<img width="537" height="91" alt="Screenshot from 2025-09-07 12-11-18" src="https://github.com/user-attachments/assets/1bd68e77-26c0-4312-9170-098319ab5cdd" />

#
