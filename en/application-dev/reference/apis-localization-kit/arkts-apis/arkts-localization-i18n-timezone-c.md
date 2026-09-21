# TimeZone

```TypeScript
export class TimeZone
```

Provides time zone management capabilities, such as time zone name translation, offset retrieval, and transition rule retrieval.

**Since:** 7

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getAppDefaultTimeZone

```TypeScript
static getAppDefaultTimeZone(): TimeZone
```

Obtains the default time zone object used by an application. If the default time zone has been set by calling setAppDefaultTimeZoneById, the default time zone object is returned. Otherwise, the system time zone object is returned.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| [TimeZone](arkts-localization-i18n-timezone-c.md) | TimeZone object, first set by application, then system time zone, last GMT time zone. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let zoneID: string = 'Asia/Shanghai';
  i18n.TimeZone.setAppDefaultTimeZoneById(zoneID);
  console.info('setAppDefaultTimeZoneById success.');
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call TimeZone.setAppDefaultTimeZoneById failed, error code: ${err.code}, message: ${err.message}.`);
}
let timeZone: i18n.TimeZone = i18n.TimeZone.getAppDefaultTimeZone();
let id: string = timeZone.getID();
console.info(`getAppDefaultTimeZone success, time zone id: ${id}`);
```

## getAvailableIDs

```TypeScript
static getAvailableIDs(): Array<string>
```

Obtains the list of time zone IDs supported by the system.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | List of time zone IDs supported by the system. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

// ids = ['America/Adak', 'America/Anchorage', 'America/Bogota', 'America/Denver', 'America/Los_Angeles', 'America/Montevideo', 'America/Santiago', 'America/Sao_Paulo', 'Asia/Ashgabat', 'Asia/Hovd', 'Asia/Jerusalem', 'Asia/Magadan', 'Asia/Omsk', 'Asia/Shanghai', 'Asia/Tokyo', 'Asia/Yerevan', 'Atlantic/Cape_Verde', 'Australia/Lord_Howe', 'Europe/Dublin', 'Europe/London', 'Europe/Moscow', 'Pacific/Auckland', 'Pacific/Easter', 'Pacific/Pago-Pago']
let ids: Array<string> = i18n.TimeZone.getAvailableIDs();
```

## getAvailableZoneCityIDs

```TypeScript
static getAvailableZoneCityIDs(): Array<string>
```

Obtains the list of time zone city IDs supported by the system.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | List of time zone city IDs supported by the system. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

// cityIDs = ['Auckland', 'Magadan', 'Lord Howe Island', 'Tokyo', 'Shanghai', 'Hovd', 'Omsk', 'Ashgabat', 'Yerevan', 'Moscow', 'Tel Aviv', 'Dublin', 'London', 'Praia', 'Montevideo', 'Brasília', 'Santiago', 'Bogotá', 'Easter Island', 'Salt Lake City', 'Los Angeles', 'Anchorage', 'Adak', 'Pago Pago']
let cityIDs: Array<string> = i18n.TimeZone.getAvailableZoneCityIDs();
```

## getCityDisplayName

```TypeScript
static getCityDisplayName(cityID: string, locale: string): string
```

