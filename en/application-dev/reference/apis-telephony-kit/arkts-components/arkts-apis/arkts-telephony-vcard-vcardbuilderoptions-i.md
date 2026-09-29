# VCardBuilderOptions

```TypeScript
export interface VCardBuilderOptions
```

Defines the VCard information.

**Since:** 23

<!--Device-vcard-export interface VCardBuilderOptions--><!--Device-vcard-export interface VCardBuilderOptions-End-->

**System capability:** SystemCapability.Telephony.CoreService

## Modules to Import

```TypeScript
import { vcard } from '@kit.TelephonyKit';
```

## cardType

```TypeScript
cardType?: VCardType
```

VCard version. The default value is **VERSION_21**.

**Type:** [VCardType](arkts-telephony-vcard-vcardtype-e.md)

**Since:** 23

<!--Device-VCardBuilderOptions-cardType?: VCardType--><!--Device-VCardBuilderOptions-cardType?: VCardType-End-->

**System capability:** SystemCapability.Telephony.CoreService

## charset

```TypeScript
charset?: string
```

VCard encoding type. The default value is **UTF-8**.

**Type:** string

**Since:** 23

<!--Device-VCardBuilderOptions-charset?: string--><!--Device-VCardBuilderOptions-charset?: string-End-->

**System capability:** SystemCapability.Telephony.CoreService
