# X509CRL

X.509 CRL操作。

**起始版本：** 11

<!--Device-cert-interface X509CRL--><!--Device-cert-interface X509CRL-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

<a id="getencoded"></a>
## getEncoded

```TypeScript
getEncoded(callback: AsyncCallback<EncodingBlob>): void
```

表示获取X509证书吊销列表的序列化数据。使用Callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getEncoded(callback: AsyncCallback<EncodingBlob>): void--><!--Device-X509CRL-getEncoded(callback: AsyncCallback<EncodingBlob>): void-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;EncodingBlob&gt; | 是 | 回调函数。当获取X509证书吊销列表序列化数据成功时，err为undefined，data为获取到的X509证书吊销列表序列化数据；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确； |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="getencoded-1"></a>
## getEncoded

```TypeScript
getEncoded(): Promise<EncodingBlob>
```

表示获取X509证书吊销列表的序列化数据。使用Promise方式返回结果。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getEncoded(): Promise<EncodingBlob>--><!--Device-X509CRL-getEncoded(): Promise<EncodingBlob>-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;EncodingBlob&gt; | Promise对象，返回X509证书吊销列表的序列化数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确； |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="getextensions"></a>
## getExtensions

```TypeScript
getExtensions(): DataBlob
```

表示获取CRL扩展的DER格式数据。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getExtensions(): DataBlob--><!--Device-X509CRL-getExtensions(): DataBlob-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataBlob](arkts-devicecertificate-cert-datablob-i.md) | 表示CRL扩展的DER格式数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="getextensionsobject"></a>
## getExtensionsObject

```TypeScript
getExtensionsObject(): CertExtension
```

获取CRL扩展对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getExtensionsObject(): CertExtension--><!--Device-X509CRL-getExtensionsObject(): CertExtension-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CertExtension](arkts-devicecertificate-cert-certextension-i.md) | CRL扩展对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="getissuername"></a>
## getIssuerName

```TypeScript
getIssuerName(): DataBlob
```

表示获取X509证书吊销列表颁发者名称。

> **说明：**  
>  
> 获取到的X509证书吊销列表颁发者名称数据带字符串结束符。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getIssuerName(): DataBlob--><!--Device-X509CRL-getIssuerName(): DataBlob-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataBlob](arkts-devicecertificate-cert-datablob-i.md) | 表示X509证书吊销列表颁发者名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="getissuername-1"></a>
## getIssuerName

```TypeScript
getIssuerName(encodingType: EncodingType): string
```

