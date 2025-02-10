# Ollama

## 介绍
- 模型采用 `Docker` 兼容的容器

## 参数 (用于环境变量或 `systemd` 配置文件)
### 指定模型存储目录
- `OLLAMA_MODELS=/var/lib/ollama`

### 指定 Home 目录
- `HOME=/var/lib/ollama`

## 指定模型下载来源
- `OLLAMA_HOST=0.0.0.0:11434`

## 设置代理

```
mkdir -p /etc/systemd/system/ollama.service.d
touch /etc/systemd/system/ollama.service.d/override.conf

[Service]
Environment="http_proxy=http://192.168.12.168:7890"
Environment="https_proxy=http://192.168.12.168:7890"

```