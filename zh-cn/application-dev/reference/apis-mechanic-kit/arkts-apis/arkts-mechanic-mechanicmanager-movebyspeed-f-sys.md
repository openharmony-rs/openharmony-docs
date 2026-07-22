# moveBySpeed（系统接口）

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## moveBySpeed

```TypeScript
function moveBySpeed(mechId: number, params: SpeedParams, duration: number): Promise<Result>
```

以特定速度移动一个具身设备

**起始版本：** 26.0.0

<!--Device-mechanicManager-function moveBySpeed(mechId: int, params: SpeedParams, duration: int): Promise<Result>--><!--Device-mechanicManager-function moveBySpeed(mechId: int, params: SpeedParams, duration: int): Promise<Result>-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mechId | number | 是 | 具身设备ID。<br>取值限定为整数。 |
| params | [SpeedParams](arkts-mechanic-mechanicmanager-speedparams-i-sys.md) | 是 | 移动参数。 |
| duration | number | 是 | 移动时长，单位ms。<br>取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&gt; | 202 - 非系统应用 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |
| [33300003](../errorcode-mechanic.md#33300003-功能不支持) | Feature not supported. |

