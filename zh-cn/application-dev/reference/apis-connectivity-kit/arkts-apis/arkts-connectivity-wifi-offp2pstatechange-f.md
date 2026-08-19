# off_p2pStateChange

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## off('p2pStateChange')

```TypeScript
function off(type: 'p2pStateChange', callback?: Callback<number>): void
```

取消订阅P2P状态改变事件。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** p2pStateChange

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function off(type: 'p2pStateChange', callback?: Callback<number>): void--><!--Device-wifi-function off(type: 'p2pStateChange', callback?: Callback<number>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'p2pStateChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;number&gt; | 否 | 状态改变回调函数。1:空闲，2:打开中，3:已打开，4:关闭中，5:已关闭 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

let recvP2pStateChangeFunc = (result:number) => {
    console.info("Receive p2p state change event: " + result);
}

// Register event
wifi.on("p2pStateChange", recvP2pStateChangeFunc);

// Unregister event
wifi.off("p2pStateChange", recvP2pStateChangeFunc);
```

