In our home directory, we find a `.pcap` file, which contains packet data captured over a network. To analyze this file, we need to use Wireshark. However, before we can do that, we must download the file:

```
$:/Snowcrash# ~/level02/ressources # scp -P 4242 scp://level02@192.168.0.169/level02.pcap level02.pcap
level02.pcap    100% 8302    10.1MB/s   00:00
```

Current rights are insufficient to run level02.pcap with Wireshark, so let's give all users the right to read, write and execute.

```
$:/Snowcrash# ~/level02/ressources # ls -la level02.pcap
----r--r-- 1 snowcrash snowcrash 8302 Oct 19 01:18 level02.pcap
$:/Snowcrash# ~/level02/Ressources # chmod 777 level02.pcap
```

If you open the level02.pcap file, you will see a stream of packets, follow tcp stream and choose utf-8
```
..%..%..&..... ..#..'..$..&..... ..#..'..$.. .....#.....'........... .38400,38400....#.SodaCan:0....'..DISPLAY.SodaCan:0......xterm.........."........!........"..".....b........b....	B.
..............................1.......!.."......"......!..........."........"..".............	..
.....................
Linux 2.6.38-8-generic-pae (::ffff:10.1.1.2) (pts/10)

..wwwbugs login: l.le.ev.ve.el.lX.X
..
Password: ft_wandr...NDRel.L0L
.
..
Login incorrect
wwwbugs login:
```

# login = l
# password = ft_wandrNDRelL0L

```
level02@Snowcrash:~$ su flag02
Password:
Don't forget to launch getflag !
flag02@Snowcrash:~$ getflag
Check flag.Here is your token : kooda2puivaav1idi4f57q8iq
```