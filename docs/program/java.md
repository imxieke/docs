# Java

Java编程规范：
参考： http://www.hawstein.com/posts/google-java-style.html
关键字：（区分大小写）
![关键字i](http://img.mukewang.com/53588ce900019bee05190178.jpg)
标识符：
由字母、数字（不可作为首字符）、下划线（_）、美元符（$）组成，第一个单词的首字母小写，其后单词的首字母大写，俗称骆驼式命名法（也称驼峰命名法），长度无限制。
### Java中的数据类型![Java中的数据类型][1]

>>在 Java 的领域里，基本数据类型变量存的是数据本身，而引用类型变量存的是保存数据的空间地址。说白了，基本数据类型变量里存储的是直接放在抽屉里的东西，而引用数据类型变量里存储的是这个抽屉的钥匙，钥匙和抽屉一一对应。

#### 常用的基本数据类型有：
![在这里输入图片描述][2]

### Java中自动类型转换

 ![图片](https://dn-coding-net-production-pp.qbox.me/34e2cbed-2476-4a31-ace7-8b931a5cc781.png)
**int 转 double 多出一位小数但是double 不可自动转换为int**；


### Java中的强制类型转换（数值上进行四舍五入）
 ![图片](https://dn-coding-net-production-pp.qbox.me/bae53401-325d-4337-b7ed-fbd1748460fa.png)

***************************************************************

### Java 注释(javadoc)

       @author 标明开发该类模块的作者
       @version 标明该类模块的版本
       @see 参考转向，也就是相关主题
       @param 对方法中某参数的说明
       @return 对方法返回值的说明
       @exception 对方法可能抛出的异常进行说明

********************************************************************************************
### Java中的算术运算符

>>>>> ## 自增和自减运算符只能用于操作变量

 ![图片](https://dn-coding-net-production-pp.qbox.me/88c04e77-05da-4e7b-91d3-caec3e065312.png)
#### 先自增1 然后复制  `+a没整明白` （可能=++a）
 ![图片](https://dn-coding-net-production-pp.qbox.me/90d8e2ec-a1cd-4679-b6c3-25386fe41062.png)
#### 先赋值再自增1
 ![图片](https://dn-coding-net-production-pp.qbox.me/0137bd52-764f-414f-a5d6-e6459877c5cc.png)
********************************************************************************************
### Java赋值运算符：

 ![图片](https://dn-coding-net-production-pp.qbox.me/490beefc-b138-42d2-9d9a-3143e41d0d4f.png)

********************************************************************************************

Java中的比较运算符

比较运算符用于判断两个数据的大小，例如：大于、等于、不等于。比较的结果是一个布尔值（ true 或 false ）。

Java 中常用的比较运算符如下表所示：

 ![图片](https://dn-coding-net-production-pp.qbox.me/3e650a8b-cbed-4419-95c6-f1201cb44e2a.png)

注意哦：

1、  > 、 < 、 >= 、 <= 只支持左右两边操作数是数值类型

2、  == 、 != 两边的操作数既可以是数值类型，也可以是引用类型

*******************************************************************************************

 ![图片](https://dn-coding-net-production-pp.qbox.me/1d7a88b7-d5e5-4fc8-aa3f-d9f1acc95c96.png)
### Java中的条件运算符（三目运算符）
布尔表达式 ？ 表达式1 ：表达式2；

 ![图片](https://dn-coding-net-production-pp.qbox.me/41b4ab20-7e05-4336-bbd7-47e5b6500d3e.png)

### Java中运算符的优先级

 ![图片](https://dn-coding-net-production-pp.qbox.me/4f1dd746-2eb5-46d4-97cf-00dbd14059bd.png)

 ![图片](https://dn-coding-net-production-pp.qbox.me/09001cc3-6e2e-4e49-b1d7-b9a7824cc799.png)


********************************************************************************************
 ![图片](https://dn-coding-net-production-pp.qbox.me/08049d83-f0ac-42a4-abb8-a6884be14453.png)
  [1]: https://coding.net/api/project/76004/files/639092/imagePreview
  [2]: https://coding.net/api/project/76004/files/639093/imagePreview