# getLowResolutionMissionSnapShot（系统接口）

## 导入模块

```TypeScript
import { missionManager } from '@kit.AbilityKit';
```

<a id="getlowresolutionmissionsnapshot"></a>
## getLowResolutionMissionSnapShot

```TypeScript
function getLowResolutionMissionSnapShot(
    deviceId: string,
    missionId: number,
    callback: AsyncCallback<MissionSnapshot>
  ): void
```

获取任务低分辨率快照。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function getLowResolutionMissionSnapShot(
    deviceId: string,
    missionId: int,
    callback: AsyncCallback<MissionSnapshot>
  ): void--><!--Device-missionManager-function getLowResolutionMissionSnapShot(
    deviceId: string,
    missionId: int,
    callback: AsyncCallback<MissionSnapshot>
  ): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备ID，本机默认为空字符串。 |
| missionId | number | 是 | 任务ID。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;MissionSnapshot&gt; | 是 | 执行结果回调函数，返回任务快照信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId为任务ID，可通过getMissionInfos接口获取真实有效的任务ID
let testMissionId = 2;

try {
  missionManager.getLowResolutionMissionSnapShot('', testMissionId,
    (err: BusinessError, data: missionManager.MissionSnapshot) => {
      if (err) {
        console.error(`getLowResolutionMissionSnapShot failed. Code: ${err.code}, message: ${err.message}.`);
      } else {
        console.info(`getLowResolutionMissionSnapShot successfully: ${JSON.stringify(data)}`);
      }
    });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getLowResolutionMissionSnapShot failed. Code: ${err.code}, message: ${err.message}.`);
}

```


<a id="getlowresolutionmissionsnapshot-1"></a>
## getLowResolutionMissionSnapShot

```TypeScript
function getLowResolutionMissionSnapShot(deviceId: string, missionId: number): Promise<MissionSnapshot>
```

获取任务低分辨率快照。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function getLowResolutionMissionSnapShot(deviceId: string, missionId: int): Promise<MissionSnapshot>--><!--Device-missionManager-function getLowResolutionMissionSnapShot(deviceId: string, missionId: int): Promise<MissionSnapshot>-End-->

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

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId为任务ID，可通过getMissionInfos接口获取真实有效的任务ID
let testMissionId = 2;

try {
  missionManager.getLowResolutionMissionSnapShot('', testMissionId).then((data: missionManager.MissionSnapshot) => {
    console.info(`getLowResolutionMissionSnapShot successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`getLowResolutionMissionSnapShot failed. Code: ${error.code}, message: ${error.message}.`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getLowResolutionMissionSnapShot failed. Code: ${err.code}, message: ${err.message}.`);
}

```

