# Http_Proxy

```c
typedef struct Http_Proxy {...} Http_Proxy
```

## 概述

代理配置结构体。

**起始版本：** 20

**相关模块：** [netstack](capi-netstack.md)

**所在头文件：** [net_http_type.h](capi-net-http-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Http_ProxyType](capi-net-http-type-h.md#http_proxytype) proxyType | Proxy configuration type. For details, see [Http_ProxyType](capi-net-http-type-h.md#http_proxytype). |
| [Http_CustomProxy](capi-netstack-http-customproxy.md) customProxy | Custom proxy configuration. For details, see [Http_CustomProxy](capi-netstack-http-customproxy.md). |


