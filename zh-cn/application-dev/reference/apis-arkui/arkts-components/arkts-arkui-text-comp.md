# Text

Text组件用于显示文本内容，支持设置字体样式、文本对齐、行高、装饰线等属性，支持图文混排、文本选择、文本识别等功能，适用于需要展示文本信息的各类应用场景。

## 子组件

可以包含Span、ImageSpan、SymbolSpan和ContainerSpan子组件。

> **说明：** 
> 
> 使用子组件实现
> [图文混排](../../../ui/arkts-text-image-layout.md)场景。

## Text

```TypeScript
Text(content?: string | Resource, value?: TextOptions)
```

定义文本组件构造函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | 否 | 文本内容。当需要直接显示文本内容时传入此参数。包含子组件Span或设置了属性字符串时，该参数不生效。<br>默认值：' '<br>**说明：** <br>显示内容的优先级：属性字符串&gt;Span&gt;Text的文本内容。 |
| value | [TextOptions](arkts-arkui-textoptions-i.md) | 否 | 文本组件初始化选项，用于配置文本控制器。当需要使用TextController的功能控制文本内容和选择时，传入此参数。<br>默认值：不设置时，不使用文本控制器。<br> |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [TextMarqueeOptions](arkts-arkui-textmarqueeoptions-i.md) | Marquee初始化参数。 |
| [TextOptions](arkts-arkui-textoptions-i.md) | Text初始化参数。 |
| [TextOverflowOptions](arkts-arkui-textoverflowoptions-i.md) | 文本超长显示方式对象。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [MarqueeStartPolicy](arkts-arkui-marqueestartpolicy-e.md) | Marquee的滚动方式，可选择默认持续滚动或条件触发滚动。 |
| [MarqueeState](arkts-arkui-marqueestate-e.md) | Marquee状态回调的返回值。 |
| [MarqueeUpdatePolicy](arkts-arkui-marqueeupdatepolicy-e.md) | 跑马灯组件属性更新后，跑马灯的滚动策略。 |
| [TextResponseType](arkts-arkui-textresponsetype-e.md) | 选择菜单的响应类型。 |
| [TextSpanType](arkts-arkui-textspantype-e.md) | Span类型信息。 |

## 示例

```TypeScript
### 示例1（设置文本布局）

该示例通过[textAlign](#textalign)、[lineHeight](#lineheight)、[baselineOffset](#baselineoffset)、[halfLeading](#halfleading12)（从API version 12开始）属性展示了文本布局的效果。


```

```TypeScript
### 示例2（设置文本样式）

该示例通过[decoration](#decoration)、[letterSpacing](#letterspacing)、[textCase](#textcase)、[fontFamily](#fontfamily)、[textShadow](#textshadow10)（从API version 10开始）、[fontStyle](#fontstyle)、[textIndent](#textindent10)（从API version 10开始）、[fontWeight](#fontweight12)（从API version 12开始，支持设置字重无极调节配置项）属性展示了不同样式的文本效果。


```

```TypeScript
### 示例3（设置文本超长省略）

该示例通过[maxLines](#maxlines)、[textOverflow](#textoverflow)、[ellipsisMode](#ellipsismode11)属性展示了文本超长省略以及调整省略位置的效果，通过MULTILINE_START和MULTILINE_CENTER两种类型实现了单行文本和多行文本场景下的省略号在行首和行中的效果。同时，可以通过[marqueeOptions](#marqueeoptions18)配置跑马灯模式下的配置项以及跑马灯动画进行到特定的阶段时，触发的回调[onMarqueeStateChange](arkts-arkui-text-comp-attribute.md#onmarqueestatechange)。

从API version 11开始，通过[ellipsisMode](#ellipsismode11)属性设置文本超长时的显示方式。

从API version 18开始，新增[marqueeOptions](#marqueeoptions18)属性设置跑马灯模式下的配置项，同时新增回调[onMarqueeStateChange](arkts-arkui-text-comp-attribute.md#onmarqueestatechange)。

从API version 24开始，[EllipsisMode](ts-appendix-enums.md#ellipsismode11)新增了MULTILINE_START和MULTILINE_CENTER枚举。


```

