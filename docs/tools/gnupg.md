# GNUPG 

## 完整生成 key 模式
`gpg --full-gen-key`

## macOS 或 Cygwin 失败使用
`gpg --gen-key`

## 解密被加密文件
`gpg --decrypt --output pkg_compress_name output_file_name`

## 生成 pgp 压缩文件
`gpg --armor file`
`gpg --sign file`


## 生成 .pub 纯文本文件
`gpg --armor --detach-sign file`

## 生成 asc 文件 明文
`gpg --clearsign file`
`gpg --sign --armor --detach-sign file`

## 生成 sig 文件 加密
`gpg --sign --detach-sign file`

## 列出已创建的 GPG 密钥
`gpg --list-secret-keys --keyid-format LONG "your_email"`

## 生成公钥
`gpg --armor --export BD6A8BDCCAFA9273`


## 删除
`gpg --delete-key KEY_ID`

## 公钥文件（.gnupg/pubring.gpg）以二进制形式储存，armor参数可以将其转换为ASCII码显示。
`gpg --armor --output public-key.txt --export KEY_ID`

## 导出私钥
`gpg --armor --output private-key.txt --export-secret-keys KEY_ID`

## 上传公钥
`gpg --send-keys KEY_ID --keyserver hkp://subkeys.pgp.net`

## 导出公钥
`gpg -a -o xxx.pub.key --export KEY_ID`


## 导出私钥
`gpg -a -o xxx.pub.key --export-secret-keys KEY_ID`