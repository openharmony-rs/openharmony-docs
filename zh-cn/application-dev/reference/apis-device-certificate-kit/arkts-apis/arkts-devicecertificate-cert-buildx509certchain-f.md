# buildX509CertChain

## buildX509CertChain

```TypeScript
function buildX509CertChain(param: CertChainBuildParameters): Promise<CertChainBuildResult>
```

表示使用CertChainBuildParameters对象方式创建X509证书链对象。使用Promise方式返回结果。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | CertChainBuildParameters | 是 | 构建证书链的参数对象。<br/><br/>[CertChainBuildParameters](arkts-devicecertificate-cert-certchainbuildparameters-i.md#CertChainBuildParameters)中的maxLength要小于证书集合中证书数量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CertChainBuildResult&gt; | Promise对象，返回创建的CertChainBuildResult实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数错误) | 参数错误。可能的原因：<br/><br/>1. 必填参数未指定；<br/><br/>2. 参数类型不正确；<br/><br/>3. 参数校验失败。 |
| [19020001](../../errorcode-universal.md#19020001-内存错误) | 内存错误。 |
| [19020002](../../errorcode-universal.md#19020002-运行时外部错误) | 运行时外部错误。可能的原因：<br/><br/>1. 内存拷贝失败；<br/><br/>2. 系统内部出现空指针；<br/><br/>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../../errorcode-universal.md#19030001-调用三方算法库API出错) | 调用三方算法库API出错。 |
| [19030002](../../errorcode-universal.md#19030002-证书签名验证错误) | 证书签名验证错误。 |
| [19030003](../../errorcode-universal.md#19030003-证书尚未生效) | 证书尚未生效。 |
| [19030004](../../errorcode-universal.md#19030004-证书过期) | 证书过期。 |
| [19030005](../../errorcode-universal.md#19030005-无法获取证书的颁发者) | 无法获取证书的颁发者。 |
| [19030006](../../errorcode-universal.md#19030006-证书的密钥用途不含证书签名) | 证书的密钥用途不含证书签名。 |
| [19030007](../../errorcode-universal.md#19030007-证书的密钥用途不含数字签名) | 证书的密钥用途不含数字签名。 |

