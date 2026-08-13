# MissionListener（系统接口）

定义系统任务状态监听，可以通过on注册。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface MissionListener--><!--Device-unnamed-export interface MissionListener-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## onMissionClosed

```TypeScript
onMissionClosed(mission: int): void
```

当系统关闭任务时会触发该回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MissionListener-onMissionClosed(mission: int): void--><!--Device-MissionListener-onMissionClosed(mission: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | int | 是 | 表示关闭的任务ID。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 定义任务状态监听器对象
let listener: missionManager.MissionListener = {
  // 任务创建时的回调处理
  onMissionCreated: (mission) => {
    console.info(`onMissionCreated mission: ${JSON.stringify(mission)}`);
  },
  // 任务销毁时的回调处理
  onMissionDestroyed: (mission) => {
    console.info(`onMissionDestroyed mission: ${JSON.stringify(mission)}`);
  },
  // 任务缩略图更新时的回调处理
  onMissionSnapshotChanged: (mission) => {
    console.info(`onMissionSnapshotChanged mission: ${JSON.stringify(mission)}`);
  },
  // 任务移至前台时的回调处理
  onMissionMovedToFront: (mission) => {
    console.info(`onMissionMovedToFront mission: ${JSON.stringify(mission)}`);
  },
  // 任务标签更新时的回调处理
  onMissionLabelUpdated: (mission) => {
    console.info(`onMissionLabelUpdated mission: ${JSON.stringify(mission)}`);
  },
  // 任务图标更新时的回调处理
  onMissionIconUpdated: (mission, icon) => {
    console.info(`onMissionIconUpdated mission: ${JSON.stringify(mission)}`);
    console.info(`onMissionIconUpdated icon: ${JSON.stringify(icon)}`);
  },
  // 任务关闭时的回调处理
  onMissionClosed: (mission) => {
    console.info(`onMissionClosed mission: ${JSON.stringify(mission)}`);
  }
};

try {
  // 注册任务状态监听器
  let listenerId = missionManager.on('mission', listener);
} catch (paramError) {
  console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
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

## onMissionCreated

```TypeScript
onMissionCreated(mission: int): void
```

当系统创建任务时会触发该回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MissionListener-onMissionCreated(mission: int): void--><!--Device-MissionListener-onMissionCreated(mission: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | int | 是 | 表示创建的任务ID。 |

## 示例

详细示例请见[onMissionClosed](#onMissionClosed)。

## onMissionDestroyed

```TypeScript
onMissionDestroyed(mission: int): void
```

当系统销毁任务时会触发该回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MissionListener-onMissionDestroyed(mission: int): void--><!--Device-MissionListener-onMissionDestroyed(mission: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | int | 是 | 表示销毁的任务ID。 |

## 示例

详细示例请见[onMissionClosed](#onMissionClosed)。

## onMissionIconUpdated

```TypeScript
onMissionIconUpdated(mission: int, icon: image.PixelMap): void
```

当系统更新任务图标时会触发该回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MissionListener-onMissionIconUpdated(mission: int, icon: image.PixelMap): void--><!--Device-MissionListener-onMissionIconUpdated(mission: int, icon: image.PixelMap): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | int | 是 | 表示任务ID。 |
| icon | image.PixelMap | 是 | 表示更新的任务图标。 |

## 示例

详细示例请见[onMissionClosed](#onMissionClosed)。

## onMissionLabelUpdated

```TypeScript
onMissionLabelUpdated(mission: int): void
```

当系统更新任务标签时会触发该回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MissionListener-onMissionLabelUpdated(mission: int): void--><!--Device-MissionListener-onMissionLabelUpdated(mission: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | int | 是 | 表示任务ID。 |

## 示例

详细示例请见[onMissionClosed](#onMissionClosed)。

## onMissionMovedToFront

```TypeScript
onMissionMovedToFront(mission: int): void
```

当系统将任务移动到前台时会触发该回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MissionListener-onMissionMovedToFront(mission: int): void--><!--Device-MissionListener-onMissionMovedToFront(mission: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | int | 是 | 表示任务ID。 |

## 示例

详细示例请见[onMissionClosed](#onMissionClosed)。

## onMissionSnapshotChanged

```TypeScript
onMissionSnapshotChanged(mission: int): void
```

当系统更新任务缩略图时会触发该回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MissionListener-onMissionSnapshotChanged(mission: int): void--><!--Device-MissionListener-onMissionSnapshotChanged(mission: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | int | 是 | 表示任务ID。 |

## 示例

详细示例请见[onMissionClosed](#onMissionClosed)。

