# registerMissionListener (System API)

## Modules to Import

```TypeScript
```

## registerMissionListener

```TypeScript
function registerMissionListener(listener: MissionListener): number
```

Registers a listener to observe the mission status.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](arkts-ability-missionmanager-on-f-sys.md)

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| listener | [MissionListener](arkts-ability-missionlistener-i-sys.md) | Yes | Mission status listener to register. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the mission status listener, which is created by the system and allocated when the listener is registered. |

**Examples**

```TypeScript
import missionManager from '@ohos.application.missionManager';

console.info('registerMissionListener');
// Register a system mission status listener.
let listenerId = missionManager.registerMissionListener({
  onMissionCreated: (mission) => {
    console.info('--------onMissionCreated-------');
  },
  onMissionDestroyed: (mission) => {
    console.info('--------onMissionDestroyed-------');
  },
  onMissionSnapshotChanged: (mission) => {
    console.info('--------onMissionSnapshotChanged-------');
  },
  onMissionMovedToFront: (mission) => {
    console.info('--------onMissionMovedToFront-------');
  },
  onMissionIconUpdated: (mission, icon) => {
    console.info('--------onMissionIconUpdated-------');
  },
  onMissionClosed: (mission) => {
    console.info('--------onMissionClosed-------');
  },
  onMissionLabelUpdated: (mission) => {
    console.info('--------onMissionLabelUpdated-------');
  }
});
```
