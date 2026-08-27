# ClickActionProposal

智慧手势点击动作处理。当通过[registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor)接口动态自定义智慧手势行为时，设置返回值 [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会触发目标组件的点击操作。

> **说明：**
> 
> - 该动作处理遵循“先选中，再点击”的处理语义。
> 
> - 当目标节点尚未被选中时，本次处理会优先建立选中态，而不会立即触发点击。

**继承/实现关系：** ClickActionProposal extends [TargetedGestureProposal](arkts-arkui-arkui-uicontext-targetedgestureproposal-c.md)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(node: FrameNode)
```

智慧手势点击动作处理的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 响应点击动作的目标节点。 |

**示例**

```TypeScript
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

function getUIContextByAtomicInterface(): UIContext {
  let callingScopeUIContext = UIContext.getCallingScopeUIContext();
  if (callingScopeUIContext) {
    hilog.info(0x00, 'testTag', `Get UIContext of calling scope.`)
    return callingScopeUIContext;
  }
  let allContexts = UIContext.getAllUIContexts();
  let length = allContexts.length;
  if (length === 1) {
    hilog.info(0x00, 'testTag', `Get UIContext of unique UI instance.`)
    return allContexts[0];
  }
  let lastFocusedUIContext = UIContext.getLastFocusedUIContext();
  if (lastFocusedUIContext) {
    hilog.info(0x00, 'testTag', `Get UIContext of last focused instance.`)
    return lastFocusedUIContext;
  }
  let lastForegroundUIContext = UIContext.getLastForegroundUIContext();
  if (lastForegroundUIContext) {
    hilog.info(0x00, 'testTag', `Get UIContext of last foregrounded instance.`)
    return lastForegroundUIContext;
  }
  if (length !== 0) {
    hilog.info(0x00, 'testTag', `Get UIContext with maximum instanceId.`)
    return allContexts[length - 1];
  }
  hilog.info(0x00, 'testTag', `Get UIContext of undefined calling scope.`)
  return new UIContext();
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  aboutToAppear() {
    let uiContext = this.getUIContext();
    hilog.info(0x00, 'testTag', `aboutToAppear UIContext: ${uiContext.getId()}`)
  }

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          let resolvedUIContext = UIContext.resolveUIContext();
          let contextByAtomicInterface = getUIContextByAtomicInterface();
          hilog.info(0x00, 'testTag',
            `UIContext id: ${resolvedUIContext.getId()}, strategy: ${resolvedUIContext.strategy}, contextByAtomicInterface: ${contextByAtomicInterface.getId()}`);
          this.message = 'Welcome';
        })
    }
    .height('100%')
    .width('100%')
  }
}
```
