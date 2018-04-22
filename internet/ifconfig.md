# ifconfig

## 列出当前网络接口配置

```
ifconfig
lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
	options=1203<RXCSUM,TXCSUM,TXSTATUS,SW_TIMESTAMP>
	inet 127.0.0.1 netmask 0xff000000
	inet6 ::1 prefixlen 128
	inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1
	nd6 options=201<PERFORMNUD,DAD>
gif0: flags=8010<POINTOPOINT,MULTICAST> mtu 1280
stf0: flags=0<> mtu 1280
……
```

### 打印网络接口列表

```
ifconfig | cut -c-10 | tr -d ' ' | tr -s '\n'
```

- `ifconfig` 输出的前 10 个字符是用于保留打印网络接口的名称
- `cut -c-10` 取出每行前 10 个字符
- `tr -d ' '` 删除每一行所有空格
- `tr -s '\n'` 压缩重复的换行符

### 显示某个特定的接口信息

```
ifconfig lo0
lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
	options=1203<RXCSUM,TXCSUM,TXSTATUS,SW_TIMESTAMP>
	inet 127.0.0.1 netmask 0xff000000
	inet6 ::1 prefixlen 128
	inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1
	nd6 options=201<PERFORMNUD,DAD>
```

## 设置 IP 地址

设置 IP 地址

```
ifconfig wlan0 192.168.0.80
```

设置 IP 地址的子网掩码

```
ifconfig wlan0 192.168.0.80 nwtmask 255.255.252.0
```

## 自动配置网络接口

```
dhclient eth0
```

