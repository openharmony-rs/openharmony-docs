# getChannelId

## Modules to Import

```TypeScript
import { customConfig } from '@kit.BasicServicesKit';
```

## getChannelId

```TypeScript
function getChannelId(): string
```

Obtains a pre-installed channel ID of this application.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Customization.CustomConfig

**Return value:**

| Type | Description |
| --- | --- |
| string | Channel ID obtained. |

**Examples**

```TypeScript
import { customConfig } from '@kit.BasicServicesKit';

let channelId: string = customConfig.getChannelId();
console.info('app channelId is ' + channelId);
```
