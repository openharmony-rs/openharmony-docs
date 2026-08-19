# SwiperContentInfo

Swiper组件的内容区信息。

**起始版本：** 22

<!--Device-unnamed-export interface SwiperContentInfo--><!--Device-unnamed-export interface SwiperContentInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## id

```TypeScript
id: string
```

Swiper组件的id。

**类型：** string

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperContentInfo-id: string--><!--Device-SwiperContentInfo-id: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## swiperItemInfos

```TypeScript
swiperItemInfos: Array<SwiperItemInfo>
```

当前处于显示状态的Swiper子组件的信息。

**类型：** Array&lt;[SwiperItemInfo](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-swiperiteminfo-i.md)&gt;

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperContentInfo-swiperItemInfos: Array<SwiperItemInfo>--><!--Device-SwiperContentInfo-swiperItemInfos: Array<SwiperItemInfo>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## uniqueId

```TypeScript
uniqueId: number
```

Swiper子组件的唯一标识符。

**类型：** number

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperContentInfo-uniqueId: number--><!--Device-SwiperContentInfo-uniqueId: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

