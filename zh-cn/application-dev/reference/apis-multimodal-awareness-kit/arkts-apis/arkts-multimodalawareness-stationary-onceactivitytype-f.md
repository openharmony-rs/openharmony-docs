# once_ActivityType

## once_ActivityType

```TypeScript
function once(activity: ActivityType, callback: Callback<ActivityResponse>): void
```

设备状态管理，查询设备状态。仅执行一次回调，用于一次性查询当前状态。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-stationary-function once(activity: ActivityType, callback: Callback<ActivityResponse>): void--><!--Device-stationary-function once(activity: ActivityType, callback: Callback<ActivityResponse>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Stationary

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| activity | [ActivityType](arkts-multimodalawareness-stationary-activitytype-t.md) | 是 | 设备状态能力类型。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ActivityResponse](arkts-multimodalawareness-stationary-activityresponse-i.md)&gt; | 是 | 回调函数，用于接收设备状态查询结果。 |

## 示例

```TypeScript
stationary.once('still', (data) => {
    console.info('data=' + JSON.stringify(data));
})
```

