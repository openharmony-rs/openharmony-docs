# offP2pPeerDeviceChange

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## offP2pPeerDeviceChange

```TypeScript
function offP2pPeerDeviceChange(callback?: Callback<WifiP2pDevice[]>): void
```

取消注册P2P对端设备状态改变事件。

**起始版本：** 23

<!--Device-wifiManager-function offP2pPeerDeviceChange(callback?: Callback<WifiP2pDevice[]>): void--><!--Device-wifiManager-function offP2pPeerDeviceChange(callback?: Callback<WifiP2pDevice[]>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;WifiP2pDevice[]&gt; | 否 | 状态改变回调函数。如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |

