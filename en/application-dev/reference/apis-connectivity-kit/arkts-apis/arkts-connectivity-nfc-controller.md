# @ohos.nfc.controller(Standard NFC)

The **nfcController** module provides APIs for opening and closing Near-Field Communication (NFC) and reading the NFC state.

**Since:** 7

**System capability:** SystemCapability.Communication.NFC.Core

## Modules to Import

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [closeNfc](arkts-connectivity-nfccontroller-closenfc-f.md) | Closes NFC. |
| [disableNfc](arkts-connectivity-nfccontroller-disablenfc-f.md) | Disables NFC. This API can be called only by system applications. |
| [enableNfc](arkts-connectivity-nfccontroller-enablenfc-f.md) | Enables NFC. This API can be called only by system applications. |
| [getNfcState](arkts-connectivity-nfccontroller-getnfcstate-f.md) | Obtains the NFC state. |
| [isNfcAvailable](arkts-connectivity-nfccontroller-isnfcavailable-f.md) | Checks whether the device supports NFC. |
| [isNfcOpen](arkts-connectivity-nfccontroller-isnfcopen-f.md) | Checks whether NFC is open. |
| [isNfcSupported](arkts-connectivity-nfccontroller-isnfcsupported-f.md) | Checks whether the device supports NFC. |
| [off](arkts-connectivity-nfccontroller-off-f.md#offnfcstatechange) | Unsubscribes from the NFC state changes. Upon successful unsubscription, the subscriber will not receive NFC state change notifications. This API uses an asynchronous callback to return the result. |
| [on](arkts-connectivity-nfccontroller-on-f.md#onnfcstatechange) | Enables listening for NFC state changes. This API uses an asynchronous callback to return the result. |
| [openNfc](arkts-connectivity-nfccontroller-opennfc-f.md) | Opens NFC. |

### Enums

| Name | Description |
| --- | --- |
| [NfcState](arkts-connectivity-nfccontroller-nfcstate-e.md) | Enumerates the NFC states. |
