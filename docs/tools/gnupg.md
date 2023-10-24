# GNUPG 
```
gpg --full-gen-key 完整生成 key 模式
gpg --armor --detach-sign file 生成 .pub 纯文本文件
gpg --armor file 生成 pgp 压缩文件
gpg --decrypt --output pkg_compress_name output_file_name 解密被加密文件
gpg --sign --armor --detach-sign file   生成 asc 文件 明文
gpg --sign --detach-sign file 生成 sig 文件 加密
```