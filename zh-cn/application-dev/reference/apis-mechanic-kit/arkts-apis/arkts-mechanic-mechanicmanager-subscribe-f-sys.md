# subscribe（系统接口）

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## subscribe

```TypeScript
function subscribe(events: MechEventType[], callback: Callback<MechEvent>): void
```

Subscribe to the specified events.

**起始版本：** 26.0.0

<!--Device-mechanicManager-function subscribe(events: MechEventType[], callback: Callback<MechEvent>): void--><!--Device-mechanicManager-function subscribe(events: MechEventType[], callback: Callback<MechEvent>): void-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| events | [MechEventType](arkts-mechanic-mechanicmanager-mecheventtype-e-sys.md)[] | 是 | Events to subscribe to. |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<MechEvent> | 是 | Callback of event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |
| [33300003](../errorcode-mechanic.md#33300003-功能不支持) | Feature not supported. |

