| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API模型切换|类名：global；<br>API声明：declare class WorkSchedulerExtensionAbility<br>差异内容：NA|类名：global；<br>API声明：export default class WorkSchedulerExtensionAbility<br>差异内容：stagemodelonly|api/@ohos.WorkSchedulerExtensionAbility.d.ts|
|新增错误码|类名：backgroundTaskManager；<br>API声明：function stopBackgroundRunning(context: Context, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：backgroundTaskManager；<br>API声明：function stopBackgroundRunning(context: Context, callback: AsyncCallback\<void>): void;<br>差异内容：201|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增错误码|类名：backgroundTaskManager；<br>API声明：function stopBackgroundRunning(context: Context): Promise\<void>;<br>差异内容：NA|类名：backgroundTaskManager；<br>API声明：function stopBackgroundRunning(context: Context): Promise\<void>;<br>差异内容：201|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：global；<br>API声明：declare namespace backgroundProcessManager<br>差异内容：declare namespace backgroundProcessManager|NA|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|删除API|类名：backgroundProcessManager；<br>API声明：export enum ProcessPriority<br>差异内容：export enum ProcessPriority|NA|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|删除API|类名：ProcessPriority；<br>API声明：PROCESS_BACKGROUND = 1<br>差异内容：PROCESS_BACKGROUND = 1|NA|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|删除API|类名：ProcessPriority；<br>API声明：PROCESS_INACTIVE = 2<br>差异内容：PROCESS_INACTIVE = 2|NA|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|删除API|类名：backgroundProcessManager；<br>API声明：export enum PowerSaveMode<br>差异内容：export enum PowerSaveMode|NA|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|删除API|类名：PowerSaveMode；<br>API声明：EFFICIENCY_MODE = 1<br>差异内容：EFFICIENCY_MODE = 1|NA|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|删除API|类名：PowerSaveMode；<br>API声明：DEFAULT_MODE = 2<br>差异内容：DEFAULT_MODE = 2|NA|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|删除API|类名：backgroundProcessManager；<br>API声明：function setProcessPriority(pid: number, priority: ProcessPriority): Promise\<void>;<br>差异内容：function setProcessPriority(pid: number, priority: ProcessPriority): Promise\<void>;|NA|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|删除API|类名：backgroundProcessManager；<br>API声明：function resetProcessPriority(pid: number): Promise\<void>;<br>差异内容：function resetProcessPriority(pid: number): Promise\<void>;|NA|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|删除API|类名：backgroundProcessManager；<br>API声明：function setPowerSaveMode(pid: number, powerSaveMode: PowerSaveMode): Promise\<void>;<br>差异内容：function setPowerSaveMode(pid: number, powerSaveMode: PowerSaveMode): Promise\<void>;|NA|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|删除API|类名：backgroundProcessManager；<br>API声明：function isPowerSaveMode(pid: number): Promise\<boolean>;<br>差异内容：function isPowerSaveMode(pid: number): Promise\<boolean>;|NA|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|删除API|类名：reminderAgentManager；<br>API声明：function updateReminder(reminderId: number, reminderReq: ReminderRequest): Promise\<void>;<br>差异内容：function updateReminder(reminderId: number, reminderReq: ReminderRequest): Promise\<void>;|NA|api/@ohos.reminderAgentManager.d.ts|
|删除API|类名：reminderAgentManager；<br>API声明：export enum RingChannel<br>差异内容：export enum RingChannel|NA|api/@ohos.reminderAgentManager.d.ts|
|删除API|类名：RingChannel；<br>API声明：RING_CHANNEL_ALARM = 0<br>差异内容：RING_CHANNEL_ALARM = 0|NA|api/@ohos.reminderAgentManager.d.ts|
|删除API|类名：RingChannel；<br>API声明：RING_CHANNEL_MEDIA = 1<br>差异内容：RING_CHANNEL_MEDIA = 1|NA|api/@ohos.reminderAgentManager.d.ts|
|删除API|类名：ReminderRequest；<br>API声明：ringChannel?: RingChannel;<br>差异内容：ringChannel?: RingChannel;|NA|api/@ohos.reminderAgentManager.d.ts|
|删除API|类名：ReminderRequest；<br>API声明：titleResourceId?: number;<br>差异内容：titleResourceId?: number;|NA|api/@ohos.reminderAgentManager.d.ts|
|删除API|类名：ReminderRequest；<br>API声明：contentResourceId?: number;<br>差异内容：contentResourceId?: number;|NA|api/@ohos.reminderAgentManager.d.ts|
|删除API|类名：ReminderRequest；<br>API声明：expiredContentResourceId?: number;<br>差异内容：expiredContentResourceId?: number;|NA|api/@ohos.reminderAgentManager.d.ts|
|删除API|类名：ReminderRequest；<br>API声明：snoozeContentResourceId?: number;<br>差异内容：snoozeContentResourceId?: number;|NA|api/@ohos.reminderAgentManager.d.ts|
|删除API|类名：backgroundTaskManager；<br>API声明：interface TransientTaskInfo<br>差异内容：interface TransientTaskInfo|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：TransientTaskInfo；<br>API声明：remainingQuota: number;<br>差异内容：remainingQuota: number;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：TransientTaskInfo；<br>API声明：transientTasks: DelaySuspendInfo[];<br>差异内容：transientTasks: DelaySuspendInfo[];|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：backgroundTaskManager；<br>API声明：interface ContinuousTaskActiveInfo<br>差异内容：interface ContinuousTaskActiveInfo|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskActiveInfo；<br>API声明：id: number;<br>差异内容：id: number;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：backgroundTaskManager；<br>API声明：interface ContinuousTaskInfo<br>差异内容：interface ContinuousTaskInfo|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskInfo；<br>API声明：abilityName: string;<br>差异内容：abilityName: string;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskInfo；<br>API声明：uid: number;<br>差异内容：uid: number;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskInfo；<br>API声明：pid: number;<br>差异内容：pid: number;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskInfo；<br>API声明：isFromWebView: boolean;<br>差异内容：isFromWebView: boolean;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskInfo；<br>API声明：backgroundModes: string[];<br>差异内容：backgroundModes: string[];|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskInfo；<br>API声明：backgroundSubModes: string[];<br>差异内容：backgroundSubModes: string[];|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskInfo；<br>API声明：notificationId: number;<br>差异内容：notificationId: number;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskInfo；<br>API声明：continuousTaskId: number;<br>差异内容：continuousTaskId: number;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskInfo；<br>API声明：abilityId: number;<br>差异内容：abilityId: number;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskInfo；<br>API声明：wantAgentBundleName: string;<br>差异内容：wantAgentBundleName: string;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskInfo；<br>API声明：wantAgentAbilityName: string;<br>差异内容：wantAgentAbilityName: string;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskInfo；<br>API声明：suspendState: boolean;<br>差异内容：suspendState: boolean;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：backgroundTaskManager；<br>API声明：interface ContinuousTaskSuspendInfo<br>差异内容：interface ContinuousTaskSuspendInfo|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskSuspendInfo；<br>API声明：continuousTaskId: number;<br>差异内容：continuousTaskId: number;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskSuspendInfo；<br>API声明：suspendState: boolean;<br>差异内容：suspendState: boolean;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskSuspendInfo；<br>API声明：suspendReason: ContinuousTaskSuspendReason;<br>差异内容：suspendReason: ContinuousTaskSuspendReason;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：backgroundTaskManager；<br>API声明：function getTransientTaskInfo(): Promise\<TransientTaskInfo>;<br>差异内容：function getTransientTaskInfo(): Promise\<TransientTaskInfo>;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：backgroundTaskManager；<br>API声明：function getAllContinuousTasks(context: Context): Promise\<ContinuousTaskInfo[]>;<br>差异内容：function getAllContinuousTasks(context: Context): Promise\<ContinuousTaskInfo[]>;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：backgroundTaskManager；<br>API声明：function getAllContinuousTasks(context: Context, includeSuspended: boolean): Promise\<ContinuousTaskInfo[]>;<br>差异内容：function getAllContinuousTasks(context: Context, includeSuspended: boolean): Promise\<ContinuousTaskInfo[]>;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：backgroundTaskManager；<br>API声明：function on(type: 'continuousTaskSuspend', callback: Callback\<ContinuousTaskSuspendInfo>): void;<br>差异内容：function on(type: 'continuousTaskSuspend', callback: Callback\<ContinuousTaskSuspendInfo>): void;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：backgroundTaskManager；<br>API声明：function off(type: 'continuousTaskSuspend', callback?: Callback\<ContinuousTaskSuspendInfo>): void;<br>差异内容：function off(type: 'continuousTaskSuspend', callback?: Callback\<ContinuousTaskSuspendInfo>): void;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：backgroundTaskManager；<br>API声明：function on(type: 'continuousTaskActive', callback: Callback\<ContinuousTaskActiveInfo>): void;<br>差异内容：function on(type: 'continuousTaskActive', callback: Callback\<ContinuousTaskActiveInfo>): void;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：backgroundTaskManager；<br>API声明：function off(type: 'continuousTaskActive', callback?: Callback\<ContinuousTaskActiveInfo>): void;<br>差异内容：function off(type: 'continuousTaskActive', callback?: Callback\<ContinuousTaskActiveInfo>): void;|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：backgroundTaskManager；<br>API声明：export enum BackgroundSubMode<br>差异内容：export enum BackgroundSubMode|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：BackgroundSubMode；<br>API声明：CAR_KEY = 1<br>差异内容：CAR_KEY = 1|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：backgroundTaskManager；<br>API声明：export enum BackgroundModeType<br>差异内容：export enum BackgroundModeType|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：BackgroundModeType；<br>API声明：SUB_MODE = 'subMode'<br>差异内容：SUB_MODE = 'subMode'|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：backgroundTaskManager；<br>API声明：export enum ContinuousTaskSuspendReason<br>差异内容：export enum ContinuousTaskSuspendReason|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskSuspendReason；<br>API声明：SYSTEM_SUSPEND_DATA_TRANSFER_LOW_SPEED = 4<br>差异内容：SYSTEM_SUSPEND_DATA_TRANSFER_LOW_SPEED = 4|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskSuspendReason；<br>API声明：SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_USE_AVSESSION = 5<br>差异内容：SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_USE_AVSESSION = 5|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskSuspendReason；<br>API声明：SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_RUNNING = 6<br>差异内容：SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_RUNNING = 6|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskSuspendReason；<br>API声明：SYSTEM_SUSPEND_AUDIO_RECORDING_NOT_RUNNING = 7<br>差异内容：SYSTEM_SUSPEND_AUDIO_RECORDING_NOT_RUNNING = 7|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskSuspendReason；<br>API声明：SYSTEM_SUSPEND_LOCATION_NOT_USED = 8<br>差异内容：SYSTEM_SUSPEND_LOCATION_NOT_USED = 8|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskSuspendReason；<br>API声明：SYSTEM_SUSPEND_BLUETOOTH_NOT_USED = 9<br>差异内容：SYSTEM_SUSPEND_BLUETOOTH_NOT_USED = 9|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskSuspendReason；<br>API声明：SYSTEM_SUSPEND_MULTI_DEVICE_NOT_USED = 10<br>差异内容：SYSTEM_SUSPEND_MULTI_DEVICE_NOT_USED = 10|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskSuspendReason；<br>API声明：SYSTEM_SUSPEND_USED_ILLEGALLY = 11<br>差异内容：SYSTEM_SUSPEND_USED_ILLEGALLY = 11|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除API|类名：ContinuousTaskSuspendReason；<br>API声明：SYSTEM_SUSPEND_SYSTEM_LOAD_WARNING = 12<br>差异内容：SYSTEM_SUSPEND_SYSTEM_LOAD_WARNING = 12|NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除kit|类名：global；<br>API声明：api\@ohos.resourceschedule.backgroundProcessManager.d.ts<br>差异内容：BackgroundTasksKit|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|arkts演进版本整改兼容变化|类名：global；<br>API声明：declare class WorkSchedulerExtensionAbility<br>差异内容：NA|类名：global；<br>API声明：export default class WorkSchedulerExtensionAbility<br>差异内容：NA|api/@ohos.WorkSchedulerExtensionAbility.d.ts|
|arkts演进版本整改兼容变化|类名：global；<br>API声明：declare class WorkSchedulerExtensionContext<br>差异内容：NA|类名：global；<br>API声明：export default class WorkSchedulerExtensionContext<br>差异内容：NA|api/application/WorkSchedulerExtensionContext.d.ts|
