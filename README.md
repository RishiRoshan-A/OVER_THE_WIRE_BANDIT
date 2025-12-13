# OVER_THE_WIRE_BANDIT
Write-ups and solutions for OverTheWire Bandit wargame, focusing on Linux fundamentals, SSH, and basic security concepts.

# LEVEL 0:
In This Level We need to connect remotely to their server using their given credentials by ssh 
command : ssh bandit0@bandit.labs.overthewire.org -p 2220
after connecting give ls to list the files and cat to read the files 
flag : ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

# LEVEL 0 --> LEVEL 1:
Using the Level 0 password we have to login into this level one 
command: ssh bandit1@bandit.labs.overthewire.org -p 2220
in this if we give ls their is a file named - lets see how we can read a file with special character
command: cat ./-
. --> current directory
/ --> path
- --> file name 
flag:263JGJPfgU6LtdEvgfWU1XP5yac29mFx

