# getMissionSnapShot（系统接口）

## getMissionSnapShot

```TypeScript
function getMissionSnapShot(deviceId: string, missionId: number, callback: AsyncCallback<MissionSnapshot>): void
```

获取任务快照。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getMissionSnapShot

**需要权限：** ohos.permission.MANAGE_MISSIONS

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备ID，本机默认为空字符串。 |
| missionId | number | 是 | 任务ID。 |
| callback | AsyncCallback&lt;MissionSnapshot&gt; | 是 | 回调函数，返回任务快照信息。 |

**示例：**

```TypeScript
import missionManager from '@ohos.application.missionManager';

let testMissionId = 2;
try {
  missionManager.getMissionSnapShot('', testMissionId, (err, data) => {
    if (err) {
      console.error(`getMissionSnapShot failed: ${err.message}`);
    } else {
      console.info(`getMissionSnapShot successfully: ${JSON.stringify(data)}`);
    }
  });
} catch (err) {
  console.error(`getMissionSnapShot failed: ${err.message}`);
}

```


## getMissionSnapShot

```TypeScript
function getMissionSnapShot(deviceId: string, missionId: number): Promise<MissionSnapshot>
```

获取任务快照。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getMissionSnapShot

**需要权限：** ohos.permission.MANAGE_MISSIONS

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
| Promise&lt;MissionSnapshot&gt; | Promise对象，返回任务快照信息。 |

**示例：**

```TypeScript
import missionManager from '@ohos.application.missionManager';
import { BusinessError } from '@ohos.base';

let testMissionId = 2;
try {
  missionManager.getMissionSnapShot('', testMissionId).then((data) => {
    console.info(`getMissionSnapShot successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`getMissionSnapShot failed. Cause: ${error.message}`);
  });
} catch (error) {
  console.error(`getMissionSnapShot failed. Cause: ${error.message}`);
}

```

