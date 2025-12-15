# MissionSnapshot (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

The module defines the snapshot of a mission. The snapshot can be obtained through [missionManager.getMissionSnapShot](js-apis-app-ability-missionManager-sys.md#missionmanagergetmissionsnapshot).

> **NOTE**
> 
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs of this module are system APIs and cannot be called by third-party applications.

## Modules to Import

```ts
import { missionManager } from '@kit.AbilityKit';
```

## MissionSnapshot

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| ability | ElementName | No| No| Ability information of the mission.| 
| snapshot | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | No| No| Snapshot of the mission.|

**Example**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos('', 10, (error, missions) => {
    if (error) {
      console.error(`getMissionInfos failed, error.code: ${JSON.stringify(error.code)}, error.message: ${JSON.stringify(error.message)}`);
      return;
    }
    console.info(`size = ${missions.length}`);
    console.info(`missions = ${JSON.stringify(missions)}`);
    let id = missions[0].missionId;

    missionManager.getMissionSnapShot('', id, (err, snapshot) => {
      if (err) {
        console.error(`getMissionSnapShot failed, err.code: ${JSON.stringify(err.code)}, err.message: ${JSON.stringify(err.message)}`);
        return;
      }
      // Carry out normal service processing.
      console.info(`bundleName = ${snapshot.ability.bundleName}`);
    });
  });
} catch (paramError) {
  console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
}
```
