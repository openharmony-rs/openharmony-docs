# SplitLayout

```TypeScript
export declare struct SplitLayout
```

The **SplitLayout** component is a split layout component that supports adaptive layout and displays different layout styles at different widths.

**Since:** 10

**Decorator:** @Component

<!--Device-unnamed-export declare struct SplitLayout--><!--Device-unnamed-export declare struct SplitLayout-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SplitLayout } from '@kit.ArkUI';
```

## container

```TypeScript
container: () => void
```

Container component used to host custom component content in the lower area of the layout. No return value.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SplitLayout-container: () => void--><!--Device-SplitLayout-container: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## mainImage

```TypeScript
mainImage: ResourceStr
```

Main image resource displayed in the upper area of the layout. Supports common image formats such as PNG, JPG, and SVG.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SplitLayout-mainImage: ResourceStr--><!--Device-SplitLayout-mainImage: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryText

```TypeScript
primaryText: ResourceStr
```

Primary title content, with no length limit. Displayed in the title area of the layout.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SplitLayout-primaryText: ResourceStr--><!--Device-SplitLayout-primaryText: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryText

```TypeScript
secondaryText?: ResourceStr
```

Secondary title content, with no length limit. Pass this parameter when a subtitle needs to be displayed below the title. If not passed, no subtitle is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SplitLayout-secondaryText?: ResourceStr--><!--Device-SplitLayout-secondaryText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## tertiaryText

```TypeScript
tertiaryText?: ResourceStr
```

Auxiliary text, with no length limit. Displayed below the subtitle area. Pass this parameter when auxiliary text needs to be displayed. If not passed, no auxiliary text is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SplitLayout-tertiaryText?: ResourceStr--><!--Device-SplitLayout-tertiaryText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
