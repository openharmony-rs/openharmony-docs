# @ohos.backgroundTaskManager

本模块提供后台任务管理能力。

当应用或业务模块处于后台（无可见界面）时，如果有需要继续执行或者后续执行的业务，可基于业务类型，申请短时任务延迟挂起（Suspend）或者长时任务避免进入挂起状态。

应用有不可中断且短时间能完成的任务时（如，用户在文件管理器上点击垃圾文件清理，若清理未完成时退到后台，文件管理器需要申请短时任务完成清理），可以使用短时任务机制。

应用中存在用户能够直观感受到的且需要一直在后台运行的业务时（如，后台播放音乐），可以使用长时任务机制。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [backgroundTaskManager:backgroundTaskManager](../../apis-background-tasks-kit/arkts-apis/arkts-resourceschedule-backgroundtaskmanager.md#backgroundTaskManager)

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [cancelSuspendDelay](arkts-api10lessdeprecatedmodules-backgroundtaskmanager-cancelsuspenddelay-f.md#cancelSuspendDelay-1) | 取消延迟挂起。<br/> |
| [getRemainingDelayTime](arkts-api10lessdeprecatedmodules-backgroundtaskmanager-getremainingdelaytime-f.md#getRemainingDelayTime-1) | 获取本次短时任务的剩余时间，使用callback异步回调。<br/> |
| [getRemainingDelayTime](arkts-api10lessdeprecatedmodules-backgroundtaskmanager-getremainingdelaytime-f.md#getRemainingDelayTime-2) | 获取本次短时任务的剩余时间，使用Promise异步回调。<br/> |
| [requestSuspendDelay](arkts-api10lessdeprecatedmodules-backgroundtaskmanager-requestsuspenddelay-f.md#requestSuspendDelay-1) | 后台应用申请延迟挂起。<br/><br/>延迟挂起时间一般情况下默认值为3分钟，低电量（依据系统低电量广播）时默认值为1分钟。<br/> |
| [startBackgroundRunning](arkts-api10lessdeprecatedmodules-backgroundtaskmanager-startbackgroundrunning-f.md#startBackgroundRunning-1) | 向系统申请长时任务，使用callback异步回调。<br/> |
| [startBackgroundRunning](arkts-api10lessdeprecatedmodules-backgroundtaskmanager-startbackgroundrunning-f.md#startBackgroundRunning-2) | 向系统申请长时任务，使用promise异步回调。<br/> |
| [stopBackgroundRunning](arkts-api10lessdeprecatedmodules-backgroundtaskmanager-stopbackgroundrunning-f.md#stopBackgroundRunning-1) | 向系统申请取消长时任务，使用callback异步回调。<br/> |
| [stopBackgroundRunning](arkts-api10lessdeprecatedmodules-backgroundtaskmanager-stopbackgroundrunning-f.md#stopBackgroundRunning-2) | 向系统申请取消长时任务，使用promise异步回调。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DelaySuspendInfo](arkts-api10lessdeprecatedmodules-backgroundtaskmanager-delaysuspendinfo-i.md) | 延迟挂起信息。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BackgroundMode](arkts-api10lessdeprecatedmodules-backgroundtaskmanager-backgroundmode-e.md) | 长时任务类型。<br/> |
| <!--DelRow-->[BackgroundMode](arkts-api10lessdeprecatedmodules-backgroundtaskmanager-backgroundmode-e-sys.md) | 长时任务类型。<br/> |

