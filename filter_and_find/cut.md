# 用 cut 按列切分文件

用于有特定分隔字符

```
cut -d'分隔字符' -f fields 
```

用于排列整齐的信息

```
cut -c 字符区间            
```

## 使用场景

- 对同一行里面的数据进行分解
- 常用场景：日志切割

## 选项与参数

| 选项参数 | 说明 |
| ---- | ---- |
| -d | 接分隔字符，与 `-f` 一起使用 |
| -f | 根据 -d 的分隔字符将一段信息分成数段，用 -f 取出第几段的意思 |
| -c | 以字符（characters）的单位取出固定字符区间 |

## 举个栗子

### 栗子一

用 `:` 分隔 `$PATH` ，并取出第 5 个。

```
➜  / echo $PATH
/usr/local/bin:/usr/bin:/bin:/usr/local/sbin:/usr/sbin:/sbin

➜  / echo $PATH | cut -d ":" -f 5
/usr/sbin
```

### 栗子二

取出 `export` 12字符以后的所有字符串。

```
➜  / export
Apple_PubSub_Socket_Render=/private/tmp/com.apple.launchd.5Ri9k5vYvp/Render
HOME=/Users/zj-db0908
LANG=zh_CN.UTF-8
LC_CTYPE=zh_CN.UTF-8
LESS=-R
LOGNAME=zj-db0908
LSCOLORS=Gxfxcxdxbxegedabagacad
PAGER=less
PATH=/usr/local/bin:/usr/bin:/bin:/usr/local/sbin:/usr/sbin:/sbin
PWD=/
SHELL=/bin/zsh
SHLVL=1
SSH_AUTH_SOCK=/private/tmp/com.apple.launchd.VGTFxfFRYS/Listeners
TERM=xterm-256color
TERM_PROGRAM=Apple_Terminal
TERM_PROGRAM_VERSION=388.1.1
TERM_SESSION_ID=0DAFA448-F866-460B-899F-39B5FF44A228
TMPDIR=/var/folders/rv/j43c3v_d2wb51r4w8t1y61h80000gn/T/
USER=zj-db0908
XPC_FLAGS=0x0
XPC_SERVICE_NAME=0
ZSH=/Users/zj-db0908/.oh-my-zsh
__CF_USER_TEXT_ENCODING=0x1F5:0x19:0x34

➜  / export | cut -c 12-
b_Socket_Render=/private/tmp/com.apple.launchd.5Ri9k5vYvp/Render
/zj-db0908
UTF-8
_CN.UTF-8

db0908
fxcxdxbxegedabagacad

ocal/bin:/usr/bin:/bin:/usr/local/sbin:/usr/sbin:/sbin

zsh

CK=/private/tmp/com.apple.launchd.VGTFxfFRYS/Listeners
256color
M=Apple_Terminal
M_VERSION=388.1.1
N_ID=0DAFA448-F866-460B-899F-39B5FF44A228
/folders/rv/j43c3v_d2wb51r4w8t1y61h80000gn/T/
908
x0
_NAME=0
zj-db0908/.oh-my-zsh
EXT_ENCODING=0x1F5:0x19:0x34
```

- `12-` 表示12之后的所有字符
- 第 12-20 的字符可以表示为 `cut -c 12-20`

### 栗子三

获取登录信息，筛选出用户名。

```
➜  / last
zj-db0908  ttys008                   Thu Dec 14 17:13   still logged in
zj-db0908  ttys007                   Thu Dec 14 15:48   still logged in
zj-db0908  ttys001                   Thu Dec 14 13:50   still logged in

➜  / last | cut -d ' ' -f 1
zj-db0908
zj-db0908
zj-db0908
```