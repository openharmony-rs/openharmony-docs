# I18NUtil

国际化工具类，提供单位转换、获取日期顺序、获取时段名称、区域匹配和路径本地化等能力。

**起始版本：** 23

<!--Device-i18n-export class I18NUtil--><!--Device-i18n-export class I18NUtil-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## convertCanonicalLocaleIdentifier

```TypeScript
static convertCanonicalLocaleIdentifier(locale: string): string
```

将区域ID调整成符合[BCP47](https://www.rfc-editor.org/info/bcp47/)标准的格式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-I18NUtil-static convertCanonicalLocaleIdentifier(locale: string): string--><!--Device-I18NUtil-static convertCanonicalLocaleIdentifier(locale: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string | 是 | 区域ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 有效的区域ID会返回符合[BCP47](https://www.rfc-editor.org/info/bcp47/)标准格式的区域ID。无效的区域ID会返回空字符串。 |

**示例**

```TypeScript
let result: string = i18n.I18NUtil.convertCanonicalLocaleIdentifier('zh-cn'); // result = 'zh-CN'
```

## getBestMatchLocale

```TypeScript
static getBestMatchLocale(locale: string, localeList: string[]): string
```

在指定区域列表中获取与某个区域最佳匹配的区域。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-I18NUtil-static getBestMatchLocale(locale: string, localeList: string[]): string--><!--Device-I18NUtil-static getBestMatchLocale(locale: string, localeList: string[]): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string | 是 | 待匹配的[区域ID字符串](../../../internationalization/i18n-locale-culture.md#实现原理)，如：zh-Hans- CN。 |
| localeList | string[] | 是 | 指定的区域ID字符串列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 与某个区域最佳匹配的区域ID。当指定区域列表中没有匹配的区域时，返回空字串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let matchedLocaleId: string = i18n.I18NUtil.getBestMatchLocale('zh-Hans-CN',
    ['en-Latn-US', 'en-GB', 'zh-Hant-CN', 'zh-Hans-MO']); // matchedLocaleId = 'zh-Hans-MO'
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call I18NUtil.getBestMatchLocale failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getDateOrder

```TypeScript
static getDateOrder(locale: string): string
```

获取某区域日期中年、月、日的排列顺序。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-I18NUtil-static getDateOrder(locale: string): string--><!--Device-I18NUtil-static getDateOrder(locale: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string | 是 | [表示区域ID的字符串](../../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组 成，如：zh-Hans-CN。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 该区域年、月、日的排列顺序。“y”表示年，“L”表示月，“d”表示日。 |

**示例**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let order: string = i18n.I18NUtil.getDateOrder('zh-CN'); // order = 'y-L-d'
```

## getThreeLetterLanguage

```TypeScript
static getThreeLetterLanguage(locale: string): string
```

将语言代码由二字母转换为三字母。二字母和三字母语言代码的规格参考[ISO 639](https://www.iso.org/iso-639-language-code)。 例如，中文的二字母语言代码是zh，对应的三字母语言代码是zho。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-I18NUtil-static getThreeLetterLanguage(locale: string): string--><!--Device-I18NUtil-static getThreeLetterLanguage(locale: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string | 是 | 待转换的语言二字母代码，如：zh。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回待转换语言二字母代码对应的三字母代码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let language: string = i18n.I18NUtil.getThreeLetterLanguage('zh') // language = 'zho'
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call I18NUtil.getThreeLetterLanguage failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getThreeLetterRegion

```TypeScript
static getThreeLetterRegion(locale: string): string
```

将地区代码由二字母转换为三字母。二字母和三字母地区代码的规格参考[ISO 3166](https://www.iso.org/iso-3166-country-codes.html) 例如，中国的二字母地区代码是CN, 三字母是CHN。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-I18NUtil-static getThreeLetterRegion(locale: string): string--><!--Device-I18NUtil-static getThreeLetterRegion(locale: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string | 是 | 待转换的地区二字母代码，如：CN。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回待转换地区二字母代码对应的三字母代码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let region: string = i18n.I18NUtil.getThreeLetterRegion('CN') // region = 'CHN'
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call I18NUtil.getThreeLetterRegion failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getTimePeriodName

```TypeScript
static getTimePeriodName(hour:int, locale?: string): string
```

获取指定时间在某区域的本地化表达。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-I18NUtil-static getTimePeriodName(hour:int, locale?: string): string--><!--Device-I18NUtil-static getTimePeriodName(hour:int, locale?: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hour | int | 是 | 指定的时间，例如16。 |
| locale | string | 否 | [表示区域ID的字符串](../../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区 组成。如：zh-Hans-CN。 <br>默认值：系统当前区域ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 指定时间在某区域的本地化表达。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let name: string = i18n.I18NUtil.getTimePeriodName(2, 'zh-CN'); // name = '凌晨'
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call I18NUtil.getTimePeriodName failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getUnicodeWrappedFilePath

```TypeScript
static getUnicodeWrappedFilePath(path: string, delimiter?: string, locale?: Intl.Locale): string
```

对文件路径进行本地化处理。 例如，将/data/out/tmp本地化处理后生成tmp/out/data/。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-I18NUtil-static getUnicodeWrappedFilePath(path: string, delimiter?: string, locale?: Intl.Locale): string--><!--Device-I18NUtil-static getUnicodeWrappedFilePath(path: string, delimiter?: string, locale?: Intl.Locale): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待处理的路径，如：/data/out/tmp。 |
| delimiter | string | 否 | 路径分隔符，默认值：/。 |
| locale | Intl.Locale | 否 | 区域对象，默认值：系统区域对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 本地化处理后的文件路径。如果区域对象表示的语言是镜像语言，则处理后的文件路径包含方向控制符，保证文件路径镜像显示。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8900001](../errorcode-i18n.md#8900001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let path: string = '/data/out/tmp';
  let delimiter: string = '/';
  let locale: Intl.Locale = new Intl.Locale('ar');
  let mirrorPath: string =
    i18n.I18NUtil.getUnicodeWrappedFilePath(path, delimiter, locale); // mirrorPath显示为: 'tmp/out/data/'
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call I18NUtil.getUnicodeWrappedFilePath failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## getUnicodeWrappedFilePath

```TypeScript
static getUnicodeWrappedFilePath(path: string, delimiter?: string, locale?: intl.Locale): string
```

对文件路径进行本地化处理。 例如，将/data/out/tmp本地化处理后生成tmp/out/data/。

**起始版本：** 18

**废弃版本：** 20

**替代接口：** [getUnicodeWrappedFilePath](../../apis-na/arkts-apis/arkts-na-i18n-i18nutil-c.md#getunicodewrappedfilepath)(path: string, delimiter?: string, locale?: Intl.Locale)

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-I18NUtil-static getUnicodeWrappedFilePath(path: string, delimiter?: string, locale?: intl.Locale): string--><!--Device-I18NUtil-static getUnicodeWrappedFilePath(path: string, delimiter?: string, locale?: intl.Locale): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待处理的路径，如：/data/out/tmp。 |
| delimiter | string | 否 | 路径分隔符，默认值：/。 |
| locale | intl.Locale | 否 | 区域对象，默认值：系统区域对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 本地化处理后的文件路径。如果区域对象表示的语言是镜像语言，则处理后的文件路径包含方向控制符，保证文件路径镜像显示。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [890001](../errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n, intl } from '@kit.LocalizationKit';

try {
  let path: string = '/data/out/tmp';
  let delimiter: string = '/';
  let locale: intl.Locale = new intl.Locale('ar');
  let mirrorPath: string =
    i18n.I18NUtil.getUnicodeWrappedFilePath(path, delimiter, locale); // mirrorPath显示为: 'tmp/out/data/'
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call I18NUtil.getUnicodeWrappedFilePath failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## setUnicodeWrappedBidiDirection

```TypeScript
static setUnicodeWrappedBidiDirection(text: string, direction: 'RTL' | 'LTR'): string
```

设置整段文本中部分文本方向，包括RTL、LTR。 > **说明：** > > 在强字符（指具有明确书写方向的字符）中不生效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-I18NUtil-static setUnicodeWrappedBidiDirection(text: string, direction: 'RTL' | 'LTR'): string--><!--Device-I18NUtil-static setUnicodeWrappedBidiDirection(text: string, direction: 'RTL' | 'LTR'): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 需要设置方向的文本。 |
| direction | 'RTL' \| 'LTR' | 是 | 'RTL'表示从右到左，'LTR'表示从左到右。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 设置方向后的文本。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let text: string = '(012) 345-6789';
  let result: string = i18n.I18NUtil.setUnicodeWrappedBidiDirection(text, 'LTR');
  console.info(`setUnicodeWrappedBidiDirection, result: ${result}`);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call I18NUtil.setUnicodeWrappedBidiDirection failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## unitConvert

```TypeScript
static unitConvert(fromUnit: UnitInfo, toUnit: UnitInfo, value: double, locale: string, style?: string): string
```

将fromUnit的单位转换为toUnit的单位，并根据区域与风格进行格式化。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-I18NUtil-static unitConvert(fromUnit: UnitInfo, toUnit: UnitInfo, value: double, locale: string, style?: string): string--><!--Device-I18NUtil-static unitConvert(fromUnit: UnitInfo, toUnit: UnitInfo, value: double, locale: string, style?: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fromUnit | [UnitInfo](../../apis-na/arkts-apis/arkts-na-i18n-unitinfo-i.md) | 是 | 需要转换的单位。 |
| toUnit | [UnitInfo](../../apis-na/arkts-apis/arkts-na-i18n-unitinfo-i.md) | 是 | 转换成的目标单位。 |
| value | double | 是 | 需要转换的单位的数量值。 |
| locale | string | 是 | [表示区域ID的字符串](../../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组 成，如：zh-Hans-CN。 |
| style | string | 否 | 格式化使用的风格，取值包括：'long', 'short', 'narrow'。默认值：short。 <br>不同取值显示效果请参考[数字与度量衡国际化](../../../internationalization/i18n-numbers-weights-measures.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 转换单位后的度量衡格式化结果。 |

**示例**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let fromUnit: i18n.UnitInfo = { unit: 'cup', measureSystem: 'US' };
let toUnit: i18n.UnitInfo = { unit: 'liter', measureSystem: 'SI' };
let convertResult: string =
  i18n.I18NUtil.unitConvert(fromUnit, toUnit, 1000, 'en-US', 'long'); // convertResult = '236.588 liters'
```

