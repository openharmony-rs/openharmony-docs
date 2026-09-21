# addPreferredLanguage

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## addPreferredLanguage

```TypeScript
export function addPreferredLanguage(language: string, index?: number): boolean
```

在系统偏好语言列表的指定位置添加偏好语言。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [addPreferredLanguage](arkts-localization-i18n-system-c-sys.md#addpreferredlanguage)

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| language | string | 是 | 待添加的偏好语言。 |
| index | number | 否 | 偏好语言的添加位置。默认值：系统偏好语言列表长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示添加成功，false表示添加失败。 |

**示例**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

// 将语言zh-CN添加到系统偏好语言列表中
let language: string = 'zh-CN';
let index: number = 0;
let success: boolean = i18n.addPreferredLanguage(language, index);
```
