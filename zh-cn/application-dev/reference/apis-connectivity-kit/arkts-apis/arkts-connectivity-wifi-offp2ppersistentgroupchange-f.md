# off_p2pPersistentGroupChange

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## off('p2pPersistentGroupChange')

```TypeScript
function off(type: 'p2pPersistentGroupChange', callback?: Callback<void>): void
```

取消订阅P2P持久群组改变事件。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** p2pPersistentGroupChange

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function off(type: 'p2pPersistentGroupChange', callback?: Callback<void>): void--><!--Device-wifi-function off(type: 'p2pPersistentGroupChange', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'p2pPersistentGroupChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 状态改变回调函数 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

let recvP2pPersistentGroupChangeFunc = (result:void) => {
    console.info("Receive p2p persistent group change event: " + result);
}

// Register event
wifi.on("p2pPersistentGroupChange", recvP2pPersistentGroupChangeFunc);

// Unregister event
wifi.off("p2pPersistentGroupChange", recvP2pPersistentGroupChangeFunc);
```

