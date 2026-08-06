# SystemLocaleManager（系统接口）

提供语言、地区和时区信息排序的能力。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-i18n-export class SystemLocaleManager--><!--Device-i18n-export class SystemLocaleManager-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## constructor

```TypeScript
constructor()
```

创建SystemLocaleManager对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SystemLocaleManager-constructor()--><!--Device-SystemLocaleManager-constructor()-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 26.0.0+ |

## getLanguageInfoArray

```TypeScript
getLanguageInfoArray(languages: Array<string>, options?: SortOptions): Array<LocaleItem>
```

获取排序后的语言信息列表。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SystemLocaleManager-getLanguageInfoArray(languages: Array<string>, options?: SortOptions): Array<LocaleItem>--><!--Device-SystemLocaleManager-getLanguageInfoArray(languages: Array<string>, options?: SortOptions): Array<LocaleItem>-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| languages | Array&lt;string&gt; | 是 | 待排序的语言列表，要求是合法的语言ID。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 语言排序选项。默认值：所有属性都取默认值时的配置项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;LocaleItem&gt; | 排序后的语言信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## getRegionInfoArray

```TypeScript
getRegionInfoArray(regions: Array<string>, options?: SortOptions): Array<LocaleItem>
```

获取排序后的国家或地区信息列表。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SystemLocaleManager-getRegionInfoArray(regions: Array<string>, options?: SortOptions): Array<LocaleItem>--><!--Device-SystemLocaleManager-getRegionInfoArray(regions: Array<string>, options?: SortOptions): Array<LocaleItem>-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| regions | Array&lt;string&gt; | 是 | 待排序的国家或地区列表，要求是合法的国家或地区ID。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 国家或地区排序选项。区域ID的默认值为系统当前区域ID，isUseLocalName的默认值为false，isSuggestedFirst的默认值为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;LocaleItem&gt; | 排序后的国家或地区信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## getTimeZoneCityItemArray

```TypeScript
static getTimeZoneCityItemArray(): Array<TimeZoneCityItem>
```

获取排序后的时区城市组合信息列表。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SystemLocaleManager-static getTimeZoneCityItemArray(): Array<TimeZoneCityItem>--><!--Device-SystemLocaleManager-static getTimeZoneCityItemArray(): Array<TimeZoneCityItem>-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;TimeZoneCityItem&gt; | 排序后的时区城市组合信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

