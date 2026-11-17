# WifiP2pServiceRequest

```TypeScript
interface WifiP2pServiceRequest
```

表示P2P服务发现请求（TLV查询）。

**起始版本：** 26.1.0

<!--Device-wifiManager-interface WifiP2pServiceRequest--><!--Device-wifiManager-interface WifiP2pServiceRequest-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## protocolType

```TypeScript
protocolType: P2pServiceProtocolType
```

服务协议类型。

**类型：** [P2pServiceProtocolType](arkts-connectivity-wifimanager-p2pserviceprotocoltype-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiP2pServiceRequest-protocolType: P2pServiceProtocolType--><!--Device-WifiP2pServiceRequest-protocolType: P2pServiceProtocolType-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## query

```TypeScript
query: Uint8Array
```

查询字节数据。最大长度为256。

**类型：** Uint8Array

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiP2pServiceRequest-query: Uint8Array--><!--Device-WifiP2pServiceRequest-query: Uint8Array-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P
