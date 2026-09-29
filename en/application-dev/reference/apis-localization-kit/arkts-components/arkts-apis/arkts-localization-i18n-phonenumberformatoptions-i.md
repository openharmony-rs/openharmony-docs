# PhoneNumberFormatOptions

```TypeScript
export interface PhoneNumberFormatOptions
```

Options for **PhoneNumberFormat** object initialization.

**Since:** 8

<!--Device-i18n-export interface PhoneNumberFormatOptions--><!--Device-i18n-export interface PhoneNumberFormatOptions-End-->

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## type

```TypeScript
type?: string
```

Type of the phone number. The value can be **E164**, **INTERNATIONAL**, **NATIONAL**, **RFC3966**, or **TYPING**.

- In API version 8, **type** is mandatory.  
- In API version 9 or later, **type** is optional.  
- In API version 12 or later, TYPING is supported, which indicates that the dialed number is formatted in real  
time.  
- In API version 23 or later, TYPING supports real-time obtaining of the home location of a dialed number.

**Type:** string

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PhoneNumberFormatOptions-type?: string--><!--Device-PhoneNumberFormatOptions-type?: string-End-->

**System capability:** SystemCapability.Global.I18n
