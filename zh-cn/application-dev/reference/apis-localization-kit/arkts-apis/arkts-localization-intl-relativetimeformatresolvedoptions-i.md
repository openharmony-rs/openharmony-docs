# RelativeTimeFormatResolvedOptions

相对时间格式化对象的格式化配置项。

**起始版本：** 8

**废弃版本：** 20

**替代接口：** return_value)

<!--Device-intl-export interface RelativeTimeFormatResolvedOptions--><!--Device-intl-export interface RelativeTimeFormatResolvedOptions-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { intl } from '@kit.LocalizationKit';
```

## locale

```TypeScript
locale: string
```

表示区域ID的字符串，包括语言以及可选的脚本和区域。

**类型：** string

**起始版本：** 8

**废弃版本：** 20

**替代接口：** locale)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RelativeTimeFormatResolvedOptions-locale: string--><!--Device-RelativeTimeFormatResolvedOptions-locale: string-End-->

**系统能力：** SystemCapability.Global.I18n

## numberingSystem

```TypeScript
numberingSystem: string
```

使用的数字系统，取值包括：

"adlm", "ahom", "arab", "arabext", "bali", "beng", "bhks", "brah", "cakm", "cham", "deva", "diak", "fullwide","gong", "gonm", "gujr", "guru", "hanidec", "hmng", "hmnp", "java", "kali", "khmr", "knda", "lana", "lanatham","laoo", "latn", "lepc", "limb", "mathbold", "mathdbl", "mathmono", "mathsanb", "mathsans", "mlym", "modi", "mong","mroo", "mtei", "mymr", "mymrshan", "mymrtlng", "newa", "nkoo", "olck", "orya", "osma", "rohg", "saur", "segment","shrd", "sind", "sinh", "sora", "sund", "takr", "talu", "tamldec", "telu", "thai", "tibt", "tirh", "vaii","wara", "wcho"。

**类型：** string

**起始版本：** 8

**废弃版本：** 20

**替代接口：** numberingsystem)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RelativeTimeFormatResolvedOptions-numberingSystem: string--><!--Device-RelativeTimeFormatResolvedOptions-numberingSystem: string-End-->

**系统能力：** SystemCapability.Global.I18n

## numeric

```TypeScript
numeric: string
```

输出消息的格式，表示格式化结果中是否使用数字表示相对日期或时间。取值包括："always", "auto"。

不同取值的显示效果请参考[附录表23](docroot://reference/apis-localization-kit/js-apis-intl.md#附录)。

**类型：** string

**起始版本：** 8

**废弃版本：** 20

**替代接口：** numeric)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RelativeTimeFormatResolvedOptions-numeric: string--><!--Device-RelativeTimeFormatResolvedOptions-numeric: string-End-->

**系统能力：** SystemCapability.Global.I18n

## style

```TypeScript
style: string
```

国际化消息的长度，取值包括："long", "short", "narrow"。

不同取值的显示效果请参考[附录表24](docroot://reference/apis-localization-kit/js-apis-intl.md#附录)。

**类型：** string

**起始版本：** 8

**废弃版本：** 20

**替代接口：** style)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RelativeTimeFormatResolvedOptions-style: string--><!--Device-RelativeTimeFormatResolvedOptions-style: string-End-->

**系统能力：** SystemCapability.Global.I18n

