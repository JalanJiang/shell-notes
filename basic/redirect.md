# 玩转文件描述符与重定向

## 文件描述符

文件描述符是与文件输入、输出相关联的**整数**。

- 0 —— stdin 标准输入
- 1 —— stdout 标准输出
- 2 —— stderr 标准错误

## 重定向


### 将输出文本保存到文件中

重定向操作符：

- `>`：先清空文件再写入
- `>>`：追加写入
- `<`：从文件中读取

```
# 清空文件并保存文本信息
echo "Hello world" > temp.txt
# 追加文本信息
echo "Hi!" >> temp.txt
# 从文件中读取数据
cat < temp.txt
```

- 使用重定向操作符后，输出内容不会在终端打印，而是被导入文件
- 默认使用标准输出，其他描述符需要指定，例如 `2>>`

### 重定向标准错误的方法

将 `ls +` 的 stderr 信息重定向到 `out.txt`：

```
ls + 2 > out.txt 
```

将 stderr 与 stdout 分开重定向：

```
ls + 2>stderr.txt 1>stdout.txt
```

将 stderr 信息转为 stdout 信息，使两者重定向到同一个文件中：

```
ls + 2>&1 output.txt

ls + &> output.txt
```
