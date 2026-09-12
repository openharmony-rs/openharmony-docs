# MissionCallbacks (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=165f415429b5c50e77e8467a2b377e5000c44425 translatedAt=2026-09-03T11:59:32.505Z pushedAt=2026-09-05T10:47:30.842Z -->

The module defines the callbacks invoked after synchronization starts. These callbacks can be used as input parameters in [registerMissionListener](js-apis-distributedMissionManager-sys.md#distributedmissionmanagerregistermissionlistener).

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs provided by this module are system APIs.
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { distributedMissionManager } from '@kit.AbilityKit';
```

## MissionCallback.notifyMissionsChanged

notifyMissionsChanged(deviceId: string): void

notifyMissionsChanged is a callback function for mission listening, used to notify mission changes. It is used to listen for mission status changes on remote devices in multi-device collaboration scenarios, such as the task manager and multi-screen collaboration. For example, cross-device mission switching and mission list synchronization.

**Device behavior difference** This API does not take effect on Wearable devices that do not support distributed service.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**Parameters**

| Name| Template| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| deviceId | string | Yes | Device ID, indicating the remote device where the mission change occurred. |

**Example**

```ts
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

## MissionCallback.notifySnapshot

notifySnapshot(deviceId: string, mission: number): void

notifySnapshot is a callback function for mission listening, used to notify mission snapshot changes. This callback is triggered when the snapshot of a mission (that is, the snapshot of the current UI state of the mission) changes. It is used to listen for mission snapshot changes on remote devices in multi-device collaboration scenarios, such as mission switching and mission restoration. For example, mission switching animation synchronization and real-time mission snapshot preview.

**Device behavior difference** This API does not take effect on Wearable devices that do not support distributed service.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**Parameters**

| Name| Template| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| deviceId |  string | Yes | Device ID of the remote device whose snapshot changes. |
| mission |  number | Yes | Mission ID of the mission whose snapshot changes. |

**Example**
```ts
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

## MissionCallback.notifyNetDisconnect

notifyNetDisconnect(deviceId: string, state: number): void

notifyNetDisconnect is a callback function for mission listening, used to notify disconnection. It is used to listen for network connection status changes on remote devices in multi-device collaboration scenarios. This callback is triggered when a device is disconnected, and is used to clean up related resources or prompt the user. For example, releasing session resources and displaying a disconnection prompt upon disconnection.

**Device behavior difference** This API does not take effect on Wearable devices that do not support distributed service.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**Parameters**

| Name| Template| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| deviceId |  string | Yes | Device ID of the remote device whose network is disconnected. |
| state |  number | Yes | Network connection status. The value is fixed at 0, indicating that the network connection is disconnected. |

**Example**

```ts
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
