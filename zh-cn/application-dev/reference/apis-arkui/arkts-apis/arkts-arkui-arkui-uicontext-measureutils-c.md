# MeasureUtils

class MeasureUtils

<p><strong>NOTE</strong>:<br>You must first use getMeasureUtils() in UIContext to obtain a MeasureUtils instance,and then call the APIs using the obtained instance.</p>

**起始版本：** 12

<!--Device-unnamed-export class MeasureUtils--><!--Device-unnamed-export class MeasureUtils-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
```

## getParagraphs

```TypeScript
getParagraphs(styledString: StyledString, options?: TextLayoutOptions): Array<Paragraph>
```

获取样式字符串的布局信息。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureUtils-getParagraphs(styledString: StyledString, options?: TextLayoutOptions): Array<Paragraph>--><!--Device-MeasureUtils-getParagraphs(styledString: StyledString, options?: TextLayoutOptions): Array<Paragraph>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | [StyledString](arkts-arkui-styledstring-c.md) | 是 | 样式化的字符串值。 |
| options | [TextLayoutOptions](arkts-arkui-textlayoutoptions-i.md) | 否 | 布局选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Paragraph&gt; | 段落结果 |

## measureText

```TypeScript
measureText(options: MeasureOptions): number
```

Obtains the width of the specified text in a single line layout.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureUtils-measureText(options: MeasureOptions): number--><!--Device-MeasureUtils-measureText(options: MeasureOptions): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [MeasureOptions](arkts-arkui-measure-measureoptions-i.md) | 是 | Options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | - The unit is px. |

## measureTextSize

```TypeScript
measureTextSize(options: MeasureOptions): SizeOptions
```

Obtains the width and height of the specified text in a single line layout.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureUtils-measureTextSize(options: MeasureOptions): SizeOptions--><!--Device-MeasureUtils-measureTextSize(options: MeasureOptions): SizeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [MeasureOptions](arkts-arkui-measure-measureoptions-i.md) | 是 | Options of measure area occupied by text. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SizeOptions](arkts-arkui-sizeoptions-i.md) | width and height for text to display.The return values for text width and height are both in px. |

