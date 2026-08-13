# MeasureText

定义了测算方法类。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare class MeasureText--><!--Device-unnamed-declare class MeasureText-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## measureText

```TypeScript
static measureText(options: MeasureOptions): double
```

计算指定文本作为单行文本显示时的宽度。如果文本包含多行（由换行符`\n`分隔），则返回其中最长的行的宽度。 > **说明：** > > -measureText需要先通过[UIContext](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md)中的 > [getMeasureUtils](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getMeasureUtils)方法获取 > [MeasureUtils](../../../reference/apis-arkui/arkts-apis-uicontext-measureutils.md)对象，然后通过该对象进行调用。 > > - 直接使用MeasureText可能导致[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题，推荐通过 > [UIContext](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md)中的 > [getMeasureUtils](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getMeasureUtils)方法获取当前UI上下文关 > 联的[MeasureUtils](../../../reference/apis-arkui/arkts-apis-uicontext-measureutils.md)实例。 > > - measureText接口的计算结果始终是单行文本的宽度，入参options中配置的布局约束（如constraintWidth、maxLines）对measureText的结果没有影响。如果需要计算布局约束下的宽度，请使用 > [measureTextSize](../../../reference/apis-arkui/arkts-apis-uicontext-measureutils.md#measuretextsize12)方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureText-static measureText(options: MeasureOptions): double--><!--Device-MeasureText-static measureText(options: MeasureOptions): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [MeasureOptions](../../apis-arkui/arkts-apis/arkts-arkui-measure-measureoptions-i.md) | 是 | 被计算文本描述信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 文本宽度。&lt;br/&gt;单位：px |

## measureTextSize

```TypeScript
static measureTextSize(options: MeasureOptions): SizeOptions
```

计算指定文本的宽度和高度。 > **说明：** > > -measureTextSize需要先通过[UIContext](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md)中的 > [getMeasureUtils](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getMeasureUtils)方法获取 > [MeasureUtils](../../../reference/apis-arkui/arkts-apis-uicontext-measureutils.md)对象，然后通过该对象进行调用。 > > - 直接使用MeasureText可能导致[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题，推荐通过 > [UIContext](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md)中的 > [getMeasureUtils](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getMeasureUtils)方法获取当前UI上下文关 > 联的[MeasureUtils](../../../reference/apis-arkui/arkts-apis-uicontext-measureutils.md)实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureText-static measureTextSize(options: MeasureOptions): SizeOptions--><!--Device-MeasureText-static measureTextSize(options: MeasureOptions): SizeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [MeasureOptions](../../apis-arkui/arkts-apis/arkts-arkui-measure-measureoptions-i.md) | 是 | 被计算文本描述信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SizeOptions](arkts-na-units-sizeoptions-i.md) | 返回文本所占布局宽度和高度。&lt;br/&gt;**说明：** &lt;br/&gt;文本宽度以及高度返回值单位均为px。 |

