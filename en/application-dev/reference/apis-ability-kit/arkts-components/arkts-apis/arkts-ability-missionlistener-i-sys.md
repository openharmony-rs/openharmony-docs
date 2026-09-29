# MissionListener (System API)

```TypeScript
export interface MissionListener
```

The module defines the listeners used to observe the mission status. The listeners can be registered by using [on](arkts-ability-missionmanager-on-f-sys.md).

**Since:** 8

<!--Device-unnamed-export interface MissionListener--><!--Device-unnamed-export interface MissionListener-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## onMissionClosed

```TypeScript
onMissionClosed(mission: number): void
```

Called when the system closes a mission.

**Since:** 9

<!--Device-MissionListener-onMissionClosed(mission: int): void--><!--Device-MissionListener-onMissionClosed(mission: int): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mission | number | Yes | Mission ID. |

**Examples**

```TypeScript
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Define the mission state listener object.
let listener: missionManager.MissionListener = {
  // Callback handling when a mission is created.
  onMissionCreated: (mission) => {
    console.info(`onMissionCreated mission: ${JSON.stringify(mission)}`);
  },
  // Callback handling when a mission is destroyed.
  onMissionDestroyed: (mission) => {
    console.info(`onMissionDestroyed mission: ${JSON.stringify(mission)}`);
  },
  // Callback handling when a mission snapshot is updated.
  onMissionSnapshotChanged: (mission) => {
    console.info(`onMissionSnapshotChanged mission: ${JSON.stringify(mission)}`);
  },
  // Callback handling when a mission is moved to the foreground.
  onMissionMovedToFront: (mission) => {
    console.info(`onMissionMovedToFront mission: ${JSON.stringify(mission)}`);
  },
  // Callback handling when a mission label is updated.
  onMissionLabelUpdated: (mission) => {
    console.info(`onMissionLabelUpdated mission: ${JSON.stringify(mission)}`);
  },
  // Callback handling when a mission icon is updated.
  onMissionIconUpdated: (mission, icon) => {
    console.info(`onMissionIconUpdated mission: ${JSON.stringify(mission)}`);
    console.info(`onMissionIconUpdated icon: ${JSON.stringify(icon)}`);
  },
  // Callback handling when a mission is closed.
  onMissionClosed: (mission) => {
    console.info(`onMissionClosed mission: ${JSON.stringify(mission)}`);
  }
};

try {
  // Register the mission state listener.
  let listenerId = missionManager.on('mission', listener);
} catch (paramError) {
  console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
}
```

## onMissionCreated

```TypeScript
onMissionCreated(mission: number): void
```

Called when the system creates a mission.

**Since:** 8

<!--Device-MissionListener-onMissionCreated(mission: int): void--><!--Device-MissionListener-onMissionCreated(mission: int): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mission | number | Yes | Mission ID. |

**Examples**

For details, see [onMissionClosed](#onmissionclosed).

## onMissionDestroyed

```TypeScript
onMissionDestroyed(mission: number): void
```

Called when the system destroys a mission.

**Since:** 8

<!--Device-MissionListener-onMissionDestroyed(mission: int): void--><!--Device-MissionListener-onMissionDestroyed(mission: int): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mission | number | Yes | Mission ID. |

**Examples**

For details, see [onMissionClosed](#onmissionclosed).

## onMissionIconUpdated

```TypeScript
onMissionIconUpdated(mission: number, icon: image.PixelMap): void
```

Called when the system updates the icon of a mission.

**Since:** 9

<!--Device-MissionListener-onMissionIconUpdated(mission: int, icon: image.PixelMap): void--><!--Device-MissionListener-onMissionIconUpdated(mission: int, icon: image.PixelMap): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mission | number | Yes | Mission ID. |
| icon | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | New mission icon. |

**Examples**

For details, see [onMissionClosed](#onmissionclosed).

## onMissionLabelUpdated

```TypeScript
onMissionLabelUpdated(mission: number): void
```

Called when the system updates the label of a mission.

**Since:** 9

<!--Device-MissionListener-onMissionLabelUpdated(mission: int): void--><!--Device-MissionListener-onMissionLabelUpdated(mission: int): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mission | number | Yes | Mission ID. |

**Examples**

For details, see [onMissionClosed](#onmissionclosed).

## onMissionMovedToFront

```TypeScript
onMissionMovedToFront(mission: number): void
```

Called when the system moves a mission to the foreground.

**Since:** 8

<!--Device-MissionListener-onMissionMovedToFront(mission: int): void--><!--Device-MissionListener-onMissionMovedToFront(mission: int): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mission | number | Yes | Mission ID. |

**Examples**

For details, see [onMissionClosed](#onmissionclosed).

## onMissionSnapshotChanged

```TypeScript
onMissionSnapshotChanged(mission: number): void
```

This callback is triggered when the system updates the task thumbnail of a mission.

**Since:** 8

<!--Device-MissionListener-onMissionSnapshotChanged(mission: int): void--><!--Device-MissionListener-onMissionSnapshotChanged(mission: int): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mission | number | Yes | Indicates the mission ID. |

**Examples**

For details, see [onMissionClosed](#onmissionclosed).
