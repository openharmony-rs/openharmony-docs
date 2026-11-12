# unregisterSuspendStateObserver（系统接口）

## 导入模块

```TypeScript
import { suspendManager } from '@ohos.resourceschedule.suspendManager';
```

## unregisterSuspendStateObserver

```TypeScript
function unregisterSuspendStateObserver(observer: SuspendStateObserver): void
```

注销先前注册的挂起状态观察者。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.GET_SUSPEND_STATE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-suspendManager-function unregisterSuspendStateObserver(observer: SuspendStateObserver): void--><!--Device-suspendManager-function unregisterSuspendStateObserver(observer: SuspendStateObserver): void-End-->

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | [SuspendStateObserver](arkts-backgroundtasks-suspendmanager-suspendstateobserver-i-sys.md) | 是 | 要取消注册的观察者。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| 31800005 | Parameter error. |
| 31800006 | Failed to get suspend manager service. |
