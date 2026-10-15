# NetStack_CertificatePinning

```c
struct NetStack_CertificatePinning {...}
```

## 概述

Defines certificate pinning information.

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 12

**相关模块：** [netstack](capi-netstack.md)

**所在头文件：** [net_ssl_c_type.h](capi-net-ssl-c-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| NetStack_CertificatePinningKind kind | Certificate lock type |
| NetStack_HashAlgorithm hashAlgorithm | Hash algorithm |
| *publicKeyHash |  |


