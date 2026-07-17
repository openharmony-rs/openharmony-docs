# NetStack_CertBlob

```c
struct NetStack_CertBlob {...}
```

## 概述

Defines the certificate data structure.

**起始版本：** 11

**相关模块：** [netstack](capi-netstack.md)

**所在头文件：** [net_ssl_c_type.h](capi-net-ssl-c-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| enum [NetStack_CertType](capi-net-ssl-c-type-h.md#netstack_certtype) type | Certificate type. |
| uint32_t size | Certificate content length. |
| uint8_t *data | Certificate data. |


