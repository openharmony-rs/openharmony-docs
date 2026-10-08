# Netstack

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

## 概述

提供网络相关模块的C接口，包括SSL/TLS证书链校验、WebSocket客户端、HTTP请求和HTTP全局拦截器等功能。

调用范式：以HTTP请求为例，典型调用流程为：创建请求实例→设置请求参数→发起请求→获取响应→销毁实例；WebSocket客户端需按创建实例→连接服务器→收发数据→关闭连接的顺序调用；SSL/TLS证书链校验需在发起网络请求前先加载并校验证书链；HTTP全局拦截器需先注册后使用，并在不再需要时注销。

**起始版本：** 11
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [net_ssl_c.h](capi-net-ssl-c-h.md) | 定义SSL/TLS证书链校验模块C接口数据结构。 |
| [net_ssl_c_type.h](capi-net-ssl-c-type-h.md) | 定义SSL/TLS证书链校验模块的C接口需要的数据结构。 |
| [net_websocket.h](capi-net-websocket-h.md) | 定义WebSocket客户端模块的接口。 |
| [net_websocket_type.h](capi-net-websocket-type-h.md) | 定义WebSocket客户端模块的C接口需要的数据结构。 |
| [net_http.h](capi-net-http-h.md) | 定义HTTP请求模块的接口。 |
| [net_http_type.h](capi-net-http-type-h.md) | 定义HTTP请求模块的C接口需要的数据结构。 |
| [http_interceptor.h](capi-net-http-interceptor-h.md) | 定义HTTP全局拦截器模块的接口。 |
| [http_interceptor_type.h](capi-net-http-interceptor-type-h.md) | 定义HTTP全局拦截器模块的C接口需要的数据结构。 |
