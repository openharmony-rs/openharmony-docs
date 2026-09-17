# OverlayManager

Provides the capability to draw overlays.

> **NOTE:** 
> 
> - The initial APIs of this class are supported since API version 12.
> 
> - In the following API examples, you must first use [getOverlayManager()](arkts-arkui-arkui-uicontext-uicontext-c.md#getoverlaymanager) in
> **UIContext** to obtain an **OverlayManager** instance, and then call the APIs using the obtained instance.
> 
> - The nodes on **OverlayManager** are above the page level, but below such components as created through
> **Dialog**, **Popup**, **Menu**, **BindSheet**, **BindContentCover**, and **Toast**.
> 
> - The drawing method inside and outside the safe area of nodes on **OverlayManager** is consistent with that of the page, and the keyboard avoidance method is also the same as that of the page.
> 
> - For properties related to **OverlayManager**, you are advised to use AppStorage for global storage across the application to prevent changes in property values when switching pages, which could lead to service errors.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## addComponentContent

```TypeScript
addComponentContent(content: ComponentContent, index?: number): void
```

Adds a specified **ComponentContent** node to the **OverlayManager**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md) | Yes | Content to add to the target node on the **OverlayManager**.<br> **NOTE:** <br> By default, the new node is centered on the page and stacked according to its stacking level. |
| index | number | No |  |

## addComponentContentWithOrder

```TypeScript
addComponentContentWithOrder(content: ComponentContent, levelOrder?: LevelOrder): void
```

Creates an overlay node with the specified display order.

This API allows you to define the stacking order of the nodes when they are created.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md) | Yes | Content to add to the target node on the **OverlayManager**.<br>**NOTE:** <br> By default, the new node is centered on the page and stacked according to its stacking level. |
| levelOrder | [LevelOrder](arkts-arkui-promptaction-levelorder-c.md) | No |  |

## hideAllComponentContents

```TypeScript
hideAllComponentContents(): void
```

Hides all **ComponentContent** nodes on the **OverlayManager**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hideComponentContent

```TypeScript
hideComponentContent(content: ComponentContent): void
```

Hides a specified **ComponentContent** node on the **OverlayManager**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md) | Yes | Content to hide on the **OverlayManager**. |

## openOrderOverlay

```TypeScript
openOrderOverlay(content: ComponentContent, options?: OrderOverlayOptions): Promise<void>
```

Opens an overlay with the specified ComponentContent and options.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md) | Yes | Content to add to the new node on the OverlayManager. <p>&lt;strong&gt;NOTE&lt;/strong&gt;:<br>By default, the new node is centered on the page and stacked according to its stacking level. </p> |
| options | [OrderOverlayOptions](arkts-arkui-arkui-uicontext-orderoverlayoptions-i.md) | No |  |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [103307](../errorcode-promptAction.md#103307-failed-to-open-the-overlay-due-to-a-system-pop-up-window) | The overlay cannot be opened due to the system pop-up window. |

## removeComponentContent

```TypeScript
removeComponentContent(content: ComponentContent): void
```

Removes a specified node from the **OverlayManager**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md) | Yes | Content to remove from the **OverlayManager**. |

## showAllComponentContents

```TypeScript
showAllComponentContents(): void
```

Shows all **ComponentContent** nodes on the **OverlayManager**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showComponentContent

```TypeScript
showComponentContent(content: ComponentContent): void
```

Shows a specified **ComponentContent** node on the **OverlayManager**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md) | Yes | Content to show on the **OverlayManager**. |
