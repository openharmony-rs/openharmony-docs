# isDoNotDisturbEnabled

## Modules to Import

```TypeScript
import { intelligentScene } from '@kit.BasicServicesKit';
```

## isDoNotDisturbEnabled

```TypeScript
function isDoNotDisturbEnabled(): Promise<boolean>
```

Checks whether Do Not Disturb is enabled on this device. The Do Not Disturb state defines if notifications are allowed to interrupt the user (e.g. via sound & vibration) and is applied globally.

**Since:** 23

**Required permissions:** ohos.permission.GET_DONOTDISTURB_STATE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Applications.IntelligentScene

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Returns whether Do Not Disturb is enabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [35200001](../errorcode-intelligentScene.md#35200001-internal-error) | Internal error. |

**Examples**

```TypeScript
import { BusinessError, intelligentScene } from '@kit.BasicServicesKit';

async function isDoNotDisturbEnabled(): Promise<boolean> {
  let isDoNotDisturbEnabled: boolean = false;
  try {
    isDoNotDisturbEnabled = await intelligentScene.isDoNotDisturbEnabled();
  } catch (err) {
    console.error(`Failed to get doNotDisturb state, code: ${err.code}, message: ${err.message}`);
  }
  if (isDoNotDisturbEnabled) {
    console.info('DoNotDisturb state is open');
  } else {
    console.info('DoNotDisturb state is closed');
  }
  return isDoNotDisturbEnabled;
}
```
