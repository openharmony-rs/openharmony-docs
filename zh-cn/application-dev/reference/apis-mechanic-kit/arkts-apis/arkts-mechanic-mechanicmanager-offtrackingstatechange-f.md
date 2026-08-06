# offTrackingStateChange

## offTrackingStateChange

```TypeScript
function offTrackingStateChange(callback?: Callback<TrackingEventInfo>): void
```

设置相机跟踪布局

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-mechanicManager-function offTrackingStateChange(callback?: Callback<TrackingEventInfo>): void--><!--Device-mechanicManager-function offTrackingStateChange(callback?: Callback<TrackingEventInfo>): void-End-->

**系统能力：** SystemCapability.Mechanic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;TrackingEventInfo&gt; | 否 | Callback used to return the tracking event information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |

