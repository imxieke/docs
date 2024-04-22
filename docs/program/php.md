# PHP Standard:

## AUTOLOADING

```php
<?php

use Vendor\Package\ClassName;

$object = new ClassName();
```

## Interface

```php
<?php

namespace Psr\Log;

/**
 * Describes a logger instance
 */
interface LoggerInterface
{
```

## Style
```php
<?php

namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```


# PHP

### ThinkPHP 3.x

```php
/**
 * @param test
 */
$this->display();
$this->display('Index');
$this->display('Index/home');
$this->display("Index:home");
$this->display(":home");
$this->display("Index:" . $this->whoami);
```

#!/usr/bin/env php									//声明php脚本
@header("content-Type: text/html; charset=utf-8"); 	//语言强制
ini_set("max_execution_time", "180"); 			 	//修改php.ini配置参数
ini_get('max_execution_time');						//获取php.ini配置参数
printf_r(ini_get_all());							//获取所有ini配置参数
in_array("One",$text);								//判断 `array` 内容是否存在在
$this->name 										//此处不可以有空格存在；
$command = `pwd`; 									//执行shell命令
_FILENAME_											//显示当前文件绝对路径
getcwd()											//显示当前文件夹
dirname(_FILE_);									//显示当前文件夹
dirname(dirname(_FILENAME_))						//显示上级文件夹


```
function{
	rand(1,10); 									//随机数, var 可选
	round(var,3)									//取3位小数
}
```
function {
	functionName(arg);								//function 输出内容
}

```PHP
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
```

2016-5-17学习记录:+1:
PHP基础语法：
包括变量、常量（const）、函数、循环、控制语句、逻辑运算符；

### PHP 变量规则：
    变量以 $ 符号开始，后面跟着变量的名称
    变量名必须以字母或者下划线字符开始
    变量名只能包含字母数字字符以及下划线（A-z、0-9 和 _ ）
    变量名不能包含空格
    变量名是区分大小写的（$y 和 $Y 是两个不同的变量）

>PS: PHP 语句和 PHP 变量都是区分大小写的。

const name = value;     //define constant value;
echo name;                    //out constant;
不可再次赋值，（PHP5.5二次赋值未报错，输出源值）
print_r ：输出数组；
### Character String:
str_split($str,2,3);截取$str character string ,从第2个开始,第三个结束（可省略，直接截取到结束）；
str_explode(" ",$str);    //截取$str字符串,以 '  '（空格）为标识

### Array:
method One:

    $arr = array("0" = "Hello", "1" = "World", "h" = "hello", "w" = "world");
     //initialization array;

Two:

    $arr = array();
    $arr[0] = "Hello:
    $arr[1] = "World";
    $arr[h] = "Hello";
    $arr[w] = "World";
    print_r($arr);

require include

include:出错时会警告（warning） 但是可禁止出现；此为包含
require：会直接报错，此为依赖
require/include_once:仅加载一次

    require "lib.php";
    require "lib.php";
    会出现两次Hello World；即加载几次出现几次 但是如果加载的文件内含有function则会报错

    require_once "lib.php";
    require_once "lib.php";
    仅会出现一次 无论加载多少次
    lib.php{
    echo "Hello World";
    }

Cookie Sission:
本地直接使用，当本地禁言cookie时使用url传递参数 如？name=hello


shell_exec passthru exec
system Realtime output


simplexml_load_string(): Entity: line 2: parser error : XML declaration allowed only at the start of the document

需要检查 XML 第一行是否被其他字符占用 首行必须为 xml <?xml version="1.0" encoding="utf-8"?>

$int + 0000 = $int + 0 只会计算一个 0

# Header
```PHP
// We'll be outputting a PDF
header("Content-Type: text/html; charset=utf-8");
header('Content-Type: application/pdf');

// It will be called downloaded.pdf
header('Content-Disposition: attachment; filename="downloaded.pdf"');
header('Content-Disposition: attachment; filename=tts.mp3')

// The PDF source is in original.pdf
readfile('original.pdf');
header('WWW-Authenticate: Negotiate');
header('WWW-Authenticate: NTLM', false);
header("Location: http://www.example.com/"); /* Redirect browser */
header("HTTP/1.0 404 Not Found");
header("Cache-Control: no-cache, must-revalidate"); // HTTP/1.1
header("Expires: Sat, 26 Jul 1997 05:00:00 GMT"); // Date in the past
header("Content-Disposition: attachment; filename=" . urlencode($file));
header("Content-Type: application/force-download");
header("Content-Type: application/octet-stream");
header("Content-Type: application/download");
header("Content-Description: File Transfer");
header("Content-Length: " . filesize($file));
header("Cache-Control: no-cache");
header("Pragma: no-cache");
header('HTTP/1.0 401 Unauthorized');
header("Content-Transfer-Encoding: binary");
header('HTTP/1.1 503 Service Temporarily Unavailable');
header('Status: 503 Service Temporarily Unavailable');
header('Retry-After:1200'); //通知搜索引擎改日再来
header('X-Powered-By:IIS');//构建假的服务器版本信息

$header = "
    'Host: api.baidu.com',
    'Cookie: JSESSIONID=D867D0819902FEDFB252740315260B07',
    'DNT: 1',
    'Connection: keep-alive',
    'Pragma: no-cache',
    'Cache-Control: no-cache',
    'Upgrade-Insecure-Requests: 1',
    'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8',
    'Accept-Encoding: gzip, deflate, br',
    'Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7',
    'x-locale: en-US',
    'Referer': https://www.baidu.com'
";

```


