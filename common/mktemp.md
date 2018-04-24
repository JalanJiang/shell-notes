# mktemp

- 生成临时文件/目录
- 返回文件名/目录名

## 选项与参数

| 选项参数 | 说明 |
| ---- | ---- |
| -d | 创建临时目录 |
| -u | 仅生成文件名 |

## For example

```
$ mktemp
$ mktemp -d
$ mktemp -u
# 根模板创建临时文件
$ mktemp test.XXX
```