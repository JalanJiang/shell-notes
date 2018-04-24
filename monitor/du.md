# du

`disk usage`

显示每个文件和目录的磁盘使用空间。

```
du [选项][文件]
```

## 选项与参数

| 选项参数 | 说明 |
| ---- | ---- |
| -a/-all | 递归显示目录中文件的大小 |
| -b/-bytes | 显示目录或文件大小时，以byte为单位 |
| -c/--total | 除了显示个别目录或文件的大小外，同时也显示所有目录或文件的总和 |
| -k/--kilobytes | 以KB(1024bytes)为单位输出 |
| -m/-megabytes | 以MB为单位输出 |
| -s/--summarize | 仅显示总计，只列出最后加总的值 |
| -h/--human-readable | 以K，M，G为单位，提高信息的可读性 |
| -x/--one-file-xystem | 以一开始处理时的文件系统为准，若遇上其它不同的文件系统目录则略过 |
| -L<符号链接>/--dereference<符号链接> | 以一开始处理时的文件系统为准，若遇上其它不同的文件系统目录则略过 |
| -S/--separate-dirs | 显示个别目录的大小时，并不含其子目录的大小 |
| -X<文件>/--exclude-from=<文件> | 在<文件>指定目录或文件 |
| --exclude=<目录或文件> | 略过指定的目录或文件 |
| -D/--dereference-args | 显示指定符号链接的源文件大小 |
| -H/--si | 与-h参数相同，但是K，M，G是以1000为换算单位 |
| -l/--count-links | 重复计算硬件链接的文件 |

## 显示目录所占空间。

```
➜  [curl] du

88	./vendor/composer
16	./vendor/php-curl-class/php-curl-class/.github
8	./vendor/php-curl-class/php-curl-class/docs
560	./vendor/php-curl-class/php-curl-class/examples
40	./vendor/php-curl-class/php-curl-class/scripts
160	./vendor/php-curl-class/php-curl-class/src/Curl
160	./vendor/php-curl-class/php-curl-class/src
584	./vendor/php-curl-class/php-curl-class/tests/PHPCurlClass
640	./vendor/php-curl-class/php-curl-class/tests
288	./vendor/php-curl-class/php-curl-class/www/img
328	./vendor/php-curl-class/php-curl-class/www
1816	./vendor/php-curl-class/php-curl-class
1816	./vendor/php-curl-class
1912	./vendor
1992	.
```

只显示当前目录下子目录的大小和当前目录的大小总和。1992为当前目录的大小总和。

显示文件+目录。

```
➜  [curl] du -a

8	./composer.json
8	./composer.lock
8	./index.php
16	./test.jpeg
32	./test1.jpg
8	./vendor/autoload.php
8	./vendor/composer/autoload_classmap.php
8	./vendor/composer/autoload_namespaces.php
8	./vendor/composer/autoload_psr4.php
8	./vendor/composer/autoload_real.php
8	./vendor/composer/autoload_static.php
32	./vendor/composer/ClassLoader.php
8	./vendor/composer/installed.json
8	./vendor/composer/LICENSE
88	./vendor/composer
………………………………………………………………………………
1912	./vendor
8	./weixin.php
1992	.
```

## 显示指定文件或目录所占空间

```
➜  [curl] du index.php

8	index.php
```

`du` 命令后可跟（多个）文件名、（多个）文件夹名。

### 显示总和大小

```
➜  [curl] du -s

1992	.
```

并增强可读性。

```
➜  [curl] du -hs

996K	.
```

### 按空间大小排序

```
➜  [curl] du | sort -nr | more
1992    .
1912    ./vendor
1816    ./vendor/php-curl-class/php-curl-class
1816    ./vendor/php-curl-class
640     ./vendor/php-curl-class/php-curl-class/tests
584     ./vendor/php-curl-class/php-curl-class/tests/PHPCurlClass
560     ./vendor/php-curl-class/php-curl-class/examples
328     ./vendor/php-curl-class/php-curl-class/www
288     ./vendor/php-curl-class/php-curl-class/www/img
160     ./vendor/php-curl-class/php-curl-class/src/Curl
160     ./vendor/php-curl-class/php-curl-class/src
88      ./vendor/composer
40      ./vendor/php-curl-class/php-curl-class/scripts
16      ./vendor/php-curl-class/php-curl-class/.github
8       ./vendor/php-curl-class/php-curl-class/docs
```