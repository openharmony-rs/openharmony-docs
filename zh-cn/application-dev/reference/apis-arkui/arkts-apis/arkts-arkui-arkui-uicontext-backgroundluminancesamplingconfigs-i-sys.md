# BackgroundLuminanceSamplingConfigs（系统接口）

背景取色参数配置。

**起始版本：** 23

<!--Device-unnamed-export interface BackgroundLuminanceSamplingConfigs--><!--Device-unnamed-export interface BackgroundLuminanceSamplingConfigs-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
```

## brightThreshold

```TypeScript
brightThreshold?: number
```

浅色亮度阈值：[0, 255]内的整数，设置的深色亮度阈值应小于浅色亮度阈值。

默认值：220

**类型：** number

**默认值：** 220

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundLuminanceSamplingConfigs-brightThreshold?: number--><!--Device-BackgroundLuminanceSamplingConfigs-brightThreshold?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## darkThreshold

```TypeScript
darkThreshold?: number
```

深色亮度阈值：[0, 255]内的整数，设置的深色亮度阈值应小于浅色亮度阈值。

默认值：150

**类型：** number

**默认值：** 150

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundLuminanceSamplingConfigs-darkThreshold?: number--><!--Device-BackgroundLuminanceSamplingConfigs-darkThreshold?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## region

```TypeScript
region?: Edges<LengthMetrics>
```

相对组件的取色区域偏移，以组件自身的左上点为基准进行偏移计算。

默认使用组件自身区域

**类型：** Edges&lt;LengthMetrics&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundLuminanceSamplingConfigs-region?: Edges<LengthMetrics>--><!--Device-BackgroundLuminanceSamplingConfigs-region?: Edges<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## samplingInterval

```TypeScript
samplingInterval?: number
```

取色间隔，单位为毫秒，最小值180ms。

默认值：500

**类型：** number

**默认值：** 500

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundLuminanceSamplingConfigs-samplingInterval?: number--><!--Device-BackgroundLuminanceSamplingConfigs-samplingInterval?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

