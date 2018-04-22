# route

## 显示路由表

```
$ route
$ route -n  #以数字形式显示所有条目
```

**macOS 则使用 `Netstat` 命令查看。**

## 设置默认网关

```
$ route add default gw IP_ADDRESS INTERFACE_NAME
```

例如

```
$ route add default gw 192.168.0.1 wlan0
```
