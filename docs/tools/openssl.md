## 查看证书信息
- openssl x509 -in cert.pem -noout -text

## CSR 信息
- openssl req -in my.csr -noout -text

## 把PEM格式的证书转化成DER格式
- openssl x509 -in cert.pem -inform PEM -out cert.der -outform DER