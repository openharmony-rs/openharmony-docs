# AdvancedMeasureFormat

提供数字格式化能力，支持根据单位使用场景自动转换合适的单位。

**起始版本：** 23

<!--Device-i18n-export class AdvancedMeasureFormat--><!--Device-i18n-export class AdvancedMeasureFormat-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor(numberFormat: Intl.NumberFormat, options?: AdvancedMeasureFormatOptions)
```

创建数字格式化对象。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedMeasureFormat-constructor(numberFormat: Intl.NumberFormat, options?: AdvancedMeasureFormatOptions)--><!--Device-AdvancedMeasureFormat-constructor(numberFormat: Intl.NumberFormat, options?: AdvancedMeasureFormatOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| numberFormat | Intl.NumberFormat | 是 | 用于格式化数字的对象。 |
| options | [AdvancedMeasureFormatOptions](arkts-localization-i18n-advancedmeasureformatoptions-i.md) | 否 |  |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let numFmt: Intl.NumberFormat = new Intl.NumberFormat('zh-Hans-CN', { style: 'unit', unit: 'fahrenheit' });
let advancedMeasureFormat: i18n.AdvancedMeasureFormat = new i18n.AdvancedMeasureFormat(numFmt, {
  unitUsage: i18n.UnitUsage.TEMPERATURE_PERSON
});

```

<a id="format"></a>
## format

```TypeScript
format(num: number): string
```

对数字进行格式化。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedMeasureFormat-format(num: double): string--><!--Device-AdvancedMeasureFormat-format(num: double): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| num | number | 是 | 需要格式化的数字。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 格式化后的文本。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let numFmt: Intl.NumberFormat = new Intl.NumberFormat('zh-Hans-CN', { style: 'unit', unit: 'fahrenheit' });
let advancedMeasureFormat: i18n.AdvancedMeasureFormat = new i18n.AdvancedMeasureFormat(numFmt, {
  unitUsage: i18n.UnitUsage.TEMPERATURE_PERSON
});
let result = advancedMeasureFormat.format(100); // result = '37.778°C'

```

