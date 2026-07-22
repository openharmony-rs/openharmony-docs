# createTrustAnchorsWithKeyStore

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## createTrustAnchorsWithKeyStore

```TypeScript
function createTrustAnchorsWithKeyStore(keystore: Uint8Array, pwd: string): Promise<Array<X509TrustAnchor>>
```

表示从P12中读取ca证书来构造[TrustAnchor](arkts-devicecertificate-cert-x509trustanchor-i.md)对象数组。使用Promise方式返回结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-cert-function createTrustAnchorsWithKeyStore(keystore: Uint8Array, pwd: string): Promise<Array<X509TrustAnchor>>--><!--Device-cert-function createTrustAnchorsWithKeyStore(keystore: Uint8Array, pwd: string): Promise<Array<X509TrustAnchor>>-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keystore | Uint8Array | 是 | DER格式的P12文件原始数据。 |
| pwd | string | 是 | 密码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;X509TrustAnchor&gt;&gt; | Promise对象，返回X509TrustAnchor对象数组。 |

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

