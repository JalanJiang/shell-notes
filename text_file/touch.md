# touch

## 创建空白文件

```
$ touch filename
```

## 修改文件相关的时间

如果文件已经存在，那么 `touch` 命令会将与该文件相关的所有时间戳都改为当前时间。

### 更改文件访问时间

```
$ touch -a filename
```

### 更改文件内容修改时间

```
$ touch -m filename
```

### 指定特定的时间和日期

```
$ touch -d "Fri Jun 25 20:50:14 IST 1999" filename
```

