# StyledString

属性字符串。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(value: string | ImageAttachment | CustomSpan, styles?: Array<StyleOptions>)
```

属性字符串的构造函数。不支持在 [loadContent()](arkts-arkui-window-window-i.md#loadcontent) 之前创建。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| [ImageAttachment](arkts-arkui-imageattachment-c.md) \| [CustomSpan](arkts-arkui-customspan-c.md) | 是 | 属性字符串文本内容。    **说明：** 当value的类型为ImageAttachment或CustomSpan时，styles参数不生效。 需要设置styles时，通过[setStyle](arkts-arkui-mutablestyledstring-c.md#setstyle)等方法实现。 |
| styles | Array&lt;[StyleOptions](arkts-arkui-styleoptions-i.md)&gt; | 否 | 属性字符串初始化选项。    **说明：** start为异常值时，按默认值0处理； 当length为异常值时，length等于属性字符串在start后的实际长度； 当StyledStringKey与StyledStringValue不匹配时，styles不生效。 |

## equals

```TypeScript
equals(other: StyledString): boolean
```

判断两个属性字符串是否相等。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| other | [StyledString](arkts-arkui-styledstring-c.md) | 是 | StyledString类型的比较对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 两个属性字符串是否相等。 |

## fromHtml

```TypeScript
static fromHtml(html: string): Promise<StyledString>
```

将HTML格式字符串转换成属性字符串，HTML标签将映射为对应的属性字符串样式（如加粗类标签映射为TextStyle、装饰类标签映射为DecorationStyle）。当前支持转换的HTML标签范围：\<p>、\&lt;span&gt;、\&lt;img&gt;、\、\&lt;strong&gt;、\&lt;b&gt;、\&lt;a&gt;、\&lt;i&gt;、\&lt;em&gt;、\&lt;s&gt;、\&lt;u&gt;、\&lt;del&gt;、\&lt;sup&gt;、\&lt;sub&gt;、\&lt;cite&gt;、\&lt;dfn&gt;、\&lt;small&gt;、\&lt;h1&gt;、\&lt;h2&gt;、\&lt;h3&gt;、\&lt;h4&gt;、\&lt;h5 &gt;、\

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| html | string | 是 | html格式的字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[StyledString](arkts-arkui-styledstring-c.md)&gt; | 属性字符串。resolve返回转换后的属性字符串；reject抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [170001](../errorcode-styled-string.md#170001-转换错误) | Convert Error. |

## getString

```TypeScript
getString(): string
```

获取字符串信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 属性字符串文本内容。 |

## getStyles

```TypeScript
getStyles(start: number, length: number, styledKey?: StyledStringKey): Array<SpanStyle>
```

获取指定范围属性字符串的样式集合。不能超出属性字符串的长度。该接口仅返回开发者设置的样式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 是 | 指定范围属性字符串的下标。 |
| length | number | 是 | 指定范围属性字符串的长度。 |
| styledKey | [StyledStringKey](arkts-arkui-styledstringkey-e.md) | 否 | 指定范围属性字符串样式的枚举值。    **说明：** 当不传入该参数时默认获取开发者设置的[StyledStringKey](arkts-arkui-styledstringkey-e.md)所有枚举值样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[SpanStyle](arkts-arkui-spanstyle-i.md)&gt; | 各样式对象的数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |

## subStyledString

```TypeScript
subStyledString(start: number, length?: number): StyledString
```

获取属性字符串的子属性字符串。不能超出属性字符串的长度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 是 | 子属性字符串开始位置的下标。 |
| length | number | 否 | 子属性字符串的长度。 不传入时默认取被查询属性字符串对象的长度与start的值的差。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [StyledString](arkts-arkui-styledstring-c.md) | 子属性字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |

## toHtml

```TypeScript
static toHtml(styledString: StyledString): string
```

将属性字符串转换成HTML格式字符串，属性字符串样式将映射为对应的HTML标签（如TextStyle映射为含style属性的span标签、ImageAttachment映射为img标签）。支持转换的属性字符串 [StyledStringKey](arkts-arkui-styledstringkey-e.md)包括：StyledStringKey.FONT、StyledStringKey.DECORATION、 StyledStringKey.LETTER_SPACING、StyledStringKey.TEXT_SHADOW、StyledStringKey.LINE_HEIGHT、StyledStringKey.IMAGE。使用方法参考 [示例12（fromHtml和toHtml互相转换）](#styledstring)。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | [StyledString](arkts-arkui-styledstring-c.md) | 是 | 要转换成HTML格式字符串的属性字符串对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | HTML格式字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |

## length

```TypeScript
readonly length: number
```

属性字符串字符的长度。  
**说明：**属性字符串中的ImageAttachment和CustomSpan长度都计为1。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
