# Shell

文件表达式
-e filename 如果 filename存在，则为真
-d filename 如果 filename为目录，则为真
-f filename 如果 filename为常规文件，则为真
-L filename 如果 filename为符号链接，则为真
-r filename 如果 filename可读，则为真
-w filename 如果 filename可写，则为真
-x filename 如果 filename可执行，则为真
-s filename 如果文件长度不为0，则为真
-h filename 如果文件是软链接，则为真
filename1 -nt filename2 如果 filename1比 filename2新，则为真。
filename1 -ot filename2 如果 filename1比 filename2旧，则为真。


整数变量表达式
-eq 等于
-ne 不等于
-gt 大于
-ge 大于等于
-lt 小于
-le 小于等于


字符串变量表达式
If  [ $a = $b ]                 如果string1等于string2，则为真
                                字符串允许使用赋值号做等号
if  [ $string1 !=  $string2 ]   如果string1不等于string2，则为真
if  [ -n $string  ]             如果string 非空(非0），返回0(true)
if  [ -z $string  ]             如果string 为空，则为真
if  [ $sting ]                  如果string 非空，返回0 (和-n类似)


    逻辑非 !                   条件表达式的相反
if [ ! 表达式 ]
if [ ! -d $num ]               如果不存在目录$num


    逻辑与 –a                   条件表达式的并列
if [ 表达式1  –a  表达式2 ]


    逻辑或 -o                   条件表达式的或
if [ 表达式1  –o 表达式2 ]

### if
if [ -f  file ]    			如果文件存在
if [ -d ...   ]    			如果目录存在
if [ -s file  ]    			如果文件存在且非空
if [ -r file  ]    			如果文件存在且可读
if [ -w file  ]   			如果文件存在且可写
if [ -x file  ]    			如果文件存在且可执行
if [-z string ]    			string 的长度为零
if [ int1 -eq int2 ]    	如果int1等于int2
if [ int1 -ne int2 ]    	如果不等于
if [ int1 -ge int2 ]       	如果>=
if [ int1 -gt int2 ]       	如果>
if [ int1 -le int2 ]       	如果<=
if [ int1 -lt int2 ]       	如果<

变量说明:
$$ Shell本身的PID（ProcessID）
$! Shell最后运行的后台Process的PID
$? 最后运行的命令的结束代码（返回值）
$- 使用Set命令设定的Flag一览
$* 所有参数列表。如"$*"用「"」括起来的情况、以"$1 $2 … $n"的形式输出所有参数。
$@ 所有参数列表。如"$@"用「"」括起来的情况、以"$1" "$2" … "$n" 的形式输出所有参数。
$# 添加到Shell的参数个数
$0 Shell本身的文件名
$1～$n 添加到Shell的各参数值。$1是第1参数、$2是第2参数…。

#### Study Address：http://c.biancheng.net/cpp/shell/
### 简介：
    Shell为解析型语言，称之为脚本语言（Shell Script Lang），执行这类程序时，解释器(interpreter)需要读取我们编写的源代码(source code)，
    并将其转换成目标代码(object code)，再由计算机运行。

# 特点：
            简单、可移植、简单；

## 不适合使用的用途：
    考虑到Shell脚本的命令限制和效率问题，下列情况一般不使用Shell：
    资源密集型的任务，尤其在需要考虑效率时（比如，排序，hash等等）。
    需要处理大任务的数学操作，尤其是浮点运算，精确运算，或者复杂的算术运算（这种情况一般使用C++或FORTRAN 来处理）。
    有跨平台（操作系统）移植需求（一般使用C 或Java）。
    复杂的应用，在必须使用结构化编程的时候（需要变量的类型检查，函数原型，等等）。
    对于影响系统全局性的关键任务应用。
    对于安全有很高要求的任务，比如你需要一个健壮的系统来防止入侵、破解、恶意破坏等等。
    项目由连串的依赖的各个部分组成。
    需要大规模的文件操作。
    需要多维数组的支持。
    需要数据结构的支持，比如链表或数等数据结构。
    需要产生或操作图形化界面 GUI。
    需要直接操作系统硬件。
    需要 I/O 或socket 接口。
    需要使用库或者遗留下来的老代码的接口。
    私人的、闭源的应用（shell 脚本把代码就放在文本文件中，全世界都能看到）。
# 注意
    如果你的应用符合上边的任意一条，那么就考虑一下更强大的语言吧——或许是Perl、Tcl、Python、Ruby；
    或者是更高层次的编译语言比如C/C++，或者是Java。即使如此，你会发现，使用shell来原型开发你的应用，在开发步骤中也是非常有用的。

Example
```shell
# Author:Xiaoke
# mail:  im@xieke.org
# Blog:  http://blog.xiaoke.org

#!/bin/bash
echo "What is your name?"
read PERSON             #从此处获得输入值
echo "Hello, $PERSON"   #此处获得值后输出
```

touch hello.sh
chmod +x *.sh     //All Script Jurisdiction Execuitve
./hello.sh

# 定义变量

首个字符必须为字母（a-z，A-Z）。
中间不能有空格，可以使用下划线（_）。
不能使用标点符号。
不能使用bash里的关键字（可用help命令查看保留关键字）。
变量名只能包含数字、字母和下划线，因为某些包含其他字符的变量有特殊含义，这样的变量被称为特殊变量。

使用：只需在变量名前加$(美元)符号即可！

    xiaoke="is my name"  #不可出现空格
    echo "$xiaoke"             #""不是必须的，建议加入
    echo  {$xiaoke}             #{}花括号是为了方便识别

# 二次定义变量（重新定义）：

    xiaoke="My Name!"
    echo "${xiaoke}"

此处值会变动,如果重新定义的多个变量在一起，重新定义的变量应放在前一个变量与后一个变量之间；
如：

    xiaoke="is my name"
    xiaoke="My Name!"
    xiaoke="My Name Is Xiaoke!"
    echo "$xiaoke"
    echo "{$xiaoke}"
    echo "$xiaoke"

输出的则是最后一个变量xiaoke的值！

# 只读变量
使用 readonly 命令可以将变量定义为只读变量，只读变量的**值不能被改变**。

    xiaoke="My Name!"
    readonly xiaoke
    xiaoke="Xiaoke's Name"
    echo $xiaoke

则会输出：hello.sh: 16: hello.sh: xiaoke: is read only

# 删除变量

使用 unset 命令仅可以删除可读变量，变量被删除后不能再次使用，且输出的为空值，unset local set!
语法：

    unset xiaoke

如：

    xiaoke="My Name"
    unset xiaoke                    #值在此处被删除，echo获取的为空值！
    echo xiaoke

返回的是空值！

# 变量类型

运行shell时，会同时存在三种变量：
1) 局部变量
        局部变量在脚本或命令中定义，仅在当前shell实例中有效，其他shell启动的程序不能访问局部变量。
