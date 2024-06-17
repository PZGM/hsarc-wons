Our home directory is empty so we look for file belonging to flag00 since we need to connect to it

```
level00@SnowCrash:~$ find / -user flag00 2>/dev/null
/usr/sbin/john
/rofs/usr/sbin/john
```

It's the same file, when we display the content we get a seemingly plain text password:
```
level00@SnowCrash:~$ cat /usr/sbin/john
cdiiddwpgswtgt
```

This password does not work for flag00 it might be encrypted
By going to dcode.fr we tried to find what type of encryption it might be with :
https://www.dcode.fr/identification-chiffrement

by trying the differente encryption we find that the resulte of the caesar encryption is the most likely:
https://www.dcode.fr/chiffre-cesar
the result of `cdiiddwpgswtgt` being `nottohardhere` with a 15 letter rotation

so we log as flag00:
```
su flag00
password => nottoohardhere
```

and run getflag:
```
flag00@SnowCrash:~$ getflag
Check flag.Here is your token : x24ti5gi3x0ol2eh4esiuxias
```