# 找出网络上的活跃主机

## 方法一

使用 `ping` 命令查询一组 IP 地址的状态。

```
#!/bin/bash

for ip in 192.168.0.{1..255} ;
do
	ping $ip -c 2 &> /dev/null ;

	if [ $? -eq 0 ];
	then
		echo $ip is alive
	else
		echo $ip is not alive
	fi
done
```

- 用 `192.168.0.{1..255}` 产生一组 IP 地址
- `&> /dev/null` 将 `stderr` 和 `stdout` 重定向到 `/dev/null` 中
- `$?` 获取上文 `ping` 命令的退出状态

## 方法二

方法一存在一个缺点，`ping` 命令按顺序执行，每执行一次 `ping` 都要经历一段延时：

1. 发送两个 echo 分组
2. 接收回应 OR 等待回应超时

处理地址越多，经历的延时就越长。为避免延时，我们可以使用并行方式来加速 `ping` 命令的执行。

步骤：

1. 将 `ping` 的动作放入 `()` 中作为子 shell 执行
2. 加上 `&` ，让命令置入后台执行

改造一下：

```
#!/bin/bash

for ip in 192.168.0.{1..255} ;
do
    (
	ping $ip -c 2 &> /dev/null ;

	if [ $? -eq 0 ];
	then
		echo $ip is alive
	else
		echo $ip is not alive
	fi
	)&
done
# 若要等待所有命令执行结束再退出当前 sh，可以加上 wait
wait
```