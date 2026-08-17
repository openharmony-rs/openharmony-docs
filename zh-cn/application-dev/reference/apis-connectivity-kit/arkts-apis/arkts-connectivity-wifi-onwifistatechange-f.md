# on_wifiStateChange

## on_wifiStateChange

```TypeScript
function on(type: 'wifiStateChange', callback: Callback<number>): void
```

订阅WLAN状态改变事件。

**起始版本：** 7

**ArkTS模式：** 起始版本为7。

**废弃版本：** 9

**替代接口：** wifiStateChange

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function on(type: 'wifiStateChange', callback: Callback<number>): void--><!--Device-wifi-function on(type: 'wifiStateChange', callback: Callback<number>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'wifiStateChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;number&gt; | 是 | 状态改变回调函数。0:未激活，1:已激活，2:激活中，3:去激活中 |

