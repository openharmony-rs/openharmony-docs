# WifiP2pServiceInfo

```TypeScript
interface WifiP2pServiceInfo
```

表示P2P服务信息。

**起始版本：** 26.1.0

<!--Device-wifiManager-interface WifiP2pServiceInfo--><!--Device-wifiManager-interface WifiP2pServiceInfo-End-->

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

<!--Device-WifiP2pServiceInfo-protocolType: P2pServiceProtocolType--><!--Device-WifiP2pServiceInfo-protocolType: P2pServiceProtocolType-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## queryList

```TypeScript
queryList: Array<string>
```

Wi-Fi协议栈进程（wpa_supplicant）使用的查询字符串列表，单条数据记录的最大大小为1024字节。

**类型：** Array&lt;string&gt;

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiP2pServiceInfo-queryList: Array<string>--><!--Device-WifiP2pServiceInfo-queryList: Array<string>-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## serviceName

```TypeScript
serviceName: string
```

服务名称。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiP2pServiceInfo-serviceName: string--><!--Device-WifiP2pServiceInfo-serviceName: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P
