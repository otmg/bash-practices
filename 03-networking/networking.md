# Networking

# host
host command in Linux system is used for DNS (Domain Name System) lookup operations. In simple words, this command is used to find the IP address of a particular domain name or if you want to find out the domain name of a particular IP address the host command becomes handy. You can also find more specific details of a domain by specifying the corresponding option along with the domain name.
```
host [-aCdlriTWV] [-c class] [-N ndots] [-t type] [-W time]
     [-R number] [-m flag] hostname [server]
```
```bash
host geeksforgeeks.org
```

Reference: https://www.geeksforgeeks.org/host-command-in-linux-with-examples/

# ip
The ip command is a Linux net-tool for system and network administrators. IP stands for Internet Protocol and as the name suggests, the tool is used for configuring network interfaces.
```
Usage: ip [ OPTIONS ] OBJECT { COMMAND | help }
       ip [ -force ] -batch filename
where  OBJECT := { link | address | addrlabel | route | rule | neigh | ntable |
                   tunnel | tuntap | maddress | mroute | mrule | monitor | xfrm |
                   netns | l2tp | fou | macsec | tcp_metrics | token | netconf | ila |
                   vrf | sr | nexthop }
       OPTIONS := { -V[ersion] | -s[tatistics] | -d[etails] | -r[esolve] |
                    -h[uman-readable] | -iec | -j[son] | -p[retty] |
                    -f[amily] { inet | inet6 | mpls | bridge | link } |
                    -4 | -6 | -I | -D | -M | -B | -0 |
                    -l[oops] { maximum-addr-flush-attempts } | -br[ief] |
                    -o[neline] | -t[imestamp] | -ts[hort] | -b[atch] [filename] |
                    -rc[vbuf] [size] | -n[etns] name | -N[umeric] | -a[ll] |
                    -c[olor]}
```

```bash
ip addr
```

Reference: https://phoenixnap.com/kb/linux-ip-command-examples

# nmap
Nmap is a tool used for determining the hosts that are running and what services the hosts are running.

Reference: https://www.unixmen.com/10-practical-examples-linux-nmap-command/

# ping
The ping command is one of the most used tools for troubleshooting, testing, and diagnosing network connectivity issues.

Ping works by sending one or more ICMP (Internet Control Message Protocol) Echo Request packages to a specified destination IP on the network and waits for a reply. When the destination receives the package, it responds with an ICMP echo reply.
```bash
ping [OPTIONS] DESTINATION
```
```bash
ping google.com
```
Reference: https://linuxize.com/post/linux-ping-command/

# wget
Wget command is a Linux command line utility that helps us to download the files from the web. We can download the files from web servers using HTTP, HTTPS and FTP protocols. We can use wget in scripts and cronjobs.
```
wget [OPTION]... [URL]...
```

Reference: https://www.fastwebhost.in/blog/10-examples-of-linux-wget-command/

# curl
```bash
curl [options] [URL...]
```

```bash
curl http://site.{one, two, three}.com
```

Reference: https://www.geeksforgeeks.org/curl-command-in-linux-with-examples