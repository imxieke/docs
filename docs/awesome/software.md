# Awesome 

## Virtual Machine
  - kvm
  - openvz
  - lxc
  - vmware

## Capture Package

### Open Source Software

#### Whistle
- Language: Node
- Description: HTTP, HTTP2, HTTPS, Websocket debugging proxy
- https://github.com/avwo/whistle

#### Mitmproxy
- An interactive TLS-capable intercepting HTTP proxy for penetration testers and software developers.
- Platform Python
- https://github.com/mitmproxy/mitmproxy

#### LightProxy (Base whistle)
- https://github.com/alibaba/lightproxy

#### NoHost (Base whistle)
- language: Node
- https://github.com/Tencent/nohost

#### Description
- 环境共享：前端无需配后台环境，后台无需配前端环境，其他人无需配任何环境
- 抓包调试：远程实时抓包调试，支持各种 Whistle 规则，以及通过链接分享抓包数据
- 历史记录：可以把环境配置及抓包数据沉淀下来，供后续随时切换查看
- 插件扩展：可以通过插件扩展实现诸如 inspect，vase，autosave 等功能
- 对外接口：提供对外接口，可供发布系统、CI等工具操作，实现自动化增删查改环境配置

#### Lyrebird (Base whistle)
- language: Node
- 移动应用插件化测试工作台
- https://github.com/Meituan-Dianping/lyrebird

### Closed Source
#### ProxyMan
- Platform: macOS/IOS/Android
- Desc: Modern. Native. Delightful Web Debugging Prox
- HomePage: https://github.com/ProxymanApp/Proxyman

#### Features
- 💻 Native macOS app. Written by Swift, Objective-C. Powered by Apple SwiftNIO for the high-performance network application.
- 🍎 Fully supports Apple Chip (e.g M1, M2, M3).
💫 Built for macOS Ventura & Sonoma.
- ✅ Hassle-free Intercept HTTP/HTTPS requests/response and WebSocket from Web Browsers, iOS, and Android devices.
- ✅ Modern and intuitive UI
- 🔍 Multiple filters
- Comprehensive Guidelines to set up with iOS simulator and iOS and Android devices.
- Basic debugging tools: Compose, Repeat, Wildcard/Regex Filter, Multiple Filters, Customize Columns, Toolbar...
- Advanced Tools: Breakpoint, Map Local, Map Remote, Backlist, External Proxying, No Caching, Protobuf, Clear Cache, Custom Certificates, Scripting, Network Conditions, Reverse Proxy, Diff, Access Control, DNS Spoofing, etc
- Automatic Setup for Backend Development: Auto capture HTTP(s) traffic from NodeJS, Ruby, and Python.
- macOS 11+

### Premium
#### Charles
- https://www.charlesproxy.com
- Windows/Linux/macOS(10.10+)
- Language: java
- Charles is an HTTP proxy / HTTP monitor / Reverse Proxy that enables a developer to view all of the HTTP and SSL / HTTPS traffic between their machine and the Internet. This includes requests, responses and the HTTP headers (which contain the cookies and caching information).

##### Features
- SSL Proxying – view SSL requests and responses in plain text
- Bandwidth Throttling to simulate slower Internet connections including latency
- AJAX debugging – view XML and JSON requests and responses as a tree or as text
- AMF – view the contents of Flash Remoting / Flex Remoting messages as a tree
- Repeat requests to test back-end changes
- Edit requests to test different inputs
- Breakpoints to intercept and edit requests or responses
- Validate recorded HTML, CSS and RSS/atom responses using the W3C validator

#### Fiddle
- Windows/Linux/macOS
- https://www.telerik.com/fiddler

##### Features
- Multiple options for capturing, including system proxy, preconfigured browser instance, and preconfigured terminal process
- Support for multiple protocols, including HTTP(S), HTTP/2, WebSocket, and gRPC communication
- Extensive Rules options for modifying traffic
- Advanced filters for precisely narrowing down traffic
- Composer functionality for creating, editing, and saving API requests
- Sharing, saving, and collaboration options
- Regular release cadence and dedicated support