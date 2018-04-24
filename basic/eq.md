# 比较与测试

## if

```
if condition;
then
    cmmands;
fi

if condition;
then
    commands;
else if condition; then
    commands;
else
    commands;
fi
```

## 算数比较

- 条件通常被放置在封闭的中括号中 `[]`
- **中括号与操作数之间有一个空格**：`[ $var -eq 0 ]`

重要操作符：

- -gt 大于
- -lt 小于
- -ge 大于或等于
- -le 小于或等于
- -a 逻辑与AND
- -o 逻辑或OR

## 文件系统相关测试

- `[ -f $file_var ]`：正常的文件路径活文件名
- `[ -x $var ]`：可执行文件
- `[ -d $var ]`：目录
- `[ -e $var ]`：文件存在
- `[ -c $var ]`：包含一个字符设备文件的路径
- `[ -b $var ]`：包含一个块设备文件路径
- `[ -w $var ]`：可写
- `[ -r $var ]`：文件可读
- `[ -L $var ]`：包含的是一个符号链接

## 字符串比较

最好使用双中括号。

- `[[ -z $str ]]`：空字符串，返回真
- `[[ -n $str ]]`：包含非空字符串，返回真
- `[[ $str1 = $str2 ]]`：**等号前后有空格，否则为赋值语句**
