# X509CRLEntry

被吊销证书对象。

**起始版本：** 11

**系统能力：** SystemCapability.Security.Cert

## getCertIssuer

```TypeScript
getCertIssuer(): DataBlob
```

表示获取被吊销证书的颁发者信息。

> **说明：**
>
> 获取到的被吊销证书的颁发者信息数据带字符串结束符。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 表示被吊销证书的颁发者信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-不支持该操作) | 不支持该操作。 |
| [19020001](../../errorcode-universal.md#19020001-内存错误) | 内存错误。 |
| [19020002](../../errorcode-universal.md#19020002-运行时外部错误) | 运行时外部错误。可能的原因：<br/><br/>1. 内存拷贝失败；<br/><br/>2. 系统内部出现空指针；<br/><br/>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../../errorcode-universal.md#19030001-调用三方算法库API出错) | 调用三方算法库API出错。 |

## getCertIssuer

```TypeScript
getCertIssuer(encodingType: EncodingType): string
```

根据编码类型获取被吊销证书的颁发者信息。

**起始版本：** 20

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encodingType | EncodingType | 是 | 表示编码类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示被吊销证书的颁发者信息，使用逗号分隔相对可分辨名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-不支持该操作) | 不支持该操作。 |
| [19020001](../../errorcode-universal.md#19020001-内存错误) | 内存错误。 |
| [19020002](../../errorcode-universal.md#19020002-运行时外部错误) | 运行时外部错误。可能的原因：<br/><br/>1. 内存拷贝失败；<br/><br/>2. 系统内部出现空指针；<br/><br/>3. 获取Native对象失败或参数转换失败。 |
| [19020003](../../errorcode-universal.md#19020003-参数检查失败) | 参数检查失败。可能的原因：<br/><br/>1. encodingType的值不在EncodingType枚举范围内。 |
| [19030001](../../errorcode-universal.md#19030001-调用三方算法库API出错) | 调用三方算法库API出错。 |

## getCertIssuerX500DistinguishedName

```TypeScript
getCertIssuerX500DistinguishedName(): X500DistinguishedName
```

获取颁发者的X509可分辨名称。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| X500DistinguishedName | X509的可分辨对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../../errorcode-universal.md#19020001-内存错误) | 内存错误。 |
| [19020002](../../errorcode-universal.md#19020002-运行时外部错误) | 运行时外部错误。可能的原因：<br/><br/>1. 内存拷贝失败；<br/><br/>2. 系统内部出现空指针；<br/><br/>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../../errorcode-universal.md#19030001-调用三方算法库API出错) | 调用三方算法库API出错。 |

## getEncoded

```TypeScript
getEncoded(callback: AsyncCallback<EncodingBlob>): void
```

表示获取被吊销证书的序列化数据。使用Callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;EncodingBlob&gt; | 是 | 回调函数。当获取被吊销证书序列化数据成功时，err为undefined，<br/>data为获取到的被吊销证书序列化数据；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数错误) | 参数错误。可能的原因：<br/><br/>1. 必填参数未指定；<br/><br/>2. 参数类型不正确； |
| [19020001](../../errorcode-universal.md#19020001-内存错误) | 内存错误。 |
| [19020002](../../errorcode-universal.md#19020002-运行时外部错误) | 运行时外部错误。可能的原因：<br/><br/>1. 内存拷贝失败；<br/><br/>2. 系统内部出现空指针；<br/><br/>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../../errorcode-universal.md#19030001-调用三方算法库API出错) | 调用三方算法库API出错。 |

## getEncoded

```TypeScript
getEncoded(): Promise<EncodingBlob>
```

表示获取被吊销证书的序列化数据。使用Promise方式返回结果。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;EncodingBlob&gt; | Promise对象，返回被吊销证书的序列化数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数错误) | 参数错误。可能的原因：<br/><br/>1. 必填参数未指定；<br/><br/>2. 参数类型不正确； |
| [19020001](../../errorcode-universal.md#19020001-内存错误) | 内存错误。 |
| [19020002](../../errorcode-universal.md#19020002-运行时外部错误) | 运行时外部错误。可能的原因：<br/><br/>1. 内存拷贝失败；<br/><br/>2. 系统内部出现空指针；<br/><br/>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../../errorcode-universal.md#19030001-调用三方算法库API出错) | 调用三方算法库API出错。 |

## getExtensions

```TypeScript
getExtensions(): DataBlob
```

表示获取CRL的扩展。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 表示X509CRL扩展用途。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../../errorcode-universal.md#19020001-内存错误) | 内存错误。 |
| [19020002](../../errorcode-universal.md#19020002-运行时外部错误) | 运行时外部错误。可能的原因：<br/><br/>1. 内存拷贝失败；<br/><br/>2. 系统内部出现空指针；<br/><br/>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../../errorcode-universal.md#19030001-调用三方算法库API出错) | 调用三方算法库API出错。 |

## getExtensionsObject

```TypeScript
getExtensionsObject(): CertExtension
```

获取对应实体的扩展域DER格式数据。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CertExtension | 证书扩展域段类对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../../errorcode-universal.md#19020001-内存错误) | 内存错误。 |
| [19020002](../../errorcode-universal.md#19020002-运行时外部错误) | 运行时外部错误。可能的原因：<br/><br/>1. 内存拷贝失败；<br/><br/>2. 系统内部出现空指针；<br/><br/>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../../errorcode-universal.md#19030001-调用三方算法库API出错) | 调用三方算法库API出错。 |

## getRevocationDate

```TypeScript
getRevocationDate(): string
```

表示获取证书被吊销的日期。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示证书被吊销的日期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../../errorcode-universal.md#19020001-内存错误) | 内存错误。 |
| [19020002](../../errorcode-universal.md#19020002-运行时外部错误) | 运行时外部错误。可能的原因：<br/><br/>1. 内存拷贝失败；<br/><br/>2. 系统内部出现空指针；<br/><br/>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../../errorcode-universal.md#19030001-调用三方算法库API出错) | 调用三方算法库API出错。 |

## getSerialNumber

```TypeScript
getSerialNumber(): bigint
```

表示获取被吊销证书的序列号。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 表示被吊销证书的序列号。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../../errorcode-universal.md#19020001-内存错误) | 内存错误。 |
| [19020002](../../errorcode-universal.md#19020002-运行时外部错误) | 运行时外部错误。可能的原因：<br/><br/>1. 内存拷贝失败；<br/><br/>2. 系统内部出现空指针；<br/><br/>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../../errorcode-universal.md#19030001-调用三方算法库API出错) | 调用三方算法库API出错。 |

## hasExtensions

```TypeScript
hasExtensions(): boolean
```

表示判断CRL Entry是否有扩展。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true则表示CRL Entry有扩展，返回false则表示无扩展。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../../errorcode-universal.md#19020001-内存错误) | 内存错误。 |
| [19020002](../../errorcode-universal.md#19020002-运行时外部错误) | 运行时外部错误。可能的原因：<br/><br/>1. 内存拷贝失败；<br/><br/>2. 系统内部出现空指针；<br/><br/>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../../errorcode-universal.md#19030001-调用三方算法库API出错) | 调用三方算法库API出错。 |

## hashCode

```TypeScript
hashCode(): Uint8Array
```

获取DER格式数据的哈希值。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | DER格式数据的哈希值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../../errorcode-universal.md#19020001-内存错误) | 内存错误。 |
| [19020002](../../errorcode-universal.md#19020002-运行时外部错误) | 运行时外部错误。可能的原因：<br/><br/>1. 内存拷贝失败；<br/><br/>2. 系统内部出现空指针；<br/><br/>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../../errorcode-universal.md#19030001-调用三方算法库API出错) | 调用三方算法库API出错。 |

## toString

```TypeScript
toString(): string
```

获取对象的字符串类型数据。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 对象的字符串类型数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../../errorcode-universal.md#19020001-内存错误) | 内存错误。 |
| [19020002](../../errorcode-universal.md#19020002-运行时外部错误) | 运行时外部错误。可能的原因：<br/><br/>1. 内存拷贝失败；<br/><br/>2. 系统内部出现空指针；<br/><br/>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../../errorcode-universal.md#19030001-调用三方算法库API出错) | 调用三方算法库API出错。 |

