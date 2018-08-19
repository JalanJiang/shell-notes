# ln

## 创建符号链接

```
$ ln -s target symbolic_link_name
```

创建一个名为 `web` 的符号链接，指向 `/var/www`。

```
$ ln -l -s /var/www ~/web
```

## 打印当前目录下的符号链接

```
$ ls -l | grep "^l"
```

## 打印符号链接所指向的目标路径

```
$ readlink web
/var/www
```