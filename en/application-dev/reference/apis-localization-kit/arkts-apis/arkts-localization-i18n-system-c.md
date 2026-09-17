# System

Provides system attribute configuration functions, including translating language and country/region names, obtaining the list of supported languages and countries/regions, and obtaining the system language and region.

**Since:** 9

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getAppPreferredLanguage

```TypeScript
static getAppPreferredLanguage(): string
```

Obtains the preferred language of an application.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| string | Preferred language of the application. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let appPreferredLanguage: string = i18n.System.getAppPreferredLanguage();
```

## getDisplayCountry

```TypeScript
static getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string
```

Obtains the country/region display name in the specified language.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| country | string | Yes | Valid country/region code. For details, see [System Locale](../../../internationalization/i18n-locale-culture.md#how-it-works). |
| locale | string | Yes | [System locale](../../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region. |
| sentenceCase | boolean | No | Whether to use sentence case to display the text. The value **true** means to display the text in title case format, and the value **false** means to display the text in the default case format of the locale. The default value is **true**. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Country/region display name in the specified language. |

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
  let displayCountry: string = i18n.System.getDisplayCountry('CN', 'en-GB'); // displayCountry = 'China'
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.getDisplayCountry failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getDisplayLanguage

```TypeScript
static getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string
```

Obtains the language display name in the specified language.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| language | string | Yes | Valid language ID. For details, see [System Locale](../../../internationalization/i18n-locale-culture.md#how-it-works). |
| locale | string | Yes | [System locale](../../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region. |
| sentenceCase | boolean | No | Whether to use sentence case to display the text. The value **true** means to display the text in title case format, and the value **false** means to display the text in the default case format of the locale. The default value is **true**. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Language display name in the specified language. |

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
  // Obtain the display name of Chinese in English.
  let displayLanguage: string = i18n.System.getDisplayLanguage('zh', 'en-GB'); // displayLanguage = 'Chinese'
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.getDisplayLanguage failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getFirstDayOfWeek

```TypeScript
static getFirstDayOfWeek(): WeekDay
```

Obtains the first day of a week in the system settings.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| [WeekDay](arkts-localization-i18n-weekday-e.md) | Start day of a week. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let firstDayOfWeek: i18n.WeekDay = i18n.System.getFirstDayOfWeek();
```

## getFirstPreferredLanguage

```TypeScript
static getFirstPreferredLanguage(): string
```

Obtains the first language in the preferred language list.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| string | First language in the preferred language list. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let firstPreferredLanguage: string = i18n.System.getFirstPreferredLanguage();
```

## getPreferredLanguageList

```TypeScript
static getPreferredLanguageList(): Array<string>
```

Obtains the list of preferred languages.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | List of preferred languages. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let preferredLanguageList: Array<string> = i18n.System.getPreferredLanguageList();
```

## getSimplifiedLanguage

```TypeScript
static getSimplifiedLanguage(language?: string): string
```

