## Composer 使用文档

### Mirrors list
```
https://mirrors.huaweicloud.com/repository/php/
https://mirrors.cloud.tencent.com/composer/ mirrors.tencentyun.com(内网)
https://mirrors.aliyun.com/composer/
```

### Template
- https://github.com/smarty-php/smarty
> a template engine for PHP, facilitating the separation of presentation (HTML/CSS) from application logic.

选项一、全局配置（推荐）

$ composer config -g repo.packagist composer https://packagist.laravel-china.org
选项二、单独使用

如果仅限当前工程使用镜像，去掉 -g 即可，如下：

$ composer config repo.packagist composer https://packagist.laravel-china.org
取消镜像

composer config -g --unset repos.packagist

调试
composer 命令增加 -vvv 可输出详细的信息，命令如下：

composer -vvv require alibabacloud/sdk


## 版本信息

- 固定版本
`composer require hyperf/validation:"v2.1.0"`

```bash
composer require hyperf/validation:">=v2.1.0"
composer require hyperf/validation:"<v2.1.0"
composer require hyperf/validation:"v2.1.*"  >=2.1.0 <=2.2.0
```

## minimum-stability (root-only)

minimum-stability 定义了包的最小稳定性。默认为 stable（稳定）。

如果你依赖于一个 dev（开发版本）包，你应该明确的进行定义。

`minimum-stability` 会对每个包的所有版本都会进行稳定性检查，低于 `minimum-stability` 所设定的最低稳定性的版本，将在解决依赖关系时被忽略。对于个别包的特殊稳定性要求，可以在 require 或 require-dev 中设定。

可用的稳定性标识（按字母排序）有：`dev、alpha、beta、RC、stable`

## prefer-stable (root-only)
当此选项被激活时，Composer 将优先使用更稳定的包版本。

使用 "prefer-stable": true 来激活它。