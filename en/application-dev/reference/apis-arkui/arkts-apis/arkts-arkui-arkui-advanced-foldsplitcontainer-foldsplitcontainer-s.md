# FoldSplitContainer

```TypeScript
export declare struct FoldSplitContainer
```

The **FoldSplitContainer** component implements split-screen layout, providing region control for two-panel and three -panel layouts on foldable screens in the expanded state (device fully unfolded), hover state (device half-folded), and folded state (device fully folded). It is suitable for responsive layout adaptation scenarios in foldable screen apps, helping developers implement intelligent split-panel layouts across multiple screen states and improving user experience. For details about fold status, see [display.FoldStatus](arkts-arkui-display-foldstatus-e.md).

> **NOTE:** 
> 
> - When the window width is less than or equal to 600 vp, the split-screen layout is used by default. When the window width is greater than 600 vp, an expanded area can be supported in addition to the top-bottom split. When the window width is greater than 600 vp and the device is in landscape half-folded state, the hover state layout can be triggered. In the hover state layout, the crease area is avoided and the expanded area cannot cross the crease area. In the hover state, you can set not to display the expanded area. For details, see [Examples](../../../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-FoldSplitContainer.md#examples).

**Since:** 12

**Decorator:** @Component

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full
