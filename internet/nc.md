# nc

创建套接字进行通信。

## 发送文本

### 设置监听套接字

```
$ nc -l 1234
```

### 连接到该套接字

```
$ nc HOST 1234
```

### 发送信息

结果如下：

![nc-example](/image/nc-example.png)

## 发送文件

接收端：

```
$ nc -l 1234 > destination_filename
```

发送端：

```
$ nc HOST 1234 < source_filename
```