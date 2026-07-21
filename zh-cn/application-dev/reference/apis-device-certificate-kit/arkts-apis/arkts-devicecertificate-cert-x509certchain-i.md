# X509CertChain

X509证书链对象。

**起始版本：** 11

<!--Device-cert-interface X509CertChain--><!--Device-cert-interface X509CertChain-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

<a id="getcertlist"></a>
## getCertList

```TypeScript
getCertList(): Array<X509Cert>
```

获取X509证书列表。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertChain-getCertList(): Array<X509Cert>--><!--Device-X509CertChain-getCertList(): Array<X509Cert>-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;X509Cert&gt; | X509证书数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数校验失败。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="hashcode"></a>
## hashCode

```TypeScript
hashCode(): Uint8Array
```

获取DER格式数据的哈希值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertChain-hashCode(): Uint8Array--><!--Device-X509CertChain-hashCode(): Uint8Array-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | DER格式数据的哈希值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="tostring"></a>
## toString

```TypeScript
toString(): string
```

获取对象的字符串类型数据。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertChain-toString(): string--><!--Device-X509CertChain-toString(): string-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 对象的字符串类型数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="validate"></a>
## validate

```TypeScript
validate(param: CertChainValidationParameters): Promise<CertChainValidationResult>
```

校验证书链。使用Promise方式返回结果。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertChain-validate(param: CertChainValidationParameters): Promise<CertChainValidationResult>--><!--Device-X509CertChain-validate(param: CertChainValidationParameters): Promise<CertChainValidationResult>-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [CertChainValidationParameters](arkts-devicecertificate-cert-certchainvalidationparameters-i.md) | 是 | 表示校验X509证书链的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CertChainValidationResult&gt; | Promise对象，返回证书链校验结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数校验失败。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |
| [19030002](../errorcode-cert.md#19030002-证书签名验证错误) | 证书签名验证错误。 |
| [19030003](../errorcode-cert.md#19030003-证书尚未生效) | 证书尚未生效。 |
| [19030004](../errorcode-cert.md#19030004-证书过期) | 证书过期。 |
| [19030005](../errorcode-cert.md#19030005-无法获取证书的颁发者) | 无法获取证书的颁发者。 |
| [19030006](../errorcode-cert.md#19030006-证书的密钥用途不含证书签名) | 证书的密钥用途不含证书签名。 |
| [19030007](../errorcode-cert.md#19030007-证书的密钥用途不含数字签名) | 证书的密钥用途不含数字签名。 |

<a id="validate-1"></a>
## validate

```TypeScript
validate(param: CertChainValidationParameters, callback: AsyncCallback<CertChainValidationResult>): void
```

使用校验参数校验证书链。使用Callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertChain-validate(param: CertChainValidationParameters, callback: AsyncCallback<CertChainValidationResult>): void--><!--Device-X509CertChain-validate(param: CertChainValidationParameters, callback: AsyncCallback<CertChainValidationResult>): void-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [CertChainValidationParameters](arkts-devicecertificate-cert-certchainvalidationparameters-i.md) | 是 | 表示校验X509证书链的参数。 |
| callback | AsyncCallback&lt;CertChainValidationResult&gt; | 是 | 回调函数。当校验证书链成功时，err为undefined，data为获取到的证书链校验结果；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数校验失败。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |
| [19030002](../errorcode-cert.md#19030002-证书签名验证错误) | 证书签名验证错误。 |
| [19030003](../errorcode-cert.md#19030003-证书尚未生效) | 证书尚未生效。 |
| [19030004](../errorcode-cert.md#19030004-证书过期) | 证书过期。 |
| [19030005](../errorcode-cert.md#19030005-无法获取证书的颁发者) | 无法获取证书的颁发者。 |
| [19030006](../errorcode-cert.md#19030006-证书的密钥用途不含证书签名) | 证书的密钥用途不含证书签名。 |
| [19030007](../errorcode-cert.md#19030007-证书的密钥用途不含数字签名) | 证书的密钥用途不含数字签名。 |

