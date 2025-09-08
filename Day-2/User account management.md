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
For the Secondary group creation → [Secondary Groups](#-creating-a-new-user)
