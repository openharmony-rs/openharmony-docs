# getMissionInfo（系统接口）

## getMissionInfo

```TypeScript
function getMissionInfo(deviceId: string, missionId: number, callback: AsyncCallback<MissionInfo>): void
```

获取单个任务信息。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getMissionInfo

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function getMissionInfo(deviceId: string, missionId: number, callback: AsyncCallback<MissionInfo>): void--><!--Device-missionManager-function getMissionInfo(deviceId: string, missionId: number, callback: AsyncCallback<MissionInfo>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备ID，本机默认为空字符串。 |
| missionId | number | 是 | 任务ID。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<MissionInfo> | 是 | 回调函数，返回任务信息。 |

**示例：**

```TypeScript
import missionManager from '@ohos.application.missionManager';

let missionId: number = 0;

// 获取指定任务信息
missionManager.getMissionInfo('', missionId, (error, mission) => {
  if (error.code) {
    console.error(`getMissionInfo failed, error.code: ${error.code}, error.message: ${error.message}`);
    return;
  }

  console.info(`mission.missionId = ${mission.missionId}`);
  console.info(`mission.runningState = ${mission.runningState}`);
  console.info(`mission.lockedState = ${mission.lockedState}`);
  console.info(`mission.timestamp = ${mission.timestamp}`);
  console.info(`mission.label = ${mission.label}`);
  console.info(`mission.iconPath = ${mission.iconPath}`);
});

```


## getMissionInfo

```TypeScript
function getMissionInfo(deviceId: string, missionId: number): Promise<MissionInfo>
```

获取单个任务信息。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getMissionInfo

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function getMissionInfo(deviceId: string, missionId: number): Promise<MissionInfo>--><!--Device-missionManager-function getMissionInfo(deviceId: string, missionId: number): Promise<MissionInfo>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备ID，本机默认为空字符串。 |
| missionId | number | 是 | 任务ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<MissionInfo> | Promise对象，返回任务信息。 |

**示例：**

```TypeScript
import missionManager from '@ohos.application.missionManager';
import { BusinessError } from '@ohos.base';

let testMissionId = 1;
try {
  // 获取指定任务信息
  missionManager.getMissionInfo('', testMissionId).then((data) => {
    console.info(`getMissionInfo successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`getMissionInfo failed. Cause: ${error.message}`);
  });
} catch (error) {
  console.error(`getMissionInfo failed. Cause: ${error.message}`);
}

```

