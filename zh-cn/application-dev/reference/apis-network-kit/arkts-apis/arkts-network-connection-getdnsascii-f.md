# getDnsAscii

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getDnsAscii

```TypeScript
function getDnsAscii(host: string, flag?: ConversionProcess): string
```

将Unicode编码形式的主机名转换为ASCII编码形式，并可通过可选的转换流程参数（conversionProcess）控制转换行为。 > **说明：** > > conversionProcess设置为NO_CONFIGURATION时，只能转换已正式分配含义的Unicode字符所对应的域名。 > conversionProcess设置为ALLOW_UNASSIGNED时，可以转换包含尚未分配含义的Unicode字符的域名。 > conversionProcess设置为USE_STD3_ASCII_RULES时，会在转换过程中强制按照STD-3 ASCII规则（即RFC 1123标准）对生成的ASCII域名进行检查。 > 传入参数中的数字和英文不做转码。

**起始版本：** 23

<!--Device-connection-function getDnsAscii(host: string, flag?: ConversionProcess): string--><!--Device-connection-function getDnsAscii(host: string, flag?: ConversionProcess): string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| host | string | 是 | 要转换的主机名（host）。每个标签（点分隔的部分）长度不超过63字节。 |
| flag | [ConversionProcess](arkts-network-connection-conversionprocess-e.md) | 否 | 转换流程参数，默认值为NO_CONFIGURATION。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回转换结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

let result = connection.getDnsAscii("www.示例.com", connection.ConversionProcess.NO_CONFIGURATION);
console.info("Succeeded to getDnsAscii: " + result);  // 预期结果：www.xn--fsq092h.com
let result = connection.getDnsAscii("www.example.com", connection.ConversionProcess.NO_CONFIGURATION);
console.info("Succeeded to getDnsAscii: " + result);  // 预期结果：www.example.com
```

