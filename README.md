# Command Line Magic

#### 1.tcpdump 仅显示IP+端口+[标志]
```
tcpdump  -nnn -t -s0 -l -i $EthX host IP1 | cut -d "," -f 1
tcpdump  -nnn -t -s0 -l -i $EthX host IP1 | cut -d "." -f 1,2,3,4,5,6,7,8
```
