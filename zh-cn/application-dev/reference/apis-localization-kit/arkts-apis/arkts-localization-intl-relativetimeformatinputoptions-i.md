# RelativeTimeFormatInputOptions

创建相对时间格式化对象时可设置的配置项。

从API version 9开始，RelativeTimeFormatInputOptions中的属性改为可选。

**起始版本：** 8

**废弃版本：** 20

**替代接口：** options)

<!--Device-intl-export interface RelativeTimeFormatInputOptions--><!--Device-intl-export interface RelativeTimeFormatInputOptions-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { intl } from '@kit.LocalizationKit';
```

## localeMatcher

```TypeScript
localeMatcher?: string
```

区域匹配算法，取值包括："best fit", "lookup"。

默认值：best fit。

**类型：** string

**起始版本：** 8

**废弃版本：** 20

**替代接口：** localematcher)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RelativeTimeFormatInputOptions-localeMatcher?: string--><!--Device-RelativeTimeFormatInputOptions-localeMatcher?: string-End-->

**系统能力：** SystemCapability.Global.I18n

## numeric

```TypeScript
numeric?: string
```

输出消息的格式，表示格式化结果中是否使用数字表示相对日期或时间。取值包括："always", "auto"。

默认值：always。

不同取值的显示效果请参考[附录表23](docroot://reference/apis-localization-kit/js-apis-intl.md#附录)。

**类型：** string

**起始版本：** 8

**废弃版本：** 20

**替代接口：** numeric)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RelativeTimeFormatInputOptions-numeric?: string--><!--Device-RelativeTimeFormatInputOptions-numeric?: string-End-->

**系统能力：** SystemCapability.Global.I18n

## style

```TypeScript
style?: string
```

国际化消息的长度，取值包括："long", "short", "narrow"。

默认值：long。

不同取值的显示效果请参考[附录表24](docroot://reference/apis-localization-kit/js-apis-intl.md#附录)。

**类型：** string

**起始版本：** 8

**废弃版本：** 20

**替代接口：** style)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RelativeTimeFormatInputOptions-style?: string--><!--Device-RelativeTimeFormatInputOptions-style?: string-End-->

**系统能力：** SystemCapability.Global.I18n

