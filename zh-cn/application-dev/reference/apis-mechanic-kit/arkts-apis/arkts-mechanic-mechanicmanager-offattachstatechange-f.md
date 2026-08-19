# offAttachStateChange

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## offAttachStateChange

```TypeScript
function offAttachStateChange(callback?: Callback<AttachStateChangeInfo>): void
```

Unsubscribes from device attachment state change events.

**起始版本：** 23

<!--Device-mechanicManager-function offAttachStateChange(callback?: Callback<AttachStateChangeInfo>): void--><!--Device-mechanicManager-function offAttachStateChange(callback?: Callback<AttachStateChangeInfo>): void-End-->

**系统能力：** SystemCapability.Mechanic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AttachStateChangeInfo](arkts-mechanic-mechanicmanager-attachstatechangeinfo-i.md)&gt; | 否 | Callback used to return the state change. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |

