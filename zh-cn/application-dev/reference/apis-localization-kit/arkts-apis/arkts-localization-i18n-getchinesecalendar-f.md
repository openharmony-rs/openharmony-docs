# getChineseCalendar

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getChineseCalendar

```TypeScript
export function getChineseCalendar(locale?: Intl.Locale): ChineseCalendar
```

获取指定区域的农历对象。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-i18n-export function getChineseCalendar(locale?: Intl.Locale): ChineseCalendar--><!--Device-i18n-export function getChineseCalendar(locale?: Intl.Locale): ChineseCalendar-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | Intl.Locale | 否 | 区域对象，默认值：系统区域对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ChineseCalendar](arkts-localization-i18n-chinesecalendar-c.md) | 农历对象。 |

