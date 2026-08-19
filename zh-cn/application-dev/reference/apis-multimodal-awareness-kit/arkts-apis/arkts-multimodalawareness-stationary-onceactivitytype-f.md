# once_ActivityType

## 导入模块

```TypeScript
import { stationary } from '@kit.MultimodalAwarenessKit';
```

## once_ActivityType

```TypeScript
function once(activity: ActivityType, callback: Callback<ActivityResponse>): void
```

查询设备状态。通过callback回调返回查询结果，仅执行一次。使用callback异步回调。

**起始版本：** 9

<!--Device-stationary-function once(activity: ActivityType, callback: Callback<ActivityResponse>): void--><!--Device-stationary-function once(activity: ActivityType, callback: Callback<ActivityResponse>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Stationary

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| activity | [ActivityType](arkts-multimodalawareness-stationary-activitytype-t.md) | 是 | 设备状态类型。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ActivityResponse](arkts-multimodalawareness-stationary-activityresponse-i.md)&gt; | 是 | 回调函数，用于接收设备状态查询结果。 |

**示例**

```TypeScript
stationary.once('still', (data) => {
    console.info('data=' + JSON.stringify(data));
});
```

