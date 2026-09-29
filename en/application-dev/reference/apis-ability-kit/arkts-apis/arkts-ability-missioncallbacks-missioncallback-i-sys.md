# MissionCallback (System API)

```TypeScript
export interface MissionCallback
```

MissionCallback registered by app.

@interface MissionCallback

**Since:** 9

<!--Device-unnamed-export interface MissionCallback--><!--Device-unnamed-export interface MissionCallback-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## notifyMissionsChanged

```TypeScript
notifyMissionsChanged: NotifyMissionsChangedCallback
```

Called by system when mission changed.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

<!--Device-MissionCallback-notifyMissionsChanged: NotifyMissionsChangedCallback--><!--Device-MissionCallback-notifyMissionsChanged: NotifyMissionsChangedCallback-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Examples**

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';

// Register the mission listener.
distributedMissionManager.registerMissionListener(
  {
    deviceId: '123456'
  },
  {
    // Callback invoked when the mission changes, receiving the device ID.
    notifyMissionsChanged: (deviceId: string) => {
      console.info(`notifyMissionsChanged deviceId: ${JSON.stringify(deviceId)}`);
    },
    // Callback invoked when the snapshot changes, receiving the device ID and mission ID.
    notifySnapshot: (deviceId: string, mission: number) => {
      console.info(`notifySnapshot deviceId: ${JSON.stringify(deviceId)}`);
      console.info(`notifySnapshot mission: ${JSON.stringify(mission)}`);
    },
    // Callback invoked when the network is disconnected, receiving the device ID and network status.
    notifyNetDisconnect: (deviceId: string, state: number) => {
      console.info(`notifyNetDisconnect deviceId: ${JSON.stringify(deviceId)}`);
      console.info(`notifyNetDisconnect state: ${JSON.stringify(state)}`);
    }
  }
);
```

## notifyNetDisconnect

```TypeScript
notifyNetDisconnect: NotifyNetDisconnectCallback
```

Called by system when network disconnect.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

<!--Device-MissionCallback-notifyNetDisconnect: NotifyNetDisconnectCallback--><!--Device-MissionCallback-notifyNetDisconnect: NotifyNetDisconnectCallback-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Examples**

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';

// Register the mission listener.
distributedMissionManager.registerMissionListener(
  {
    deviceId: '123456'
  },
  {
    // Callback invoked when the mission changes, receiving the device ID.
    notifyMissionsChanged: (deviceId: string) => {
      console.info(`notifyMissionsChanged deviceId: ${JSON.stringify(deviceId)}`);
    },
    // Callback invoked when the snapshot changes, receiving the device ID and mission ID.
    notifySnapshot: (deviceId: string, mission: number) => {
      console.info(`notifySnapshot deviceId: ${JSON.stringify(deviceId)}`);
      console.info(`notifySnapshot mission: ${JSON.stringify(mission)}`);
    },
    // Callback invoked when the network is disconnected, receiving the device ID and network status.
    notifyNetDisconnect: (deviceId: string, state: number) => {
      console.info(`notifyNetDisconnect deviceId: ${JSON.stringify(deviceId)}`);
      console.info(`notifyNetDisconnect state: ${JSON.stringify(state)}`);
    }
  }
);
```

## notifySnapshot

```TypeScript
notifySnapshot: NotifySnapshotCallback
```

Called by system when snapshot changed.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

<!--Device-MissionCallback-notifySnapshot: NotifySnapshotCallback--><!--Device-MissionCallback-notifySnapshot: NotifySnapshotCallback-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Examples**

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';

// Register the mission listener.
distributedMissionManager.registerMissionListener(
  {
    deviceId: '123456'
  },
  {
    // Callback invoked when the mission changes, receiving the device ID.
    notifyMissionsChanged: (deviceId: string) => {
      console.info(`notifyMissionsChanged deviceId: ${JSON.stringify(deviceId)}`);
    },
    // Callback invoked when the snapshot changes, receiving the device ID and mission ID.
    notifySnapshot: (deviceId: string, mission: number) => {
      console.info(`notifySnapshot deviceId: ${JSON.stringify(deviceId)}`);
      console.info(`notifySnapshot mission: ${JSON.stringify(mission)}`);
    },
    // Callback invoked when the network is disconnected, receiving the device ID and network status.
    notifyNetDisconnect: (deviceId: string, state: number) => {
      console.info(`notifyNetDisconnect deviceId: ${JSON.stringify(deviceId)}`);
      console.info(`notifyNetDisconnect state: ${JSON.stringify(state)}`);
    }
  }
);
```
