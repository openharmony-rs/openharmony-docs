# getMissionSnapShot（系统接口）

<a id="getmissionsnapshot"></a>
## getMissionSnapShot

```TypeScript
function getMissionSnapShot(deviceId: string, missionId: number, callback: AsyncCallback<MissionSnapshot>): void
```

获取任务快照。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getMissionSnapShot

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function getMissionSnapShot(deviceId: string, missionId: number, callback: AsyncCallback<MissionSnapshot>): void--><!--Device-missionManager-function getMissionSnapShot(deviceId: string, missionId: number, callback: AsyncCallback<MissionSnapshot>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备ID，本机默认为空字符串。 |
| missionId | number | 是 | 任务ID。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;MissionSnapshot&gt; | 是 | 回调函数，返回任务快照信息。 |

**示例：**

```TypeScript
import missionManager from '@ohos.application.missionManager';

let testMissionId = 2;
try {
  // 获取任务快照
  missionManager.getMissionSnapShot('', testMissionId, (err, data) => {
    if (err) {
      console.error(`getMissionSnapShot failed. Code: ${err.code}, message: ${err.message}.`);
    } else {
      console.info(`getMissionSnapShot successfully. Data: ${JSON.stringify(data)}`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`getMissionSnapShot sync failed. Code: ${error.code}, message: ${error.message}.`);
}

```


<a id="getmissionsnapshot-1"></a>
## getMissionSnapShot

```TypeScript
function getMissionSnapShot(deviceId: string, missionId: number): Promise<MissionSnapshot>
```

获取任务快照。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getMissionSnapShot

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function getMissionSnapShot(deviceId: string, missionId: number): Promise<MissionSnapshot>--><!--Device-missionManager-function getMissionSnapShot(deviceId: string, missionId: number): Promise<MissionSnapshot>-End-->

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
  // 获取任务快照
  missionManager.getMissionSnapShot('', testMissionId).then((data) => {
    console.info(`getMissionSnapShot successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`getMissionSnapShot failed. Cause: ${error.message}`);
  });
} catch (error) {
  console.error(`getMissionSnapShot failed. Cause: ${error.message}`);
}

```

