# MaterialState

Enumerates the material enabling states, indicating the states of the application-level immersive system material configuration.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

Default state. The immersive system material is enabled by default for the [Dialog](../../../ui/arkts-base-dialog-overview.md), [Toast](../../../ui/arkts-create-toast.md), and AlphabetIndexer components if the background color, blur, and shadow are not set for the components. The immersive system material is enabled by default for the text menu triggered by long-pressing or double-clicking after copyOption is set in the Text component. For other components, whether the immersive system material is enabled is set by the application.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ENABLE

```TypeScript
ENABLE = 1
```

Enabled state. The immersive system material is enabled by default for the [Dialog](../../../ui/arkts-base-dialog-overview.md), [Toast](../../../ui/arkts-create-toast.md), AlphabetIndexer, [ChipGroup](arkts-arkui-arkui-advanced-chipgroup-chipgroup-s.md), Chip, Select, Menu Control, Toggle, [SegmentButton](arkts-arkui-arkui-advanced-segmentbutton-segmentbutton-s.md), SegmentButtonV2, Slider, [bindSheet](../arkts-components/arkts-arkui-commonmethod-c.md#bindsheet), and SelectionMenu. After copyOption is set for the Text component, the immersive system material is enabled by default for the text menu triggered by long-pressing or double-clicking. In this state, the immersive system material style takes precedence over the background color, blur, shadow, and border style set for the components. You need to set whether to enable the immersive system material for other components.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DISABLE

```TypeScript
DISABLE = 2
```

Disabled state. The immersive system material cannot be enabled for any component. Even if you set the immersive system material parameters for a component, the settings will not take effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
