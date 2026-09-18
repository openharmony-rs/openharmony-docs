# getLowResolutionMissionSnapShot (System API)

## Modules to Import

```TypeScript
import { missionManager } from '@kit.AbilityKit';
```

## getLowResolutionMissionSnapShot

```TypeScript
function getLowResolutionMissionSnapShot(
    deviceId: string,
    missionId: number,
    callback: AsyncCallback<MissionSnapshot>
  ): void
```

Obtains the low-resolution snapshot of a given mission. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Device ID. It is a null string by default for the local device. |
| missionId | number | Yes | Mission ID. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[MissionSnapshot](arkts-ability-missionmanager-missionsnapshot-t-sys.md)&gt; | Yes | Callback used to return the snapshot information obtained. |

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

// testMissionId is the mission ID. You can obtain a valid mission ID through the getMissionInfos API.
let testMissionId = 2;

try {
  missionManager.getLowResolutionMissionSnapShot('', testMissionId,
    (err: BusinessError, data: missionManager.MissionSnapshot) => {
      if (err) {
        console.error(`getLowResolutionMissionSnapShot failed. Code: ${err.code}, message: ${err.message}.`);
      } else {
        console.info(`getLowResolutionMissionSnapShot successfully: ${JSON.stringify(data)}`);
      }
    });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getLowResolutionMissionSnapShot failed. Code: ${err.code}, message: ${err.message}.`);
}
```

```TypeScript
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId is the mission ID, which can be obtained through the getMissionInfos API.
let testMissionId = 2;

try {
  missionManager.getLowResolutionMissionSnapShot('', testMissionId).then((data: missionManager.MissionSnapshot) => {
    console.info(`getLowResolutionMissionSnapShot successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`getLowResolutionMissionSnapShot failed. Code: ${error.code}, message: ${error.message}.`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getLowResolutionMissionSnapShot failed. Code: ${err.code}, message: ${err.message}.`);
}
```


## getLowResolutionMissionSnapShot

```TypeScript
function getLowResolutionMissionSnapShot(deviceId: string, missionId: number): Promise<MissionSnapshot>
```

Obtains the low-resolution snapshot of a given mission. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Device ID. It is a null string by default for the local device. |
| missionId | number | Yes | Mission ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[MissionSnapshot](arkts-ability-missionmanager-missionsnapshot-t-sys.md)&gt; | Promise used to return the snapshot information obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

See [getLowResolutionMissionSnapShot](#getlowresolutionmissionsnapshot)
