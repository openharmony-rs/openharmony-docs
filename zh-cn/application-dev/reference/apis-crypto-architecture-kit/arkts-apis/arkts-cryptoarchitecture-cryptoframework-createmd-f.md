# createMd

## createMd

```TypeScript
function createMd(algName: string): Md
```

生成Md实例，用于进行消息摘要的计算与操作。

支持的规格详见
[MD消息摘要算法规格](../../../../security/CryptoArchitectureKit/crypto-generate-message-digest-overview.md#支持的算法与规格)。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.MessageDigest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| algName | string | 是 | 指定摘要算法，支持算法请参考<br/>[MD消息摘要算法规格](../../../../security/CryptoArchitectureKit/crypto-generate-message-digest-overview.md#支持的算法与规格)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Md | 返回由输入算法指定生成的[Md](arkts-cryptoarchitecture-cryptoframework-md-i.md#Md)对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-非法入参) | 非法入参。可能的原因：<br/><br/>1. 必填参数未指定；<br/><br/>2. 参数类型不正确；<br/><br/>3. 参数验证失败。 |
| [17620001](../../errorcode-universal.md#17620001-内存操作失败) | 内存操作失败。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let md = cryptoFramework.createMd('SHA256');
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`sync failed: errCode: ${e.code}, errMsg: ${e.message}`);
}

```

