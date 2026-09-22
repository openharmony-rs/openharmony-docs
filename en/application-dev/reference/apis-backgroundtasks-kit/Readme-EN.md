# Background Tasks Kit<!--background-tasks-api-->

<!--Kit: Background Tasks Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=298e4d5de4139f6963e24584b03fa18002046fd4 translatedAt=2026-09-22T01:19:22.629Z pushedAt=2026-09-22T08:29:46.698Z -->

- ArkTS APIs<!--background-tasks-arkts-->
  - [@ohos.reminderAgentManager (Background Agent Reminder)](js-apis-reminderAgentManager.md)
  - [@ohos.resourceschedule.backgroundTaskManager (Background Task Management)](js-apis-resourceschedule-backgroundTaskManager.md) 
  - [@ohos.resourceschedule.workScheduler (Deferred Task Scheduling)](js-apis-resourceschedule-workScheduler.md)
  - [@ohos.WorkSchedulerExtensionAbility (Deferred Task Scheduling Callbacks)](js-apis-WorkSchedulerExtensionAbility.md)
  - [@ohos.resourceschedule.backgroundProcessManager (Background Child Process Management)](js-apis-backgroundProcessManager.md)
  - [@ohos.resourceschedule.backgroundLoader (Background Loader)](js-apis-resourceschedule-backgroundLoader.md)
  <!--Del-->
  - [@ohos.reminderAgentManager (Background Agent Reminder) (system API)](js-apis-reminderAgentManager-sys.md)
  - [@ohos.resourceschedule.backgroundTaskManager (Background Task Management) (System API)](js-apis-resourceschedule-backgroundTaskManager-sys.md)
  - [@ohos.resourceschedule.deviceStandby (Device Standby) (System API)](js-apis-resourceschedule-deviceStandby-sys.md)
  - [@ohos.resourceschedule.usageStatistics (Device Usage Statistics) (System API)](js-apis-resourceschedule-deviceUsageStatistics-sys.md)
  - [@ohos.resourceschedule.workScheduler (Deferred Task Scheduling) (System API)](js-apis-resourceschedule-workScheduler-sys.md)
  - [@ohos.resourceschedule.backgroundProcessManager (Background Child Process Management) (System API)](js-apis-backgroundProcessManager-sys.md)
  <!--DelEnd-->
  - Application<!--background-tasks-arkts-application-->
    - [WorkSchedulerExtensionContext (Work Scheduler Callback Context)](js-apis-WorkSchedulerExtensionContext.md)
    <!--Del-->
    - [WorkSchedulerExtensionContext (Work Scheduler Callback Context) (system API)](js-apis-WorkSchedulerExtensionContext-sys.md)
    <!--DelEnd-->
  - APIs No Longer Maintained<!--background-tasks-arkts-dep-->
    - [@ohos.backgroundTaskManager (Background Task Management)](js-apis-backgroundTaskManager.md)
    - [@ohos.bundleState (Device Usage Statistics)](js-apis-deviceUsageStatistics.md)
    - [@ohos.reminderAgent (Background Agent Reminder)](js-apis-reminderAgent.md)
    <!--Del-->
    - [@ohos.backgroundTaskManager (Background Task Management) (System API)](js-apis-backgroundTaskManager-sys.md)
    - [@ohos.bundleState (Device Usage Statistics) (System API)](js-apis-deviceUsageStatistics-sys.md)
    <!--DelEnd-->
- C APIs<!--background-tasks-c-->
  - Module<!--background-tasks-module-->
    - [BackgroundProcessManager](capi-backgroundprocessmanager.md)
    - [TransientTask](capi-transienttask.md)
  - Header Files<!--background-tasks-headerfile-->
    - [background_process_manager.h](capi-background-process-manager-h.md)
    - [transient_task_api.h](capi-transient-task-api-h.md)
    - [transient_task_type.h](capi-transient-task-type-h.md)
  - Structs<!--background-tasks-struct-->
    - [TransientTask_DelaySuspendInfo](capi-transienttask-transienttask-delaysuspendinfo.md)
    - [TransientTask_TransientTaskInfo](capi-transienttask-transienttask-transienttaskinfo.md)
- Error Codes<!--background-tasks-arkts-errcode-->
  - [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md)
  - [backgroundProcessManager Error Codes](errorcode-backgroundProcessManager.md)
  <!--Del-->
  - [DeviceUsageStatistics Error Codes](errorcode-DeviceUsageStatistics.md)
  <!--DelEnd-->
  - [reminderAgentManager Error Codes](errorcode-reminderAgentManager.md)
  - [workScheduler Error Codes](errorcode-workScheduler.md)
  - <!--no_check-->