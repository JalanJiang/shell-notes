# df

`disk free`

检查linux服务器的文件系统的磁盘空间占用情况，可以获取硬盘被占用了多少空间，目前还剩下多少空间等信息。

```
df [选项] [文件]
```

## 选项与参数

### 必要参数

| 选项参数 | 说明 |
| ---- | ---- |
| -a | 全部文件系统列表 |
| -h | 方便阅读方式显示 |
| -H | 等于“-h”，但是计算式，1K=1000，而不是1K=1024 |
| -i | 显示inode信息 |
| -k | 区块为1024字节 |
| -l | 只显示本地文件系统 |
| -m | 区块为1048576字节 |
| --no-sync | 忽略 sync 命令 |
| -P | 输出格式为POSIX |
| --sync | 在取得磁盘信息前，先执行sync命令 |
| -T | 文件系统类型 | 

### 选择参数

| 选项参数 | 说明 |
| ---- | ---- |
| --block-size=<区块大小> | 指定区块大小 |
| -t<文件系统类型> | 只显示选定文件系统的磁盘信息 |
| -x<文件系统类型> | 不显示选定文件系统的磁盘信息 |
| --help | 显示帮助信息 |
| --version | 显示版本信息 |

## 显示磁盘使用情况

```
➜  hexo-blog git:(hexo) ✗ df

Filesystem                             512-blocks      Used Available Capacity iused      ifree %iused  Mounted on
/dev/disk1                              487662600 442159384  44991216    91% 2063908 4292903371    0%   /
devfs                                         390       390         0   100%     676          0  100%   /dev
map -hosts                                      0         0         0   100%       0          0  100%   /net
map auto_home                                   0         0         0   100%       0          0  100%   /home
/Users/zj-db0908/Downloads/Postman.app  487662600 424199248  62951352    88% 2037977 4292929302    0%   /private/var/folders/rv/j43c3v_d2wb51r4w8t1y61h80000gn/T/AppTranslocation/6FDC6726-A781-4388-B23C-1AB94288EC12
```

## 显示指定类型磁盘

```
➜  hexo-blog git:(hexo) ✗ df -T devfs

Filesystem 512-blocks Used Available Capacity iused ifree %iused  Mounted on
devfs             390  390         0   100%     676     0  100%   /dev
```

## 以易读方式展示

```
➜  hexo-blog git:(hexo) ✗ df -h

Filesystem                               Size   Used  Avail Capacity iused      ifree %iused  Mounted on
/dev/disk1                              233Gi  211Gi   21Gi    91% 2063910 4292903369    0%   /
devfs                                   195Ki  195Ki    0Bi   100%     676          0  100%   /dev
map -hosts                                0Bi    0Bi    0Bi   100%       0          0  100%   /net
map auto_home                             0Bi    0Bi    0Bi   100%       0          0  100%   /home
/Users/zj-db0908/Downloads/Postman.app  233Gi  202Gi   30Gi    88% 2037977 4292929302    0%   /private/var/folders/rv/j43c3v_d2wb51r4w8t1y61h80000gn/T/AppTranslocation/6FDC6726-A781-4388-B23C-1AB94288EC12
```

仅显示本地文件系统情况。

```
➜  hexo-blog git:(hexo) ✗ df -lh
Filesystem   Size   Used  Avail Capacity iused      ifree %iused  Mounted on
/dev/disk1  233Gi  211Gi   21Gi    91% 2063911 4292903368    0%   /
```