## 禁用 `ipv6`
`resolver      8.8.8.8 ipv6=off;`

## SSL_do_handshake() failed
`proxy_ssl_server_name on;`

## sub_filter 文本替换无效

```
        proxy_ssl_server_name on;
        gzip off;
        proxy_set_header Accept-Encoding '';
        proxy_redirect off;
        sub_filter_once off;
        sub_filter_types *;
        sub_filter '' '';
```

### `header` 信息
使用X-Frame-Options HTTP 响应标头来指示是否应允许浏览器在`<frame>`或`<iframe>`中呈现页面。这可以防止点击劫持攻击

```
add_header X-Frame-Options "SAMEORIGIN";
X-Frame-Options: SAMEORIGIN
```

#### Strict-Transport-Security
HTTP Strict Transport Security (HSTS) 是网站用来声明只能使用安全连接 (HTTPS) 访问它们的一种方法。如果网站声明了 HSTS 策略，浏览器必须拒绝所有 HTTP 连接并阻止用户接受不安全的 SSL 证书。要将 HSTS 标头添加到您的 nginx 服务器，您可以将以下指令添加到您的服务器部分：

```
add_header Strict-Transport-Security "max-age=31536000; includeSubdomains; preload";
```

#### CSP and X-XSS-Protection

内容安全策略 (CSP) 保护您的 Web 服务器免受某些类型的攻击，包括跨站点脚本攻击(Cross-site Scripting attacks XSS) 和数据注入攻击。您可以通过添加以下示例`Content-Security-Policy`标头来实施 CSP（请注意，应配置实际标头以满足您的独特要求）：
```
add_header Content-Security-Policy "default-src 'self' http: https: data: blob: 'unsafe-inline'" always;
```

HTTP X-XSS-Protection标头受 IE 和 Safari 支持，如果您有强大的内容安全策略，现代浏览器则不需要。但是，为了在旧浏览器（尚不支持 CSP）的情况下帮助防止 XSS，您可以将 X-XSS Protection 标头添加到您的服务器部分：
`add_header X-XSS-Protection "1; mode=block";`

### 禁用任何不需要的 HTTP 方法
我们建议您禁用任何不会被使用且不需要在 Web 服务器上实现的 HTTP 方法。如果在nginx虚拟主机配置文件的location块中添加如下条件，服务器将只允许GET、HEAD、POST方法，并会过滤掉DELETE、TRACE等方法。

```
location / {
    limit_except GET HEAD POST { deny all; }
}
```
另一种方法是将以下条件添加到服务器部分（或服务器块）。它可以被认为是更通用的，但你应该小心if位置上下文中的语句。
```
if ($request_method !~ ^(GET|HEAD|POST)$ ) {
    return 444;
}
```
# Nginx embedded variables

Source document at: http://nginx.org/en/docs/http/ngx_http_core_module.html#variables

Wiki document (deprecated) at: http://wiki.nginx.org/HttpCoreModule

