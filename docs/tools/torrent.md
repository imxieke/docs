- 经过了Napster到Gnutella到BitTorrent三代的P2P技术的发展才渐进成熟
- DHT全称为分布式哈希表（Distributed Hash Table）
- DHT网络是Tracker-less的，不依赖于其他的Tracker服务器
- `urn`为统一资源名称，`btih` 是BitTorrent Info Hash的缩写，是BitTorrent使用的Hash函数。
- 磁力链接的下载原理其实就是先根据磁力链接获取种子文件
- Peer:”peer”节点实现了BT协议，使用TCP协议，用于资源文件的传输；
- node:”node”节点用于实现DHT协议，使用UDP协议，用于节点的路由管理和资源位置的查询。
- 基于 HTTP 的 Tracker 协议
- 基于 UDP 的 Trackerless 协议
- 基于 TCP 的 Peer wire 协议。

## Download Site info list
- name 
- size 分为单个和全部文件总大小
- Seeders 下载节点
- Leechers 似乎是已经下载次数
- Time 创建时间
- Source 来源
- Updated
- Hashinfo 哈希值
- Keywords(后期生成) 种子信息 
- Magnet `magnet:?xt=urn:btih:` 地址
- .Torrent 下载地址
- File list 文件列表 含单个与全部文件大小
- Trackers trackers 列表

### bootstrap node DHT 服务器 udp
- router.bittorrent.com 6881 √
- router.utorrent.com √
- router.bitcomet.com x Blocked by GFW
- dht.transmissionbt.com √ slow 

magnet:?xt=urn:btih:85f8b869e6ff1d6757a9f6ed91555a640f155647&dn=3D.Naked.Ambition.2014.720p.HDRip.x264.AC3-SmY&xl=1732355474&tr=http://tracker.prq.to/announce

magnet:?xt=urn:btih:c571747dd7629c2fadeefe9b37e8109f7f9eb9e3&dn=%EF%BC%88%E6%89%93%E9%A3%9E%E6%9C%BA%E5%BF%85%E5%A4%87%E9%BB%91%E4%B8%9D%E5%A5%B3%EF%BC%89%E5%A4%A7%E6%88%98%E9%BB%91%E4%B8%9D%E7%BE%8E%E5%A5%B3.mp4&tr=udp://tracker.openbittorrent.com:80&tr=udp://tracker.opentrackr.org:1337/announce

udp://tracker.opentrackr.org:1337/announce

http://itorrents.org/torrent/645BCFD64B223511F476FCBDADFA90E73F0FCB84.torrent
https://btdb.eu/tfiles/640fe84c613c17f663551d218689a64e8aebeabe.torrent
https://btdb.eu/dl/64/640fe84c613c17f663551d218689a64e8aebeabe.torrent
https://www.seedpeer.me/torrent/640fe84c613c17f663551d218689a64e8aebeabe

## btdb.eu data
(hash|name|category|link|link to download|)
Total export, updated every 3 days, [fulldump2.txt.gz](https://btdb.eu/api/fulldump2.txt.gz) (1.44 GB)
Export with last day torrents, updated every 1 hour, [hourly.txt.gz](https://btdb.eu/api/hourly.txt.gz) (1 MB)
## TorrentGalaxy's data
Download TorrentGalaxy's last 24h torrent data dump
(Updated hourly)
[tgx24hdump.txt.gz](https://torrentgalaxy.to/cache/tgx24hdump.txt.gz)