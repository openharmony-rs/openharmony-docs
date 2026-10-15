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

## locallyGenerated

```TypeScript
locallyGenerated?: boolean
```

Whether the disconnection is initiated by the local device when the Wi-Fi client left the hotspot.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-StationInfo-locallyGenerated?: boolean--><!--Device-StationInfo-locallyGenerated?: boolean-End-->

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

## reasonCode

```TypeScript
reasonCode?: number
```

The client reason code of the Wi-Fi client leaving the hotspot, as defined in the IEEE 802.11 protocol. The default value is 1.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-StationInfo-reasonCode?: int--><!--Device-StationInfo-reasonCode?: int-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## rssi

```TypeScript
rssi?: number
```

The Received Signal Strength Indicator (RSSI) in dBm of the Wi-Fi client when it left the hotspot. The default value is -127.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-StationInfo-rssi?: int--><!--Device-StationInfo-rssi?: int-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.