2) 环境变量
        所有的程序，包括shell启动的程序，都能访问环境变量，有些程序需要环境变量来保证其正常运行。必要的时候shell脚本也可以定义环境变量。
3) shell变量
        shell变量是由shell程序设置的特殊变量。shell变量中有一部分是环境变量，有一部分是局部变量，这些变量保证了shell的正常运行

# 特殊变量：Shell $0, $#, $*, $@, $?, $$和命令行参数
-------------------------------------------------------------------------------------------------------------------------------------------
特殊变量列表：
变量	含义
$0	当前脚本的文件名
$n	传递给脚本或函数的参数。n 是一个数字，表示第几个参数。例如，第一个参数是$1，第二个参数是$2。
$#	传递给脚本或函数的参数个数。
$*	传递给脚本或函数的所有参数。
$@	传递给脚本或函数的所有参数。被双引号(" ")包含时，与 $* 稍有不同，下面将会讲到。
$?	上个命令的退出状态，或函数的返回值。
$$	当前Shell进程ID。对于 Shell 脚本，就是这些脚本所在的进程ID。
---------------------------------------------------------------------------------------------------------------------------------------------

$* 和 $@ 的区别
$* 和 $@ 都表示传递给函数或脚本的所有参数，不被双引号(" ")包含时，都以"$1" "$2" … "$n" 的形式输出所有参数。
但是当它们被双引号(" ")包含时：
"$*" 会将所有的参数作为一个整体，以"$1 $2 … $n"的形式输出所有参数；
"$@" 会将各个参数分开，以"$1" "$2" … "$n" 的形式输出所有参数。


# Shell变量替换，命令替换，转义字符
    PS、必须是命令 如date、time apt-get update 不允许出现非命令字符
       `Command` 例：DATE=`sudo apt-get update`     echo "$DATE" //尽量大写

# 转义字符	含义
    \\	反斜杠
    \a	警报，响铃
    \b	退格（删除键）
    \f	换页(FF)，将当前位置移到下页开头
    \n	换行
    \r	回车
    \t	水平制表符（tab键）
    \v	垂直制表符


变量替换

    变量替换可以根据变量的状态（是否为空、是否定义等）来改变它的值

可以使用的变量替换形式：
形式	说明

    ${var}	变量本来的值
    ${var:-word}	如果变量 var 为空或已被删除(unset)，那么返回 word，但不改变 var 的值。
    ${var:=word}	如果变量 var 为空或已被删除(unset)，那么返回 word，并将 var 的值设置为 word。
    ${var:?message}	如果变量 var 为空或已被删除(unset)，那么将消息 message 送到标准错误输出，可以用来检测变量 var 是否可以被正常赋值。
    若此替换出现在Shell脚本中，那么脚本将停止运行。
    ${var:+word}	如果变量 var 被定义，那么返回 word，但不改变 var 的值。


