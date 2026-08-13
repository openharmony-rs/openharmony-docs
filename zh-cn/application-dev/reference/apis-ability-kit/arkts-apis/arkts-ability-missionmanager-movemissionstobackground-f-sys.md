# moveMissionsToBackground（系统接口）

## moveMissionsToBackground

```TypeScript
function moveMissionsToBackground(missionIds: Array<int>, callback: AsyncCallback<Array<int>>): void
```

将指定任务批量切到后台，返回的结果任务ID按被隐藏时的任务层级排序。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function moveMissionsToBackground(missionIds: Array<int>, callback: AsyncCallback<Array<int>>): void--><!--Device-missionManager-function moveMissionsToBackground(missionIds: Array<int>, callback: AsyncCallback<Array<int>>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionIds | Array&lt;int&gt; | 是 | 任务ID数组。 |
| callback | AsyncCallback&lt;Array&lt;int&gt;&gt; | 是 | 执行结果回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos('', 10, (error: BusinessError, missionInfos: Array<missionManager.MissionInfo>) => {
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

ArkTS-Sta示例：

```TypeScript
'use static'
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos('', 10,
    (error: BusinessError | null, missionInfos: Array<missionManager.MissionInfo> | undefined) => {
      if (error?.code) {
        console.error(`getMissionInfos failed, error ${JSON.stringify(error)}.`);
        return;
      }

      if (!missionInfos || missionInfos.length === 0) {
        console.info('No mission infos available or missionInfos is undefined');
        return;
      }

      let toHides = new Array<int>();
      for (let missionInfo of missionInfos) {
        if (missionInfo.abilityState == abilityManager.AbilityState.FOREGROUND) {
          toHides.push(missionInfo.missionId);
        }
      }
      missionManager.moveMissionsToBackground(toHides, (err: BusinessError | null, data: Array<int> | undefined) => {
        if (err) {
          console.error(`moveMissionsToBackground failed: ${err.message}`);
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
function moveMissionsToBackground(missionIds: Array<int>): Promise<Array<int>>
```

将指定任务批量切到后台，返回的结果按被隐藏时的任务层级排序。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function moveMissionsToBackground(missionIds: Array<int>): Promise<Array<int>>--><!--Device-missionManager-function moveMissionsToBackground(missionIds: Array<int>): Promise<Array<int>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionIds | Array&lt;int&gt; | 是 | 任务ID数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;int&gt;&gt; | Promise对象，返回任务ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos('', 10, (error: BusinessError, missionInfos: Array<missionManager.MissionInfo>) => {
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

ArkTS-Sta示例：

```TypeScript
'use static'
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos('', 10,
    (error: BusinessError | null, missionInfos: Array<missionManager.MissionInfo> | undefined) => {
      if (error?.code) {
        console.error(`getMissionInfos failed, error ${JSON.stringify(error)}.`);
        return;
      }

      if (!missionInfos || missionInfos.length === 0) {
        console.info('No mission infos available or missionInfos is undefined');
        return;
      }

      let toHides = new Array<int>();
      for (let missionInfo of missionInfos) {
        if (missionInfo.abilityState == abilityManager.AbilityState.FOREGROUND) {
          toHides.push(missionInfo.missionId);
        }
      }
      missionManager.moveMissionsToBackground(toHides).then((hideRes: Array<int>) => {
        console.info(`moveMissionsToBackground is called, res: ${hideRes}`);
      });
    });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```

