# ComposeListItem

```TypeScript
export declare struct ComposeListItem
```

Creates a ComposeListItem component that allows customization of the left, center, and right content areas.

**Since:** 10

**Decorator:** @Component

<!--Device-unnamed-export declare struct ComposeListItem--><!--Device-unnamed-export declare struct ComposeListItem-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ComposeListItem, ContentItem, IconType, OperateButton, OperateCheck, OperateIcon, OperateItem } from '@kit.ArkUI';
```

## contentItem

```TypeScript
contentItem?: ContentItem
```

Elements on the left and in the center.

**Type:** [ContentItem](arkts-arkui-arkui-advanced-composelistitem-contentitem-c.md)

**Since:** 10

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ComposeListItem-contentItem?: ContentItem--><!--Device-ComposeListItem-contentItem?: ContentItem-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## operateItem

```TypeScript
operateItem?: OperateItem
```

Element on the right.

**Type:** [OperateItem](arkts-arkui-arkui-advanced-composelistitem-operateitem-c.md)

**Since:** 10

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ComposeListItem-operateItem?: OperateItem--><!--Device-ComposeListItem-operateItem?: OperateItem-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
