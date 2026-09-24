# lockMission (System API)

## Modules to Import

```TypeScript
```

## lockMission

```TypeScript
function lockMission(missionId: number, callback: AsyncCallback<void>): void
```

Locks a given mission. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [lockMission](arkts-ability-missionmanager-lockmission-f-sys.md)

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| missionId | number | Yes | Mission ID. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the mission is locked, **err** is **undefined**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import missionManager from '@ohos.application.missionManager';
import { BusinessError } from '@ohos.base';

let testMissionId = 2;
try {
  // Lock the specified mission.
  missionManager.lockMission(testMissionId, (err, data) => {
    if (err) {
      console.error(`lockMission failed. Code: ${err.code}, message: ${err.message}.`);
    } else {
      console.info(`lockMission successfully. Data: ${JSON.stringify(data)}`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`lockMission sync failed. Code: ${error.code}, message: ${error.message}.`);
}
```


<a id="lockmission-1"></a>

## lockMission

```TypeScript
function lockMission(missionId: number): Promise<void>
```

Locks a given mission. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [lockMission](arkts-ability-missionmanager-lockmission-f-sys.md)

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

```TypeScript
import missionManager from '@ohos.application.missionManager';
import { BusinessError } from '@ohos.base';

let testMissionId = 2;
try {
  // Lock the specified mission.
  missionManager.lockMission(testMissionId).then((data) => {
    console.info(`lockMission successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`lockMission failed. Code: ${error.code}, message: ${error.message}.`);
  });
} catch (error) {
  let err = error as BusinessError;
  console.error(`lockMission sync failed. Code: ${err.code}, message: ${err.message}.`);
}
```
