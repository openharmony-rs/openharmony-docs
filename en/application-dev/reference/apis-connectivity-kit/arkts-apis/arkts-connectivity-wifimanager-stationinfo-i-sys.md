# StationInfo (System API)

```TypeScript
interface StationInfo
```

Wi-Fi station information. @typedef StationInfo

**Since:** 9

<!--Device-wifiManager-interface StationInfo--><!--Device-wifiManager-interface StationInfo-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## ipAddress

```TypeScript
ipAddress: string
```

The IP address of the Wi-Fi client

**Type:** string

**Since:** 9

<!--Device-StationInfo-ipAddress: string--><!--Device-StationInfo-ipAddress: string-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## macAddress

```TypeScript
macAddress: string
```

The MAC address of the Wi-Fi client

**Type:** string

**Since:** 9

<!--Device-StationInfo-macAddress: string--><!--Device-StationInfo-macAddress: string-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## macAddressType

```TypeScript
macAddressType?: DeviceAddressType
```

The MAC address type of the Wi-Fi client

**Type:** [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md)

**Since:** 10

<!--Device-StationInfo-macAddressType?: DeviceAddressType--><!--Device-StationInfo-macAddressType?: DeviceAddressType-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## name

```TypeScript
name: string
```

The network name of the Wi-Fi client

**Type:** string

**Since:** 9

<!--Device-StationInfo-name: string--><!--Device-StationInfo-name: string-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.
