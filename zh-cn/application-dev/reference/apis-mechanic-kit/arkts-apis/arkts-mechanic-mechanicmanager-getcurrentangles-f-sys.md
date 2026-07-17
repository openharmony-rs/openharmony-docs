# getCurrentAngles（系统接口）

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## getCurrentAngles

```TypeScript
function getCurrentAngles(mechId: number): EulerAngles
```

Obtains the current angles of a mechanical device.

**起始版本：** 20

<!--Device-mechanicManager-function getCurrentAngles(mechId: int): EulerAngles--><!--Device-mechanicManager-function getCurrentAngles(mechId: int): EulerAngles-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mechId | number | 是 | ID of the mechanical device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EulerAngles](arkts-mechanic-mechanicmanager-eulerangles-i-sys.md) | Rotation angles. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |

**示例：**

```TypeScript
console.info('Query current location');
let currentAngles: mechanicManager.EulerAngles = mechanicManager.getCurrentAngles(0);
console.info(`'Query current location, location:' ${currentAngles}`);

```

