# SegmentButtonOptions


> **说明：**
> 
> 不支持设置字体类型。
> 分段按钮选项类用于提供初始数据和自定义属性。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SegmentButton, SegmentButtonOptions, SegmentButtonItemOptionsArray, TabSegmentButtonOptions, TabSegmentButtonConstructionOptions, CapsuleSegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonTextItem, SegmentButtonIconItem, SegmentButtonIconTextItem, DimensionNoPercentage, CommonSegmentButtonOptions, ItemRestriction, SegmentButtonItemTuple, SegmentButtonItemArray, SegmentButtonItemOptionsConstructorOptions, SegmentButtonItemOptions, BorderRadiusMode } from '@kit.ArkUI';
```

## capsule

```TypeScript
static capsule(options: CapsuleSegmentButtonConstructionOptions): SegmentButtonOptions
```

创建胶囊类的SegmentButtonOptions，用于定义胶囊类分段按钮。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CapsuleSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonconstructionoptions-i.md) | 是 | 胶囊类分段按钮信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md) | 分段按钮选项，用于定义胶囊类分段按钮。 |

## constructor

```TypeScript
constructor(options: TabSegmentButtonOptions | CapsuleSegmentButtonOptions)
```

构造函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TabSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonoptions-i.md) \| [CapsuleSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonoptions-i.md) | 是 | 页签类或者胶囊类分段按钮信息。 |

## tab

```TypeScript
static tab(options: TabSegmentButtonConstructionOptions): SegmentButtonOptions
```

创建SegmentButtonOptions类，用于定义页签。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TabSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonconstructionoptions-i.md) | 是 | 页签类分段按钮信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md) | 分段按钮选项，用于定义页签类分段按钮。 |

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle: BlurStyle
```

背景模糊材质。默认值：BlurStyle.NONE值为undefined时，按默认值处理。

**类型：** BlurStyle

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBorderRadius

```TypeScript
backgroundBorderRadius?: LengthMetrics
```

分段按钮整体容器的边框圆角半径。  
**说明：**此属性仅在borderRadiusMode为BorderRadiusMode.CUSTOM时生效。对于胶囊类多选分段按钮（type为"capsule"且multiply为true），此属性不生效，需要用itemBorderRadius配置圆角。圆角大小受组件尺寸限制，最大值为组件宽或高的一半，不支持百分比设置。超出最大值时自动修正为最大值，使用百分比时按默认值处理。默认值：`\$r('sys.float.segmentbutton_container_shape')`值为undefined时，按默认值处理。

**类型：** LengthMetrics

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor: ResourceColor
```

分段按钮组件的背景板颜色。值为undefined时，背景板颜色为\$r('sys.color.ohos_id_color_button_normal')。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
backgroundSystemMaterial?: uiMaterial.Material
```

分段按钮组件的背景板的系统材质。不同系统材质具有不同的属性，产生不同的效果。传入材质后，SegmentButton的动效发生改变。对于胶囊类多选分段按钮（即type为"capsule"且multiply为true），该属性不生效。默认值：无材质效果。从API版本26.0.0开始，除胶囊类多选分段按钮（即type为"capsule"且multiply为true）外，backgroundSystemMaterial设置自动反色的系统材质时，fontColor和 selectedFontColor使用支持反色的特殊系统资源，颜色自动适配到材质背景色的反色。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderRadiusMode

```TypeScript
borderRadiusMode?: BorderRadiusMode
```

边框圆角模式，用于控制圆角计算方式。默认值：BorderRadiusMode.DEFAULT值为undefined时，按默认值处理。

**类型：** [BorderRadiusMode](arkts-arkui-arkui-advanced-segmentbutton-borderradiusmode-e.md)

**默认值：** BorderRadiusMode.Default

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonPadding

```TypeScript
buttonPadding: Padding | Dimension
```

分段按钮组件的按钮内边距。值为undefined时，仅图标按钮和仅文字按钮内边距：`{ top: 4, right: 8, bottom: 4, left: 8 }`图标+文本按钮内边距：`{ top: 6, right: 8, bottom: 6, left: 8 }`单位：vp

