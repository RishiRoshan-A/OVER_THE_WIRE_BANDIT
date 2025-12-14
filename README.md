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









