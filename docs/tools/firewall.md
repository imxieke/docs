## Firewall

- firewall-cmd --list-ports 需要重启才可以看到新添加的
- firewall-cmd --zone=public --add-port=80/tcp --permanent 开放端口

```
--permanent         永久开放 没有此参数重启后失效
–zone               作用域
–add-port=80/tcp    添加端口，格式为：端口/通讯协议
--reload            重启firewall
--state             查看默认防火墙状态

systemctl stop firewalld.service        #停止firewall
systemctl disable firewalld.service     #禁止firewall开机启动
```