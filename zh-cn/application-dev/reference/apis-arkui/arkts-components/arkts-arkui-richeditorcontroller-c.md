# RichEditorController

RichEditor组件的控制器，继承自[RichEditorBaseController](arkts-arkui-richeditorbasecontroller-c.md)。

> **说明：**
>
> 当内容的长度超过组件显示区域的高度时，调用插入接口（例如[addTextSpan](arkts-arkui-richeditorcontroller-c.md#addtextspan-1)、
> [addImageSpan](arkts-arkui-richeditorcontroller-c.md#addimagespan-1)、[addBuilderSpan](arkts-arkui-richeditorcontroller-c.md#addbuilderspan-1)
> 、[addSymbolSpan](arkts-arkui-richeditorcontroller-c.md#addsymbolspan-1)），组件会自动滚动内容使得插入内容末尾可见。

**继承/实现关系：** RichEditorController extends [RichEditorBaseController](arkts-arkui-richeditorbasecontroller-c.md)

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addBuilderSpan

```TypeScript
addBuilderSpan(value: CustomBuilder, options?: RichEditorBuilderSpanOptions): number
```

在RichEditor中添加用户自定义布局（BuilderSpan）。

> **说明：**
>
> - RichEditor组件添加占位Span，占位Span调用系统的measure方法计算真实的长宽和位置。
>
> - 可通过[RichEditorBuilderSpanOptions](arkts-arkui-richeditorbuilderspanoptions-i.md)设置此builder在RichEditor中的index（一个文字为一个单位）。
>
> - 此占位Span不可获焦，支持拖拽，支持部分通用属性，占位、删除等能力等同于ImageSpan，长度视为一个文字。
>
> - 支持通过[bindSelectionMenu](RichEditorAttribute.bindSelectionMenu)设置自定义菜单。
>
> - 不支持通过[getSpans](arkts-arkui-richeditorcontroller-c.md#getspans-1)，[getSelection](arkts-arkui-richeditorcontroller-c.md#getselection-1)，
> [onSelect](RichEditorAttribute.onSelect)，[aboutToDelete](RichEditorAttribute.aboutToDelete)获取
> builderSpan信息。
>
> - 不支持通过[updateSpanStyle](arkts-arkui-richeditorcontroller-c.md#updatespanstyle-1)，
> [updateParagraphStyle](arkts-arkui-richeditorcontroller-c.md#updateparagraphstyle-1)等方式更新builder。
>
> - 对此builder节点进行复制或粘贴不生效。
>
> - builder的布局约束由RichEditor传入，如果builder里最外层组件不设置大小，则会用RichEditor的大小作为maxSize。
>
> - builder的手势相关事件机制与通用手势事件相同，如果builder中未设置透传，则仅有builder中的子组件响应。
>
> - 如果组件光标闪烁，插入后光标位置更新为新插入builder的后面。

通用属性仅支持[size](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#size)、
[padding](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#padding)、
[margin](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#margin)、
[aspectRatio](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-layout-constraints.md#aspectratio)、
[borderStyle](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#borderstyle)、
[borderWidth](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#borderwidth)、
[borderColor](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#bordercolor)、
[borderRadius](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#borderradius)、
[backgroundColor](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor)、
[backgroundBlurStyle](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundblurstyle9)
、[opacity](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)、
[blur](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#blur)、
[backdropBlur](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backdropblur)、
[shadow](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#shadow)、
[grayscale](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#grayscale)、
[brightness](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#brightness)、
[saturate](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#saturate)、
[contrast](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#contrast)、
[invert](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#invert)、
[sepia](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#sepia)、
[hueRotate](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#huerotate)、
[colorBlend](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#colorblend)、
[linearGradientBlur](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#lineargradientblur12)
、[clip](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-sharp-clipping.md#clip12)、
[mask](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-sharp-clipping.md#mask12)、
[foregroundBlurStyle](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-foreground-blur-style.md#foregroundblurstyle)
、
[accessibilityGroup](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitygroup)
、
[accessibilityText](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitytext)
、
[accessibilityDescription](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitydescription)
、
[accessibilityLevel](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitylevel)
、
[sphericalEffect](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#sphericaleffect12)
、[lightUpEffect](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#lightupeffect12)、
[pixelStretchEffect](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#pixelstretcheffect12)
。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | CustomBuilder | 是 | 自定义组件。 |
| options | RichEditorBuilderSpanOptions | 否 | builder选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 添加完成的builderSpan在所有Span中的索引位置。 |

## addImageSpan

```TypeScript
addImageSpan(value: PixelMap | ResourceStr, options?: RichEditorImageSpanOptions): number
```

添加图片内容，如果组件光标闪烁，插入后光标位置更新为新插入图片的后面。

该接口为同步接口，在弱网环境下，直接添加网络图片可能会阻塞UI线程造成冻屏问题。不建议直接添加网络图片。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | PixelMap \| ResourceStr | 是 | 图片内容。 |
| options | RichEditorImageSpanOptions | 否 | 图片选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 添加完成的ImageSpan在所有Span中的索引位置。 |

## addSymbolSpan

```TypeScript
addSymbolSpan(value: Resource, options?: RichEditorSymbolSpanOptions ): number
```

在RichEditor中添加图标小符号（SymbolSpan），如果组件光标闪烁，插入后光标位置更新为新插入SymbolSpan的后面。

暂不支持手势、复制、拖拽处理。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Resource | 是 | symbol资源信息。 |
| options | RichEditorSymbolSpanOptions | 否 | symbol选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 添加完成的SymbolSpan在所有Span中的索引位置。 |

## addTextSpan

```TypeScript
addTextSpan(content: ResourceStr, options?: RichEditorTextSpanOptions): number
```

添加文本内容，如果组件光标闪烁，插入后光标位置更新为新插入文本的后面。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ResourceStr | 是 | 文本内容。 <br>从API version 20开始，支持Resource类型。<br>**起始版本：** 20 |
| options | RichEditorTextSpanOptions | 否 | 文本选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 添加完成的TextSpan在所有Span中的索引位置。 |

## deleteSpans

```TypeScript
deleteSpans(value?: RichEditorRange): void
```

删除指定范围内的文本和图片。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | RichEditorRange | 否 | 删除范围。省略时，删除所有文本和图片。 |

## fromStyledString

```TypeScript
fromStyledString(value: StyledString): Array<RichEditorSpan>
```

将属性字符串转换为span信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | StyledString | 是 | 转换前的属性字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;RichEditorSpan&gt; | 文本和图片Span信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. |

## getParagraphs

```TypeScript
getParagraphs(value?: RichEditorRange): Array<RichEditorParagraphResult>
```

获取指定范围的段落信息。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | RichEditorRange | 否 | 需要获取段落的范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;RichEditorParagraphResult&gt; | 选中段落的信息。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## getSelection

```TypeScript
getSelection(): RichEditorSelection
```

获取选中内容的范围和span信息。未选中时，返回光标所在span信息。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RichEditorSelection | 选中内容信息。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## getSpans

```TypeScript
getSpans(value?: RichEditorRange): Array<RichEditorImageSpanResult | RichEditorTextSpanResult>
```

获取span信息。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | RichEditorRange | 否 | 需要获取span范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;RichEditorImageSpanResult \| RichEditorTextSpanResult&gt; | 文本和图片Span信息。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## toStyledString

```TypeScript
toStyledString(value: RichEditorRange): StyledString
```

将给定范围的组件内容转换成属性字符串，SymbolSpan和BuilderSpan不支持转换。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | RichEditorRange | 是 | 需要获取的范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| StyledString | 转换后的属性字符串 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. |

## updateParagraphStyle

```TypeScript
updateParagraphStyle(value: RichEditorParagraphStyleOptions): void
```

更新段落的样式。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | RichEditorParagraphStyleOptions | 是 | 段落的样式选项信息。 |

## updateSpanStyle

```TypeScript
updateSpanStyle(value: RichEditorUpdateTextSpanStyleOptions | RichEditorUpdateImageSpanStyleOptions | RichEditorUpdateSymbolSpanStyleOptions): void
```

更新文本、图片或SymbolSpan样式。

若只更新了一个Span的部分内容，则会根据更新部分、未更新部分将该Span拆分为多个Span。

使用该接口更新文本、图片或SymbolSpan样式时默认不会关闭自定义文本选择菜单。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | RichEditorUpdateTextSpanStyleOptions \| RichEditorUpdateImageSpanStyleOptions \| RichEditorUpdateSymbolSpanStyleOptions | 是 | 文本、图片或SymbolSpan的样式选项信息。<br>**起始版本：** 11 |

