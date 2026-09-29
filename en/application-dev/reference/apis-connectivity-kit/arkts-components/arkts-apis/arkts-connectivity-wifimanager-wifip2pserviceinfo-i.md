# WifiP2pServiceInfo

```TypeScript
interface WifiP2pServiceInfo
```

Represents the P2P service information.

**Since:** 26.0.1

<!--Device-wifiManager-interface WifiP2pServiceInfo--><!--Device-wifiManager-interface WifiP2pServiceInfo-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## protocolType

```TypeScript
protocolType: P2pServiceProtocolType
```

Service protocol type.

**Type:** [P2pServiceProtocolType](arkts-connectivity-wifimanager-p2pserviceprotocoltype-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-WifiP2pServiceInfo-protocolType: P2pServiceProtocolType--><!--Device-WifiP2pServiceInfo-protocolType: P2pServiceProtocolType-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## queryList

```TypeScript
queryList: Array<string>
```

Query string list consumed by wpa_supplicant. The maximum size of a single data record is 1024.

**Type:** Array&lt;string&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-WifiP2pServiceInfo-queryList: Array<string>--><!--Device-WifiP2pServiceInfo-queryList: Array<string>-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## serviceName

```TypeScript
serviceName: string
```

Service name. Refer to the [addDnsSdLocalP2pService](arkts-connectivity-wifimanager-adddnssdlocalp2pservice-f.md) or [addUpnpLocalP2pService](arkts-connectivity-wifimanager-addupnplocalp2pservice-f.md) functions.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-WifiP2pServiceInfo-serviceName: string--><!--Device-WifiP2pServiceInfo-serviceName: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P
