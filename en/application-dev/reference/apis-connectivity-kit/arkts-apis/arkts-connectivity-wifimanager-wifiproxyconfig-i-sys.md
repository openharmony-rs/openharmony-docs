# WifiProxyConfig (System API)

Wi-Fi Proxy config. @typedef WifiProxyConfig

**Since:** 10

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## exclusionObjects

```TypeScript
exclusionObjects?: string
```

Exclusion objects for manual configured proxy. objects are separated by ','.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## pacWebAddress

```TypeScript
pacWebAddress?: string
```

PAC web address for auto configured proxy.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## proxyMethod

```TypeScript
proxyMethod?: ProxyMethod
```

Wi-Fi proxy method

**Type:** [ProxyMethod](arkts-connectivity-wifimanager-proxymethod-e-sys.md)

**Since:** 10

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## serverHostName

```TypeScript
serverHostName?: string
```

Server host name for manual configured proxy.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## serverPort

```TypeScript
serverPort?: number
```

Server port for manual configured proxy.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.
