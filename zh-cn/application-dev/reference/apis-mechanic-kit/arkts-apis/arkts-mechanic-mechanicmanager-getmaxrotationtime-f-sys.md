# getMaxRotationTime（系统接口）

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

<a id="getmaxrotationtime"></a>
## getMaxRotationTime

```TypeScript
function getMaxRotationTime(mechId: number): number
```

Obtains the maximum continuous rotation duration of a mechanical device.

**起始版本：** 20

<!--Device-mechanicManager-function getMaxRotationTime(mechId: int): int--><!--Device-mechanicManager-function getMaxRotationTime(mechId: int): int-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mechId | number | 是 | ID of the mechanical device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Maximum rotation duration. Unit: millisecond. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |

**示例：**

```TypeScript
console.info('Query maximum rotation time');
let maxTime = mechanicManager.getMaxRotationTime(0);
console.info(`'Query maximum rotation time successful, maximum time:' ${maxTime}`);

```

