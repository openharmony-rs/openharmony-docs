# DateTimeFormat

提供日期格式化的能力。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-intl-export class DateTimeFormat--><!--Device-intl-export class DateTimeFormat-End-->

**系统能力：** SystemCapability.Global.I18n

## constructor

```TypeScript
constructor()
```

创建时间日期格式化对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-DateTimeFormat-constructor()--><!--Device-DateTimeFormat-constructor()-End-->

**系统能力：** SystemCapability.Global.I18n

## constructor

```TypeScript
constructor(locale: string | Array<string>, options?: DateTimeOptions)
```

创建时间日期格式化对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-DateTimeFormat-constructor(locale: string | Array<string>, options?: DateTimeOptions)--><!--Device-DateTimeFormat-constructor(locale: string | Array<string>, options?: DateTimeOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string \| Array&lt;string&gt; | 是 | 区域ID或区域ID数组。输入是区域ID数组时，使用第一个有效的区域ID。 |
| options | DateTimeOptions | 否 | 创建时间日期格式化对象时可设置的配置项。 &lt;br&gt;若所有选项均未设置时，year、month、day三个属性的默认值为numeric。 &lt;br&gt;默认值：所有属性都取默认值时的配置项。 |

## format

```TypeScript
format(date: Date): string
```

对时间日期进行格式化，返回格式化后的时间日期字符串。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-DateTimeFormat-format(date: Date): string--><!--Device-DateTimeFormat-format(date: Date): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 是 | 时间日期。 &lt;br&gt;**说明：** &lt;br&gt;月份从0开始计数，0表示一月。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 格式化后的时间日期字符串。 |

## formatRange

```TypeScript
formatRange(startDate: Date, endDate: Date): string
```

对时间日期段进行格式化，返回格式化后的时间日期段字符串。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-DateTimeFormat-formatRange(startDate: Date, endDate: Date): string--><!--Device-DateTimeFormat-formatRange(startDate: Date, endDate: Date): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startDate | Date | 是 | 时间日期的开始。 &lt;br&gt;**说明：** &lt;br&gt;月份从0开始计数，0表示一月。 |
| endDate | Date | 是 | 时间日期的结束。 &lt;br&gt;**说明：** &lt;br&gt;月份从0开始计数，0表示一月。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 格式化后的时间日期段字符串。 |

## resolvedOptions

```TypeScript
resolvedOptions(): DateTimeOptions
```

获取创建时间日期格式化对象时设置的配置项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-DateTimeFormat-resolvedOptions(): DateTimeOptions--><!--Device-DateTimeFormat-resolvedOptions(): DateTimeOptions-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DateTimeOptions | 时间日期格式化对象设置的配置项。 |

