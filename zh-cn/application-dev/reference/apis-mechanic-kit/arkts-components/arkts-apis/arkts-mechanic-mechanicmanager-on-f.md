# on

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## on('attachStateChange')

```TypeScript
function on(type: 'attachStateChange', callback: Callback<AttachStateChangeInfo>): void
```

Subscribes to device attachment state change events.

**起始版本：** 20

**系统能力：** SystemCapability.Mechanic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'attachStateChange' | 是 | Event type. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AttachStateChangeInfo](arkts-mechanic-mechanicmanager-attachstatechangeinfo-i.md)&gt; | 是 | Callback used to return the state change. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |


## on('trackingStateChange')

```TypeScript
function on(type: 'trackingStateChange', callback: Callback<TrackingEventInfo>): void
```

Subscribes to tracking events.

**起始版本：** 20

**系统能力：** SystemCapability.Mechanic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'trackingStateChange' | 是 | Event type. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[TrackingEventInfo](arkts-mechanic-mechanicmanager-trackingeventinfo-i.md)&gt; | 是 | Callback used to return the tracking event information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
