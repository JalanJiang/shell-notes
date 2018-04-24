# 数组和关联数组

## 数组

```
#!/bin/sh

# 声明数组
array_ver=(1 2 3 4)
echo ${array_ver[2]}
array_ver[3]="test2" #数组赋值
index=3
echo ${array_ver[$index]}
# 打印数组中的所有值
echo ${array_ver[*]}
echo ${array_ver[@]}
# 打印数组长度
echo ${#array_ver[*]}
```

## 关联数组

```
#!/bin/sh
# 声明关联数组
declare -A ass_array
index1=1
index2=2
# 内嵌“索引-值”列表的方法，提供一个“索引-值”列表
ass_array=([$index1]=1 [$index2]=2)
echo ${ass_array[*]}
# 使用一个独立的“索引-值”进行赋值
ass_array[$index1]=2
ass_array[$index2]=1
echo ${ass_array[*]}
```

使用关联数组为水果定制价格：

```
#!/bin/sh
declare -A fruits_value
fruits_value=([apple]='100' [orange]='200')
echo "Apple costs ${fruits_value[*]}"
```

列出数组索引：

```
echo ${!ass_array[*]}
echo ${!ass_array[@]}
```
