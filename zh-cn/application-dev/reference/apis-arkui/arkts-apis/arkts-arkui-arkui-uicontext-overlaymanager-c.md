# OverlayManager

class OverlayManager

**起始版本：** 12

<!--Device-unnamed-export class OverlayManager--><!--Device-unnamed-export class OverlayManager-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
```

<a id="addcomponentcontent"></a>
## addComponentContent

```TypeScript
addComponentContent(content: ComponentContent, index?: number): void
```

Adds a specified ComponentContent node to the OverlayManager.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OverlayManager-addComponentContent(content: ComponentContent, index?: number): void--><!--Device-OverlayManager-addComponentContent(content: ComponentContent, index?: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ComponentContent](../arkts-components/arkts-arkui-componentcontent-t.md) | 是 | Content to add to the target node on the **OverlayManager**.<br>**NOTE**<br>By default, the new node is centered on the page and stacked according to its stacking level. |
| index | number | 否 |  |

<a id="addcomponentcontentwithorder"></a>
## addComponentContentWithOrder

```TypeScript
addComponentContentWithOrder(content: ComponentContent, levelOrder?: LevelOrder): void
```

Creates a floating layer node with the specified display order.This API allows you to define the stacking order of the nodes when they are created.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-OverlayManager-addComponentContentWithOrder(content: ComponentContent, levelOrder?: LevelOrder): void--><!--Device-OverlayManager-addComponentContentWithOrder(content: ComponentContent, levelOrder?: LevelOrder): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ComponentContent](../arkts-components/arkts-arkui-componentcontent-t.md) | 是 | Content to add to the target node on the **OverlayManager**.<br>**NOTE**<br>By default, the new node is centered on the page and stacked according to its stacking level. |
| levelOrder | [LevelOrder](arkts-arkui-levelorder-t.md) | 否 |  |

<a id="hideallcomponentcontents"></a>
## hideAllComponentContents

```TypeScript
hideAllComponentContents(): void
```

Hide all ComponentContents on the OverlayManager.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OverlayManager-hideAllComponentContents(): void--><!--Device-OverlayManager-hideAllComponentContents(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="hidecomponentcontent"></a>
## hideComponentContent

```TypeScript
hideComponentContent(content: ComponentContent): void
```

Hide the ComponentContent.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OverlayManager-hideComponentContent(content: ComponentContent): void--><!--Device-OverlayManager-hideComponentContent(content: ComponentContent): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ComponentContent](../arkts-components/arkts-arkui-componentcontent-t.md) | 是 | Content to hide on the **OverlayManager**. |

<a id="openorderoverlay"></a>
## openOrderOverlay

```TypeScript
openOrderOverlay(content: ComponentContent, options?: OrderOverlayOptions): Promise<void>
```

打开具有指定ComponentContent和选项的浮层。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OverlayManager-openOrderOverlay(content: ComponentContent, options?: OrderOverlayOptions): Promise<void>--><!--Device-OverlayManager-openOrderOverlay(content: ComponentContent, options?: OrderOverlayOptions): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ComponentContent](../arkts-components/arkts-arkui-componentcontent-t.md) | 是 | OverlayManager新增节点需要添加的内容。<p><strong>注意</strong>：。<br>默认情况下，新节点在页面中居中，并根据其堆叠级别进行堆叠。</p> |
| options | [OrderOverlayOptions](arkts-arkui-arkui-uicontext-orderoverlayoptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 函数返回的promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103307](../errorcode-promptAction.md#103307-系统弹出窗口导致无法打开浮层) | The overlay cannot be opened due to the system pop-up window. |

<a id="removecomponentcontent"></a>
## removeComponentContent

```TypeScript
removeComponentContent(content: ComponentContent): void
```

Removes a specified ComponentContent node from the OverlayManager

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OverlayManager-removeComponentContent(content: ComponentContent): void--><!--Device-OverlayManager-removeComponentContent(content: ComponentContent): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ComponentContent](../arkts-components/arkts-arkui-componentcontent-t.md) | 是 | Content to remove from the **OverlayManager**. |

<a id="showallcomponentcontents"></a>
## showAllComponentContents

```TypeScript
showAllComponentContents(): void
```

Show all ComponentContents on the OverlayManager.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OverlayManager-showAllComponentContents(): void--><!--Device-OverlayManager-showAllComponentContents(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="showcomponentcontent"></a>
## showComponentContent

```TypeScript
showComponentContent(content: ComponentContent): void
```

Show the ComponentContent.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OverlayManager-showComponentContent(content: ComponentContent): void--><!--Device-OverlayManager-showComponentContent(content: ComponentContent): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ComponentContent](../arkts-components/arkts-arkui-componentcontent-t.md) | 是 | Content to show on the **OverlayManager**. |

