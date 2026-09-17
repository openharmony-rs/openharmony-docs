# WifiScanInfo

Describes the scanned Wi-Fi information. @typedef WifiScanInfo

**Since:** 12

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

**System capability:** SystemCapability.Communication.WiFi.STA

## bssid

```TypeScript
bssid: string
```

Wi-Fi bssid(MAC): the length is 6

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

## bssidType

```TypeScript
bssidType: DeviceAddressType
```

Wi-Fi bssid type

**Type:** [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

## capabilities

```TypeScript
capabilities: string
```

Hotspot capability

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

## centerFrequency0

```TypeScript
centerFrequency0: number
```

Center frequency 0.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

## centerFrequency1

```TypeScript
centerFrequency1: number
```

Center frequency 1.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

## channelWidth

```TypeScript
channelWidth: number
```

Channel width

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

## frequency

```TypeScript
frequency: number
```

Frequency

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

## infoElems

```TypeScript
infoElems: Array<WifiInfoElem>
```

Information elements.

**Type:** Array&lt;[WifiInfoElem](arkts-connectivity-wifimanager-wifiinfoelem-i.md)&gt;

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

## isHiLinkNetwork

```TypeScript
isHiLinkNetwork: boolean
```

Whether the Wi-Fi hotspot is HiLink network.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.Communication.WiFi.STA

## rssi

```TypeScript
rssi: number
```

Received signal strength indicator (RSSI)

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

## securityType

```TypeScript
securityType: WifiSecurityType
```

Security type: reference definition of WifiSecurityType

**Type:** [WifiSecurityType](arkts-connectivity-wifimanager-wifisecuritytype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

Wi-Fi SSID: the maximum length is 32

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

## supportedWifiCategory

```TypeScript
supportedWifiCategory: WifiCategory
```

Supported wifi category

**Type:** [WifiCategory](arkts-connectivity-wifimanager-wificategory-e.md)

**Since:** 12

**System capability:** SystemCapability.Communication.WiFi.STA

## timestamp

```TypeScript
timestamp: number
```

Time stamp

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA
