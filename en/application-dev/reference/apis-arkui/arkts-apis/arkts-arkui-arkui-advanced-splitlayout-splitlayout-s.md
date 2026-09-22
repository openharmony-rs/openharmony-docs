# SplitLayout

```TypeScript
export declare struct SplitLayout
```

The **SplitLayout** component provides common page layout styles, mainly used to display combined layouts of images, titles, and content containers. It is suitable for split display scenarios that require adaptation to different screen sizes (such as detail pages, settings pages, etc.). It supports adaptation to different screen widths (three layouts: ≤ 600 vp, &gt; 600 vp and ≤ 840 vp, &gt; 840 vp), addressing the need to display different layout styles on devices of different sizes, improving page adaptability and user experience.

> **NOTE:** 
> 
> - This component can only be used in the stage model.
> 
> - **SplitLayout** does not support setting [universal attributes](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md) and [universal events](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md). If set, the build toolchain will generate an additional \_\_Common\_\_ node and attach the universal attributes or universal events to \_\_Common\_\_ instead of directly applying them to **SplitLayout** itself, causing the configured attributes or events to not take effect.

The [universal events](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md) are not supported.

[Universal attributes](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md) are not supported.

**Since:** 10

**Decorator:** @Component

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full