**类型：** Padding \| [Dimension](arkts-arkui-dimension-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttons

```TypeScript
buttons: SegmentButtonItemOptionsArray
```

分段按钮组件的按钮信息，包括图标和文本信息。

**类型：** [SegmentButtonItemOptionsArray](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptionsarray-c.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

布局方向。默认值：Direction.Auto值为undefined时，按默认值处理。

**类型：** Direction

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor: ResourceColor
```

按钮未选中态的文本颜色。默认值：\$r('sys.color.ohos_id_color_text_secondary')值为undefined时，按默认值处理。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize: DimensionNoPercentage
```

分段按钮组件的按钮未选中态的字体大小，不支持百分比设置。单位：fp值为undefined时，字体大小为\$r('sys.float.ohos_id_text_size_body2')。

**类型：** [DimensionNoPercentage](arkts-arkui-dimensionnopercentage-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight: FontWeight
```

分段按钮组件的按钮未选中态的字体粗细。值为undefined时，字体粗细为FontWeight.Regular。

**类型：** FontWeight

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageSize

```TypeScript
imageSize: SizeOptions
```

分段按钮组件的图片尺寸。值为undefined时，图片尺寸为{ width: 24, height: 24 }。单位：vp  
**说明：**`imageSize`属性对仅图标按钮和图标+文本按钮生效，对纯文本按钮无效果。

**类型：** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemBorderRadius

```TypeScript
itemBorderRadius?: LengthMetrics
```

分段按钮中按钮项的边框圆角半径。  
**说明：**此属性仅在borderRadiusMode为BorderRadiusMode.CUSTOM时生效。对于胶囊类多选分段按钮（type为"capsule"且multiply为true），只能控制两端的选项圆角。圆角大小受组件尺寸限制，最大值为组件宽或高的一半，不支持百分比设置。超出最大值时自动修正为最大值，使用百分比时按默认值处理。默认值：`\$r('sys.float.segmentbutton_selected_background_shape')`值为undefined时，按默认值处理。

**类型：** LengthMetrics

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## localizedButtonPadding

```TypeScript
localizedButtonPadding?: LocalizedPadding
```

分段按钮组件的按钮内边距，支持随布局方向（LTR/RTL）自适应。默认值：仅图标按钮和仅文字按钮默认值： `{ top: LengthMetrics.vp(4), end: LengthMetrics.vp(8), bottom: LengthMetrics.vp(4), start: LengthMetrics.vp(8) }`图标+文本按钮默认值： `{ top: LengthMetrics.vp(6), end: LengthMetrics.vp(8), bottom: LengthMetrics.vp(6), start: LengthMetrics.vp(8) }`值为undefined时，按默认值处理。

**类型：** [LocalizedPadding](arkts-arkui-localizedpadding-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## localizedTextPadding

```TypeScript
localizedTextPadding?: LocalizedPadding
```

文本内边距，支持随布局方向（LTR/RTL）自适应。默认值：0单位：vp值为undefined时，按默认值处理。

**类型：** [LocalizedPadding](arkts-arkui-localizedpadding-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## multiply

```TypeScript
multiply: boolean
```

分段按钮组件是否可以多选。true：可多选；false：不可多选。页签类分段按钮（type为"tab"）时，multiply强制为false，设置true不生效。默认值： false值为undefined时，按默认值处理。

**类型：** boolean

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor: ResourceColor
```

按钮选中态的背景板颜色。默认值：type为"tab"时，默认值为`\$r('sys.color.segment_button_checked_foreground_color')`。type为"capsule"时，默认值为`\$r('sys.color.ohos_id_color_emphasize')`。值为undefined时，按默认值处理。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedFontColor

```TypeScript
selectedFontColor: ResourceColor
```

按钮选中态的文本颜色。默认值：type为"tab"时，默认值为`\$r('sys.color.ohos_id_color_text_primary')`。type为"capsule"时，默认值为`\$r('sys.color.ohos_id_color_foreground_contrary')`。值为undefined时，按默认值处理。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedFontSize

```TypeScript
selectedFontSize: DimensionNoPercentage
```

分段按钮组件的按钮选中态的字体大小，不支持百分比设置。单位：fp值为undefined时，字体大小为\$r('sys.float.ohos_id_text_size_body2')。

**类型：** [DimensionNoPercentage](arkts-arkui-dimensionnopercentage-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedFontWeight

```TypeScript
selectedFontWeight: FontWeight
```

分段按钮组件的按钮选中态的字体粗细。值为undefined时，字体粗细为FontWeight.Medium。

**类型：** FontWeight

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textPadding

```TypeScript
textPadding: Padding | Dimension
```

分段按钮组件的文本内边距。值为undefined时，文本内边距为0。单位：vp

**类型：** Padding \| [Dimension](arkts-arkui-dimension-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: "tab" | "capsule"
```

类型为页签类分段按钮。

**类型：** "tab" \| "capsule"

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
