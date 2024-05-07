## BBR

### kernel > 4
```
echo net.core.default_qdisc=fq >> /etc/sysctl.conf
echo net.ipv4.tcp_congestion_control=bbr >> /etc/sysctl.conf
sysctl -p
```

## 检查是否生效
```
执行 sysctl net.ipv4.tcp_available_congestion_control
输出 net.ipv4.tcp_available_congestion_control = bbr cubic reno
```