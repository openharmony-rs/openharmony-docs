# isSupported

## Modules to Import

```TypeScript
import { cardEmulation } from '@kit.ConnectivityKit';
```

## isSupported

```TypeScript
function isSupported(feature: number): boolean
```

Checks whether a certain type of card emulation is supported.

> **NOTE:** 
> 
> This API is supported since API version 6 and deprecated since API version 9. Use
> [hasHceCapability](arkts-connectivity-cardemulation-hashcecapability-f.md) instead.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [hasHceCapability](arkts-connectivity-cardemulation-hashcecapability-f.md)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NFC.CardEmulation

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| feature | number | Yes | Card emulation type to check. For details, see [FeatureType](arkts-connectivity-cardemulation-featuretype-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the card emulation type is supported; returns **false** otherwise. |

**Examples**

```TypeScript
// Applicable to devices other than lite wearables
import { cardEmulation } from '@kit.ConnectivityKit';

let isHceSupported: boolean = cardEmulation.isSupported(cardEmulation.FeatureType.HCE);
if (!isHceSupported) {
    console.info('this device is not supported for HCE, ignore it.');
}
```

```TypeScript
// Applicable to lite wearables
import cardEmulation from '@ohos.nfc.cardEmulation';

let isHceSupported = cardEmulation.isSupported(cardEmulation.FeatureType.HCE);
if (!isHceSupported) {
    console.error('this device is not supported for HCE, ignore it.');
}
```
