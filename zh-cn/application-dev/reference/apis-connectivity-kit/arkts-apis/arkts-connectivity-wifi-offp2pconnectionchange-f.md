# off_p2pConnectionChange

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## off('p2pConnectionChange')

```TypeScript
function off(type: 'p2pConnectionChange', callback?: Callback<WifiP2pLinkedInfo>): void
```

取消订阅P2P连接改变事件。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** p2pConnectionChange

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function off(type: 'p2pConnectionChange', callback?: Callback<WifiP2pLinkedInfo>): void--><!--Device-wifi-function off(type: 'p2pConnectionChange', callback?: Callback<WifiP2pLinkedInfo>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'p2pConnectionChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;WifiP2pLinkedInfo&gt; | 否 | 状态改变回调函数 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

let recvP2pConnectionChangeFunc = (result:wifi.WifiP2pLinkedInfo) => {
    console.info("Receive p2p connection change event: " + result);
}

// Register event
wifi.on("p2pConnectionChange", recvP2pConnectionChangeFunc);

// Unregister event
wifi.off("p2pConnectionChange", recvP2pConnectionChangeFunc);
```

