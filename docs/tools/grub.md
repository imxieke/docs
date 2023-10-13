## 修改主题

放置目录, 需要有 `theme.txt`

```
若不存在则创建
sudo mkdir /boot/grub/themes
目前不确定是哪个 或许两个都可以
/boot/grub/themes/
sudo chown $USER /boot/grub/themes/
```

### 编辑 `/etc/default/grub`

```
cp -fr /your/path/name /boot/grub/themes/name
nvim /etc/default/grub
GRUB_THEME="/boot/grub/themes/name/theme.txt"
修改为屏幕尺寸否则可能会无法填满屏幕
GRUB_GFXMODE=1920x1080
```

### 生效
执行 `update-grub` 使 `grub` 生效

### 基于 RPM 的系统上 例如 Fedora, 运行下面的命令来更新 GRUB:

```
grub-mkconfig -o /boot/grub/grub.cfg
```

### 通用配置
```
# Debian ⛔ Ubuntu ⛔ Arch
sudo grub-mkconfig -o /boot/grub/grub.cfg

# Fedora ⛔ Redhat
sudo grub2-mkconfig -o /boot/grub2/grub.cfg
```