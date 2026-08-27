# MissionCallback（系统接口）

作为可以[registerMissionListener]的入参，表示开始同步后，建立的回调函数，用于监听任务状态变化，包含任务列表变化通知、任务快照通知和断开连接通知等功能。@interface MissionCallback

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## notifyMissionsChanged

```TypeScript
notifyMissionsChanged: NotifyMissionsChangedCallback
```

notifyMissionsChanged是任务监听的callback函数，用于通知任务变化。用于在多设备协同场景下，监听远程设备的任务状态变化，如任务管理器、多屏协同等场景。当远程设备的任务列表发生增、删、排序等变化时，触发此回调通知。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';

// 注册任务监听器
distributedMissionManager.registerMissionListener(
  {
    deviceId: '123456'
  },
  {
    // 任务变化时的回调，接收设备ID
    notifyMissionsChanged: (deviceId: string) => {
      console.info(`notifyMissionsChanged deviceId: ${JSON.stringify(deviceId)}`);
    },
    // 快照变化时的回调，接收设备ID和任务ID
    notifySnapshot: (deviceId: string, mission: number) => {
      console.info(`notifySnapshot deviceId: ${JSON.stringify(deviceId)}`);
      console.info(`notifySnapshot mission: ${JSON.stringify(mission)}`);
    },
    // 网络断开时的回调，接收设备ID和网络状态
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

notifyNetDisconnect是任务监听的callback函数，用于通知断开连接。用于在多设备协同场景下，监听远程设备的网络连接状态变化，当设备断开连接时触发回调通知。开发者应在此回调中清理资源、提示用户网络断开，并释放与该设备相关的会话资源。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';

// 注册任务监听器
distributedMissionManager.registerMissionListener(
  {
    deviceId: '123456'
  },
  {
    // 任务变化时的回调，接收设备ID
    notifyMissionsChanged: (deviceId: string) => {
      console.info(`notifyMissionsChanged deviceId: ${JSON.stringify(deviceId)}`);
    },
    // 快照变化时的回调，接收设备ID和任务ID
    notifySnapshot: (deviceId: string, mission: number) => {
      console.info(`notifySnapshot deviceId: ${JSON.stringify(deviceId)}`);
      console.info(`notifySnapshot mission: ${JSON.stringify(mission)}`);
    },
    // 网络断开时的回调，接收设备ID和网络状态
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

notifySnapshot是任务监听的callback函数，用于通知任务快照变化。当任务的快照（即任务当前界面状态的快照）发生变化时触发该回调。用于在多设备协同场景下，监听远程设备任务界面状态变化，如多屏协同中界面同步更新等场景。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';

// 注册任务监听器
distributedMissionManager.registerMissionListener(
  {
    deviceId: '123456'
  },
  {
    // 任务变化时的回调，接收设备ID
    notifyMissionsChanged: (deviceId: string) => {
      console.info(`notifyMissionsChanged deviceId: ${JSON.stringify(deviceId)}`);
    },
    // 快照变化时的回调，接收设备ID和任务ID
    notifySnapshot: (deviceId: string, mission: number) => {
      console.info(`notifySnapshot deviceId: ${JSON.stringify(deviceId)}`);
      console.info(`notifySnapshot mission: ${JSON.stringify(mission)}`);
    },
    // 网络断开时的回调，接收设备ID和网络状态
    notifyNetDisconnect: (deviceId: string, state: number) => {
      console.info(`notifyNetDisconnect deviceId: ${JSON.stringify(deviceId)}`);
      console.info(`notifyNetDisconnect state: ${JSON.stringify(state)}`);
    }
  }
);
```
