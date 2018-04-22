# 用 grep 在文件中搜索文本

```
grep [-acinv] [--color=auto] '搜索字符串' filename
```

## 使用场景

取出符合查找条件的一行信息

## 选项与参数

| 选项参数 | 说明 |
| -- | -- |
| -a |  将 binary 文件以 text 文件的方式搜寻数据|
| -c | 计算找到“搜寻字符串”的次数 |
| -i | 忽略大小写的不同（大小写视为相同）|
| -n | 顺便输出行号 |
| -v | 反向选择（显示出没有“搜寻字符串”的那行） |
| -E | 使用正则表达式 |
| -o | 仅输出匹配到的文本 |
| -b | 打印模式匹配所位于的字符或字节偏移 |
| -l/-L | 在多个文件中寻找匹配 |
| --include | 指定包含文件 |
| --exclude | 排除文件 |
| --exclude-dir | 排除文件夹 |
| -A | 文本前x行 |
| -B | 文本后x行 |

## 举个栗子

### 搜索包含特定模式的文本行

```
grep pattern filename
grep pattern file1 file2 file3 ...
```

取出出现 `root` 的一行。

```
➜  / last | grep "root"

root      console                   Mon Oct  2 13:29 - shutdown  (00:02)
root      console                   Tue Aug 29 10:47 - shutdown  (00:00)
root      console                   Thu Jun 15 13:31 - 13:31  (00:00)
root      console                   Tue Jun  6 12:10 - 12:10  (00:00)
```

取出未出现 `root` 的一行。

```
➜  / last | grep -v "root"

zj-db0908  ttys008                   Thu Dec 14 17:13   still logged in
zj-db0908  ttys007                   Thu Dec 14 15:48   still logged in
zj-db0908  ttys001                   Thu Dec 14 13:50   still logged in

```

### 正则匹配

```
grep -E "[a-z]+" filename
egrep "[a-z]+" filename
```

### 搜索多个文件

```
#输出有匹配结果的文件列表
grep -l linux file1 file2 file3
```

`-L` 与 `-l` 相反，会返回一个不匹配文本的文件列表。

### 递归搜索文件

```
grep "text" . -R -n
```

### 多 pattern 匹配

使用 `-e` 指定多个匹配样式。

```
grep -e pattern1 -e pattern2
```

提供一个样式文件，在样式文件中指定多个样式。

```
grep -f path_file
```

path_file 文件内容（一行一个匹配样式）：

```
hello
world
```

### 与 cut 配合使用

取出带 `root` 的信息进行分隔，并只取出分隔结果的第一栏。

```
➜  / last | grep "root" | cut -d " " -f 1

root
root
root
root
```

### 关键词上色

取出 `/etc/asl.conf` 文件中带 `Faci` 的行，并对关键词上色。

```
➜  / grep --color=auto "Faci" /etc/asl.conf

? [= Facility authpriv] access 0 80
? [= Facility remoteauth] [<= Level critical] access 0 80
? [= Facility internal] ignore
? [= Facility auth] [<= Level info] file system.log
? [= Facility authpriv] [<= Level info] file system.log
# Facility com.apple.alf.logging gets saved in appfirewall.log
? [= Facility com.apple.alf.logging] file appfirewall.log file_max=5M all_max=50M
```




