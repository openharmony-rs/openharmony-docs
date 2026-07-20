# SegmentButtonOptions

> **说明：**  
>  
> 不支持设置字体类型。

分段按钮选项类用于提供初始数据和自定义属性。

**起始版本：** 11

**装饰器类型：** @Observed

<!--Device-unnamed-declare class SegmentButtonOptions--><!--Device-unnamed-declare class SegmentButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CommonSegmentButtonOptions, SegmentButtonItemOptionsConstructorOptions, SegmentButtonIconTextItem, SegmentButtonItemOptions, SegmentButtonTextItem, CapsuleSegmentButtonOptions, SegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonItemTuple, SegmentButton, SegmentButtonItemArray, SegmentButtonItemOptionsArray, SegmentButtonIconItem, BorderRadiusMode, TabSegmentButtonConstructionOptions, TabSegmentButtonOptions, ItemRestriction, DimensionNoPercentage } from '@kit.ArkUI';
```

<a id="capsule"></a>
## capsule

```TypeScript
static capsule(options: CapsuleSegmentButtonConstructionOptions): SegmentButtonOptions
```

创建胶囊类的SegmentButtonOptions。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-static capsule(options: CapsuleSegmentButtonConstructionOptions): SegmentButtonOptions--><!--Device-SegmentButtonOptions-static capsule(options: CapsuleSegmentButtonConstructionOptions): SegmentButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CapsuleSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonconstructionoptions-i.md) | 是 | 胶囊类分段按钮信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md) | 分段按钮选项。 |

<a id="constructor"></a>
## constructor

```TypeScript
constructor(options: TabSegmentButtonOptions | CapsuleSegmentButtonOptions)
```

构造函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-constructor(options: TabSegmentButtonOptions | CapsuleSegmentButtonOptions)--><!--Device-SegmentButtonOptions-constructor(options: TabSegmentButtonOptions | CapsuleSegmentButtonOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TabSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonoptions-i.md) \| CapsuleSegmentButtonOptions | 是 | 页签类或者胶囊类分段按钮信息。 |

<a id="tab"></a>
## tab

```TypeScript
static tab(options: TabSegmentButtonConstructionOptions): SegmentButtonOptions
```

创建SegmentButtonOptions类，用于定义页签。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-static tab(options: TabSegmentButtonConstructionOptions): SegmentButtonOptions--><!--Device-SegmentButtonOptions-static tab(options: TabSegmentButtonConstructionOptions): SegmentButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TabSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonconstructionoptions-i.md) | 是 | 页签类分段按钮信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md) | 分段按钮选项。 |

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle: BlurStyle
```

分段按钮组件的背景模糊材质。

值为undefined时，背景模糊材质为BlurStyle.NONE。

**类型：** BlurStyle

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-backgroundBlurStyle: BlurStyle--><!--Device-SegmentButtonOptions-backgroundBlurStyle: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBorderRadius

```TypeScript
backgroundBorderRadius?: LengthMetrics
```

分段按钮整体容器的边框圆角半径。

**说明：**

此属性仅在borderRadiusMode为BorderRadiusMode.CUSTOM时生效。

对于胶囊类多选按钮(type为"capsule"且multiply为true)，此属性不生效，需要用itemBorderRadius配置圆角。

圆角大小受组件尺寸限制，最大值为组件宽或高的一半，不支持百分比设置。

默认值：`$r('sys.float.segmentbutton_container_shape')`

值为undefined时，按默认值处理。

**类型：** LengthMetrics

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-backgroundBorderRadius?: LengthMetrics--><!--Device-SegmentButtonOptions-backgroundBorderRadius?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor: ResourceColor
```

分段按钮组件的背景板颜色。

值为undefined时，背景板颜色为$r('sys.color.ohos_id_color_button_normal')。

**类型：** ResourceColor

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-backgroundColor: ResourceColor--><!--Device-SegmentButtonOptions-backgroundColor: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderRadiusMode

```TypeScript
borderRadiusMode?: BorderRadiusMode
```

边框圆角模式，用于控制圆角计算方式。

默认值：BorderRadiusMode.DEFAULT

值为undefined时，按默认值处理。

**类型：** BorderRadiusMode

**默认值：** BorderRadiusMode.Default

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-borderRadiusMode?: BorderRadiusMode--><!--Device-SegmentButtonOptions-borderRadiusMode?: BorderRadiusMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonPadding

```TypeScript
buttonPadding: Padding | Dimension
```

分段按钮组件的按钮内边距。

值为undefined时，仅图标按钮和仅文字按钮内边距：`{ top: 4, right: 8, bottom: 4, left: 8 }`

图标+文本按钮内边距：`{ top: 6, right: 8, bottom: 6, left: 8 }`

单位：vp

**类型：** Padding \| Dimension

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-buttonPadding: Padding | Dimension--><!--Device-SegmentButtonOptions-buttonPadding: Padding | Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttons

```TypeScript
buttons: SegmentButtonItemOptionsArray
```

分段按钮组件的按钮信息，包括图标和文本信息。

**类型：** SegmentButtonItemOptionsArray

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-buttons: SegmentButtonItemOptionsArray--><!--Device-SegmentButtonOptions-buttons: SegmentButtonItemOptionsArray-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

分段按钮组件的布局方向。

默认值：Direction.Auto

值为undefined时，按默认值处理。

**类型：** Direction

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-direction?: Direction--><!--Device-SegmentButtonOptions-direction?: Direction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor: ResourceColor
```

分段按钮组件的按钮未选中态的文本颜色。

值为undefined时，颜色为$r('sys.color.ohos_id_color_text_secondary')。

