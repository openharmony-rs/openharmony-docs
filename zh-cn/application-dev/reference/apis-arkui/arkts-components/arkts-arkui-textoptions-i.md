# TextOptions

Text初始化参数。

**起始版本：** 11

<!--Device-unnamed-declare interface TextOptions--><!--Device-unnamed-declare interface TextOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { WindowExtensionAbility, WindowExtensionContext } from '@kit.ArkUI';
import { NodeRenderType, RenderOptions, BuilderNode, ReactiveBuilderNode, BuildOptions, NodeController, FrameNode, DrawContext, Size, Offset, Position, Pivot, Scale, Translation, Matrix4, Rotation, Frame, RenderNode, XComponentNode, LengthMetrics, ColorMetrics, BackgroundBlur, ContentBlur, ForegroundBlur, LengthUnit, LengthMetricsUnit, LayoutConstraint, ComponentContent, ReactiveComponentContent, NodeContent, Content, typeNode, NodeAdapter, ShapeMask, ShapeClip, Rect, RoundRect, edgeColors, edgeWidths, borderStyles, borderRadiuses, ExpandMode, ChildrenCountMode, UIState, InputEventType } from '@kit.ArkUI';
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo } from '@kit.ArkUI';
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## controller

```TypeScript
controller: TextController
```

文本控制器。

**类型：** [TextController](arkts-arkui-textcontroller-c.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextOptions-controller: TextController--><!--Device-TextOptions-controller: TextController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

