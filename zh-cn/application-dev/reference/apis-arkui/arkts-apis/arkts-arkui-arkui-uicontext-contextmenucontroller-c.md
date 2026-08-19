# ContextMenuController

class ContextMenuController 提供控制菜单关闭的能力。 > **说明：** > > - 本Class首批接口从API version 12开始支持。 > - 以下API需先使用UIContext中的[getContextMenuController()](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-uicontext-c.md#getcontextmenucontroller)方法获取 > ContextMenuController实例，再通过此实例调用对应方法。

**起始版本：** 12

<!--Device-unnamed-export declare class ContextMenuController--><!--Device-unnamed-export declare class ContextMenuController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## close

```TypeScript
close(): void
```

关闭菜单

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ContextMenuController-close(): void--><!--Device-ContextMenuController-close(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

