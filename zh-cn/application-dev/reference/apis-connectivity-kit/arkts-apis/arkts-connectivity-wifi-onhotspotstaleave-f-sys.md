# on_hotspotStaLeave（系统接口）

## on_hotspotStaLeave

```TypeScript
function on(type: 'hotspotStaLeave', callback: Callback<StationInfo>): void
```

订阅WLAN热点STA离开事件。

**起始版本：** 7

**ArkTS模式：** 起始版本为7。

**废弃版本：** 9

**替代接口：** hotspotStaLeave

**需要权限：** ohos.permission.MANAGE_WIFI_HOTSPOT

<!--Device-wifi-function on(type: 'hotspotStaLeave', callback: Callback<StationInfo>): void--><!--Device-wifi-function on(type: 'hotspotStaLeave', callback: Callback<StationInfo>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hotspotStaLeave' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;StationInfo&gt; | 是 | 状态改变回调函数 |

