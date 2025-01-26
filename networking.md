# SOC Analyst Industrial Training - Basic Networking

## 🗓️ Week 1 (Day 1-5): Foundation Building

### Network Fundamentals & Architecture

We began by establishing a strong foundation in networking essentials. I learned about the OSI model and TCP/IP stack, understanding how data flows through different network layers. IPv4 addressing and subnetting became second nature through extensive practice.

**Key Commands Practiced:**

```bash
ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute
       valid_lft forever preferred_lft forever
2: ens33: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:0c:29:ec:33:1e brd ff:ff:ff:ff:ff:ff
    altname enp2s1
    inet 192.168.17.132/24 brd 192.168.17.255 scope global dynamic noprefixroute ens33
       valid_lft 1709sec preferred_lft 1709sec
    inet6 fe80::20c:29ff:feec:331e/64 scope link
       valid_lft forever preferred_lft forever
```

```bash
netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.17.2    0.0.0.0         UG        0 0          0 ens33
192.168.17.0    0.0.0.0         255.255.255.0   U         0 0          0 ens33
```

```bash
ipcalc 192.168.17.132
Address:   192.168.17.132       11000000.10101000.00010001. 10000100
Netmask:   255.255.255.0 = 24   11111111.11111111.11111111. 00000000
Wildcard:  0.0.0.255            00000000.00000000.00000000. 11111111
=>
Network:   192.168.17.0/24      11000000.10101000.00010001. 00000000
HostMin:   192.168.17.1         11000000.10101000.00010001. 00000001
HostMax:   192.168.17.254       11000000.10101000.00010001. 11111110
Broadcast: 192.168.17.255       11000000.10101000.00010001. 11111111
Hosts/Net: 254                   Class C, Private Internet
```

### Routing & Switching Concepts

I explored how packets traverse networks through routing protocols and learned about ARP for MAC address resolution. Understanding VLANs and network segmentation proved crucial for security analysis.

**Practical Exercises:**

```bash
arp -a
_gateway (192.168.17.2) at 00:50:56:f7:03:9b [ether] on ens33

ip route show
default via 192.168.17.2 dev ens33 proto dhcp src 192.168.17.132 metric 100
192.168.17.0/24 dev ens33 proto kernel scope link src 192.168.17.132 metric 100
```

```bash
traceroute -n 8.8.8.8
1  192.168.56.1  1.234 ms  1.123 ms  0.987 ms
2  10.0.2.2      5.678 ms  5.432 ms  5.234 ms
```

### DNS and DHCP Services

DNS resolution and DHCP processes were thoroughly examined. I learned to identify different DNS record types and analyze DNS queries for potential security threats.

**Command Examples:**

```bash
dig google.com A

; <<>> DiG 9.18.30-0ubuntu0.24.04.2-Ubuntu <<>> google.com A
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 21414
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		5	IN	A	142.250.195.14

;; Query time: 49 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Wed Jan 15 15:27:45 IST 2025
;; MSG SIZE  rcvd: 55
```

```bash
nslookup -type=MX gmail.com
Server:		127.0.0.53
Address:	127.0.0.53#53

Non-authoritative answer:
gmail.com	mail exchanger = 5 gmail-smtp-in.l.google.com.
gmail.com	mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
gmail.com	mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
gmail.com	mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
gmail.com	mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.

Authoritative answers can be found from:
```

```bash
sudo tcpdump -nn port 443 -c 5
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on ens33, link-type EN10MB (Ethernet), snapshot length 262144 bytes
15:32:20.166469 IP 192.168.17.132.37190 > 34.160.144.191.443: Flags [S], seq 2408349805, win 64240, options [mss 1460,sackOK,TS val 3875993476 ecr 0,nop,wscale 7], length 0
15:32:20.181149 IP 34.160.144.191.443 > 192.168.17.132.37190: Flags [S.], seq 877277409, ack 2408349806, win 64240, options [mss 1460], length 0
15:32:20.181234 IP 192.168.17.132.37190 > 34.160.144.191.443: Flags [.], ack 1, win 64240, length 0
15:32:20.182055 IP 192.168.17.132.37190 > 34.160.144.191.443: Flags [P.], seq 1:221, ack 1, win 64240, length 220
15:32:20.182639 IP 34.160.144.191.443 > 192.168.17.132.37190: Flags [.], ack 221, win 64240, length 0
5 packets captured
5 packets received by filter
0 packets dropped by kernel
```

### Network Scanning Techniques

We practiced various scanning methods using nmap, understanding different scan types and their purposes. I learned to interpret scan results and correlate them with potential security threats.

