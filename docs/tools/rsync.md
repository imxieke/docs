# Rsync
- `--remove-source-files` 当文件同步完成后删除源文件

### 常用 同步后删除源文件

### 会压缩文件
`rsync -avz --progress --remove-source-files --recursive`
### 不压缩文件
`rsync -v --progress --remove-source-files --recursive`

#### 同步至本地 同步到服务器则将源和目标参数对调
- 老版本默认不支持 `ssh`  需要使用 `-e ssh` 选项 新版本可以忽略
- 但是非标准 ssh 端口 需要指定端口信息 `ssh -p <port>`
```
rsync -avzrtp --progress -e ssh user@host:/path/to/dir <dest>
rsync --archive --verbose --compress --recursive --times --perms 
```

## 参数
- `--remove-source-files` 	删除源文件当传输完成
- `--delete` 				将删除只存在于目标目录、不存在于源目录的文件
- --exclude 排除指定文件
  - 下面是几个示例
  - `--exclude '*.txt'`
  - `--exclude 'file1.txt' --exclude 'dir1/*'`
  - `--exclude={'file1.txt','dir1/*'}`
  - `--exclude-from` 将所有规则写进一般为 txt 文件
  - `--include="*.txt" --exclude='*'` 也可以配合 `include` 排除所有 但包含`*.txt`