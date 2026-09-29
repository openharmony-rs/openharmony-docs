# WifiScanInfo (System API)

```TypeScript
export interface WifiScanInfo
```

Describes the scanned WiFi information.

**Since:** 10

<!--Device-geoLocationManager-export interface WifiScanInfo--><!--Device-geoLocationManager-export interface WifiScanInfo-End-->

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## bssid

```TypeScript
bssid: string
```

WiFi bssid(MAC): the length is 6.

**Type:** string

**Since:** 10

<!--Device-WifiScanInfo-bssid: string--><!--Device-WifiScanInfo-bssid: string-End-->

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## frequency

```TypeScript
frequency: number
```

Frequency

**Type:** number

**Since:** 10

<!--Device-WifiScanInfo-frequency: int--><!--Device-WifiScanInfo-frequency: int-End-->

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## rssi

```TypeScript
rssi: number
```

Received signal strength indicator (RSSI).

**Type:** number

**Since:** 10

<!--Device-WifiScanInfo-rssi: int--><!--Device-WifiScanInfo-rssi: int-End-->

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## ssid

```TypeScript
ssid: string
```

WiFi SSID: the maximum length is 32.

**Type:** string

**Since:** 10

<!--Device-WifiScanInfo-ssid: string--><!--Device-WifiScanInfo-ssid: string-End-->

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## timestamp

```TypeScript
timestamp: number
```

Time stamp.

**Type:** number

**Since:** 10

<!--Device-WifiScanInfo-timestamp: long--><!--Device-WifiScanInfo-timestamp: long-End-->

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.
