# discoverServices

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## discoverServices

```TypeScript
function discoverServices(): void
```

启动P2P服务发现。使用待处理请求的TLV查询进行发现，如果待处理列表为空，则回退为发现所有服务类型。启动发现前，请先通过[addDnsSdServiceRequest](arkts-connectivity-wifimanager-adddnssdservicerequest-f.md)或[addUpnpServiceRequest](arkts-connectivity-wifimanager-addupnpservicerequest-f.md)添加服务请求。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.GET_WIFI_PEERS_MAC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wifiManager-function discoverServices(): void--><!--Device-wifiManager-function discoverServices(): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p功能未打开) | Wi-Fi STA disabled. |
