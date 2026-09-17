# clearMission (System API)

## Modules to Import

```TypeScript
```

## clearMission

```TypeScript
function clearMission(missionId: number, callback: AsyncCallback<void>): void
```

Clears a given mission, regardless of whether it is locked. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [clearMission](arkts-ability-missionmanager-clearmission-f-sys.md)

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| missionId | number | Yes | Mission ID. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the mission is cleared, **err** is **undefined**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import missionManager from '@ohos.application.missionManager';
import { BusinessError } from '@ohos.base';

let testMissionId = 2;
try {
  // Clear the specified mission.
  missionManager.clearMission(testMissionId, (err, data) => {
    if (err) {
      console.error(`clearMission failed. Code: ${err.code}, message: ${err.message}.`);
    } else {
      console.info(`clearMission successfully. Data: ${JSON.stringify(data)}`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`clearMission sync failed. Code: ${error.code}, message: ${error.message}.`);
}
```

```TypeScript
import missionManager from '@ohos.application.missionManager';
import { BusinessError } from '@ohos.base';

let testMissionId = 2;
try {
  // Clear the specified mission.
  missionManager.clearMission(testMissionId).then((data) => {
    console.info(`clearMission successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`clearMission failed. Code: ${error.code}, message: ${error.message}.`);
  });
} catch (error) {
  let err = error as BusinessError;
  console.error(`clearMission sync failed. Code: ${err.code}, message: ${err.message}.`);
}
```


## clearMission

```TypeScript
function clearMission(missionId: number): Promise<void>
```

Clears a given mission, regardless of whether it is locked. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [clearMission](arkts-ability-missionmanager-clearmission-f-sys.md)

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

**Examples**

See [clearMission](#clearmission)
