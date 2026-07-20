# StyledNumberFormat

提供富文本数字格式化的能力。

**起始版本：** 18

<!--Device-i18n-export class StyledNumberFormat--><!--Device-i18n-export class StyledNumberFormat-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor(numberFormat: Intl.NumberFormat | SimpleNumberFormat, options?: StyledNumberFormatOptions)
```

创建需要富文本显示的数字格式化的对象。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-StyledNumberFormat-constructor(numberFormat: Intl.NumberFormat | SimpleNumberFormat, options?: StyledNumberFormatOptions)--><!--Device-StyledNumberFormat-constructor(numberFormat: Intl.NumberFormat | SimpleNumberFormat, options?: StyledNumberFormatOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| numberFormat | Intl.NumberFormat \| SimpleNumberFormat | 是 | 用于格式化数字的对象。 |
| options | [StyledNumberFormatOptions](arkts-localization-i18n-stylednumberformatoptions-i.md) | 否 |  |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let integerTextStyle: TextStyle = new TextStyle({ fontColor: Color.Red });
  let decimalTextStyle: TextStyle = new TextStyle({ fontColor: Color.Brown });
  let fractionTextStyle: TextStyle = new TextStyle({ fontColor: Color.Blue });
  let unitTextStyle: TextStyle = new TextStyle({ fontColor: Color.Green });

  // 通过Intl.NumberFormat创建StyledNumberFormat对象
  let numFmt: Intl.NumberFormat = new Intl.NumberFormat('zh', { style: 'unit', unit: 'percent' });
  let styledNumFmt: i18n.StyledNumberFormat = new i18n.StyledNumberFormat(numFmt, {
    integer: integerTextStyle,
    decimal: decimalTextStyle,
    fraction: fractionTextStyle,
    unit: unitTextStyle
  });

  // 通过SimpleNumberFormat创建StyledNumberFormat对象
  let locale: Intl.Locale = new Intl.Locale('zh');
  let simpleNumFmt: i18n.SimpleNumberFormat = i18n.getSimpleNumberFormatBySkeleton('percent', locale);
  let styledSimpleNumFmt: i18n.StyledNumberFormat = new i18n.StyledNumberFormat(simpleNumFmt, {
    integer: integerTextStyle,
    decimal: decimalTextStyle,
    fraction: fractionTextStyle,
    unit: unitTextStyle
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call i18n.StyledNumberFormat failed, error code: ${err.code}, message: ${err.message}.`);
}

```

<a id="constructor-1"></a>
## constructor

```TypeScript
constructor(numberFormat: intl.NumberFormat | SimpleNumberFormat, options?: StyledNumberFormatOptions)
```

创建需要富文本显示的数字格式化的对象。

**起始版本：** 18

**废弃版本：** 20

**替代接口：** [constructor(numberFormat:](arkts-localization-i18n-stylednumberformat-c.md#constructor-1)

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-StyledNumberFormat-constructor(numberFormat: intl.NumberFormat | SimpleNumberFormat, options?: StyledNumberFormatOptions)--><!--Device-StyledNumberFormat-constructor(numberFormat: intl.NumberFormat | SimpleNumberFormat, options?: StyledNumberFormatOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| numberFormat | intl.NumberFormat \| SimpleNumberFormat | 是 | 用于格式化数字的对象。 |
| options | [StyledNumberFormatOptions](arkts-localization-i18n-stylednumberformatoptions-i.md) | 否 |  |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n, intl } from '@kit.LocalizationKit';

try {
  let integerTextStyle: TextStyle = new TextStyle({ fontColor: Color.Red });
  let decimalTextStyle: TextStyle = new TextStyle({ fontColor: Color.Brown });
  let fractionTextStyle: TextStyle = new TextStyle({ fontColor: Color.Blue });
  let unitTextStyle: TextStyle = new TextStyle({ fontColor: Color.Green });

  // 通过intl.NumberFormat创建StyledNumberFormat对象
  let numFmt: intl.NumberFormat = new intl.NumberFormat('zh', { style: 'unit', unit: 'percent' });
  let styledNumFmt: i18n.StyledNumberFormat = new i18n.StyledNumberFormat(numFmt, {
    integer: integerTextStyle,
    decimal: decimalTextStyle,
    fraction: fractionTextStyle,
    unit: unitTextStyle
  });

  // 通过SimpleNumberFormat创建StyledNumberFormat对象
  let locale: intl.Locale = new intl.Locale('zh');
  let simpleNumFmt: i18n.SimpleNumberFormat = i18n.getSimpleNumberFormatBySkeleton('percent', locale);
  let styledSimpleNumFmt: i18n.StyledNumberFormat = new i18n.StyledNumberFormat(simpleNumFmt, {
    integer: integerTextStyle,
    decimal: decimalTextStyle,
    fraction: fractionTextStyle,
    unit: unitTextStyle
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call i18n.StyledNumberFormat failed, error code: ${err.code}, message: ${err.message}.`);
}

```

<a id="format"></a>
## format

```TypeScript
format(value: number): StyledString
```

使用数字格式化对象对数字进行格式化，返回富文本对象。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-StyledNumberFormat-format(value: double): StyledString--><!--Device-StyledNumberFormat-format(value: double): StyledString-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 需要格式化的数字。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [StyledString](../../apis-arkui/arkts-apis/arkts-arkui-styledstring-c.md) | 格式化后的富文本对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let integerTextStyle: TextStyle = new TextStyle({ fontColor: Color.Red });
  let decimalTextStyle: TextStyle = new TextStyle({ fontColor: Color.Brown });
  let fractionTextStyle: TextStyle = new TextStyle({ fontColor: Color.Blue });
  let unitTextStyle: TextStyle = new TextStyle({ fontColor: Color.Green });

  // 通过Intl.NumberFormat创建StyledNumberFormat对象
  let numFmt: Intl.NumberFormat = new Intl.NumberFormat('zh', { style: 'unit', unit: 'percent' });
  let styledNumFmt: i18n.StyledNumberFormat = new i18n.StyledNumberFormat(numFmt, {
    integer: integerTextStyle,
    decimal: decimalTextStyle,
    fraction: fractionTextStyle,
    unit: unitTextStyle
  });
  // formattedNumber.getString() 为 '1,234.568%'。显示formattedNumber时'1,234'是红色，'.'是棕色，'568'是蓝色，'%'是绿色
  let formattedNumber: StyledString = styledNumFmt.format(1234.5678);

  // 通过SimpleNumberFormat创建StyledNumberFormat对象
  let locale: Intl.Locale = new Intl.Locale('zh');
  let simpleNumFmt: i18n.SimpleNumberFormat = i18n.getSimpleNumberFormatBySkeleton('percent', locale);
  let styledSimpleNumFmt: i18n.StyledNumberFormat = new i18n.StyledNumberFormat(simpleNumFmt, {
    integer: integerTextStyle,
    decimal: decimalTextStyle,
    fraction: fractionTextStyle,
    unit: unitTextStyle
  });
  // formattedSimpleNumber.getString() 为 '1,234.5678%'。显示formattedSimpleNumber时'1,234'是红色，'.'是棕色，'5678'是蓝色，'%'是绿色
  let formattedSimpleNumber: StyledString = styledSimpleNumFmt.format(1234.5678);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call StyledNumberFormat.format failed, error code: ${err.code}, message: ${err.message}.`);
}

```