运算符	说明	举例

    +	加法	`expr $a + $b` 结果为 30。
    -	减法	`expr $a - $b` 结果为 10。
    *	乘法	`expr $a \* $b` 结果为  200。
    /	除法	`expr $b / $a` 结果为 2。
    %	取余	`expr $b % $a` 结果为 0。
    =	赋值	a=$b 将把变量 b 的值赋给 a。
    ==	相等。用于比较两个数字，相同则返回 true。	[ $a == $b ] 返回 false。
    !=	不相等。用于比较两个数字，不相同则返回 true。	[ $a != $b ] 返回 true。

   条件表达式
文件表达式
if [ -f  file ]    如果文件存在
if [ -d ...   ]    如果目录存在
if [ -s file  ]    如果文件存在且非空
if [ -r file  ]    如果文件存在且可读
if [ -w file  ]    如果文件存在且可写
if [ -x file  ]    如果文件存在且可执行
整数变量表达式
if [ int1 -eq int2 ]    如果int1等于int2
if [ int1 -ne int2 ]    如果不等于
if [ int1 -ge int2 ]       如果>=
if [ int1 -gt int2 ]       如果>
if [ int1 -le int2 ]       如果<=
if [ int1 -lt int2 ]       如果<

字符串变量表达式
```
If  [ $a = $b ]                 如果string1等于string2
                                字符串允许使用赋值号做等号
if  [ $string1 !=  $string2 ]   如果string1不等于string2
if  [ -n $string  ]             如果string 非空(非0），返回0(true)
if  [ -z $string  ]             如果string 为空
if  [ $sting ]                  如果string 非空，返回0 (和-n类似)
$0 这个程式的执行名字
$n 这个程式的第n个参数值，n=1..9
$* 这个程式的所有参数,此选项参数可超过9个。
$# 这个程式的参数个数
$$ 这个程式的PID(脚本运行的当前进程ID号)
$! 执行上一个背景指令的PID(后台运行的最后一个进程的进程ID号)
$? 执行上一个指令的返回值 (显示最后命令的退出状态。0表示没有错误，其他任何值表明有错误)
$- 显示shell使用的当前选项，与set命令功能相同
$@ 跟$*类似，但是可以当作数组用
```


auto double int struct break else long switch case enum register
typedef char extern return union const float short unsigned continue
for signed void default goto sizeof volatile do if while static

float a = 1/3.0f
printf("%.10f",c); //%.10f 表示输出10位小数
scanf("%d \t %s \n",&a,&b);
printf("%p\n",&a );			变量的内存地址
printf("%s %d",a,&b);  //string need to add `&`
file --> internet --> memory -> disk
file -> disk -> memory -> display
from static data to dynamic data conversion
negative Conversion Hex:正常转换，取反+1

Hex Conversion:
Hex input Standard:
Binary:		0b01 = 1
Octonary:	0001 = 1
Decimal:	1	 = 1
HexaDecimal:0x01 = 1

a 'a' "a" /变量 /字符 /字符串
char a = 65; printf("%c \n",a); //直接输出Ascll控制符
char a = '6'; printf("%d",a);	//直接输出ascll 值

shell脚本字符串截取的8种方法
假设有变量 var=http://www.aaa.com/123.htm.

1. # 号截取，删除左边字符，保留右边字符。

1
echo ${var#*//}
 其中 var 是变量名，# 号是运算符，*// 表示从左边开始删除第一个 // 号及左边的所有字符
即删除 http://
结果是 ：www.aaa.com/123.htm

2. ## 号截取，删除左边字符，保留右边字符。

1
echo ${var##*/}


##*/ 表示从左边开始删除最后（最右边）一个 / 号及左边的所有字符
即删除 http://www.aaa.com/

结果是 123.htm

3. %号截取，删除右边字符，保留左边字符

1
echo ${var%/*}


%/* 表示从右边开始，删除第一个 / 号及右边的字符

结果是：http://www.aaa.com

4. %% 号截取，删除右边字符，保留左边字符

1
echo ${var%%/*}
 %%/* 表示从右边开始，删除最后（最左边）一个 / 号及右边的字符
结果是：http:

5. 从左边第几个字符开始，及字符的个数

1
echo ${var:0:5}


其中的 0 表示左边第一个字符开始，5 表示字符的总个数。
结果是：http:

6. 从左边第几个字符开始，一直到结束。

1
echo ${var:7}


其中的 7 表示左边第8个字符开始，一直到结束。
结果是 ：www.aaa.com/123.htm

7. 从右边第几个字符开始，及字符的个数

1
echo ${var:0-7:3}


其中的 0-7 表示右边算起第七个字符开始，3 表示字符的个数。
结果是：123

8. 从右边第几个字符开始，一直到结束。

1
echo ${var:0-7}


表示从右边第七个字符开始，一直到结束。
结果是：123.htm

注：（左边的第一个字符是用 0 表示，右边的第一个字符用 0-1 表示）


## 删除传入的第一个参数
```shell
echo $@
shift # 删除第一个参数 后面自动前移
echo "${@:2}" # 从第二个开始输出 同样可以实现删除第一个参数
```