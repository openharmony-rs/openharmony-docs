# MissionListener（系统接口）

定义系统任务状态监听，可以通过[on](arkts-ability-missionmanager-on-f-sys.md)注册。

**起始版本：** 8

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## onMissionClosed

```TypeScript
onMissionClosed(mission: number): void
```

当系统关闭任务时会触发该回调函数。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | number | 是 | 表示关闭的任务ID。 |

**示例**

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

## onMissionCreated

```TypeScript
onMissionCreated(mission: number): void
```

当系统创建任务时会触发该回调函数。

**起始版本：** 8

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | number | 是 | 表示创建的任务ID。 |

**示例**

详细示例请见[onMissionClosed](#onmissionclosed)。

## onMissionDestroyed

```TypeScript
onMissionDestroyed(mission: number): void
```

当系统销毁任务时会触发该回调函数。

**起始版本：** 8

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | number | 是 | 表示销毁的任务ID。 |

**示例**

详细示例请见[onMissionClosed](#onmissionclosed)。

## onMissionIconUpdated

```TypeScript
onMissionIconUpdated(mission: number, icon: image.PixelMap): void
```

当系统更新任务图标时会触发该回调函数。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | number | 是 | 表示任务ID。 |
| icon | image.PixelMap | 是 | 表示更新的任务图标。 |

**示例**

详细示例请见[onMissionClosed](#onmissionclosed)。

## onMissionLabelUpdated

```TypeScript
onMissionLabelUpdated(mission: number): void
```

当系统更新任务标签时会触发该回调函数。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | number | 是 | 表示任务ID。 |

**示例**

详细示例请见[onMissionClosed](#onmissionclosed)。

## onMissionMovedToFront

```TypeScript
onMissionMovedToFront(mission: number): void
```

当系统将任务移动到前台时会触发该回调函数。

**起始版本：** 8

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | number | 是 | 表示任务ID。 |

**示例**

详细示例请见[onMissionClosed](#onmissionclosed)。

## onMissionSnapshotChanged

```TypeScript
onMissionSnapshotChanged(mission: number): void
```

当系统更新任务缩略图时会触发该回调函数。

**起始版本：** 8

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | number | 是 | 表示任务ID。 |

**示例**

详细示例请见[onMissionClosed](#onmissionclosed)。
