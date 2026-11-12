# registerSuspendStateObserver（系统接口）

## 导入模块

```TypeScript
import { suspendManager } from '@ohos.resourceschedule.suspendManager';
```

## registerSuspendStateObserver

```TypeScript
function registerSuspendStateObserver(observer: SuspendStateObserver, stateList: Array<FreezeState>, pidList?: Array<number>): void
```

注册一个挂起状态观察者来监听应用的挂起状态变化。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.GET_SUSPEND_STATE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-suspendManager-function registerSuspendStateObserver(observer: SuspendStateObserver, stateList: Array<FreezeState>, pidList?: Array<int>): void--><!--Device-suspendManager-function registerSuspendStateObserver(observer: SuspendStateObserver, stateList: Array<FreezeState>, pidList?: Array<int>): void-End-->

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | [SuspendStateObserver](arkts-backgroundtasks-suspendmanager-suspendstateobserver-i-sys.md) | 是 | 要注册的观察员。 |
| stateList | Array&lt;[FreezeState](arkts-backgroundtasks-suspendmanager-freezestate-e-sys.md)&gt; | 是 | 订阅状态类型列表。 |
| pidList | Array&lt;number&gt; | 否 | 要筛选的可选进程ID列表。如果未指定或为空，所有进程状态更改都会触发回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| 31800005 | Parameter error. |
| 31800006 | Failed to get suspend manager service. |
