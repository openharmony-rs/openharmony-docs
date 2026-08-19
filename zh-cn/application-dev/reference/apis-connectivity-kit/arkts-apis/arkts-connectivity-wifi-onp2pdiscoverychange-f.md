# on_p2pDiscoveryChange

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## on('p2pDiscoveryChange')

```TypeScript
function on(type: 'p2pDiscoveryChange', callback: Callback<number>): void
```

订阅P2P发现事件。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** p2pDiscoveryChange

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function on(type: 'p2pDiscoveryChange', callback: Callback<number>): void--><!--Device-wifi-function on(type: 'p2pDiscoveryChange', callback: Callback<number>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'p2pDiscoveryChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;number&gt; | 是 | 状态改变回调函数 |

