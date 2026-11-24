# NetStack_Certificates

```c
typedef struct NetStack_Certificates {...} NetStack_Certificates
```

## 概述

Define certificate information.

<!--Device-struct NetStack_Certificates {...}--><!--Device-struct NetStack_Certificates {...}-End-->

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 12

**相关模块：** [netstack](capi-network-kit-netstack.md)

**所在头文件：** [net_ssl_c_type.h](capi-net-ssl-c-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char **content | PEM content of the certificate.<br><!--Device-char **content--><!--Device-char **content-End--> |
| size_t length | Number of certificates.<br><!--Device-size_t length--><!--Device-size_t length-End--> |


