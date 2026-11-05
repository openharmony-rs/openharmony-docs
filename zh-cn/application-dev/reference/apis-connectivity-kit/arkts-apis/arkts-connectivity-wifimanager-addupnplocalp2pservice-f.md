# addUpnpLocalP2pService

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## addUpnpLocalP2pService

```TypeScript
function addUpnpLocalP2pService(uuid: string, device: string,
    services: Array<string>, serviceName: string): void
```

添加并注册一个UPnP（Universal Plug and Play，通用即插即用）本地P2P服务描述，供对端进行服务发现。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.GET_WIFI_INFO_INTERNAL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wifiManager-function addUpnpLocalP2pService(uuid: string, device: string,    services: Array<string>, serviceName: string): void--><!--Device-wifiManager-function addUpnpLocalP2pService(uuid: string, device: string,    services: Array<string>, serviceName: string): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | string | 是 | 该UUID的字符串表示形式，格式参见[RFC 4122](http://www.ietf.org/rfc/rfc4122.txt)。标准固定长度为36个字符，不允许包含空格，例如"6859dede-8574-59ab-9332-123456789012"。 |
| device | string | 是 | UPnP设备类型，字符串表示形式，格式参见[UPnP Device Architecture 1.1](http://www.upnp.org/specs/arch/UPnP-arch-DeviceArchitecture-v1.1.pdf)。长度取决于标准定义，不允许包含空格，通常为几十个字符，建议保持在255字节以内，例如"urn:schemas-upnp-org:device:MediaServer:1"。 |
| services | Array&lt;string&gt; | 是 | UPnP服务类型列表，字符串表示形式，格式参见[UPnP Device Architecture 1.1](http://www.upnp.org/specs/arch/UPnP-arch-DeviceArchitecture-v1.1.pdf)。每个服务的长度不得超过512字节，建议Array中的元素数量不宜过多，例如"urn:schemas-upnp-org:service:ContentDirectory:1"。 |
| serviceName | string | 是 | 用于标识本地服务对象的服务名称，最大长度为63字符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | The Wi-Fi service is not started properly, or there is an Wi-Fi service error. |
| [2801001](../errorcode-wifi.md#2801001-p2p功能未打开) | Wi-Fi STA disabled. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

try {
  let uuid = "6859dede-8574-59ab-9332-123456789012";
  let device = "urn:schemas-upnp-org:device:MediaServer:1";
  let services = ["urn:schemas-upnp-org:service:ContentDirectory:1"];
  wifiManager.addUpnpLocalP2pService(uuid, device, services, "serviceName");
} catch (error) {
  console.error("failed: " + JSON.stringify(error));
}
```
