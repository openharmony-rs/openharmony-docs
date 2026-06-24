# createMac

## createMac

```TypeScript
function createMac(algName: string): Mac
```

生成Mac实例，用于消息认证码的计算与操作。

支持的规格详见[HMAC消息认证码算法规格](../../../../security/CryptoArchitectureKit/crypto-compute-mac-overview.md)。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Mac

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| algName | string | 是 | 指定摘要算法，支持算法请参考<br/>[HMAC消息认证码算法规格](../../../../security/CryptoArchitectureKit/crypto-compute-mac-overview.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Mac | 返回由输入算法指定生成的[Mac](arkts-cryptoarchitecture-cryptoframework-mac-i.md#Mac)对象。 |

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
  // Set algName based on the algorithm supported.
  let mac = cryptoFramework.createMac('SHA256');
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`sync failed: errCode: ${e.code}, errMsg: ${e.message}`);
}

```


## createMac

```TypeScript
function createMac(macSpec: MacSpec): Mac
```

生成Mac实例，用于进行消息认证码的计算与操作。

支持的规格详见[MAC消息认证码算法规格](../../../../security/CryptoArchitectureKit/crypto-compute-mac-overview.md)。

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Mac

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| macSpec | MacSpec | 是 | 根据消息验证码的不同算法，指定入参结构体，支持算法请参考<br/>[MAC消息认证码算法规格](../../../../security/CryptoArchitectureKit/crypto-compute-mac-overview.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Mac | 返回由指定入参结构体生成的[Mac](arkts-cryptoarchitecture-cryptoframework-mac-i.md#Mac)对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-非法入参) | 非法入参。可能的原因：<br/><br/>1. 必填参数未指定；<br/><br/>2. 参数类型不正确；<br/><br/>3. 参数验证失败。 |
| [17620001](../../errorcode-universal.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../../errorcode-universal.md#17620002-获取Native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../../errorcode-universal.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Set algName based on the algorithm supported.
  let spec: cryptoFramework.HmacSpec = {
    algName: 'HMAC',
    mdName: 'SHA256',
  };
  let mac = cryptoFramework.createMac(spec);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`sync failed: errCode: ${error.code}, errMsg: ${error.message}`);
}

```

