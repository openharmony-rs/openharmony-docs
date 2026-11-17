# P2pDnsSdInfo

```TypeScript
interface P2pDnsSdInfo
```

Represents the DNS-SD service response information received from a peer device.

**Since:** 26.1.0

<!--Device-wifiManager-interface P2pDnsSdInfo--><!--Device-wifiManager-interface P2pDnsSdInfo-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## device

```TypeScript
device: WifiP2pDevice
```

The peer device that responded with the service.

**Type:** [WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-P2pDnsSdInfo-device: WifiP2pDevice--><!--Device-P2pDnsSdInfo-device: WifiP2pDevice-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## instanceName

```TypeScript
instanceName: string
```

Instance name of the discovered Bonjour service.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-P2pDnsSdInfo-instanceName: string--><!--Device-P2pDnsSdInfo-instanceName: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## registrationType

```TypeScript
registrationType: string
```

Registration type of the discovered Bonjour service. The value prefix is the same as the serviceType input parameter in [addDnsSdLocalP2pService](arkts-connectivity-wifimanager-adddnssdlocalp2pservice-f.md), with ".local." appended at the end.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-P2pDnsSdInfo-registrationType: string--><!--Device-P2pDnsSdInfo-registrationType: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P
