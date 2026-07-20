# getCalendar

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

<a id="getcalendar"></a>
## getCalendar

```TypeScript
export function getCalendar(locale: string, type?: string): Calendar
```

获取指定区域和历法的日历对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-i18n-export function getCalendar(locale: string, type?: string): Calendar--><!--Device-i18n-export function getCalendar(locale: string, type?: string): Calendar-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string | 是 | [表示区域ID的字符串](docroot://internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组成，例如zh-Hans-CN。 |
| type | string | 否 | 表示历法，取值包括：buddhist, chinese, coptic, ethiopic, hebrew, gregory, indian, islamic_civil, islamic_tbla, islamic_umalqura, japanese, persian。<br>默认值：区域默认的历法。不同取值代表的含义和使用场景请参考[设置日历和历法](docroot://internationalization/i18n-calendar.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Calendar](arkts-localization-i18n-calendar-c.md) | 日历对象。 |

