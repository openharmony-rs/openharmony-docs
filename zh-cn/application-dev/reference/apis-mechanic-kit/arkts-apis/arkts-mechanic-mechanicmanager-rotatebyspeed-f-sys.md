# rotateBySpeed（系统接口）

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

<a id="rotatebyspeed"></a>
## rotateBySpeed

```TypeScript
function rotateBySpeed(mechId: number, speed: RotationSpeed, duration: number): Promise<Result>
```

Rotates a mechanical device at the specified speed.

**起始版本：** 20

<!--Device-mechanicManager-function rotateBySpeed(mechId: int, speed: RotationSpeed, duration: int): Promise<Result>--><!--Device-mechanicManager-function rotateBySpeed(mechId: int, speed: RotationSpeed, duration: int): Promise<Result>-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mechId | number | 是 | ID of the mechanical device. |
| speed | [RotationSpeed](arkts-mechanic-mechanicmanager-rotationspeed-i-sys.md) | 是 | Rotation speed. |
| duration | number | 是 | Rotation duration. Unit: millisecond. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&gt; | Promise that return the execution result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |

**示例：**

```TypeScript
console.info('Start rotate');
let degree: mechanicManager.RotationSpeed = {
  yawSpeed: 3 * Math.PI,
  rollSpeed: 3 * Math.PI,
  pitchSpeed: 3 * Math.PI
}
mechanicManager.rotateBySpeed(0, degree, 500)
  .then((result) => {
    console.info(`'Rotate result:' ${result}`);
  });
console.info('Rotate finish');

```

