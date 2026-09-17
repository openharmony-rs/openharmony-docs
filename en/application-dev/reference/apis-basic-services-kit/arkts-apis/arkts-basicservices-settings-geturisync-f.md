# getUriSync

## Modules to Import

```TypeScript
import { settings } from '@kit.BasicServicesKit';
```

## getUriSync

```TypeScript
function getUriSync(name: string): string
```

Get settingsdata uri (synchronous method)

**Since:** 8

**Deprecated since:** 26.0.0

**System capability:** SystemCapability.Applications.Settings.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Indicates the name of the setting to set. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns settingsdata uri. |

**Examples**

```TypeScript
// Obtain the URI of a data item.
let uriVar:string = settings.getUriSync(settings.display.SCREEN_BRIGHTNESS_STATUS);
```
