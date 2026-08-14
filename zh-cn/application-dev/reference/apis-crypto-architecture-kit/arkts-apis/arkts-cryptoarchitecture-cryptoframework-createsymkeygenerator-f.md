# createSymKeyGenerator

## createSymKeyGenerator

```TypeScript
function createSymKeyGenerator(algName: string): SymKeyGenerator
```

创建对应算法的对称密钥生成器实例。 &lt;br&gt;支持的规格详见 [对称密钥生成和转换规格](../../../security/CryptoArchitectureKit/crypto-key-generation-conversion.md)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-cryptoFramework-function createSymKeyGenerator(algName: string): SymKeyGenerator--><!--Device-cryptoFramework-function createSymKeyGenerator(algName: string): SymKeyGenerator-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.SymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| algName | string | 是 | 待生成对称密钥生成器的算法名称。&lt;br&gt;具体取值详见 [对称密钥生成和转换规格](../../../security/CryptoArchitectureKit/crypto-key-generation-conversion.md) 一节中的“字符串参数”。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SymKeyGenerator](arkts-cryptoarchitecture-cryptoframework-symkeygenerator-i.md) | 返回对称密钥生成器实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因： &lt;br&gt;1. 必填参数未指定； &lt;br&gt;2. 参数类型不正确； &lt;br&gt;3. 参数验证失败。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该操作不支持。 |

## 示例

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let symKeyGenerator = cryptoFramework.createSymKeyGenerator('3DES192');
```

