# System

提供系统属性相关的能力，包括语言地区名称翻译、支持的语言地区列表获取和系统语言地区获取等。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-i18n-export class System--><!--Device-i18n-export class System-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
```

## addPreferredLanguage

```TypeScript
static addPreferredLanguage(language: string, index?: int): void
```

在系统偏好语言列表的指定位置添加偏好语言。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-System-static addPreferredLanguage(language: string, index?: int): void--><!--Device-System-static addPreferredLanguage(language: string, index?: int): void-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| language | string | 是 | 待添加的偏好语言，要求是合法的语言ID。 |
| index | int | 否 | 偏好语言的添加位置。 <br>取值范围：[0, 系统偏好语言列表长度]，小于0时取值为0，大于系统偏好语言列表长度时取值为系统偏好语言列表长度。 <br>默认值：系统偏好语言列表长度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 26.0.0+ |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## getSystemCollations

```TypeScript
static getSystemCollations(): Map<string, string>
```

获取系统支持的排序方式及名称。如系统语言为英文时，可以支持大写在前或小写在前的排序方式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-System-static getSystemCollations(): Map<string, string>--><!--Device-System-static getSystemCollations(): Map<string, string>-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Map&lt;string, string&gt; | 系统支持的排序方式及名称。其中Map的key为表示排序方式的字符串，value为表示排序方式对应名称的字符串。 支持的范围和系统语言相关。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## getSystemMeasurements

```TypeScript
static getSystemMeasurements(): Map<string, string>
```

获取系统支持的度量衡及其名称。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-System-static getSystemMeasurements(): Map<string, string>--><!--Device-System-static getSystemMeasurements(): Map<string, string>-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Map&lt;string, string&gt; | 系统支持的度量衡及其名称。其中Map的key表示度量衡的标识，value表示度量衡的名称。支持的度量衡如下： - metric：公制。 - uksystem：英制。 - ussystem：美制。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## getSystemNumberPatterns

```TypeScript
static getSystemNumberPatterns(): Map<string, string>
```

获取系统支持的数字格式及示例。数字格式指数字中的千分符和小数分隔符的格式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-System-static getSystemNumberPatterns(): Map<string, string>--><!--Device-System-static getSystemNumberPatterns(): Map<string, string>-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Map&lt;string, string&gt; | 系统支持的数字格式及示例。 其中Map的key表示数字格式，是千分符和小数分隔符的unicode编码，value表示数字格式对应的示例。支持的范围和系统语言地区相关。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## getSystemNumberingSystems

```TypeScript
static getSystemNumberingSystems(): Map<string, string>
```

获取系统支持的数字系统及示例。示例为数字0~9在对应数字系统下的显示。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-System-static getSystemNumberingSystems(): Map<string, string>--><!--Device-System-static getSystemNumberingSystems(): Map<string, string>-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Map&lt;string, string&gt; | 系统支持的数字系统及示例。其中Map的key为表示数字系统的字符串，value为表示数字系统对应的示例。 支持的范围和系统语言相关。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## getSystemNumericalDatePatterns

```TypeScript
static getSystemNumericalDatePatterns(): Map<string, string>
```

获取系统支持的数字日期格式及其示例。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-System-static getSystemNumericalDatePatterns(): Map<string, string>--><!--Device-System-static getSystemNumericalDatePatterns(): Map<string, string>-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Map&lt;string, string&gt; | 获取系统支持的数字日期格式及其示例。 其中Map的key表示数字日期格式，形如dd/MM/y；value表示数字日期示例，形如18/07/2025。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## getUsingCollation

```TypeScript
static getUsingCollation(): string
```

获取系统当前使用的排序方式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-System-static getUsingCollation(): string--><!--Device-System-static getUsingCollation(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 系统当前使用的排序方式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## getUsingMeasurement

```TypeScript
static getUsingMeasurement(): string
```

获取系统当前使用的度量衡。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-System-static getUsingMeasurement(): string--><!--Device-System-static getUsingMeasurement(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 系统当前使用的度量衡，取值及对应含义如下： - metric：公制。 - uksystem：英制。 - ussystem：美制。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## getUsingNumberPattern

```TypeScript
static getUsingNumberPattern(): string
```

获取系统当前使用的数字格式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-System-static getUsingNumberPattern(): string--><!--Device-System-static getUsingNumberPattern(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 系统当前使用的数字格式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## getUsingNumberingSystem

```TypeScript
static getUsingNumberingSystem(): string
```

获取系统当前使用的数字系统。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-System-static getUsingNumberingSystem(): string--><!--Device-System-static getUsingNumberingSystem(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 系统支持的数字系统。支持的范围可以通过getSystemNumberingSystems获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## getUsingNumericalDatePattern

```TypeScript
static getUsingNumericalDatePattern(): string
```

获取系统当前使用的数字日期格式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-System-static getUsingNumericalDatePattern(): string--><!--Device-System-static getUsingNumericalDatePattern(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 系统当前使用的数字日期格式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## removePreferredLanguage

```TypeScript
static removePreferredLanguage(index: int): void
```

从系统偏好语言列表中移除指定位置的偏好语言。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-System-static removePreferredLanguage(index: int): void--><!--Device-System-static removePreferredLanguage(index: int): void-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待删除偏好语言在系统偏好语言列表中的位置。 <br>取值范围：[0, 系统偏好语言列表长度]，小于0时取值为0，大于系统偏好语言列表长度时取值为系统偏好语言列表长度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 26.0.0+ |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed.<br>**适用版本：** 23 - 24 |

## set24HourClock

```TypeScript
static set24HourClock(option: boolean): void
```

设置系统时制是否为24小时制。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-System-static set24HourClock(option: boolean): void--><!--Device-System-static set24HourClock(option: boolean): void-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | boolean | 是 | true表示设置系统时制为24小时制，false表示设置系统时制为12小时制。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 26.0.0+ |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed.<br>**适用版本：** 23 - 24 |

## setFirstDayOfWeek

```TypeScript
static setFirstDayOfWeek(type: WeekDay): void
```

设置系统的周起始日。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-System-static setFirstDayOfWeek(type: WeekDay): void--><!--Device-System-static setFirstDayOfWeek(type: WeekDay): void-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [WeekDay](arkts-na-i18n-weekday-e.md) | 是 | 周期起始日。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## setSystemCollation

```TypeScript
static setSystemCollation(identifier: string): void
```

设置系统的排序方式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-System-static setSystemCollation(identifier: string): void--><!--Device-System-static setSystemCollation(identifier: string): void-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| identifier | string | 是 | 系统支持的排序方式。支持的范围可以通过getSystemCollations获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8900001](../../apis-localization-kit/errorcode-i18n.md#8900001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## setSystemLanguage

```TypeScript
static setSystemLanguage(language: string): void
```

设置系统语言。若要监听系统语言变化，可以监听 [公共事件](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_locale_changed) OHOS::EventFwk::CommonEventSupport::COMMON_EVENT_LOCALE_CHANGED，具体可参考 [系统语言与区域](../../../internationalization/i18n-system-language-region.md#开发步骤)。 <br>**说明：** <br>可以通过i18n.System.getSystemLanguage()接口获取系统语言。 <br>从API version 21开始，也可以使用[param工具](../../../tools/param-tool.md#获取系统参数的值)的“param get persist.global.language”命令获取系统语言。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-System-static setSystemLanguage(language: string): void--><!--Device-System-static setSystemLanguage(language: string): void-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| language | string | 是 | [合法的语言ID](../../../internationalization/i18n-locale-culture.md#实现原理)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 26.0.0+ |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## setSystemMeasurement

```TypeScript
static setSystemMeasurement(identifier: string): void
```

设置系统的度量衡。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-System-static setSystemMeasurement(identifier: string): void--><!--Device-System-static setSystemMeasurement(identifier: string): void-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| identifier | string | 是 | 系统支持的度量衡。支持的范围可以通过getSystemMeasurements获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8900001](../../apis-localization-kit/errorcode-i18n.md#8900001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## setSystemNumberPattern

```TypeScript
static setSystemNumberPattern(pattern: string): void
```

设置系统的数字格式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-System-static setSystemNumberPattern(pattern: string): void--><!--Device-System-static setSystemNumberPattern(pattern: string): void-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pattern | string | 是 | 系统支持的数字格式。支持的范围可以通过getSystemNumberPatterns获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8900001](../../apis-localization-kit/errorcode-i18n.md#8900001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## setSystemNumberingSystem

```TypeScript
static setSystemNumberingSystem(identifier: string): void
```

设置系统的数字系统。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-System-static setSystemNumberingSystem(identifier: string): void--><!--Device-System-static setSystemNumberingSystem(identifier: string): void-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| identifier | string | 是 | 系统支持的数字系统。支持的范围可以通过getSystemNumberingSystems获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8900001](../../apis-localization-kit/errorcode-i18n.md#8900001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## setSystemNumericalDatePattern

```TypeScript
static setSystemNumericalDatePattern(identifier : string): void
```

设置系统的数字日期格式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-System-static setSystemNumericalDatePattern(identifier : string): void--><!--Device-System-static setSystemNumericalDatePattern(identifier : string): void-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| identifier | string | 是 | 系统支持的数字日期格式。支持的范围可以通过getSystemNumericalDatePatterns获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8900001](../../apis-localization-kit/errorcode-i18n.md#8900001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## setSystemRegion

```TypeScript
static setSystemRegion(region: string): void
```

设置系统地区。若要监听系统地区变化，可以监听 [公共事件](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_locale_changed) OHOS::EventFwk::CommonEventSupport::COMMON_EVENT_LOCALE_CHANGED，具体可参考 [系统语言与区域](../../../internationalization/i18n-system-language-region.md#开发步骤)。 <br>**说明：** <br>可以通过i18n.System.getSystemRegion()接口获取系统地区。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-System-static setSystemRegion(region: string): void--><!--Device-System-static setSystemRegion(region: string): void-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | string | 是 | [合法的地区ID](../../../internationalization/i18n-locale-culture.md#实现原理)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 26.0.0+ |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## setTemperatureType

```TypeScript
static setTemperatureType(type: TemperatureType): void
```

设置系统的温度单位。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-System-static setTemperatureType(type: TemperatureType): void--><!--Device-System-static setTemperatureType(type: TemperatureType): void-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [TemperatureType](arkts-na-i18n-temperaturetype-e.md) | 是 | 温度单位。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## setUsingLocalDigit

```TypeScript
static setUsingLocalDigit(flag: boolean): void
```

设置系统是否使用本地数字。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-System-static setUsingLocalDigit(flag: boolean): void--><!--Device-System-static setUsingLocalDigit(flag: boolean): void-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flag | boolean | 是 | true表示打开本地数字开关，false表示关闭本地数字开关。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 26.0.0+ |

