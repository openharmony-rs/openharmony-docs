# getSystemPasteboard

## Modules to Import

```TypeScript
import { pasteboard } from '@kit.BasicServicesKit';
```

## getSystemPasteboard

```TypeScript
function getSystemPasteboard(): SystemPasteboard
```

Obtains **SystemPasteboard** object.

**Since:** 6

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-pasteboard-function getSystemPasteboard(): SystemPasteboard--><!--Device-pasteboard-function getSystemPasteboard(): SystemPasteboard-End-->

**System capability:** SystemCapability.MiscServices.Pasteboard

**Return value:**

| Type | Description |
| --- | --- |
| [SystemPasteboard](arkts-basicservices-pasteboard-systempasteboard-i.md) | **SystemPasteboard** object. |

**Examples**

```TypeScript
// Obtain the SystemPasteboard object.
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
```
