# System

Provides system attribute configuration functions, including translating language and country/region names, obtaining the list of supported languages and countries/regions, and obtaining the system language and region.

**Since:** 9

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## addPreferredLanguage

```TypeScript
static addPreferredLanguage(language: string, index?: number): void
```

Adds a preferred language to the specified position on the preferred language list.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_CONFIGURATION

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| language | string | Yes | Valid ID of the language to be added as a preferred language. |
| index | number | No | Position to which the preferred language is added. The default value is the length of the preferred language list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

// Add zh-CN to the preferred language list.
let language = 'zh-CN';
let index = 0;
try {
  i18n.System.addPreferredLanguage(language, index); // Add zh-CN to the first place in the preferred language list.
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.addPreferredLanguage failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getSystemCollations

```TypeScript
static getSystemCollations(): Map<string, string>
```

Gets collations supported by system locale.

**Since:** 20

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Map&lt;string, string&gt; | The map will containing the collation's identifier and name. If the map is empty of the collation for given locale does not need to be set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let systemCollations: Map<string, string> = i18n.System.getSystemCollations();
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.getSystemCollations failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getSystemMeasurements

```TypeScript
static getSystemMeasurements(): Map<string, string>
```

Gets measurements supported by system locale.

**Since:** 20

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Map&lt;string, string&gt; | a map will containing identifier and name of measurements supported by system locale. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let systemMeasurements: Map<string, string> = i18n.System.getSystemMeasurements();
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.getSystemMeasurements failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getSystemNumberingSystems

```TypeScript
static getSystemNumberingSystems(): Map<string, string>
```

Gets numbering systems supported by system locale.

**Since:** 20

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Map&lt;string, string&gt; | a map will containing the numbering system 's identifier and sample. If the map is empty, there is no local digit for given locale. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let systemNumberingSystems: Map<string, string> = i18n.System.getSystemNumberingSystems();
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.getSystemNumberingSystems failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getSystemNumberPatterns

```TypeScript
static getSystemNumberPatterns(): Map<string, string>
```

Gets commonly used number patterns for system locale.

**Since:** 20

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Map&lt;string, string&gt; | a map containing the used number patterns and example of system locale. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let systemNumberPatterns: Map<string, string> = i18n.System.getSystemNumberPatterns();
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.getSystemNumberPatterns failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getSystemNumericalDatePatterns

```TypeScript
static getSystemNumericalDatePatterns(): Map<string, string>
```

Gets numerical date patterns and examples supported by system locale.

**Since:** 20

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Map&lt;string, string&gt; | a map containing the date patterns and examples |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let datePatterns: Map<string, string> = i18n.System.getSystemNumericalDatePatterns();
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.getSystemNumericalDatePatterns failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getUsingCollation

```TypeScript
static getUsingCollation(): string
```

Gets collation currently used by system locale.

**Since:** 20

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| string | The identifier of the collation model used by system locale will be return. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let usingCollation: string = i18n.System.getUsingCollation();
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.getUsingCollation failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getUsingMeasurement

```TypeScript
static getUsingMeasurement(): string
```

Gets measurement currently used by system locale.

**Since:** 20

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| string | The identifier of measurement system using by system locale |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let usingMeasurement: string = i18n.System.getUsingMeasurement();
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.getUsingMeasurement failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getUsingNumberingSystem

```TypeScript
static getUsingNumberingSystem(): string
```

Gets numbering system currently used by system locale.

**Since:** 20

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| string | the numbering systems's identifier. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

## getUsingNumberPattern

```TypeScript
static getUsingNumberPattern(): string
```

Gets number pattern used by system locale.

**Since:** 20

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| string | The number pattern identifier used by system locale |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let usingNumberPattern: string = i18n.System.getUsingNumberPattern();
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.getUsingNumberPattern failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getUsingNumericalDatePattern

```TypeScript
static getUsingNumericalDatePattern(): string
```

Gets numerical date pattern currently used by system locale.

**Since:** 20

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| string | The numerical date pattern used by system locale |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let datePattern: string = i18n.System.getUsingNumericalDatePattern();
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.getUsingNumericalDatePattern failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## removePreferredLanguage

```TypeScript
static removePreferredLanguage(index: number): void
```

Removes a preferred language from the specified position on the preferred language list.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_CONFIGURATION

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Position of the preferred language to delete. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed.<br>**Applicable version:** 9 - 24 |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

// Delete the first preferred language from the preferred language list.
let index: number = 0;
try {
  i18n.System.removePreferredLanguage(index);
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.removePreferredLanguage failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## set24HourClock

```TypeScript
static set24HourClock(option: boolean): void
```

Sets whether to use the 24-hour clock.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_CONFIGURATION

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | boolean | Yes | Whether to use the 24-hour clock. The value "true" means to use the 24-hour clock, the the value "false" means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed.<br>**Applicable version:** 9 - 24 |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

// Set the system time to the 24-hour clock.
try {
  i18n.System.set24HourClock(true);
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.set24HourClock failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## setFirstDayOfWeek

```TypeScript
static setFirstDayOfWeek(type: WeekDay): void
```

Sets the first day of a week.

**Since:** 18

**Required permissions:** ohos.permission.UPDATE_CONFIGURATION

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [WeekDay](arkts-localization-i18n-weekday-e.md) | Yes | Start day of a week. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  i18n.System.setFirstDayOfWeek (i18n.WeekDay.MON); // Set the preferred start day of a week to Monday.
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.setFirstDayOfWeek failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## setSystemCollation

```TypeScript
static setSystemCollation(identifier: string): void
```

Sets the system collation mode.

**Since:** 20

**Required permissions:** ohos.permission.UPDATE_CONFIGURATION

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| identifier | string | Yes | Identifier of the collation mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [8900001](../errorcode-i18n.md#8900001-parameter-verification-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  i18n.System.setSystemCollation("zhuyin"); // If the specified collation mode is not supported, an error is reported.
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.setSystemCollation failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## setSystemLanguage

```TypeScript
static setSystemLanguage(language: string): void
```

Sets the system language.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_CONFIGURATION

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| language | string | Yes | Valid language ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

// Set the system language
try {
  i18n.System.setSystemLanguage('zh'); // Set the current system language to zh.
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.setSystemLanguage failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## setSystemLocale

```TypeScript
static setSystemLocale(locale: string): void
```

Sets the system locale.

**Since:** 9

**Deprecated since:** 20

**Required permissions:** ohos.permission.UPDATE_CONFIGURATION

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | string | Yes | System locale, which consists of the language, script, and country/region. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  i18n.System.setSystemLocale('zh-CN'); // Set the system locale to zh-CN.
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.setSystemLocale failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## setSystemMeasurement

```TypeScript
static setSystemMeasurement(identifier: string): void
```

Sets the measurement system used by the system locale.

**Since:** 20

**Required permissions:** ohos.permission.UPDATE_CONFIGURATION

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| identifier | string | Yes | Identifier of the measurement system. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [8900001](../errorcode-i18n.md#8900001-parameter-verification-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  i18n.System.setSystemMeasurement("uksystem"); // If the specified measurement system is not supported, error code 8900001 is reported.
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.setSystemMeasurement failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## setSystemNumberingSystem

```TypeScript
static setSystemNumberingSystem(identifier: string): void
```

Sets the numbering system used by the system locale.

**Since:** 20

**Required permissions:** ohos.permission.UPDATE_CONFIGURATION

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| identifier | string | Yes | Identifier of the numbering system. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [8900001](../errorcode-i18n.md#8900001-parameter-verification-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  i18n.System.setSystemNumberingSystem("arab"); // If the specified numbering system is not supported, an error is reported.
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.setSystemNumberingSystem failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## setSystemNumberPattern

```TypeScript
static setSystemNumberPattern(pattern: string): void
```

Sets the number pattern used by the system locale.

**Since:** 20

**Required permissions:** ohos.permission.UPDATE_CONFIGURATION

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pattern | string | Yes | Identifier of the number pattern. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [8900001](../errorcode-i18n.md#8900001-parameter-verification-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  i18n.System.setSystemNumberPattern("002e002c"); // If the specified number pattern is not supported, an error is reported.
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.setSystemNumberPattern failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## setSystemNumericalDatePattern

```TypeScript
static setSystemNumericalDatePattern(identifier : string): void
```

Sets the numerical date pattern used by the system locale.

**Since:** 20

**Required permissions:** ohos.permission.UPDATE_CONFIGURATION

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| identifier | string | Yes | Identifier of the numerical date pattern. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [8900001](../errorcode-i18n.md#8900001-parameter-verification-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  i18n.System.setSystemNumericalDatePattern("dd/MM/y"); // If the specified numerical date pattern is not supported, error code 8900001 is reported.
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.setSystemNumericalDatePattern failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## setSystemRegion

```TypeScript
static setSystemRegion(region: string): void
```

Sets the system region.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_CONFIGURATION

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| region | string | Yes | Valid region ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  i18n.System.setSystemRegion('CN'); // Set the current system region to CN.
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.setSystemRegion failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## setTemperatureType

```TypeScript
static setTemperatureType(type: TemperatureType): void
```

Sets the temperature unit of the system.

**Since:** 18

**Required permissions:** ohos.permission.UPDATE_CONFIGURATION

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [TemperatureType](arkts-localization-i18n-temperaturetype-e.md) | Yes | Temperature unit. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  i18n.System.setTemperatureType(i18n.TemperatureType.CELSIUS); //: Set the temperature unit to °C.
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.setTemperatureType failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## setUsingLocalDigit

```TypeScript
static setUsingLocalDigit(flag: boolean): void
```

Specifies whether to enable use of local digits.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_CONFIGURATION

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| flag | boolean | Yes | Whether to turn on the local digit switch. The value "true" means to turn on the local digit switch, and the value "false" indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed.<br>**Applicable version:** 9 - 24 |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  i18n.System.setUsingLocalDigit(true); // Enable the local digit switch.
} catch(error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.setUsingLocalDigit failed, error code: ${err.code}, message: ${err.message}.`);
}
```
