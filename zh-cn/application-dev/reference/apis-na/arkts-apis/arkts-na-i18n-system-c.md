# System

提供系统属性相关的能力，包括语言地区名称翻译、支持的语言地区列表获取和系统语言地区获取等。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-i18n-export class System--><!--Device-i18n-export class System-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
```

## getAppPreferredLanguage

```TypeScript
static getAppPreferredLanguage(): string
```

获取应用偏好语言。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getAppPreferredLanguage(): string--><!--Device-System-static getAppPreferredLanguage(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 应用偏好语言。 |

## getDisplayCountry

```TypeScript
static getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string
```

获取国家地区名称在指定语言下的翻译。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string--><!--Device-System-static getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| country | string | 是 | 国家地区，要求是[合法的国家地区码](../../../internationalization/i18n-locale-culture.md#实现原理)。 |
| locale | string | 是 | [表示区域ID的字符串](../../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组 成。 |
| sentenceCase | boolean | 否 | true表示按照首字母大写的格式显示文本，false表示按照区域默认的大小写格式显示文本。默认值：true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 国家地区名称在指定语言下的翻译。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## getDisplayLanguage

```TypeScript
static getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string
```

获取语言名称在指定语言下的翻译。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string--><!--Device-System-static getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| language | string | 是 | 语言，要求是[合法的语言ID](../../../internationalization/i18n-locale-culture.md#实现原理)。 |
| locale | string | 是 | [表示区域ID的字符串](../../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组 成。 |
| sentenceCase | boolean | 否 | true表示按照首字母大写的格式显示文本，false表示按照区域默认的大小写格式显示文本。默认值：true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 语言名称在指定语言下的翻译。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## getFirstDayOfWeek

```TypeScript
static getFirstDayOfWeek(): WeekDay
```

获取系统设置的周起始日。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getFirstDayOfWeek(): WeekDay--><!--Device-System-static getFirstDayOfWeek(): WeekDay-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WeekDay](arkts-na-i18n-weekday-e.md) | 周起始日。 |

## getFirstPreferredLanguage

```TypeScript
static getFirstPreferredLanguage(): string
```

获取系统偏好语言列表中的第一个语言。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getFirstPreferredLanguage(): string--><!--Device-System-static getFirstPreferredLanguage(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 系统偏好语言列表中的第一个语言。 |

## getPreferredLanguageList

```TypeScript
static getPreferredLanguageList(): Array<string>
```

获取系统偏好语言列表。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getPreferredLanguageList(): Array<string>--><!--Device-System-static getPreferredLanguageList(): Array<string>-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 系统偏好语言列表。 |

## getSimplifiedLanguage

```TypeScript
static getSimplifiedLanguage(language?: string): string
```

获取语言的简化表示。例如：'en-Latn-US'的简化表示为'en'，'en-Latn-GB'的简化表示为'en-GB'。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getSimplifiedLanguage(language?: string): string--><!--Device-System-static getSimplifiedLanguage(language?: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| language | string | 否 | [合法的语言ID](../../../internationalization/i18n-locale-culture.md#实现原理)。默认值：系统语言。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 不传入language时，会根据系统语言和地区判断是否存在系统支持的方言，若存在则返回方言的简化表示；若不存在，则返回系统语言的简化表示。 <br>传入language时，返回language的简化表示。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## getSystemCountries

```TypeScript
static getSystemCountries(language: string): Array<string>
```

获取输入语言下系统支持的国家地区列表。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getSystemCountries(language: string): Array<string>--><!--Device-System-static getSystemCountries(language: string): Array<string>-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| language | string | 是 | [合法的语言ID](../../../internationalization/i18n-locale-culture.md#实现原理)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | language参数指定的语言下，系统支持的国家/地区列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## getSystemLanguage

```TypeScript
static getSystemLanguage(): string
```

获取系统当前设置的语言。若要监听系统语言变化，可以监听 [公共事件](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_locale_changed) OHOS::EventFwk::CommonEventSupport::COMMON_EVENT_LOCALE_CHANGED，具体可参考 [系统语言与区域](../../../internationalization/i18n-system-language-region.md#开发步骤)。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-System-static getSystemLanguage(): string--><!--Device-System-static getSystemLanguage(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示语言ID的字符串。 |

## getSystemLanguages

```TypeScript
static getSystemLanguages(): Array<string>
```

获取系统支持的语言列表。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getSystemLanguages(): Array<string>--><!--Device-System-static getSystemLanguages(): Array<string>-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 系统支持的语言列表。 |

## getSystemLocaleInstance

```TypeScript
static getSystemLocaleInstance(): Intl.Locale
```

获取系统当前设置的区域对象。若要监听系统区域变化，可以监听 [公共事件](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_locale_changed) OHOS::EventFwk::CommonEventSupport::COMMON_EVENT_LOCALE_CHANGED，具体可参考 [系统语言与区域](../../../internationalization/i18n-system-language-region.md#开发步骤)。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getSystemLocaleInstance(): Intl.Locale--><!--Device-System-static getSystemLocaleInstance(): Intl.Locale-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Intl.Locale | the locale object currently used by the system. |

## getSystemRegion

```TypeScript
static getSystemRegion(): string
```

获取系统当前设置的国家地区。若要监听系统地区变化，可以监听 [公共事件](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_locale_changed) OHOS::EventFwk::CommonEventSupport::COMMON_EVENT_LOCALE_CHANGED，具体可参考 [系统语言与区域](../../../internationalization/i18n-system-language-region.md#开发步骤)。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getSystemRegion(): string--><!--Device-System-static getSystemRegion(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示国家地区ID的字符串。 |

## getTemperatureName

```TypeScript
static getTemperatureName(type: TemperatureType): string
```

获取温度单位的名称。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getTemperatureName(type: TemperatureType): string--><!--Device-System-static getTemperatureName(type: TemperatureType): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [TemperatureType](arkts-na-i18n-temperaturetype-e.md) | 是 | 温度单位。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回温度单位的名称，包括celsius，fahrenheit，kelvin。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## getTemperatureType

```TypeScript
static getTemperatureType(): TemperatureType
```

获取系统设置的温度单位。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getTemperatureType(): TemperatureType--><!--Device-System-static getTemperatureType(): TemperatureType-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TemperatureType](arkts-na-i18n-temperaturetype-e.md) | 温度单位。 |

## getUsingLocalDigit

```TypeScript
static getUsingLocalDigit(): boolean
```

判断系统是否使用本地数字。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-System-static getUsingLocalDigit(): boolean--><!--Device-System-static getUsingLocalDigit(): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示系统当前使用本地数字，false表示系统当前不使用本地数字。 |

## is24HourClock

```TypeScript
static is24HourClock(): boolean
```

判断系统时制是否为24小时制。若要监听系统时制变化，可以监听 [公共事件](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_time_changed) OHOS::EventFwk::CommonEventSupport::COMMON_EVENT_TIME_CHANGED，具体可参考 [用户偏好](../../../internationalization/i18n-user-preferences.md#开发步骤)。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-System-static is24HourClock(): boolean--><!--Device-System-static is24HourClock(): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示系统时制为24小时制，false表示系统时制为12小时制。 |

## isSuggested

```TypeScript
static isSuggested(language: string, region?: string): boolean
```

判断语言是否是地区的推荐语言。用于根据地区推荐语言或根据语言推荐地区。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-System-static isSuggested(language: string, region?: string): boolean--><!--Device-System-static isSuggested(language: string, region?: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| language | string | 是 | [合法的语言ID](../../../internationalization/i18n-locale-culture.md#实现原理)，例如zh。 |
| region | string | 否 | [合法的国家地区码](../../../internationalization/i18n-locale-culture.md#实现原理)，例如CN。 <br>默认值：SIM卡国家地区。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示语言是地区的推荐语言，false表示语言不是地区的推荐语言。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## setAppPreferredLanguage

```TypeScript
static setAppPreferredLanguage(language: string): void
```

设置应用偏好语言。设置后，应用将优先加载应用偏好语言对应的资源。设置偏好语言为'default'后，应用语言将跟随系统语言，应用冷启动生效。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-System-static setAppPreferredLanguage(language: string): void--><!--Device-System-static setAppPreferredLanguage(language: string): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| language | string | 是 | [合法的语言ID](../../../internationalization/i18n-locale-culture.md#实现原理)或'default'。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

