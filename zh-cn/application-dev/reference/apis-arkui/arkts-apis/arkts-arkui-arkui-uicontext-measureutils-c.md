# MeasureUtils

MeasureUtils提供文本宽度、高度等相关计算能力，适用于文本自适应布局、多行文本截断、动态UI适配等场景。通过该类可精确计算文本尺寸，帮助开发者在布局前预判文本显示效果，避免文本溢出或布局错乱等问题。 > **说明：**> > - 以下API需先使用UIContext中的[getMeasureUtils()](arkts-arkui-arkui-uicontext-uicontext-c.md#getMeasureUtils)方法获取MeasureUtils实例，再通过此实例调用对应方法。 > > - 如需更多测算文本参数，建议使用图形对应测算接口[Paragraph](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-paragraph-c.md#Paragraph)接口。 > > - 调用文本计算接口时，应避免同时用[ApplicationContext.setFontSizeScale](../../apis-ability-kit/arkts-apis/arkts-ability-applicationcontext-c.md#setFontSizeScale)设置应用字体大小缩放比例。为了确保时序正确性，建议开发者自行监听字体缩放变化，以保证测算结果的准确性。 > > - 在测算裁剪后的文本时，由于某些Unicode字符（如emoji）的码位长度大于1，直接按字符串长度裁剪会导致不准确的结果。建议基于Unicode码点进行迭代处理，避免错误截断字符，确保测算结果准确，请参考[measureTextSize](#measureTextSize)的示例2。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-export class MeasureUtils--><!--Device-unnamed-export class MeasureUtils-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getParagraphs

```TypeScript
getParagraphs(styledString: StyledString, options?: TextLayoutOptions): Array<Paragraph>
```

将属性字符串根据文本布局选项转换成对应的[Paragraph](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-paragraph-c.md#Paragraph)数组。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureUtils-getParagraphs(styledString: StyledString, options?: TextLayoutOptions): Array<Paragraph>--><!--Device-MeasureUtils-getParagraphs(styledString: StyledString, options?: TextLayoutOptions): Array<Paragraph>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | StyledString | 是 | 待转换的属性字符串。 |
| options | [TextLayoutOptions](arkts-arkui-textcommon-textlayoutoptions-i.md) | 否 | 文本布局选项。省略时使用默认布局配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Paragraph&gt; | 根据文本布局选项转换后得到的[Paragraph]{ |

## measureText

```TypeScript
measureText(options: MeasureOptions): number
```

计算指定文本作为单行文本显示时的宽度，如果文本包含多行（由换行符`\n`分隔），则返回其中最长的行的宽度。 > **说明：**> > - 调用此接口时，应避免同时使用[ApplicationContext.setFontSizeScale](../../apis-ability-kit/arkts-apis/arkts-ability-applicationcontext-c.md#setFontSizeScale)设置应用字体大小缩放比例。为了确保时序正确性，建议开发者自行监听字体缩放变化，以保证测算结果的准确性。 > > - measureText接口的计算结果始终是单行文本的宽度，入参options中配置的布局约束（如constraintWidth、maxLines）对measureText的结果没有影响。如果需要计算布局约束下的宽度，请使用[measureTextSize](#measureTextSize)方法。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureUtils-measureText(options: MeasureOptions): number--><!--Device-MeasureUtils-measureText(options: MeasureOptions): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [MeasureOptions](arkts-arkui-measure-measureoptions-i.md) | 是 | 文本测量配置选项。包含文本内容（textContent）、字体大小（fontSize）等属性。constraintWidth、maxLines等布局约束属性对measureText的计算结果无影响，如需计算布局约束下的宽度，请使用measureTextSize方法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 文本宽度。&lt;br&gt;**说明：**&lt;br&gt;浮点数会向上取整。&lt;br&gt;单位：px |

## measureTextSize

```TypeScript
measureTextSize(options: MeasureOptions): SizeOptions
```

计算指定文本的宽度和高度。 > **说明：**> > 调用此接口时，应避免同时使用[ApplicationContext.setFontSizeScale](../../apis-ability-kit/arkts-apis/arkts-ability-applicationcontext-c.md#setFontSizeScale)设置应用字体大小缩放比例。为了确保时序正确性，建议开发者自行监听字体缩放变化，以保证测算结果的准确性。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureUtils-measureTextSize(options: MeasureOptions): SizeOptions--><!--Device-MeasureUtils-measureTextSize(options: MeasureOptions): SizeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [MeasureOptions](arkts-arkui-measure-measureoptions-i.md) | 是 | 文本测量配置选项。包含文本内容（textContent）、字体大小（fontSize）、约束宽度（constraintWidth）、最大行数（maxLines）等属性，用于配置被计算文本的测量参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SizeOptions](../../apis-na/arkts-apis/arkts-na-units-sizeoptions-i.md) | 返回文本所占布局宽度和高度。&lt;br&gt;**说明：**&lt;br&gt;未设置constraintWidth时，文本宽度返回值会向上取整；传参constraintWidth时，文本宽度返回值不被取整。&lt;br&gt;文本宽度以及高度返回值单位均为px。 |

