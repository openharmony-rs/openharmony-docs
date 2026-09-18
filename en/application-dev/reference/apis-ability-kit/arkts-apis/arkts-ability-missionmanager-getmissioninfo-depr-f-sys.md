# getMissionInfo (System API)

## Modules to Import

```TypeScript
```

## getMissionInfo

```TypeScript
function getMissionInfo(deviceId: string, missionId: number, callback: AsyncCallback<MissionInfo>): void
```

Obtains the information about a given mission. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getMissionInfo](arkts-ability-missionmanager-getmissioninfo-f-sys.md)

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Device ID. It is a null string by default for the local device. |
| missionId | number | Yes | Mission ID. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[MissionInfo](arkts-ability-missioninfo-i-sys.md)&gt; | Yes | Callback used to return the mission information obtained. |

**Examples**

```TypeScript
import missionManager from '@ohos.application.missionManager';

let missionId: number = 0;

// Obtain information about the specified mission.
missionManager.getMissionInfo('', missionId, (error, mission) => {
  if (error.code) {
    console.error(`getMissionInfo failed, error.code: ${error.code}, error.message: ${error.message}`);
    return;
  }

  console.info(`mission.missionId = ${mission.missionId}`);
  console.info(`mission.runningState = ${mission.runningState}`);
  console.info(`mission.lockedState = ${mission.lockedState}`);
  console.info(`mission.timestamp = ${mission.timestamp}`);
  console.info(`mission.label = ${mission.label}`);
  console.info(`mission.iconPath = ${mission.iconPath}`);
});
```

```TypeScript
import missionManager from '@ohos.application.missionManager';
import { BusinessError } from '@ohos.base';

let testMissionId = 1;
try {
  // Obtain information about the specified mission.
  missionManager.getMissionInfo('', testMissionId).then((data) => {
    console.info(`getMissionInfo successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`getMissionInfo failed. Cause: ${error.message}`);
  });
} catch (error) {
  console.error(`getMissionInfo failed. Cause: ${error.message}`);
}
```


## getMissionInfo

```TypeScript
function getMissionInfo(deviceId: string, missionId: number): Promise<MissionInfo>
```

Obtains the information about a given mission. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getMissionInfo](arkts-ability-missionmanager-getmissioninfo-f-sys.md)

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
| Promise&lt;[MissionInfo](arkts-ability-missioninfo-i-sys.md)&gt; | Promise used to return the mission information obtained. |

**Examples**

See [getMissionInfo](#getmissioninfo)