```TypeScript
### 示例4（设置文本断行及折行）

该示例通过[wordBreak](#wordbreak11)（从API version 11开始）、[lineBreakStrategy](#linebreakstrategy12)（从API version 12开始）、[clip](ts-universal-attributes-sharp-clipping.md#clip12)属性展示了文本在不同断行、折行规则下的效果以及文本超长时是否截断。


```

```TypeScript
### 示例5（设置文本选中和复制）

该示例通过[selection](#selection11)（从API version 11开始）、[onCopy](#oncopy11)（从API version 11开始）、[draggable](#draggable9)（从API version 9开始）、[caretColor](#caretcolor14)（从API version 14开始）、[selectedBackgroundColor](#selectedbackgroundcolor14)（从API version 14开始）、[onWillCopy](#onwillcopy)接口展示了文本选中、触发复制回调、设置文本选中可拖拽、修改手柄和选中颜色的效果以及如何拦截系统复制。

从API版本26.0.0开始，新增[onWillCopy](#onwillcopy)接口。


```

```TypeScript
### 示例6（设置文本自适应和缩放倍数限制范围）

该示例通过[heightAdaptivePolicy](#heightadaptivepolicy10)（从API version 10开始）属性展示文本自适应效果以及通过[minFontScale](#minfontscale12)（从API version 12开始）、[maxFontScale](#maxfontscale12)（从API version 12开始）展示设置字体缩放倍数限制范围。


```

```TypeScript
### 示例7（设置文本识别）

从API version 11开始，该示例通过[enableDataDetector](#enabledatadetector11)、[dataDetectorConfig](#datadetectorconfig11)接口实现了文本识别的功能。当[enableDataDetector](#enabledatadetector11)设为true且不设置[dataDetectorConfig](#datadetectorconfig11)时，系统会识别所有实体类型，并将识别实体的字体颜色改为蓝色、添加蓝色下划线。


```

```TypeScript
### 示例8（文本绑定自定义菜单）

从API version 11开始，该示例通过[bindSelectionMenu](#bindselectionmenu11)、[onTextSelectionChange](#ontextselectionchange11)、[closeSelectionMenu](#closeselectionmenu11)接口实现了文本绑定自定义菜单的功能。


```

```TypeScript
### 示例9（设置文本特性与行间距）

从API version 12开始，该示例通过[fontFeature](#fontfeature12)、[lineSpacing](#linespacing12)接口展示了设置文本特性与行间距的效果，同时，配置[LineSpacingOptions](ts-text-common.md#linespacingoptions20对象说明)中的onlyBetweenLines（从API version 20开始）属性，可以设置文本的行间距，是否仅在行与行之间生效。


```

```TypeScript
### 示例10（获取文本信息）

从API version 12开始，该示例通过[getLayoutManager](#getlayoutmanager12)接口调用文本的布局管理对象获取文本信息，同时，[LayoutManager](ts-text-common.md#layoutmanager12)中的[getRectsForRange](./ts-text-common.md#getrectsforrange14)（从API version 14开始）接口可以获取指定矩形宽度样式和高度样式下，文本中任意区间范围内字符或占位符的绘制区域信息。


```

```TypeScript
### 示例11（实现键盘框选文本）

从API version 12开始，该示例通过[textSelectable](arkts-arkui-text-comp-attribute.md#textselectable)属性实现了设置TextSelectMode.SELECTABLE_FOCUSABLE时能够触发键盘框选文本功能。


```

```TypeScript
### 示例12（文本扩展自定义菜单）

从API version 12开始，该示例通过[editMenuOptions](#editmenuoptions12)接口实现了文本设置自定义菜单扩展项的文本内容、图标以及回调的功能，同时，可以在[onPrepareMenu](ts-text-common.md#属性-1)（从API version 20开始）回调中，进行菜单数据的设置。


```

