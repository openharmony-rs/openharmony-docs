# getMaxRotationSpeed（系统接口）

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

<a id="getmaxrotationspeed"></a>
## getMaxRotationSpeed

```TypeScript
function getMaxRotationSpeed(mechId: number): RotationSpeed
```

Obtains the maximum rotation speed of a mechanical device.

**起始版本：** 20

<!--Device-mechanicManager-function getMaxRotationSpeed(mechId: int): RotationSpeed--><!--Device-mechanicManager-function getMaxRotationSpeed(mechId: int): RotationSpeed-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mechId | number | 是 | ID of the mechanical device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RotationSpeed](arkts-mechanic-mechanicmanager-rotationspeed-i-sys.md) | Maximum speed. Only the absolute value of the speed is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |

**示例：**

```TypeScript
console.info('Query rotation speed');
let speedLimit: mechanicManager.RotationSpeed = mechanicManager.getMaxRotationSpeed(0);
console.info(`'Query rotation speed successful, speed limit information:' ${speedLimit}`);

```

