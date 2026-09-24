# OverlayManager

```TypeScript
export class OverlayManager
```

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

**Examples**

```TypeScript
import { ComponentContent, OverlayManager } from '@kit.ArkUI';

class Params {
  text: string = "";
  offset: Position;

  constructor(text: string, offset: Position) {
    this.text = text;
    this.offset = offset;
  }
}

@Builder
function builderText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
  }.offset(params.offset)
}

@Entry
@Component
struct OverlayExample {
  @State message: string = 'ComponentContent';
  private uiContext: UIContext = this.getUIContext();
  private overlayNode: OverlayManager = this.uiContext.getOverlayManager();
  @StorageLink('contentArray') contentArray: ComponentContent<Params>[] = [];
  @StorageLink('componentContentIndex') componentContentIndex: number = 0;
  @StorageLink('arrayIndex') arrayIndex: number = 0;
  @StorageLink("componentOffset") componentOffset: Position = { x: 0, y: 110 };

  build() {
    Column({ space: 5 }) {
      Button("++componentContentIndex: " + this.componentContentIndex).onClick(() => {
        ++this.componentContentIndex;
      })
      Button("--componentContentIndex: " + this.componentContentIndex).onClick(() => {
        --this.componentContentIndex;
      })
      Button("Add ComponentContent" + this.contentArray.length).onClick(() => {
        let componentContent = new ComponentContent(
          this.uiContext, wrapBuilder<[Params]>(builderText),
          new Params(this.message + (this.contentArray.length), this.componentOffset)
        );
        this.contentArray.push(componentContent);
        this.overlayNode.addComponentContent(componentContent, this.componentContentIndex);
      })
      Button("++arrayIndex: " + this.arrayIndex).onClick(() => {
        ++this.arrayIndex;
      })
      Button("--arrayIndex: " + this.arrayIndex).onClick(() => {
        --this.arrayIndex;
      })
      Button("Delete ComponentContent" + this.arrayIndex).onClick(() => {
        if (this.arrayIndex >= 0 && this.arrayIndex < this.contentArray.length) {
          let componentContent = this.contentArray.splice(this.arrayIndex, 1);
          this.overlayNode.removeComponentContent(componentContent.pop());
        } else {
          console.info("Invalid arrayIndex.");
        }
      })
      Button("Show ComponentContent" + this.arrayIndex).onClick(() => {
        if (this.arrayIndex >= 0 && this.arrayIndex < this.contentArray.length) {
          let componentContent = this.contentArray[this.arrayIndex];
          this.overlayNode.showComponentContent(componentContent);
        } else {
          console.info("Invalid arrayIndex.");
        }
      })
      Button("Hide ComponentContent" + this.arrayIndex).onClick(() => {
        if (this.arrayIndex >= 0 && this.arrayIndex < this.contentArray.length) {
          let componentContent = this.contentArray[this.arrayIndex];
          this.overlayNode.hideComponentContent(componentContent);
        } else {
          console.info("Invalid arrayIndex.");
        }
      })
      Button("Show All ComponentContent").onClick(() => {
        this.overlayNode.showAllComponentContents();
      })
      Button("Hide All ComponentContent").onClick(() => {
        this.overlayNode.hideAllComponentContents();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

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

**Examples**

This example demonstrates how to use addComponentContentWithOrder to create an overlay node with the specified display order.

```TypeScript
import { ComponentContent, PromptAction, LevelOrder, UIContext, OverlayManager } from '@kit.ArkUI';

class Params {
  text: string = "";
  offset: Position;
  constructor(text: string, offset: Position) {
    this.text = text;
    this.offset = offset;
  }
}
@Builder
function builderText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
  }.offset(params.offset)
}

@Entry
@Component
struct Index {
  @State message: string = 'Dialog box';
  private ctx: UIContext = this.getUIContext();
  private promptAction: PromptAction = this.ctx.getPromptAction();
  private overlayNode: OverlayManager = this.ctx.getOverlayManager();
  @StorageLink('contentArray') contentArray: ComponentContent<Params>[] = [];
  @StorageLink('componentContentIndex') componentContentIndex: number = 0;
  @StorageLink('arrayIndex') arrayIndex: number = 0;
  @StorageLink("componentOffset") componentOffset: Position = { x: 0, y: 80 };

  build() {
    Row() {
      Column({ space: 10 }) {
        Button('OverlayManager Bottom Overlay')
          .fontSize(20)
          .onClick(() => {
            let componentContent = new ComponentContent(
              this.ctx, wrapBuilder<[Params]>(builderText),
              new Params(this.message + (this.contentArray.length), this.componentOffset)
            );
            this.contentArray.push(componentContent);
            this.overlayNode.addComponentContentWithOrder(componentContent, LevelOrder.clamp(100.1));
            let topOrder: LevelOrder = this.promptAction.getTopOrder();
            if (topOrder !== undefined) {
              console.error('topOrder: ' + topOrder.getOrder());
            }
            let bottomOrder: LevelOrder = this.promptAction.getBottomOrder();
            if (bottomOrder !== undefined) {
              console.error('bottomOrder: ' + bottomOrder.getOrder());
            }
          })
        Button('OverlayManager Top Overlay')
          .fontSize(20)
          .onClick(() => {
            let componentContent = new ComponentContent(
              this.ctx, wrapBuilder<[Params]>(builderText),
              new Params(this.message + (this.contentArray.length), this.componentOffset)
            );
            this.contentArray.push(componentContent);
            this.overlayNode.addComponentContentWithOrder(componentContent, LevelOrder.clamp(100.2));
            let topOrder: LevelOrder = this.promptAction.getTopOrder();
            if (topOrder !== undefined) {
              console.error('topOrder: ' + topOrder.getOrder());
            }
            let bottomOrder: LevelOrder = this.promptAction.getBottomOrder();
            if (bottomOrder !== undefined) {
              console.error('bottomOrder: ' + bottomOrder.getOrder());
            }
          })
      }.width('100%')
    }.height('100%')
  }
}
```

## hideAllComponentContents

```TypeScript
hideAllComponentContents(): void
```

Hides all **ComponentContent** nodes on the **OverlayManager**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

See the example for [addComponentContent](#addcomponentcontent).

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

**Examples**

See the example for [addComponentContent](#addcomponentcontent).

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

**Examples**

See the example for [addComponentContent](#addcomponentcontent).

## showAllComponentContents

```TypeScript
showAllComponentContents(): void
```

Shows all **ComponentContent** nodes on the **OverlayManager**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

See the example for [addComponentContent](#addcomponentcontent).

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

**Examples**

See the example for [addComponentContent](#addcomponentcontent).
