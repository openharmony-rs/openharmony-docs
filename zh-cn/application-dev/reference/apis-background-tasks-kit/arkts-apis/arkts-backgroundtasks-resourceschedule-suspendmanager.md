# @ohos.resourceschedule.suspendManager(冻结管理)

提供查询应用卡顿状态和注册监听器的API。挂起状态改变。

> **说明：** 
> 
> -该模块提供的API为系统API。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace suspendManager--><!--Device-unnamed-declare namespace suspendManager-End-->

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { suspendManager } from '@ohos.resourceschedule.suspendManager';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getSuspendStateByPidList](arkts-backgroundtasks-suspendmanager-getsuspendstatebypidlist-f-sys.md#getsuspendstatebypidlist-1) | 根据进程的PID查询进程的冻结状态。 |
| [registerSuspendStateObserver](arkts-backgroundtasks-suspendmanager-registersuspendstateobserver-f-sys.md#registersuspendstateobserver-1) | 注册一个挂起状态观察者来监听应用的挂起状态变化。 |
| [unregisterSuspendStateObserver](arkts-backgroundtasks-suspendmanager-unregistersuspendstateobserver-f-sys.md#unregistersuspendstateobserver-1) | 注销先前注册的挂起状态观察者。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SuspendStateObserver](arkts-backgroundtasks-suspendmanager-suspendstateobserver-i-sys.md) | 定义挂起状态变化的观察者。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FreezeState](arkts-backgroundtasks-suspendmanager-freezestate-e-sys.md) | 枚举应用程序的冻结状态。 |
<!--DelEnd-->
