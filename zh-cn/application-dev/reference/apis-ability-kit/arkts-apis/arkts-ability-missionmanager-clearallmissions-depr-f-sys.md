# clearAllMissions（系统接口）

## clearAllMissions

```TypeScript
function clearAllMissions(callback: AsyncCallback<void>): void
```

清理所有未锁定的任务。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** clearAllMissions

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function clearAllMissions(callback: AsyncCallback<void>): void--><!--Device-missionManager-function clearAllMissions(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数，当清理所有未锁定的任务成功，err为undefined，否则为错误对象。 |

**示例：**

```TypeScript
import missionManager from '@ohos.application.missionManager';

try {
  // 清理所有未锁定的任务
  missionManager.clearAllMissions(err => {
    if (err) {
      console.error(`clearAllMissions failed: ${err.message}`);
    } else {
      console.info('clearAllMissions successfully.');
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`clearAllMissions sync failed. Code: ${error.code}, message: ${error.message}.`);
}

```


## clearAllMissions

```TypeScript
function clearAllMissions(): Promise<void>
```

清理所有未锁定的任务。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** clearAllMissions

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function clearAllMissions(): Promise<void>--><!--Device-missionManager-function clearAllMissions(): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
import missionManager from '@ohos.application.missionManager';
import { BusinessError } from '@ohos.base';

try {
  // 清理所有未锁定的任务
  missionManager.clearAllMissions().then((data) => {
    console.info(`clearAllMissions successfully. Data: ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`clearAllMissions failed. Code: ${err.code}, message: ${err.message}.`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`clearAllMissions sync failed. Code: ${error.code}, message: ${error.message}.`);
}

```

