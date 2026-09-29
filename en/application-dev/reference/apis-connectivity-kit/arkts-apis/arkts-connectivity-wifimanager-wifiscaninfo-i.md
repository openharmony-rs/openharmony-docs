# WifiScanInfo

```TypeScript
interface WifiScanInfo
```

Describes the scanned Wi-Fi information. @typedef WifiScanInfo

**Since:** 12

<!--Device-wifiManager-interface WifiScanInfo--><!--Device-wifiManager-interface WifiScanInfo-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## band

```TypeScript
band: number
```

Frequency band, 1: 2.4G, 2: 5G

**Type:** number

**Since:** 9

<!--Device-WifiScanInfo-band: int--><!--Device-WifiScanInfo-band: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## bssid

```TypeScript
bssid: string
```

Wi-Fi bssid(MAC): the length is 6

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-WifiScanInfo-bssid: string--><!--Device-WifiScanInfo-bssid: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## bssidType

```TypeScript
bssidType: DeviceAddressType
```

Wi-Fi bssid type

**Type:** [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-WifiScanInfo-bssidType: DeviceAddressType--><!--Device-WifiScanInfo-bssidType: DeviceAddressType-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## capabilities

```TypeScript
capabilities: string
```

Hotspot capability

**Type:** string

**Since:** 9

<!--Device-WifiScanInfo-capabilities: string--><!--Device-WifiScanInfo-capabilities: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## centerFrequency0

```TypeScript
centerFrequency0: number
```

Center frequency 0.

**Type:** number

**Since:** 9

<!--Device-WifiScanInfo-centerFrequency0: int--><!--Device-WifiScanInfo-centerFrequency0: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## centerFrequency1

```TypeScript
centerFrequency1: number
```

Center frequency 1.

**Type:** number

**Since:** 9

<!--Device-WifiScanInfo-centerFrequency1: int--><!--Device-WifiScanInfo-centerFrequency1: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## channelWidth

```TypeScript
channelWidth: number
```

Channel width

**Type:** number

**Since:** 9

<!--Device-WifiScanInfo-channelWidth: int--><!--Device-WifiScanInfo-channelWidth: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## frequency

```TypeScript
frequency: number
```

Frequency

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-WifiScanInfo-frequency: int--><!--Device-WifiScanInfo-frequency: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## infoElems

```TypeScript
infoElems: Array<WifiInfoElem>
```

Information elements.

**Type:** Array&lt;[WifiInfoElem](arkts-connectivity-wifimanager-wifiinfoelem-i.md)&gt;

**Since:** 9

<!--Device-WifiScanInfo-infoElems: Array<WifiInfoElem>--><!--Device-WifiScanInfo-infoElems: Array<WifiInfoElem>-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## isHiLinkNetwork

```TypeScript
isHiLinkNetwork: boolean
```

Whether the Wi-Fi hotspot is HiLink network.

**Type:** boolean

**Since:** 12

<!--Device-WifiScanInfo-isHiLinkNetwork: boolean--><!--Device-WifiScanInfo-isHiLinkNetwork: boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## rssi

```TypeScript
rssi: number
```

Received signal strength indicator (RSSI)

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-WifiScanInfo-rssi: int--><!--Device-WifiScanInfo-rssi: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## securityType

```TypeScript
securityType: WifiSecurityType
```

Security type: reference definition of WifiSecurityType

**Type:** [WifiSecurityType](arkts-connectivity-wifimanager-wifisecuritytype-e.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-WifiScanInfo-securityType: WifiSecurityType--><!--Device-WifiScanInfo-securityType: WifiSecurityType-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

Wi-Fi SSID: the maximum length is 32

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-WifiScanInfo-ssid: string--><!--Device-WifiScanInfo-ssid: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## supportedWifiCategory

```TypeScript
supportedWifiCategory: WifiCategory
```

Supported wifi category

**Type:** [WifiCategory](arkts-connectivity-wifimanager-wificategory-e.md)

**Since:** 12

<!--Device-WifiScanInfo-supportedWifiCategory: WifiCategory--><!--Device-WifiScanInfo-supportedWifiCategory: WifiCategory-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## timestamp

```TypeScript
timestamp: number
```

Time stamp

**Type:** number

**Since:** 9

<!--Device-WifiScanInfo-timestamp: long--><!--Device-WifiScanInfo-timestamp: long-End-->

**System capability:** SystemCapability.Communication.WiFi.STA
