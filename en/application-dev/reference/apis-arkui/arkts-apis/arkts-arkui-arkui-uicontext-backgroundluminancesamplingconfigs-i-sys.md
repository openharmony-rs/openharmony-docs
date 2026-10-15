# BackgroundLuminanceSamplingConfigs (System API)

```TypeScript
export interface BackgroundLuminanceSamplingConfigs
```

Defines the background luminance sampling parameter configuration.

**Since:** 23

<!--Device-unnamed-export interface BackgroundLuminanceSamplingConfigs--><!--Device-unnamed-export interface BackgroundLuminanceSamplingConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

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

Light brightness threshold. The value is an integer in the range [0, 255]. The light brightness threshold must be greater than the dark brightness threshold. When you need to adjust the sensitivity of light‑color detection, you can customize this value. A lower value makes the light‑color detection more lenient, while a higher value makes it more stringent.

Default value: 220

**Type:** number

**Default:** 220

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackgroundLuminanceSamplingConfigs-brightThreshold?: number--><!--Device-BackgroundLuminanceSamplingConfigs-brightThreshold?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## darkThreshold

```TypeScript
darkThreshold?: number
```

Dark brightness threshold. The value is an integer in the range [0, 255]. The dark brightness threshold must be less than the light brightness threshold. When you need to adjust the sensitivity of dark‑color detection, you can customize this value. A higher value makes the dark‑color detection more lenient, while a lower value makes it more stringent.

Default value: 150

**Type:** number

**Default:** 150

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackgroundLuminanceSamplingConfigs-darkThreshold?: number--><!--Device-BackgroundLuminanceSamplingConfigs-darkThreshold?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## region

```TypeScript
region?: Edges<LengthMetrics>
```

Offset of the sampling area relative to the component, calculated based on the upper left corner of the component. It is recommended to set the sampling area within the visible range to avoid inaccurate sampling results caused by excessive offset.

The component's own region is used by default.

**Type:** [Edges](arkts-arkui-graphics-edges-i.md)&lt;[LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackgroundLuminanceSamplingConfigs-region?: Edges<LengthMetrics>--><!--Device-BackgroundLuminanceSamplingConfigs-region?: Edges<LengthMetrics>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## samplingInterval

```TypeScript
samplingInterval?: number
```

Sampling interval, in milliseconds. Value range: ≥180 ms. Set a smaller value (for example, 180–300 ms) when more frequent background color sampling responses are needed, and set a larger value (for example, 500–1000 ms) to conserve system resources.

Default value: 500 ms

**Type:** number

**Default:** 500

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackgroundLuminanceSamplingConfigs-samplingInterval?: number--><!--Device-BackgroundLuminanceSamplingConfigs-samplingInterval?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
