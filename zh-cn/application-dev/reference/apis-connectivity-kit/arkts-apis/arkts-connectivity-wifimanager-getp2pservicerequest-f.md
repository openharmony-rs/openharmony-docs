# getP2pServiceRequest

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getP2pServiceRequest

```TypeScript
function getP2pServiceRequest(): Promise<Array<WifiP2pServiceRequest>>
```

查询待处理的P2P服务发现请求，使用Promise异步回调。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.GET_WIFI_INFO_INTERNAL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wifiManager-function getP2pServiceRequest(): Promise<Array<WifiP2pServiceRequest>>--><!--Device-wifiManager-function getP2pServiceRequest(): Promise<Array<WifiP2pServiceRequest>>-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;WifiP2pServiceRequest&gt;&gt; | Promise对象。用于返回待处理的服务发现请求列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p功能未打开) | Wi-Fi STA disabled. |
