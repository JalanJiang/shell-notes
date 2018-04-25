# uniq

```
uniq [-ic]
```

## 选项与参数

| 选项参数 | 说明 |
| ---- | ---- |
| -i | 忽略大小写 |
| -c | 进行计数 |

## 使用场景

排序后将重复的数据仅列出一个显示。

## 栗子一

使用 last 将账号列出，仅取出账号栏，进行排序后仅取出一位。

```
➜  / last | cut -d ' ' -f 1 | sort | uniq


_mbsetupuser
reboot
root
shutdown
wtmp
zj-db0908
```

## 栗子二

计算每个用户的登录次数。

```
last | cut -d ' ' -f 1 | sort | uniq -c

   1
   3 _mbsetupuser
  38 reboot
   4 root
  30 shutdown
   1 wtmp
 340 zj-db0908
```

注：wtmp 与第一行的空白都是 last 的默认字符，可以忽略
