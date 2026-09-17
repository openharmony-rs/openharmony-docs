# isNotifyAllowedInDoNotDisturb

## Modules to Import

```TypeScript
import { intelligentScene } from '@kit.BasicServicesKit';
```

## isNotifyAllowedInDoNotDisturb

```TypeScript
function isNotifyAllowedInDoNotDisturb(): Promise<boolean>
```

Checks whether calling bundle is allow notify(e.g. sound & vibration) when system Do Not Disturb is on.

**Since:** 23

**Required permissions:** ohos.permission.GET_DONOTDISTURB_STATE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Applications.IntelligentScene

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Returns whether notify in Do Not Disturb mode is Allowed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [35200001](../errorcode-intelligentScene.md#35200001-internal-error) | Internal error. |

**Examples**

```TypeScript
import { BusinessError, intelligentScene } from '@kit.BasicServicesKit';

async function isNotifyAllowedInDoNotDisturb(): Promise<boolean> {
  let isNotifyAllowedInDoNotDisturb: boolean = false;
  try {
    isNotifyAllowedInDoNotDisturb = await intelligentScene.isNotifyAllowedInDoNotDisturb();
  } catch (err) {
    console.error(`Failed to get doNotDisturb state, code: ${err.code}, message: ${err.message}`);
  }
  if (isNotifyAllowedInDoNotDisturb) {
    console.info('Allowed to notify in doNotDisturb state');
  } else {
    console.info('Not allowed to notify in doNotDisturb state or doNotDisturb is closed');
  }
  return isNotifyAllowedInDoNotDisturb;
}
```
