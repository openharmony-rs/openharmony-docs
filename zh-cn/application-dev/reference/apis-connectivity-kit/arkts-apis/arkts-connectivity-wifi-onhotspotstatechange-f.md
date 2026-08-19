# on_hotspotStateChange

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## on('hotspotStateChange')

```TypeScript
function on(type: 'hotspotStateChange', callback: Callback<number>): void
```

订阅WLAN热点状态改变事件。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** hotspotStateChange

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function on(type: 'hotspotStateChange', callback: Callback<number>): void--><!--Device-wifi-function on(type: 'hotspotStateChange', callback: Callback<number>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hotspotStateChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;number&gt; | 是 | 状态改变回调函数。0:未激活，1:已激活，2:激活中，3:去激活中 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

let recvHotspotStateChangeFunc = (result:number) => {
    console.info("Receive hotspot state change event: " + result);
}

// Register event
wifi.on("hotspotStateChange", recvHotspotStateChangeFunc);

// Unregister event
wifi.off("hotspotStateChange", recvHotspotStateChangeFunc);
```

