# certVerification

## 导入模块

```TypeScript
import { networkSecurity } from '@kit.NetworkKit';
```

## certVerification

```TypeScript
export function certVerification(cert: CertBlob, caCert?: CertBlob): Promise<int>
```

系统将使用证书管理中的预置CA证书和用户安装的CA证书来校验应用传入的证书。使用Promise异步回调。

**起始版本：** 23

<!--Device-networkSecurity-export function certVerification(cert: CertBlob, caCert?: CertBlob): Promise<int>--><!--Device-networkSecurity-export function certVerification(cert: CertBlob, caCert?: CertBlob): Promise<int>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cert | CertBlob | 是 | 被校验的证书。 |
| caCert | CertBlob | 否 | 传入自定义的CA证书。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | 以promise形式返回一个数字，表示证书验证的结果。如果证书验证成功，则返回0； 否则验证失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2305027](../errorcode-net-networkSecurity.md#2305027-证书不可信) | Certificate is untrusted. |
| [2305024](../errorcode-net-networkSecurity.md#2305024-无效的证书颁发机构ca) | Invalid certificate authority (CA). |
| [2305003](../errorcode-net-networkSecurity.md#2305003-获取证书吊销列表失败) | Unable to get certificate revocation list (CRL). |
| [2305002](../errorcode-net-networkSecurity.md#2305002-获取证书颁发者失败) | Unable to get issuer certificate. |
| [2305001](../errorcode-net-networkSecurity.md#2305001-未定义的错误) | Unspecified error. |
| [2305007](../errorcode-net-networkSecurity.md#2305007-证书签名失败) | Certificate signature failure. |
| [2305006](../errorcode-net-networkSecurity.md#2305006-无法解码颁发者公钥) | Unable to decode issuer public key. |
| [2305005](../errorcode-net-networkSecurity.md#2305005-无法解密证书吊销列表签名) | Unable to decrypt CRL signature. |
| [2305069](../errorcode-net-networkSecurity.md#2305069-无效的证书验证上下文) | Invalid certificate verification context.<br>**适用版本：** 12+ |
| [2305004](../errorcode-net-networkSecurity.md#2305004-无法解密证书签名) | Unable to decrypt certificate signature. |
| [2305011](../errorcode-net-networkSecurity.md#2305011-crl尚未生效) | CRL is not yet valid. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2305010](../errorcode-net-networkSecurity.md#2305010-证书已过期) | Certificate has expired. |
| [2305009](../errorcode-net-networkSecurity.md#2305009-证书尚未生效) | Certificate is not yet valid. |
| [2305008](../errorcode-net-networkSecurity.md#2305008-证书吊销列表签名失败) | CRL signature failure. |
| [2305012](../errorcode-net-networkSecurity.md#2305012-crl已过期) | CRL has expired. |
| [2305018](../errorcode-net-networkSecurity.md#2305018-自签名证书) | Self-signed certificate.<br>**适用版本：** 12+ |
| [2305023](../errorcode-net-networkSecurity.md#2305023-证书已被吊销) | Certificate has been revoked. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { networkSecurity } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 定义证书数据块
const cert:networkSecurity.CertBlob = {
  type: networkSecurity.CertType.CERT_TYPE_PEM,
  data: '-----BEGIN CERTIFICATE-----\n... (certificate data) ...\n-----END CERTIFICATE-----',
};

const caCert:networkSecurity.CertBlob = {
  type: networkSecurity.CertType.CERT_TYPE_PEM,
  data: '-----BEGIN CERTIFICATE-----\n... (CA certificate data) ...\n-----END CERTIFICATE-----',
};

// 执行异步证书验证
networkSecurity.certVerification(cert, caCert)
  .then((result) => {
    console.info('Certificate verification result:', result);
  })
  .catch((error: BusinessError) => {
    console.error('Certificate verification failed:', error);
  });
```

ArkTS-Sta示例：

```TypeScript
import { networkSecurity } from '@kit.NetworkKit';

// 定义证书数据块
const cert:networkSecurity.CertBlob = {
  type: networkSecurity.CertType.CERT_TYPE_PEM,
  data: '-----BEGIN CERTIFICATE-----\n... (certificate data) ...\n-----END CERTIFICATE-----',
};

const caCert:networkSecurity.CertBlob = {
  type: networkSecurity.CertType.CERT_TYPE_PEM,
  data: '-----BEGIN CERTIFICATE-----\n... (CA certificate data) ...\n-----END CERTIFICATE-----',
};

// 执行异步证书验证
networkSecurity.certVerification(cert, caCert)
  .then((result) => {
    console.info('Certificate verification result:', result);
  })
  .catch((error: Error) => {
    console.error('Certificate verification failed:', error);
  });
```

