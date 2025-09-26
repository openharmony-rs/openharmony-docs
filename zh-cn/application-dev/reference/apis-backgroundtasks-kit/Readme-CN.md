# Background Tasks Kit（后台任务开发服务）<!--background-tasks-api-->

<!--Kit: Background Tasks Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @cheng-shichang-->
<!--Designer: @zhouben25-->
<!--Tester: @fenglili18-->
<!--Adviser: @Brilliantry_Rui-->

- ArkTS API<!--background-tasks-arkts-->
  - [@ohos.reminderAgentManager (后台代理提醒)](js-apis-reminderAgentManager.md)
  - [@ohos.resourceschedule.backgroundTaskManager (后台任务管理)](js-apis-resourceschedule-backgroundTaskManager.md) 
  - [@ohos.resourceschedule.workScheduler (延迟任务调度)](js-apis-resourceschedule-workScheduler.md)
  - [@ohos.WorkSchedulerExtensionAbility (延迟任务调度回调)](js-apis-WorkSchedulerExtensionAbility.md)
  - [@ohos.resourceschedule.backgroundProcessManager (后台子进程管控)](js-apis-backgroundProcessManager.md)
  <!--Del-->
  - [@ohos.reminderAgentManager (后台代理提醒)(系统接口)](js-apis-reminderAgentManager-sys.md)
  - [@ohos.resourceschedule.backgroundTaskManager (后台任务管理)(系统接口)](js-apis-resourceschedule-backgroundTaskManager-sys.md)
  - [@ohos.resourceschedule.deviceStandby (设备待机模块)(系统接口)](js-apis-resourceschedule-deviceStandby-sys.md)
  - [@ohos.resourceschedule.usageStatistics (设备使用信息统计)(系统接口)](js-apis-resourceschedule-deviceUsageStatistics-sys.md) 
  <!--DelEnd-->
  - application<!--background-tasks-arkts-application-->
    - [WorkSchedulerExtensionContext](js-apis-inner-application-WorkSchedulerExtensionContext.md)
    <!--Del-->
    - [WorkSchedulerExtensionContext(系统接口)](js-apis-inner-application-WorkSchedulerExtensionContext-sys.md)
    <!--DelEnd-->
  - 已停止维护的接口<!--background-tasks-arkts-dep-->
    - [@ohos.backgroundTaskManager (后台任务管理)](js-apis-backgroundTaskManager.md)
    - [@ohos.bundleState (设备使用信息统计)](js-apis-deviceUsageStatistics.md)
    - [@ohos.reminderAgent (后台代理提醒)](js-apis-reminderAgent.md)
    <!--Del-->
    - [@ohos.backgroundTaskManager (后台任务管理)(系统接口)](js-apis-backgroundTaskManager-sys.md)
    - [@ohos.bundleState (设备使用信息统计)(系统接口)](js-apis-deviceUsageStatistics-sys.md)
    <!--DelEnd-->
- C API<!--background-tasks-c-->
  - 模块<!--background-tasks-module-->
    - [BackgroundProcessManager](capi-backgroundprocessmanager.md)
    - [TransientTask](capi-transienttask.md)
  - 头文件<!--background-tasks-headerfile-->
    - [background_process_manager.h](capi-background-process-manager-h.md)
    - [transient_task_api.h](capi-transient-task-api-h.md)
    - [transient_task_type.h](capi-transient-task-type-h.md)
  - 结构体<!--background-tasks-struct-->
    - [TransientTask_DelaySuspendInfo](capi-transienttask-transienttask-delaysuspendinfo.md)
    - [TransientTask_TransientTaskInfo](capi-transienttask-transienttask-transienttaskinfo.md)
- 错误码<!--background-tasks-arkts-errcode-->
  - [backgroundTaskManager错误码](errorcode-backgroundTaskMgr.md)
  - [backgroundProcessManager错误码](errorcode-backgroundProcessManager.md)
  <!--Del-->
  - [DeviceUsageStatistics错误码](errorcode-DeviceUsageStatistics.md)
  <!--DelEnd-->
  - [reminderAgentManager错误码](errorcode-reminderAgentManager.md)
  - [workScheduler错误码](errorcode-workScheduler.md)