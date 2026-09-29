# PhoneNumberFormat

```TypeScript
export class PhoneNumberFormat
```

Provides phone number management capabilities, such as phone number validity verification, formatting, and home location retrieval.

**Since:** 8

<!--Device-i18n-export class PhoneNumberFormat--><!--Device-i18n-export class PhoneNumberFormat-End-->

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## constructor

```TypeScript
constructor(country: string, options?: PhoneNumberFormatOptions)
```

Creates a **PhoneNumberFormat** object.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PhoneNumberFormat-constructor(country: string, options?: PhoneNumberFormatOptions)--><!--Device-PhoneNumberFormat-constructor(country: string, options?: PhoneNumberFormatOptions)-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| country | string | Yes | Country/region to which the phone number to be formatted belongs. |
| options | [PhoneNumberFormatOptions](arkts-localization-i18n-phonenumberformatoptions-i.md) | No | Options for **PhoneNumberFormat** object initialization. The default value is **NATIONAL**. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let option: i18n.PhoneNumberFormatOptions = { type: 'E164' };
let phoneNumberFormat: i18n.PhoneNumberFormat = new i18n.PhoneNumberFormat('CN', option);
```

## format

```TypeScript
format(phoneNumber: string): string
```

Formats a phone number.

> **Description**
> 
> Formatting dialed phone numbers is supported since API version 12.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PhoneNumberFormat-format(phoneNumber: string): string--><!--Device-PhoneNumberFormat-format(phoneNumber: string): string-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| phoneNumber | string | Yes | Phone number to be formatted.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| string | Formatted phone number. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let formatter: i18n.PhoneNumberFormat = new i18n.PhoneNumberFormat('CN');
// formattedPhoneNumber = '158 **** 2312'
let formattedPhoneNumber: string = formatter.format('158****2312');

// Format the phone number being dialed.
let option: i18n.PhoneNumberFormatOptions = { type: 'TYPING' };
let typingFormatter: i18n.PhoneNumberFormat = new i18n.PhoneNumberFormat('CN', option);
let phoneNumber: string = '130493';
let formatResult: string = '';
for (let i = 0; i < phoneNumber.length; i++) {
  formatResult += phoneNumber.charAt(i);
  formatResult = typingFormatter.format(formatResult); // formatResult = '130 493'
}
```

## getLocationName

```TypeScript
getLocationName(phoneNumber: string, locale: string): string
```

Obtains the home location of a phone number.

> **Description**
> 
> This API can be used to obtain the home location of a dialed number in real time since API version 23.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PhoneNumberFormat-getLocationName(phoneNumber: string, locale: string): string--><!--Device-PhoneNumberFormat-getLocationName(phoneNumber: string, locale: string): string-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| phoneNumber | string | Yes | Phone number. To obtain the home location of a number in other countries/regions, you need to prefix the number with **00** and the country code.<br>**Since:** 12 |
| locale | string | Yes | [System locale](../../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Home location of the phone number. If the number is invalid, an empty string is returned. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

// Obtain the home location of the complete phone number.
let phonenumberFormat: i18n.PhoneNumberFormat = new i18n.PhoneNumberFormat('CN');
let locationName: string = phonenumberFormat.getLocationName('158****2345', 'zh-CN'); // locationName = 'Zhanjiang, Guangdong Province'
let locName: string = phonenumberFormat.getLocationName('0039312****789', 'zh-CN'); // locName = 'Italy'

// Obtain the home area of the phone number being dialed.
let option: i18n.PhoneNumberFormatOptions = { type: 'TYPING' };
let typingFormatter: i18n.PhoneNumberFormat = new i18n.PhoneNumberFormat('CN', option);
let formatResult = typingFormatter.getLocationName('1', 'en'); // formatResult = ''
formatResult = typingFormatter.getLocationName('13', 'en'); // formatResult = 'China'
formatResult = typingFormatter.getLocationName('133', 'en'); // formatResult = 'China'
formatResult = typingFormatter.getLocationName('1334', 'en'); // formatResult = 'China'
formatResult = typingFormatter.getLocationName('13342', 'en'); // formatResult = 'China'
formatResult = typingFormatter.getLocationName('133426', 'en'); // formatResult = 'Dongguan, Guangdong'
```

## isValidNumber

```TypeScript
isValidNumber(phoneNumber: string): boolean
```

Checks whether the phone number is valid for the country/region in the **PhoneNumberFormat** object.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PhoneNumberFormat-isValidNumber(phoneNumber: string): boolean--><!--Device-PhoneNumberFormat-isValidNumber(phoneNumber: string): boolean-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| phoneNumber | string | Yes | Phone number to be checked.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the phone number is valid. The value **true** indicates that the phone number is valid, and the value **false** indicates the opposite. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let formatter: i18n.PhoneNumberFormat = new i18n.PhoneNumberFormat('CN');
let isValidNumber: boolean = formatter.isValidNumber('158****2312'); // isValidNumber = true
```
