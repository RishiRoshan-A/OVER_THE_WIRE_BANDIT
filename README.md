# OVER_THE_WIRE_BANDIT
Write-ups and solutions for OverTheWire Bandit wargame, focusing on Linux fundamentals, SSH, and basic security concepts.

# LEVEL 0:
In This Level We need to connect remotely to their server using their given credentials by ssh 

command : ssh bandit0@bandit.labs.overthewire.org -p 2220

-----------------------------------------------------------------------------------------------------------------------------------------------
# LEVEL 0 --> LEVEL 1:

After connecting usign ssh give the command: ls

there is a file called readme (which contains password for the next level ) to read it

command : cat readme 

flag : ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

------------------------------------------------------------------------------------------------------------------------------------------------
# LEVEL 1 --> LEVEL 2:

Using the Level 0 password we have to login into this level one

command: ssh bandit1@bandit.labs.overthewire.org -p 2220

in this if we give ls their is a file named - lets see how we can read a file with command : cat ./-

. --> current directory

/ --> path

- --> file name

flag : 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

------------------------------------------------------------------------------------------------------------------------------------------------
# LEVEL 2 --> LEVEL 3 :

The password for the next level is stored in a file called --spaces in this filename-- located in the home directory

command : ssh bandit2@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login to this level 

bandit2@bandit:~$ ls
--spaces in this filename--

to read this file  commad : cat ./--spaces in this filename--

. --> current directory

/ --> path

--spaces in this filename--  --> file_name

flag: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

------------------------------------------------------------------------------------------------------------------------------------------------
# LEVEL 3 --> LEVEL 4:

The password for the next level is stored in a hidden file in the inhere directory.

commad : ssh bandit3@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login 

commad : ls 

go to inhere folder and command : ls -la to list the hidden files  and to read the hidden file 

command: cat ...Hiding-From-You

flag : 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

------------------------------------------------------------------------------------------------------------------------------------------------
# LEVEL 4 --> LEVEL 5 : 

The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command

commad : ssh bandit4@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login 

command : ls

navigate to inhere folder  command : cd inhere

there are many files in this we have to find human-readable file 

by using the file command we can find what type of file it is 

bandit4@bandit:~/inhere$ file ./-file0*

./-file00: data
./-file01: OpenPGP Public Key
./-file02: OpenPGP Public Key
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data


therefore ./-file07 is a human readable file 

command : cat ./-file07 

flag : 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

------------------------------------------------------------------------------------------------------------------------------------------------

# LEVEL 5 --> LEVEL 6 :

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable
1033 bytes in size
not executable

command : ssh bandit5@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login 

go to inhere folder enter the command to find the file mentioned in the question

bandit5@bandit:~/inhere$ find . -type f -size 1033c -readable ! -executable
./maybehere07/.file2

now cat the file to read the flag 

bandit5@bandit:~/inhere$ cat ./maybehere07/.file2

flag : HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

------------------------------------------------------------------------------------------------

# LEVEL 6 --> LEVEL 7 : 

The password for the next level is stored somewhere on the server and has all of the following properties:

owned by user bandit7
owned by group bandit6
33 bytes in size

command : ssh bandit6@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login

navigate to root directory  command : cat /

now lets search for the file in the server

command : bandit6@bandit:/$ find -size 33c -user bandit7 -group bandit6 -type f 2>/dev/null

./var/lib/dpkg/info/bandit7.password

now lets cat the contents of the file 

command : cat ./var/lib/dpkg/info/bandit7.password

flag : morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

------------------------------------------------------------------------------------------------

# LEVEL 7 --> LEVEL 8 : 

The password for the next level is stored in the file data.txt next to the word millionth

command : ssh bandit7@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login

command : cat data.txt | grep millionth

flag : dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

------------------------------------------------------------------------------------------------

# LEVEL 8 --> LEVEL 9 :

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

command : ssh bandit8@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login

command : sort data.txt | uniq -u 

sort will arrange the file in alpahbetical order and uniq will remove the duplicates

