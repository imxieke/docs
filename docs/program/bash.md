## 删除传入的第一个参数
```shell
echo $@
shift # 删除第一个参数 后面自动前移
echo "${@:2}" # 从第二个开始输出 同样可以实现删除第一个参数
```