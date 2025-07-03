# MYSQL

## MYSQL 优化

## 避免使用select *

很多时候，我们写sql语句时，为了方便，喜欢直接使用select *，一次性查出表中所有列的数据。

### 反例：

`select * from user where id=1;`
在实际业务场景中，可能我们真正需要使用的只有其中一两列。查了很多数据，但是不用，白白浪费了数据库资源，比如：内存或者cpu。

此外，多查出来的数据，通过网络IO传输的过程中，也会增加数据传输的时间。

还有一个最重要的问题是：`select *`不会走`覆盖索引`，会出现大量的`回表`操作，而从导致查询sql的性能很低。

那么，如何优化呢？

### 正例：

`select name,age from user where id=1;`

sql语句查询时，只查需要用到的列，多余的列根本无需查出来。

# Change Password
在MySQL 5.7 password字段已从mysql.user表中删除，新的字段名是

`authenticalion_string`

选择数据库：

`use mysql;`

更新root的密码：

`update user set authentication_string=password('新密码') where user='root' and Host='localhost';`

刷新权限：`flush privileges;`

## 忘记密码
```bash
mysqld --defaults-file="/etc/mysql/my.ini" --skip-grant-tables
mysql -u root 无需输入密码
update mysql.user set authentication_string = password('123456') where
user='root';
flush privileges;
```

## 快速导入数据库
```sql
  # 关闭日志
  set sql_log_bin=OFF;
  # 关闭autocommit自动提交模式
  set autocommit=0;
  START TRANSACTION;
  source xxx.sql
  COMMIT;
```

## 运维常用命令
```
查看当前最大连接数
show variables like '%max_connection%';
重新设置最大连接数
set global max_connections=1000;
所有用户的当前连接前 100 条
show processlist;
全列出请使用
show full processlist;
```

### 查看变量
`mysql>show status like '%变量名%';`

### 变量名如下：
Aborted_clients 由于客户没有正确关闭连接已经死掉，已经放弃的连接数量。
Aborted_connects 尝试已经失败的MySQL服务器的连接的次数。
Connections 试图连接MySQL服务器的次数。
Created_tmp_tables 当执行语句时，已经被创造了的隐含临时表的数量。
Delayed_insert_threads 正在使用的延迟插入处理器线程的数量。
Delayed_writes 用INSERT DELAYED写入的行数。
Delayed_errors 用INSERT DELAYED写入的发生某些错误(可能重复键值)的行数。
Flush_commands 执行FLUSH命令的次数。
Handler_delete 请求从一张表中删除行的次数。
Handler_read_first 请求读入表中第一行的次数。
Handler_read_key 请求数字基于键读行。
Handler_read_next 请求读入基于一个键的一行的次数。
Handler_read_rnd 请求读入基于一个固定位置的一行的次数。
Handler_update 请求更新表中一行的次数。
Handler_write 请求向表中插入一行的次数。
Key_blocks_used 用于关键字缓存的块的数量。
Key_read_requests 请求从缓存读入一个键值的次数。
Key_reads 从磁盘物理读入一个键值的次数。
Key_write_requests 请求将一个关键字块写入缓存次数。
Key_writes 将一个键值块物理写入磁盘的次数。
Max_used_connections 同时使用的连接的最大数目。
Not_flushed_key_blocks 在键缓存中已经改变但是还没被清空到磁盘上的键块。
Not_flushed_delayed_rows 在INSERT DELAY队列中等待写入的行的数量。
Open_tables 打开表的数量。
Open_files 打开文件的数量。
Open_streams 打开流的数量(主要用于日志记载）
Opened_tables 已经打开的表的数量。
Questions 发往服务器的查询的数量。
Slow_queries 要花超过long_query_time时间的查询数量。
Threads_connected 当前打开的连接的数量。
Threads_running 不在睡眠的线程数量。
Uptime 服务器工作了多长时间，单位秒。


```MYSQL
CREATE TABLE ethereum (
    `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
    `field1` text COLLATE utf8_unicode_ci NOT NULL COMMENT '字段1',
    `field2` varchar(128) COLLATE utf8_unicode_ci NOT NULL DEFAULT  '' COMMENT '字段2',
    PRIMARY KEY (`id`)
)ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLILATE=utf8_unicode_ci;
```

mysql中有utf8和utf8mb4两种编码，在mysql中请大家忘记**utf8**，永远使用**utf8mb4**。这是mysql的一个遗留问题，mysql中的utf8最多只能支持3bytes长度的字符编码，对于一些需要占据4bytes的文字，mysql的utf8就不支持了，要使用utf8mb4才行

# MYSQL

### LIMIT
```MYSQL
SELECT * FROM TABLENAME LIMIT 1; QUERY First field
SELECT * FROM TABLENAME LIMIT 2,5; Query 3 - 7, first param is start(times+1 , start in zero(0)) second param is times,
SELECT * FROM TABLENAME LIMIT 3 OFFSET 1 ,Query 3 fields ,right offset 1 unit,  start with 1 (0 + 1)
```

# SQL
```SQL
CREATE TABLE `wb_blog` (
   `id` smallint(8) unsigned NOT NULL,
  `catid` smallint(5) unsigned NOT NULL DEFAULT '0',
   `title` varchar(80) NOT NULL DEFAULT '',
   `content` text NOT NULL,
   PRIMARY KEY (`id`),
  )
