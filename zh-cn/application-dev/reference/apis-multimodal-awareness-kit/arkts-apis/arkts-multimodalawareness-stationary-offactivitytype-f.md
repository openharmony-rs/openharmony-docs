# off_ActivityType

## 导入模块

```TypeScript
import { stationary } from '@kit.MultimodalAwarenessKit';
```

## off_ActivityType

```TypeScript
function off(activity: ActivityType, event: ActivityEvent, callback?: Callback<ActivityResponse>): void
```

取消订阅设备状态服务。取消订阅后，将停止接收该状态相关的回调函数调用。调用off()时需要使用与on()相同的activity和event参数。

**起始版本：** 9

<!--Device-stationary-function off(activity: ActivityType, event: ActivityEvent, callback?: Callback<ActivityResponse>): void--><!--Device-stationary-function off(activity: ActivityType, event: ActivityEvent, callback?: Callback<ActivityResponse>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Stationary

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| activity | [ActivityType](arkts-multimodalawareness-stationary-activitytype-t.md) | 是 | 设备状态类型。 |
| event | [ActivityEvent](arkts-multimodalawareness-stationary-activityevent-e.md) | 是 | 事件类型。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ActivityResponse](arkts-multimodalawareness-stationary-activityresponse-i.md)&gt; | 否 | 要移除的回调函数。未传递callback参数或传递undefined时，移除该进程下订阅该类型的所有callback。 |

**示例**

```TypeScript
stationary.off('still', stationary.ActivityEvent.ENTER);
```