Obtains time zone city display name in the specified language.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cityID | string | Yes | Time zone city ID. |
| locale | string | Yes | [System locale](../../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Time zone city display name in the specified language. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let displayName: string = i18n.TimeZone.getCityDisplayName('Shanghai', 'zh-CN'); // displayName = 'Shanghai (China)'
```

## getDisplayName

```TypeScript
getDisplayName(locale?: string, isDST?: boolean): string
```

Obtains time zone display name in the specified language.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | string | No | [System locale](../../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region. The default value is the current system locale. |
| isDST | boolean | No | Whether DST information is displayed. The value **true** indicates that DST information is displayed, and the value **false** indicates the opposite. The default value is **false**. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Time zone display name in the specified language. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let timezone: i18n.TimeZone = i18n.getTimeZone('Asia/Shanghai');
let timezoneName: string = timezone.getDisplayName('zh-CN', false); // timezoneName = 'China Standard Time'
```

## getID

```TypeScript
getID(): string
```

Obtains the ID of the specified **TimeZone** object.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| string | Time zone ID corresponding to the **TimeZone** object. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let timezone: i18n.TimeZone = i18n.getTimeZone('Asia/Shanghai');
let timezoneID: string = timezone.getID(); // timezoneID = 'Asia/Shanghai'
```

## getOffset

```TypeScript
getOffset(date?: number): number
```

Obtains the offset of the specified time zone at the specified time.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| date | number | No | Specified time, in milliseconds. The default value is the system time. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Time zone offset, in milliseconds. When the DST is used, the time zone offset is the raw time zone offset plus the DST offset. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let timezone: i18n.TimeZone = i18n.getTimeZone('Asia/Shanghai');
let offset: number = timezone.getOffset(1234567890); // offset = 28800000
```

## getRawOffset

```TypeScript
getRawOffset(): number
```

Obtains the raw offset of the specified time zone.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| number | Raw offset of the time zone, in milliseconds. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let timezone: i18n.TimeZone = i18n.getTimeZone('Asia/Shanghai');
let offset: number = timezone.getRawOffset(); // offset = 28800000
```

## getTimezoneFromCity

```TypeScript
static getTimezoneFromCity(cityID: string): TimeZone
```

Creates a **TimeZone** object corresponding to the specified time zone city.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cityID | string | Yes | Time zone city ID. The value must be a time zone city ID supported by the system. |

**Return value:**

| Type | Description |
| --- | --- |
| [TimeZone](arkts-localization-i18n-timezone-c.md) | **TimeZone** object corresponding to the specified time zone city ID. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let timezone: i18n.TimeZone = i18n.TimeZone.getTimezoneFromCity('Shanghai');
```

## getTimezonesByLocation

```TypeScript
static getTimezonesByLocation(longitude: number, latitude: number): Array<TimeZone>
```

Creates an array of **TimeZone** objects corresponding to the specified location.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| longitude | number | Yes | Longitude. The value range is [-180, 179.9). A positive value is used for east longitude and a negative value is used for west longitude. |
| latitude | number | Yes | Latitude. The value range is [-90, 89.9). A positive value is used for north latitude and a negative value is used for south latitude. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TimeZone](arkts-localization-i18n-timezone-c.md)&gt; | **TimeZone** objects corresponding to the specified location. |

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
  let timezoneArray: Array<i18n.TimeZone> = i18n.TimeZone.getTimezonesByLocation(-118.1, 34.0);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call TimeZone.getTimezonesByLocation failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getZoneRules

```TypeScript
public getZoneRules(): ZoneRules
```

Obtains the time zone transition rules. For details about the time zone transition logic, see [DST Transition](../../../internationalization/i18n-dst-transition.md).

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| [ZoneRules](arkts-localization-i18n-zonerules-c.md) | Time zone transition rule, including the transition time and the offset before and after the transition. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let tzId: string = 'America/Tijuana';
let timeZone: i18n.TimeZone = i18n.getTimeZone(tzId);
let zoneRules: i18n.ZoneRules = timeZone.getZoneRules();
let date = new Date(2025, 4, 13);
let zoneOffsetTransition: i18n.ZoneOffsetTransition =
    zoneRules.nextTransition(date.getTime()); // Obtain the nextTransition object for time zone transition after May 13, 2025.
zoneOffsetTransition.getMilliseconds(); // Timestamp of the transition point: 1762074000000
zoneOffsetTransition.getOffsetAfter(); // Post-transition offset: -28800000
zoneOffsetTransition.getOffsetBefore(); // Pre-transition offset: -25200000
// Format the timestamp of the transition point.
let dateTimeFormat: Intl.DateTimeFormat = new Intl.DateTimeFormat('en-US', {
  timeZone: tzId,
  dateStyle: 'long',
  timeStyle: 'long',
  hour12: false
});
let dateFormat: string =
  dateTimeFormat.format(new Date(zoneOffsetTransition.getMilliseconds())); // November 2, 2025, 1:00:00 PST
```

## isDaylightSavingTime

```TypeScript
public isDaylightSavingTime(date: Date): boolean
```

Check if the given date use daylight saving time. The calculation will be based on the matched time zone rules.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| date | Date | Yes | Date and time. Note: The month starts from **0**, indicating January. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | true if the date use daylight saving time, and false otherwise. |

**Examples**

```TypeScript
let timezone: i18n.TimeZone = i18n.getTimeZone('Asia/Shanghai');
let isDST = timezone.isDaylightSavingTime(new Date(2026, 3, 15));
```

## setAppDefaultTimeZoneById

```TypeScript
static setAppDefaultTimeZoneById(zoneID: string): void
```

Sets the default time zone for the current app, the value will be used on the application's runtime lifecycle. When the date time formatting function is used, the default time zone ID of the app is used preferentially.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| zoneID | string | Yes | Time zone ID that set default for app. for example, "Asia/Shanghai".<br> Time zone ID supported by the system |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [8900001](../errorcode-i18n.md#8900001-parameter-verification-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let zoneID: string = 'Asia/Shanghai';
  i18n.TimeZone.setAppDefaultTimeZoneById(zoneID);
  console.info('setAppDefaultTimeZoneById success.');
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call TimeZone.setAppDefaultTimeZoneById failed, error code: ${err.code}, message: ${err.message}.`);
}
```
