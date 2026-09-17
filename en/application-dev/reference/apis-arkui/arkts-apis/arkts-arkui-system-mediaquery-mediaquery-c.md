# MediaQuery

Defines the MediaQuery API.

**Since:** 3

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SystemMediaQuery, MediaQueryEvent, MediaQueryList } from '@kit.ArkUI';
```

## matchMedia

```TypeScript
static matchMedia(condition: string): MediaQueryList
```

Creates a **MediaQueryList** object based on the query condition.

**Since:** 3

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| condition | string | Yes | Query condition. |

**Return value:**

| Type | Description |
| --- | --- |
| [MediaQueryList](arkts-arkui-system-mediaquery-mediaquerylist-i.md) | Created **MediaQueryList** object. For details, see the following description. |

**Examples**

```TypeScript
let mMediaQueryList = mediaquery.matchMedia('(max-width: 466)');
```
