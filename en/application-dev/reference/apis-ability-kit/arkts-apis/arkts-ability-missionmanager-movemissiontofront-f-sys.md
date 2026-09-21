# moveMissionToFront (System API)

## Modules to Import

```TypeScript
import { missionManager } from '@kit.AbilityKit';
```

## moveMissionToFront

```TypeScript
function moveMissionToFront(missionId: number, callback: AsyncCallback<void>): void
```

Switches a given mission to the foreground. This API uses an asynchronous callback to return the result.

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
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |

**Examples**

```TypeScript
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId is the mission ID. Obtain a valid mission ID through the getMissionInfos API.
let testMissionId = 2;

try {
  missionManager.moveMissionToFront(testMissionId, (err: BusinessError, data: void) => {
    if (err) {
      console.error(`moveMissionToFront failed. Code: ${err.code}, message: ${err.message}.`);
    } else {
      console.info(`moveMissionToFront successfully: ${JSON.stringify(data)}`);
    }
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`moveMissionToFront failed. Code: ${err.code}, message: ${err.message}.`);
}
```


<a id="movemissiontofront-1"></a>

## moveMissionToFront

```TypeScript
function moveMissionToFront(missionId: number, options: StartOptions, callback: AsyncCallback<void>): void
```

Switches a given mission to the foreground, with the startup parameters for the switching specified. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| missionId | number | Yes | Mission ID. |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | Yes | Startup parameters, which are used to specify the window mode and device ID for switching the mission to the foreground. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |

**Examples**

```TypeScript
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId is the mission ID, which can be obtained through the getMissionInfos API.
let testMissionId = 2;

try {
  missionManager.moveMissionToFront(testMissionId, { windowMode: 101 }, (err: BusinessError, data: void) => {
    if (err) {
      console.error(`moveMissionToFront failed. Code: ${err.code}, message: ${err.message}.`);
    } else {
      console.info(`moveMissionToFront successfully: ${JSON.stringify(data)}`);
    }
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`moveMissionToFront failed. Code: ${err.code}, message: ${err.message}.`);
}
```


<a id="movemissiontofront-2"></a>

## moveMissionToFront

```TypeScript
function moveMissionToFront(missionId: number, options?: StartOptions): Promise<void>
```

Switches a given mission to the foreground, with the startup parameters for the switching specified. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| missionId | number | Yes | Mission ID. |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | No | Startup parameters, which are used to specify the window mode and device ID for switching the mission to the foreground. By default, no value is passed in, indicating that the default startup parameters are used. |

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
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |

**Examples**

```TypeScript
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId is the mission ID. Obtain a valid mission ID through the getMissionInfos API.
let testMissionId = 2;

try {
  missionManager.moveMissionToFront(testMissionId).then((data: void) => {
    console.info(`moveMissionToFront successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`moveMissionToFront failed. Code: ${error.code}, message: ${error.message}.`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`moveMissionToFront failed. Code: ${err.code}, Cause: ${err.message}.`);
}
```
