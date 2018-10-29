# Command Line Magic

#### 1.tcpdump 仅显示IP+端口+[标志]
```
tcpdump  -nnn -t -s0 -l -i $EthX host IP1 | cut -d "," -f 1
tcpdump  -nnn -t -s0 -l -i $EthX host IP1 | cut -d "." -f 1,2,3,4,5,6,7,8

# output
IP 192.168.x.xxx.41282 > 192.168.x.1.80: Flags [S]
IP 192.168.x.1.80 > 192.168.x.xxx.41282: Flags [S.]
IP 192.168.x.xxx.41282 > 192.168.x.1.80: Flags [.]
IP 192.168.x.xxx.41282 > 192.168.x.1.80: Flags [F.]
```

#### 2.Netfilter Debugging
```
iptables -t raw -A OUTPUT -p icmp -j TRACE
iptables -t nat -A OUTPUT -d 10.8.0.0/24 -j DNAT --to 192.168.8.1

iptables -t raw -vnL --line
iptables -t nat -vnL --line

ping -c1 10.8.0.10
    
tail -F /var/log/kern.log

Reference:
http://www.strlen.de/talks/nfdebug.pdf
http://inai.de/images/nf-packet-flow.svg
```
![](https://www.zer0d0y.info/images/Tips-and-Hacks-for-Everyday-Life-p1.png)

#### 3.命令提示符显示IP地址
```
PS1="\[\033[01;31m\]\u@"192.168.X.X" \w #\[\033[00m\] ";
```
