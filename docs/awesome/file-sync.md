## 文件同步

### [RSync](https://rsync.samba.org) (C)
- linux 下常用的文件同步工具, 跨文件夹 计算机文件同步
- 支持增量备份
- 镜像站点常用的同步工具

### [RClone](https://github.com/rclone/rclone) (Go)
- rsync for cloud storage
- 适用于云存储的同步工具
- 支持非常多的云服务商
- 支持多线程 分块 传输压缩
- 支持挂载到本地
- Can serve local or remote files over HTTP/WebDAV/FTP/SFTP/DLNA

### [Syncthing](https://github.com/syncthing/syncthing) (Go)
- 点对点文件同步
- 很强大 倾向于个人或团队文件同步

### [Resilio Sync](https://www.resilio.com/individuals) `闭源`
- 点对点文件同步
- 倾向于文件共享 由于众所周知的原因 国内水土不服

### [微力同步](https://www.verysync.com) `闭源`
- 点对点文件同步
- 会将文件分割加密
- 国内用户的替代品