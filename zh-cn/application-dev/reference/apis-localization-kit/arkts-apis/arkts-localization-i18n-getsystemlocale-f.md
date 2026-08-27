# getSystemLocale

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getSystemLocale

```TypeScript
export function getSystemLocale(): string
```


> [System.getSystemLocale](arkts-localization-i18n-system-c.md#getsystemlocaleinstance)代替。
> 获取系统区域ID。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getSystemLocale](arkts-localization-i18n-system-c.md#getsystemlocale)

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 系统区域ID。 |

**示例**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let systemLocale: string = i18n.System.getSystemLocale(); // 如果系统语言为简体中文、地区为中国，systemLocale = 'zh-Hans-CN'
```

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let locale: string = i18n.getSystemLocale();
```
