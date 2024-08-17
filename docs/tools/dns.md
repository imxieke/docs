## DNS

### DNS-over-HTTPS (DoH) 两个标准
```
https://dns.google/dns-query – RFC 8484 (GET and POST)
https://dns.google/resolve? – JSON API (GET)
```

|类型|ID|意义|示例 taobao.com|
|---|----|-|-|
|A|1|IPv4地址|101.37.183.171|
|NS|2|NS记录|ns1.taobao.com.|
|CNAME|5|域名CNAME记录|www.taobao.com.danuoyi.tbcache.com.|
|SOA|6|ZONE的SOA记录|ns4.taobao.com. hostmaster.alibabadns.com. 2018011109 3600 1200 3600 360|
|TXT|16|TXT记录|"v=spf1 include:spf1.xxx.com -all|
|AAAA|28|IPv6地址|240e:e1:f300:1:3::3fa|
|||||

### Example
- https://dns.google/resolve?name=baidu.com&type=CNAME

### DOH 文档
 - https://help.aliyun.com/document_detail/171666.html

## Cloudflare (IP 可用于 DOT)
- 1.1.1.1
- 1.0.0.1
- 2606:4700:4700::1111
- 2606:4700:4700::1001
- tls://1.0.0.1:853
- https://dns.cloudflare.com/dns-query
- https://cloudflare-dns.com/dns-query
- https://mozilla.cloudflare-dns.com/dns-query
- https://1.1.1.1/dns-query
- https://tor.cloudflare-dns.com 仅 Tor 可以用
- https://security.cloudflare-dns.com/dns-query 屏蔽内容

## [Google](https://developers.google.com/speed/public-dns?hl=zh-cn) (被污染)
- 8.8.8.8
- 8.8.4.4
- tls://8.8.8.8:853
- 2001:4860:4860::8888
- 2001:4860:4860::8844
- 2001:4860:4860:0:0:0:0:8888
- 2001:4860:4860:0:0:0:0:8844
- DOH
  - https://dns.google/dns-query
  - https://dns.google/resolve
- DNS64 不知道是啥请勿使用
  - dns64.dns.google
  - 2001:4860:4860::64
  - 2001:4860:4860::6464
  - 2001:4860:4860:0:0:0:0:64
  - 2001:4860:4860:0:0:0:0:6464

## [阿里 DNS](https://www.alidns.com)
### IPV4
  - 223.5.5.5
  - 223.6.6.6
### IPV6
  - 2400:3200::1
  - 2400:3200:baba::1
### DOH
  - https://dns.alidns.com/dns-query
  - https://223.5.5.5/dns-query
  - https://223.6.6.6/dns-query
### DOH JSON
  - https://dns.alidns.com/resolve
  - https://223.5.5.5/resolve
  - https://223.6.6.6/resolve

## [DNSPod](https://www.dnspod.cn/products/publicdns)
### IPV4
  - 119.29.29.29
  - 119.28.28.28
  - 182.254.116.116
### IPV6
  - 2402:4e00::
  - 2402:4e00:1::
### DOH
  - https://doh.pub/dns-query
  - https://1.12.12.12/dns-query
  - https://120.53.53.53/dns-query
### DOH 国密
  - https://sm2.doh.pub/dns-query
  - https://doh.pub
### DOT
  - dot.pub
  - 1.12.12.12
  - 120.53.53.53

## 字节跳动
### IPV4
  - 180.184.1.1
  - 180.184.2.2

## [IBM](https://www.quad9.net)
- Standard
  - 9.9.9.9
  - 149.112.112.112
  - 2620:fe::fe
  - 2620:fe::9
  - https://dns.quad9.net/dns-query
  - tls://dns.quad9.net
- Malware blocking
  - 9.9.9.11
  - 149.112.112.11
  - 2620:fe::11
  - 2620:fe::fe:11
  - https://dns11.quad9.net/dns-query
  - tls://dns11.quad9.net

## [Cisco OpenDNS](https://support.opendns.com/hc/en-us/articles/360038086532-Using-DNS-over-HTTPS-DoH-with-OpenDNS)
- 标准版
  - 208.67.222.222
  - 208.67.220.220
  - 2620:0:ccc::2
  - 2620:0:ccd::2
  - 2620:119:35::35
  - 2620:119:53::53
- 屏蔽成人内容
  - 208.67.222.123
  - 208.67.220.123
  - 2620:119:35::123
  - 2620:119:53::123
- DOH
  - doh.opendns.com
  - doh.familyshield.opendns.com 屏蔽成人内容
  - https://doh.opendns.com/dns-query
  -  https://doh.familyshield.opendns.com/dns-query

