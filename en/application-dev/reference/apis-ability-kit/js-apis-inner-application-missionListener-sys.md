# MissionListener (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

The module defines the listeners used to observe the mission status. The listeners can be registered by using [on](js-apis-app-ability-missionManager-sys.md#missionmanageronmission).

> **NOTE**
> 
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { missionManager } from '@kit.AbilityKit';
```

## MissionListener

### onMissionCreated

onMissionCreated(mission: number): void

Called when the system creates a mission.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| mission | number | Yes| Mission ID.|

**Example**

For details, see [onMissionClosed](#onmissionclosed9).

### onMissionDestroyed

onMissionDestroyed(mission: number): void

Called when the system destroys a mission.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| mission | number | Yes| Mission ID.|

**Example**

For details, see [onMissionClosed](#onmissionclosed9).

### onMissionSnapshotChanged

onMissionSnapshotChanged(mission: number): void

Called when the system updates the snapshot of a mission.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| mission | number | Yes| Mission ID.|

**Example**

For details, see [onMissionClosed](#onmissionclosed9).

### onMissionMovedToFront

onMissionMovedToFront(mission: number): void

Called when the system moves a mission to the foreground.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| mission | number | Yes| Mission ID.|

**Example**

For details, see [onMissionClosed](#onmissionclosed9).

### onMissionLabelUpdated<sup>9+</sup>

onMissionLabelUpdated(mission: number): void

Called when the system updates the label of a mission.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| mission | number | Yes| Mission ID.|

**Example**

For details, see [onMissionClosed](#onmissionclosed9).

### onMissionIconUpdated<sup>9+</sup>

onMissionIconUpdated(mission: number, icon: image.PixelMap): void

Called when the system updates the icon of a mission.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| mission | number | Yes| Mission ID.|
| icon | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | Yes| New mission icon.|

**Example**

For details, see [onMissionClosed](#onmissionclosed9).

### onMissionClosed<sup>9+</sup>

onMissionClosed(mission: number): void

Called when the system closes a mission.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| mission | number | Yes| Mission ID.|

**Example**
```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let listener: missionManager.MissionListener = {
  onMissionCreated: (mission) => {
    console.info(`onMissionCreated mission: ${JSON.stringify(mission)}`);
  },
  onMissionDestroyed: (mission) => {
    console.info(`onMissionDestroyed mission: ${JSON.stringify(mission)}`);
  },
  onMissionSnapshotChanged: (mission) => {
    console.info(`onMissionSnapshotChanged mission: ${JSON.stringify(mission)}`);
  },
  onMissionMovedToFront: (mission) => {
    console.info(`onMissionMovedToFront mission: ${JSON.stringify(mission)}`);
  },
  onMissionLabelUpdated: (mission) => {
    console.info(`onMissionLabelUpdated mission: ${JSON.stringify(mission)}`);
  },
  onMissionIconUpdated: (mission, icon) => {
    console.info(`onMissionIconUpdated mission: ${JSON.stringify(mission)}`);
    console.info(`onMissionIconUpdated icon: ${JSON.stringify(icon)}`);
  },
  onMissionClosed: (mission) => {
    console.info(`onMissionClosed mission: ${JSON.stringify(mission)}`);
  }
};

try {
  let listenerId = missionManager.on('mission', listener);
} catch (paramError) {
  console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
}
```
