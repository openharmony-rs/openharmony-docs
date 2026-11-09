# WifiProxyConfig (System API)

```TypeScript
interface WifiProxyConfig
```

Represents the Wi-Fi proxy configuration.

**Since:** 10

<!--Device-wifiManager-interface WifiProxyConfig--><!--Device-wifiManager-interface WifiProxyConfig-End-->

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

Excluded objects of the manually configured proxy. Multiple objects are separated by commas (,).

**Type:** string

**Since:** 10

<!--Device-WifiProxyConfig-exclusionObjects?: string--><!--Device-WifiProxyConfig-exclusionObjects?: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## pacWebAddress

```TypeScript
pacWebAddress?: string
```

PAC web address of the proxy automatically configured.

**Type:** string

**Since:** 10

<!--Device-WifiProxyConfig-pacWebAddress?: string--><!--Device-WifiProxyConfig-pacWebAddress?: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## proxyMethod

```TypeScript
proxyMethod?: ProxyMethod
```

Proxy method.

**Type:** [ProxyMethod](arkts-connectivity-wifimanager-proxymethod-e-sys.md)

**Since:** 10

<!--Device-WifiProxyConfig-proxyMethod?: ProxyMethod--><!--Device-WifiProxyConfig-proxyMethod?: ProxyMethod-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## serverHostName

```TypeScript
serverHostName?: string
```

Server host name of the proxy manually configured.

**Type:** string

**Since:** 10

<!--Device-WifiProxyConfig-serverHostName?: string--><!--Device-WifiProxyConfig-serverHostName?: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## serverPort

```TypeScript
serverPort?: number
```

Server port of the proxy manually configured.

**Type:** number

**Since:** 10

<!--Device-WifiProxyConfig-serverPort?: int--><!--Device-WifiProxyConfig-serverPort?: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.
