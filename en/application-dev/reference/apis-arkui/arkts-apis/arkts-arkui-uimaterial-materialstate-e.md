# MaterialState

```TypeScript
enum MaterialState
```

Enumerates the material enabling states, indicating the states of the application-level immersive system material configuration.

**Since:** 26.0.0

<!--Device-uiMaterial-enum MaterialState--><!--Device-uiMaterial-enum MaterialState-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

Default state. The immersive system material is enabled by default for the [Dialog](../../../ui/arkts-base-dialog-overview.md), [Toast](../../../ui/arkts-create-toast.md), and [AlphabetIndexer](../arkts-components/arkts-arkui-alphabetindexer-comp.md) components if the background color, blur, and shadow are not set for the components. The immersive system material is enabled by default for the text menu triggered by long-pressing or double-clicking after [copyOption](../arkts-components/arkts-arkui-text-comp-attribute.md#copyoption) is set in the [Text](../arkts-components/arkts-arkui-text-comp.md) component. For other components, whether the immersive system material is enabled is set by the application.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-MaterialState-DEFAULT = 0--><!--Device-MaterialState-DEFAULT = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ENABLE

```TypeScript
ENABLE = 1
```

Enabled state. The immersive system material is enabled by default for the [Dialog](../../../ui/arkts-base-dialog-overview.md), [Toast](../../../ui/arkts-create-toast.md), [AlphabetIndexer](../arkts-components/arkts-arkui-alphabetindexer-comp.md), [ChipGroup](arkts-arkui-arkui-advanced-chipgroup-chipgroup-s.md), [Chip](arkts-arkui-arkui-advanced-chip.md), [Select](../arkts-components/arkts-arkui-select-comp.md), [Menu Control](../arkts-components/arkts-arkui-common-comp.md), [Toggle](../arkts-components/arkts-arkui-toggle-comp.md), [SegmentButton](arkts-arkui-arkui-advanced-segmentbutton-segmentbutton-s.md), [SegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2.md), [Slider](../arkts-components/arkts-arkui-slider-comp.md), and [SelectionMenu](arkts-arkui-arkui-advanced-selectionmenu.md) components. After [copyOption](../arkts-components/arkts-arkui-text-comp-attribute.md#copyoption) is set for the [Text](../arkts-components/arkts-arkui-text-comp.md) component, the immersive system material is enabled by default for the text menu triggered by long-pressing or double-clicking. In this state, the immersive system material style takes precedence over the background color, blur, shadow, and border style set for the components. You need to set whether to enable the immersive system material for other components.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-MaterialState-ENABLE = 1--><!--Device-MaterialState-ENABLE = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DISABLE

```TypeScript
DISABLE = 2
```

Disabled state. The immersive system material cannot be enabled for any component. Even if you set the immersive system material parameters for a component, the settings will not take effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-MaterialState-DISABLE = 2--><!--Device-MaterialState-DISABLE = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
