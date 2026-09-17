# startSyncRemoteMissions (System API)

## Modules to Import

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
```

## startSyncRemoteMissions

```TypeScript
function startSyncRemoteMissions(parameter: MissionParameter, callback: AsyncCallback<void>): void
```

Starts to synchronize the remote mission list. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parameter | [MissionParameter](arkts-ability-distributedmissionmanager-missionparameter-t-sys.md) | Yes | Parameters required for synchronization. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the synchronization is started, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Start synchronization of the mission list of the remote device.
  distributedMissionManager.startSyncRemoteMissions(
    {
      deviceId: "",
      fixConflict: false,
      tag: 0
    },
    (error: BusinessError) => {
      if (error) {
        console.error(`startSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info('startSyncRemoteMissions finished');}
  )
} catch (error) {
  console.error(`startSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
}
```

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  distributedMissionManager.startSyncRemoteMissions(
    {
      deviceId: "",
      fixConflict: false,
      tag: 0
    }
  ).then(() => {
      console.info('startSyncRemoteMissions finished successfully');
    }).catch((error: BusinessError) => {
    console.error(`startSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`startSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
}
```


## startSyncRemoteMissions

```TypeScript
function startSyncRemoteMissions(parameter: MissionParameter): Promise<void>
```

Starts to synchronize the remote mission list. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parameter | [MissionParameter](arkts-ability-distributedmissionmanager-missionparameter-t-sys.md) | Yes | Parameters required for synchronization. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

See [startSyncRemoteMissions](#startsyncremotemissions)
