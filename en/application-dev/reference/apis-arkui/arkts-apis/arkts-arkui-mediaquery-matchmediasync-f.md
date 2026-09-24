# matchMediaSync

## Modules to Import

```TypeScript
import { mediaquery } from '@kit.ArkUI';
```

## matchMediaSync

```TypeScript
function matchMediaSync(condition: string): MediaQueryListener
```

Sets the media query criteria and returns the corresponding listening handle.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getMediaQuery](arkts-arkui-arkui-uicontext-uicontext-c.md#getmediaquery) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [MediaQuery](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 7

**Deprecated since:** 18

**Substitutes:** matchMediaSync

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| condition | string | Yes | Media query condition. For details, see [Syntax](../../../ui/arkts-layout-development-media-query.md#syntax). |

**Return value:**

| Type | Description |
| --- | --- |
| [MediaQueryListener](arkts-arkui-mediaquery-mediaquerylistener-i.md) | Listening handle to a media event, which is used to register or unregister the listening callback. |

**Examples**

```TypeScript
import { mediaquery } from '@kit.ArkUI';

let listener: mediaquery.MediaQueryListener = mediaquery.matchMediaSync('(orientation: landscape)'); // Listen for landscape events.
```
