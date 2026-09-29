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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 13.

<!--Device-customConfig-function getChannelId(): string--><!--Device-customConfig-function getChannelId(): string-End-->

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
