# off_wifiStateChange

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## off('wifiStateChange')

```TypeScript
function off(type: 'wifiStateChange', callback?: Callback<number>): void
```

取消订阅WLAN状态改变事件。 &lt;p&gt;如果没有指定callback参数，将取消注册该事件关联的所有回调函数。&lt;/p&gt;

**起始版本：** 7

**废弃版本：** 9

**替代接口：** wifiStateChange

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function off(type: 'wifiStateChange', callback?: Callback<number>): void--><!--Device-wifi-function off(type: 'wifiStateChange', callback?: Callback<number>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'wifiStateChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;number&gt; | 否 | 状态改变回调函数。0:未激活，1:已激活，2:激活中，3:去激活中 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

let recvPowerNotifyFunc = (result:number) => {
    console.info("Receive power state change event: " + result);
}

// Register event
wifi.on("wifiStateChange", recvPowerNotifyFunc);

// Unregister event
wifi.off("wifiStateChange", recvPowerNotifyFunc);
```

