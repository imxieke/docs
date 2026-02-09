# Debian

```bash
sudo sed -i 's#deb.debian.org#mirrors.aliyun.com#g' /etc/apt/sources.list
sudo sed -i 's#ftp.debian.org#mirrors.aliyun.com#g' /etc/apt/sources.list
sudo sed -i 's#security.debian.org#mirrors.aliyun.com#g' /etc/apt/sources.list
```

### /etc/apt/sources.list
```bash
deb http://mirrors.aliyun.com/debian bookworm main contrib non-free non-free-firmware
deb http://mirrors.aliyun.com/debian bookworm-updates main contrib non-free non-free-firmware
deb http://mirrors.aliyun.com/debian-security bookworm-security main contrib non-free non-free-firmware
deb http://mirrors.aliyun.com/debian bookworm-backports main contrib non-free non-free-firmware
```

## 多版本 PHP
```bash
apt update
apt upgrade
apt install -y apt-transport-https lsb-release ca-certificates wget
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/php.list
apt update

wget -O /usr/share/keyrings/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb [signed-by=/usr/share/keyrings/php.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list

```

## 12 升 13

```
apt update
apt upgrade -y
apt full-upgrade -y
apt autoclean
apt autoremove -y

# 执行完成后重新执行上面的命令
sed -i 's/bookworm/trixie/g' /etc/apt/sources.list /etc/apt/sources.list.d/*.{list,sources} 2>/dev/null


```