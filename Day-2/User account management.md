# User Account Management
## creating a new user
⦾ Creating a new user requires administrative privileges.<br>
⦾ We'll use sudo commands to gain privileges.<br>
⦾ basically, sudo mean "SuperUser-Do".<br>
⦾ superuser mean root user.<br>
⦾ Here in linux we have 2 groups:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1)Primary group<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2)Secondary group<br>
⦾ When you create new user with `adduser` command it will automatically create a primary group for that user.<br>
⦾ This is called User Private Group(UPG) Schema.<br>
⦾ We have two types of command to create user `adduser`(Highlevel one) and `useradd`(Lowlevel one).<br>
⦾ First let us see how to add user using `adduser` command.<br>
Now lets add a user named jack:<br>
```bash
sudo adduser jack
```
here The sample output will be like this and we were asked to enter the user details like name phone number we can just press ENTER on the keyboard.<br>
<img width="500" height="300" alt="Screenshot from 2025-09-08 15-23-14" src="https://github.com/user-attachments/assets/2167ff5e-438a-45e2-b802-79ced8bc939f" /><br>
Now we have to conform that the user is created.<br>
```bash
ls /home
id jack
```
here `id` command will show you jacks user ID(UID), primary Group ID(GID) and any other secondary Groups.<br>
<img width="506" height="93" alt="Screenshot from 2025-09-08 15-28-10" src="https://github.com/user-attachments/assets/615d0963-fe95-4aab-837c-2cbef92f74da" /><br>
And the Secondary group creation we discuss it after we lwearned how to create a group<br>
⦾ Next let us see how to add user using `useradd` command.<br>
```bash
sudo useradd joker
```
`useradd` command creates new user named `joker`<br>
⦾ To verify that the user was created, we will examine the `/etc/passwd` file.<br>
```bash
sudo grep -w 'joker' /etc/passwd
```
- `grep` is a command-line utility for searching plain-text data.<br>
- `-w` is a option that tells grep to match the whole word only.<br>
- `/etc/passwd` is a file that is like a phonebook for user accounts.<br>
The sample output will be like this:<br>
<img width="400" height="79" alt="Screenshot from 2025-09-08 16-19-14" src="https://github.com/user-attachments/assets/b0571026-df46-47b6-9e34-ab7dd5efc183" /><br>
Here in the sample output:<br>
- `x` is the password.It will not be visible so shown as `X`.<br>
- The first `5001` is userID and the next one groupId.<br>
- `/home/joker` is the home directory.<br>
- `/bin/sh` is the default shell.<br>
## creating a user with a home directory
- Let's create another user nammed `bob` and give them home directory.<br>
1) Run this command
   ```bash
   sudo useradd -m bob
   ```
  - `-m` creates a home directory for user.<br>
  - home directory mean personal folder where a user can store their files and settings.<br>
2) Let's verify home directory was created.<br>
   ```bash
      sudo ls -ld /home/bob
   ```
The sample output will be like this:<br>
<img width="506" height="115" alt="Screenshot from 2025-09-08 16-36-49" src="https://github.com/user-attachments/assets/f8dba4e2-04ef-44d4-afd1-9b275c6849b6" /><br>
- `d` directory<br>
- `rwxr-x---` shows who can read, write or execute in this directory.<br>
- 2 `bob` one is user and other is group owner.<br>
- `4096` is the size of the directory.<br>
## Setting a user Password
- lets set a password for `joker`.<br>
1)
```bash
sudo passwd joker
```
- you'll be asked to enter the password(keep an easy one for practice purpose):`password123`<br>
2) If successful you'll see a message saying <br>
`passwd: password updated successfully`.<br>
- The sample output will be like:<br>
<img width="726" height="139" alt="Screenshot from 2025-09-08 16-48-10" src="https://github.com/user-attachments/assets/3c47b82d-a6ee-4ee5-a115-4d30c5cd1c79" /><br>

- Behind the scenes, Linux stores enceyoted password in a secure file called `/etc/shadow`.<br>
## Modifying User Properties
- Linux allows us to change various settings for a user account after it's been created.<br>
- Lets change the `joker` home direcory.<br>
1)Run this command
```bash
sudo usermod -d /home/wayne joker
```
- `usermod` command is used to modify users account settings.<br>
- `-d` says it is a directory.
- `home/wayne` is new directory.<br>
2) Now lets verify
  ```bash
  sudo grep -w 'joker' /etc/passwd
  ```
  <img width="541" height="63" alt="Screenshot from 2025-09-08 16-56-13" src="https://github.com/user-attachments/assets/a9a98bf1-cad5-446c-8d64-1f5276f6486f" /><br>
