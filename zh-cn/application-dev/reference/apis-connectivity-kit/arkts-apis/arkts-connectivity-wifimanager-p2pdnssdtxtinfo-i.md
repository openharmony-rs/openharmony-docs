# P2pDnsSdTxtInfo

```TypeScript
interface P2pDnsSdTxtInfo
```

表示从对端设备收到的DNS-SD TXT记录信息。

**起始版本：** 26.1.0

<!--Device-wifiManager-interface P2pDnsSdTxtInfo--><!--Device-wifiManager-interface P2pDnsSdTxtInfo-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## device

```TypeScript
device: WifiP2pDevice
```

响应该TXT记录的对端设备。

**类型：** [WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-P2pDnsSdTxtInfo-device: WifiP2pDevice--><!--Device-P2pDnsSdTxtInfo-device: WifiP2pDevice-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## txtRecord

```TypeScript
txtRecord: Map<string, string>
```

包含键值对的TXT记录。

**类型：** Map&lt;string, string&gt;

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-P2pDnsSdTxtInfo-txtRecord: Map<string, string>--><!--Device-P2pDnsSdTxtInfo-txtRecord: Map<string, string>-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## wholeDomainName

```TypeScript
wholeDomainName: string
```

TXT记录的完整域名。格式为instanceName + "." + serviceType + ".local."。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-P2pDnsSdTxtInfo-wholeDomainName: string--><!--Device-P2pDnsSdTxtInfo-wholeDomainName: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P