flag : 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

------------------------------------------------------------------------------------------------

# LEVEL 9 --> LEVEL 10 : 

The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

command : ssh bandit9@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login

since the data.txt is in a non human format we use strings to convert it into human readable format and grep =  to find the flag

command : strings data.txt | grep =

flag : FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

------------------------------------------------------------------------------------------------

# LEVEL 10 --> LEVEL 11 

The password for the next level is stored in the file data.txt, which contains base64 encoded data

command : ssh bandit10@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login

When we cat the data.txt it is in the base64 encoded format : VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==

we want to decode this to find the flag 

command : cat data.txt | base64 -d

flag : dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

------------------------------------------------------------------------------------------------

# LEVEL 11 --> LEVEL 12

The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

command : ssh bandit11@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login

cat data.txt to see the contents inside the file : Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4   , looks like it is encoded with rot13 lets decode it 

use online rot13 decoder to find the flag

flag : 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

------------------------------------------------------------------------------------------------

# LEVEL 12 --> LEVEL 13 

The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

command :  ssh bandit12@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login

In this challenge move the file to temp directory in order to edit or modify the file 

change the file hexadump to original file command : xxd -r data.txt > data.bin

using file command check the file type if it is showing zip file command : gunzip file_name

else showing Bzip2 file command : bunzip2 file_name

else showing archive file command : tar -xf file_name

first rename the file to correct extension and then apply the above commands repeatdely until you find ASCII text file 

flag : FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
------------------------------------------------------------------------------------------------

# LEVEL 13 --> LEVEL 14

Level Goal

The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Look at the commands that logged you into previous bandit levels, and find out how to use the key for this level.

Command to login : ssh bandit13@bandit.labs.overthewire.org -p 2220

Command : ls --> to see the list of files 

We can see a file named sshkey.private with this we can login into level 14 

use command : scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private . 

to get the key to our system

Command : chmod 600 sshkey.private

Command :  ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org

Command : cat /etc/bandit_pass/bandit14  to see the flag

Flag : MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

-------------------------------------------------------------------------------------------------------------

# LEVEL 14 --> LEVEL 15 

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

Use telnet to connect to port 30000 on localhost 

command : telnet localhost 30000

enter the previous flag and we got the flag

Flag : 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

-------------------------------------------------------------------------------------------------------------

# LEVEL 15 --> LEVEL 16

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage

commad to login : ssh bandit15@bandit.labs.overthewire.org -p 2220

use the previous flag as password

use command : openssl s_client -connect localhost:30001 -ign_eof

openssl is a tool which is used for secured communication

s_client --> secure client means use ssl encryption 

-connect --> conecting to the localhost on port 30001

-ign_eof --> dont stop the connection even if i hit enter or stop typing 

run this command and enter the previous flag and we will get the password

flag : kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

-------------------------------------------------------------------------------------------------------------

# LEVEL 16 --> LEVEL 17 

The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.

command to login : ssh bandit16@bandit.labs.overthewire.org -p 2220

enter the previous flag as password

Lets perform an nmap scan to find which ports are giving us a response

command : nmap -A localhost -p 31000-32000

we found that port 31790 , gave an output that Wrong! Please enter the correct current password

Lets connect to that port using openssl

command : openssl s_client -connect localhost:31790 -ign_eof

execute the command and enter the previous flag  

and we have got a rsa key , copy the key and store it in a file to login into next level 

-------------------------------------------------------------------------------------------------------------

# LEVEL 17 --> LEVEL 18

There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19

command to login : ssh bandit17@bandit.labs.overthewire.org -p 2220 -i bandit17  

now if we give command ls , we can see two files 1) passwords.old 2) passwords.new and we have to find the line that has been changed between passwords.old and passwords.new

so we can use diff command to find it

command : diff passwords.old passwords.new

flag : x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO

-------------------------------------------------------------------------------------------------------------

# LEVEL 18 --> LEVEL 19

The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

