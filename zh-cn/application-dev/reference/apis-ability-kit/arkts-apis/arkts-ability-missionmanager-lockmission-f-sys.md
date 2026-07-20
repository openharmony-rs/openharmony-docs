# lockMission（系统接口）

## 导入模块

```TypeScript
import { missionManager } from '@kit.AbilityKit';
```

<a id="lockmission"></a>
## lockMission

```TypeScript
function lockMission(missionId: number, callback: AsyncCallback<void>): void
```

锁定指定任务ID的任务。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function lockMission(missionId: int, callback: AsyncCallback<void>): void--><!--Device-missionManager-function lockMission(missionId: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | number | 是 | 任务ID。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 执行结果回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300001](../errorcode-ability.md#16300001-指定的任务不存在) | Mission not found. |

**示例：**

```TypeScript
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId为任务ID，可通过getMissionInfos接口获取真实有效的任务ID
let testMissionId = 2;

try {
  missionManager.lockMission(testMissionId, (err: BusinessError, data: void) => {
    if (err) {
      console.error(`lockMission failed. Code: ${err.code}, message: ${err.message}.`);
    } else {
      console.info(`lockMission successfully: ${JSON.stringify(data)}`);
    }
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`lockMission failed. Code: ${err.code}, message: ${err.message}.`);
}

```


<a id="lockmission-1"></a>
## lockMission

```TypeScript
function lockMission(missionId: number): Promise<void>
```

锁定指定任务ID的任务。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function lockMission(missionId: int): Promise<void>--><!--Device-missionManager-function lockMission(missionId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | number | 是 | 任务ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300001](../errorcode-ability.md#16300001-指定的任务不存在) | Mission not found. |

**示例：**

```TypeScript
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId为任务ID，可通过getMissionInfos接口获取真实有效的任务ID
let testMissionId = 2;

try {
  missionManager.lockMission(testMissionId).then((data: void) => {
    console.info(`lockMission successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`lockMission failed. Code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`lockMission failed. Code: ${err.code}, message: ${err.message}`);
}

```

