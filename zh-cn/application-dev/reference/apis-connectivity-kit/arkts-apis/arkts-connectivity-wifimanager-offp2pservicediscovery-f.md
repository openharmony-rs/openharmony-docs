# offP2pServiceDiscovery

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## offP2pServiceDiscovery

```TypeScript
function offP2pServiceDiscovery(callback?: Callback<P2pServiceDiscoveryInfo>): void
```

取消订阅通用服务响应事件。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.GET_WIFI_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wifiManager-function offP2pServiceDiscovery(callback?: Callback<P2pServiceDiscoveryInfo>): void--><!--Device-wifiManager-function offP2pServiceDiscovery(callback?: Callback<P2pServiceDiscoveryInfo>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[P2pServiceDiscoveryInfo](arkts-connectivity-wifimanager-p2pservicediscoveryinfo-t.md)&gt; | 否 | 待取消注册的回调函数。未指定该参数时，取消注册该事件类型的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
