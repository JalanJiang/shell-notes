# sh
 
- 系统管理工具
- 用于访问远程计算机上的 shell
- 使用加密通道传输网络数据
- 默认运行在 22 端口
 
## 基本语法
 
### 连接运行 SSH 服务的远程主机
 
```
$ ssh -p port username@remote_host
```
 
### 在远程主机中执行命令并将命令显示在本地 shell 中
 
```
$ ssh user@host 'COMMANDS1; COMMANDS2, COMMANDS3'
```
 
### 数据压缩传输
 
```
$ ssh -C user@hostname COMMANDS
```
 
### 重定向至远程 shell 的 stdin
 
```
$ echo 'text' | ssh user@remote_root 'echo'
```

----

## 实现无密码自动登录

SSH 采用了**非对称加密技术**，认证密钥包括两个部分：

- 公钥
- 私钥

### 创建 SSH 密钥

```
# 指定加密算法类型为RSA
$ ssh-keygen -t rsa
```

输入口令后生成：

- 公钥 `id_rsa.pub`
- 私钥 `id_rsa`

### 将公钥添加到远程服务器中

将公钥传给远程主机，并将其加入文件 ~/.ssh/authorized_keys 中。

```
$ ssh user@remote_root "cat >> ~/.ssh/authorized_keys" < ~/.ssh/id_rsa.pub
```

----

## 端口转发

端口转发允许其他计算机利用你的主机来连接到远程服务器上的特定服务。

**转发本地主机的流量：**

将本地主机端口 8000 上的流量 **转发到** www.kernel.org的 80 端口上。

当用户访问本地主机时他将访问到 www.kernel.org:80 的服务。

```
$ ssh -L 8000:www.kernel.org:80 user@localhost
```

**转发远程主机上的流量：**

将远程主机端口 8000 上的流量 **转发到** www.kernel.org的 80 端口上。

```
$ ssh -L 8000:www.kernel.org:80 user@remote_root
```

### 非交互式端口转发

- 转发端口
- 不需要保持一个打开状态的 Shell

```
$ ssh -fL 8000:www.kernel.org:80 user@localhost -N
```

- `-f` 指定 ssh 在执行命令前转入后台运行
- `-L` 指定主机登录名
- `-N` 无需执行命令，只执行端口转发

### 反向端口转发（远程 --> 本地）

适用场景：让用户访问未联网主机上的服务。

将远程主机端口 8000 上的流量转发到本地主机的 80 端口上：

```
$ ssh -R 8000:localhost:80 user@remote_root
```



 

 
 