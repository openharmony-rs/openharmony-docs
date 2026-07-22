# unlockMission（系统接口）

## unlockMission

```TypeScript
function unlockMission(missionId: number, callback: AsyncCallback<void>): void
```

解锁指定任务id的任务。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** unlockMission

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function unlockMission(missionId: number, callback: AsyncCallback<void>): void--><!--Device-missionManager-function unlockMission(missionId: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | number | 是 | 任务ID。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，当解锁指定任务id的任务成功，err为undefined，否则为错误对象。 |

**示例：**

```TypeScript
import missionManager from '@ohos.application.missionManager';

let testMissionId = 2;
try {
  // 解锁指定任务
  missionManager.unlockMission(testMissionId, (err, data) => {
    if (err) {
      console.error(`unlockMission failed. Code: ${err.code}, message: ${err.message}.`);
    } else {
      console.info(`unlockMission successfully. Data: ${JSON.stringify(data)}`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`unlockMission sync failed. Code: ${error.code}, message: ${error.message}.`);
}

```


## unlockMission

```TypeScript
function unlockMission(missionId: number): Promise<void>
```

解锁指定任务id的任务。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** unlockMission

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function unlockMission(missionId: number): Promise<void>--><!--Device-missionManager-function unlockMission(missionId: number): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | number | 是 | 任务ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
import missionManager from '@ohos.application.missionManager';
import { BusinessError } from '@ohos.base';

let testMissionId = 2;
try {
  // 解锁指定任务
  missionManager.unlockMission(testMissionId).then((data) => {
    console.info(`unlockMission successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`unlockMission failed. Code: ${error.code}, message: ${error.message}.`);
  });
} catch (error) {
  let err = error as BusinessError;
  console.error(`unlockMission sync failed. Code: ${err.code}, message: ${err.message}.`);
}

```

