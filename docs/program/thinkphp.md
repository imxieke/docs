## 中间件传参
- 使用 facade 无法查到值 需 `use think\Request`

## 全局和应用中间件无法获取 controller 和 action
- 必须用路由中间件