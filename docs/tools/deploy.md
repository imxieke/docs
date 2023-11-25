# 免费部署平台

## Pages

| 平台 | 类型 | 空间 | 流量 | 特性 | 限制 |
|---|:--|:--|:--|---|---|
| [Github](https://pages.github.com) | 静态| 1G | 100G/月 | Https/自定义域名 | 部署 10次/小时 Action 除外 |
| [Cloudflare](https://pages.cloudflare.com) | 静态 React, Vue, Gatsby, and Hugo | 未知 | 无限 | Https/自定义域名 | 部署 500次/月 |
| Gitlab | 静态| 未知 | 未知 | Https/自定义域名 | 未知 |
| CodeBerg | 静态| 未知 | 未知 | Https/自定义域名 | 未知 |

## Engine && Worker

| 平台 | 请求数 | CI&CD/Min | 语言 | Serveless | CPU/TPQ | Docker | DB | 流量 | 备注 |
|-----|-----|------|-----|----------|---|---|------|------|------|
|[Vercel]| 1 百万 | 6,000 | Node | √ |10ms| x|√|100G||
|[Deno]| 1 百万 | x | Node/Deno/WebAssembly | √ |10s| x|√|100G||
|[Cloudflare]| 10万/天 | x | Node | √ |10ms| x|√|适量||
|[Netlify]| 1 百万 | 300 | Node | √ |未知| x|√|100G|主打静态站点|
|[Zeabur]| x | √ | static | √ |未知| x|√|未知|主打静态站点|
|[Render]| x | 500 | Node/Python/Go/Rust/Ruby/Elixir | x |未知| √|√|100G|Redis/PGSQL 主打一个全能|

- ## 不建议用于生产环境 数据随时可能会丢失 部分平台可能会将项目停止

[Vercel]: https://vercel.com/pricing
[Deno]: https://dash.deno.com
[Cloudflare]: https://workers.cloudflare.com
[Netlify]: https://www.netlify.com
[Zeabur]: https://zeabur.com
[Render]: https://render.com