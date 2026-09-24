# off

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## off('attachStateChange')

```TypeScript
function off(type: 'attachStateChange', callback?: Callback<AttachStateChangeInfo>): void
```

Unsubscribes from device attachment state change events.

**起始版本：** 20

**系统能力：** SystemCapability.Mechanic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'attachStateChange' | 是 | Event type. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AttachStateChangeInfo](arkts-mechanic-mechanicmanager-attachstatechangeinfo-i.md)&gt; | 否 | Callback used to return the state change. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |

**示例**

```TypeScript
// 定义连接状态变化回调函数
let callback = (result: mechanicManager.AttachStateChangeInfo) => {
  console.info(`'callback result:' ${result}`);
};

console.info('Unregister');
// 取消注册"attachStateChange"事件监听
mechanicManager.off("attachStateChange", callback);
console.info('Succeeded in unregistering callback.');
```


## off('trackingStateChange')

```TypeScript
function off(type: 'trackingStateChange', callback?: Callback<TrackingEventInfo>): void
```

设置相机跟踪布局

**起始版本：** 20

**系统能力：** SystemCapability.Mechanic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'trackingStateChange' | 是 | Event type. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[TrackingEventInfo](arkts-mechanic-mechanicmanager-trackingeventinfo-i.md)&gt; | 否 | Callback used to return the tracking event information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |

**示例**

```TypeScript
// 定义跟踪状态变化回调函数
let callback = (result: mechanicManager.TrackingEventInfo) => {
  console.info(`'callback result:' ${result}`);
};

console.info('Unregister');
// 取消注册"trackingStateChange"事件监听
mechanicManager.off("trackingStateChange", callback);
console.info('Succeeded in unregistering callback.');
```
