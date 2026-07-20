# ISO8601DateTimeFormat

符合ISO 8601标准的日期格式化对象。

**起始版本：** 26.0.0

<!--Device-i18n-export class ISO8601DateTimeFormat--><!--Device-i18n-export class ISO8601DateTimeFormat-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

<a id="constructor"></a>
## constructor

```TypeScript
public constructor(options?: ISO8601DateTimeFormatOptions)
```

创建符合ISO 8601标准的日期格式化对象。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ISO8601DateTimeFormat-public constructor(options?: ISO8601DateTimeFormatOptions)--><!--Device-ISO8601DateTimeFormat-public constructor(options?: ISO8601DateTimeFormatOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ISO8601DateTimeFormatOptions](arkts-localization-i18n-iso8601datetimeformatoptions-i.md) | 否 | 符合ISO 8601标准的日期格式化对象创建时的配置项。默认值：所有属性都取默认值时的配置项。 |

<a id="format"></a>
## format

```TypeScript
public format(date: Date): string
```

对时间日期进行格式化，返回符合ISO 8601标准的时间日期字符串。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ISO8601DateTimeFormat-public format(date: Date): string--><!--Device-ISO8601DateTimeFormat-public format(date: Date): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 是 | 时间日期。<br>**说明：**<br>月份从0开始计数，0表示一月。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 符合ISO8601标准的时间日期字符串。 |

