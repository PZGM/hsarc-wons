In our home directory, we find a `.pcap` file, which contains packet data captured over a network. To analyze this file, we need to use Wireshark. However, before we can do that, we must download the file:

```
$:/Snowcrash# ~/level02/ressources # scp -P 4242 scp://level02@[ip]/level02.pcap level02.pcap
level02.pcap    100% 8302    10.1MB/s   00:00
```

Our current permissions are insufficient to run level02.pcap with Wireshark. To resolve this, let's grant all users read, write, and execute permissions.

```
$:/Snowcrash# ~/level02/ressources # ls -la level02.pcap
----r--r-- 1 snowcrash snowcrash 8302 Oct 19 01:18 level02.pcap
$:/Snowcrash# ~/level02/Ressources # chmod 777 level02.pcap
```

If you open the level02.pcap file, you will see a stream of packets, follow tcp stream and choose ASCII you'll find a line with:
```
Password: ft_wandr...NDRel.L0L
```

We use hexdump to analyze the token file and identify the problematic characters shown as a dot.
We notice that 7F represents the deletion key. By removing the correct 7F entries, we uncover the decrypted token: ft_waNDReL0L.

```
level02@Snowcrash:~$ su flag02
Password:
Don't forget to launch getflag !
flag02@Snowcrash:~$ getflag
Check flag.Here is your token : kooda2puivaav1idi4f57q8iq
```
