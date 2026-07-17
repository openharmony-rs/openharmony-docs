# Http_HeaderEntry

```c
typedef struct Http_HeaderEntry {...} Http_HeaderEntry
```

## 概述

请求或者响应的标头的所有键值对。

**起始版本：** 20

**相关模块：** [netstack](capi-netstack.md)

**所在头文件：** [net_http_type.h](capi-net-http-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char *key | 请求或者响应的标头中的键。 |
| [Http_HeaderValue](capi-netstack-http-headervalue.md) *value | Value of the key in the request or response header. For details, see [Http_HeaderValue](capi-netstack-http-headervalue.md). |
| struct [Http_HeaderEntry](capi-netstack-http-headerentry.md) *next | 链式存储。指向下一个Http_HeaderEntry。 |


