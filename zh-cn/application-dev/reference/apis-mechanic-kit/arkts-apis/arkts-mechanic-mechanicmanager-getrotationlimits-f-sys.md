# getRotationLimits（系统接口）

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

<a id="getrotationlimits"></a>
## getRotationLimits

```TypeScript
function getRotationLimits(mechId: number): RotationLimits
```

Obtains the maximum rotation angles relative to the reference point for the specified mechanical device.

**起始版本：** 20

<!--Device-mechanicManager-function getRotationLimits(mechId: int): RotationLimits--><!--Device-mechanicManager-function getRotationLimits(mechId: int): RotationLimits-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mechId | number | 是 | ID of the mechanical device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RotationLimits](arkts-mechanic-mechanicmanager-rotationlimits-i-sys.md) | Maximum rotation angles. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |

**示例：**

```TypeScript
console.info('Query rotation limit information');
let degreeLimit: mechanicManager.RotationLimits = mechanicManager.getRotationLimits(0);
console.info(`'Query the rotation limit information successfully, limit information:' ${degreeLimit}`);

```

