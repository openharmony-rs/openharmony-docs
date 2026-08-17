# off_wifiScanStateChange

## off_wifiScanStateChange

```TypeScript
function off(type: 'wifiScanStateChange', callback?: Callback<number>): void
```

取消订阅WLAN扫描状态改变事件。 &lt;p&gt;如果没有指定callback参数，将取消注册该事件关联的所有回调函数。&lt;/p&gt;

**起始版本：** 7

**ArkTS模式：** 起始版本为7。

**废弃版本：** 9

**替代接口：** wifiScanStateChange

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function off(type: 'wifiScanStateChange', callback?: Callback<number>): void--><!--Device-wifi-function off(type: 'wifiScanStateChange', callback?: Callback<number>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'wifiScanStateChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;number&gt; | 否 | 状态改变回调函数。0:扫描失败，1:扫描成功 |

## 示例

```TypeScript
import wifi from '@ohos.wifi';

let recvWifiScanStateChangeFunc = (result:number) => {
    console.info("Receive Wifi scan state change event: " + result);
}

// Register event
wifi.on("wifiScanStateChange", recvWifiScanStateChangeFunc);

// Unregister event
wifi.off("wifiScanStateChange", recvWifiScanStateChangeFunc);
```

