# SimpleDateTimeFormat

提供时间日期格式化的能力。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-i18n-export class SimpleDateTimeFormat--><!--Device-i18n-export class SimpleDateTimeFormat-End-->

**系统能力：** SystemCapability.Global.I18n

## format

```TypeScript
format(date: Date): string
```

对时间日期进行格式化。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SimpleDateTimeFormat-format(date: Date): string--><!--Device-SimpleDateTimeFormat-format(date: Date): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 是 | 时间日期。 &lt;br&gt;**说明：** &lt;br&gt;月份从0开始计数，0表示一月。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 格式化后的时间日期字符串。 |

