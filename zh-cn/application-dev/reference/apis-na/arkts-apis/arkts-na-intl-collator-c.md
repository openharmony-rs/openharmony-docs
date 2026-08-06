# Collator

提供字符串排序的能力。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-intl-export class Collator--><!--Device-intl-export class Collator-End-->

**系统能力：** SystemCapability.Global.I18n

## compare

```TypeScript
compare(first: string, second: string): int
```

根据配置项的排序规则，比较两个字符串。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Collator-compare(first: string, second: string): int--><!--Device-Collator-compare(first: string, second: string): int-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| first | string | 是 | 进行比较的第一个字符串。 |
| second | string | 是 | 进行比较的第二个字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 比较结果。 |

## constructor

```TypeScript
constructor()
```

使用当前系统区域创建排序对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Collator-constructor()--><!--Device-Collator-constructor()-End-->

**系统能力：** SystemCapability.Global.I18n

## constructor

```TypeScript
constructor(locale: string | Array<string>, options?: CollatorOptions)
```

根据指定的区域和配置项创建排序对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Collator-constructor(locale: string | Array<string>, options?: CollatorOptions)--><!--Device-Collator-constructor(locale: string | Array<string>, options?: CollatorOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string \| Array&lt;string&gt; | 是 | 区域ID或区域ID数组。输入是区域ID数组时，使用第一个有效的区域ID。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 创建排序对象时可设置的配置项。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：所有属性都取默认值时的配置项。 |

## resolvedOptions

```TypeScript
resolvedOptions(): CollatorOptions
```

获取创建排序对象时设置的配置项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Collator-resolvedOptions(): CollatorOptions--><!--Device-Collator-resolvedOptions(): CollatorOptions-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回排序对象的属性。 |

