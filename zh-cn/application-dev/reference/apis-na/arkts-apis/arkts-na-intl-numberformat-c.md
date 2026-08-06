# NumberFormat

提供标准的数字格式化的能力。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-intl-export class NumberFormat--><!--Device-intl-export class NumberFormat-End-->

**系统能力：** SystemCapability.Global.I18n

## constructor

```TypeScript
constructor()
```

使用当前系统区域创建数字格式化对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-NumberFormat-constructor()--><!--Device-NumberFormat-constructor()-End-->

**系统能力：** SystemCapability.Global.I18n

## constructor

```TypeScript
constructor(locale: string | Array<string>, options?: NumberOptions)
```

根据指定的区域和配置项创建数字格式化对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-NumberFormat-constructor(locale: string | Array<string>, options?: NumberOptions)--><!--Device-NumberFormat-constructor(locale: string | Array<string>, options?: NumberOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string \| Array&lt;string&gt; | 是 | 区域ID或区域ID数组。输入是区域ID数组时，使用第一个有效的区域ID。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 创建数字格式化对象时可设置的配置项。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：所有属性都取默认值时的配置项。 |

## format

```TypeScript
format(num: double): string
```

对数字进行格式化，返回格式化后的数字字符串。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-NumberFormat-format(num: double): string--><!--Device-NumberFormat-format(num: double): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| num | double | 是 | 数字对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 格式化后的数字字符串。 |

## formatRange

```TypeScript
formatRange(startRange: double, endRange: double): string
```

对数字范围进行格式化，返回格式化后的数字范围字符串。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-NumberFormat-formatRange(startRange: double, endRange: double): string--><!--Device-NumberFormat-formatRange(startRange: double, endRange: double): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startRange | double | 是 | 数字范围的起始值。 |
| endRange | double | 是 | 数字范围的终止值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 格式化后的数字范围字符串。 |

## resolvedOptions

```TypeScript
resolvedOptions(): NumberOptions
```

获取创建数字格式化对象时设置的配置项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-NumberFormat-resolvedOptions(): NumberOptions--><!--Device-NumberFormat-resolvedOptions(): NumberOptions-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 创建数字格式化对象时设置的配置项。 |

