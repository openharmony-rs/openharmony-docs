# clearMission (System API)

## Modules to Import

```TypeScript
import { missionManager } from '@kit.AbilityKit';
```

## clearMission

```TypeScript
function clearMission(missionId: number, callback: AsyncCallback<void>): void
```

Clears a given mission, regardless of whether it is locked. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| missionId | number | Yes | Mission ID. |
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

// testMissionId is the mission ID, which can be obtained through the getMissionInfos API to get a real and valid mission ID.
let testMissionId = 2;

try {
  missionManager.clearMission(testMissionId, (err: BusinessError, data: void) => {
    if (err) {
      console.error(`clearMission failed. Code: ${err.code}, message: ${err.message}.`);
    } else {
      console.info(`clearMission successfully: ${JSON.stringify(data)}`);
    }
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`clearMission failed. Code: ${err.code}, message: ${err.message}.`);
}
```


<a id="clearmission-1"></a>

## clearMission

```TypeScript
function clearMission(missionId: number): Promise<void>
```

Clears a given mission, regardless of whether it is locked. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| missionId | number | Yes | Mission ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

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

// testMissionId is the mission ID, which can be obtained through the getMissionInfos API.
let testMissionId = 2;

try {
  missionManager.clearMission(testMissionId).then((data: void) => {
    console.info(`clearMission successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`clearMission failed. Code: ${error.code}, message: ${error.message}.`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`clearMission failed. Code: ${err.code}, message: ${err.message}.`);
}
```
