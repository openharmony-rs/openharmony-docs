# off_p2pDeviceChange

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## off('p2pDeviceChange')

```TypeScript
function off(type: 'p2pDeviceChange', callback?: Callback<WifiP2pDevice>): void
```

取消订阅P2P本地设备改变事件。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** p2pDeviceChange

**需要权限：** ohos.permission.LOCATION

<!--Device-wifi-function off(type: 'p2pDeviceChange', callback?: Callback<WifiP2pDevice>): void--><!--Device-wifi-function off(type: 'p2pDeviceChange', callback?: Callback<WifiP2pDevice>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'p2pDeviceChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;WifiP2pDevice&gt; | 否 | 状态改变回调函数 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

let recvP2pDeviceChangeFunc = (result:wifi.WifiP2pDevice) => {
    console.info("Receive p2p device change event: " + result);
}

// Register event
wifi.on("p2pDeviceChange", recvP2pDeviceChangeFunc);

// Unregister event
wifi.off("p2pDeviceChange", recvP2pDeviceChangeFunc);
```