In this challenge we cant normally login into ssh since someone has modified .bashrc to log you out when you log in with SSH.

command : ssh -T bandit18@bandit.labs.overthewire.org -p 2220 

and enter the previous flag as the password 

-T --> tells dont spawn a interactive terminal , then .bashrc does not executes but we keeps logined in and we dont get a interactive shell

type command : ls

there is a file called readme , lets cat this file

command : cat readme

flag : cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8

-------------------------------------------------------------------------------------------------------------

# LEVEL 19 --> LEVEL 20

To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

command : ssh  bandit19@bandit.labs.overthewire.org -p 2220 

and enter the previous flag as the password 

if we type ls we see a file called bandit20-do

lets execute it command : ./bandit20-do

bandit19@bandit:~$ ./bandit20-do 
Run a command as another user.
  Example: ./bandit20-do whoami

  so using this we can read /etc/bandit_pass

  command :  ./bandit20-do cat /etc/bandit_pass/bandit20

now we got the flag

flag : 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO

-------------------------------------------------------------------------------------------------------------

# LEVEL 20 --> LEVEL 21

There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

NOTE: Try connecting to your own network daemon to see if it works as you think

command to login : ssh  bandit20@bandit.labs.overthewire.org -p 2220 

and enter the previous flag as the password 


bandit20@bandit:~$ ls
suconnect
bandit20@bandit:~$ ./suconnect
Usage: ./suconnect <portnumber>
This program will connect to the given port on localhost using TCP. If it receives the correct password from the other side, the next password is transmitted back.
bandit20@bandit:~$ 

 Lets open a another terminal emulator and logged into the bandit20 account again.
In the second terminal, lets run nc -nlvp 12345 and enter current level's password when prompted.
The -nlvp option is a combination of four options: -n means "Do not resolce DNS, -l put Netcat in listen mode, -v enables verbose ouput, and -p specifies the port number.

Now lets run ./suconnect 12345

bandit20@bandit:~$ ./suconnect 12345
Read: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
Password matches, sending next password

Flag : EeoULMCra2q0dSkYj561DX7s1CpBuOBt

-------------------------------------------------------------------------------------------------------------

# LEVEL 21 --> LEVEL 22

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.


command to login : ssh  bandit21@bandit.labs.overthewire.org -p 2220 

and enter the previous flag as the password 

First we are reading the /etc/cron.d file in which 

bandit21@bandit:/$ cat /etc/cron.d/cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null

we got an another file , lets cat that and we got an another file which contains the flag 

bandit21@bandit:/$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
bandit21@bandit:/$ cat  /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q

flag : tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q

-------------------------------------------------------------------------------------------------------------

# LEVEL 22 --> LEVEL 23 

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.

command to login : ssh  bandit21@bandit.labs.overthewire.org -p 2220 

and enter the previous flag as the password 

lets read the file /etc/cron.d similar where it shows another script , lets cat that and we got a script 

lets create a folder in tmp and make a file in it and copy the script to it 

bandit22@bandit:~$ cat  /usr/bin/cronjob_bandit23.sh
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
bandit22@bandit:~$ cat /tmp/$mytarget
cat: /tmp/: Permission denied
bandit22@bandit:~$ mkdir /tmp/rr
bandit22@bandit:~$ cd /tmp/rr
bandit22@bandit:/tmp/rr$ nano rr.sh

bandit22@bandit:/tmp/rr$ chmod 777 rr.sh 
bandit22@bandit:/tmp/rr$ ./rr.sh 
Copying passwordfile /etc/bandit_pass/bandit22 to /tmp/8169b67bd894ddbb4412f91573b38db3
bandit22@bandit:/tmp/rr$ cat /tmp/8169b67bd894ddbb4412f91573b38db3
OZf11i0IjMVN551jX3CmStKLYqjk54Ga

flag : OZf11i0IjMVN551jX3CmStKLYqjk54Ga

-------------------------------------------------------------------------------------------------------------

# LEVEL 23 --> LEVEL 24

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!



 




