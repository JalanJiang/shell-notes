# lsof

- 列出端口
- 列出端口上所运行的服务

## 列出端口上运行的服务详情

```
$ lsof -i
COMMAND     PID USER   FD   TYPE             DEVICE SIZE/OFF NODE NAME
loginwind    99  jjy    8u  IPv4 0xec41920aa58efc09      0t0  UDP *:*
UserEvent   302  jjy    4u  IPv4 0xec41920aaa580379      0t0  UDP *:*
Mail        322  jjy    9u  IPv4 0xec41920ab4d92f21      0t0  TCP 172.16.23.66:49712->220.181.72.229:imaps (ESTABLISHED)
Mail        322  jjy   13u  IPv4 0xec41920ab4d92f21      0t0  TCP 172.16.23.66:49712->220.181.72.229:imaps (ESTABLISHED)
Mail        322  jjy   17u  IPv4 0xec41920ab4b9bc61      0t0  TCP 172.16.23.66:49717->220.181.72.229:imaps (ESTABLISHED)
```
`172.16.23.66:49712->220.181.72.229:imaps` 中：

- `172.16.23.66:49712` 对应本地主机
- `220.181.72.229:imaps` 对应远程主机

## 列出本地主机当前的开放端口

```
$ lsof -i | grep ":[0-9]\+->" -o | grep "[0-9]\+" -o | sort | uniq
```

- `:[0-9]\+->` 从 `lsof` 输出中提取主机端口部分（`:49712->`）
- `[0-9]\+` 提取端口号
- 同一个端口可能拥有多个连接，所以使用 `sort + uniq` 进行去重处理