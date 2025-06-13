# 免密登录

### 生成 ssh key
`ssh-keygen -t rsa -C  "email@example.com"`

```
Host github
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa
```

```bash
# 如果不用 root 登录可注释
PermitRootLogin yes
AuthorizedKeysFile .ssh/authorized_keys
PubkeyAuthentication yes
PasswordAuthentication no
# 不关闭可能造成无法登陆
StrictModes no
```

## 受信任的远程主机 key
~/.ssh/authorized_keys


### 重启sshd服务
- `systemctl restart ssh`

# ProxyCommand
```
Host github.com
  ProxyCommand nc -v -x 192.168.10.120:7890 %h %p
# Linux
ProxyCommand nc --proxy-type socks5 --proxy 127.0.0.1:7891 %h %p
```