Obtains the simplified representation of a language. For example, the simplified representation of **en-Latn-US** is **en**, and that of **en-Latn-GB** is **en-GB**.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| language | string | No | [Valid language ID](../../../internationalization/i18n-locale-culture.md#how-it-works). The default value is the system language. |

**Return value:**

| Type | Description |
| --- | --- |
| string | If **language** is not passed, the application checks for dialects supported by the system based on the system language and locale. If such a dialect is found, the simplified representation of the dialect is returned. Otherwise, the simplified representation of the system language is returned. If **language** is passed, the simplified representation of the specified language is returned. |

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
  // simplifiedLanguage = 'zh'
  let simplifiedLanguage: string = i18n.System.getSimplifiedLanguage('zh-Hans-CN');
  // Obtain the simplified representation of the current system language.
  let simplifiedSystemLanguage: string = i18n.System.getSimplifiedLanguage();
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.getSimplifiedLanguage failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getSystemCountries

```TypeScript
static getSystemCountries(language: string): Array<string>
```

Obtains the list of countries/regions supported for the specified language.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| language | string | Yes | [Valid language ID](../../../internationalization/i18n-locale-culture.md#how-it-works). |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | List of countries/regions supported for the specified language. |

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
  // systemCountries = [ 'ZW', 'YT', 'YE', ..., 'ER', 'CN', 'DE' ]
  let systemCountries: Array<string> = i18n.System.getSystemCountries('zh');
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.getSystemCountries failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getSystemLanguage

```TypeScript
static getSystemLanguage(): string
```

Obtains the current system language. To listen for system language changes, enable listening for [COMMON_EVENT_LOCALE_CHANGED](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-commoneventmanager-support-e.md#common_event_locale_changed). For details, see [System Language and Region](../../../internationalization/i18n-system-language-region.md#how-to-develop).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| string | Language ID. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let systemLanguage: string = i18n.System.getSystemLanguage(); // If the system language is simplified Chinese, then systemLanguage is 'zh-Hans'.
```

## getSystemLanguages

```TypeScript
static getSystemLanguages(): Array<string>
```

Obtains the list of system languages. Since API version 11, this API is supported in ArkTS widgets.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | List of system languages. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

// systemLanguages = [ 'ug', 'bo', 'zh-Hant', 'en-Latn-US', 'zh-Hans' ]
let systemLanguages: Array<string> = i18n.System.getSystemLanguages();
```

## getSystemLocale

```TypeScript
static getSystemLocale(): string
```

Obtains the current system locale.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [getSystemLocaleInstance](#getsystemlocaleinstance)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| string | Locale ID. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let systemLocale: string = i18n.System.getSystemLocale(); // If the system language is simplified Chinese and the system region is China, then systemLocale is zh-Hans-CN.
```

## getSystemLocaleInstance

```TypeScript
static getSystemLocaleInstance(): Intl.Locale
```

Obtains the current system locale. To listen for system locale changes, enable listening for [COMMON_EVENT_LOCALE_CHANGED](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-commoneventmanager-support-e.md#common_event_locale_changed). For details, see [System Language and Region](../../../internationalization/i18n-system-language-region.md#how-to-develop).

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| [Intl.Locale](arkts-localization-intl-locale-c.md) | the locale object currently used by the system. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let systemLocale: Intl.Locale = i18n.System.getSystemLocaleInstance();
```

## getSystemRegion

```TypeScript
static getSystemRegion(): string
```

Obtains the current system country/region. To listen for system region changes, enable listening for [COMMON_EVENT_LOCALE_CHANGED](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-commoneventmanager-support-e.md#common_event_locale_changed). For details, see [System Language and Region](../../../internationalization/i18n-system-language-region.md#how-to-develop).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| string | Country/region ID. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let systemRegion: string = i18n.System.getSystemRegion(); // If the system region is China, then systemRegion is CN.
```

## getTemperatureName

```TypeScript
static getTemperatureName(type: TemperatureType): string
```

Obtains the name of a temperature unit.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [TemperatureType](arkts-localization-i18n-temperaturetype-e.md) | Yes | Temperature unit. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Name of the temperature unit, which can be **celsius**, **fahrenheit**, and **kelvin**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  // temperatureName = 'celsius'
  let temperatureName: string = i18n.System.getTemperatureName(i18n.TemperatureType.CELSIUS);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.getTemperatureName failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getTemperatureType

```TypeScript
static getTemperatureType(): TemperatureType
```

Obtains the temperature unit of the system.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| [TemperatureType](arkts-localization-i18n-temperaturetype-e.md) | Temperature unit. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let temperatureType: i18n.TemperatureType = i18n.System.getTemperatureType();
```

## getUsingLocalDigit

```TypeScript
static getUsingLocalDigit(): boolean
```

Checks whether use of local digits is enabled.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether use of local digits is enabled. The value **true** indicates that use of local digits is enabled, and the value **false** indicates the opposite. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let usingLocalDigit: boolean = i18n.System.getUsingLocalDigit();
```

## is24HourClock

```TypeScript
static is24HourClock(): boolean
```

Checks whether the 24-hour clock is used. To listen for system time format changes, enable listening for [COMMON_EVENT_TIME_CHANGED](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-commoneventmanager-support-e.md#common_event_time_changed). For details, see [User Preference](../../../internationalization/i18n-user-preferences.md#how-to-develop).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the 24-hour clock is used. The value **true** indicates that the 24-hour clock is used, the the value **false** means the opposite. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let is24HourClock: boolean = i18n.System.is24HourClock(); // If the 24-hour clock is used, then is24HourClock is true.
```

## isSuggested

```TypeScript
static isSuggested(language: string, region?: string): boolean
```

Checks whether a language is a suggested language in the specified region. It can be used for region-based language recommendation or language-based region recommendation.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| language | string | Yes | [Valid language ID](../../../internationalization/i18n-locale-culture.md#how-it-works), for example, **zh**. |
| region | string | No | [Valid country/region code](../../../internationalization/i18n-locale-culture.md#how-it-works), for example, **CN**. The default value is the country/region of the SIM card. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether a language is a suggested language. The value **true** indicates that the language is a suggested language of the region, the the value false indicates the opposite. |

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
  let isSuggestedCountry: boolean = i18n.System.isSuggested('zh', 'CN'); // isSuggestedCountry = true
  isSuggestedCountry = i18n.System.isSuggested('en'); // Check whether a language is a suggested language for the current system region.
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.isSuggested failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## setAppPreferredLanguage

```TypeScript
static setAppPreferredLanguage(language: string): void
```

Sets the preferred language of the application. Resources are loaded in the preferred language when the application is launched. If the preferred language is set to **default**, the application's language will be the same as the system language, and the setting will take effect upon cold starting of the application.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| language | string | Yes | [Valid language ID](../../../internationalization/i18n-locale-culture.md#how-it-works) or **default**. |

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
  i18n.System.setAppPreferredLanguage('zh');
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.setAppPreferredLanguage failed, error code: ${err.code}, message: ${err.message}.`);
}
```
