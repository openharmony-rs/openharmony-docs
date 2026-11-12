# verifyCertChain

## 导入模块

```TypeScript
import { networkSecurity } from '@kit.NetworkKit';
```

## verifyCertChain

```TypeScript
export function verifyCertChain(cert: CertBlob[], caCert?: CertBlob, hostname?: string): Promise<CertBlob[]>
```

传入证书链数组，进行证书链校验并构建排序后的证书链。系统将使用证书管理中的预置CA证书和用户安装的CA证书来配合校验传入的证书。使用Promise异步回调。

> **说明：** 
> 
> 这些错误代码对应于证书验证过程中的各种失败。
> 
> **注意：**
> 
> 请务必将示例中的证书数据替换为实际的证书内容。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-networkSecurity-export function verifyCertChain(cert: CertBlob[], caCert?: CertBlob, hostname?: string): Promise<CertBlob[]>--><!--Device-networkSecurity-export function verifyCertChain(cert: CertBlob[], caCert?: CertBlob, hostname?: string): Promise<CertBlob[]>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cert | [CertBlob](arkts-network-networksecurity-certblob-i.md)[] | 是 | 待校验证书数组。第一个元素必须是叶子证书（end-entity certificate），其余元素为中间证书。 |
| caCert | [CertBlob](arkts-network-networksecurity-certblob-i.md) | 否 | 传入自定义的CA证书。不传入则使用系统预置CA证书。 |
| hostname | string | 否 | 需要验证的主机名，用于校验证书中的主机名是否匹配。不传入则跳过主机名验证。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[CertBlob](arkts-network-networksecurity-certblob-i.md)[]&gt; | Promise对象，返回排序后的证书链数组，顺序为从叶子节点到根节点。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2305001](../errorcode-net-networkSecurity.md#2305001-未定义的错误) | Unspecified error. |
| [2305002](../errorcode-net-networkSecurity.md#2305002-获取证书颁发者失败) | Unable to get issuer certificate. |
| [2305004](../errorcode-net-networkSecurity.md#2305004-无法解密证书签名) | Unable to decrypt certificate signature. |
| [2305006](../errorcode-net-networkSecurity.md#2305006-无法解码颁发者公钥) | Unable to decode issuer public key. |
| [2305007](../errorcode-net-networkSecurity.md#2305007-证书签名失败) | Certificate signature failure. |
| [2305009](../errorcode-net-networkSecurity.md#2305009-证书尚未生效) | Certificate is not yet valid. |
| [2305010](../errorcode-net-networkSecurity.md#2305010-证书已过期) | Certificate has expired. |
| [2305018](../errorcode-net-networkSecurity.md#2305018-自签名证书) | Self-signed certificate. |
| [2305024](../errorcode-net-networkSecurity.md#2305024-无效的证书颁发机构ca) | Invalid certificate authority (CA). |
| [2305027](../errorcode-net-networkSecurity.md#2305027-证书不可信) | Certificate is untrusted. |
| [2305062](../errorcode-net-networkSecurity.md#2305062-主机名验证失败) | Invalid hostname. |
| [2305069](../errorcode-net-networkSecurity.md#2305069-无效的证书验证上下文) | Invalid certificate verification context. |

**示例**

```TypeScript
import { networkSecurity } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Define certificate blobs
const cert1: networkSecurity.CertBlob = {
  type: networkSecurity.CertType.CERT_TYPE_PEM,
  data: '-----BEGIN CERTIFICATE-----\n... (server certificate) ...\n-----END CERTIFICATE-----',
};

const cert2: networkSecurity.CertBlob = {
  type: networkSecurity.CertType.CERT_TYPE_PEM,
  data: '-----BEGIN CERTIFICATE-----\n... (intermediate certificate) ...\n-----END CERTIFICATE-----',
};

const caCert: networkSecurity.CertBlob = {
  type: networkSecurity.CertType.CERT_TYPE_PEM,
  data: '-----BEGIN CERTIFICATE-----\n... (CA certificate) ...\n-----END CERTIFICATE-----',
};

// Verify and build sorted cert chain
networkSecurity.verifyCertChain([cert1, cert2], caCert, "example.com")
  .then((sortedChain: Array<networkSecurity.CertBlob>) => {
    console.info('Certificate chain verified and sorted, chain length:', sortedChain.length);
    for (let i = 0; i < sortedChain.length; i++) {
      console.info(`Certificate ${i}: type=${sortedChain[i].type}, data=${sortedChain[i].data}`);
    }
  })
  .catch((error: BusinessError) => {
    console.error('Certificate chain verification failed:', error);
  });
```
