# createVerify

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## createVerify

```TypeScript
function createVerify(algName: string): Verify
```

创建验签实例。 <br>支持的规格详见[签名验签规格](../../../security/CryptoArchitectureKit/crypto-sign-sig-verify-overview.md)。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-cryptoFramework-function createVerify(algName: string): Verify--><!--Device-cryptoFramework-function createVerify(algName: string): Verify-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| algName | string | 是 | 指定签名验证算法。当前支持RSA、ECC、DSA、SM2&lt;sup&gt;10+&lt;/sup&gt;，Ed25519&lt;sup&gt;11+&lt;/sup&gt;和 ML-DSA&lt;sup&gt;26.0.0+&lt;/sup&gt;。 <br>使用RSA PKCS1模式时需设置摘要；使用RSA PSS模式时需设置摘要和掩码摘要。使用RSA算法验签时，设置recover参数可支持验签恢复。 <br>支持的规格详见 [签名验签规格](../../../security/CryptoArchitectureKit/crypto-sign-sig-verify-overview.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Verify](arkts-cryptoarchitecture-cryptoframework-verify-i.md) | 返回对应算法的Verify实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | This operation is not supported. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |

**示例**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let verifier1 = cryptoFramework.createVerify('RSA1024|PKCS1|SHA256');

let verifier2 = cryptoFramework.createVerify('RSA1024|PSS|SHA256|MGF1_SHA256');

let verifier3 = cryptoFramework.createVerify('RSA1024|PKCS1|SHA256|Recover');
```

