# StyledDateTimeFormat

提供富文本时间日期格式化的能力。

**起始版本：** 23

<!--Device-i18n-export class StyledDateTimeFormat--><!--Device-i18n-export class StyledDateTimeFormat-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## constructor

```TypeScript
constructor(dateTimeFormat: Intl.DateTimeFormat | SimpleDateTimeFormat,
        options?: StyledDateTimeFormatOptions)
```

创建需要富文本显示的时间日期格式化的对象。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-StyledDateTimeFormat-constructor(dateTimeFormat: Intl.DateTimeFormat | SimpleDateTimeFormat,
        options?: StyledDateTimeFormatOptions)--><!--Device-StyledDateTimeFormat-constructor(dateTimeFormat: Intl.DateTimeFormat | SimpleDateTimeFormat,
        options?: StyledDateTimeFormatOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dateTimeFormat | Intl.DateTimeFormat \| SimpleDateTimeFormat | 是 | 用于格式化时间日期的对象。 |
| options | [StyledDateTimeFormatOptions](arkts-localization-i18n-styleddatetimeformatoptions-i.md) | 否 |  |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let yearTextStyle: TextStyle = new TextStyle({ fontColor: Color.Red });
  let monthTextStyle: TextStyle = new TextStyle({ fontColor: Color.Green });
  let dayTextStyle: TextStyle = new TextStyle({ fontColor: Color.Blue });

  // 通过Intl.DateTimeFormat创建StyledDateTimeFormat对象
  let dateFormat: Intl.DateTimeFormat = new Intl.DateTimeFormat('zh-Hans-CN', { dateStyle: 'full' });
  let styledDateFormat: i18n.StyledDateTimeFormat = new i18n.StyledDateTimeFormat(dateFormat, {
    year: yearTextStyle,
    month: monthTextStyle,
    day: dayTextStyle
  });

  let hourTextStyle: TextStyle = new TextStyle({ fontColor: Color.Yellow });
  let minuteTextStyle: TextStyle = new TextStyle({ fontColor: Color.Orange });
  let secondTextStyle: TextStyle = new TextStyle({ fontColor: Color.Pink });

  // 通过SimpleDateTimeFormat创建StyledDateTimeFormat对象
  let locale: Intl.Locale = new Intl.Locale('zh-Hans-CN');
  let simpleTimeFormat: i18n.SimpleDateTimeFormat = i18n.getSimpleDateTimeFormatBySkeleton('hhmmss', locale);
  let styledTimeFormat: i18n.StyledDateTimeFormat = new i18n.StyledDateTimeFormat(simpleTimeFormat, {
    hour: hourTextStyle,
    minute: minuteTextStyle,
    second: secondTextStyle
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call i18n.StyledDateTimeFormat failed, error code: ${err.code}, message: ${err.message}.`);
}

```

## format

```TypeScript
format(date: Date): StyledString
```

对时间日期进行格式化，返回富文本对象。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-StyledDateTimeFormat-format(date: Date): StyledString--><!--Device-StyledDateTimeFormat-format(date: Date): StyledString-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 是 | 时间日期。<br>**说明：**<br>月份从0开始计数，0表示一月。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [StyledString](../../apis-arkui/arkts-apis/arkts-arkui-styled-string-styledstring-c.md) | 格式化后的富文本对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let yearTextStyle: TextStyle = new TextStyle({ fontColor: Color.Red });
  let monthTextStyle: TextStyle = new TextStyle({ fontColor: Color.Green });
  let dayTextStyle: TextStyle = new TextStyle({ fontColor: Color.Blue });

  // 通过Intl.DateTimeFormat创建StyledDateTimeFormat对象
  let dateFormat: Intl.DateTimeFormat = new Intl.DateTimeFormat('zh-Hans-CN', { dateStyle: 'full' });
  let styledDateFormat: i18n.StyledDateTimeFormat = new i18n.StyledDateTimeFormat(dateFormat, {
    year: yearTextStyle,
    month: monthTextStyle,
    day: dayTextStyle
  });
  let date: Date = new Date(2025, 11, 1);
  // formattedDate.getString() 为 '2025年12月1日星期一'。显示formattedDate时'2025'是红色，'12'是绿色，'1'是蓝色
  let formattedDate: StyledString = styledDateFormat.format(date);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call StyledNumberFormat.format failed, error code: ${err.code}, message: ${err.message}.`);
}

```

