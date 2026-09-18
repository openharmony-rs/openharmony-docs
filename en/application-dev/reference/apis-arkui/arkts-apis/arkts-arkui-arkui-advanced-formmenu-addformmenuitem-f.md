# AddFormMenuItem

## Modules to Import

```TypeScript
import { AddFormMenuItem, FormMenuItemStyle, AddFormOptions } from '@kit.ArkUI';
```

## AddFormMenuItem

```TypeScript
export declare function AddFormMenuItem(
  want: Want,
  componentId: string,
  options?: AddFormOptions
): void
```

Build function of AddFormMenuItem.

**Since:** 12

**Decorator:** @Builder

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | The want of the form to publish. |
| componentId | string | Yes | The id of the component used to get form snapshot. |
| options | [AddFormOptions](arkts-arkui-arkui-advanced-formmenu-addformoptions-i.md) | No | Add form options. |
