To get files offline
Start the practice session
Open the gui desktop

In CTF VM open an ssh session to the active desktop
`ssh -i enpm809v-pwn.college hacker@dojo.pwn.college`
confirm path the target binary
secure copy the target binary to the local machine
`scp -i enpm809v-pwn.college hacker@dojo.pwn.college:/challenge/<target binary name> /home/roger-pilton/Documents/`
run binary and get to work
