# unregisterMissionListener（系统接口）

## unregisterMissionListener

```TypeScript
function unregisterMissionListener(listenerId: number, callback: AsyncCallback<void>): void
```

解注册任务状态监听器。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function unregisterMissionListener(listenerId: number, callback: AsyncCallback<void>): void--><!--Device-missionManager-function unregisterMissionListener(listenerId: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| listenerId | number | 是 | 系统任务状态监听器的index值，和监听器一一对应，由registerMissionListener方法返回。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 执行结果回调函数。 |

**示例：**

```TypeScript
import missionManager from '@ohos.application.missionManager';

console.info('registerMissionListener');
let listenerId = missionManager.registerMissionListener({
  onMissionCreated: (mission) => {
    console.info('--------onMissionCreated-------');
  },
  onMissionDestroyed: (mission) => {
    console.info('--------onMissionDestroyed-------');
  },
  onMissionSnapshotChanged: (mission) => {
    console.info('--------onMissionSnapshotChanged-------');
  },
  onMissionMovedToFront: (mission) => {
    console.info('--------onMissionMovedToFront-------');
  },
  onMissionIconUpdated: (mission, icon) => {
    console.info('--------onMissionIconUpdated-------');
  },
  onMissionClosed: (mission) => {
    console.info('--------onMissionClosed-------');
  },
  onMissionLabelUpdated: (mission) => {
    console.info('--------onMissionLabelUpdated-------');
  }
});

// 解注册系统任务状态监听器
missionManager.unregisterMissionListener(listenerId, (error) => {
  let err = error as BusinessError;
  console.error(`unregisterMissionListener failed. Code: ${err.code}, message: ${err.message}.`);
});

```


## unregisterMissionListener

```TypeScript
function unregisterMissionListener(listenerId: number): Promise<void>
```

解注册任务状态监听器。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function unregisterMissionListener(listenerId: number): Promise<void>--><!--Device-missionManager-function unregisterMissionListener(listenerId: number): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| listenerId | number | 是 | 系统任务状态监听器的index值，和监听器一一对应，由registerMissionListener方法返回。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
import missionManager from '@ohos.application.missionManager';
import { BusinessError } from '@ohos.base';

console.info('registerMissionListener');
let listenerId = missionManager.registerMissionListener({
  onMissionCreated: (mission) => {
    console.info('--------onMissionCreated-------');
  },
  onMissionDestroyed: (mission) => {
    console.info('--------onMissionDestroyed-------');
  },
  onMissionSnapshotChanged: (mission) => {
    console.info('--------onMissionSnapshotChanged-------');
  },
  onMissionMovedToFront: (mission) => {
    console.info('--------onMissionMovedToFront-------');
  },
  onMissionIconUpdated: (mission, icon) => {
    console.info('--------onMissionIconUpdated-------');
  },
  onMissionClosed: (mission) => {
    console.info('--------onMissionClosed-------');
  },
  onMissionLabelUpdated: (mission) => {
    console.info('--------onMissionLabelUpdated-------');
  }
});

// 解注册系统任务状态监听器
missionManager.unregisterMissionListener(listenerId)
  .then(() => {
    console.info(`UnregisterMissionListener success.`)
  })
  .catch((error: BusinessError) => {
    console.error(`unregisterMissionListener failed. Code: ${error.code}, message: ${error.message}.`);
  });

```

