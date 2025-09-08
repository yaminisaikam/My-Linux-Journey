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
## Changing user Shell
- Another important setting we can modify is the users default shell.<br>
- By default,the user `joker` is using `/bin/sh` as their shell.
1) How to change Shell:<br>
```bash
sudo usermod -s /bin/bash joker
```
- `-s` is a option that speciifies the new login shell for the user.<br>
2) To verify the changes<br>
```bash
sudo grep -w 'joker' /etc/password
```
<img width="433" height="118" alt="Screenshot from 2025-09-08 20-32-30" src="https://github.com/user-attachments/assets/29c9df4d-4224-4f80-af30-004f04864111" /><br>
# Adding user to a Group
- In Linux, we use groups to organize users and manage permissions.<br>
- One important group is `sudo` group, which gives users administrative privileges.<br>
- Lets add joker to the sudo group.<br>
⭐ Remember: Adding a user to the sudo group gives them significant power over the system, so this should be done cautiously and only when necessary.<br>
1) Adding `joker` to the `sudo` group.<br>
```bash
sudo usermod -aG sudo joker
```
- `-aG` append to a group, without removing from other groups.<br>
- `sudo` group we are adding user to.<br>
2) Verify the change<br>
```bash
groups joker
```
- you should see `sudo` listed among the joker's groups.<br>
<img width="433" height="118" alt="Screenshot from 2025-09-08 20-45-31" src="https://github.com/user-attachments/assets/fe2a604a-3410-4e42-b98e-277b9ec3fdc3" /><br>
3) Switch to the joker user and try a command that requires sudo privileges.<br>
```bash
su - joker
```
- It asks for password : `password123`(which we kept while creating the user `joker`)<br>
4) Now use this command to chech the user has the sudo privileges:<br>
```bash
sudo cat /etc/shadow
```
`/etc/shadow` is a file which is usually only accessible to root(i.e., sudo user)<br>
5) After you are done, type `exit` to return to original user account.<br>
## Locking and unlocking User Accounts
- some times, you might need to trmporarily disable a user account without deletinf it.<br>
1) Lock the `joker` account<br>
```bash
sudo passwd -l joker
```
- `-l` locks the password.<br>
- the sample output would be like this.
<img width="423" height="59" alt="Screenshot from 2025-09-08 20-59-26" src="https://github.com/user-attachments/assets/64e3118e-66b0-4225-9a63-ab5b62996871" /><br>
2) Try switching to the joker user<br>
```bash
su - joker
```
- then enter the password `password123`.<br>
<img width="423" height="75" alt="Screenshot from 2025-09-08 21-01-46" src="https://github.com/user-attachments/assets/afbecd09-5ce5-485a-83a5-dee2e8147174" /><br>
3) Unlock the user account <br>
```bash
sudo passwd -u joker
```
- `-u` option unlocks the password.<br>
4) Try switching to the `joker` user again.<br>
```bash
su - joker
```
5) Type `exit`<br>
## Deleting a user
- to delete a user we use `userdel` command.<br>
1) Now deleter the `bob` and their home directory.<br>
```bash
sudo userdel -r bob
```
- `userdel` to delete user account.<br>
- `-r` option removes the user home directory and mail spool.<br>
2) Verify that thr user has been deleted.<br>
  ```bash
  sudo grep -w 'bob' /etc/passwd
  sudo ls -ld /home/bob
  ```
  <img width="516" height="110" alt="Screenshot from 2025-09-08 21-11-21" src="https://github.com/user-attachments/assets/3f8124fe-1e45-4990-b3a1-cde6a0462431" /><br>
# View current user information
- In Linux, each user has a unique username.<br>
- Lets start by identifying which user were currently loged in as:<br>
```bash
whoami
```
`whoami` is a simple too that displays the username of current user.
## Explore user groups
- In Linux, user groups are a way to organize miltiple users for permission management.<br>
- Each user has a primary group and can belong to multiple secondary groups.<br>
  1)
  ```bash
  id user
  ```
  2) Now lets view all groups on the system<br>
  ```bash
  cat /etc/group | sort
  ```
  - `/etc/group` is where groups information is stored.<br>
  - `| sort` sorts all the groups alphabetically.<br>
  3) To see only groups releated to only your `user_name` use<br>
  ```bash
  cat /etc/group | grep -E 'user'
  ```
  ## Creating a new group and add user to it
  - lets create new group called `developers` and add our new user `jack` to it.<br>
  1)Adding group<br>
    ```bash
    sudo groupadd developers
    ```
  2)Add `jack`   (if `jack already existed no need to add`)<br>
  ```bash
  sudo useradd jack
  ```
  3)now add `jack` the group<br>
  ```bash
  sudo usermod -aG developers jack
  ```
  4) To verify jack added or not<br>
  ```bash
  groups jack
  ```
  - The sample output will be like this<br>
  <img width="524" height="135" alt="Screenshot from 2025-09-08 21-33-50" src="https://github.com/user-attachments/assets/6929d0bc-3481-4e55-8454-eb6e39e2c99d" /><br>
