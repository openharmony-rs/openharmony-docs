# createVerify

## createVerify

```TypeScript
function createVerify(algName: string): Verify
```

创建验签实例。 &lt;br&gt;支持的规格详见[签名验签规格](../../../security/CryptoArchitectureKit/crypto-sign-sig-verify-overview.md)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-cryptoFramework-function createVerify(algName: string): Verify--><!--Device-cryptoFramework-function createVerify(algName: string): Verify-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| algName | string | 是 | 指定签名验证算法。当前支持RSA、ECC、DSA、SM2&lt;sup&gt;10+&lt;/sup&gt;，Ed25519&lt;sup&gt;11+&lt;/sup&gt;和 ML-DSA&lt;sup&gt;26.0.0+&lt;/sup&gt;。 &lt;br&gt;使用RSA PKCS1模式时需设置摘要；使用RSA PSS模式时需设置摘要和掩码摘要。使用RSA算法验签时，设置recover参数可支持验签恢复。 &lt;br&gt;支持的规格详见 [签名验签规格](../../../security/CryptoArchitectureKit/crypto-sign-sig-verify-overview.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Verify](arkts-cryptoarchitecture-cryptoframework-verify-i.md) | 返回对应算法的Verify实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因： &lt;br&gt;1. 必填参数未指定； &lt;br&gt;2. 参数类型不正确； &lt;br&gt;3. 参数验证失败。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该操作不支持。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |

## 示例

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let verifier1 = cryptoFramework.createVerify('RSA1024|PKCS1|SHA256');

let verifier2 = cryptoFramework.createVerify('RSA1024|PSS|SHA256|MGF1_SHA256');

let verifier3 = cryptoFramework.createVerify('RSA1024|PKCS1|SHA256|Recover');
```

