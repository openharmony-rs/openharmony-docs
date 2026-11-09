# P2pDnsSdTxtInfo

```TypeScript
interface P2pDnsSdTxtInfo
```

Represents the DNS-SD TXT record information received from a peer device.

**Since:** 26.0.1

<!--Device-wifiManager-interface P2pDnsSdTxtInfo--><!--Device-wifiManager-interface P2pDnsSdTxtInfo-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## device

```TypeScript
device: WifiP2pDevice
```

The peer device that responded with the TXT record.

**Type:** [WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-P2pDnsSdTxtInfo-device: WifiP2pDevice--><!--Device-P2pDnsSdTxtInfo-device: WifiP2pDevice-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## txtRecord

```TypeScript
txtRecord: Map<string, string>
```

TXT record map containing key/value pairs.

**Type:** Map&lt;string, string&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-P2pDnsSdTxtInfo-txtRecord: Map<string, string>--><!--Device-P2pDnsSdTxtInfo-txtRecord: Map<string, string>-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## wholeDomainName

```TypeScript
wholeDomainName: string
```

The full domain name of the TXT record. The format is instanceName + "." + serviceType + ".local.".

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-P2pDnsSdTxtInfo-wholeDomainName: string--><!--Device-P2pDnsSdTxtInfo-wholeDomainName: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P
