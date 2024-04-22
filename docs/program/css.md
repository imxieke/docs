# CSS
# CSS
class= 	.className
id= 	#idName
border:size solid color 			//边缘边框
padding:2px; 						//框内上下左右填充，填一个值则是上下左右一样 二个则是上下一样 左右一样
color 								//Text Color
background-color 					//Text Background
box-shadow: x y color;				//边框阴影
background-repeat: repeat 			//重复图像
background-repeat: no-repeat 		//不重复图像
background-repeat: repeat-x			//垂直显示图像
background-repeat: repeat-y			//竖直显示图像
background-position: 5% 9%;			//定义图像位置
parameter: center,top.bottom,left,right,px,cm,%  (x,y) and left top, left bottom, left center etc
background: #ff0000 url(/i/eg_bg_03.gif) no-repeat fixed left;  //Shorthand
background-color: transparent 		//透明颜色背景
background-attachment:fixed 		//固定图像，否则鼠标拖动会变成透明背景
background-clip: border-box			//裁剪背景区域
parameter:border-box|padding-box|content-box;

Selector:
* 						//通用选择器
. 						//Class选择器
#						//id选择器
` `(空格)     			//包含选择器 包含选择的元素
>						//子选择器,当前 div 子元素
+						//相邻选择器 只有两个在一起的元素才会生效
~						//兄弟选择器，除第一个所有元素都会生效
E[class]				//属性选择器, 当属性为class 的元素
E[class="logo"]			//属性选择器, 当属性为class且值为logo 的元素
E[class~="logo"]		//属性选择器, 当属性为class且值为logo top 的元素,logo top 之间用空格分开
E[class^="a"]			//属性选择器，当属性为class且开头字母为a的元素
E[class$="a"]			//属性选择器，当属性为class且开头结尾为a的元素
E[class*="a"]			//属性选择器，当属性为class且包含a元素
E[class|="a"]			//属性选择器，当属性为class且开头为a且以-分割 属性值 的元素

Notes:
background-color、background-image 不能继承
!important 增加在元素中优先使用权 .name{color:black !important;}
//导入外部元素
@import url(http://domain.com/demo.css);
@import url("http://domain.com/demo.css");
@import "http://domain.com/demo.css";
@import "demo.css";
@charset "utf-8";  		//定义字符编码
``` 					//自定义字体 支持 ttf otf eot( <ie9)
@font-face{
	font-family:YH;
	src:url(http://domain/fonts/MSYH.TTF);
}
body{
	font-family:YH;
}
```