# @ohos.nfc.controller(Standard NFC)

The **nfcController** module provides APIs for opening and closing Near-Field Communication (NFC) and reading the NFC state.

**Since:** 7

<!--Device-unnamed-declare namespace nfcController--><!--Device-unnamed-declare namespace nfcController-End-->

**System capability:** SystemCapability.Communication.NFC.Core

## Modules to Import

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [disableNfc](arkts-connectivity-nfccontroller-disablenfc-f.md#disablenfc-1) | Disables NFC. This API can be called only by system applications. |
| [enableNfc](arkts-connectivity-nfccontroller-enablenfc-f.md#enablenfc-1) | Enables NFC. This API can be called only by system applications. |
| [getNfcState](arkts-connectivity-nfccontroller-getnfcstate-f.md#getnfcstate-1) | Obtains the NFC state. |
| [isNfcOpen](arkts-connectivity-nfccontroller-isnfcopen-f.md#isnfcopen-1) | Checks whether NFC is open. |
| [isNfcSupported](arkts-connectivity-nfccontroller-isnfcsupported-f.md#isnfcsupported-1) | Checks whether the device supports NFC. |
| [off('nfcStateChange')](arkts-connectivity-nfccontroller-off-f.md#offnfcstatechange) | Unsubscribes from the NFC state changes. Upon successful unsubscription, the subscriber will not receive NFC state change notifications. This API uses an asynchronous callback to return the result. |
| [on('nfcStateChange')](arkts-connectivity-nfccontroller-on-f.md#onnfcstatechange) | Enables listening for NFC state changes. This API uses an asynchronous callback to return the result. |
| [closeNfc](arkts-connectivity-nfccontroller-closenfc-f.md#closenfc-1) | Closes NFC. |
| [isNfcAvailable](arkts-connectivity-nfccontroller-isnfcavailable-f.md#isnfcavailable-1) | Checks whether the device supports NFC. |
| [openNfc](arkts-connectivity-nfccontroller-opennfc-f.md#opennfc-1) | Opens NFC. |

### Enums

| Name | Description |
| --- | --- |
| [NfcState](arkts-connectivity-nfccontroller-nfcstate-e.md) | Enumerates the NFC states. |
