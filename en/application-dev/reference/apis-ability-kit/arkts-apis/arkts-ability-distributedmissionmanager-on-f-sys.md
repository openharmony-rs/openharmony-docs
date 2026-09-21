# on (System API)

## Modules to Import

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
```

## on('continueStateChange')

```TypeScript
function on(type: 'continueStateChange', callback: Callback<ContinueCallbackInfo>): void
```

Subscribes to continuation state change events of the current mission.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'continueStateChange' | Yes | Event type. The value **'continueStateChange'** indicates the continuation state change event of the current mission. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ContinueCallbackInfo](arkts-ability-distributedmissionmanager-continuecallbackinfo-i-sys.md)&gt; | Yes | Callback used to return the continuation state and information of the current mission.<br>**Since:** 11 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';

  try {
    // Register a listener for mission continuation state change events.
    distributedMissionManager.on('continueStateChange', (data) => {
      console.info("continueStateChange on:" + JSON.stringify(data));
    });
  } catch (error) {
    console.error(`continueStateChange failed. Code: ${error.code}, message: ${error.message}`);
  }
```