```

```SQL
CREATE TABLE `wb_blog` (
	`id` smallint(8) unsigned NOT NULL,
	`catid` smallint(5) unsigned NOT NULL DEFAULT '0',
	`title` varchar(80) NOT NULL DEFAULT '',
	`content` text NOT NULL,
	PRIMARY KEY (`id`),
	UNIQUE KEY `catename` (`catid`)
);
```
CREATE UNIQUE INDEX catename ON wb_blog(catid)
ALTER TABLE wb_blog DROP INDEX catename;
alter table user add unique index(user_id,user_name);

注意

唯一索引。

它与前面的"普通索引"类似，不同的就是：索引列的值必须唯一，但允许有空值。如果是组合索引，则列值的组合必须唯一。它有以下几种创建方式：
（1）创建索引：CREATE UNIQUE INDEX indexName ON tableName(tableColumns(length))
（2）修改表结构：ALTER tableName ADD UNIQUE [indexName] ON (tableColumns(length))
（3）创建表的时候直接指定：CREATE TABLE tableName ( [...], UNIQUE [indexName](tableColumns(length));

3.主键索引

它是一种特殊的唯一索引，不允许有空值。一般是在建表的时候同时创建主键索引：CREATE TABLE testIndex(i_testID INT NOT NULL AUTO_INCREMENT,vc_Name VARCHAR(16) NOT NULL,PRIMARY KEY(i_testID)); 当然也可以用ALTER命令。

关于<meta NAME="keywords" CONTENT="">
昨天终于以实习身份入职一家小创业公司，今天让我多看看别人的网页怎么写的，发现了一个以前都没关注过的东西。

<meta name="keywords" content="XX_XX_XXX"/>
在百度上搜索了一下，看到了一篇详细介绍如下：

 META标签是HTML语言HEAD区的一个辅助性标签，它位于HTML文档头部的`<HEAD>`标记和`<TITLE>`标记之间，它提供用户不可见的信息。meta标签通常用来为搜索引擎robots定义页面主题，或者是定义用户浏览器上的cookie；它可以用于鉴别作者，设定页面格式，标注内容提要和关键字；还可以设置页面使其可以根据你定义的时间间隔刷新自己,以及设置RASC内容等级，等等。

　　name是描述网页的，对应于Content（网页内容），以便于搜索引擎机器人查找、分类（目前几乎所有的搜索引擎都使用网上机器人自动查找meta值来给网页分类）。
　　name的value值（name=""）指定所提供信息的类型。有些值是已经定义好的。例如description(说明)、keyword(关键字)、refresh(刷新)等。还可以指定其他任意值，如：creationdate(创建日期) 、
document ID(文档编号)和level(等级)等。
　　name的content指定实际内容。如：如果指定level(等级)为value(值)，则Content可能是beginner(初级)、intermediate(中级)、advanced(高级)。

　　1、Keywords (关键字)
　　　说明：为搜索引擎提供的关键字列表
　　　用法：<Meta name="Keywords" Content="关键词1,关键词2，关键词3,关键词4,……">
　　　注意：各关键词间用英文逗号“,”隔开。META的通常用处是指定搜索引擎用来提高搜索质量的关键词。当数个META元素提供文档语言从属信息时，搜索引擎会使用lang特性来过滤并通过用户的语言优先参照来显示搜索结果。例如：
　　　　　　<Meta name="Kyewords" Lang="EN" Content="vacation,greece,sunshine">
　　　　　　<Meta name="Kyewords" Lang="FR" Content="vacances,grè:ce,soleil">

　　2、Description (简介)
　　　说明：Description用来告诉搜索引擎你的网站主要内容。
　　　用法：<Meta name="Description" Content="你网页的简述">
　　　注意：

　　3、Robots (机器人向导)
　　　说明：Robots用来告诉搜索机器人哪些页面需要索引，哪些页面不需要索引。Content的参数有all、none、index、noindex、follow、nofollow。默认是all。
　　　用法：<Meta name="Robots" Content="All|None|Index|Noindex|Follow|Nofollow">
　　　注意：许多搜索引擎都通过放出robot/spider搜索来登录网站，这些robot/spider就要用到meta元素的一些特性来决定怎样登录。

　　　 all：文件将被检索，且页面上的链接可以被查询；
　　　 none：文件将不被检索，且页面上的链接不可以被查询；(和 "noindex, no follow" 起相同作用)
　　　 index：文件将被检索；（让robot/spider登录）
　　　 follow：页面上的链接可以被查询；
　　　 noindex：文件将不被检索，但页面上的链接可以被查询；(不让robot/spider登录)
　　　nofollow：文件将不被检索，页面上的链接可以被查询。(不让robot/spider顺着此页的连接往下探找)

　　4、Author (作者)
　　　说明：标注网页的作者或制作组
　　　用法：<Meta name="Author" Content="张三，abc@sina.com">
　　　注意：Content可以是：你或你的制作组的名字,或Email

　　5、Copyright (版权)
　　　说明：标注版权
　　　用法：<Meta name="Copyright" Content="本页版权归Zerospace所有。All Rights Reserved">
　　　注意：

　　6、Generator (编辑器)
　　　说明：编辑器的说明
　　　用法：<Meta name="Generator" Content="PCDATA|FrontPage|">
　　　注意：Content="你所用编辑器"

　　7、revisit-after (重访)
　　　说明：
　　　用法：<META name="revisit-after" CONTENT="7 days" >


### Statement：
Declaretion:

    **Hello World**     //black
    //Hello World        //black
    --Hello World--    //green
    'Hello World'        //red

### **--创建数据库** 顺序：
--CreateDB->DBNAME->FileSize->FileMaxSize->Filegrowth;
create database xiaoke
on(
name='xiaoke',						--定义逻辑名称
filename='C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\DATA\xiaoke.mdf',--定义物理名称/路径
size=3mb,							--定义初始大小
maxsize=50mb,						--定义最大值
filegrowth=10%)						--定义每次增长值 可为 num% or xmb
log on(
name='xiaoke_log',
filename='C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\DATA\xiaoke.ldf',
size=1mb,
maxsize=10mb,
filegrowth=1mb)

**修改数据库student文件相关参数**
alter database xiaoke
modify file(
name='xiaoke',
filename='C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\DATA\xk.mdf',	--定义主文件路径文件名
size=5MB,
maxsize=unlimited,																--文件的最大空间不受限制
filegrowth=10%)

**修改数据库student日志文件相关参数**
alter database xiaoke
modify file(
name='xiaoke_log',
filename='C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\DATA\stu_log.ldf',--定义日志文件路径文件名
size=3MB,
maxsize=unlimited,
filegrowth=3MB
)
--create database xiaoke			创建数据库xiaoke
--drop database xiaoke				终止数据库xiaoke
--sp_renamedb 'xiaoke','xk'
--sp_renamedb 'xk','xiaoke'			更改##数据库逻辑名称
--sp_databases					查看当前用户下所有数据库
--use xiaoke						将###切换为当前数据库
--sp_helpfile						查看当前数据库信息、
--sp_helpdb						查看当前用户下所有数据库详细信息
--sp_helpdb xiaoke				查看指定数据库的详细信息
 ![图片](https://dn-coding-net-production-pp.qbox.me/25a29ae1-dd5d-4bd4-b7a8-a6fcefa1b733.JPG)

**新建表stu_info**
create table tablename(
columnname char(50) primary key not null,
变值使用varchar，如姓名、地址，非变值使用char（定值）；
primary key主键，每个表必有且仅有一个；
not null（不为空）
每句结尾必须添加,最后一句不加将）移动至结尾最后一个字符前)
 ![图片](https://dn-coding-net-production-pp.qbox.me/9d9c9365-98d0-41e2-8e82-d8ee67ff7469.png)

**修改表stu_info字段名:stu_id 改为：stuid**
sp_rename 'stu_info.[stu_id]','stuid'

删除及修改需添加column，增加命令无需添加column；
alter table config
add tel char(11) not null  //在插入列后，如打开未修改的表将无法保存数据，按住esc键取消重新打开
alter column tel char(14) not null
drop column config

char，varchar	最多8000个英文，4000个汉字
nchar，nvarchar	可存储4000个字符，无论英文还是汉字

mysql -u root -p //login to mysql server.
select * from table;
create database dbname;
alter table user add name varchar(64); //add new fields to tables
alter table user change old_name new_name varchar(32); change table

close PDO Connection:
{
    $connect->close();          //Object-oriented
    mysqli_close($connect);     //instance
    $connect = null;            //PDO
}

## 数据恢复

```shell
# must be root user
mysqlbinlog --start-datetime="2020-03-20 10:00:00" --stop-datetime="2024-05-27 10:54:00" mysql-bin.000001 | mysql -uroot -p demo