## CNNIC
  - 1.2.4.8
  - 202.98.0.68 随机出现错误地址
  - 210.2.4.8

## [360](https://sdns.360.net/dnsPublic.html)
- 101.198.198.198
- 中国电信/铁通/移动
  - 101.226.4.6
  - 218.30.118.6
- 中国联通
  - 123.125.81.6
  - 140.207.198.6
### DOH
  - https://doh.360.cn/dns-query RFC8484
  - https://doh.360.cn/query? json
  - https://doh.360.cn/resolve?
### DOH RFC8484
  - https://doh.360.cn/dns-query
### DOT
  - dot.360.cn

## [百度](https://dudns.baidu.com)
- 180.76.76.76
- 2400:da00::6666

## [信风科技](https://www.114dns.com)
- 纯净 无劫持   无需再忍受被强扭去看广告或粗俗网站之痛苦
  - 114.114.114.114
  - 114.114.115.115
- 拦截 钓鱼病毒木马网站  增强网银、证券、购物、游戏、隐私信息安全
  - 114.114.114.119
  - 114.114.115.119
- 拦截 色情网站  保护少年儿童免受网络色情内容的毒害
  - 114.114.114.110
  - 114.114.115.110

## [CFIEC Public DNS](https://www.ipv6dns.com/index) 中国下一代互联网工程中心公共DNS服务器IPv6地址
  - 240C::6666 天地互连 ipv6 dns
  - 240C::6644
  - dot
    - dns.ipv6dns.com
  - doh
    - https://dns.ipv6dns.com/dns-query

## One DNS
- 拦截版 防护各类恶意软件，过滤广告骚扰
  - 117.50.11.11
  - 52.80.66.66
  - 117.50.22.22
  - 2400:7fc0:849e:200::4
  - 2404:c2c0:85d8:901::4
- 纯净版 不对访问网站进行任何过滤拦截
  - 117.50.10.10
  - 52.80.52.52
  - 2400:7fc0:849e:200::8
  - 2404:c2c0:85d8:901::8
- 家庭版 在拦截版的基础上，增加了色情暴力、赌博站点过滤
  - 117.50.60.30
  - 52.80.60.30

## 清华大学 TUNA 协会 DNS 服务器
- 101.6.6.6
- 2001:da8::666
- 校内
  - 166.111.8.28
  - 166.111.8.29
  - 2402:f000:1:801::8:28
  - 2402:f000:1:801::8:29

## [台湾网路资讯中心公共DNS](https://101.101.101.101)
- 101.101.101.101
- 101.102.103.104
- 2001:de4::101
- 2001:de4::102

## Level3 Public DNS
- 209.244.0.3
- 209.244.0.4

## [Comodo Secure DNS](https://www.comodo.com/secure-dns/#secure-dns)
- 8.26.56.26
- 8.20.247.20

## Yandex DNS
- Basic
  - 77.88.8.8
  - 77.88.8.1
  - 2a02:6b8::feed:0ff
  - 2a02:6b8:0:1::feed:0ff
  - DOH
    - 77.88.8.8:443
  - DOT
    - 77.88.8.8:853
    - common.dot.dns.yandex.net (Private DNS for Android)
- Safe
  - 77.88.8.88
  - 77.88.8.2
  - 2a02:6b8::feed:bad
  - 2a02:6b8:0:1::feed:bad
  - DOH
    - 77.88.8.88:443
  - DOT
    - 77.88.8.88:853 (Private DNS for Android)

## [Norton DNS](https://nortondns.com)
- Basic (virus, phishing sites, and scam sites)
  - 199.85.126.10
- Safe (Basic + Pornography)
  - 199.85.126.20
- Family (Safe + Other)
  - 199.85.126.30

## [SB DNS](https://dns.sb)
- 185.222.222.222
- 45.11.45.11
- 2a09::
- 2a11::
- DOT
  - dot.sb
  - ip+853
- DOH
  - https://doh.dns.sb/dns-query
  - https://doh.sb/dns-query
  - https://45.11.45.11/dns-query
  - https://185.222.222.222/dns-query
  - https://jp-kix.doh.sb/dns-query
  - https://jp-nrt.doh.sb/dns-query
  - https://hk-hkg.doh.sb/dns-query
  - https://us-nyc.doh.sb/dns-query
  - https://sg-sin.doh.sb/dns-query
  - https://kr-sel.doh.sb/dns-query
  - and more https://dns.sb/doh/

## ~~V2EX DNS~~ 小老弟不太行 噶了
- ~~199.91.73.222~~
- ~~178.79.131.110~~