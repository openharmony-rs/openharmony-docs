# net_ssl_c.h

## 概述

定义SSL/TLS证书链校验模块C接口数据结构。

**库：** libnet_ssl.so

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 11

**相关模块：** [netstack](capi-netstack.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [uint32_t OH_NetStack_CertVerification(const struct NetStack_CertBlob *cert, const struct NetStack_CertBlob *caCert)](#oh_netstack_certverification) | 对外暴露的证书链校验接口。 |
| [int32_t OH_NetStack_GetPinSetForHostName(const char *hostname, NetStack_CertificatePinning *pin)](#oh_netstack_getpinsetforhostname) | 获取证书锁定信息。 |
| [int32_t OH_NetStack_GetCertificatesForHostName(const char *hostname, NetStack_Certificates *certs)](#oh_netstack_getcertificatesforhostname) | 获取证书信息。 |
| [void OH_Netstack_DestroyCertificatesContent(NetStack_Certificates *certs)](#oh_netstack_destroycertificatescontent) | 释放证书内容。 |
| [int32_t OH_Netstack_IsCleartextPermitted(bool *isCleartextPermitted)](#oh_netstack_iscleartextpermitted) | 整体明文HTTP是否允许。 |
| [int32_t OH_Netstack_IsCleartextPermittedByHostName(const char *hostname, bool *isCleartextPermitted)](#oh_netstack_iscleartextpermittedbyhostname) | 按域名明文HTTP是否允许。 |
| [int32_t OH_Netstack_IsCleartextCfgByComponent(const char *component, bool *componentCfg)](#oh_netstack_iscleartextcfgbycomponent) | 检查组件是否已配置开启明文HTTP拦截功能。 |
| [uint32_t OH_NetStack_CreateAndVerifySortedCertChain(const struct NetStack_CertBlob *cert, size_t certCount, const struct NetStack_CertBlob *caCert, const char *hostname, struct NetStack_CertBlob **outSortedChain, size_t *outSortedCount)](#oh_netstack_createandverifysortedcertchain) | 创建并验证排序的证书链。 |
| [void OH_NetStack_FreeCertChain(struct NetStack_CertBlob *certChain, size_t certCount)](#oh_netstack_freecertchain) | 释放由OH_NetStack_CreateAndVerifySortedCertChain分配的证书链。 |

## 函数说明

### OH_NetStack_CertVerification()

```c
uint32_t OH_NetStack_CertVerification(const struct NetStack_CertBlob *cert, const struct NetStack_CertBlob *caCert)
```

**描述**

对外暴露的证书链校验接口。

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const struct NetStack_CertBlob](capi-netstack-netstack-certblob.md) *cert | 用户传入的待校验证书。 |
| [const struct NetStack_CertBlob](capi-netstack-netstack-certblob.md) *caCert | 用户指定的证书，若为空则以系统预置证书进行校验。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | 0 - 成功。<br>     <br>2305001 - 未指定的错误。<br>     <br>2305002 - 无法获取颁发者证书。<br>     <br>2305003 - 无法获取证书吊销列表（CRL）。<br>     <br>2305004 - 无法解密证书签名。<br>     <br>2305005 - 无法解密CRL签名。<br>     <br>2305006 - 无法解码颁发者公钥。<br>     <br>2305007 - 证书签名失败。<br>     <br>2305008 - CRL签名失败。<br>     <br>2305009 - 证书尚未生效。<br>     <br>2305010 - 证书已过期。<br>     <br>2305011 - CRL尚未有效。<br>     <br>2305012 - CRL已过期。<br>     <br>2305023 - 证书已被吊销。<br>     <br>2305024 - 证书颁发机构（CA）无效。<br>     <br>2305027 - 证书不受信任。 |

### OH_NetStack_GetPinSetForHostName()

```c
int32_t OH_NetStack_GetPinSetForHostName(const char *hostname, NetStack_CertificatePinning *pin)
```

**描述**

获取证书锁定信息。

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *hostname | 主机名。 |
| [NetStack_CertificatePinning](capi-netstack-netstack-certificatepinning.md) *pin | 证书锁定信息的结构体。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 0 - 成功。<br>     <br>401 - 参数设置错误。<br>     <br>2305999 - 内存错误。 |

### OH_NetStack_GetCertificatesForHostName()

```c
int32_t OH_NetStack_GetCertificatesForHostName(const char *hostname, NetStack_Certificates *certs)
```

**描述**

获取证书信息。

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *hostname | 主机名。 |
| [NetStack_Certificates](capi-netstack-netstack-certificates.md) *certs | 证书信息的结构体。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 0 - 成功。<br>     <br>401 - 参数设置错误。<br>     <br>2305999 - 内存错误。 |

### OH_Netstack_DestroyCertificatesContent()

```c
void OH_Netstack_DestroyCertificatesContent(NetStack_Certificates *certs)
```

**描述**

释放证书内容。

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [NetStack_Certificates](capi-netstack-netstack-certificates.md) *certs | 证书信息。 |

### OH_Netstack_IsCleartextPermitted()

```c
int32_t OH_Netstack_IsCleartextPermitted(bool *isCleartextPermitted)
```

**描述**

整体明文HTTP是否允许。

**需要权限：** ohos.permission.INTERNET

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| bool *isCleartextPermitted | 输出参数，如果允许明文流量，则true，否则false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 0 - 成功。<br>     <br>201 - 权限被拒。<br>     <br>401 - 参数错误。 |

### OH_Netstack_IsCleartextPermittedByHostName()

```c
int32_t OH_Netstack_IsCleartextPermittedByHostName(const char *hostname, bool *isCleartextPermitted)
```

**描述**

按域名明文HTTP是否允许。

**需要权限：** ohos.permission.INTERNET

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *hostname | 主机名。 |
| bool *isCleartextPermitted | 输出参数，如果允许指定主机名的明文流量，则true，否则false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 0 - 成功。<br>     <br>201 - 权限被拒。<br>     <br>401 - 参数错误。 |

### OH_Netstack_IsCleartextCfgByComponent()

```c
int32_t OH_Netstack_IsCleartextCfgByComponent(const char *component, bool *componentCfg)
```

**描述**

检查组件是否已配置开启明文HTTP拦截功能。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *component | 组件名称，当前支持的组件：Network Kit、ArkWeb。 |
| bool *componentCfg | 输出参数，组件是否配置开启明文HTTP拦截功能，如果开启则为true，否则为false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 0 - 成功。<br>     <br>2100001 - 无效的参数值。 |

### OH_NetStack_CreateAndVerifySortedCertChain()

```c
uint32_t OH_NetStack_CreateAndVerifySortedCertChain(const struct NetStack_CertBlob *cert, size_t certCount, const struct NetStack_CertBlob *caCert, const char *hostname, struct NetStack_CertBlob **outSortedChain, size_t *outSortedCount)
```

**描述**

创建并验证排序的证书链。

>**说明：** 
>After use, you must call [OH_NetStack_FreeCertChain](capi-net-ssl-c-h.md#oh_netstack_freecertchain) to release the
 *       allocated memory pointed by outSortedChain. Failure to do so will cause memory leaks.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const struct NetStack_CertBlob](capi-netstack-netstack-certblob.md) *cert | 要验证的证书链。不能为NULL或空。 |
| size_t certCount | 证书链中的证书数量。 |
| [const struct NetStack_CertBlob](capi-netstack-netstack-certblob.md) *caCert | 用户指定的CA证书。如果为NULL，则使用预设证书。 |
| const char *hostname | 预期的服务器主机名。 |
| [struct NetStack_CertBlob](capi-netstack-netstack-certblob.md) **outSortedChain | 用于接收排序证书链的指针。如果调用者不需要链数据，可以为NULL。仅在返回值为0时有效。必须使用OH_NetStack_FreeCertChain释放分配的内存。 |
| size_t *outSortedCount | 用于接收排序证书数量的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | 0 - 成功。<br>         2305001 - 未指定的错误。<br>         2305002 - 无法获取颁发者证书。<br>         2305004 - 无法解密证书签名。<br>         2305006 - 无法解码颁发者公钥。<br>         2305007 - 证书签名失败。<br>         2305009 - 证书尚未生效。<br>         2305010 - 证书已过期。<br>         2305024 - 无效的证书颁发机构(CA)。<br>         2305062 - 主机名验证失败。<br>         2305027 - 证书不受信任。 |

### OH_NetStack_FreeCertChain()

```c
void OH_NetStack_FreeCertChain(struct NetStack_CertBlob *certChain, size_t certCount)
```

**描述**

释放由OH_NetStack_CreateAndVerifySortedCertChain分配的证书链。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct NetStack_CertBlob](capi-netstack-netstack-certblob.md) *certChain | 从outSortedChain接收的证书链指针。如果为NULL，此函数不执行任何操作。 |
| size_t certCount | 证书链中的证书数量。 |