```

## 数字类型
- UNSIGNED 无符号数，如果不加这个标识，则为有符号数
- ZEROFILL补零标识，如果有这个标识，会自动给类型增加 UNSIGNED 标识

## tinyint smallint int bigint 区别

### tinyint
- 从 -2^7 (-128) 到 2^7 - 1 (123) 的整型数据。存储大小为 1 个字节
- unsigned 是从 0 到 255 的整型数据
- 最大值 `tinyint(3)` 超过无效 也不会存储

### smallint
- 从 -2^15 (-32,768) 到 2^15 - 1 (32,767) 的整型数据。存储大小为 2 个字节。
- unsigned 是从 0 到 65535 的整型数据。
- 最大值 `smallint(5)`

### mediumint
- 从 -8388608 到 8388607 无符号为 0, 16777215 存储大小为3字节
- - 最大值 `mediumint(8)`

### int
- 从 -2^31 (-2,147,483,648) 到 2^31 - 1 (2,147,483,647) 的整型数据（所有数字）.存储大小为 4 个字节。
- unsigned 是从 0 到 4294967296 的整型数据。
- 最大值 `int(10)`

### bigint
- 从 -2^63 (-9,223,372,036,854,775,808) 到 2^63-1 (9,223,372,036,854,775,807) 的整型数据（所有数字）。存储大小为 8 个字节。
- unsigned 是(自己算吧)
- 最大值 `bigint(20)`

### float 2^128
### double 2^1024

## 快捷预览

|类型|最小值(有符号/无符号)|最大值(有符号/无符号)|字节|
|-|-|-|-|
|tinyint|-2^7(-128)/0|2^7(128)/255|1|
|smallint|-2^15 (-32,768)/0|2^15 - 1 (32,767)/65535|2|
|mediumint|-2^23(-8388608)/0|2^23(8388607)/16777215|3|
|int|-2^31 (-2,147,483,648)/0|2^31 - 1 (2,147,483,647)/4294967296|4|
|bigint|-2^63 (-9,223,372,036,854,775,808)/0|9223372036854775807 / 18446744073709551615|8|



## 修改 sql_mode

### 查看现在的 sql_mode
`SELECT @@sql_mode;`



## MYSQL 自增 ID 重置
`ALTER TABLE table_name AUTO_INCREMENT = 1;`


## 字符集
- utf8mb4 是 utf8(utf8mb3) 的超集, 完全兼容它

- `utf8mb4_general_cs`
- `utf8mb4_unicode_ci`
  - 存储超出 utf8mb3 范围的字符，如某些不常用的汉字和新增的 Unicode 字符。
  - 存储 emoji 表情，这些表情需要四字节的编码。
  - 确保数据库能够支持国际化应用，处理各种语言和特殊字符 。

- `utf8mb4_0900_ai_ci`


### 字段说明
- `ai` 指的是口音不敏感。也就是说，排序时 `e，è，é，ê` 和 `ë` 之间没有区别
- `ci case insensitiv` 表示不区分大小写。也就是说，排序时 `p` 和 `P` 之间没有区别
- `cs case sensitive` 的缩写，即大小写敏感。[mysql 5.7 之后取消了这个]