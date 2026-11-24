# Http_Proxy

```c
typedef struct Http_Proxy {...} Http_Proxy
```

## 概述

代理配置结构体。

<!--Device-struct Http_Proxy {...}--><!--Device-struct Http_Proxy {...}-End-->

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 20

**相关模块：** [netstack](capi-network-kit-netstack.md)

**所在头文件：** [net_http_type.h](capi-net-http-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Http_ProxyType](capi-net-http-type-h.md#http_proxytype) proxyType | 代理配置类型，参考[Http_ProxyType](capi-net-http-type-h.md#http_proxytype)。<br><!--Device-Http_ProxyType proxyType--><!--Device-Http_ProxyType proxyType-End--> |
| [Http_CustomProxy](capi-netstack-http-customproxy.md) customProxy | 自定义代理配置信息，参考[Http_CustomProxy](capi-netstack-http-customproxy.md)。<br><!--Device-Http_CustomProxy customProxy--><!--Device-Http_CustomProxy customProxy-End--> |


