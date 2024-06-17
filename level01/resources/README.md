Our home directory is also empty in this level.

In the absence of specific information, we can refer to the /etc/passwd file, as it contains valuable details about users and groups.

In this instance, we observe that the /etc/passwd file contains a hashed password for the user flag01.

```
level01@SnowCrash:~$ cat /etc/passwd
...
flag00:x:3000:3000::/home/flag/flag00:/bin/bash
flag01:42hDRfypTqqnw:3001:3001::/home/flag/flag01:/bin/bash
flag02:x:3002:3002::/home/flag/flag02:/bin/bash
...
```
get it
```
scp -P 4242 level01@[ip]:/etc/passwd .
```
john the ripper out of it (a famous password decryption tool) :
```
john passwd
```

you will get an output like this:
```
$:/Snowcrash# john level01/Ressources/passwd
Loaded 1 password hash (descrypt, traditional crypt(3) [DES 128/128 SSE2-16])
Press 'q' or Ctrl-C to abort, almost any other key for status
abcdefg          (flag01)
1g 0:00:00:00 100% 2/3 33.33g/s 46433p/s 46433c/s 46433C/s raquel..bigman
Use the "--show" option to display all of the cracked passwords reliably
Session completed
```

you can see the password for the flag01 as `abcdefg`

now login as flag01 and get the flag with getflag
and run getflag:
```
flag01@SnowCrash:~$ getflag
Check flag.Here is your token : f2av5il02puano7naaf6adaaf
```