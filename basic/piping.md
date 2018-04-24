# 管道

将命令序列的输出读入变量。

- 使用场景：想获取的输出需要经过几道手续才能得到
- 定界符：`|`
- 注意：
	- 仅会处理 `standard input` ，对 `standard error output` 没有处理能力
	- 管线后：必须跟着可接受 `standard input` 数据的命令（例如 less, more, head, tail）


列出 `/Users/www` 目录下的所有文件，并进行分页显示。

```
ls -al /Users/www | less
```

## 获取管道相连命令序列的输出

子shell方法：`cmd_output = $(COMMANDS)`

```
cmd_output = $(ls | cat -n)
echo $cmd_output
```

反引用法：

```
cmd_output = `ls | cat -n`
echo $cmd_output
```

## 利用子shell生成独立进程

```
pwd;
#子shell不会对当前shell产生影响
(cd /bin; ls);
pwd
```

- 把子shell放在双引号中可以保留空格和换行
