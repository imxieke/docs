# JavaScript

JavaScript的基本数据类型有六种，分别是（1）Number (2)String (3)boolean (4)undefined (5)null
（6）Object。

1 关键字
break case catch continue default delete do else finally for function if in instanceof new return switch this throw try typeof var void while with
2 保留字
abstract boolean byte char class const debugger double enum export extends fimal float goto implements import int interface long mative package private protected public short static super synchronized
throws transient volatile
Connet Char :+;
global variable: delete of close current pages
local  variable: delete of after running

Array: []
Object:{}
var name = "imxieke";
var name; //value unchange;
var name = ["imxieke","Xiekers","Xiaoke"];
var name = new Array("imxieke","Xiekers","Xiaoke");
var name = new Array();
name[0] = "imxieke";
name[1] = "Xiekers";
name[2] = "Xiaoke";

var person = {first:"imxieke",last:"Xiekers"};
var person = {
    first   :"imxieke",
    last    :"Xiekers"
    };
person.first;
person["first"];
window.open参数
 ![图片](https://dn-coding-net-production-pp.qbox.me/9aa36bd7-b361-4ef1-8056-ee67b4e6d0e3.png)

window.alert == alert   //pop alert
document.write()        //Write Content to Browse Pages
innerHTML               //Replace Content to HTML Element
console.log()           //print content to console
document.getElementById("").innerHTML="";

innerHTML= string number function


### 获取标签内的值

输入框 $('#id').val()
标签内 $('.class').text()
指定标签 $("#id").attr("href");