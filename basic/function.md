# 函数和参数

## 定义函数

```
function fname()
{
    statements;
}

fname()
{
    statements;
}
``` 

## 执行函数 

```
fname;
```

## 参数传递

```
fname arg1 arg2;
```

## 参数表示

- $1 第一个参数
- $2 第二个参数
- $n 第n个参数
- $@ 以列表形式一次性打印所有参数

## 获取函数返回值

```
cmd;
echo $?; #获取函数返回值
```
