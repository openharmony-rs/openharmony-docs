# SystemLocaleManager (System API)

Provide some functions for settings and startup guide to select language or region.

**Since:** 10

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## constructor

```TypeScript
constructor()
```

Creates a SystemLocaleManager object.

**Since:** 10

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let systemLocaleManager: i18n.SystemLocaleManager = new i18n.SystemLocaleManager();
```

## getLanguageInfoArray

```TypeScript
getLanguageInfoArray(languages: Array<string>, options?: SortOptions): Array<LocaleItem>
```

Obtains the list of languages after sorting.

**Since:** 10

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| languages | Array&lt;string&gt; | Yes | Valid IDs of the languages to be sorted. |
| options | [SortOptions](arkts-localization-i18n-sortoptions-i-sys.md) | No | Language sorting option. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[LocaleItem](arkts-localization-i18n-localeitem-i-sys.md)&gt; | Language list after sorting. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

// Assume that the system language is zh-Hans, the system region is CN, and the system locale is zh-Hans-CN.
let systemLocaleManager: i18n.SystemLocaleManager = new i18n.SystemLocaleManager();
let languages: string[] = ["zh-Hans", "en-US", "pt", "ar"];
let sortOptions: i18n.SortOptions = {locale: "zh-Hans-CN", isUseLocalName: true, isSuggestedFirst: true};
try {
    // The language list after sorting is [zh-Hans, en-US, pt, ar].
    let sortedLanguages: Array<i18n.LocaleItem> = systemLocaleManager.getLanguageInfoArray(languages, sortOptions);
} catch(error) {
    let err: BusinessError = error as BusinessError;
    console.error(`call systemLocaleManager.getLanguageInfoArray failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getRegionInfoArray

```TypeScript
getRegionInfoArray(regions: Array<string>, options?: SortOptions): Array<LocaleItem>
```

Obtains the IDs of the countries or regions after sorting.

**Since:** 10

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| regions | Array&lt;string&gt; | Yes | Valid IDs of the countries or regions to be sorted. |
| options | [SortOptions](arkts-localization-i18n-sortoptions-i-sys.md) | No | Country/region sorting option. By default, locale is the current system locale, isUseLocalName is false, and isSuggestedFirst is true. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[LocaleItem](arkts-localization-i18n-localeitem-i-sys.md)&gt; | IDs of the countries or regions after sorting. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

// Assume that the system language is zh-Hans, the system region is CN, and the system locale is zh-Hans-CN.
let systemLocaleManager: i18n.SystemLocaleManager = new i18n.SystemLocaleManager();
let regions: string[] = ["CN", "US", "PT", "EG"];
let sortOptions: i18n.SortOptions = {locale: "zh-Hans-CN", isUseLocalName: false, isSuggestedFirst: true};
try {
    // The country/region list after sorting is [CN, EG, US, PT].
    let sortedRegions: Array<i18n.LocaleItem> = systemLocaleManager.getRegionInfoArray(regions, sortOptions);
} catch(error) {
    let err: BusinessError = error as BusinessError;
    console.error(`call systemLocaleManager.getRegionInfoArray failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getTimeZoneCityItemArray

```TypeScript
static getTimeZoneCityItemArray(): Array<TimeZoneCityItem>
```

Obtains list of time zone city items after sorting.

**Since:** 10

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TimeZoneCityItem](arkts-localization-i18n-timezonecityitem-i-sys.md)&gt; | List of time zone city items after sorting. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let timeZoneCityItemArray: Array<i18n.TimeZoneCityItem> = i18n.SystemLocaleManager.getTimeZoneCityItemArray();
  for (let i = 0; i < timeZoneCityItemArray.length; i++) {
      console.info(timeZoneCityItemArray[i].zoneId + ", " + timeZoneCityItemArray[i].cityId + ", " + timeZoneCityItemArray[i].cityDisplayName +
          ", " + timeZoneCityItemArray[i].offset + "\r\n");
  }
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call SystemLocaleManager.getTimeZoneCityItemArray failed, error code: ${err.code}, message: ${err.message}.`);
}
```
