# clearAllMissions (System API)

## Modules to Import

```TypeScript
import { missionManager } from '@kit.AbilityKit';
```

## clearAllMissions

```TypeScript
function clearAllMissions(callback: AsyncCallback<void>): void
```

Clears all unlocked missions. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.clearAllMissions((err: BusinessError) => {
    if (err) {
      console.error(`clearAllMissions failed. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('clearAllMissions successfully.');
    }
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`clearAllMissions failed. Code: ${err.code}, message: ${err.message}`);
}
```


<a id="clearallmissions-1"></a>

## clearAllMissions

```TypeScript
function clearAllMissions(): Promise<void>
```

Clears all unlocked missions. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.clearAllMissions().then((data: void) => {
    console.info(`clearAllMissions successfully. Data: ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`clearAllMissions failed. Code: ${err.code}, message: ${err.message}.`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`clearAllMissions failed. Code: ${err.code}, message: ${err.message}.`);
}
```