```TypeScript
### 示例13（配置隐私隐藏）

从API version 12开始，该示例通过[privacySensitive](#privacysensitive12)属性展示了文本如何配置隐私隐藏的效果，实际显示需要卡片框架支持。


```

```TypeScript
### 示例14（设置中西文自动间距）

从API version 20开始，该示例通过[enableAutoSpacing](#enableautospacing20)属性设置中西文自动间距。


```

```TypeScript
### 示例15（文本颜色按线性或径向渐变）

从API version 20开始，该示例通过[shaderStyle](#shaderstyle20)接口实现了对Text组件显示为渐变色和纯色的功能。


```

```TypeScript
### 示例16（配置除去行尾空格）

从API version 20开始，该示例通过[optimizeTrailingSpace](arkts-arkui-text-comp-attribute.md#optimizetrailingspace)属性展示了文本如何配置除去行尾空格的效果，一般需要与对齐功能搭配使用，实际显示需要字体引擎支持。


```

```TypeScript
### 示例17（文本垂直对齐）

从API version 20开始，该示例通过[textVerticalAlign](#textverticalalign20)属性展示了文本如何设置文本垂直对齐效果。


```

```TypeScript
### 示例18（文本翻牌动效）

从API version 20开始，该示例通过[contentTransition](#contenttransition20)属性展示了数字翻牌效果。


```

```TypeScript
### 示例19（文本内容区垂直对齐）

从API version 21开始，该示例通过[textContentAlign](#textcontentalign21)属性展示了当文本内容区高度大于组件高度时文本内容区的垂直对齐。


```

```TypeScript
### 示例20（倍数行高和最大最小行高）

从API version 22开始，该示例通过[lineHeightMultiple](#lineheightmultiple22)属性展示了使用倍数模式设置行高，同时通过[minLineHeight](arkts-arkui-text-comp-attribute.md#minlineheight)和[maxLineHeight](arkts-arkui-text-comp-attribute.md#maxlineheight)来设置最小和最大行高值。


```

```TypeScript
### 示例21（文本设置显示最小行数）

从API version 22开始，该示例使用[minLines](#minlines22)属性设置文本显示的最小行数。


```

```TypeScript
### 示例22（设置文本选择区域并高亮显示）

从API version 23开始，该示例使用[TextController](arkts-arkui-textcontroller-c.md)中的[setTextSelection](#settextselection23)设置文本选择区域并高亮显示。


```

```TypeScript
### 示例23（设置行首标点符号压缩和行尾标点符号悬挂）

本示例通过[compressLeadingPunctuation](#compressleadingpunctuation23)接口设置行首标点符号压缩，通过[punctuationOverflow](#punctuationoverflow)设置行尾标点符号悬挂。

左侧有间距的标点符号位于行首时，标点会直接压缩间距至左侧边界。

文本自动换行后，剩余内容（含标点符号）需要能够放入上一行，标点符号悬挂才生效。

从API版本23开始，新增compressLeadingPunctuation接口。

从API版本26.0.0开始，新增punctuationOverflow接口。


```

```TypeScript
### 示例24（设置自适应间距）

该示例通过[includeFontPadding](#includefontpadding23)接口增加首行尾行间距和[fallbackLineSpacing](#fallbacklinespacing23)接口设置自适应行间距。

从API version 23开始，新增[includeFontPadding](#includefontpadding23)和[fallbackLineSpacing](#fallbacklinespacing23)接口。


```

```TypeScript
### 示例25（设置文本拖拽时的背板样式）

该示例通过[selectedDragPreviewStyle](#selecteddragpreviewstyle23)接口设置文本拖拽时的背板样式。

从API version 23开始，新增selectedDragPreviewStyle接口。


```

```TypeScript
### 示例26（设置文本排版方向）

该示例通过[textDirection](#textdirection23)接口设置文本排版方向。

从API version 23开始，新增textDirection接口。


```

