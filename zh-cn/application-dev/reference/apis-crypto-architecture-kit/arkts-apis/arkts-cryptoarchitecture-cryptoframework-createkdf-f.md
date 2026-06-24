# createKdf

## createKdf

```TypeScript
function createKdf(algName: string): Kdf
```

密钥派生函数（key derivation function）实例生成。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| algName | string | 是 | 指定密钥派生算法（包含HMAC配套的散列函数）：目前支持PBKDF2、HKDF、SCRYPT、X963KDF算法，<br/>如"PBKDF2\|SHA256", "HKDF\|SHA256", "SCRYPT", "X963KDF\|SHA256"。<br/>支持的规格详见<br/>[密钥派生函数规格](../../../../security/CryptoArchitectureKit/crypto-key-derivation-overview.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Kdf | 返回由输入算法指定生成的Kdf对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-非法入参) | 非法入参。可能的原因：<br/><br/>1. 必填参数未指定；<br/><br/>2. 参数类型不正确；<br/><br/>3. 参数验证失败。 |
| [801](../../errorcode-universal.md#801-该操作不支持) | 该操作不支持。 |
| [17620001](../../errorcode-universal.md#17620001-内存操作失败) | 内存操作失败。 |

**示例：**

PBKDF2算法

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let kdf = cryptoFramework.createKdf('PBKDF2|SHA256');

```

