# Http_HeaderEntry

```c
struct Http_HeaderEntry {...}
```

## 概述

请求或者响应的标头的所有键值对。

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 20

**相关模块：** [netstack](capi-netstack.md)

**所在头文件：** [net_http_type.h](capi-net-http-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char *key | 请求或者响应的标头中的键。 |
| Http_HeaderValue *value | Value of the key in the request or response header. For details, see [Http_HeaderValue](capi-netstack-http-headervalue.md). |
| struct Http_HeaderEntry *next | 链式存储。指向下一个Http_HeaderEntry。 |


