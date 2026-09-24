# RichEditorController

```TypeScript
declare class RichEditorController extends RichEditorBaseController
```

RichEditor组件的控制器，继承自[RichEditorBaseController](arkts-arkui-richeditor-comp-richeditorbasecontroller-c.md)。

> **说明：** 
> 
> 当内容的长度超过组件显示区域的高度时，调用插入接口（例如[addTextSpan](#addtextspan)、
> [addImageSpan](#addimagespan)、[addBuilderSpan](#addbuilderspan)
> 、[addSymbolSpan](#addsymbolspan)），组件会自动滚动内容使得插入内容末尾可见。

## 导入对象

```ts
controller: RichEditorController = new RichEditorController();
```

**继承/实现关系：** RichEditorController extends [RichEditorBaseController](arkts-arkui-richeditor-comp-richeditorbasecontroller-c.md)

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
> - 可通过[RichEditorBuilderSpanOptions](arkts-arkui-richeditor-comp-richeditorbuilderspanoptions-i.md)设置此builder在RichEditor中的index（一个文字为一个单位）。
> 
> - 此占位Span不可获焦，支持拖拽，支持部分通用属性，占位、删除等能力等同于ImageSpan，长度视为一个文字。
> 
> - 支持通过[bindSelectionMenu](arkts-arkui-richeditor-comp-attribute.md#bindselectionmenu)设置自定义菜单。
> 
> - 不支持通过[getSpans](#getspans)，[getSelection](#getselection)，[onSelect](arkts-arkui-richeditor-comp-attribute.md#onselect)，[aboutToDelete](arkts-arkui-richeditor-comp-attribute.md#abouttodelete)获取builderSpan信息。
> 
> - 不支持通过[updateSpanStyle](#updatespanstyle)，[updateParagraphStyle](#updateparagraphstyle)等方式更新builder。
> 
> - 对此builder节点进行复制或粘贴不生效。
> 
> - builder的布局约束由RichEditor传入，如果builder里最外层组件不设置大小，则会用RichEditor的大小作为maxSize。
> 
> - builder的手势相关事件机制与通用手势事件相同，如果builder中未设置透传，则仅有builder中的子组件响应。
> 
> - 如果组件光标闪烁，插入后光标位置更新为新插入builder的后面。
> 
> - 对[addBuilderSpan](#addbuilderspan)的节点文本，[enableDataDetector](arkts-arkui-richeditor-comp-attribute.md#enabledatadetector)、[dataDetectorConfig](arkts-arkui-richeditor-comp-attribute.md#datadetectorconfig)、[enableSelectedDataDetector](arkts-arkui-richeditor-comp-attribute.md#enableselecteddatadetector)功能不会生效。通用属性仅支持[size](arkts-arkui-common-comp-commonmethod-c.md#size)、[padding](arkts-arkui-common-comp-commonmethod-c.md#padding)、[margin](arkts-arkui-common-comp-commonmethod-c.md#margin)、[aspectRatio](arkts-arkui-common-comp-commonmethod-c.md#aspectratio)、[borderStyle](arkts-arkui-common-comp-commonmethod-c.md#borderstyle)、[borderWidth](arkts-arkui-common-comp-commonmethod-c.md#borderwidth)、[borderColor](arkts-arkui-common-comp-commonmethod-c.md#bordercolor)、[borderRadius](arkts-arkui-common-comp-commonmethod-c.md#borderradius)、[backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor)、[backgroundBlurStyle](arkts-arkui-common-comp-commonmethod-c.md#backgroundblurstyle)、[opacity](arkts-arkui-common-comp-commonmethod-c.md#opacity)、[blur](arkts-arkui-common-comp-commonmethod-c.md#blur)、[backdropBlur](arkts-arkui-common-comp-commonmethod-c.md#backdropblur)、[shadow](arkts-arkui-common-comp-commonmethod-c.md#shadow)、[grayscale](arkts-arkui-common-comp-commonmethod-c.md#grayscale)、[brightness](arkts-arkui-common-comp-commonmethod-c.md#brightness)、[saturate](arkts-arkui-common-comp-commonmethod-c.md#saturate)、[contrast](arkts-arkui-common-comp-commonmethod-c.md#contrast)、[invert](arkts-arkui-common-comp-commonmethod-c.md#invert)、[sepia](arkts-arkui-common-comp-commonmethod-c.md#sepia)、[hueRotate](arkts-arkui-common-comp-commonmethod-c.md#huerotate)、[colorBlend](arkts-arkui-common-comp-commonmethod-c.md#colorblend)、[linearGradientBlur](arkts-arkui-common-comp-commonmethod-c.md#lineargradientblur)、[clip](arkts-arkui-common-comp-commonmethod-c.md#clip)、[mask](arkts-arkui-common-comp-commonmethod-c.md#mask)、[foregroundBlurStyle](arkts-arkui-common-comp-commonmethod-c.md#foregroundblurstyle)、[accessibilityGroup](arkts-arkui-common-comp-commonmethod-c.md#accessibilitygroup)、[accessibilityText](arkts-arkui-common-comp-commonmethod-c.md#accessibilitytext)、[accessibilityDescription](arkts-arkui-common-comp-commonmethod-c.md#accessibilitydescription)、[accessibilityLevel](arkts-arkui-common-comp-commonmethod-c.md#accessibilitylevel)、[sphericalEffect](arkts-arkui-common-comp-commonmethod-c.md#sphericaleffect)、[lightUpEffect](arkts-arkui-common-comp-commonmethod-c.md#lightupeffect)、[pixelStretchEffect](arkts-arkui-common-comp-commonmethod-c.md#pixelstretcheffect)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | 是 | 自定义布局内容，用于在RichEditor中创建BuilderSpan占位组件。 |
| options | [RichEditorBuilderSpanOptions](arkts-arkui-richeditor-comp-richeditorbuilderspanoptions-i.md) | 否 | builder选项。当需要设置builder的偏移位置或无障碍属性时传入此参数；省略时，builder添加到所有内容末尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 添加完成的builderSpan在所有Span中的索引位置。 |

## addImageSpan

```TypeScript
addImageSpan(value: PixelMap | ResourceStr, options?: RichEditorImageSpanOptions): number
```

添加图片内容。如果组件光标闪烁，插入后光标位置更新为新插入图片的后面。当controller未绑定组件或绑定controller的组件被释放时，该接口调用无效。

该接口为同步接口，在弱网环境下，直接添加网络图片可能会阻塞UI线程造成冻屏问题。不建议直接添加网络图片。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 图片内容。 |
| options | [RichEditorImageSpanOptions](arkts-arkui-richeditor-comp-richeditorimagespanoptions-i.md) | 否 | 图片选项。<br>当需要设置图片样式、偏移位置或段落样式时传入此参数；不传入时，图片将使用默认样式插入到内容末尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 添加完成的ImageSpan在所有Span中的索引位置。 |

## addRichEditorBuilderSpan

```TypeScript
addRichEditorBuilderSpan(value: RichEditorBuilderSpan, info?: BuilderSpanInfo): number
```

在**RichEditor**中添加自定义布局（BuilderSpan），提供身份识别与生命周期感知能力。

> **说明：** 
> 
> - BuilderSpan对象中的[onAttach](arkts-arkui-richeditor-comp-richeditorbuilderspan-i.md#onattach)和[onDetach](arkts-arkui-richeditor-comp-richeditorbuilderspan-i.md#ondetach)回调接收一个[BuilderSpanInfo](arkts-arkui-richeditor-comp-builderspaninfo-i.md)对象，包含span的id和offset。
> 
> - 当**RichEditor**组件使用[RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md)构造时，不支持此接口。
> 
> - 撤销/重做不会还原BuilderSpan对象。通过撤销还原时，被移除的BuilderSpan会降级为空格文本Span。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorBuilderSpan](arkts-arkui-richeditor-comp-richeditorbuilderspan-i.md) | 是 | BuilderSpan对象，包含构造器、生命周期回调和无障碍配置。 |
| info | [BuilderSpanInfo](arkts-arkui-richeditor-comp-builderspaninfo-i.md) | 否 | BuilderSpan的身份与位置信息。**info.id**用于标识BuilderSpan，**info.offset**用于指定插入位置。省略时，BuilderSpan追加到末尾且id为undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 添加完成的builderSpan在所有Span中的索引位置。 |

## addSymbolSpan

```TypeScript
addSymbolSpan(value: Resource, options?: RichEditorSymbolSpanOptions ): number
```

在RichEditor中添加图标小符号（SymbolSpan）。如果组件光标闪烁，插入后光标位置更新为新插入SymbolSpan的后面。

SymbolSpan暂不支持手势、复制操作和拖拽处理。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Resource](../arkts-apis/arkts-arkui-resource-t.md) | 是 | SymbolSpan图标资源引用，用于指定系统预置或自定义的Symbol图标。 |
| options | [RichEditorSymbolSpanOptions](arkts-arkui-richeditor-comp-richeditorsymbolspanoptions-i.md) | 否 | symbol选项。<br>当需要设置SymbolSpan的偏移位置或样式时传入此参数；不传入时，SymbolSpan将使用默认样式插入到内容末尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 添加完成的SymbolSpan在所有Span中的索引位置。 |

## addTextSpan

```TypeScript
addTextSpan(content: ResourceStr, options?: RichEditorTextSpanOptions): number
```

添加文本内容。如果组件光标闪烁，插入后光标位置更新为新插入文本的后面。当controller未绑定组件或绑定controller的组件被释放时，该接口调用无效。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 文本内容。<br>从API version 20开始，支持Resource类型。<br>**适用版本：** 20 |
| options | [RichEditorTextSpanOptions](arkts-arkui-richeditor-comp-richeditortextspanoptions-i.md) | 否 | 文本选项。<br>当需要设置偏移位置、文本样式、段落样式等信息时传入此参数；不传入时，文本将使用默认样式插入到内容末尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 添加完成的TextSpan在所有Span中的索引位置。 |

## deleteSpans

```TypeScript
deleteSpans(value?: RichEditorRange): void
```

删除指定范围内的文本和图片。当controller未绑定组件或绑定controller的组件被释放时，该接口调用无效。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-richeditor-comp-richeditorrange-i.md) | 否 | 删除范围。省略时，删除所有文本和图片。 |

## fromStyledString

```TypeScript
fromStyledString(value: StyledString): Array<RichEditorSpan>
```

将属性字符串转换为span信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [StyledString](../arkts-apis/arkts-arkui-styledstring-c.md) | 是 | 转换前的属性字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[RichEditorSpan](arkts-arkui-richeditor-comp-richeditorspan-t.md)&gt; | 将属性字符串解析后得到的文本和图片Span信息，可用于查询属性字符串中各Span的内容、样式和位置。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | The parameter check failed. |

## getParagraphs

```TypeScript
getParagraphs(value?: RichEditorRange): Array<RichEditorParagraphResult>
```

获取指定范围的段落信息。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-richeditor-comp-richeditorrange-i.md) | 否 | 需要获取段落的范围。<br>省略时，获取所有段落信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[RichEditorParagraphResult](arkts-arkui-richeditor-comp-richeditorparagraphresult-i.md)&gt; | 选中范围内的段落信息，包含各段落的样式和起始结束位置，可用于查询段落排版属性或进行段落样式更新。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## getRichEditorBuilderSpans

```TypeScript
getRichEditorBuilderSpans(value?: RichEditorRange): Array<BuilderSpanInfo>
```

获取指定范围内BuilderSpan的身份与位置信息。

> **说明：** 
> 
> - 当**RichEditor**组件使用[RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md)构造时，不支持此接口。
> 
> - 通过接口[addBuilderSpan](#addbuilderspan)创建的BuilderSpan，返回的[BuilderSpanInfo](arkts-arkui-richeditor-comp-builderspaninfo-i.md)中id为**undefined**（匿名）。
> 
> - 返回的[BuilderSpanInfo](arkts-arkui-richeditor-comp-builderspaninfo-i.md)中的**offset**字段反映当前实际偏移位置，随文本内容变化动态更新。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-richeditor-comp-richeditorrange-i.md) | 否 | 目标BuilderSpan的范围。<br>省略时，返回所有BuilderSpan信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[BuilderSpanInfo](arkts-arkui-richeditor-comp-builderspaninfo-i.md)&gt; | BuilderSpan身份与位置信息数组。<br>当controller未绑定组件或绑定controller的组件被释放时，返回**undefined**。 |

## getSelection

```TypeScript
getSelection(): RichEditorSelection
```

获取选中内容的范围和span信息。未选中时，返回光标所在span信息。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RichEditorSelection](arkts-arkui-richeditor-comp-richeditorselection-i.md) | 选中区域起始/结束位置及选中文本和图片的详细信息。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## getSpans

```TypeScript
getSpans(value?: RichEditorRange): Array<RichEditorImageSpanResult | RichEditorTextSpanResult>
```

获取span信息。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-richeditor-comp-richeditorrange-i.md) | 否 | 需要获取span的范围。<br>省略时，获取所有span信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[RichEditorImageSpanResult](arkts-arkui-richeditor-comp-richeditorimagespanresult-i.md) &#124; [RichEditorTextSpanResult](arkts-arkui-richeditor-comp-richeditortextspanresult-i.md)&gt; | 指定范围内的文本和图片Span详细信息，包含各Span的位置、内容、样式等属性，可用于查询和操作组件内的文本与图片内容。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## toStyledString

```TypeScript
toStyledString(value: RichEditorRange): StyledString
```

将给定范围的组件内容转换成属性字符串，SymbolSpan和BuilderSpan不支持转换。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-richeditor-comp-richeditorrange-i.md) | 是 | 需要获取的范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [StyledString](../arkts-apis/arkts-arkui-styledstring-c.md) | 组件指定范围内容转换后的属性字符串，可用于跨组件传递富文本内容或进行样式编辑操作。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | The parameter check failed. |

## updateParagraphStyle

```TypeScript
updateParagraphStyle(value: RichEditorParagraphStyleOptions): void
```

更新段落的样式。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorParagraphStyleOptions](arkts-arkui-richeditor-comp-richeditorparagraphstyleoptions-i.md) | 是 | 段落的样式选项信息。 |

## updateSpanStyle

```TypeScript
updateSpanStyle(value: RichEditorUpdateTextSpanStyleOptions | RichEditorUpdateImageSpanStyleOptions | RichEditorUpdateSymbolSpanStyleOptions): void
```

更新文本、图片或SymbolSpan样式。

若只更新了一个Span的部分内容，则会根据更新部分、未更新部分将该Span拆分为多个Span。当controller未绑定组件或绑定controller的组件被释放时，该接口调用无效。

使用该接口更新文本、图片或SymbolSpan样式时默认不会关闭自定义文本选择菜单。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorUpdateTextSpanStyleOptions](arkts-arkui-richeditor-comp-richeditorupdatetextspanstyleoptions-i.md) &#124; [RichEditorUpdateImageSpanStyleOptions](arkts-arkui-richeditor-comp-richeditorupdateimagespanstyleoptions-i.md) &#124; [RichEditorUpdateSymbolSpanStyleOptions](arkts-arkui-richeditor-comp-richeditorupdatesymbolspanstyleoptions-i.md) | 是 | 文本、图片或SymbolSpan的样式选项信息。<br>**适用版本：** 11 |
