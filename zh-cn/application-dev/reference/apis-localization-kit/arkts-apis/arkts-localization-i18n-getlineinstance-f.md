# getLineInstance

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getLineInstance

```TypeScript
export function getLineInstance(locale: string): BreakIterator
```

获取用于定位文本可换行点的BreakIterator对象。该对象内部维护一个换行迭代器，可以用于访问各个可换行点。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-i18n-export function getLineInstance(locale: string): BreakIterator--><!--Device-i18n-export function getLineInstance(locale: string): BreakIterator-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string | 是 | [表示区域ID的字符串](../../../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组成。<br>生成的[BreakIterator](arkts-localization-i18n-breakiterator-c.md)将按照指定区域的规则计算可换行点的位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BreakIterator](arkts-localization-i18n-breakiterator-c.md) | 可换行点处理器。 |

