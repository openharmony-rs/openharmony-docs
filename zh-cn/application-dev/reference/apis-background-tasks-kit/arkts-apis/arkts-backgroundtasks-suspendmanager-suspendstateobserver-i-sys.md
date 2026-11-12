# SuspendStateObserver（系统接口）

```TypeScript
export interface SuspendStateObserver
```

定义挂起状态变化的观察者。

**起始版本：** 26.1.0

<!--Device-suspendManager-export interface SuspendStateObserver--><!--Device-suspendManager-export interface SuspendStateObserver-End-->

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { suspendManager } from '@ohos.resourceschedule.suspendManager';
```

## onActive

```TypeScript
onActive(pidList: Array<number>, uid: number): void
```

当应用程序转换到活动状态时调用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SuspendStateObserver-onActive(pidList: Array<int>, uid: int): void--><!--Device-SuspendStateObserver-onActive(pidList: Array<int>, uid: int): void-End-->

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pidList | Array&lt;number&gt; | 是 | 转换为活动的进程ID列表。 |
| uid | number | 是 | 应用的UID。<br>取值限定为整数。 |

## onDoze

```TypeScript
onDoze(pidList: Array<number>, uid: number): void
```

当应用程序进入doze状态时调用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SuspendStateObserver-onDoze(pidList: Array<int>, uid: int): void--><!--Device-SuspendStateObserver-onDoze(pidList: Array<int>, uid: int): void-End-->

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pidList | Array&lt;number&gt; | 是 | 被doze的进程ID列表。 |
| uid | number | 是 | 应用的UID。<br>取值限定为整数。 |

## onFrozen

```TypeScript
onFrozen(pidList: Array<number>, uid: number): void
```

当应用程序完全冻结时调用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SuspendStateObserver-onFrozen(pidList: Array<int>, uid: int): void--><!--Device-SuspendStateObserver-onFrozen(pidList: Array<int>, uid: int): void-End-->

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pidList | Array&lt;number&gt; | 是 | 被冻结的进程ID列表。 |
| uid | number | 是 | 应用的UID。<br>取值限定为整数。 |
