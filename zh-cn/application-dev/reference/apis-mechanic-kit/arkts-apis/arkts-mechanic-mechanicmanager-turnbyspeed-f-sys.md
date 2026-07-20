# turnBySpeed（系统接口）

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

<a id="turnbyspeed"></a>
## turnBySpeed

```TypeScript
function turnBySpeed(mechId: number, angleSpeed: number, duration: number): Promise<Result>
```

Rotate in place according to the speed.

**起始版本：** 26.0.0

<!--Device-mechanicManager-function turnBySpeed(mechId: int, angleSpeed: double, duration: int): Promise<Result>--><!--Device-mechanicManager-function turnBySpeed(mechId: int, angleSpeed: double, duration: int): Promise<Result>-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mechId | number | 是 | ID of the mechanical device.<br>The value should be an integer. |
| angleSpeed | number | 是 | angular velocity. |
| duration | number | 是 | Duration of movement, unit ms.<br>The value should be an integer. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&gt; | Promise that returns the execution result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |
| [33300003](../errorcode-mechanic.md#33300003-功能不支持) | Feature not supported. |

