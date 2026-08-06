# BreakIterator

提供文本换行相关的能力，包括可换行点的获取、移动和识别等。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-i18n-export class BreakIterator--><!--Device-i18n-export class BreakIterator-End-->

**系统能力：** SystemCapability.Global.I18n

## current

```TypeScript
current(): int
```

获取换行迭代器在当前处理文本中的位置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-BreakIterator-current(): int--><!--Device-BreakIterator-current(): int-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 获取换行迭代器在当前处理的文本中的位置。 |

## first

```TypeScript
first(): int
```

将换行迭代器移动到第一个可换行点。第一个可换行点总是在被处理文本的起始位置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-BreakIterator-first(): int--><!--Device-BreakIterator-first(): int-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 被处理文本的第一个可换行点的偏移量。 |

## following

```TypeScript
following(offset: int): int
```

将换行迭代器移动到指定位置后面一个可换行点。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-BreakIterator-following(offset: int): int--><!--Device-BreakIterator-following(offset: int): int-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | int | 是 | 将换行迭代器移动到文本指定位置的后面一个可换行点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 换行迭代器移动后的位置。若offset所指定位置的下一个可换行点超出了文本的范围，则返回-1。 |

## getLineBreakText

```TypeScript
getLineBreakText(): string
```

获取BreakIterator对象当前处理的文本。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-BreakIterator-getLineBreakText(): string--><!--Device-BreakIterator-getLineBreakText(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | BreakIterator对象正在处理的文本。 |

## isBoundary

```TypeScript
isBoundary(offset: int): boolean
```

判断指定位置是否为可换行点。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-BreakIterator-isBoundary(offset: int): boolean--><!--Device-BreakIterator-isBoundary(offset: int): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | int | 是 | 文本指定位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示offset指定的文本位置是一个可换行点，false表示offset指定的文本位置不是一个可换行点。 |

## last

```TypeScript
last(): int
```

将换行迭代器移动到最后一个可换行点。最后一个可换行点总是在被处理文本末尾的下一个位置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-BreakIterator-last(): int--><!--Device-BreakIterator-last(): int-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 被处理文本的最后一个可换行点的偏移量。 |

## next

```TypeScript
next(index?: int): int
```

将换行迭代器向后移动index个可换行点。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-BreakIterator-next(index?: int): int--><!--Device-BreakIterator-next(index?: int): int-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 否 | 换行迭代器将要移动的可换行点数，取值为整数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_正数表示向后移动index个可换行点，负数表示向前移动index个可换行点。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 移动index个可换行点后，当前换行迭代器在文本中的位置。 |

## previous

```TypeScript
previous(): int
```

将换行迭代器向前移动一个可换行点。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-BreakIterator-previous(): int--><!--Device-BreakIterator-previous(): int-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 移动到前一个可换行点后，当前换行迭代器在文本中的位置。 |

## setLineBreakText

```TypeScript
setLineBreakText(text: string): void
```

设置BreakIterator对象要处理的文本。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-BreakIterator-setLineBreakText(text: string): void--><!--Device-BreakIterator-setLineBreakText(text: string): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 输入文本。 |