**Scanning Commands:**

```bash
sudo nmap -sS 192.168.17.132
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-01-16 12:01 IST
Nmap scan report for safeaeon-ubuntu (192.168.17.132)
Host is up (0.0000070s latency).
All 1000 scanned ports on safeaeon-ubuntu (192.168.17.132) are in ignored states.
Not shown: 1000 closed tcp ports (reset)

Nmap done: 1 IP address (1 host up) scanned in 0.20 seconds
```

```bash
sudo nmap -sU -p53,123,161 192.168.17.132
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-05-16 13:10 IST
Nmap scan report for 192.168.17.132
Host is up (0.000072s latency).

PORT    STATE  SERVICE
53/udp  closed domain
123/udp closed ntp
161/udp closed snmp

Nmap done: 1 IP address (1 host up) scanned in 8.42 seconds
```

### Firewall Configuration & Security

I gained hands-on experience with iptables and UFW, learning to create rules for allowing and blocking traffic. Understanding stateful inspection and rule ordering was emphasized.

**Firewall Commands:**

```bash
sudo iptables -L -n
Output: Chain INPUT (policy ACCEPT)
         target     prot opt source               destination
         ACCEPT     tcp  --  192.168.17.0/24      0.0.0.0/0           tcp dpt:22

sudo ufw status numbered
Output: Status: active
         [1] 22/tcp                     ALLOW IN    192.168.17.0/24
         [2] 80/tcp                     ALLOW IN    Anywhere

iptables -I INPUT -s 192.168.17.200 -j DROP
Applied rule to block specific IP address
```

---

## 🗓️ Week 2 (Day 6-10): Advanced Analysis & Security

### Packet Analysis with Wireshark

Packet inspection became a core skill as I learned to use Wireshark effectively. Understanding protocol dissection and creating custom filters proved essential for SOC work.
PCAP (Packet Capture) files contain captured network traffic that serves as digital evidence of network events. We analyzed various PCAP files to understand traffic patterns, identify network issues, and detect security incidents. Through systematic analysis, we learned to follow TCP streams, examine protocol interactions, and spot anomalies like unusual DNS queries, suspicious port usage, or unexpected traffic flows. The captured packets revealed the story of network communications - showing not just what happened, but the sequence of events, timing, and protocol-level details that are crucial for incident response. PCAP analysis proved invaluable for troubleshooting network performance issues, validating security controls, and conducting post-incident forensic investigations. We practiced using display filters to isolate specific traffic patterns and statistics to quantify network behavior, transforming raw packet data into actionable security intelligence.

**Wireshark Filters Applied:**

```text
tcp.port == 80 and http.request.method == "GET"
# Captured HTTP GET requests

dns.qry.name contains "malware" or dns.qry.name contains "C2"
# Filtered suspicious DNS queries

tcp.flags.syn == 1 and tcp.flags.ack == 0
# Identified TCP SYN scans
```

**tcpdump Examples:**

