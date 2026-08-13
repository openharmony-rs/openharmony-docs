# on_ActivityType

## on_ActivityType

```TypeScript
function on(activity: ActivityType, event: ActivityEvent, reportLatencyNs: number, callback: Callback<ActivityResponse>): void
```

设备状态管理，订阅设备状态变化事件。当设备满足指定状态条件时，系统会触发回调函数上报状态变化事件，用于持续监听设备状态变化事件。调用on()后，必须在不使用时调用off()取消订阅，避免多余的性能功耗开销。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-stationary-function on(activity: ActivityType, event: ActivityEvent, reportLatencyNs: number, callback: Callback<ActivityResponse>): void--><!--Device-stationary-function on(activity: ActivityType, event: ActivityEvent, reportLatencyNs: number, callback: Callback<ActivityResponse>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Stationary

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| activity | [ActivityType](arkts-multimodalawareness-stationary-activitytype-t.md) | 是 | 设备状态能力类型。 |
| event | [ActivityEvent](arkts-multimodalawareness-stationary-activityevent-e.md) | 是 | 事件类型。 |
| reportLatencyNs | number | 是 | 报告延时，单位：纳秒（ns），取值范围[1000000000, 3000000000]。超出范围时返回错误。建议根据业务场景选择合适的值，较小值可提高实时性但 会增加功耗，较大值可降低功耗但会降低响应速度。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ActivityResponse](arkts-multimodalawareness-stationary-activityresponse-i.md)&gt; | 是 | 回调函数，用于接收设备状态变化结果。 |

## 示例

```TypeScript
let reportLatencyNs = 1000000000;
stationary.on('still', stationary.ActivityEvent.ENTER, reportLatencyNs, (data) => {
    console.info('data=' + JSON.stringify(data));
})
```

