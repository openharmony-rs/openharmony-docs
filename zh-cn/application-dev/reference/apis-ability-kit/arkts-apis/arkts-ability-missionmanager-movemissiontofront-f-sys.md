# moveMissionToFront（系统接口）

## 导入模块

```TypeScript
import { missionManager } from '@kit.AbilityKit';
```

## moveMissionToFront

```TypeScript
function moveMissionToFront(missionId: int, callback: AsyncCallback<void>): void
```

把指定任务ID的任务切到前台。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function moveMissionToFront(missionId: int, callback: AsyncCallback<void>): void--><!--Device-missionManager-function moveMissionToFront(missionId: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | int | 是 | 任务ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 执行结果回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |

**示例**

```TypeScript
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId为任务ID，可通过getMissionInfos接口获取真实有效的任务ID
let testMissionId = 2;

try {
  missionManager.moveMissionToFront(testMissionId, (err: BusinessError | null, data: undefined) => {
    if (err) {
      console.error(`moveMissionToFront failed. Code: ${err.code}, message: ${err.message}.`);
    } else {
      console.info(`moveMissionToFront successfully: ${JSON.stringify(data)}`);
    }
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`moveMissionToFront failed. Code: ${err.code}, message: ${err.message}.`);
}
```


## moveMissionToFront

```TypeScript
function moveMissionToFront(missionId: int, options: StartOptions, callback: AsyncCallback<void>): void
```

把指定任务ID的任务切到前台，同时指定任务切换到前台时的启动参数，例如窗口模式、设备ID等。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function moveMissionToFront(missionId: int, options: StartOptions, callback: AsyncCallback<void>): void--><!--Device-missionManager-function moveMissionToFront(missionId: int, options: StartOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | int | 是 | 任务ID。 |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | 是 | 启动参数选项，用于指定任务切到前台时的窗口模式，设备ID等。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 执行结果回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |

**示例**

```TypeScript
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId为任务ID，可通过getMissionInfos接口获取真实有效的任务ID
let testMissionId = 2;

try {
  missionManager.moveMissionToFront(testMissionId, { windowMode: 101 },
    (err: BusinessError | null, data: undefined) => {
      if (err) {
        console.error(`moveMissionToFront failed. Code: ${err.code}, message: ${err.message}.`);
      } else {
        console.info(`moveMissionToFront successfully: ${JSON.stringify(data)}`);
      }
    });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`moveMissionToFront failed. Code: ${err.code}, message: ${err.message}.`);
}
```


## moveMissionToFront

```TypeScript
function moveMissionToFront(missionId: int, options?: StartOptions): Promise<void>
```

把指定任务ID的任务切到前台，同时指定任务切换到前台时的启动参数，例如窗口模式、设备ID等。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function moveMissionToFront(missionId: int, options?: StartOptions): Promise<void>--><!--Device-missionManager-function moveMissionToFront(missionId: int, options?: StartOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | int | 是 | 任务ID。 |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | 否 | 启动参数选项，用于指定任务切到前台时的窗口模式，设备ID等。默认为空，表示按照默认启动参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |

**示例**

```TypeScript
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId为任务ID，可通过getMissionInfos接口获取真实有效的任务ID
let testMissionId = 2;

try {
  missionManager.moveMissionToFront(testMissionId).then((data) => {
    console.info(`moveMissionToFront successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: Error) => {
    let err: BusinessError = error as BusinessError;
    console.error(`moveMissionToFront failed. Code: ${err.code}, message: ${err.message}.`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`moveMissionToFront failed. Code: ${err.code}, Cause: ${err.message}.`);
}
```