**类型：** ResourceColor

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-fontColor: ResourceColor--><!--Device-SegmentButtonOptions-fontColor: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize: DimensionNoPercentage
```

分段按钮组件的按钮未选中态的字体大小，不支持百分比设置。

值为undefined时，字体大小为$r('sys.float.ohos_id_text_size_body2')。

**类型：** DimensionNoPercentage

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-fontSize: DimensionNoPercentage--><!--Device-SegmentButtonOptions-fontSize: DimensionNoPercentage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight: FontWeight
```

分段按钮组件的按钮未选中态的字体粗细。

值为undefined时，字体粗细为FontWeight.Regular。

**类型：** FontWeight

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-fontWeight: FontWeight--><!--Device-SegmentButtonOptions-fontWeight: FontWeight-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageSize

```TypeScript
imageSize: SizeOptions
```

分段按钮组件的图片尺寸。

值为undefined时，图片尺寸为{ width: 24, height: 24 }。

单位：vp

**说明：**

`imageSize`属性对仅图标按钮和图标+文本按钮生效，对仅文字按钮无效果。

**类型：** SizeOptions

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-imageSize: SizeOptions--><!--Device-SegmentButtonOptions-imageSize: SizeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemBorderRadius

```TypeScript
itemBorderRadius?: LengthMetrics
```

分段按钮中按钮项的边框圆角半径。

**说明：**

此属性仅在borderRadiusMode为BorderRadiusMode.CUSTOM时生效。

对于胶囊类多选按钮(type为"capsule"且multiply为true)，只能控制两端的选项圆角。

圆角大小受组件尺寸限制，最大值为组件宽或高的一半，不支持百分比设置。

默认值：`$r('sys.float.segmentbutton_selected_background_shape')`

值为undefined时，按默认值处理。

**类型：** LengthMetrics

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-itemBorderRadius?: LengthMetrics--><!--Device-SegmentButtonOptions-itemBorderRadius?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## localizedButtonPadding

```TypeScript
localizedButtonPadding?: LocalizedPadding
```

分段按钮组件的按钮内边距。

默认值：

仅图标按钮和仅文字按钮默认值：`{ top: LengthMetrics.vp(4), end: LengthMetrics.vp(8), bottom: LengthMetrics.vp(4), start: LengthMetrics.vp(8) }`

图标+文本按钮默认值：`{ top: LengthMetrics.vp(6), end: LengthMetrics.vp(8), bottom: LengthMetrics.vp(6), start: LengthMetrics.vp(8) }`

值为undefined时，按默认值处理。

**类型：** LocalizedPadding

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-localizedButtonPadding?: LocalizedPadding--><!--Device-SegmentButtonOptions-localizedButtonPadding?: LocalizedPadding-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## localizedTextPadding

```TypeScript
localizedTextPadding?: LocalizedPadding
```

文本内边距。

默认值：0

值为undefined时，按默认值处理。

**类型：** LocalizedPadding

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-localizedTextPadding?: LocalizedPadding--><!--Device-SegmentButtonOptions-localizedTextPadding?: LocalizedPadding-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## multiply

```TypeScript
multiply: boolean
```

分段按钮组件是否可以多选。

true: 可多选；false: 不可多选。页签类分段按钮只支持单选，设置`multiply`为`true`不生效。

值为undefined时，分段按钮不支持多选。

**类型：** boolean

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-multiply: boolean--><!--Device-SegmentButtonOptions-multiply: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor: ResourceColor
```

分段按钮组件的按钮选中态背景板颜色。

值为undefined时，type为"tab"时，背景板颜色为`$r('sys.color.segment_button_checked_foreground_color')`。

type为"capsule"时，背景板颜色为`$r('sys.color.ohos_id_color_emphasize')`。

**类型：** ResourceColor

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-selectedBackgroundColor: ResourceColor--><!--Device-SegmentButtonOptions-selectedBackgroundColor: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedFontColor

```TypeScript
selectedFontColor: ResourceColor
```

分段按钮组件的按钮选中态的文本颜色。

值为undefined时，type为"tab"时，颜色为`$r('sys.color.ohos_id_color_text_primary')`。

type为"capsule"时，颜色为`$r('sys.color.ohos_id_color_foreground_contrary')`。

**类型：** ResourceColor

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-selectedFontColor: ResourceColor--><!--Device-SegmentButtonOptions-selectedFontColor: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedFontSize

```TypeScript
selectedFontSize: DimensionNoPercentage
```

分段按钮组件的按钮选中态的字体大小，不支持百分比设置。

值为undefined时，字体大小为$r('sys.float.ohos_id_text_size_body2')。

**类型：** DimensionNoPercentage

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-selectedFontSize: DimensionNoPercentage--><!--Device-SegmentButtonOptions-selectedFontSize: DimensionNoPercentage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedFontWeight

```TypeScript
selectedFontWeight: FontWeight
```

分段按钮组件的按钮选中态的字体粗细。

值为undefined时，字体粗细为FontWeight.Medium。

**类型：** FontWeight

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-selectedFontWeight: FontWeight--><!--Device-SegmentButtonOptions-selectedFontWeight: FontWeight-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textPadding

```TypeScript
textPadding: Padding | Dimension
```

分段按钮组件的文本内边距。

值为undefined时，文本内边距为0。

单位：vp

**类型：** Padding \| Dimension

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-textPadding: Padding | Dimension--><!--Device-SegmentButtonOptions-textPadding: Padding | Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: "tab" | "capsule"
```

分段按钮组件的类型。

**说明：**

"tab"：页签类分段按钮，适用于页面或内容区域的切换场景。

"capsule"：胶囊类分段按钮，适用于单选或多选的选择场景。

**类型：** "tab" \| "capsule"

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonOptions-type: "tab" | "capsule"--><!--Device-SegmentButtonOptions-type: "tab" | "capsule"-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

