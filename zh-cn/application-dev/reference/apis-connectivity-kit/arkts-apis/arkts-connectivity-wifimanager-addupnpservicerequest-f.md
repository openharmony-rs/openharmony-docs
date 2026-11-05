# addUpnpServiceRequest

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## addUpnpServiceRequest

```TypeScript
function addUpnpServiceRequest(searchTarget?: string): void
```

添加UPnP服务发现请求，用于匹配指定的搜索目标。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.GET_WIFI_INFO_INTERNAL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wifiManager-function addUpnpServiceRequest(searchTarget?: string): void--><!--Device-wifiManager-function addUpnpServiceRequest(searchTarget?: string): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| searchTarget | string | 否 | UPnP搜索目标。未指定该参数时，默认为空字符串。<br>入参类型示例如下：<br> <ul> <li>搜索所有UPnP设备和服务："ssdp:all"<li>搜索特定根设备："upnp:rootdevice"<li>搜索特定设备类型（urn:schemas-upnp-org:device:...）：<br>例如"urn:schemas-upnp-org:device:MediaServer:2"<li>搜索特定服务类型（urn:schemas-upnp-org:service:...）：<br>例如"urn:schemas-upnp-org:service:ContentDirectory:2"<li>搜索特定UUID：例如："uuid:6859dede-8574-59ab-9332-123456789012"</ul> |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p功能未打开) | Wi-Fi STA disabled. |
