# ping

ping 命令用于检查网络上两台主机之间的连通性。

它使用 **互联网控制消息协议**（Internet Control Message Protcocol, ICMP）中的 echo 分组。当向某台主机发送 echo 分组时，如果分组送达，将会返回一条回应。

## 检查某台主机是否可以到达

```
$ ping ADDRESS
```

ADDRESS可以是：

- 主机名
- 域名
- IP地址

## 往返时间

ping 命令可以获得两台主机之间的往返时间（Round Trip Time，RTT），它代表分组从源主机到目的主机一来一回的时间（单位毫秒）。

```
$ ping baidu.com
PING baidu.com (123.125.115.110): 56 data bytes
64 bytes from 123.125.115.110: icmp_seq=0 ttl=51 time=47.460 ms
64 bytes from 123.125.115.110: icmp_seq=1 ttl=51 time=47.768 ms
64 bytes from 123.125.115.110: icmp_seq=2 ttl=51 time=64.368 ms
^C
--- baidu.com ping statistics ---
3 packets transmitted, 3 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 47.460/53.199/64.368/7.899 ms
```

- 最小 RTT：47.460ms
- 平均 RTT：53.199ms
- 最大 RTT：64.368ms
- 平均差：7.899ms

## 限制发送的分组数量

```
-c COUNT
```

```
$ ping baidu.com -c 2
PING baidu.com (123.125.115.110): 56 data bytes
64 bytes from 123.125.115.110: icmp_seq=0 ttl=51 time=48.835 ms
64 bytes from 123.125.115.110: icmp_seq=1 ttl=51 time=60.618 ms

--- baidu.com ping statistics ---
2 packets transmitted, 2 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 48.835/54.727/60.618/5.892 ms
```

## ping 命令的返回状态

- 返回0：执行状态顺利，目的主机可到达
- 返回非0：目的主机不可到达

```
#!/bin/bash
#获取ping返回状态
ping baidu.com -c 2

if [ $? -eq 0 ];
then
	echo Success
else
	echo Failure
fi
```



