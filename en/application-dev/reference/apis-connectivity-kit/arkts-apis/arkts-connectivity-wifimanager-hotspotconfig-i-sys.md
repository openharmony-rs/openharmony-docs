# HotspotConfig (System API)

Wi-Fi hotspot configuration information. @typedef HotspotConfig

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## band

```TypeScript
band: number
```

The frequency band of the Wi-Fi hotspot

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## channel

```TypeScript
channel?: number
```

The channel of the Wi-Fi hotspot.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## ipAddress

```TypeScript
ipAddress?: string
```

IP address of the dhcp server, it's a string, For example 192.168.43.1

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## maxConn

```TypeScript
maxConn: number
```

The maximum number of connections allowed by the Wi-Fi hotspot

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## preSharedKey

```TypeScript
preSharedKey: string
```

The password of the Wi-Fi hotspot

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## securityType

```TypeScript
securityType: WifiSecurityType
```

The encryption mode of the Wi-Fi hotspot

**Type:** [WifiSecurityType](arkts-connectivity-wifimanager-wifisecuritytype-e.md)

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## ssid

```TypeScript
ssid: string
```

The SSID of the Wi-Fi hotspot

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.
