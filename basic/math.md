# 使用 Shell 进行数学运算

## 整数运算

let 命令

- let 命令可以执行基本的算数操作
- 使用 let 时，变量前不需要 `$`

```
#!/bin/sh
no1=4;
no2=5;
let result=no1+no2;
# 自加操作
let result++;
# 自减操作
let result--;
# 简写形式
let result+=1;
let result-=2;
# 输出结果
echo result=$result;
``` 

`[]` 操作符

- `[]` 操作符使用方法与 let 命令类似
- 在 `[]` 中可以使用 `$`，也可以不使用 `$`

```
result=$[no1 + no2];
result1=$[$no1 + $no2];
```

`(())`操作符

- `(())` 前需加 `$`

```
result2=$((no1+no2));
```

## 浮点数运算

借助数学运算高级工具 `bc`。

```
# 直接输出结果
echo "4*2.5" | bc; #10.0
# 作为变量存储
no=5;
result=`echo "$no*1.5" | bc`;
echo result=$result; #result=7.5
```

### 使用 `scale` 设定保留小数精度


```
echo "scale=2;3/8" | bc; #.37
```

### 进制转换

- `obase=`：指定转换结果的进制
- `ibase=`：指定当前数值的进制

```
#!/bin/sh
no=100;
echo "obase=2;$no" | bc; #1100100

no1=1100100;
echo "obase=10;ibase=2;$no1" | bc; #100
```

### 计算平方与平方根

```
echo "sqrt(100)" | bc #10
echo "10^10" | bc #10000000000
```
