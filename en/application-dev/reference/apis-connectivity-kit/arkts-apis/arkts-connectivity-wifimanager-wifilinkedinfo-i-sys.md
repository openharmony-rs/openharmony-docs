# WifiLinkedInfo

```TypeScript
interface WifiLinkedInfo
```

Wi-Fi connection information. @typedef WifiLinkedInfo

**Since:** 12

<!--Device-wifiManager-interface WifiLinkedInfo--><!--Device-wifiManager-interface WifiLinkedInfo-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## chload

```TypeScript
chload: number
```

The load value of this Wi-Fi connection. A greater value indicates a higher load.

**Type:** number

**Since:** 9

<!--Device-WifiLinkedInfo-chload: int--><!--Device-WifiLinkedInfo-chload: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## isHiLinkProNetwork

```TypeScript
isHiLinkProNetwork?: boolean
```

Whether the Wi-Fi hotspot is HiLinkPro network.

**Type:** boolean

**Since:** 20

<!--Device-WifiLinkedInfo-isHiLinkProNetwork?: boolean--><!--Device-WifiLinkedInfo-isHiLinkProNetwork?: boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## networkId

```TypeScript
networkId: number
```

The ID(uniquely identifies) of a Wi-Fi connection.

**Type:** number

**Since:** 9

<!--Device-WifiLinkedInfo-networkId: int--><!--Device-WifiLinkedInfo-networkId: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## snr

```TypeScript
snr: number
```

The signal-to-noise ratio (SNR) of this Wi-Fi connection.

**Type:** number

**Since:** 9

<!--Device-WifiLinkedInfo-snr: int--><!--Device-WifiLinkedInfo-snr: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## suppState

```TypeScript
suppState: SuppState
```

The state of the supplicant of this Wi-Fi connection.

**Type:** [SuppState](arkts-connectivity-wifimanager-suppstate-e-sys.md)

**Since:** 9

<!--Device-WifiLinkedInfo-suppState: SuppState--><!--Device-WifiLinkedInfo-suppState: SuppState-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## wifiTxRxValid

```TypeScript
wifiTxRxValid?: boolean
```

Whether Wi-Fi Tx and Rx are both working properly

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WifiLinkedInfo-wifiTxRxValid?: boolean--><!--Device-WifiLinkedInfo-wifiTxRxValid?: boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.
