## 中间件传参
- 使用 facade 无法查到值 需 `use think\Request`

## 全局和应用中间件无法获取 controller 和 action
- 必须用路由中间件

## Facade
```php
use think\facade\Config;
Config::get('app');
Config::get('route');

Config::get('app.app_name');
Config::get('route.url_domain_root');

Config::get('database.default.host');

判断是否存在某个设置参数
Config::has('template');
Config::has('route.route_rule_merge');
```

### 创建项目
`composer create-project topthink/think think`

### 升级到最新版本
`composer update topthink/framework`


### 调试模式
在根目录添加或修改 `.env`

`APP_DEBUG`

### 配置文件后缀
`CONFIG_EXT=ini`

### 指定配置文件
```
.env.example
.env.testing
.env.develop
```

```php
// 执行HTTP应用并响应
$http = (new App())->setEnvName('develop')->http;

$response = $http->run();

$response->send();

$http->end($response);
```
