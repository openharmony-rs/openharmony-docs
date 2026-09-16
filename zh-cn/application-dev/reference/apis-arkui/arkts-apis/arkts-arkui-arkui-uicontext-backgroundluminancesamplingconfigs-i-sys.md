# BackgroundLuminanceSamplingConfigs（系统接口）

背景亮度采样参数配置。背景亮度采样用于定期从组件背景区域取色，根据亮度阈值判定背景的明暗程度，以支持组件自适应明暗风格等场景。

**起始版本：** 23

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## brightThreshold

```TypeScript
brightThreshold?: number
```

浅色亮度阈值：[0, 255]内的整数，设置的浅色亮度阈值应大于深色亮度阈值，若浅色亮度阈值不大于深色亮度阈值，将抛出异常。当需要调整浅色判定灵敏度时可自定义此值，低于默认值220的设置使浅色判定更宽松，高于默认值的设置使浅色判定更严格。

默认值：220

**类型：** number

**默认值：** 220

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## darkThreshold

```TypeScript
darkThreshold?: number
```

深色亮度阈值：[0, 255]内的整数，设置的深色亮度阈值应小于浅色亮度阈值。当需要调整深色判定灵敏度时可自定义此值，高于默认值150的设置使深色判定更宽松，低于默认值的设置使深色判定更严格。

默认值：150

**类型：** number

**默认值：** 150

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## region

```TypeScript
region?: Edges<LengthMetrics>
```

相对组件的采样区域偏移，以组件自身的左上点为基准进行偏移计算。取色区域建议设置在可见范围内，避免偏移超出组件可见区域导致采样结果不准确。

默认取色区域与所配置组件区域一致（即不设置偏移时，取色区域等于组件自身区域）。

**类型：** [Edges](arkts-arkui-graphics-edges-i.md)&lt;[LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## samplingInterval

```TypeScript
samplingInterval?: number
```

取色间隔，单位为毫秒，取值范围：≥180ms。传入小于180ms的值时，自动修正为180ms。当需要更频繁的背景取色响应时可设置较小值（如180-300ms），当需要节省系统资源时可设置较大值（如500-1000ms）。

默认值：500ms

**类型：** number

**默认值：** 500

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