```TypeScript
### 示例27（获取指定坐标和范围对应的文本信息）

从API version 24开始，支持[getCharacterPositionAtCoordinate](ts-text-common.md#getcharacterpositionatcoordinate24)，[getGlyphRangeForCharacterRange](ts-text-common.md#getglyphrangeforcharacterrange24)，[getCharacterRangeForGlyphRange](ts-text-common.md#getcharacterrangeforglyphrange24)接口。该示例通过[getLayoutManager](#getlayoutmanager12)接口调用文本的布局管理对象获取文本信息，通过[LayoutManager](ts-text-common.md#layoutmanager12)中的[getCharacterPositionAtCoordinate](ts-text-common.md#getcharacterpositionatcoordinate24)获取坐标字符的位置信息，通过[getGlyphRangeForCharacterRange](ts-text-common.md#getglyphrangeforcharacterrange24)根据字符索引范围获取字形索引范围和实际的字符索引范围，通过[getCharacterRangeForGlyphRange](ts-text-common.md#getcharacterrangeforglyphrange24)根据字形索引范围获取字符索引范围和实际的字形索引范围。


```

```TypeScript
### 示例28（设置文本排版时是否使能孤字优化）

该示例通过[orphanCharOptimization](#orphancharoptimization)接口设置使能孤字优化，确保段落最后一行不出现孤字。

从API版本26.0.0开始，新增orphanCharOptimization接口。

该效果图会因设备尺寸差异有显示区别，仅供参考。


```

```TypeScript
### 示例29（设置可变字体的属性）

该示例通过[fontVariations](#fontvariations)接口设置可变字体的属性。

从API版本26.0.0开始，新增[fontVariations](#fontvariations)接口。


```

```TypeScript
### 示例30（设置图片预览菜单）

该示例通过[bindSelectionMenu](#bindselectionmenu11)接口实现了文本设置图片预览菜单的功能。

从API版本26.0.0开始，文本组件调用该接口时，options中的menuType属性传入MenuType.PREVIEW_MENU，设置图片预览菜单的能力生效。


```

```TypeScript
### 示例31（设置属性字符串段落缓存策略）

该示例通过[incrementalUpdatePolicy](#incrementalupdatepolicy)接口设置文本渲染的增量更新策略，使用段落级缓存优化渲染性能。

从API版本26.0.0开始，新增incrementalUpdatePolicy属性。


```

```TypeScript
### 示例32（设置文本尾部缩进）

该示例通过[tailIndents](#tailindents)接口实现了文本尾部缩进的功能。

从API版本26.0.0开始，通过tailIndents属性设置文本尾部缩进。


```

```TypeScript
### 示例33（设置文本选择的AI菜单）

该示例通过[enableSelectedDataDetector](#enableselecteddatadetector22)，配置文本选择AI菜单功能。

从API version 22开始，新增enableSelectedDataDetector。
```

```TypeScript
### 示例34（长按含表情符号文本绘制渐变高亮背景）

该示例通过[getLayoutManager](#getlayoutmanager12)接口获取文本的布局管理对象，使用[LayoutManager](ts-text-common.md#layoutmanager12)中以UTF-16编码查询的[getCharacterPositionAtCoordinate](ts-text-common.md#getcharacterpositionatcoordinate)根据长按坐标获取字符位置与亲和性，再通过[getGlyphRangeForCharacterRange](ts-text-common.md#getglyphrangeforcharacterrange)获取对应的字形索引范围与实际字符范围，最后通过[getRectsForRange](ts-text-common.md#getrectsforrange14)获取文本矩形区域，并在[Canvas](ts-components-canvas-canvas.md)上绘制渐变背景，实现对包含表情符号（字形簇）文本的高亮。

从API版本26.0.0开始，新增带编码类型参数的getCharacterPositionAtCoordinate、getGlyphRangeForCharacterRange、getCharacterRangeForGlyphRange接口重载，以及TextEncoding枚举。
```