<table>
	<tr>
		<th>Name</th>
		<th>Description</th>
		<th>Read only</th>
	</tr>
	<tr>
		<td><code>$arg_<em>name</em></code></td>
		<td>Argument <em>name</em> in the request line</td>
		<td>No</td>
	</tr>
	<tr>
		<td><code>$args</code></td>
		<td>Arguments in the request line</td>
		<td>No</td>
	</tr>
	<tr>
		<td><code>$binary_remote_addr</code></td>
		<td>Client address in a binary form, value’s length is always 4 bytes for IPv4 addresses or 16 bytes for IPv6 addresses</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$body_bytes_sent</code></td>
		<td>Number of bytes sent to a client, not counting the response header; this variable is compatible with the &quot;%B&quot; parameter of the <code>mod_log_config</code> Apache module</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$bytes_sent</code></td>
		<td>Number of bytes sent to a client (1.3.8, 1.2.5)</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$connection</code></td>
		<td>Connection serial number (1.3.8, 1.2.5)</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$connection_requests</code></td>
		<td>Current number of requests made through a connection (1.3.8, 1.2.5)</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$content_length</code></td>
		<td>&quot;Content-Length&quot; request header field</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$content_type</code></td>
		<td>&quot;Content-Type&quot; request header field</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$cookie_<em>name</em></code></td>
		<td>The <code><em>name</em></code> cookie</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$document_root</code></td>
		<td>Root or alias directive's value for the current request</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$document_uri</code></td>
		<td>Same as <code>$uri</code></td>
		<td></td>
	</tr>
	<tr>
		<td><code>$host</code></td>
		<td>In this order of precedence: host name from the request line, or host name from the &quot;Host&quot; request header field, or the server name matching a request</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$hostname</code></td>
		<td>Host name</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$http_<em>name</em></code></td>
		<td>Arbitrary request header field; the last part of a variable <em>name</em> is the field name converted to lower case with dashes replaced by underscores</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$https</code></td>
		<td>&quot;on&quot; if connection operates in SSL mode, or an empty string otherwise</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$is_args</code></td>
		<td>&quot;?&quot; if a request line has arguments, or an empty string otherwise</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$limit_rate</code></td>
		<td>Setting this variable enables response rate limiting; see <a href="http://nginx.org/en/docs/http/ngx_http_core_module.html#limit_rate">limit_rate</a></td>
		<td></td>
	</tr>
	<tr>
		<td><code>$msec</code></td>
		<td>Current time in seconds with the milliseconds resolution (1.3.9, 1.2.6)</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$nginx_version</code></td>
		<td>Nginx version</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$pid</code></td>
		<td>PID of the worker process</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$pipe</code></td>
		<td>&quot;p&quot; if request was pipelined, &quot;.&quot; otherwise (1.3.12, 1.2.7)</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$proxy_protocol_addr</code></td>
		<td>Client address from the PROXY protocol header, or an empty string otherwise (1.5.12). The PROXY protocol must be previously enabled by setting the <code>proxy_protocol</code> parameter in the listen directive.</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$proxy_protocol_port</code></td>
		<td>Client port from the PROXY protocol header, or an empty string otherwise (1.11.0). The PROXY protocol must be previously enabled by setting the proxy_protocol parameter in the listen directive.</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$query_string</code></td>
		<td>Same as <code>$args</code></td>
		<td>Yes</td>
	</tr>
	<tr>
		<td><code>$realpath_root</code></td>
		<td>An absolute pathname corresponding to the root or alias directive's value for the current request, with all symbolic links resolved to real paths</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$remote_addr</code></td>
		<td>Client address</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$remote_port</code></td>
		<td>Client port</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$remote_user</code></td>
		<td>User name supplied with the Basic authentication</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$request</code></td>
		<td>Full original request line</td>
		<td>Yes</td>
	</tr>
	<tr>
		<td><code>$request_body</code></td>
		<td>Request body. The variable’s value is made available in locations processed by the proxy_pass, fastcgi_pass, uwsgi_pass, and scgi_pass directives when the request body was read to a memory buffer.</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$request_body_file</code></td>
		<td>Name of a temporary file with the request body. At the end of processing, the file needs to be removed. To always write the request body to a file, client_body_in_file_only needs to be enabled. When the name of a temporary file is passed in a proxied request or in a request to a FastCGI server, passing the request body should be disabled by the proxy_pass_request_body off and fastcgi_pass_request_body off directives, respectively.</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$request_completion</code></td>
		<td>&quot;OK&quot; if a request has completed, or an empty string otherwise</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$request_filename</code></td>
		<td>File path for the current request, based on the root or alias directives, and the request URI</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$request_id</code></td>
		<td>Unique request identifier generated from 16 random bytes, in hexadecimal (1.11.0)</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$request_length</code></td>
		<td>Request length (including request line, header, and request body) (1.3.12, 1.2.7)</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$request_method</code></td>
		<td>Request method, usually &quot;GET&quot; or &quot;POST&quot;</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$request_time</code></td>
		<td>Request processing time in seconds with a milliseconds resolution (1.3.9, 1.2.6); time elapsed since the first bytes were read from the client</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$request_uri</code></td>
		<td>Full original request URI (with arguments)</td>
		<td>Yes</td>
	</tr>
	<tr>
		<td><code>$scheme</code></td>
		<td>Request scheme, &quot;http&quot; or &quot;https&quot;</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$sent_http_<em>name</em></code></td>
		<td>Arbitrary response header field; the last part of a variable name is the field name converted to lower case with dashes replaced by underscores</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$sent_trailer_<em>name</em></code></td>
		<td>Arbitrary field sent at the end of the response (1.13.2); the last part of a variable name is the field name converted to lower case with dashes replaced by underscores</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$server_addr</code></td>
		<td>An address of the server which accepted a request. Computing a value of this variable usually requires one system call. To avoid a system call, the listen directives must specify addresses and use the bind parameter.</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$server_name</code></td>
		<td>Name of the server which accepted a request</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$server_port</code></td>
		<td>Port of the server which accepted a request</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$server_protocol</code></td>
		<td>Request protocol, usually &quot;HTTP/1.0&quot; or &quot;HTTP/1.1&quot;, or &quot;HTTP/2.0&quot;</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$status</code></td>
		<td>Response status (1.3.2, 1.2.2)</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$tcpinfo_rtt</code>, <code>$tcpinfo_rttvar</code>, <code>$tcpinfo_snd_cwnd</code>, <code>$tcpinfo_rcv_space</code></td>
		<td>Information about the client TCP connection; available on systems that support the <code>TCP_INFO</code> socket option</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$time_iso8601</code></td>
		<td>Local time in the ISO 8601 standard format (1.3.12, 1.2.7)</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$time_local</code></td>
		<td>Local time in the Common Log Format (1.3.12, 1.2.7)</td>
		<td></td>
	</tr>
	<tr>
		<td><code>$uri</code></td>
		<td>Current URI in request, normalized. The value of <code>$uri</code> may change during request processing, e.g. when doing internal redirects, or when using index files.</td>
		<td></td>
	</tr>
