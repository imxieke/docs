# Laravel

### Statement：
Declaretion:

    **Hello World**     //black
    //Hello World        //black
    --Hello World--    //green
    'Hello World'        //red

方法: 类中的函数
函数 可全局直接使用

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

### & (引用) ：不同的名字访问同一个变量内容。
>Ref: https://www.cnblogs.com/gengyi/p/6399752.html
```php
$a="ABC";
$b =&$a;
echo $a;//这里输出:ABC
echo $b;//这里输出:ABC
$b="EFG";
echo $a;//这里$a的值变为EFG 所以输出EFG
echo $b;//这里输出EFG
```