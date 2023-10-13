# WSL
- 启用 CPU 虚拟化
- 安装内核更新包
- 启用 hyper-v

## 错误代码
### 0x800701bc
- 更新内核
- https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi
- `wsl --update`

#### 0x80370114
- 启用 hyper-v 虚拟机


## 常见命令
### Set WSL 2 as your default version
- `wsl --set-default-version 2`

### Enable Virtual Machine feature
- `dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart`
- `Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform`

### 启用子系统
- `dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart`
- `Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux`

## 更改 wsl 系统 版本
- `wsl --set-version <distro name> 2`
- 
## 设定默认 wsl 系统
- `wslconfig /s <name>`
- `wsl --set-default, -s <name>`


## WSL url

### Archlinux
- https://github.com/yuk7/ArchWSL/releases

### CentOS
- https://github.com/mishamosher/CentOS-WSL/releases

* Redhat
- https://github.com/yosukes-dev/RHWSL/releases

### Fedora
- https://github.com/yosukes-dev/FedoraWSL

### Manjaro
- https://github.com/sileshn/ManjaroWSL

### Alpine
- https://github.com/yuk7/AlpineWSL