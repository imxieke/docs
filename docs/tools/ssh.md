# ~/.ssh/config

### 生成 ssh key
`ssh-keygen -t rsa`

```
Host hostalias
  HostName google.com
  User ubuntu
  ForwardAgent yes
  IdentityFile ~/.ssh/id_rsa
```

```
PubkeyAuthentication yes
PasswordAuthentication no
```

## 受信任的远程主机 key
~/.ssh/authorized_keys


重启sshd服务


# ProxyCommand
```
Host github.com
  ProxyCommand nc -v -x 192.168.10.120:7890 %h %p
# Linux
ProxyCommand nc --proxy-type socks5 --proxy 127.0.0.1:7891 %h %p
```