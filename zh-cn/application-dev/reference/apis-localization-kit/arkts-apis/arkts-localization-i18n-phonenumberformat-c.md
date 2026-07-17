# PhoneNumberFormat

提供电话号码相关的能力，包括电话号码有效性判断、格式化和归属地获取。

**起始版本：** 8

<!--Device-i18n-export class PhoneNumberFormat--><!--Device-i18n-export class PhoneNumberFormat-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## constructor

```TypeScript
constructor(country: string, options?: PhoneNumberFormatOptions)
```

创建电话号码格式化对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PhoneNumberFormat-constructor(country: string, options?: PhoneNumberFormatOptions)--><!--Device-PhoneNumberFormat-constructor(country: string, options?: PhoneNumberFormatOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| country | string | 是 | 表示电话号码所属的国家地区代码，要求是[合法的国家地区码](../../../../internationalization/i18n-locale-culture.md#实现原理)。 |
| options | [PhoneNumberFormatOptions](arkts-localization-i18n-phonenumberformatoptions-i.md) | 否 | 电话号码格式化时设置的配置项。默认值：NATIONAL。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let option: i18n.PhoneNumberFormatOptions = { type: 'E164' };
let phoneNumberFormat: i18n.PhoneNumberFormat = new i18n.PhoneNumberFormat('CN', option);

```

## format

```TypeScript
format(phoneNumber: string): string
```

对电话号码进行格式化。

> **说明**  
>  
> 从API version 12开始，支持对拨号中的电话号码进行格式化。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PhoneNumberFormat-format(phoneNumber: string): string--><!--Device-PhoneNumberFormat-format(phoneNumber: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 待格式化的电话号码。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 格式化后的电话号码。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let formatter: i18n.PhoneNumberFormat = new i18n.PhoneNumberFormat('CN');
// formattedPhoneNumber = '158 **** 2312'
let formattedPhoneNumber: string = formatter.format('158****2312');

// 拨号中的电话号码格式化
let option: i18n.PhoneNumberFormatOptions = { type: 'TYPING' };
let typingFormatter: i18n.PhoneNumberFormat = new i18n.PhoneNumberFormat('CN', option);
let phoneNumber: string = '130493';
let formatResult: string = '';
for (let i = 0; i < phoneNumber.length; i++) {
  formatResult += phoneNumber.charAt(i);
  formatResult = typingFormatter.format(formatResult); // formatResult = '130 493'
}

```

## getLocationName

```TypeScript
getLocationName(phoneNumber: string, locale: string): string
```

获取电话号码归属地。

> **说明**  
>  
> 从API version 23开始，支持对拨号中的电话号码实时获取归属地。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PhoneNumberFormat-getLocationName(phoneNumber: string, locale: string): string--><!--Device-PhoneNumberFormat-getLocationName(phoneNumber: string, locale: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 电话号码。获取其他地区电话号码的归属地时，需要在电话号码前加00+国际区号。<br>**起始版本：** 12 |
| locale | string | 是 | [表示区域ID的字符串](../../../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 电话号码归属地。无效号码时返回空字符串。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

// 完整电话号码的归属地获取
let phonenumberFormat: i18n.PhoneNumberFormat = new i18n.PhoneNumberFormat('CN');
let locationName: string = phonenumberFormat.getLocationName('158****2345', 'zh-CN'); // locationName = '广东省湛江市'
let locName: string = phonenumberFormat.getLocationName('0039312****789', 'zh-CN'); // locName = '意大利'

// 拨号中的电话号码归属地获取
let option: i18n.PhoneNumberFormatOptions = { type: 'TYPING' };
let typingFormatter: i18n.PhoneNumberFormat = new i18n.PhoneNumberFormat('CN', option);
let formatResult = typingFormatter.getLocationName('1', 'en'); // formatResult = ''
formatResult = typingFormatter.getLocationName('13', 'en'); // formatResult = 'China'
formatResult = typingFormatter.getLocationName('133', 'en'); // formatResult = 'China'
formatResult = typingFormatter.getLocationName('1334', 'en'); // formatResult = 'China'
formatResult = typingFormatter.getLocationName('13342', 'en'); // formatResult = 'China'
formatResult = typingFormatter.getLocationName('133426', 'en'); // formatResult = 'Dongguan, Guangdong'

```

## isValidNumber

```TypeScript
isValidNumber(phoneNumber: string): boolean
```

判断电话号码是否为当前电话号码格式化对象中国家的有效号码。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PhoneNumberFormat-isValidNumber(phoneNumber: string): boolean--><!--Device-PhoneNumberFormat-isValidNumber(phoneNumber: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 待判断的电话号码。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示电话号码有效，false表示电话号码无效。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let formatter: i18n.PhoneNumberFormat = new i18n.PhoneNumberFormat('CN');
let isValidNumber: boolean = formatter.isValidNumber('158****2312'); // isValidNumber = true

```

