# ApplicationShortcutCallbackInfo

```TypeScript
export interface ApplicationShortcutCallbackInfo
```

应用级快捷键触发时的回调信息。

**起始版本：** 26.1.0

<!--Device-unnamed-export interface ApplicationShortcutCallbackInfo--><!--Device-unnamed-export interface ApplicationShortcutCallbackInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## uiContext

```TypeScript
uiContext: UIContext
```

触发应用级快捷键的UI实例对应的UIContext。

**类型：** [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-ApplicationShortcutCallbackInfo-uiContext: UIContext--><!--Device-ApplicationShortcutCallbackInfo-uiContext: UIContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
