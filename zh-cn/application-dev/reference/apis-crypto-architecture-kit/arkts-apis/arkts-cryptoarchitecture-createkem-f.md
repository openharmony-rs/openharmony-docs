# createKem

## createKem

```TypeScript
function createKem(algNameId: KemAlgNameId): Kem
```

创建一个用于密钥封装和解封装操作的KEM实例。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| algNameId | KemAlgNameId | 是 | KEM的算法名称ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Kem | KEM实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

function createKem() {
  try {
    let kem = cryptoFramework.createKem(cryptoFramework.KemAlgNameId.ML_KEM_768);
    console.info('create kem success');
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`create kem failed: errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

```

