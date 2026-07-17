# moveMissionToFront（系统接口）

## moveMissionToFront

```TypeScript
function moveMissionToFront(missionId: number, callback: AsyncCallback<void>): void
```

把指定任务id的任务切到前台。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** moveMissionToFront

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function moveMissionToFront(missionId: number, callback: AsyncCallback<void>): void--><!--Device-missionManager-function moveMissionToFront(missionId: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | number | 是 | 任务ID。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数，当把指定任务id的任务切到前台成功，err为undefined，否则为错误对象。 |

**示例：**

```TypeScript
import missionManager from '@ohos.application.missionManager';

let testMissionId = 2;
try {
  // 将指定任务切换到前台
  missionManager.moveMissionToFront(testMissionId, (err, data) => {
    if (err) {
      console.error(`moveMissionToFront failed: ${err.message}`);
    } else {
      console.info(`moveMissionToFront successfully: ${JSON.stringify(data)}`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`moveMissionToFront failed. Code: ${error.code}, message: ${error.message}.`);
}

```


## moveMissionToFront

```TypeScript
function moveMissionToFront(missionId: number, options: StartOptions, callback: AsyncCallback<void>): void
```

把指定任务id的任务切到前台，同时指定任务切换到前台时的启动参数，例如窗口模式、设备ID等。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** moveMissionToFront

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function moveMissionToFront(missionId: number, options: StartOptions, callback: AsyncCallback<void>): void--><!--Device-missionManager-function moveMissionToFront(missionId: number, options: StartOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | number | 是 | 任务ID。 |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c-sys.md) | 是 | 启动参数选项，用于指定任务切到前台时的窗口模式，设备ID等。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数，当把指定任务id的任务切到前台成功，err为undefined，否则为错误对象。 |

**示例：**

```TypeScript
import missionManager from '@ohos.application.missionManager';

let testMissionId = 2;
try {
  // 将指定任务切换到前台，并指定窗口模式
  missionManager.moveMissionToFront(testMissionId, { windowMode: 101 }, (err, data) => {
    if (err) {
      console.error(`moveMissionToFront failed. Code: ${err.code}, message: ${err.message}.`);
    } else {
      console.info(`moveMissionToFront successfully. Data: ${JSON.stringify(data)}`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`moveMissionToFront sync failed. Code: ${error.code}, message: ${error.message}.`);
}

```


## moveMissionToFront

```TypeScript
function moveMissionToFront(missionId: number, options?: StartOptions): Promise<void>
```

把指定任务id的任务切到前台，同时指定任务切换到前台时的启动参数，例如窗口模式、设备ID等。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** moveMissionToFront

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function moveMissionToFront(missionId: number, options?: StartOptions): Promise<void>--><!--Device-missionManager-function moveMissionToFront(missionId: number, options?: StartOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | number | 是 | 任务ID。 |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c-sys.md) | 否 | 启动参数选项，用于指定任务切到前台时的窗口模式，设备ID等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
import missionManager from '@ohos.application.missionManager';
import { BusinessError } from '@ohos.base';

let testMissionId = 2;
try {
  // 将指定任务切换到前台
  missionManager.moveMissionToFront(testMissionId).then((data) => {
    console.info(`moveMissionToFront successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`moveMissionToFront failed. Cause: ${error.message}`);
  });
} catch (error) {
  console.error(`moveMissionToFront failed. Cause: ${error.message}`);
}

```

