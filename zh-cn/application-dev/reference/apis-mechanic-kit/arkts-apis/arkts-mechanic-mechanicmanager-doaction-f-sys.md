# doAction（系统接口）

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

<a id="doaction"></a>
## doAction

```TypeScript
function doAction(mechId: number, actionType: ActionType): Promise<Result>
```

Execute an action sequence.

**起始版本：** 26.0.0

<!--Device-mechanicManager-function doAction(mechId: int, actionType: ActionType): Promise<Result>--><!--Device-mechanicManager-function doAction(mechId: int, actionType: ActionType): Promise<Result>-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mechId | number | 是 | ID of the mechanical device.<br>The value should be an integer. |
| actionType | [ActionType](../../apis-avsession-kit/arkts-apis/arkts-avsession-avmusictemplate-actiontype-t.md) | 是 | Type of action sequence. |

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

