# offP2pConnectionChange

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## offP2pConnectionChange

```TypeScript
function offP2pConnectionChange(callback?: Callback<WifiP2pLinkedInfo>): void
```

取消注册P2P连接状态改变事件。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function offP2pConnectionChange(callback?: Callback<WifiP2pLinkedInfo>): void--><!--Device-wifiManager-function offP2pConnectionChange(callback?: Callback<WifiP2pLinkedInfo>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;WifiP2pLinkedInfo&gt; | 否 | 状态改变回调函数。如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

