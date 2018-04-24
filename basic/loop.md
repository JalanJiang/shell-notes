# 迭代器（循环）

## for

```
for var in list;
do
    commands;
done
```

list 可以是字符串，也可以是序列。

```
for i in {a..z};
do
    actions;
done;
```

```
for ((i=0; i<10; i++))
{
    commands;
}
```

## while

```
while condition
do
    commands;
done
```

## until

```
x = 0
until [$x -eq 9];
do
    let x++;
    echo $x;
done
```
