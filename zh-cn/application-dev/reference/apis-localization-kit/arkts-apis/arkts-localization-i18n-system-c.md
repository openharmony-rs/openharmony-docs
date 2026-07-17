# System

提供系统属性相关的能力，包括语言地区名称翻译、支持的语言地区列表获取和系统语言地区获取等。

**起始版本：** 9

<!--Device-i18n-export class System--><!--Device-i18n-export class System-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getAppPreferredLanguage

```TypeScript
static getAppPreferredLanguage(): string
```

获取应用偏好语言。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getAppPreferredLanguage(): string--><!--Device-System-static getAppPreferredLanguage(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 应用偏好语言。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let appPreferredLanguage: string = i18n.System.getAppPreferredLanguage();

```

## getDisplayCountry

```TypeScript
static getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string
```

获取国家地区名称在指定语言下的翻译。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string--><!--Device-System-static getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| country | string | 是 | 国家地区，要求是[合法的国家地区码](../../../../internationalization/i18n-locale-culture.md#实现原理)。 |
| locale | string | 是 | [表示区域ID的字符串](../../../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组成。 |
| sentenceCase | boolean | 否 | true表示按照首字母大写的格式显示文本，false表示按照区域默认的大小写格式显示文本。默认值：true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 国家地区名称在指定语言下的翻译。 |

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

获取语言名称在指定语言下的翻译。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string--><!--Device-System-static getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| language | string | 是 | 语言，要求是[合法的语言ID](../../../../internationalization/i18n-locale-culture.md#实现原理)。 |
| locale | string | 是 | [表示区域ID的字符串](../../../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组成。 |
| sentenceCase | boolean | 否 | true表示按照首字母大写的格式显示文本，false表示按照区域默认的大小写格式显示文本。默认值：true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 语言名称在指定语言下的翻译。 |

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
  // 获取“中文”在英文下的翻译
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

获取系统设置的周起始日。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getFirstDayOfWeek(): WeekDay--><!--Device-System-static getFirstDayOfWeek(): WeekDay-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WeekDay](arkts-localization-i18n-weekday-e.md) | 周起始日。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let firstDayOfWeek: i18n.WeekDay = i18n.System.getFirstDayOfWeek();

```

## getFirstPreferredLanguage

```TypeScript
static getFirstPreferredLanguage(): string
```

获取系统偏好语言列表中的第一个语言。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getFirstPreferredLanguage(): string--><!--Device-System-static getFirstPreferredLanguage(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 系统偏好语言列表中的第一个语言。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let firstPreferredLanguage: string = i18n.System.getFirstPreferredLanguage();

```

## getPreferredLanguageList

```TypeScript
static getPreferredLanguageList(): Array<string>
```

获取系统偏好语言列表。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getPreferredLanguageList(): Array<string>--><!--Device-System-static getPreferredLanguageList(): Array<string>-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 系统偏好语言列表。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let preferredLanguageList: Array<string> = i18n.System.getPreferredLanguageList();

```

## getSimplifiedLanguage

```TypeScript
static getSimplifiedLanguage(language?: string): string
```

获取语言的简化表示。例如：'en-Latn-US'的简化表示为'en'，'en-Latn-GB'的简化表示为'en-GB'。

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getSimplifiedLanguage(language?: string): string--><!--Device-System-static getSimplifiedLanguage(language?: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| language | string | 否 | [合法的语言ID](../../../../internationalization/i18n-locale-culture.md#实现原理)。默认值：系统语言。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 不传入language时，会根据系统语言和地区判断是否存在系统支持的方言，若存在则返回方言的简化表示；若不存在，则返回系统语言的简化表示。<br>传入language时，返回language的简化表示。 |

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
  // simplifiedLanguage = 'zh'
  let simplifiedLanguage: string = i18n.System.getSimplifiedLanguage('zh-Hans-CN');
  // 获取当前系统语言的简化表示
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

获取输入语言下系统支持的国家地区列表。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getSystemCountries(language: string): Array<string>--><!--Device-System-static getSystemCountries(language: string): Array<string>-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| language | string | 是 | [合法的语言ID](../../../../internationalization/i18n-locale-culture.md#实现原理)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | language参数指定的语言下，系统支持的国家/地区列表。 |

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

获取系统当前设置的语言。若要监听系统语言变化，可以监听[公共事件](../../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_locale_changed)OHOS::EventFwk::CommonEventSupport::COMMON_EVENT_LOCALE_CHANGED，具体可参考[系统语言与区域](../../../../internationalization/i18n-system-language-region.md#开发步骤)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-System-static getSystemLanguage(): string--><!--Device-System-static getSystemLanguage(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示语言ID的字符串。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let systemLanguage: string = i18n.System.getSystemLanguage(); // 如果系统语言为简体中文，systemLanguage = 'zh-Hans'

```

## getSystemLanguages

```TypeScript
static getSystemLanguages(): Array<string>
```

获取系统支持的语言列表。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getSystemLanguages(): Array<string>--><!--Device-System-static getSystemLanguages(): Array<string>-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 系统支持的语言列表。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

// systemLanguages = [ 'ug', 'bo', 'zh-Hant', 'en-Latn-US', 'zh-Hans' ]
let systemLanguages: Array<string> = i18n.System.getSystemLanguages();

```

## getSystemLocale

```TypeScript
static getSystemLocale(): string
```

> [System.getSystemLocaleInstance](arkts-localization-i18n-system-c.md#getsystemlocaleinstance-1)代替。  
> 获取系统当前设置的区域。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** [getSystemLocaleInstance](arkts-localization-i18n-system-c.md#getsystemlocaleinstance-1)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getSystemLocale(): string--><!--Device-System-static getSystemLocale(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示区域ID的字符串。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let systemLocale: string = i18n.System.getSystemLocale(); // 如果系统语言为简体中文、地区为中国，systemLocale = 'zh-Hans-CN'

```

## getSystemLocaleInstance

```TypeScript
static getSystemLocaleInstance(): Intl.Locale
```

获取系统当前设置的区域对象。若要监听系统区域变化，可以监听[公共事件](../../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_locale_changed)OHOS::EventFwk::CommonEventSupport::COMMON_EVENT_LOCALE_CHANGED，具体可参考[系统语言与区域](../../../../internationalization/i18n-system-language-region.md#开发步骤)。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getSystemLocaleInstance(): Intl.Locale--><!--Device-System-static getSystemLocaleInstance(): Intl.Locale-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Intl.Locale | the locale object currently used by the system. |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let systemLocale: Intl.Locale = i18n.System.getSystemLocaleInstance();

```

## getSystemRegion

```TypeScript
static getSystemRegion(): string
```

获取系统当前设置的国家地区。若要监听系统地区变化，可以监听[公共事件](../../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_locale_changed)OHOS::EventFwk::CommonEventSupport::COMMON_EVENT_LOCALE_CHANGED，具体可参考[系统语言与区域](../../../../internationalization/i18n-system-language-region.md#开发步骤)。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getSystemRegion(): string--><!--Device-System-static getSystemRegion(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示国家地区ID的字符串。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let systemRegion: string = i18n.System.getSystemRegion(); // 如果系统地区为中国，systemRegion = 'CN'

```

## getTemperatureName

```TypeScript
static getTemperatureName(type: TemperatureType): string
```

获取温度单位的名称。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getTemperatureName(type: TemperatureType): string--><!--Device-System-static getTemperatureName(type: TemperatureType): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [TemperatureType](arkts-localization-i18n-temperaturetype-e.md) | 是 | 温度单位。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回温度单位的名称，包括celsius，fahrenheit，kelvin。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [890001](../errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

**示例：**

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

获取系统设置的温度单位。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getTemperatureType(): TemperatureType--><!--Device-System-static getTemperatureType(): TemperatureType-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TemperatureType](arkts-localization-i18n-temperaturetype-e.md) | 温度单位。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let temperatureType: i18n.TemperatureType = i18n.System.getTemperatureType();

```

## getUsingLocalDigit

```TypeScript
static getUsingLocalDigit(): boolean
```

判断系统是否使用本地数字。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getUsingLocalDigit(): boolean--><!--Device-System-static getUsingLocalDigit(): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示系统当前使用本地数字，false表示系统当前不使用本地数字。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let usingLocalDigit: boolean = i18n.System.getUsingLocalDigit();

```

## is24HourClock

```TypeScript
static is24HourClock(): boolean
```

判断系统时制是否为24小时制。若要监听系统时制变化，可以监听[公共事件](../../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_time_changed)OHOS::EventFwk::CommonEventSupport::COMMON_EVENT_TIME_CHANGED，具体可参考[用户偏好](../../../../internationalization/i18n-user-preferences.md#开发步骤)。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-System-static is24HourClock(): boolean--><!--Device-System-static is24HourClock(): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示系统时制为24小时制，false表示系统时制为12小时制。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let is24HourClock: boolean = i18n.System.is24HourClock(); // 如果系统时制是24小时制，is24HourClock = true

```

## isSuggested

```TypeScript
static isSuggested(language: string, region?: string): boolean
```

判断语言是否是地区的推荐语言。用于根据地区推荐语言或根据语言推荐地区。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-System-static isSuggested(language: string, region?: string): boolean--><!--Device-System-static isSuggested(language: string, region?: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| language | string | 是 | [合法的语言ID](../../../../internationalization/i18n-locale-culture.md#实现原理)，例如zh。 |
| region | string | 否 | [合法的国家地区码](../../../../internationalization/i18n-locale-culture.md#实现原理)，例如CN。<br>默认值：SIM卡国家地区。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示语言是地区的推荐语言，false表示语言不是地区的推荐语言。 |

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
  let isSuggestedCountry: boolean = i18n.System.isSuggested('zh', 'CN'); // isSuggestedCountry = true
  isSuggestedCountry = i18n.System.isSuggested('en'); // 结果和系统当前地区相关
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.isSuggested failed, error code: ${err.code}, message: ${err.message}.`);
}

```

## setAppPreferredLanguage

```TypeScript
static setAppPreferredLanguage(language: string): void
```

设置应用偏好语言。设置后，应用将优先加载应用偏好语言对应的资源。设置偏好语言为'default'后，应用语言将跟随系统语言，应用冷启动生效。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-System-static setAppPreferredLanguage(language: string): void--><!--Device-System-static setAppPreferredLanguage(language: string): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| language | string | 是 | [合法的语言ID](../../../../internationalization/i18n-locale-culture.md#实现原理)或'default'。 |

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
  i18n.System.setAppPreferredLanguage('zh');
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call System.setAppPreferredLanguage failed, error code: ${err.code}, message: ${err.message}.`);
}

```

