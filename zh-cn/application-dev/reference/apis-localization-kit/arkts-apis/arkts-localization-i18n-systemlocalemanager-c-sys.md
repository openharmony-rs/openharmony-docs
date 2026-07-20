# SystemLocaleManager（系统接口）

提供语言、地区和时区信息排序的能力。

**起始版本：** 10

<!--Device-i18n-export class SystemLocaleManager--><!--Device-i18n-export class SystemLocaleManager-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

创建SystemLocaleManager对象。

**起始版本：** 10

<!--Device-SystemLocaleManager-constructor()--><!--Device-SystemLocaleManager-constructor()-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let systemLocaleManager: i18n.SystemLocaleManager = new i18n.SystemLocaleManager();

```

<a id="getlanguageinfoarray"></a>
## getLanguageInfoArray

```TypeScript
getLanguageInfoArray(languages: Array<string>, options?: SortOptions): Array<LocaleItem>
```

获取排序后的语言信息列表。

**起始版本：** 10

<!--Device-SystemLocaleManager-getLanguageInfoArray(languages: Array<string>, options?: SortOptions): Array<LocaleItem>--><!--Device-SystemLocaleManager-getLanguageInfoArray(languages: Array<string>, options?: SortOptions): Array<LocaleItem>-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| languages | Array&lt;string&gt; | 是 | 待排序的语言列表，要求是合法的语言ID。 |
| options | [SortOptions](arkts-localization-i18n-sortoptions-i-sys.md) | 否 | 语言排序选项。默认值：所有属性都取默认值时的配置项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;LocaleItem&gt; | 排序后的语言信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

// 当系统语言为zh-Hans，系统地区为CN，系统区域为zh-Hans-CN时
let systemLocaleManager: i18n.SystemLocaleManager = new i18n.SystemLocaleManager();
let languages: string[] = ["zh-Hans", "en-US", "pt", "ar"];
let sortOptions: i18n.SortOptions = {locale: "zh-Hans-CN", isUseLocalName: true, isSuggestedFirst: true};
try {
    // 排序后的语言顺序为: [zh-Hans, en-US, pt, ar]
    let sortedLanguages: Array<i18n.LocaleItem> = systemLocaleManager.getLanguageInfoArray(languages, sortOptions);
} catch(error) {
    let err: BusinessError = error as BusinessError;
    console.error(`call systemLocaleManager.getLanguageInfoArray failed, error code: ${err.code}, message: ${err.message}.`);
}

```

<a id="getregioninfoarray"></a>
## getRegionInfoArray

```TypeScript
getRegionInfoArray(regions: Array<string>, options?: SortOptions): Array<LocaleItem>
```

获取排序后的国家或地区信息列表。

**起始版本：** 10

<!--Device-SystemLocaleManager-getRegionInfoArray(regions: Array<string>, options?: SortOptions): Array<LocaleItem>--><!--Device-SystemLocaleManager-getRegionInfoArray(regions: Array<string>, options?: SortOptions): Array<LocaleItem>-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| regions | Array&lt;string&gt; | 是 | 待排序的国家或地区列表，要求是合法的国家或地区ID。 |
| options | [SortOptions](arkts-localization-i18n-sortoptions-i-sys.md) | 否 | 国家或地区排序选项。区域ID的默认值为系统当前区域ID，isUseLocalName的默认值为false，isSuggestedFirst的默认值为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;LocaleItem&gt; | 排序后的国家或地区信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed.A non-system application calls a system API.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

// 当系统语言为zh-Hans，系统地区为CN，系统区域为zh-Hans-CN时
let systemLocaleManager: i18n.SystemLocaleManager = new i18n.SystemLocaleManager();
let regions: string[] = ["CN", "US", "PT", "EG"];
let sortOptions: i18n.SortOptions = {locale: "zh-Hans-CN", isUseLocalName: false, isSuggestedFirst: true};
try {
    // 排序后的地区顺序为: [CN, EG, US, PT]
    let sortedRegions: Array<i18n.LocaleItem> = systemLocaleManager.getRegionInfoArray(regions, sortOptions);
} catch(error) {
    let err: BusinessError = error as BusinessError;
    console.error(`call systemLocaleManager.getRegionInfoArray failed, error code: ${err.code}, message: ${err.message}.`);
}

```

<a id="gettimezonecityitemarray"></a>
## getTimeZoneCityItemArray

```TypeScript
static getTimeZoneCityItemArray(): Array<TimeZoneCityItem>
```

获取排序后的时区城市组合信息列表。

**起始版本：** 10

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
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed.A non-system application calls a systemAPI.<br>**适用版本：** 12+ |

**示例：**

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

