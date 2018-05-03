# comm

- 用于两个文件之间的比较
- 必须使用排序过的文件作为输入
- 按照需求对输出进行格式化
    - `-1` 从输出中删除第一列
    - `-2` 从输出中删除第二列
    - `-3` 从输出中删除第三列

## 不带参数选项

```
$ comm A.txt B.txt
apple
	    carrot
	    cookies
		         gold
iron
		         orange
silver
steel
```

- 第一列包含仅在 A.txt 中出现的行
- 第二列包含只在 B.txt 中出现的行
- 第三列包含 A.txt 和 B.txt 中相同的行
- 各列以 `\t` 作为定界符

## 打印交集

删除第一列和第二列

```
$ comm -1 -2 A.txt B.txt
gold
orange
```

## 打印不同行

```
$ comm -3 A.txt B.txt
apple
	    carrot
	    cookies	         
iron	         
silver
steel
```

## 生成规范性输出

将两列合并成一列。

```
$ comm -3 A.txt B.txt | sed 's/^\t//'
```

## 打印差集

A的差集：

```
$ comm -2 -3 A.txt B.txt
```

B的差集：

```
$ comm -1 -3 A.txt B.txt
```

