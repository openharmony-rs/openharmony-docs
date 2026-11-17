# removeAllP2pServiceRequests

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## removeAllP2pServiceRequests

```TypeScript
function removeAllP2pServiceRequests(): void
```

移除所有待处理的服务发现请求。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.GET_WIFI_INFO_INTERNAL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wifiManager-function removeAllP2pServiceRequests(): void--><!--Device-wifiManager-function removeAllP2pServiceRequests(): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p功能未打开) | Wi-Fi STA disabled. |
