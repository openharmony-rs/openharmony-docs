| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API模型切换|类名：global；<br>API声明：export default class WorkSchedulerExtensionAbility<br>差异内容：stagemodelonly|类名：global；<br>API声明：declare class WorkSchedulerExtensionAbility<br>差异内容：NA|api/@ohos.WorkSchedulerExtensionAbility.d.ts|
|删除错误码|类名：backgroundTaskManager；<br>API声明：function stopBackgroundRunning(context: Context, callback: AsyncCallback\<void>): void;<br>差异内容：201|类名：backgroundTaskManager；<br>API声明：function stopBackgroundRunning(context: Context, callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|删除错误码|类名：backgroundTaskManager；<br>API声明：function stopBackgroundRunning(context: Context): Promise\<void>;<br>差异内容：201|类名：backgroundTaskManager；<br>API声明：function stopBackgroundRunning(context: Context): Promise\<void>;<br>差异内容：NA|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace backgroundProcessManager<br>差异内容：declare namespace backgroundProcessManager|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|新增API|NA|类名：backgroundProcessManager；<br>API声明：export enum ProcessPriority<br>差异内容：export enum ProcessPriority|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|新增API|NA|类名：ProcessPriority；<br>API声明：PROCESS_BACKGROUND = 1<br>差异内容：PROCESS_BACKGROUND = 1|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|新增API|NA|类名：ProcessPriority；<br>API声明：PROCESS_INACTIVE = 2<br>差异内容：PROCESS_INACTIVE = 2|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|新增API|NA|类名：backgroundProcessManager；<br>API声明：export enum PowerSaveMode<br>差异内容：export enum PowerSaveMode|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|新增API|NA|类名：PowerSaveMode；<br>API声明：EFFICIENCY_MODE = 1<br>差异内容：EFFICIENCY_MODE = 1|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|新增API|NA|类名：PowerSaveMode；<br>API声明：DEFAULT_MODE = 2<br>差异内容：DEFAULT_MODE = 2|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|新增API|NA|类名：backgroundProcessManager；<br>API声明：function setProcessPriority(pid: number, priority: ProcessPriority): Promise\<void>;<br>差异内容：function setProcessPriority(pid: number, priority: ProcessPriority): Promise\<void>;|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|新增API|NA|类名：backgroundProcessManager；<br>API声明：function resetProcessPriority(pid: number): Promise\<void>;<br>差异内容：function resetProcessPriority(pid: number): Promise\<void>;|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|新增API|NA|类名：backgroundProcessManager；<br>API声明：function setPowerSaveMode(pid: number, powerSaveMode: PowerSaveMode): Promise\<void>;<br>差异内容：function setPowerSaveMode(pid: number, powerSaveMode: PowerSaveMode): Promise\<void>;|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|新增API|NA|类名：backgroundProcessManager；<br>API声明：function isPowerSaveMode(pid: number): Promise\<boolean>;<br>差异内容：function isPowerSaveMode(pid: number): Promise\<boolean>;|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：interface TransientTaskInfo<br>差异内容：interface TransientTaskInfo|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：TransientTaskInfo；<br>API声明：remainingQuota: number;<br>差异内容：remainingQuota: number;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：TransientTaskInfo；<br>API声明：transientTasks: DelaySuspendInfo[];<br>差异内容：transientTasks: DelaySuspendInfo[];|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskNotification；<br>API声明：continuousTaskId?: number;<br>差异内容：continuousTaskId?: number;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：interface ContinuousTaskCancelInfo<br>差异内容：interface ContinuousTaskCancelInfo|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskCancelInfo；<br>API声明：reason: ContinuousTaskCancelReason;<br>差异内容：reason: ContinuousTaskCancelReason;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskCancelInfo；<br>API声明：id: number;<br>差异内容：id: number;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：interface ContinuousTaskActiveInfo<br>差异内容：interface ContinuousTaskActiveInfo|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskActiveInfo；<br>API声明：id: number;<br>差异内容：id: number;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：interface ContinuousTaskInfo<br>差异内容：interface ContinuousTaskInfo|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskInfo；<br>API声明：abilityName: string;<br>差异内容：abilityName: string;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskInfo；<br>API声明：uid: number;<br>差异内容：uid: number;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskInfo；<br>API声明：pid: number;<br>差异内容：pid: number;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskInfo；<br>API声明：isFromWebView: boolean;<br>差异内容：isFromWebView: boolean;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskInfo；<br>API声明：backgroundModes: string[];<br>差异内容：backgroundModes: string[];|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskInfo；<br>API声明：backgroundSubModes: string[];<br>差异内容：backgroundSubModes: string[];|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskInfo；<br>API声明：notificationId: number;<br>差异内容：notificationId: number;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskInfo；<br>API声明：continuousTaskId: number;<br>差异内容：continuousTaskId: number;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskInfo；<br>API声明：abilityId: number;<br>差异内容：abilityId: number;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskInfo；<br>API声明：wantAgentBundleName: string;<br>差异内容：wantAgentBundleName: string;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskInfo；<br>API声明：wantAgentAbilityName: string;<br>差异内容：wantAgentAbilityName: string;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskInfo；<br>API声明：suspendState: boolean;<br>差异内容：suspendState: boolean;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：interface ContinuousTaskSuspendInfo<br>差异内容：interface ContinuousTaskSuspendInfo|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskSuspendInfo；<br>API声明：continuousTaskId: number;<br>差异内容：continuousTaskId: number;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskSuspendInfo；<br>API声明：suspendState: boolean;<br>差异内容：suspendState: boolean;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskSuspendInfo；<br>API声明：suspendReason: ContinuousTaskSuspendReason;<br>差异内容：suspendReason: ContinuousTaskSuspendReason;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function getTransientTaskInfo(): Promise\<TransientTaskInfo>;<br>差异内容：function getTransientTaskInfo(): Promise\<TransientTaskInfo>;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function getAllContinuousTasks(context: Context): Promise\<ContinuousTaskInfo[]>;<br>差异内容：function getAllContinuousTasks(context: Context): Promise\<ContinuousTaskInfo[]>;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function getAllContinuousTasks(context: Context, includeSuspended: boolean): Promise\<ContinuousTaskInfo[]>;<br>差异内容：function getAllContinuousTasks(context: Context, includeSuspended: boolean): Promise\<ContinuousTaskInfo[]>;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function on(type: 'continuousTaskCancel', callback: Callback\<ContinuousTaskCancelInfo>): void;<br>差异内容：function on(type: 'continuousTaskCancel', callback: Callback\<ContinuousTaskCancelInfo>): void;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function off(type: 'continuousTaskCancel', callback?: Callback\<ContinuousTaskCancelInfo>): void;<br>差异内容：function off(type: 'continuousTaskCancel', callback?: Callback\<ContinuousTaskCancelInfo>): void;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function on(type: 'continuousTaskSuspend', callback: Callback\<ContinuousTaskSuspendInfo>): void;<br>差异内容：function on(type: 'continuousTaskSuspend', callback: Callback\<ContinuousTaskSuspendInfo>): void;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function off(type: 'continuousTaskSuspend', callback?: Callback\<ContinuousTaskSuspendInfo>): void;<br>差异内容：function off(type: 'continuousTaskSuspend', callback?: Callback\<ContinuousTaskSuspendInfo>): void;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function on(type: 'continuousTaskActive', callback: Callback\<ContinuousTaskActiveInfo>): void;<br>差异内容：function on(type: 'continuousTaskActive', callback: Callback\<ContinuousTaskActiveInfo>): void;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function off(type: 'continuousTaskActive', callback?: Callback\<ContinuousTaskActiveInfo>): void;<br>差异内容：function off(type: 'continuousTaskActive', callback?: Callback\<ContinuousTaskActiveInfo>): void;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：export enum ContinuousTaskCancelReason<br>差异内容：export enum ContinuousTaskCancelReason|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskCancelReason；<br>API声明：USER_CANCEL = 1<br>差异内容：USER_CANCEL = 1|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskCancelReason；<br>API声明：SYSTEM_CANCEL = 2<br>差异内容：SYSTEM_CANCEL = 2|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskCancelReason；<br>API声明：USER_CANCEL_REMOVE_NOTIFICATION = 3<br>差异内容：USER_CANCEL_REMOVE_NOTIFICATION = 3|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskCancelReason；<br>API声明：SYSTEM_CANCEL_DATA_TRANSFER_LOW_SPEED = 4<br>差异内容：SYSTEM_CANCEL_DATA_TRANSFER_LOW_SPEED = 4|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskCancelReason；<br>API声明：SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_USE_AVSESSION = 5<br>差异内容：SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_USE_AVSESSION = 5|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskCancelReason；<br>API声明：SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_RUNNING = 6<br>差异内容：SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_RUNNING = 6|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskCancelReason；<br>API声明：SYSTEM_CANCEL_AUDIO_RECORDING_NOT_RUNNING = 7<br>差异内容：SYSTEM_CANCEL_AUDIO_RECORDING_NOT_RUNNING = 7|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskCancelReason；<br>API声明：SYSTEM_CANCEL_NOT_USE_LOCATION = 8<br>差异内容：SYSTEM_CANCEL_NOT_USE_LOCATION = 8|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskCancelReason；<br>API声明：SYSTEM_CANCEL_NOT_USE_BLUETOOTH = 9<br>差异内容：SYSTEM_CANCEL_NOT_USE_BLUETOOTH = 9|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskCancelReason；<br>API声明：SYSTEM_CANCEL_NOT_USE_MULTI_DEVICE = 10<br>差异内容：SYSTEM_CANCEL_NOT_USE_MULTI_DEVICE = 10|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskCancelReason；<br>API声明：SYSTEM_CANCEL_USE_ILLEGALLY = 11<br>差异内容：SYSTEM_CANCEL_USE_ILLEGALLY = 11|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：export enum BackgroundSubMode<br>差异内容：export enum BackgroundSubMode|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：BackgroundSubMode；<br>API声明：CAR_KEY = 1<br>差异内容：CAR_KEY = 1|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：export enum BackgroundModeType<br>差异内容：export enum BackgroundModeType|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：BackgroundModeType；<br>API声明：SUB_MODE = 'subMode'<br>差异内容：SUB_MODE = 'subMode'|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：export enum ContinuousTaskSuspendReason<br>差异内容：export enum ContinuousTaskSuspendReason|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskSuspendReason；<br>API声明：SYSTEM_SUSPEND_DATA_TRANSFER_LOW_SPEED = 4<br>差异内容：SYSTEM_SUSPEND_DATA_TRANSFER_LOW_SPEED = 4|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskSuspendReason；<br>API声明：SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_USE_AVSESSION = 5<br>差异内容：SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_USE_AVSESSION = 5|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskSuspendReason；<br>API声明：SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_RUNNING = 6<br>差异内容：SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_RUNNING = 6|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskSuspendReason；<br>API声明：SYSTEM_SUSPEND_AUDIO_RECORDING_NOT_RUNNING = 7<br>差异内容：SYSTEM_SUSPEND_AUDIO_RECORDING_NOT_RUNNING = 7|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskSuspendReason；<br>API声明：SYSTEM_SUSPEND_LOCATION_NOT_USED = 8<br>差异内容：SYSTEM_SUSPEND_LOCATION_NOT_USED = 8|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskSuspendReason；<br>API声明：SYSTEM_SUSPEND_BLUETOOTH_NOT_USED = 9<br>差异内容：SYSTEM_SUSPEND_BLUETOOTH_NOT_USED = 9|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskSuspendReason；<br>API声明：SYSTEM_SUSPEND_MULTI_DEVICE_NOT_USED = 10<br>差异内容：SYSTEM_SUSPEND_MULTI_DEVICE_NOT_USED = 10|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskSuspendReason；<br>API声明：SYSTEM_SUSPEND_USED_ILLEGALLY = 11<br>差异内容：SYSTEM_SUSPEND_USED_ILLEGALLY = 11|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：ContinuousTaskSuspendReason；<br>API声明：SYSTEM_SUSPEND_SYSTEM_LOAD_WARNING = 12<br>差异内容：SYSTEM_SUSPEND_SYSTEM_LOAD_WARNING = 12|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：function updateReminder(reminderId: number, reminderReq: ReminderRequest): Promise\<void>;<br>差异内容：function updateReminder(reminderId: number, reminderReq: ReminderRequest): Promise\<void>;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：export enum RingChannel<br>差异内容：export enum RingChannel|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：RingChannel；<br>API声明：RING_CHANNEL_ALARM = 0<br>差异内容：RING_CHANNEL_ALARM = 0|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：RingChannel；<br>API声明：RING_CHANNEL_MEDIA = 1<br>差异内容：RING_CHANNEL_MEDIA = 1|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：ringChannel?: RingChannel;<br>差异内容：ringChannel?: RingChannel;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：titleResourceId?: number;<br>差异内容：titleResourceId?: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：contentResourceId?: number;<br>差异内容：contentResourceId?: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：expiredContentResourceId?: number;<br>差异内容：expiredContentResourceId?: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：snoozeContentResourceId?: number;<br>差异内容：snoozeContentResourceId?: number;|api/@ohos.reminderAgentManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.resourceschedule.backgroundProcessManager.d.ts<br>差异内容：BackgroundTasksKit|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|arkts演进版本整改兼容变化|类名：global；<br>API声明：export default class WorkSchedulerExtensionAbility<br>差异内容：NA|类名：global；<br>API声明：declare class WorkSchedulerExtensionAbility<br>差异内容：NA|api/@ohos.WorkSchedulerExtensionAbility.d.ts|
|arkts演进版本整改兼容变化|类名：global；<br>API声明：export default class WorkSchedulerExtensionContext<br>差异内容：NA|类名：global；<br>API声明：declare class WorkSchedulerExtensionContext<br>差异内容：NA|api/application/WorkSchedulerExtensionContext.d.ts|
