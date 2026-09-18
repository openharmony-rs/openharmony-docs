# I18NUtil

Internationalization utility class, which provides the capabilities of unit conversion, date sequence retrieval, time segment name retrieval, region matching, and path localization.

**Since:** 9

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## convertCanonicalLocaleIdentifier

```TypeScript
static convertCanonicalLocaleIdentifier(locale: string): string
```

Adjusts a locale ID to a format that complies with the [BCP47](https://www.rfc-editor.org/info/bcp47) standard.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | string | Yes | Locale string to be converted, which consists of the language, script, and country/region. |

**Return value:**

| Type | Description |
| --- | --- |
| string | If the input locale ID is valid, a locale ID that complies with the [BCP47](https://www.rfc-editor.org/info/bcp47) standard will be returned. If the input locale ID is invalid, an empty string is returned. |

**Examples**

```TypeScript
let result: string = i18n.I18NUtil.convertCanonicalLocaleIdentifier('zh-cn'); // result = 'zh-CN'
```

## getBestMatchLocale

```TypeScript
static getBestMatchLocale(locale: string, localeList: string[]): string
```

Obtains the locale that best matches a region from the specified locale list.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | string | Yes | [Locale ID](../../../internationalization/i18n-locale-culture.md#how-it-works), for example, **zh-Hans-CN**. |
| localeList | string[] | Yes | List of locale IDs. |

**Return value:**

| Type | Description |
| --- | --- |
| string | ID of the locale that best matches a region. If no matching locale is found, an empty string is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let matchedLocaleId: string = i18n.I18NUtil.getBestMatchLocale('zh-Hans-CN',
    ['en-Latn-US', 'en-GB', 'zh-Hant-CN', 'zh-Hans-MO']); // matchedLocaleId = 'zh-Hans-MO'
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call I18NUtil.getBestMatchLocale failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getDateOrder

```TypeScript
static getDateOrder(locale: string): string
```

Obtains the sequence of the year, month, and day in the specified locale.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | string | Yes | [Locale ID](../../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region, for example, **zh-Hans-CN**. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Sequence of the year, month, and day in the locale. **y** indicates the year, **L** indicates the month, and **d** indicates the day. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let order: string = i18n.I18NUtil.getDateOrder('zh-CN'); // order = 'y-L-d'
```

## getThreeLetterLanguage

```TypeScript
static getThreeLetterLanguage(locale: string): string
```

Converts a language code from two letters to three letters.

For example, the two-letter language code of Chinese is **zh**, and the corresponding three-letter language code is **zho**. For details, see [ISO 639](https://www.iso.org/iso-639-language-code).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | string | Yes | Two-letter code of the language to be converted, for example, **zh**. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Language code after conversion. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let language: string = i18n.I18NUtil.getThreeLetterLanguage('zh') // language = 'zho'
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call I18NUtil.getThreeLetterLanguage failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getThreeLetterRegion

```TypeScript
static getThreeLetterRegion(locale: string): string
```

Converts a region code from two letters to three letters.

For example, the two-letter region code of China is **CN**, and the corresponding three-letter region code is **CHN**. For details, see [ISO 3166](https://www.iso.org/iso-3166-country-codes.html).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | string | Yes | Two-letter country/region code to be converted, for example, **CN**. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Region code after conversion . |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let region: string = i18n.I18NUtil.getThreeLetterRegion('CN') // region = 'CHN'
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call I18NUtil.getThreeLetterRegion failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getTimePeriodName

```TypeScript
static getTimePeriodName(hour:number, locale?: string): string
```

Obtains the localized expression of the specified time in the specified locale.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hour | number | Yes | Specified time, for example, **16**. |
| locale | string | No | [System locale](../../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region. for example, **zh-Hans-CN**. The default value is the current system locale. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Localized expression of the specified time in the specified locale. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let name: string = i18n.I18NUtil.getTimePeriodName(2, 'zh-CN'); // name = 'a.m.'
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call I18NUtil.getTimePeriodName failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getUnicodeWrappedFilePath

```TypeScript
static getUnicodeWrappedFilePath(path: string, delimiter?: string, locale?: Intl.Locale): string
```

Localizes a file path for the specified locale.

For example, "/data/out/tmp" is changed to "tmp/out/data/" after localization.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path to mirror, for example, "/data/out/tmp". |
| delimiter | string | No | Path delimiter. The default value is "/". |
| locale | [Intl.Locale](arkts-localization-intl-locale-c.md) | No | **Locale** object. The default value is the current system locale. |

**Return value:**

| Type | Description |
| --- | --- |
| string | File path after localization. If the specified locale object corresponds to an RTL language, the processed file path contains a direction control character to ensure that the file path is displayed in mirror mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [8900001](../errorcode-i18n.md#8900001-parameter-verification-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let path: string = '/data/out/tmp';
  let delimiter: string = '/';
  let locale: Intl.Locale = new Intl.Locale('ar');
  let mirrorPath: string =
    i18n.I18NUtil.getUnicodeWrappedFilePath(path, delimiter, locale); // mirrorPath is displayed as tmp/out/data/.
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call I18NUtil.getUnicodeWrappedFilePath failed, error code: ${err.code}, message: ${err.message}.`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n, intl } from '@kit.LocalizationKit';

try {
  let path: string = '/data/out/tmp';
  let delimiter: string = '/';
  let locale: intl.Locale = new intl.Locale('ar');
  let mirrorPath: string =
    i18n.I18NUtil.getUnicodeWrappedFilePath(path, delimiter, locale); // mirrorPath is displayed as tmp/out/data/.
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call I18NUtil.getUnicodeWrappedFilePath failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getUnicodeWrappedFilePath

```TypeScript
static getUnicodeWrappedFilePath(path: string, delimiter?: string, locale?: intl.Locale): string
```

Localizes a file path for the specified locale.

For example, "/data/out/tmp" is changed to "tmp/out/data/" after localization.

**Since:** 18

**Deprecated since:** 20

**Substitutes:** [getUnicodeWrappedFilePath](#getunicodewrappedfilepath)(path: string, delimiter?: string, locale?: Intl.Locale)

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path to mirror, for example, "/data/out/tmp". |
| delimiter | string | No | Path delimiter. The default value is "/". |
| locale | [intl.Locale](arkts-localization-intl-locale-c.md) | No | **Locale** object. The default value is the current system locale. |

**Return value:**

| Type | Description |
| --- | --- |
| string | File path after localization. If the specified locale object corresponds to an RTL language, the processed file path contains a direction control character to ensure that the file path is displayed in mirror mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

See [getUnicodeWrappedFilePath](#getunicodewrappedfilepath)

## setUnicodeWrappedBidiDirection

```TypeScript
static setUnicodeWrappedBidiDirection(text: string, direction: 'RTL' | 'LTR'): string
```

Sets the text direction for certain text within a paragraph, including RTL (right-to-left) and LTR (left-to-right). NOTE: The setting does not take effect within strong characters (characters with an intrinsic, unambiguous writing direction).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Text for which the direction needs to be set. |
| direction | 'RTL' &#124; 'LTR' | Yes | The value can be "RTL" or "LTR"."RTL" indicates setting the input text direction from right to left."LTR" indicates setting the input text direction from left to right. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Processed Text. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let text: string = '(012) 345-6789';
  let result: string = i18n.I18NUtil.setUnicodeWrappedBidiDirection(text, 'LTR');
  console.info(`setUnicodeWrappedBidiDirection, result: ${result}`);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call I18NUtil.setUnicodeWrappedBidiDirection failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## unitConvert

```TypeScript
static unitConvert(fromUnit: UnitInfo, toUnit: UnitInfo, value: number, locale: string, style?: string): string
```

Converts one measurement unit into another and formats the unit based on the specified locale and style.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fromUnit | [UnitInfo](arkts-localization-i18n-unitinfo-i.md) | Yes | Measurement unit to be converted. |
| toUnit | [UnitInfo](arkts-localization-i18n-unitinfo-i.md) | Yes | Measurement unit to be converted to. |
| value | number | Yes | Value of the measurement unit to be converted. |
| locale | string | Yes | [Locale ID](../../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region, for example, **zh-Hans-CN**. |
| style | string | No | Style used for formatting. The value can be **long**, **short**, or **narrow**. The default value is **short**. For details about the meaning or display effect of different values, see [Number and Unit of Measurement Formatting](../../../internationalization/i18n-numbers-weights-measures.md). |

**Return value:**

| Type | Description |
| --- | --- |
| string | String converted to the measurement unit after formatting. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let fromUnit: i18n.UnitInfo = { unit: 'cup', measureSystem: 'US' };
let toUnit: i18n.UnitInfo = { unit: 'liter', measureSystem: 'SI' };
let convertResult: string =
  i18n.I18NUtil.unitConvert(fromUnit, toUnit, 1000, 'en-US', 'long'); // convertResult = '236.588 liters'
```
