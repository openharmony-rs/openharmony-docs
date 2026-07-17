# TimeZone

提供时区相关的能力，包括时区名称翻译、偏移量获取和跳变规则获取等。

**起始版本：** 7

<!--Device-i18n-export class TimeZone--><!--Device-i18n-export class TimeZone-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getAppDefaultTimeZone

```TypeScript
static getAppDefaultTimeZone(): TimeZone
```

获取应用使用的默认时区对象。若调用[setAppDefaultTimeZoneById](arkts-localization-i18n-timezone-c.md#setappdefaulttimezonebyid-1)设置了默认时区，则返回设置的默认时区对象；否则，返回系统时区对象。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TimeZone-static getAppDefaultTimeZone(): TimeZone--><!--Device-TimeZone-static getAppDefaultTimeZone(): TimeZone-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TimeZone](arkts-localization-i18n-timezone-c.md) | 应用使用的默认时区对象。 |

**示例：**

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

获取系统支持的时区ID列表。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimeZone-static getAvailableIDs(): Array<string>--><!--Device-TimeZone-static getAvailableIDs(): Array<string>-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 系统支持的时区ID列表。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

// ids = ['America/Adak', 'America/Anchorage', 'America/Bogota', 'America/Denver', 'America/Los_Angeles', 'America/Montevideo', 'America/Santiago', 'America/Sao_Paulo', 'Asia/Ashgabat', 'Asia/Hovd', 'Asia/Jerusalem', 'Asia/Magadan', 'Asia/Omsk', 'Asia/Shanghai', 'Asia/Tokyo', 'Asia/Yerevan', 'Atlantic/Cape_Verde', 'Australia/Lord_Howe', 'Europe/Dublin', 'Europe/London', 'Europe/Moscow', 'Pacific/Auckland', 'Pacific/Easter', 'Pacific/Pago-Pago']
let ids: Array<string> = i18n.TimeZone.getAvailableIDs();

```

## getAvailableZoneCityIDs

```TypeScript
static getAvailableZoneCityIDs(): Array<string>
```

获取系统支持的时区城市ID列表。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimeZone-static getAvailableZoneCityIDs(): Array<string>--><!--Device-TimeZone-static getAvailableZoneCityIDs(): Array<string>-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 系统支持的时区城市ID列表。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

// cityIDs = ['Auckland', 'Magadan', 'Lord Howe Island', 'Tokyo', 'Shanghai', 'Hovd', 'Omsk', 'Ashgabat', 'Yerevan', 'Moscow', 'Tel Aviv', 'Dublin', 'London', 'Praia', 'Montevideo', 'Brasília', 'Santiago', 'Bogotá', 'Easter Island', 'Salt Lake City', 'Los Angeles', 'Anchorage', 'Adak', 'Pago Pago']
let cityIDs: Array<string> = i18n.TimeZone.getAvailableZoneCityIDs();

```

## getCityDisplayName

```TypeScript
static getCityDisplayName(cityID: string, locale: string): string
```

获取时区城市名称在指定语言下的翻译。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimeZone-static getCityDisplayName(cityID: string, locale: string): string--><!--Device-TimeZone-static getCityDisplayName(cityID: string, locale: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cityID | string | 是 | 时区城市ID。 |
| locale | string | 是 | [表示区域ID的字符串](../../../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 时区城市名称在指定语言下的翻译。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let displayName: string = i18n.TimeZone.getCityDisplayName('Shanghai', 'zh-CN'); // displayName = '上海 (中国)'

```

## getDisplayName

```TypeScript
getDisplayName(locale?: string, isDST?: boolean): string
```

获取时区对象名称在指定语言下的翻译。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimeZone-getDisplayName(locale?: string, isDST?: boolean): string--><!--Device-TimeZone-getDisplayName(locale?: string, isDST?: boolean): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string | 否 | [表示区域ID的字符串](../../../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组成。默认值：系统当前区域ID。 |
| isDST | boolean | 否 | true表示显示夏令时信息，false表示不显示夏令时信息。默认值：false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 时区对象名称在指定语言下的翻译。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let timezone: i18n.TimeZone = i18n.getTimeZone('Asia/Shanghai');
let timezoneName: string = timezone.getDisplayName('zh-CN', false); // timezoneName = '中国标准时间'

```

## getID

```TypeScript
getID(): string
```

获取时区对象的ID。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimeZone-getID(): string--><!--Device-TimeZone-getID(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 时区对象对应的时区ID。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let timezone: i18n.TimeZone = i18n.getTimeZone('Asia/Shanghai');
let timezoneID: string = timezone.getID(); // timezoneID = 'Asia/Shanghai'

```

## getOffset

```TypeScript
getOffset(date?: number): number
```

获取某一时刻时区对象所表示时区的偏移量。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimeZone-getOffset(date?: double): int--><!--Device-TimeZone-getOffset(date?: double): int-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | number | 否 | 待计算时区偏移量的时刻，单位为毫秒（ms）。默认值：系统时间。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 时区的偏移量，单位为毫秒（ms）。当处于夏令时时，时区偏移量为时区原始偏移量加夏令时偏移量。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let timezone: i18n.TimeZone = i18n.getTimeZone('Asia/Shanghai');
let offset: number = timezone.getOffset(1234567890); // offset = 28800000

```

## getRawOffset

```TypeScript
getRawOffset(): number
```

获取时区对象所表示时区的原始偏移量。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimeZone-getRawOffset(): int--><!--Device-TimeZone-getRawOffset(): int-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 时区的原始偏移量，单位为毫秒（ms）。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let timezone: i18n.TimeZone = i18n.getTimeZone('Asia/Shanghai');
let offset: number = timezone.getRawOffset(); // offset = 28800000

```

## getTimezoneFromCity

```TypeScript
static getTimezoneFromCity(cityID: string): TimeZone
```

创建对应时区城市的时区对象。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimeZone-static getTimezoneFromCity(cityID: string): TimeZone--><!--Device-TimeZone-static getTimezoneFromCity(cityID: string): TimeZone-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cityID | string | 是 | 时区城市ID，要求是系统支持的时区城市ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TimeZone](arkts-localization-i18n-timezone-c.md) | 时区城市对应的时区对象。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let timezone: i18n.TimeZone = i18n.TimeZone.getTimezoneFromCity('Shanghai');

```

## getTimezonesByLocation

```TypeScript
static getTimezonesByLocation(longitude: number, latitude: number): Array<TimeZone>
```

创建地理位置对应的时区对象数组。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimeZone-static getTimezonesByLocation(longitude: double, latitude: double): Array<TimeZone>--><!--Device-TimeZone-static getTimezonesByLocation(longitude: double, latitude: double): Array<TimeZone>-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| longitude | number | 是 | 经度，范围[-180, 179.9)，东经取正值，西经取负值。 |
| latitude | number | 是 | 纬度，范围[-90, 89.9)，北纬取正值，南纬取负值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<TimeZone> | 时区对象数组，数组中对象对应的时区为该地理位置推荐的时区。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

**示例：**

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

获取时区跳变规则，时区的跳变逻辑参考[夏令时跳变](../../../../internationalization/i18n-dst-transition.md)。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TimeZone-public getZoneRules(): ZoneRules--><!--Device-TimeZone-public getZoneRules(): ZoneRules-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ZoneRules](arkts-localization-i18n-zonerules-c.md) | 时区跳变规则，包含跳变的时间点、跳变前后的偏移量信息。 |

## isDaylightSavingTime

```TypeScript
public isDaylightSavingTime(date: Date): boolean
```

判断指定的时间日期是否处于夏令时。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TimeZone-public isDaylightSavingTime(date: Date): boolean--><!--Device-TimeZone-public isDaylightSavingTime(date: Date): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 是 | 时间日期。<br>**说明：**<br>月份从0开始计数，0表示一月。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否处于夏令时。true表示处于夏令时，false表示不处于夏令时。 |

## setAppDefaultTimeZoneById

```TypeScript
static setAppDefaultTimeZoneById(zoneID: string): void
```

设置当前应用的默认时区，在应用运行时生命周期内有效。

> **说明：**  
>  
> 进行日期时间格式化时，若未指定时区，会优先使用应用设置的默认时区。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TimeZone-static setAppDefaultTimeZoneById(zoneID: string): void--><!--Device-TimeZone-static setAppDefaultTimeZoneById(zoneID: string): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| zoneID | string | 是 | 应用设置默认的时区ID，如："Asia/Shanghai"。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8900001](../errorcode-i18n.md#8900001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

**示例：**

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

