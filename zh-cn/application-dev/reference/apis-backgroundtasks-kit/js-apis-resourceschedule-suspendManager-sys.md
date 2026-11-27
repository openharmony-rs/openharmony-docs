# @ohos.resourceschedule.suspendManager (冻结管理模块)(系统接口)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->

本模块提供查询应用状态和注册监听的API，可监听应用冻结状态的改变，并通过进程pid列表查询应用当前的冻结状态。

>  **说明**:
>
> 本模块接口为系统接口。

**起始版本：** 26.1.0

## 导入模块

```ts
import { suspendManager } from '@kit.BackgroundTasksKit';
```

## suspendManager.registerSuspendStateObserver

registerSuspendStateObserver(observer: SuspendStateObserver, stateList: Array&lt;FreezeState&gt;, pidList?: Array&lt;number&gt;): void

注册一个冻结状态观察者来监听应用冻结状态的变化。

**ArkTS模式：** 本接口仅适用于ArkTS-Dyn。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力:** SystemCapability.Resourceschedule.BackgroundProcessManager

**需要权限:** ohos.permission.GET_SUSPEND_STATE

**系统接口：** 此接口为系统接口。

**参数**：

| 参数名      | 类型                   | 必填   | 说明                             |
| -------- | -------------------- | ---- | ------------------------------ |
| observer |[SuspendStateObserver](#suspendstateobserver)| 是    | 要注册的观察者。 |
| stateList |Array&lt;[FreezeState](#freezestate)&gt; | 是    | 订阅状态类型的列表。 |
| pidList |Array&lt;number&gt; | 否    | 要筛选的可选进程ID列表。如果未指定或为空，所有进程状态更改都会触发回调。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[suspendManager错误码](errorcode-suspendManager.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 31800005 | Parameter error. |
| 31800006 | Failed to get suspend manager service. |

**示例**：

```ts
import { suspendManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: suspendManager.SuspendStateObserver = {
  onActive: (pidList: Array<number>, uid: number) => {
    console.info('SUSPEND_MANAGER onActive, pidList: ' + JSON.stringify(pidList) + ', uid: ' + uid);
  },
  onDoze: (pidList: Array<number>, uid: number) => {
    console.info('SUSPEND_MANAGER onDoze, pidList: ' + JSON.stringify(pidList) + ', uid: ' + uid);
  },
  onFrozen: (pidList: Array<number>, uid: number) => {
    console.info('SUSPEND_MANAGER onFrozen, pidList: ' + JSON.stringify(pidList) + ', uid: ' + uid);
  }
};
try {
    let stateList: Array<suspendManager.FreezeState> = [suspendManager.FreezeState.FROZEN];
    suspendManager.registerSuspendStateObserver(observer, stateList);
    console.info(`Operation registerSuspendStateObserver succeeded.`);
} catch (err) {
    console.error(`registerSuspendStateObserver failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
}
```

## suspendManager.unregisterSuspendStateObserver

unregisterSuspendStateObserver(observer: SuspendStateObserver): void

注销先前注册的冻结状态观察者。

**ArkTS模式：** 本接口仅适用于ArkTS-Dyn。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力:** SystemCapability.Resourceschedule.BackgroundProcessManager

**需要权限:** ohos.permission.GET_SUSPEND_STATE

**系统接口：** 此接口为系统接口。

**参数**：

| 参数名      | 类型                   | 必填   | 说明                             |
| -------- | -------------------- | ---- | ------------------------------ |
| observer |[SuspendStateObserver](#suspendstateobserver)| 是    | 要取消注册的观察者。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[suspendManager错误码](errorcode-suspendManager.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 31800005 | Parameter error. |
| 31800006 | Failed to get suspend manager service. |

**示例**：

```ts
import { suspendManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: suspendManager.SuspendStateObserver = {
  onActive: (pidList: Array<number>, uid: number) => {
    console.info('SUSPEND_MANAGER onActive, pidList: ' + JSON.stringify(pidList) + ', uid: ' + uid);
  },
  onDoze: (pidList: Array<number>, uid: number) => {
    console.info('SUSPEND_MANAGER onDoze, pidList: ' + JSON.stringify(pidList) + ', uid: ' + uid);
  },
  onFrozen: (pidList: Array<number>, uid: number) => {
    console.info('SUSPEND_MANAGER onFrozen, pidList: ' + JSON.stringify(pidList) + ', uid: ' + uid);
  }
};
try {
    suspendManager.unregisterSuspendStateObserver(observer);
    console.info(`Operation unregisterSuspendStateObserver succeeded.`);
} catch (err) {
    console.error(`unregisterSuspendStateObserver failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
}
```

## suspendManager.getSuspendStateByPidList

getSuspendStateByPidList(pidList: Array&lt;number&gt;): Array&lt;FreezeState&gt;

根据进程的pid查询进程的冻结状态。

**ArkTS模式：** 本接口仅适用于ArkTS-Dyn。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力:** SystemCapability.Resourceschedule.BackgroundProcessManager

**需要权限:** ohos.permission.GET_SUSPEND_STATE

**系统接口：** 此接口为系统接口。

**参数**：

| 参数名      | 类型                   | 必填   | 说明                             |
| -------- | -------------------- | ---- | ------------------------------ |
| pidList |Array&lt;number&gt; | 是    | 要查询的进程ID列表。必须为正整数。 |

**返回值**：

| 类型                    | 说明                                       |
| --------------------- | ---------------------------------------- |
| Array&lt;[FreezeState](#freezestate)&gt; | 冻结状态列表。若无匹配状态，返回空数组。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[suspendManager错误码](errorcode-suspendManager.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 31800005 | Parameter error. |
| 31800006 | Failed to get suspend manager service. |

**示例**：

```ts
import { suspendManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { process } from '@kit.ArkTS';

let pidList: Array<number> = [process.pid];
try {
  let stateList: Array<suspendManager.FreezeState> = suspendManager.getSuspendStateByPidList(pidList);
  console.info('getSuspendStateByPidList result: ' + JSON.stringify(stateList));
} catch (err) {
  console.error(`getSuspendStateByPidList failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
}
```

## SuspendStateObserver

定义冻结状态变化的观察者。

**ArkTS模式：** 本接口仅适用于ArkTS-Dyn。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力:** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。

### onActive

onActive(pidList: Array&lt;number&gt;, uid: number): void

当应用状态转换到活动状态时回调。

**ArkTS模式：** 本接口仅适用于ArkTS-Dyn。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力:** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名  | 类型      | 必填   | 说明                |
|------| ------- | ---- |-------------------|
| pidList | Array&lt;number&gt; | 是    | 转换为激活状态的uid对应的pid列表。 |
| uid | number | 是    | 应用转为激活状态的uid。 |

**示例**：

```ts
import { suspendManager } from '@kit.BackgroundTasksKit';

let observer: suspendManager.SuspendStateObserver = {
  onActive: (pidList: Array<number>, uid: number) => {
    console.info('SUSPEND_MANAGER onActive, pidList: ' + JSON.stringify(pidList) + ', uid: ' + uid);
  },
  onDoze: (pidList: Array<number>, uid: number) => {
    console.info('SUSPEND_MANAGER onDoze, pidList: ' + JSON.stringify(pidList) + ', uid: ' + uid);
  },
  onFrozen: (pidList: Array<number>, uid: number) => {
    console.info('SUSPEND_MANAGER onFrozen, pidList: ' + JSON.stringify(pidList) + ', uid: ' + uid);
  }
};
```

### onDoze

onDoze(pidList: Array&lt;number&gt;, uid: number): void

当应用程序进入doze状态时回调。

**ArkTS模式：** 本接口仅适用于ArkTS-Dyn。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力:** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名  | 类型      | 必填   | 说明                |
|------| ------- | ---- |-------------------|
| pidList | Array&lt;number&gt; | 是    | 被doze的uid对应的pid列表。 |
| uid | number | 是    | 被doze的应用的uid。 |

**示例**：

```ts
import { suspendManager } from '@kit.BackgroundTasksKit';

let observer: suspendManager.SuspendStateObserver = {
  onActive: (pidList: Array<number>, uid: number) => {
    console.info('SUSPEND_MANAGER onActive, pidList: ' + JSON.stringify(pidList) + ', uid: ' + uid);
  },
  onDoze: (pidList: Array<number>, uid: number) => {
    console.info('SUSPEND_MANAGER onDoze, pidList: ' + JSON.stringify(pidList) + ', uid: ' + uid);
  },
  onFrozen: (pidList: Array<number>, uid: number) => {
    console.info('SUSPEND_MANAGER onFrozen, pidList: ' + JSON.stringify(pidList) + ', uid: ' + uid);
  }
};
```

### onFrozen

onFrozen(pidList: Array&lt;number&gt;, uid: number): void

当应用程序完全冻结时回调。

**ArkTS模式：** 本接口仅适用于ArkTS-Dyn。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力:** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名  | 类型      | 必填   | 说明                |
|------| ------- | ---- |-------------------|
| pidList | Array&lt;number&gt;| 是    | 冻结的uid对应的pid列表。 |
| uid | number | 是    | 被冻结的应用uid。 |

**示例**：

```ts
import { suspendManager } from '@kit.BackgroundTasksKit';

let observer: suspendManager.SuspendStateObserver = {
  onActive: (pidList: Array<number>, uid: number) => {
    console.info('SUSPEND_MANAGER onActive, pidList: ' + JSON.stringify(pidList) + ', uid: ' + uid);
  },
  onDoze: (pidList: Array<number>, uid: number) => {
    console.info('SUSPEND_MANAGER onDoze, pidList: ' + JSON.stringify(pidList) + ', uid: ' + uid);
  },
  onFrozen: (pidList: Array<number>, uid: number) => {
    console.info('SUSPEND_MANAGER onFrozen, pidList: ' + JSON.stringify(pidList) + ', uid: ' + uid);
  }
};
```

## FreezeState

应用程序状态的枚举。

**ArkTS模式：** 本接口仅适用于ArkTS-Dyn。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力:** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。

|名称   |值   |说明|
| ------------ | ------------ |--------------|
|ACTIVE    |0   |应用处于激活状态。|
|DOZE    |1   |应用处于doze状态，进入冻结过程，但尚未完全冻结。|
|FROZEN     |2   |应用处于冻结状态。|
