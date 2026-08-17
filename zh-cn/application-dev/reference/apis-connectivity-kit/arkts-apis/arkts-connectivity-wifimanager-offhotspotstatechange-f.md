# offHotspotStateChange

## offHotspotStateChange

```TypeScript
function offHotspotStateChange(callback?: Callback<int>): void
```

取消注册热点状态改变事件。 如果未指定callback参数，将取消注册该事件关联的所有回调函数。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function offHotspotStateChange(callback?: Callback<int>): void--><!--Device-wifiManager-function offHotspotStateChange(callback?: Callback<int>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;int&gt; | 否 | 状态改变回调函数。如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2601000](../errorcode-wifi.md#2601000-hotspot模块异常) | Operation failed. |

