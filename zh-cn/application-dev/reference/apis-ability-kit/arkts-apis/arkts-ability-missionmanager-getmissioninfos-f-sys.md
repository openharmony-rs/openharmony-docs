# getMissionInfos（系统接口）

## 导入模块

```TypeScript
import { missionManager } from '@kit.AbilityKit';
```

## getMissionInfos

```TypeScript
function getMissionInfos(deviceId: string, numMax: int, callback: AsyncCallback<Array<MissionInfo>>): void
```

获取所有任务信息。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function getMissionInfos(deviceId: string, numMax: int, callback: AsyncCallback<Array<MissionInfo>>): void--><!--Device-missionManager-function getMissionInfos(deviceId: string, numMax: int, callback: AsyncCallback<Array<MissionInfo>>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备ID，本机默认为空字符串。 |
| numMax | int | 是 | 任务信息数量上限。 |
| callback | AsyncCallback&lt;Array&lt;MissionInfo&gt;&gt; | 是 | 执行结果回调函数，返回任务信息数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

**示例**

```TypeScript
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 获取所有任务信息
  missionManager.getMissionInfos('', 10,
    (error: BusinessError | null, missions: Array<missionManager.MissionInfo> | undefined) => {
      if (error) {
        console.error(`getMissionInfos failed, error.code: ${error.code}, error.message: ${error.message}`);
      } else {
        console.info(`size = ${missions?.length}`);
        console.info(`missions = ${JSON.stringify(missions)}`);
      }
    });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```


## getMissionInfos

```TypeScript
function getMissionInfos(deviceId: string, numMax: int): Promise<Array<MissionInfo>>
```

获取所有任务信息。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function getMissionInfos(deviceId: string, numMax: int): Promise<Array<MissionInfo>>--><!--Device-missionManager-function getMissionInfos(deviceId: string, numMax: int): Promise<Array<MissionInfo>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备ID，本机默认为空字符串。 |
| numMax | int | 是 | 任务信息数量上限。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;MissionInfo&gt;&gt; | Promise对象，返回所有任务信息的数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

**示例**

```TypeScript
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 获取所有任务信息
  missionManager.getMissionInfos('', 10).then((data: Array<missionManager.MissionInfo>) => {
    console.info(`getMissionInfos successfully. Data: ${JSON.stringify(data)}`);
  }).catch((err: Error) => {
    let error: BusinessError = err as BusinessError;
    console.error(`getMissionInfos failed. Code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getMissionInfos failed. Code: ${err.code}, message: ${err.message}`);
}
```

