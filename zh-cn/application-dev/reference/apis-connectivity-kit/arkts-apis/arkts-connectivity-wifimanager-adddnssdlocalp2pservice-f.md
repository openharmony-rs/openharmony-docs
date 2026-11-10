# addDnsSdLocalP2pService

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## addDnsSdLocalP2pService

```TypeScript
function addDnsSdLocalP2pService(instanceName: string, serviceType: string,
    txtRecord: Map<string, string>, serviceName: string): void
```

添加并注册一个DNS-SD（DNS Service Discovery，基于DNS的服务发现）本地P2P服务描述，供对端进行服务发现。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.GET_WIFI_INFO_INTERNAL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wifiManager-function addDnsSdLocalP2pService(instanceName: string, serviceType: string,    txtRecord: Map<string, string>, serviceName: string): void--><!--Device-wifiManager-function addDnsSdLocalP2pService(instanceName: string, serviceType: string,    txtRecord: Map<string, string>, serviceName: string): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instanceName | string | 是 | 实例名，用于对端服务发现，最大长度为63字符。 |
| serviceType | string | 是 | 服务类型，用于对端服务发现，最大长度为63字符。不能为空字符串，可自定义，推荐格式为"_<ServiceName>._<Protocol>"，例如"_http._tcp"。 |
| txtRecord | Map&lt;string, string&gt; | 是 | 包含键值对的TXT记录。键不能包含等号（=），单条记录长度（key.length + value.length）必须小于255字节。建议所有键和值序列化后的总大小保持在200-400字节以内，超出单个mDNS数据包的限制会导致数据无法正确广播或被对端忽略。键值对数量无限制。定义格式见[draft-cheshire-dnsext-dns-sd-11.txt](http://files.dns-sd.org/draft-cheshire-dnsext-dns-sd.txt)。 |
| serviceName | string | 是 | 用于标识本地服务对象的服务名称，最大长度为63字符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p功能未打开) | Wi-Fi STA disabled. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

try {
  let txtRecord: Map<string, string> = new Map();
  txtRecord.set("name", "xxx");
  wifiManager.addDnsSdLocalP2pService("instanceName", "_http._tcp", txtRecord, "serviceName");
} catch (error) {
  console.error("failed: " + JSON.stringify(error));
}
```
