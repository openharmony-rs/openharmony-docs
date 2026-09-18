# @ohos.arkui.advanced.PopupV2

## Modules to Import

```TypeScript
import { PopupV2, PopupV2InitInfo, PopupV2Button } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [PopupV2](arkts-arkui-arkui-advanced-popupv2-popupv2-f.md) | Build function of PopupV2. This component is implemented based on state management V2 Compared with Popup, PopupV2 offers a higher level of observation and management over data objects. |

### Interfaces

| Name | Description |
| --- | --- |
| [PopupV2Button](arkts-arkui-arkui-advanced-popupv2-popupv2button-i.md) | Defines the popup button |
| [PopupV2InitInfo](arkts-arkui-arkui-advanced-popupv2-popupv2initinfo-i.md) | Defines the popup init info. |

## Examples

```TypeScript
### Example 1: Setting the Popup Style

This example implements the popup style by configuring [titleModifier](arkts-arkui-arkui-advanced-popupv2-popupv2initinfo-i.md), [messageModifier](arkts-arkui-arkui-advanced-popupv2-popupv2initinfo-i.md), and [PopupV2Button](arkts-arkui-arkui-advanced-popupv2-popupv2button-i.md).

Since API version 26.0.0, titleModifier, messageModifier, and PopupV2Button are added.


```

```TypeScript
### Example 2: Setting Layout Direction

This example implements a mirrored layout effect by configuring [direction](arkts-arkui-arkui-advanced-popupv2-popupv2initinfo-i.md), suitable for RTL (right-to-left) layout requirements in internationalization scenarios.

Since API version 26.0.0, the direction parameter is added.


```

```TypeScript
### Example 3: Setting a Custom Width

This example implements a custom width effect by configuring [maxWidth](arkts-arkui-arkui-advanced-popupv2-popupv2initinfo-i.md), suitable for scenarios such as long message notifications that require adjusting the display width.

Since API version 26.0.0, the maxWidth parameter is added.
```
