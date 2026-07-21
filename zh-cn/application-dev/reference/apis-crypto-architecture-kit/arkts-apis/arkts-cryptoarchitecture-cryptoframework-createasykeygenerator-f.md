# createAsyKeyGenerator

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

<a id="createasykeygenerator"></a>
## createAsyKeyGenerator

```TypeScript
function createAsyKeyGenerator(algName: string): AsyKeyGenerator
```

通过指定算法名称的字符串，获取相应的非对称密钥生成器实例。

支持的规格详见[非对称密钥生成和转换规格](../../../security/CryptoArchitectureKit/crypto-asym-key-generation-conversion-spec.md)。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-cryptoFramework-function createAsyKeyGenerator(algName: string): AsyKeyGenerator--><!--Device-cryptoFramework-function createAsyKeyGenerator(algName: string): AsyKeyGenerator-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| algName | string | 是 | 非对称密钥生成支持的算法名。详见[非对称密钥生成和转换规格](../../../security/CryptoArchitectureKit/crypto-asym-key-generation-conversion-spec.md)一节中的“字符串参数”。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AsyKeyGenerator](arkts-cryptoarchitecture-cryptoframework-asykeygenerator-i.md) | 返回非对称密钥生成器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该操作不支持。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ECC256');

```

