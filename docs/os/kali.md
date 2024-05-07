# Kali

```
sudo sed -i 's#http.kali.org#mirrors.aliyun.com#g' /etc/apt/sources.list
```

### /etc/apt/sources.list
```bash
$ cat /etc/apt/sources.list
# See: https://www.kali.org/docs/general-use/kali-linux-sources-list-repositories/
deb http://http.kali.org/kali kali-rolling main contrib non-free non-free-firmware

# Additional line for source packages
#deb-src http://http.kali.org/kali kali-rolling main contrib non-free non-free-firmware
```