根据编码类型获取X509证书吊销列表颁发者名称。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getIssuerName(encodingType: EncodingType): string--><!--Device-X509CRL-getIssuerName(encodingType: EncodingType): string-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encodingType | [EncodingType](arkts-devicecertificate-cert-encodingtype-e.md) | 是 | 表示编码类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示X509证书吊销列表颁发者名称，使用逗号分隔相对可分辨名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19020003](../errorcode-cert.md#19020003-参数检查失败) | 参数检查失败。可能的原因：<br>1. encodingType的值不在EncodingType枚举范围内。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="getissuerx500distinguishedname"></a>
## getIssuerX500DistinguishedName

```TypeScript
getIssuerX500DistinguishedName(): X500DistinguishedName
```

获取CRL颁发者的X.500可分辨名称对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getIssuerX500DistinguishedName(): X500DistinguishedName--><!--Device-X509CRL-getIssuerX500DistinguishedName(): X500DistinguishedName-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [X500DistinguishedName](arkts-devicecertificate-cert-x500distinguishedname-i.md) | X.500可分辨名称对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="getlastupdate"></a>
## getLastUpdate

```TypeScript
getLastUpdate(): string
```

表示获取X509证书吊销列表最后一次更新日期，日期为ASN.1时间格式。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getLastUpdate(): string--><!--Device-X509CRL-getLastUpdate(): string-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示X509证书吊销列表最后一次更新日期，日期为ASN.1时间格式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="getnextupdate"></a>
## getNextUpdate

```TypeScript
getNextUpdate(): string
```

表示获取证书吊销列表下一次更新的日期，日期为ASN.1时间格式。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getNextUpdate(): string--><!--Device-X509CRL-getNextUpdate(): string-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示X509证书吊销列表下一次更新的日期，日期为ASN.1时间格式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="getrevokedcert"></a>
## getRevokedCert

```TypeScript
getRevokedCert(serialNumber: bigint): X509CRLEntry
```

表示通过指定证书序列号获取证书吊销条目。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getRevokedCert(serialNumber: bigint): X509CRLEntry--><!--Device-X509CRL-getRevokedCert(serialNumber: bigint): X509CRLEntry-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| serialNumber | bigint | 是 | 表示证书序列号。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [X509CRLEntry](arkts-devicecertificate-cert-x509crlentry-i.md) | 表示证书吊销条目。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数校验失败。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="getrevokedcertwithcert"></a>
## getRevokedCertWithCert

```TypeScript
getRevokedCertWithCert(cert: X509Cert): X509CRLEntry
```

表示通过指定证书对象获取证书吊销条目。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getRevokedCertWithCert(cert: X509Cert): X509CRLEntry--><!--Device-X509CRL-getRevokedCertWithCert(cert: X509Cert): X509CRLEntry-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cert | [X509Cert](arkts-devicecertificate-cert-x509cert-i.md) | 是 | 表示证书对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [X509CRLEntry](arkts-devicecertificate-cert-x509crlentry-i.md) | 表示证书吊销条目。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数校验失败。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="getrevokedcerts"></a>
## getRevokedCerts

```TypeScript
getRevokedCerts(callback: AsyncCallback<Array<X509CRLEntry>>): void
```

表示获取证书吊销条目列表。使用Callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getRevokedCerts(callback: AsyncCallback<Array<X509CRLEntry>>): void--><!--Device-X509CRL-getRevokedCerts(callback: AsyncCallback<Array<X509CRLEntry>>): void-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;X509CRLEntry&gt;&gt; | 是 | 回调函数。当获取证书吊销条目列表成功时，err为undefined，data为获取到的证书吊销条目列表；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确； |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="getrevokedcerts-1"></a>
## getRevokedCerts

```TypeScript
getRevokedCerts(): Promise<Array<X509CRLEntry>>
```

表示获取证书吊销条目列表。使用Promise方式返回结果。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getRevokedCerts(): Promise<Array<X509CRLEntry>>--><!--Device-X509CRL-getRevokedCerts(): Promise<Array<X509CRLEntry>>-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;X509CRLEntry&gt;&gt; | Promise对象，返回证书吊销条目列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确； |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="getsignature"></a>
## getSignature

```TypeScript
getSignature(): DataBlob
```

表示获取X509证书吊销列表的签名数据。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getSignature(): DataBlob--><!--Device-X509CRL-getSignature(): DataBlob-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataBlob](arkts-devicecertificate-cert-datablob-i.md) | 表示X509证书吊销列表的签名数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="getsignaturealgname"></a>
## getSignatureAlgName

```TypeScript
getSignatureAlgName(): string
```

表示获取X509证书吊销列表签名的算法名称。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getSignatureAlgName(): string--><!--Device-X509CRL-getSignatureAlgName(): string-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示X509证书吊销列表签名的算法名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="getsignaturealgoid"></a>
## getSignatureAlgOid

```TypeScript
getSignatureAlgOid(): string
```

表示获取X509证书吊销列表签名算法的对象标识符OID（Object Identifier）。OID是由国际标准化组织（ISO）的名称注册机构分配。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getSignatureAlgOid(): string--><!--Device-X509CRL-getSignatureAlgOid(): string-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示X509证书吊销列表签名算法的对象标识符OID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="getsignaturealgparams"></a>
## getSignatureAlgParams

```TypeScript
getSignatureAlgParams(): DataBlob
```

