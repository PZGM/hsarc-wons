Upon logging in, we find one binary and one token file. While we can read the token, it appears to be encrypted.

Next, we attempt to pass some input to the binary to see if it can decrypt the token:

```
level09@SnowCrash:~$ ./level09 aaaaa
abcde
```

We immediately notice that the binary shifts each character by its index in the string. To decrypt the token,
We can write a simple script that reverses this process:
```
#include <stdio.h>
#include <unistd.h>

int main(int argc, char **argv)
{
    int i = 0;
    if (argc != 2)
        return (0);
    while (argv[1][i])
    {
	argv[1][i] -= i;
        i++;
    }
    printf("Password is : %s\n", argv[1]);
    return (1);
}
```
We run it and obtain the token:

```
level09@SnowCrash:~$ ./reverse_hash `cat token`
Password is: f3iji1ju5yuevaus41q1afiuq
```
Now we just have to connect as flag09 and launch getflag

```
Don't forget to launch getflag !
flag09@SnowCrash:~$ getflag
Check flag.Here is your token : s5cAJpM8ev6XHw998pRWG728z
```
