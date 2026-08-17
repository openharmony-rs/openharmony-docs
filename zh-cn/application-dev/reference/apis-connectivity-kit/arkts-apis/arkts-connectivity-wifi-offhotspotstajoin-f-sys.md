# off_hotspotStaJoin（系统接口）

## off_hotspotStaJoin

```TypeScript
function off(type: 'hotspotStaJoin', callback?: Callback<StationInfo>): void
```

取消订阅WLAN热点STA加入事件。 &lt;p&gt;如果没有指定callback参数，将取消注册该事件关联的所有回调函数。&lt;/p&gt;

**起始版本：** 7

**ArkTS模式：** 起始版本为7。

**废弃版本：** 9

**替代接口：** hotspotStaJoin

**需要权限：** ohos.permission.MANAGE_WIFI_HOTSPOT

<!--Device-wifi-function off(type: 'hotspotStaJoin', callback?: Callback<StationInfo>): void--><!--Device-wifi-function off(type: 'hotspotStaJoin', callback?: Callback<StationInfo>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hotspotStaJoin' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;StationInfo&gt; | 否 | 状态改变回调函数 |

