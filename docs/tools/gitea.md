## 常见问题
### 无法 ssh 登录
- 必须指定 /bin/bash 不然无法登录

useradd -M -G git -s /bin/bash git
useradd -M -g 1004 -s /bin/bash git 若用户组存在则指定用户组 id