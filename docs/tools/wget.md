# 镜像网站

### 此方法不会更改 html 内的 url
- wget -m --no-check-certificate www.example.com

### 以递归的方式下载整站，并将页面中链接转换为本地链接
- wget -r -p -np -k http://www.example.com

#### 下载 http://example.com 网站上 packages 目录中所有文件
- wget -r -np -nd http://example.com/packages/

#### 只下载 http://ooxx.com/packages/ 当前目录下 .ipk 后缀文件和 .gz 后缀文件。
- wget -nd -r -l1 --no-parent -A.ipk -A.gz http://ooxx.com/packages/

#### 下载网站目录下除 html 外的文件和目录，且不遵守 robots.txt 限制。
- wget -c -r -np -k -L --reject=html http://mirrors.rit.edu/rpi/images/ -e robots=off

### wget options
- -m -mirror 镜像 –mirror 等价于 -r -N -l inf -nr
- -e robots=off 无视robots.txt协议
- -np 作用是不遍历父目录
- -nd 表示不在本机重新创建目录结构。
- -i --input-file 使用本地文件下载地址集 所有下载地址都写在这里
- -A --accept=iso 只接受 iso 文件 可使用 -i file.txt
- --no-check-certificate 不检查 SSL 证书
- -r, –recursive（递归）
- -k, –convert-links（转换链接、将 HTML 页面中的链接转换为相对链接即本地链接）
- -p, –page-requisites（下载所有的图片等页面显示所需的内容）
- -np, –no-parent（不追溯至父级）
- –restrict-file-names=nocontrol 用来解决中文乱码问题（需要可以试试）
- -L,  --relative     网页跳转跟随
- -U "Mozilla/5.0 (Windows; U; Windows NT 5.1; zh-CN; rv:1.9.1.6) Gecko/20091201 Firefox/3.5.6"
- -np, –no-parent（不追溯至父级）          don’t ascend to the parent directory.
- -p,  –page-requisites（页面必需元素）    get all images, etc. needed to display HTML page.（下载所有的图片等页面显示所需的内容）
- -k,  –convert-links（转换链接）      make links in downloaded HTML point to local files.（将下载的HTML页面中的链接转换为相对链接即本地链接）
- –limit-rate=300k 限速
- -c   断点续传
- --spider  模拟爬虫测试链接不进行下载    don't download anything