```bash
tcpdump -nn -i any -A port 80 and host 192.168.56.101
sudo tcpdump -nn -i any -A port 443 and host 192.168.17.132
tcpdump: data link type LINUX_SLL2
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on any, link-type LINUX_SLL2 (Linux cooked v2), snapshot length 262144 bytes
15:47:08.915764 ens33 Out IP 192.168.17.132.40172 > 34.120.237.76.443: Flags [S], seq 956546298, win 64240, options [mss 1460,sackOK,TS val 720851001 ecr 0,nop,wscale 7], length 0
E..<_.@.@......."x.L....9......................
*.P9........
15:47:08.937372 ens33 In  IP 34.120.237.76.443 > 192.168.17.132.40172: Flags [S.], seq 1171914945, ack 956546299, win 64240, options [mss 1460], length 0
E..,3.....%S"x.L........E...9...`.............
15:47:08.937435 ens33 Out IP 192.168.17.132.40172 > 34.120.237.76.443: Flags [.], ack 1, win 64240, length 0
E..(_.@.@......."x.L....9...E...P.......
15:47:08.939436 ens33 Out IP 192.168.17.132.40172 > 34.120.237.76.443: Flags [P.], seq 1:2523, ack 1, win 64240, length 2522
E.
._.@.@......."x.L....9...E...P..........	...	.......5. i........."nR.?."KM.y0.	l +.....".^!..>..5."...	.-x.I....9.".......+./.....,.0.
.
.
.
.
49 packets captured
49 packets received by filter
0 packets dropped by kernel
```

### VPN and Encrypted Communications

I explored VPN protocols, focusing on the working of GRE tunnel and IPSec protocol.
[Virtual Private Network (VPN) - Deep Dive](https://www.youtube.com/watch?v=7WhEk7Ga-Bw)

### Log Analysis and Correlation

Advanced log parsing techniques using grep, awk, and sed were mastered. I learned to identify patterns indicative of attacks and create automated analysis scripts.

**Log Analysis Commands:**

```bash
grep "Failed password" /var/log/auth.log | wc -l
0

sudo dmesg | grep firefox

[    8.996880] systemd[1]: Mounting snap-firefox-6103.mount - Mount unit for firefox, revision 6103...
[    9.009957] systemd[1]: Mounting snap-firefox-6159.mount - Mount unit for firefox, revision 6159...
[    9.099635] systemd[1]: Mounted snap-firefox-6103.mount - Mount unit for firefox, revision 6103.
[    9.099955] systemd[1]: Mounted snap-firefox-6159.mount - Mount unit for firefox, revision 6159.
[ 1246.004026] audit: type=1400 audit(1747389735.903:188): apparmor="DENIED" operation="open" class="file" profile="snap-update-ns.firefox" name="/usr/local/share/" pid=5293 comm="5" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[ 1246.088102] audit: type=1400 audit(1747389735.988:189): apparmor="DENIED" operation="open" class="file" profile="snap-update-ns.firefox" name="/proc/5301/maps" pid=5301 comm="5" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 1247.820978] audit: type=1400 audit(1747389737.720:190): apparmor="DENIED" operation="mknod" class="file" profile="snap.firefox.firefox" name="/home/berserk/.local/share/fonts/.uuid.TMP-ruKfxs" pid=5172 comm=5B70616E676F5D204663496E6974 requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
```

### Incident Response and Forensics

The final phase focused on practical incident response scenarios. I learned to correlate network evidence, contain threats, and document findings appropriately.

**Network Forensics Commands:**

```bash
sudo netstat -tupln | grep ":22"
tcp6       0      0 :::22                   :::*                    LISTEN      1/init

sudo ss -tuln | grep :22
tcp   LISTEN 0      4096               *:22               *:*

sudo lsof -i :22 -n
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
systemd    1 root   94u  IPv6 283933      0t0  TCP *:ssh (LISTEN)
sshd    9055 root    3u  IPv6 283933      0t0  TCP *:ssh (LISTEN)

```

**Process and Connection Analysis:**

```bash
# Analyzed established connections by remote IP
sudo netstat -antup | grep ESTABLISHED | awk '{print $5}' | cut -d: -f1 | sort | uniq -c
      1 142.250.192.142
      1 192.168.17.254
      1 34.107.243.93

# Listed active network connections
sudo lsof -i | grep -E "(ESTABLISHED|LISTEN)" | head -20

systemd      1            root   94u  IPv6 283933      0t0  TCP *:ssh (LISTEN)
systemd-r  843 systemd-resolve   15u  IPv4  18915      0t0  TCP _localdnsstub:domain (LISTEN)
systemd-r  843 systemd-resolve   17u  IPv4  18917      0t0  TCP _localdnsproxy:domain (LISTEN)
cupsd     1687            root    6u  IPv6  26750      0t0  TCP ip6-localhost:ipp (LISTEN)
cupsd     1687            root    7u  IPv4  26751      0t0  TCP localhost:ipp (LISTEN)
firefox   5172         berserk   80u  IPv4 285841      0t0  TCP safeaeon-ubuntu:57550->203.137.36.34.bc.googleusercontent.com:https (ESTABLISHED)
firefox   5172         berserk   96u  IPv4  51930      0t0  TCP safeaeon-ubuntu:41294->93.243.107.34.bc.googleusercontent.com:https (ESTABLISHED)
firefox   5172         berserk   97u  IPv4 287822      0t0  TCP safeaeon-ubuntu:44160->217.138.110.34.bc.googleusercontent.com:https (ESTABLISHED)
sshd      9055            root    3u  IPv6 283933      0t0  TCP *:ssh (LISTEN)

```

---

## 📊 Summary:

Through this comprehensive training program, I developed proficiency in:

1. **Network Protocol Analysis**: Can now dissect packets and identify anomalies in network traffic
2. **Security Tool Proficiency**: Comfortable with nmap, Wireshark, iptables, and log analysis tools
3. **Incident Detection**: Able to recognize attack patterns and correlate events across multiple log sources
4. **Practical Skills**: Hands-on experience with real network scenarios and security challenges
