# MissionListener (系统接口)

定义系统任务状态监听，可以通过[on](js-apis-app-ability-missionManager-sys.md#missionmanageronmission)注册。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口为系统接口。

## 导入模块

```ts
import { missionManager } from '@kit.AbilityKit';
```

## 属性

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

| 名称        | 类型                 | 必填 | 说明                                                         |
| ----------- | -------- | ---- | ------------------------------------------------------------ |
| onMissionCreated    | function               | 否   | 表示当系统创建任务时回调执行。<br>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| onMissionDestroyed   | function               | 否   | 表示当系统销毁任务时回调执行。<br>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| onMissionSnapshotChanged   | function               | 否   | 表示当系统更新任务缩略图时回调执行。<br>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| onMissionMovedToFront   | function               | 否   | 表示当系统将任务移动到前台时回调执行。<br>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| onMissionLabelUpdated<sup>9+</sup>   | function               | 否   | 表示当系统更新任务标签时回调执行。<br>**ArkTS-Dyn起始版本：** 9<br/>**ArkTS-Sta起始版本：** 23 |
| onMissionIconUpdated<sup>9+</sup>   | function               | 否   | 表示当系统更新任务图标时回调执行。<br>**ArkTS-Dyn起始版本：** 9<br/>**ArkTS-Sta起始版本：** 23 |
| onMissionClosed<sup>9+</sup>   | function               | 否   | 表示当系统关闭任务时回调执行。<br>**ArkTS-Dyn起始版本：** 9<br/>**ArkTS-Sta起始版本：** 23 |

**示例：**

ArkTS-Dyn示例：

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
  console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { PixelMap } from '@ohos.arkui.component';

class ListenerCustom implements missionManager.MissionListener {
  onMissionCreated(mission: int) {
    console.info(`onMissionCreated mission: ${JSON.stringify(mission)}`);
  }

  onMissionDestroyed(mission: int) {
    console.info(`onMissionDestroyed mission: ${JSON.stringify(mission)}`);
  }

  onMissionSnapshotChanged(mission: int) {
    console.info(`onMissionSnapshotChanged mission: ${JSON.stringify(mission)}`);
  }

  onMissionMovedToFront(mission: int) {
    console.info(`onMissionMovedToFront mission: ${JSON.stringify(mission)}`);
  }

  onMissionLabelUpdated(mission: int) {
    console.info(`onMissionLabelUpdated mission: ${JSON.stringify(mission)}`);
  }

  onMissionIconUpdated(mission: int, icon: PixelMap) {
    console.info(`onMissionIconUpdated mission: ${JSON.stringify(mission)}`);
    console.info(`onMissionIconUpdated icon: ${JSON.stringify(icon)}`);
  }

  onMissionClosed(mission: int) {
    console.info(`onMissionClosed mission: ${JSON.stringify(mission)}`);
  }
}

try {
  let listener = new ListenerCustom();
  let listenerId = missionManager.onMission(listener);
} catch (paramError) {
  console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
}
```

