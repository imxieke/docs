## Tips
- 对于无法识别的标签可使用内容替换 如 link->span

# 获取头部信息
- find('title')->text(); // 获取网站标题
- find('meta[name=keywords]')->content; // 获取网站头部关键词
- find('h3>a')->texts(); //获取搜索结果标题列表
- find('h3>a')->attrs('href'); //获取搜索结果链接列表
- find('img')->src; //获取第一张图片的链接地址
- find('img:eq(1)')->src; //获取第二张图片的链接地址
- find('img')->eq(2)->src; //获取第三张图片的链接地址
- encoding('UTF-8','GB2312')   编码转换
- removeHead()           移除头部信息 当编码转换不可用时使用
- find('.two')->children('img')->attrs('alt'); //获取class为two元素下的所有img孩子节点

### 遍历图片

```php
find('img')->map(function($img){
	echo $img->alt;  //打印图片的alt属性
});
```

## HTTP网络操作（GuzzleHttp）
### 携带cookie登录新浪微博
```php
// 采集新浪微博需要登录才能访问的页面
$ql = QueryList::get('http://weibo.com','param1=testvalue & params2=somevalue',[
    'headers' => [
        // 填写从浏览器获取到的cookie
        'Cookie' => 'SINAGLOBAL=546064; wb_cmtLike_2112031=1; wvr=6;....'
    ]
]);
//echo $ql->getHtml();
echo $ql->find('title')->text();
// 输出: 我的首页 微博-随时随地发现新鲜事
```

### 使用Http代理
```php
$urlParams = ['param1' => 'testvalue','params2' => 'somevalue'];
$opts = [
	// 设置http代理
    'proxy' => 'http://222.141.11.17:8118',
    //设置超时时间，单位：秒
    'timeout' => 30,
     // 伪造http头
    'headers' => [
        'Referer' => 'https://querylist.cc/',
        'User-Agent' => 'testing/1.0',
        'Accept'     => 'application/json',
        'X-Foo'      => ['Bar', 'Baz'],
        'Cookie'    => 'abc=111;xxx=222'
    ]
];
$ql->get('http://httpbin.org/get',$urlParams,$opts);
// echo $ql->getHtml();
```

### 模拟登录
```php
// 用post登录
$ql = QueryList::post('http://xxxx.com/login',[
    'username' => 'admin',
    'password' => '123456'
])->get('http://xxx.com/admin');
//采集需要登录才能访问的页面
$ql->get('http://xxx.com/admin/page');
//echo $ql->getHtml();
```

### Form表单操作
### 模拟登陆GitHub
```php

// 获取QueryList实例
$ql = QueryList::getInstance();
//获取到登录表单
$form = $ql->get('https://github.com/login')->find('form');

//填写GitHub用户名和密码
$form->find('input[name=login]')->val('your github username or email');
$form->find('input[name=password]')->val('your github password');

//序列化表单数据
$fromData = $form->serializeArray();
$postData = [];
foreach ($fromData as $item) {
    $postData[$item['name']] = $item['value'];
}

//提交登录表单
$actionUrl = 'https://github.com'.$form->attr('action');
$ql->post($actionUrl,$postData);
//判断登录是否成功
// echo $ql->getHtml();
$userName = $ql->find('.header-nav-current-user>.css-truncate-target')->text();
if($userName)
{
    echo '登录成功!欢迎你:'.$userName;
}else{
    echo '登录失败!';
}
```