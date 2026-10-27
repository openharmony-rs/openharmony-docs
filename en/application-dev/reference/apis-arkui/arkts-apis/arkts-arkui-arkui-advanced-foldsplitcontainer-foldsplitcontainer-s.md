# FoldSplitContainer

```TypeScript
export declare struct FoldSplitContainer
```

Implements region control for the two-panel split-screen layout (primary area + secondary area) and three-panel layout (primary area + secondary area + expanded area) on foldable screens in the expanded, hover, and folded states.

**Since:** 12

**Decorator:** @Component

<!--Device-unnamed-export declare struct FoldSplitContainer--><!--Device-unnamed-export declare struct FoldSplitContainer-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ExtraRegionPosition, ExpandedRegionLayoutOptions, HoverModeRegionLayoutOptions, FoldedRegionLayoutOptions, PresetSplitRatio, FoldSplitContainer, HoverModeStatus, OnHoverStatusChangeHandler, } from '@kit.ArkUI';
```

## onHoverStatusChange

```TypeScript
onHoverStatusChange?: OnHoverStatusChangeHandler
```

Callback function triggered when the foldable screen enters or exits hover mode. When not passed, no callback is made for hover state changes.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-FoldSplitContainer-onHoverStatusChange?: OnHoverStatusChangeHandler--><!--Device-FoldSplitContainer-onHoverStatusChange?: OnHoverStatusChangeHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## animationOptions

```TypeScript
animationOptions?: AnimateParam | null
```

Parameters for setting animation effects. The value **null** indicates that animation is disabled.

Default value: **null**

**Type:** [AnimateParam](../arkts-components/arkts-arkui-common-comp-animateparam-i.md) &#124; null

**Since:** 12

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-FoldSplitContainer-animationOptions?: AnimateParam | null--><!--Device-FoldSplitContainer-animationOptions?: AnimateParam | null-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## expandedLayoutOptions

```TypeScript
expandedLayoutOptions: ExpandedRegionLayoutOptions
```

Expanded state layout information, used to control whether the expanded area spans through, the area ratio, and the position in the expanded state of a foldable screen. The expanded area is supported when the window width is greater than 600 vp.

**Type:** [ExpandedRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-expandedregionlayoutoptions-i.md)

**Since:** 12

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-FoldSplitContainer-expandedLayoutOptions: ExpandedRegionLayoutOptions--><!--Device-FoldSplitContainer-expandedLayoutOptions: ExpandedRegionLayoutOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## extra

```TypeScript
extra?: Callback<void>
```

Callback function for building the UI content of the expanded area. Pass this parameter when a three-column layout or an additional content area is needed. This parameter can be omitted when no expanded area is required. This callback function has no parameters and no return value. When not passed, no corresponding area is displayed.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt;

**Since:** 12

**Decorator:** @BuilderParam

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-FoldSplitContainer-extra?: Callback<void>--><!--Device-FoldSplitContainer-extra?: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## foldedLayoutOptions

```TypeScript
foldedLayoutOptions: FoldedRegionLayoutOptions
```

Folded state layout information, used to control the height ratio between the primary area and the secondary area in the folded state of a foldable screen. This takes effect when the device is in the folded state. A split- screen layout is used by default when the window width is less than or equal to 600 vp.

**Type:** [FoldedRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-foldedregionlayoutoptions-i.md)

**Since:** 12

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-FoldSplitContainer-foldedLayoutOptions: FoldedRegionLayoutOptions--><!--Device-FoldSplitContainer-foldedLayoutOptions: FoldedRegionLayoutOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hoverModeLayoutOptions

```TypeScript
hoverModeLayoutOptions: HoverModeRegionLayoutOptions
```

Hover state layout information, used to control whether the expanded area is displayed, the area ratio, and the position in the semi-folded hover state of a foldable screen. The hover state layout is triggered when the window width is greater than 600 vp and the device is in landscape semi-folded state.

**Type:** [HoverModeRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-hovermoderegionlayoutoptions-i.md)

**Since:** 12

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-FoldSplitContainer-hoverModeLayoutOptions: HoverModeRegionLayoutOptions--><!--Device-FoldSplitContainer-hoverModeLayoutOptions: HoverModeRegionLayoutOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primary

```TypeScript
primary: Callback<void>
```

Callback function for building the UI content of the primary area. This callback function has no parameters and no return value, and is invoked during component layout.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt;

**Since:** 12

**Decorator:** @BuilderParam

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-FoldSplitContainer-primary: Callback<void>--><!--Device-FoldSplitContainer-primary: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondary

```TypeScript
secondary: Callback<void>
```

Callback function for building the UI content of the secondary area. This callback function has no parameters and no return value, and is invoked during component layout.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt;

**Since:** 12

**Decorator:** @BuilderParam

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-FoldSplitContainer-secondary: Callback<void>--><!--Device-FoldSplitContainer-secondary: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
