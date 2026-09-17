# @ohos.mediaquery

The **mediaquery** module provides different styles for different media types.

> **NOTE:** 
> 
> - This module cannot be used in the file declaration of the [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md). In other words, the APIs of this module can be used only after a component instance is created; they cannot be called in the lifecycle of the UIAbility.
> 
> - The functionality of this module depends on UI context. This means that the APIs of this module cannot be used where [the UI context is ambiguous](../../../ui/arkts-global-interface.md#ambiguous-ui-context). For details, see [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md).

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { mediaquery } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [matchMediaSync](arkts-arkui-mediaquery-matchmediasync-f.md) | Sets the media query condition. This API returns the corresponding media query listener. |

### Interfaces

| Name | Description |
| --- | --- |
| [MediaQueryListener](arkts-arkui-mediaquery-mediaquerylistener-i.md) | Implements the media query listener, including the first query result when the listener is applied for. The specified media query condition, for example, **'(width &lt;= 600vp)'**, is compared system information. If related information is not initialized during the first query, **matches** returns **false**. |
| [MediaQueryResult](arkts-arkui-mediaquery-mediaqueryresult-i.md) | Provides the media query result. |
