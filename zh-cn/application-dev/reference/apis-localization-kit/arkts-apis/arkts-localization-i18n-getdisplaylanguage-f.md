# getDisplayLanguage

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getDisplayLanguage

```TypeScript
export function getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string
```

获取指定语言的本地化显示文本。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getDisplayLanguage](arkts-localization-i18n-system-c.md#getdisplaylanguage)

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| language | string | 是 | 指定语言。 |
| locale | string | 是 | [表示区域ID的字符串](../../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组成。 |
| sentenceCase | boolean | 否 | true表示按照首字母大写的格式显示文本，false表示按照区域默认的大小写格式显示文本。默认值：true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 指定语言的本地化显示文本。 |

**示例**

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

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let languageName: string = i18n.getDisplayLanguage('zh', 'en-GB', true); // languageName = 'Chinese'
languageName = i18n.getDisplayLanguage('zh', 'en-GB'); // languageName = 'Chinese'
```
