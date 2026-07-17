# moveMissionsToBackground（系统接口）

## 导入模块

```TypeScript
import { missionManager } from '@kit.AbilityKit';
```

## moveMissionsToBackground

```TypeScript
function moveMissionsToBackground(missionIds: Array<number>, callback: AsyncCallback<Array<number>>): void
```

将指定任务批量切到后台，返回的结果任务ID按被隐藏时的任务层级排序。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function moveMissionsToBackground(missionIds: Array<int>, callback: AsyncCallback<Array<int>>): void--><!--Device-missionManager-function moveMissionsToBackground(missionIds: Array<int>, callback: AsyncCallback<Array<int>>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionIds | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<number> | 是 | 任务ID数组。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<number>> | 是 | 执行结果回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

```TypeScript
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos("", 10, (error: BusinessError, missionInfos: Array<missionManager.MissionInfo>) => {
    if (error.code) {
      console.error(`getMissionInfos failed, error code: ${error.code}, error msg: ${error.message}`);
      return;
    }

    let toHides = new Array<number>();
    for (let missionInfo of missionInfos) {
      if (missionInfo.abilityState == abilityManager.AbilityState.FOREGROUND) {
        toHides.push(missionInfo.missionId);
      }
    }
    missionManager.moveMissionsToBackground(toHides, (err: BusinessError, data: Array<number>) => {
      if (err) {
        console.error(`moveMissionsToBackground failed. Code: ${err.code}, message: ${err.message}.`);
      } else {
        console.info(`moveMissionsToBackground successfully: ${JSON.stringify(data)}`);
      }
    });
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}

```


## moveMissionsToBackground

```TypeScript
function moveMissionsToBackground(missionIds: Array<number>): Promise<Array<number>>
```

将指定任务批量切到后台，返回的结果按被隐藏时的任务层级排序。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function moveMissionsToBackground(missionIds: Array<int>): Promise<Array<int>>--><!--Device-missionManager-function moveMissionsToBackground(missionIds: Array<int>): Promise<Array<int>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionIds | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<number> | 是 | 任务ID数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<number>> | Promise对象，返回任务ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

```TypeScript
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos("", 10, (error: BusinessError, missionInfos: Array<missionManager.MissionInfo>) => {
    if (error.code) {
      console.error(`getMissionInfos failed, error code: ${error.code}, error msg: ${error.message}`);
      return;
    }

    let toHides = new Array<number>();
    for (let missionInfo of missionInfos) {
      if (missionInfo.abilityState == abilityManager.AbilityState.FOREGROUND) {
        toHides.push(missionInfo.missionId);
      }
    }
    missionManager.moveMissionsToBackground(toHides).then((hideRes: Array<number>) => {
      console.info(`moveMissionsToBackground is called, res: ${JSON.stringify(hideRes)}`);
    });
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}

```

