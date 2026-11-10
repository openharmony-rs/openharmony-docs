# WifiLinkedInfo (System API)

```TypeScript
interface WifiLinkedInfo
```

Wi-Fi connection information.

**Since:** 9

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

Channel load. A larger value indicates a higher load.

**Type:** number

**Since:** 9

<!--Device-WifiLinkedInfo-chload: int--><!--Device-WifiLinkedInfo-chload: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## isHiLinkProNetwork

```TypeScript
isHiLinkProNetwork?: boolean
```

Whether the network is a HiLinkPro network. The value **true** indicates that the network is a HiLinkPro network, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 20

<!--Device-WifiLinkedInfo-isHiLinkProNetwork?: boolean--><!--Device-WifiLinkedInfo-isHiLinkProNetwork?: boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## networkId

```TypeScript
networkId: number
```

Network configuration ID.

**Type:** number

**Since:** 9

<!--Device-WifiLinkedInfo-networkId: int--><!--Device-WifiLinkedInfo-networkId: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## snr

```TypeScript
snr: number
```

Signal-to-noise ratio (SNR), in dB.

**Type:** number

**Since:** 9

<!--Device-WifiLinkedInfo-snr: int--><!--Device-WifiLinkedInfo-snr: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## suppState

```TypeScript
suppState: SuppState
```

Supplicant state.

**Type:** [SuppState](arkts-connectivity-wifimanager-suppstate-e-sys.md)

**Since:** 9

<!--Device-WifiLinkedInfo-suppState: SuppState--><!--Device-WifiLinkedInfo-suppState: SuppState-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## wifiTxRxValid

```TypeScript
wifiTxRxValid?: boolean
```

Whether the Wi-Fi transmitting (Tx) and receiving (Rx) functions are working properly.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WifiLinkedInfo-wifiTxRxValid?: boolean--><!--Device-WifiLinkedInfo-wifiTxRxValid?: boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.
