# getRotationAxesStatus（系统接口）

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

<a id="getrotationaxesstatus"></a>
## getRotationAxesStatus

```TypeScript
function getRotationAxesStatus(mechId: number): RotationAxesStatus
```

Obtains the status of the rotation axes.

**起始版本：** 20

<!--Device-mechanicManager-function getRotationAxesStatus(mechId: int): RotationAxesStatus--><!--Device-mechanicManager-function getRotationAxesStatus(mechId: int): RotationAxesStatus-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mechId | number | 是 | ID of the mechanical device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RotationAxesStatus](arkts-mechanic-mechanicmanager-rotationaxesstatus-i-sys.md) | Rotation axis status. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |

**示例：**

```TypeScript
console.info('Query the rotation axis status');
let axisStatus: mechanicManager.RotationAxesStatus = mechanicManager.getRotationAxesStatus(0);
console.info(`'Query the rotation axis status successfully, axis state:' ${axisStatus}`);

```