</table>

`if ($geoip_country_code = JP) { return 403; }`

```
Syntax:	if (condition) { ... }
Default:	—
Context:	server, location
```

不可以放到 http 下

```nginx
= 开头表示精确匹配。如 A 中只匹配根目录结尾的请求，后面不能带任何字符串；
^~ 开头表示uri以某个常规字符串开头，不是正则匹配；
~ 开头表示区分大小写的正则匹配；
~* 开头表示不区分大小写的正则匹配；
/ 通用匹配, 如果没有其它匹配,任何请求都会匹配到

location  = / {
  # 精确匹配 / ，主机名后面不能带任何字符串
  [ configuration A ]
}location  / {
  # 因为所有的地址都以 / 开头，所以这条规则将匹配到所有请求
  # 但是正则和最长字符串会优先匹配
  [ configuration B ]
}location /documents/ {  # 匹配任何以 /documents/ 开头的地址，匹配符合以后，还要继续往下搜索
  # 只有后面的正则表达式没有匹配到时，这一条才会采用这一条
  [ configuration C ]
}location ~ /documents/Abc {  # 匹配任何以 /documents/Abc 开头的地址，匹配符合以后，还要继续往下搜索
  # 只有后面的正则表达式没有匹配到时，这一条才会采用这一条
  [ configuration CC ]
}location ^~ /images/ {  # 匹配任何以 /images/ 开头的地址，匹配符合以后，停止往下搜索正则，采用这一条。
  [ configuration D ]
}location ~* \.(gif|jpg|jpeg)$ {  # 匹配所有以 gif,jpg或jpeg 结尾的请求
  # 然而，所有请求 /images/ 下的图片会被 config D 处理，因为 ^~ 到达不了这一条正则
  [ configuration E ]
}location /images/ {  # 字符匹配到 /images/，继续往下，会发现 ^~ 存在
  [ configuration F ]
}location /images/abc {  # 最长字符匹配到 /images/abc，继续往下，会发现 ^~ 存在
  # F与G的放置顺序是没有关系的
  [ configuration G ]
}location ~ /images/abc/ {  # 只有去掉 config D 才有效：先最长匹配 config G 开头的地址，继续往下搜索，匹配到这一条正则，采用
  # 因为都是正则匹配，优先级一样，选择最上面的
    [ configuration H ]
}location ~* /js/.*/\.js
```

### 优先级
- ( location = ) > ( location 完整路径 ) > ( location ^~ 路径 ) > ( location ,* 正则顺序 ) > ( location 部分起始路径 ) > ( / )