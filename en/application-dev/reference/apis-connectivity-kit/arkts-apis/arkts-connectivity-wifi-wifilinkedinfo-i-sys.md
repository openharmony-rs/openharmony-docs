# WifiLinkedInfo

Wi-Fi connection information.

@interface WifiLinkedInfo

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [WifiLinkedInfo](arkts-connectivity-wifimanager-wifilinkedinfo-i.md)

**System capability:** SystemCapability.Communication.WiFi.STA

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## chload

```TypeScript
chload: number
```

The load value of this Wi-Fi connection. A greater value indicates a higher load.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [chload](arkts-connectivity-wifimanager-wifilinkedinfo-i-sys.md#chload)

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## networkId

```TypeScript
networkId: number
```

The ID(uniquely identifies) of a Wi-Fi connection.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [networkId](arkts-connectivity-wifimanager-wifilinkedinfo-i-sys.md#networkid)

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## snr

```TypeScript
snr: number
```

The signal-to-noise ratio (SNR) of this Wi-Fi connection.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [snr](arkts-connectivity-wifimanager-wifilinkedinfo-i-sys.md#snr)

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## suppState

```TypeScript
suppState: SuppState
```

The state of the supplicant of this Wi-Fi connection.

**Type:** [SuppState](arkts-connectivity-wifi-suppstate-e-sys.md)

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [suppState](arkts-connectivity-wifimanager-wifilinkedinfo-i-sys.md#suppstate)

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.
