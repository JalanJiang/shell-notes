# 调试脚本

## 使用 `-x` 选项：

```
bash -x script.sh
sh -x script.sh
```

## 部分调试

```
#!/bin/bash

for i in {1..6};
do 
    set -x
    echo $i #只会打印出此行调试信息
    set +x
done
echo "Script executed"
```

- 加上 `DEBUG` 打印调试信息
- 把 `#!/bin/bash` 改为 `#!/bin/bash -xv`，不用其他选项就能启用调试功能了