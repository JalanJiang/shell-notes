# cat

`cat` 即 `concatenate`，拼接。

## 用 cat 读取文件

```
$ cat file1 file2 file3
```

`cat` 将作为命令行参数的文件内容拼接到一起。

打印单个文件的内容则使用 `cat file.txt`。

## 从标准输入中进行读取

从标准输入中读取需要使用管道。

```
OUTPUT_FROM_SOME COMMANDA | cat
```

例如：

```
$ echo 'Text through stdin' | cat - file.txt
```

**`-` 被作为 stdin 文本的文件名。**

## 文件查看选项

### 摆脱多余空白行

```
$ cat -s file
```

### 将制表符显示为 `^|`

```
$ cat -T file
```

### 加入行号

```
$ cat -n file
```

**`-n` 也会为空白行加上行号。若要跳过空白行，可以使用 `-b`。**
