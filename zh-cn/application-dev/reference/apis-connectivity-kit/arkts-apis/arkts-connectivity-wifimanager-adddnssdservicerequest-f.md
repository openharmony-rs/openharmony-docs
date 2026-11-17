# addDnsSdServiceRequest

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## addDnsSdServiceRequest

```TypeScript
function addDnsSdServiceRequest(serviceType?: string, instanceName?: string): void
```

添加DNS-SD服务发现请求，用于匹配DNS-SD服务。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.GET_WIFI_INFO_INTERNAL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wifiManager-function addDnsSdServiceRequest(serviceType?: string, instanceName?: string): void--><!--Device-wifiManager-function addDnsSdServiceRequest(serviceType?: string, instanceName?: string): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| serviceType | string | 否 | 服务类型，用于对端服务发现。推荐格式为"_<服务名>._<协议>"，例如："_http._tcp"。与[addDnsSdLocalP2pService](arkts-connectivity-wifimanager-adddnssdlocalp2pservice-f.md)的入参serviceType对应。未指定该参数时，默认为空字符串，匹配所有服务类型。 |
| instanceName | string | 否 | 实例名称，用于发现对端服务。与[addDnsSdLocalP2pService](arkts-connectivity-wifimanager-adddnssdlocalp2pservice-f.md)的入参instanceName对应。未指定该参数时，默认为空字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p功能未打开) | Wi-Fi STA disabled. |
