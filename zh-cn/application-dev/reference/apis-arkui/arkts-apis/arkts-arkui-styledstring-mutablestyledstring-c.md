# MutableStyledString

继承于[StyledString](arkts-arkui-styledstring-styledstring-c.md#StyledString)类。 > **以下接口异常入参处理统一说明：** > > 当start和length越界或者必填传入undefined时，会抛出异常； > > 当styledKey和styledValue传入异常值或者两者对应关系不匹配时，会抛出异常。

**继承/实现关系：** MutableStyledString extends [StyledString](arkts-arkui-styledstring-styledstring-c.md#StyledString)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class MutableStyledString--><!--Device-unnamed-export declare class MutableStyledString-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## appendStyledString

```TypeScript
appendStyledString(other: StyledString): void
```

在末尾位置追加新的属性字符串。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MutableStyledString-appendStyledString(other: StyledString): void--><!--Device-MutableStyledString-appendStyledString(other: StyledString): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| other | [StyledString](arkts-arkui-styledstring-styledstring-c.md) | 是 | 新的属性字符串对象。 |

## clearStyles

```TypeScript
clearStyles(): void
```

清除属性字符串对象的所有样式。 被清空样式类型对象属性使用的是对应[Text](../../../reference/apis-arkui/arkui-ts/ts-basic-components-text.md)组件属性的设置值，若Text组件未设置值， 则使用对应Text组件属性的默认值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MutableStyledString-clearStyles(): void--><!--Device-MutableStyledString-clearStyles(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: string | ImageAttachment | CustomSpan, styles?: Array<StyleOptions>)
```

可变属性字符串的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MutableStyledString-constructor(value: string | ImageAttachment | CustomSpan, styles?: Array<StyleOptions>)--><!--Device-MutableStyledString-constructor(value: string | ImageAttachment | CustomSpan, styles?: Array<StyleOptions>)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| [ImageAttachment](arkts-arkui-styledstring-imageattachment-c.md) \| [CustomSpan](arkts-arkui-styledstring-customspan-c.md) | 是 | 属性字符串文本内容。&lt;br/&gt;**说明：** &lt;br/&gt;当value的类型为ImageAttachment或 CustomSpan时，styles参数不生效。&lt;br/&gt;需要设置styles时，通过[setStyle](#setStyle)等方法实现。 |
| styles | Array&lt;[StyleOptions](arkts-arkui-styledstring-styleoptions-i.md)&gt; | 否 | 属性字符串初始化选项。&lt;br/&gt;**说明：** &lt;br/&gt;start为异常值时，按默认值0处理；&lt;br/&gt;当length为异常值时， length等于属性字符串在start后的实际长度；&lt;br/&gt;当StyledStringKey与StyledStringValue不匹配时，styles不生效。 |

## insertString

```TypeScript
insertString(start: int, other: string): void
```

插入字符串。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MutableStyledString-insertString(start: int, other: string): void--><!--Device-MutableStyledString-insertString(start: int, other: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | 插入位置的下标。&lt;br/&gt;取值范围：大于等于0。 |
| other | string | 是 | 插入的新文本内容。&lt;br/&gt;**说明：** &lt;br/&gt;插入的字符串使用的是start-1位置字符的样式。若start-1位置字符未设置样式，则使用start位置字符样式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## insertStyledString

```TypeScript
insertStyledString(start: int, other: StyledString): void
```

在指定位置插入新的属性字符串。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MutableStyledString-insertStyledString(start: int, other: StyledString): void--><!--Device-MutableStyledString-insertStyledString(start: int, other: StyledString): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | 开始插入位置的下标。&lt;br/&gt;取值范围：大于等于0。 |
| other | [StyledString](arkts-arkui-styledstring-styledstring-c.md) | 是 | 新的属性字符串对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## removeString

```TypeScript
removeString(start: int, length: int): void
```

移除指定范围的字符串。 当属性字符串中包含图片或[CustomSpan](arkts-arkui-styledstring-customspan-c.md#CustomSpan)时，同样生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MutableStyledString-removeString(start: int, length: int): void--><!--Device-MutableStyledString-removeString(start: int, length: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | 指定范围的下标。&lt;br/&gt;取值范围：大于等于0。 |
| length | int | 是 | 指定范围的长度。&lt;br/&gt;取值范围：大于等于0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## removeStyle

```TypeScript
removeStyle(start: int, length: int, styledKey: StyledStringKey): void
```

清除指定范围内容的指定类型样式。 被清空样式类型对象属性使用的是对应[Text](../../../reference/apis-arkui/arkui-ts/ts-basic-components-text.md)组件属性的设置值，若Text组件未设置值， 则使用对应Text组件属性的默认值。 当属性字符串中包含图片时，同样生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MutableStyledString-removeStyle(start: int, length: int, styledKey: StyledStringKey): void--><!--Device-MutableStyledString-removeStyle(start: int, length: int, styledKey: StyledStringKey): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | 指定范围开始位置的下标。&lt;br/&gt;取值范围：大于等于0。 |
| length | int | 是 | 指定范围的长度。&lt;br/&gt;取值范围：大于等于0。 |
| styledKey | [StyledStringKey](arkts-arkui-styledstring-styledstringkey-e.md) | 是 | 样式类型枚举值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## removeStyles

```TypeScript
removeStyles(start: int, length: int): void
```

清除指定范围内容的所有样式。 被清空样式类型对象属性使用的是对应[Text](../../../reference/apis-arkui/arkui-ts/ts-basic-components-text.md)组件属性的设置值，若Text组件未设置值， 则使用对应Text组件属性的默认值。 当属性字符串中包含图片时，同样生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MutableStyledString-removeStyles(start: int, length: int): void--><!--Device-MutableStyledString-removeStyles(start: int, length: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | 指定范围开始位置的下标。&lt;br/&gt;取值范围：大于等于0。 |
| length | int | 是 | 指定范围的长度。&lt;br/&gt;取值范围：大于等于0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## replaceString

```TypeScript
replaceString(start: int, length: int, other: string): void
```

替换指定范围的字符串。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MutableStyledString-replaceString(start: int, length: int, other: string): void--><!--Device-MutableStyledString-replaceString(start: int, length: int, other: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | 指定范围的下标。&lt;br/&gt;取值范围：大于等于0。 |
| length | int | 是 | 指定范围的长度。&lt;br/&gt;取值范围：大于等于0。 |
| other | string | 是 | 替换的新文本内容。&lt;br/&gt;**说明：** &lt;br/&gt;替换的字符串使用的是start位置字符的样式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## replaceStyle

```TypeScript
replaceStyle(spanStyle: SpanStyle): void
```

替换指定范围内容为指定类型新样式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MutableStyledString-replaceStyle(spanStyle: SpanStyle): void--><!--Device-MutableStyledString-replaceStyle(spanStyle: SpanStyle): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| spanStyle | [SpanStyle](arkts-arkui-styledstring-spanstyle-i.md) | 是 | 样式对象。&lt;br/&gt;**说明：** &lt;br/&gt;默认清空原有样式，替换为新样式。&lt;br/&gt;当SpanStyle的styledKey为IMAGE或 CUSTOM_SPAN时，只有当start的位置当前是image或CustomSpan且长度为1，才会生效，其余情况无效果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## replaceStyledString

```TypeScript
replaceStyledString(start: int, length: int, other: StyledString): void
```

替换指定范围为新的属性字符串。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MutableStyledString-replaceStyledString(start: int, length: int, other: StyledString): void--><!--Device-MutableStyledString-replaceStyledString(start: int, length: int, other: StyledString): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | 指定范围开始位置的下标。&lt;br/&gt;取值范围：大于等于0。 |
| length | int | 是 | 指定范围的长度。&lt;br/&gt;取值范围：大于等于0。 |
| other | [StyledString](arkts-arkui-styledstring-styledstring-c.md) | 是 | 新的属性字符串对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## setStyle

```TypeScript
setStyle(spanStyle: SpanStyle): void
```

为指定范围内容设置指定类型新样式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MutableStyledString-setStyle(spanStyle: SpanStyle): void--><!--Device-MutableStyledString-setStyle(spanStyle: SpanStyle): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| spanStyle | [SpanStyle](arkts-arkui-styledstring-spanstyle-i.md) | 是 | 样式对象。&lt;br/&gt;默认不清空原有样式，叠加新样式。如果StyledStringValue类型相同，则新样式将覆盖旧样式。&lt;br/&gt;当SpanStyle的 styledKey为IMAGE或CUSTOM_SPAN时，只有当start的位置当前是image或CustomSpan且长度为1，才会生效，其余情况无效果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. |

