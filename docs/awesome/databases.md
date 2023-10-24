## 数据库

## 关系数据库(Relational Database Management System RDBMS)

### MYSQL (C++)
- https://www.mysql.com
- https://github.com/mysql/mysql-server
- MySQL 社区版可能是全球最受欢迎的免费开源关系型数据库

### MariaDB (C++)
- https://mariadb.org
- https://github.com/MariaDB/server
> MariaDB 是 MySQL 服务器的一个社区版本的分支。MariaDB 由 MySQL 团队的核心成员创建，积极与外部开发人员合作，提供业界最具特色、最稳定、最理智的开放 SQL 服务器。

### PostgreSQL (C)
- https://www.postgresql.org
- https://git.postgresql.org/gitweb/?p=postgresql.git
> 世界上最先进的开源关系数据库

### Microsoft SQL Server <span style="color: red;" >(收费)</span>
- https://www.microsoft.com/zh-cn/sql-server
- 由微软推出的关系数据库解决方案, `很好很大很强大`

### Firebird (C++)
- https://firebirdsql.org
- https://github.com/FirebirdSQL/firebird
> 开源跨平台的关系数据库系统，支持多版本并发控制（Multiversion Concurrency Control，MVCC）、Stored Procedure、Trigger、自定义方法（User-defined function，UDF）等商用数据库行为程序。

### SQLite (C)
- https://www.sqlite.org
- https://github.com/sqlite/sqlite
> 嵌入式轻量级开源数据库,不适合用于做并发项目

### OceanBase
- https://open.oceanbase.com
- https://github.com/oceanbase/oceanbase
- `蚂蚁集团` 旗下分布式关系型数据库 `兼容 MYSQL`
- 对硬件最低要求 2核 8G, oneman, 个人项目似乎不合适
- 文件系统支持 EXT4 戓 XFS，当数据超过 16T 时，使用 XFS

### tidb (Go)
- https://github.com/pingcap/tidb
- https://pingcap.com
- an open-source, cloud-native, distributed, MySQL-Compatible database for elastic scale and real-time analytics.

## 时间序列数据库(time series database)
### InfluxDB (Rust)
- https://www.influxdata.com/home
- https://github.com/influxdata/influxdb
> #### 专注于海量时序数据的高性能读、高性能写、高效存储与实时分析等
> 
> 一个开源的时间序列数据库开发的公司射影数据。它用于存储和检索时间序列数据，如操作监控、应用度量、物联网传感器数据和实时分析等领域。它还支持处理来自 Graphite 的数据。

## 面向文档的数据库(document-oriented database)
### CouchDB (Erlang)
- https://couchdb.apache.org
- https://github.com/apache/couchdb
> Apache 基金会旗下 NoSQL 文档存储数据库，使用JSON作为存储格式，JavaScript作为查询语言。

### MongoDB (C++)
- https://www.mongodb.com
- https://github.com/mongodb/mongo
- 一个基于分布式文件存储的开源数据库系统。
- 适用于实时的插入、更新与查询的需求，并具备应用程序实时数据存储所需的复制及高度伸缩性

## 键值对存储数据库 (Key-Value)
### LevelDB (C++)
- https://github.com/google/leveldb
- 由 `Google` 公司所研发的 键-值 存储嵌入式数据库管理系统编程库.
- 没有关系数据模型，不支持 SQL 查询，也不支持索引
- 只支持单进程，不支持多进程

### RocksDB (C++)
- http://rocksdb.org
- https://github.com/facebook/rocksdb
- A Persistent Key-Value Store for Flash and RAM Storage,Base LevelDB
- 可作为内嵌式数据库来使用，也可以作为自研数据库的底层存储引擎来使用

### Redis (C)
- https://redis.io
- https://github.com/redis/redis
- 开源、支持网络、基于内存、分布式、可选持久性的键值对存储数据库。
- 常用于缓存，事件发布或订阅，高速队列等场景。

### Memcache (C)
- https://memcached.org
- https://github.com/memcached/memcached
- 分布式的高速缓存系统
- 用于高性能内存缓存，从而降低数据访问延迟、增加吞吐量并减轻后端系统的负载。

### etcd (Go)
- https://etcd.io
- https://github.com/etcd-io/etcd
- 分布式统一键值存储
- 用于分布式系统或计算机集群的共享配置、服务发现和的调度协调。

### cockroach
- https://www.cockroachlabs.com
- https://github.com/cockroachdb/cockroach
- 云原生分布式 SQL 数据库，旨在构建、扩展和管理现代数据密集型应用程序。