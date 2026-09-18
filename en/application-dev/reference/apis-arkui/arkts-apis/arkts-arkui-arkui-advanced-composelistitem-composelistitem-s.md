# ComposeListItem

The **ComposeListItem** component is a container that presents a series of items arranged in a column with the same width. You can use it to present data of the same type in a multiple and coherent row style, for example, images or text.

> **NOTE:** 
> 
> - This component can be used only in the stage model.
> 
> - If the **ComposeListItem** component has universal attributes and universal events configured, the compiler toolchain automatically generates an additional \_\_Common\_\_ node and mounts the universal attributes and universal events on this node rather than the **ComposeListItem** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **ComposeListItem** component.

**Since:** 10

**Decorator:** @Component

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full