表示获取X509证书吊销列表签名的算法参数。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getSignatureAlgParams(): DataBlob--><!--Device-X509CRL-getSignatureAlgParams(): DataBlob-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataBlob](arkts-devicecertificate-cert-datablob-i.md) | 表示X509证书吊销列表签名的算法参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 不支持该操作。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="gettbsinfo"></a>
## getTBSInfo

```TypeScript
getTBSInfo(): DataBlob
```

表示获取证书吊销列表的tbsCertList信息。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getTBSInfo(): DataBlob--><!--Device-X509CRL-getTBSInfo(): DataBlob-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataBlob](arkts-devicecertificate-cert-datablob-i.md) | 表示证书吊销列表的tbsCertList信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="gettype"></a>
## getType

```TypeScript
getType(): string
```

表示获取证书吊销列表类型。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getType(): string--><!--Device-X509CRL-getType(): string-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示证书吊销列表类型。 |

<a id="getversion"></a>
## getVersion

```TypeScript
getVersion(): number
```

表示获取X509证书吊销列表的版本号。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-getVersion(): int--><!--Device-X509CRL-getVersion(): int-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 表示获取X509证书吊销列表的版本号。 |

<a id="hashcode"></a>
## hashCode

```TypeScript
hashCode(): Uint8Array
```

获取DER格式数据的哈希值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-hashCode(): Uint8Array--><!--Device-X509CRL-hashCode(): Uint8Array-End-->

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

<a id="isrevoked"></a>
## isRevoked

```TypeScript
isRevoked(cert: X509Cert): boolean
```

表示检查证书是否吊销。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-isRevoked(cert: X509Cert): boolean--><!--Device-X509CRL-isRevoked(cert: X509Cert): boolean-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cert | [X509Cert](arkts-devicecertificate-cert-x509cert-i.md) | 是 | 表示被检查的证书对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示证书吊销状态，true表示已吊销，false表示未吊销。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数校验失败。 |

<a id="match"></a>
## match

```TypeScript
match(param: X509CRLMatchParameters): boolean
```

判断证书吊销列表是否与输入参数匹配。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-match(param: X509CRLMatchParameters): boolean--><!--Device-X509CRL-match(param: X509CRLMatchParameters): boolean-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [X509CRLMatchParameters](arkts-devicecertificate-cert-x509crlmatchparameters-i.md) | 是 | 表示需要匹配的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当参数匹配时，该方法返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数校验失败。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="tostring"></a>
## toString

```TypeScript
toString(): string
```

获取对象的字符串类型数据。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-toString(): string--><!--Device-X509CRL-toString(): string-End-->

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

<a id="tostring-1"></a>
## toString

```TypeScript
toString(encodingType: EncodingType): string
```

根据编码类型获取对象的字符串类型数据。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-toString(encodingType: EncodingType): string--><!--Device-X509CRL-toString(encodingType: EncodingType): string-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encodingType | [EncodingType](arkts-devicecertificate-cert-encodingtype-e.md) | 是 | 表示编码类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示对象的字符串类型数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19020003](../errorcode-cert.md#19020003-参数检查失败) | 参数检查失败。可能的原因：<br>1. encodingType的值不在EncodingType枚举范围内。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="verify"></a>
## verify

```TypeScript
verify(key: cryptoFramework.PubKey, callback: AsyncCallback<void>): void
```

表示对X509证书吊销列表进行验签。使用Callback异步回调。验签支持RSA算法。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-verify(key: cryptoFramework.PubKey, callback: AsyncCallback<void>): void--><!--Device-X509CRL-verify(key: cryptoFramework.PubKey, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | cryptoFramework.PubKey | 是 | 表示用于验签的公钥对象。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当验签成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数校验失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

<a id="verify-1"></a>
## verify

```TypeScript
verify(key: cryptoFramework.PubKey): Promise<void>
```

表示对X509证书吊销列表进行验签。使用Promise方式返回结果。验签支持RSA算法。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRL-verify(key: cryptoFramework.PubKey): Promise<void>--><!--Device-X509CRL-verify(key: cryptoFramework.PubKey): Promise<void>-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | cryptoFramework.PubKey | 是 | 表示用于验签的公钥对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数校验失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

