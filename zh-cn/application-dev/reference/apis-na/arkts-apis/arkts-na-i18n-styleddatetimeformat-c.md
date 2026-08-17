# StyledDateTimeFormat

提供富文本时间日期格式化的能力。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

<!--Device-i18n-export class StyledDateTimeFormat--><!--Device-i18n-export class StyledDateTimeFormat-End-->

**系统能力：** SystemCapability.Global.I18n

## constructor

```TypeScript
constructor(dateTimeFormat: Intl.DateTimeFormat | SimpleDateTimeFormat,
        options?: StyledDateTimeFormatOptions)
```

创建需要富文本显示的时间日期格式化的对象。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-StyledDateTimeFormat-constructor(dateTimeFormat: Intl.DateTimeFormat | SimpleDateTimeFormat,        options?: StyledDateTimeFormatOptions)--><!--Device-StyledDateTimeFormat-constructor(dateTimeFormat: Intl.DateTimeFormat | SimpleDateTimeFormat,        options?: StyledDateTimeFormatOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dateTimeFormat | Intl.DateTimeFormat \| [SimpleDateTimeFormat](arkts-na-i18n-simpledatetimeformat-c.md) | 是 | 用于格式化时间日期的对象。 |
| options | [StyledDateTimeFormatOptions](arkts-na-i18n-styleddatetimeformatoptions-i.md) | 否 | 指定时间日期格式化对象的配置项。默认值：默认的文本样式。 |

## format

```TypeScript
format(date: Date): StyledString
```

对时间日期进行格式化，返回富文本对象。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-StyledDateTimeFormat-format(date: Date): StyledString--><!--Device-StyledDateTimeFormat-format(date: Date): StyledString-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 是 | 时间日期。 <br>**说明：** <br>月份从0开始计数，0表示一月。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [StyledString](../../apis-arkui/arkts-apis/arkts-arkui-styledstring-styledstring-c.md) | 格式化后的富文本对象。 |

