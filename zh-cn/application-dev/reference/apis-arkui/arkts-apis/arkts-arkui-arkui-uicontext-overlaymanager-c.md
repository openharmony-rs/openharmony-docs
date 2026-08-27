# OverlayManager

class OverlayManager

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

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

Adds a specified ComponentContent node to the OverlayManager.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md) | 是 | Content to add to the target node on the **OverlayManager**.   **NOTE：**By default, the new node is centered on the page and stacked according to its stacking level. |
| index | number | 否 |  |

**示例**

```TypeScript
import { ComponentContent, OverlayManager } from '@kit.ArkUI';

class Params {
  text: string = '';
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
  @StorageLink('componentOffset') componentOffset: Position = { x: 0, y: 110 };

  build() {
    Column({ space: 5 }) {
      Button('++componentContentIndex: ' + this.componentContentIndex).onClick(() => {
        ++this.componentContentIndex;
      })
      Button('--componentContentIndex: ' + this.componentContentIndex).onClick(() => {
        --this.componentContentIndex;
      })
      Button('增加ComponentContent' + this.contentArray.length).onClick(() => {
        let componentContent = new ComponentContent(
          this.uiContext, wrapBuilder<[Params]>(builderText),
          new Params(this.message + (this.contentArray.length), this.componentOffset)
        );
        this.contentArray.push(componentContent);
        this.overlayNode.addComponentContent(componentContent, this.componentContentIndex);
      })
      Button('++arrayIndex: ' + this.arrayIndex).onClick(() => {
        ++this.arrayIndex;
      })
      Button('--arrayIndex: ' + this.arrayIndex).onClick(() => {
        --this.arrayIndex;
      })
      Button('删除ComponentContent' + this.arrayIndex).onClick(() => {
        if (this.arrayIndex >= 0 && this.arrayIndex < this.contentArray.length) {
          let componentContent = this.contentArray.splice(this.arrayIndex, 1);
          this.overlayNode.removeComponentContent(componentContent.pop());
        } else {
          console.info('arrayIndex有误');
        }
      })
      Button('显示ComponentContent' + this.arrayIndex).onClick(() => {
        if (this.arrayIndex >= 0 && this.arrayIndex < this.contentArray.length) {
          let componentContent = this.contentArray[this.arrayIndex];
          this.overlayNode.showComponentContent(componentContent);
        } else {
          console.info('arrayIndex有误');
        }
      })
      Button('隐藏ComponentContent' + this.arrayIndex).onClick(() => {
        if (this.arrayIndex >= 0 && this.arrayIndex < this.contentArray.length) {
          let componentContent = this.contentArray[this.arrayIndex];
          this.overlayNode.hideComponentContent(componentContent);
        } else {
          console.info('arrayIndex有误');
        }
      })
      Button('显示所有ComponentContent').onClick(() => {
        this.overlayNode.showAllComponentContents();
      })
      Button('隐藏所有ComponentContent').onClick(() => {
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

Creates a floating layer node with the specified display order. This API allows you to define the stacking order of the nodes when they are created.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md) | 是 | Content to add to the target node on the **OverlayManager**.    **NOTE：**By default, the new node is centered on the page and stacked according to its stacking level. |
| levelOrder | [LevelOrder](arkts-arkui-promptaction-levelorder-c.md) | 否 |  |

**示例**

本示例展示如何调用addComponentContentWithOrder接口创建浮层节点并指定显示顺序。

```TypeScript
import { ComponentContent, PromptAction, LevelOrder, UIContext, OverlayManager } from '@kit.ArkUI';

class Params {
  text: string = '';
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
  @State message: string = '弹窗';
  private ctx: UIContext = this.getUIContext();
  private promptAction: PromptAction = this.ctx.getPromptAction();
  private overlayNode: OverlayManager = this.ctx.getOverlayManager();
  @StorageLink('contentArray') contentArray: ComponentContent<Params>[] = [];
  @StorageLink('componentContentIndex') componentContentIndex: number = 0;
  @StorageLink('arrayIndex') arrayIndex: number = 0;
  @StorageLink('componentOffset') componentOffset: Position = { x: 0, y: 80 };

  build() {
    Row() {
      Column({ space: 10 }) {
        Button('OverlayManager下面弹窗')
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
              console.info('topOrder: ' + topOrder.getOrder());
            }
            let bottomOrder: LevelOrder = this.promptAction.getBottomOrder();
            if (bottomOrder !== undefined) {
              console.info('bottomOrder: ' + bottomOrder.getOrder());
            }
          })
        Button('OverlayManager上面弹窗')
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
              console.info('topOrder: ' + topOrder.getOrder());
            }
            let bottomOrder: LevelOrder = this.promptAction.getBottomOrder();
            if (bottomOrder !== undefined) {
              console.info('bottomOrder: ' + bottomOrder.getOrder());
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

Hide all ComponentContents on the OverlayManager.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

请参考[addComponentContent](#addcomponentcontent)示例。

## hideComponentContent

```TypeScript
hideComponentContent(content: ComponentContent): void
```

Hide the ComponentContent.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md) | 是 | Content to hide on the **OverlayManager**. |

**示例**

请参考[addComponentContent](#addcomponentcontent)示例。

## openOrderOverlay

```TypeScript
openOrderOverlay(content: ComponentContent, options?: OrderOverlayOptions): Promise<void>
```

打开具有指定ComponentContent和选项的浮层。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md) | 是 | OverlayManager新增节点需要添加的内容。 & lt;p & gt; & lt;strong & gt;注意 & lt;/strong & gt;：。 默认情况下，新节点在页面中居中，并根据其堆叠级别进行堆叠。 & lt;/p & gt; |
| options | [OrderOverlayOptions](arkts-arkui-arkui-uicontext-orderoverlayoptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 函数返回的promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103307](../errorcode-promptAction.md#103307-系统弹出窗口导致无法打开浮层) | The overlay cannot be opened due to the system pop-up window. |

**示例**

```TypeScript
import { ComponentContent, OverlayManager, LevelOrder, LevelMode } from '@kit.ArkUI';

class Params {
  text: string = '';
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

  build() {
    Column({ space: 5 }) {
      Button('打开浮层').onClick(() => {
        let componentContent = new ComponentContent(
          this.uiContext, wrapBuilder<[Params]>(builderText),
          new Params(this.message, { x: 0, y: 110 })
        );
        this.overlayNode.openOrderOverlay(componentContent, {
          levelOrder: LevelOrder.clamp(100),
          levelMode: LevelMode.OVERLAY
        });
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## removeComponentContent

```TypeScript
removeComponentContent(content: ComponentContent): void
```

Removes a specified ComponentContent node from the OverlayManager

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md) | 是 | Content to remove from the **OverlayManager**. |

**示例**

请参考[addComponentContent](#addcomponentcontent)示例。

## showAllComponentContents

```TypeScript
showAllComponentContents(): void
```

Show all ComponentContents on the OverlayManager.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

请参考[addComponentContent](#addcomponentcontent)示例。

## showComponentContent

```TypeScript
showComponentContent(content: ComponentContent): void
```

Show the ComponentContent.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md) | 是 | Content to show on the **OverlayManager**. |

**示例**

请参考[addComponentContent](#addcomponentcontent)示例。
