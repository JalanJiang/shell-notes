# `$` 的用法

| 符号 | 说明 |
| ---- | ---- |
| $0 | 执行脚本名称 |
| $n | 传入的第 n 个参数，n = 0～9 |
| $* | 传入的所有参数 |
| $@ | 跟 $* 类似，但是可以当作数组用 |
| $# | 参数个数 |
| $$ | 进程PID |
| $! | 执行上一个背景指令的PID(后台运行的最后一个进程的进程ID号) |
| $? | 执行上一个指令的返回值 (显示最后命令的退出状态。0表示没有错误，其他任何值表明有错误) |
| $- | 显示shell使用的当前选项，与set命令功能相同 |
