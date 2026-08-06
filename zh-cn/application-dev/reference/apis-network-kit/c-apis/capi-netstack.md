# netstack

## 概述

提供HTTP客户端模块的C接口。

**起始版本：** 20
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [net_http_type.h](capi-net-http-type-h.md) | 定义HTTP请求模块的C接口需要的数据结构。 |
| [net_http.h](capi-net-http-h.md) | 定义HTTP请求模块的接口。 |
| [net_websocket.h](capi-net-websocket-h.md) | 定义WebSocket客户端模块的接口。 |
| [net_websocket_type.h](capi-net-websocket-type-h.md) | 定义WebSocket客户端模块的C接口需要的数据结构。 |
| [http_interceptor_type.h](capi-http-interceptor-type-h.md) | 为HTTP全局拦截器模块提供C接口的数据结构定义，包含拦截器的请求/响应头信息、HTTP请求/响应数据包结构、拦截器配置信息以及相关的枚举类型和函数指针。 |
| [http_interceptor.h](capi-http-interceptor-h.md) | 定义HTTP全局拦截器模块的接口，分为只读拦截器与可修改拦截器两类。通过全局只读拦截器，开发者可以监控应用内部通过所支持的系统网络组件发起的所有HTTP请求，实现日志记录功能，也可以在全局可修改拦截器中添加自定义逻辑，修改应用内部通过所支持的系统网络组件发起的HTTP请求的请求头、响应头、响应体。 |
| [net_ssl_c_type.h](capi-net-ssl-c-type-h.md) | 定义SSL/TLS证书链校验模块的C接口需要的数据结构。 |
| [net_ssl_c.h](capi-net-ssl-c-h.md) | 定义SSL/TLS证书链校验模块C接口数据结构。 |