system() 输出并返回最后一行shell结果。
exec() 不输出结果，返回最后一行shell结果，所有结果可以保存到一个返回的数组里面。
passthru() 只调用命令，把命令的运行结果原样地直接输出到标准输出设备上。



# OOP

## interface 类似拓展 插件 等等 赋予类一些功能

下面实现一个门和报警器的接口 因为门和报警器不是一个概念所以需要分开
另外 出了开和关 还可以添加锁门方法
以及报警可以添加摄像头等等方法
```php
interface Door
{
    public function open(){};
    public function close(){};
}

interface Alert
{
    public function alert(){};
    public function screen(){};
}


class Door implements Door
{
    public function open(){}
    public function close(){}
    public function alert(){}
    public function screen(){}
}

```

## interface 和 abstract 区别

interface 像是一个模板定义了一个方法可以做什么
abstrct 将类常见的方法抽离出来 无需在子类中实现即可直接调用
abstract function 除外 必须实现后才可以使用

interface 强调特定功能的实现
abstract 强调所属关系 继承关系

### Changelog
# 7.4
- 发行于2019年11月28日
- ## 特点
- 支持为类的属性声明类型
- 支持使用更简洁的箭头函数
- 支持使用…运算符展开数组或可迭代对象
- 支持使用_字符在数字字面量中添加分隔符
- 支持创建对对象的弱引用
- 支持在__toString()方法中抛出异常
- 支持在PHP启动时预加载一些脚本到共享内存中
- ## 区别
- 相比PHP 7.3，性能提升了约10%
- 相比PHP 7.3，新增了25个新特性和改进
- 相比PHP 7.3，废弃了10个功能，并移除了2个扩展

# 8.0
- 发行于 2020年11月26日
- ## 特点
- 支持使用命名参数来指定函数调用的参数名
- 支持使用属性构造器来声明类的属性和构造函数参数
- 支持使用联合类型来声明一个值可以是多种类型之一
- 支持使用匹配表达式来根据一个值的可能情况执行不同的操作
- 支持使用空安全运算符来避免空值引起的错误
- 支持使用JIT编译器来将PHP代码编译为机器码，以提高性能
- ## 区别
- 相比PHP 7.4，性能提升了约23%
- 相比PHP 7.4，新增了74个新特性和改进
- 相比PHP 7.4，废弃了24个功能，并移除了3个扩展

# 8.1
- 发行于 2021/11/25
- ## 特点
- 支持使用枚举类型来定义一组命名的常量
- 支持使用只读属性来声明一个不能被修改的属性
- 支持使用纤程来实现并发编程
- 支持使用交集类型来声明一个值必须是多种类型之一
- 支持使用never类型来表示一个函数永远不会返回
- ## 区别
- 相比PHP 8.0，性能提升了约5%
- 相比PHP 8.0，新增了39个新特性和改进
- 相比PHP 8.0，废弃了12个功能，并移除了1个扩展

# 8.2
- 发行于 2022/12/8
- ## 特点
- 计划支持使用泛型模板来声明一个参数化的类型
- 计划支持使用属性模式匹配来根据对象的属性执行不同的操作
- 计划支持使用尾递归优化来避免栈溢出错误
- 计划支持使用部分应用来创建一个预先绑定了部分参数的函数
- ## 区别

# 8.1 -> 8.2
- ### JIT 改进:
> PHP 8.2 与 PHP 8.1 相比在 JIT (Just-In-Time) 的改进方面做了很多工作。PHP 8.2 通过增加函数调用优化，以及引入更高效的内存分配和管理技术，从而提高 JIT 的性能。
- ### 强制命名参数:
> PHP 8.2 引入了强制命名参数，可以确保函数的参数传递是明确和一致的。在 PHP 8.1 中，参数是可选的，但是在 PHP 8.2 中，可以强制使用命名参数。
- ### 类的属性提升:
> PHP 8.1 引入了类属性提升语法，可以在类的定义中声明和初始化属性，而不必在构造函数中显式初始化。PHP 8.2 对此进行了优化，使得属性提升语法更加方便和灵活。
- ### 优化的字符串函数:
>PHP 8.2 通过优化字符串函数，如 str_contains、str_starts_with 和 str_ends_with 等，提高了字符串处理的性能。
- ### 新增一些函数
>PHP 8.2 引入了一些新函数，如 array_is_list、fdiv 和 fmod，以及更多的 HTTP 相关函数，如 http_parse_cookie 和 http_build_cookie。

# 8.0 -> 8.1
- ### 性能提升
>PHP 8.0和8.1都引入了新的JIT编译器，它可以将PHP代码转换成更快的机器码，从而提高性能。在PHP 8.1中，JIT编译器有了更多的优化，因此它可以进一步提高性能。

- ### 类型系统
> PHP 8.0引入了静态类型，这意味着您可以在编写代码时显式指定变量类型，从而提高代码的可读性和可维护性。PHP 8.1增加了类型别名，这使得在代码中使用更复杂的类型变得更加容易。

- ### 异常处理
> PHP 8.0引入了新的异常类型，这使得在处理错误时更加灵活。PHP 8.1增加了try语句的新功能，使其更加灵活和易于使用。

- ### 其他特性
> PHP 8.1增加了一些新的语言特性，如Union Types、Read-Only Properties和New in Initializers等。这些特性使得编写PHP代码更加容易和灵活。