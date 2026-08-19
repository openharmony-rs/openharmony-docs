# StyledString

属性字符串

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class StyledString--><!--Device-unnamed-export declare class StyledString-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: string | ImageAttachment | CustomSpan, styles?: Array<StyleOptions>)
```

属性字符串的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledString-constructor(value: string | ImageAttachment | CustomSpan, styles?: Array<StyleOptions>)--><!--Device-StyledString-constructor(value: string | ImageAttachment | CustomSpan, styles?: Array<StyleOptions>)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| [ImageAttachment](arkts-arkui-styledstring-imageattachment-c.md) \| [CustomSpan](arkts-arkui-styledstring-customspan-c.md) | 是 | 属性字符串文本内容。<br/>**说明：** <br/>当value的类型为ImageAttachment或 CustomSpan时，styles参数不生效。<br/>需要设置styles时，通过[setStyle](arkts-arkui-styledstring-mutablestyledstring-c.md#setstyle)等方法实现。 |
| styles | Array&lt;[StyleOptions](arkts-arkui-styledstring-styleoptions-i.md)&gt; | 否 | 属性字符串初始化选项。<br/>**说明：** <br/>start为异常值时，按默认值0处理；<br/>当length为异常值时， length等于属性字符串在start后的实际长度；<br/>当StyledStringKey与StyledStringValue不匹配时，styles不生效。 |

## equals

```TypeScript
equals(other: StyledString): boolean
```

判断两个属性字符串是否相等。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledString-equals(other: StyledString): boolean--><!--Device-StyledString-equals(other: StyledString): boolean-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| other | [StyledString](arkts-arkui-styledstring-styledstring-c.md) | 是 | StyledString类型的比较对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 两个属性字符串是否相等。<br/>true表示相等，false表示不相等。<br/>**说明：** <br/>当属性字符串的文本及样式均一致，视为相等。<br/>不比较 [GestureStyle]{ |

## fromHtml

```TypeScript
static fromHtml(html: string): Promise<StyledString | undefined>
```

将HTML格式字符串转换成属性字符串，使用Promise异步回调。当前支持转换的HTML标签范围：\&lt;p&gt;、\&lt;span&gt;、\&lt;img&gt;、\ 、\&lt;strong&gt;、\&lt;b&gt;、\&lt;a&gt;、\&lt;i&gt;、\&lt;em&gt;、\&lt;s&gt;、\&lt;u&gt;、\&lt;del&gt;、\&lt;sup&gt;、\&lt;sub&gt;、\&lt;cite&gt;、\&lt;dfn&gt;、\&lt;small&gt;、\&lt;h1&gt;、\&lt;h2&gt;、\&lt;h3&gt;、\&lt;h4&gt;、\&lt; h5&gt;、\

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledString-static fromHtml(html: string): Promise<StyledString | undefined>--><!--Device-StyledString-static fromHtml(html: string): Promise<StyledString | undefined>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| html | string | 是 | html格式的字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[StyledString](arkts-arkui-styledstring-styledstring-c.md) \| undefined&gt; | [Promise](../../../arkts-utils/async-concurrency-overview.md#promise)对象，属性字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [170001](../errorcode-styled-string.md#170001-转换错误) | Convert Error. |

## getString

```TypeScript
getString(): string
```

获取字符串信息。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledString-getString(): string--><!--Device-StyledString-getString(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 属性字符串文本内容。<br/>**说明：** <br/>当属性字符串中包含图片或[CustomSpan]{ |

## getStyles

```TypeScript
getStyles(start: int, length: int, styledKey?: StyledStringKey): Array<SpanStyle> | undefined
```

获取指定范围属性字符串的样式集合。不能超出属性字符串的长度。 该接口仅返回开发者设置的样式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledString-getStyles(start: int, length: int, styledKey?: StyledStringKey): Array<SpanStyle> | undefined--><!--Device-StyledString-getStyles(start: int, length: int, styledKey?: StyledStringKey): Array<SpanStyle> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | 指定范围属性字符串的下标。<br/>取值范围：大于等于0。 |
| length | int | 是 | 指定范围属性字符串的长度。<br/>取值范围：大于等于0。 |
| styledKey | [StyledStringKey](arkts-arkui-styledstring-styledstringkey-e.md) | 否 | 指定范围属性字符串样式的枚举值。<br/>**说明：** <br/>当不传入该参数时默认获取开发者设置的 [StyledStringKey](arkts-arkui-styledstring-styledstringkey-e.md)所有枚举值样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[SpanStyle](arkts-arkui-styledstring-spanstyle-i.md)&gt; | 各样式对象的数组。<br/>**说明：** <br/>当指定范围属性字符串未设置任何样式，则返回空数组。<br/>当start和length越 界或者必填传入undefined时，会抛出异常；<br/>当styledKey传入异常值或undefined时，会抛出异常。<br/>当styledKey为CustomSpan时，返回的是创建CustomSpan时传入 的样式对象，即修改该样式对象也会影响实际的显示效果。 |

## subStyledString

```TypeScript
subStyledString(start: int, length?: int): StyledString | undefined
```

获取属性字符串的子属性字符串。不能超出属性字符串的长度。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledString-subStyledString(start: int, length?: int): StyledString | undefined--><!--Device-StyledString-subStyledString(start: int, length?: int): StyledString | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | 子属性字符串开始位置的下标。<br/>取值范围：大于等于0。 |
| length | int | 否 | 子属性字符串的长度。<br/>取值范围：大于等于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [StyledString](arkts-arkui-styledstring-styledstring-c.md) | 子属性字符串。<br/>**说明：** <br/>当start为合法入参时，length的默认值是被查询属性字符串对象的长度与start的值的差。&lt; br/&gt;当start和length越界或者必填传入undefined时，会抛出异常。 |

## toHtml

```TypeScript
static toHtml(styledString: StyledString): string
```

将属性字符串转换成HTML格式字符串。支持转换的属性字符串[StyledStringKey](arkts-arkui-styledstring-styledstringkey-e.md)包括：StyledStringKey.FONT、 StyledStringKey.DECORATION、StyledStringKey.LETTER_SPACING、StyledStringKey.TEXT_SHADOW、StyledStringKey.LINE_HEIGHT 、StyledStringKey.IMAGE。 使用方法参考 [示例12（fromHtml和toHtml互相转换）](../../../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#示例12fromhtml和tohtml互相转换)。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledString-static toHtml(styledString: StyledString): string--><!--Device-StyledString-static toHtml(styledString: StyledString): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | [StyledString](arkts-arkui-styledstring-styledstring-c.md) | 是 | 属性字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | HTML格式字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

