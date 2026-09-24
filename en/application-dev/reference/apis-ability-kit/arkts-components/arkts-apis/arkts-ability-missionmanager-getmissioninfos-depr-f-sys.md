# getMissionInfos (System API)

## Modules to Import

```TypeScript
```

## getMissionInfos

```TypeScript
function getMissionInfos(deviceId: string, numMax: number, callback: AsyncCallback<Array<MissionInfo>>): void
```

Obtains information about all missions. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getMissionInfos](arkts-ability-missionmanager-getmissioninfos-f-sys.md)

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Device ID. It is a null string by default for the local device. |
| numMax | number | Yes | Maximum number of missions whose information can be obtained. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[MissionInfo](arkts-ability-missioninfo-i-sys.md)&gt;&gt; | Yes | Callback used to return the array of mission information obtained. |

**Examples**

```TypeScript
import missionManager from '@ohos.application.missionManager';

// Obtain all mission information.
missionManager.getMissionInfos('', 10, (error, missions) => {
  if (error.code) {
    console.error(`getMissionInfos failed, error.code: ${error.code}, error.message: ${error.message}`);
    return;
  }
  console.info(`size = ${missions.length}`);
  console.info(`missions = ${JSON.stringify(missions)}`);
});
```


<a id="getmissioninfos-1"></a>

## getMissionInfos

```TypeScript
function getMissionInfos(deviceId: string, numMax: number): Promise<Array<MissionInfo>>
```

Obtains information about all missions. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getMissionInfos](arkts-ability-missionmanager-getmissioninfos-f-sys.md)

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Device ID. It is a null string by default for the local device. |
| numMax | number | Yes | Maximum number of missions whose information can be obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[MissionInfo](arkts-ability-missioninfo-i-sys.md)&gt;&gt; | Promise used to return the array of mission information obtained. |

**Examples**

```TypeScript
import missionManager from '@ohos.application.missionManager';
import { BusinessError } from '@ohos.base';

try {
  // Obtain all mission information.
  missionManager.getMissionInfos('', 10).then((data) => {
    console.info(`getMissionInfos successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`getMissionInfos failed. Cause: ${error.message}`);
  });
} catch (error) {
  console.error(`getMissionInfos failed. Cause: ${error.message}`);
}
```
