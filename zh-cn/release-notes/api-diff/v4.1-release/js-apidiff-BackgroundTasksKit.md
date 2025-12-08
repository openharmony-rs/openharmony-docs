| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace backgroundTaskManager<br>差异内容：declare namespace backgroundTaskManager|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：interface DelaySuspendInfo<br>差异内容：interface DelaySuspendInfo|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：DelaySuspendInfo；<br>API声明：requestId: number;<br>差异内容：requestId: number;|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：DelaySuspendInfo；<br>API声明：actualDelayTime: number;<br>差异内容：actualDelayTime: number;|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function cancelSuspendDelay(requestId: number): void;<br>差异内容：function cancelSuspendDelay(requestId: number): void;|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function getRemainingDelayTime(requestId: number, callback: AsyncCallback\<number>): void;<br>差异内容：function getRemainingDelayTime(requestId: number, callback: AsyncCallback\<number>): void;|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function getRemainingDelayTime(requestId: number): Promise\<number>;<br>差异内容：function getRemainingDelayTime(requestId: number): Promise\<number>;|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function requestSuspendDelay(reason: string, callback: Callback\<void>): DelaySuspendInfo;<br>差异内容：function requestSuspendDelay(reason: string, callback: Callback\<void>): DelaySuspendInfo;|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent, callback: AsyncCallback\<void>): void;<br>差异内容：function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent, callback: AsyncCallback\<void>): void;|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent): Promise\<void>;<br>差异内容：function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent): Promise\<void>;|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function stopBackgroundRunning(context: Context, callback: AsyncCallback\<void>): void;<br>差异内容：function stopBackgroundRunning(context: Context, callback: AsyncCallback\<void>): void;|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function stopBackgroundRunning(context: Context): Promise\<void>;<br>差异内容：function stopBackgroundRunning(context: Context): Promise\<void>;|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：export enum BackgroundMode<br>差异内容：export enum BackgroundMode|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：BackgroundMode；<br>API声明：DATA_TRANSFER = 1<br>差异内容：DATA_TRANSFER = 1|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：BackgroundMode；<br>API声明：AUDIO_PLAYBACK = 2<br>差异内容：AUDIO_PLAYBACK = 2|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：BackgroundMode；<br>API声明：AUDIO_RECORDING = 3<br>差异内容：AUDIO_RECORDING = 3|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：BackgroundMode；<br>API声明：LOCATION = 4<br>差异内容：LOCATION = 4|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：BackgroundMode；<br>API声明：BLUETOOTH_INTERACTION = 5<br>差异内容：BLUETOOTH_INTERACTION = 5|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：BackgroundMode；<br>API声明：MULTI_DEVICE_CONNECTION = 6<br>差异内容：MULTI_DEVICE_CONNECTION = 6|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：BackgroundMode；<br>API声明：TASK_KEEPING = 9<br>差异内容：TASK_KEEPING = 9|api/@ohos.backgroundTaskManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace bundleState<br>差异内容：declare namespace bundleState|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：bundleState；<br>API声明：interface BundleStateInfo<br>差异内容：interface BundleStateInfo|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：BundleStateInfo；<br>API声明：id: number;<br>差异内容：id: number;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：BundleStateInfo；<br>API声明：abilityInFgTotalTime?: number;<br>差异内容：abilityInFgTotalTime?: number;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：BundleStateInfo；<br>API声明：abilityPrevAccessTime?: number;<br>差异内容：abilityPrevAccessTime?: number;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：BundleStateInfo；<br>API声明：abilityPrevSeenTime?: number;<br>差异内容：abilityPrevSeenTime?: number;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：BundleStateInfo；<br>API声明：abilitySeenTotalTime?: number;<br>差异内容：abilitySeenTotalTime?: number;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：BundleStateInfo；<br>API声明：bundleName?: string;<br>差异内容：bundleName?: string;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：BundleStateInfo；<br>API声明：fgAbilityAccessTotalTime?: number;<br>差异内容：fgAbilityAccessTotalTime?: number;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：BundleStateInfo；<br>API声明：fgAbilityPrevAccessTime?: number;<br>差异内容：fgAbilityPrevAccessTime?: number;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：BundleStateInfo；<br>API声明：infosBeginTime?: number;<br>差异内容：infosBeginTime?: number;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：BundleStateInfo；<br>API声明：infosEndTime?: number;<br>差异内容：infosEndTime?: number;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：BundleStateInfo；<br>API声明：merge(toMerge: BundleStateInfo): void;<br>差异内容：merge(toMerge: BundleStateInfo): void;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：bundleState；<br>API声明：interface BundleActiveState<br>差异内容：interface BundleActiveState|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：BundleActiveState；<br>API声明：appUsagePriorityGroup?: number;<br>差异内容：appUsagePriorityGroup?: number;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：BundleActiveState；<br>API声明：bundleName?: string;<br>差异内容：bundleName?: string;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：BundleActiveState；<br>API声明：indexOfLink?: string;<br>差异内容：indexOfLink?: string;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：BundleActiveState；<br>API声明：nameOfClass?: string;<br>差异内容：nameOfClass?: string;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：BundleActiveState；<br>API声明：stateOccurredTime?: number;<br>差异内容：stateOccurredTime?: number;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：BundleActiveState；<br>API声明：stateType?: number;<br>差异内容：stateType?: number;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：bundleState；<br>API声明：function isIdleState(bundleName: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：function isIdleState(bundleName: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：bundleState；<br>API声明：function isIdleState(bundleName: string): Promise\<boolean>;<br>差异内容：function isIdleState(bundleName: string): Promise\<boolean>;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：bundleState；<br>API声明：function queryAppUsagePriorityGroup(callback: AsyncCallback\<number>): void;<br>差异内容：function queryAppUsagePriorityGroup(callback: AsyncCallback\<number>): void;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：bundleState；<br>API声明：function queryAppUsagePriorityGroup(): Promise\<number>;<br>差异内容：function queryAppUsagePriorityGroup(): Promise\<number>;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：bundleState；<br>API声明：interface BundleActiveInfoResponse<br>差异内容：interface BundleActiveInfoResponse|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：BundleActiveInfoResponse；<br>API声明：[key: string]: BundleStateInfo;<br>差异内容：[key: string]: BundleStateInfo;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：bundleState；<br>API声明：export enum IntervalType<br>差异内容：export enum IntervalType|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：IntervalType；<br>API声明：BY_OPTIMIZED = 0<br>差异内容：BY_OPTIMIZED = 0|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：IntervalType；<br>API声明：BY_DAILY = 1<br>差异内容：BY_DAILY = 1|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：IntervalType；<br>API声明：BY_WEEKLY = 2<br>差异内容：BY_WEEKLY = 2|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：IntervalType；<br>API声明：BY_MONTHLY = 3<br>差异内容：BY_MONTHLY = 3|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：IntervalType；<br>API声明：BY_ANNUALLY = 4<br>差异内容：BY_ANNUALLY = 4|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：bundleState；<br>API声明：function queryCurrentBundleActiveStates(begin: number, end: number, callback: AsyncCallback\<Array\<BundleActiveState>>): void;<br>差异内容：function queryCurrentBundleActiveStates(begin: number, end: number, callback: AsyncCallback\<Array\<BundleActiveState>>): void;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：bundleState；<br>API声明：function queryCurrentBundleActiveStates(begin: number, end: number): Promise\<Array\<BundleActiveState>>;<br>差异内容：function queryCurrentBundleActiveStates(begin: number, end: number): Promise\<Array\<BundleActiveState>>;|api/@ohos.bundleState.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace reminderAgent<br>差异内容：declare namespace reminderAgent|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：function publishReminder(reminderReq: ReminderRequest, callback: AsyncCallback\<number>): void;<br>差异内容：function publishReminder(reminderReq: ReminderRequest, callback: AsyncCallback\<number>): void;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：function publishReminder(reminderReq: ReminderRequest): Promise\<number>;<br>差异内容：function publishReminder(reminderReq: ReminderRequest): Promise\<number>;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：function cancelReminder(reminderId: number, callback: AsyncCallback\<void>): void;<br>差异内容：function cancelReminder(reminderId: number, callback: AsyncCallback\<void>): void;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：function cancelReminder(reminderId: number): Promise\<void>;<br>差异内容：function cancelReminder(reminderId: number): Promise\<void>;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：function getValidReminders(callback: AsyncCallback\<Array\<ReminderRequest>>): void;<br>差异内容：function getValidReminders(callback: AsyncCallback\<Array\<ReminderRequest>>): void;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：function getValidReminders(): Promise\<Array\<ReminderRequest>>;<br>差异内容：function getValidReminders(): Promise\<Array\<ReminderRequest>>;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：function cancelAllReminders(callback: AsyncCallback\<void>): void;<br>差异内容：function cancelAllReminders(callback: AsyncCallback\<void>): void;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：function cancelAllReminders(): Promise\<void>;<br>差异内容：function cancelAllReminders(): Promise\<void>;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：function addNotificationSlot(slot: NotificationSlot, callback: AsyncCallback\<void>): void;<br>差异内容：function addNotificationSlot(slot: NotificationSlot, callback: AsyncCallback\<void>): void;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：function addNotificationSlot(slot: NotificationSlot): Promise\<void>;<br>差异内容：function addNotificationSlot(slot: NotificationSlot): Promise\<void>;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：function removeNotificationSlot(slotType: notification.SlotType, callback: AsyncCallback\<void>): void;<br>差异内容：function removeNotificationSlot(slotType: notification.SlotType, callback: AsyncCallback\<void>): void;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：function removeNotificationSlot(slotType: notification.SlotType): Promise\<void>;<br>差异内容：function removeNotificationSlot(slotType: notification.SlotType): Promise\<void>;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：export enum ActionButtonType<br>差异内容：export enum ActionButtonType|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ActionButtonType；<br>API声明：ACTION_BUTTON_TYPE_CLOSE = 0<br>差异内容：ACTION_BUTTON_TYPE_CLOSE = 0|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ActionButtonType；<br>API声明：ACTION_BUTTON_TYPE_SNOOZE = 1<br>差异内容：ACTION_BUTTON_TYPE_SNOOZE = 1|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：export enum ReminderType<br>差异内容：export enum ReminderType|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderType；<br>API声明：REMINDER_TYPE_TIMER = 0<br>差异内容：REMINDER_TYPE_TIMER = 0|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderType；<br>API声明：REMINDER_TYPE_CALENDAR = 1<br>差异内容：REMINDER_TYPE_CALENDAR = 1|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderType；<br>API声明：REMINDER_TYPE_ALARM = 2<br>差异内容：REMINDER_TYPE_ALARM = 2|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：interface ActionButton<br>差异内容：interface ActionButton|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ActionButton；<br>API声明：title: string;<br>差异内容：title: string;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ActionButton；<br>API声明：type: ActionButtonType;<br>差异内容：type: ActionButtonType;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：interface WantAgent<br>差异内容：interface WantAgent|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：WantAgent；<br>API声明：pkgName: string;<br>差异内容：pkgName: string;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：WantAgent；<br>API声明：abilityName: string;<br>差异内容：abilityName: string;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：interface MaxScreenWantAgent<br>差异内容：interface MaxScreenWantAgent|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：MaxScreenWantAgent；<br>API声明：pkgName: string;<br>差异内容：pkgName: string;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：MaxScreenWantAgent；<br>API声明：abilityName: string;<br>差异内容：abilityName: string;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：interface ReminderRequest<br>差异内容：interface ReminderRequest|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：reminderType: ReminderType;<br>差异内容：reminderType: ReminderType;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：actionButton?: [<br>            ActionButton?,<br>            ActionButton?<br>        ];<br>差异内容：actionButton?: [<br>            ActionButton?,<br>            ActionButton?<br>        ];|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：wantAgent?: WantAgent;<br>差异内容：wantAgent?: WantAgent;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：maxScreenWantAgent?: MaxScreenWantAgent;<br>差异内容：maxScreenWantAgent?: MaxScreenWantAgent;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：ringDuration?: number;<br>差异内容：ringDuration?: number;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：snoozeTimes?: number;<br>差异内容：snoozeTimes?: number;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：timeInterval?: number;<br>差异内容：timeInterval?: number;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：title?: string;<br>差异内容：title?: string;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：content?: string;<br>差异内容：content?: string;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：expiredContent?: string;<br>差异内容：expiredContent?: string;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：snoozeContent?: string;<br>差异内容：snoozeContent?: string;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：notificationId?: number;<br>差异内容：notificationId?: number;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：slotType?: notification.SlotType;<br>差异内容：slotType?: notification.SlotType;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：interface ReminderRequestCalendar<br>差异内容：interface ReminderRequestCalendar|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequestCalendar；<br>API声明：dateTime: LocalDateTime;<br>差异内容：dateTime: LocalDateTime;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequestCalendar；<br>API声明：repeatMonths?: Array\<number>;<br>差异内容：repeatMonths?: Array\<number>;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequestCalendar；<br>API声明：repeatDays?: Array\<number>;<br>差异内容：repeatDays?: Array\<number>;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：interface ReminderRequestAlarm<br>差异内容：interface ReminderRequestAlarm|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequestAlarm；<br>API声明：hour: number;<br>差异内容：hour: number;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequestAlarm；<br>API声明：minute: number;<br>差异内容：minute: number;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequestAlarm；<br>API声明：daysOfWeek?: Array\<number>;<br>差异内容：daysOfWeek?: Array\<number>;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：interface ReminderRequestTimer<br>差异内容：interface ReminderRequestTimer|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：ReminderRequestTimer；<br>API声明：triggerTimeInSeconds: number;<br>差异内容：triggerTimeInSeconds: number;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：reminderAgent；<br>API声明：interface LocalDateTime<br>差异内容：interface LocalDateTime|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：LocalDateTime；<br>API声明：year: number;<br>差异内容：year: number;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：LocalDateTime；<br>API声明：month: number;<br>差异内容：month: number;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：LocalDateTime；<br>API声明：day: number;<br>差异内容：day: number;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：LocalDateTime；<br>API声明：hour: number;<br>差异内容：hour: number;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：LocalDateTime；<br>API声明：minute: number;<br>差异内容：minute: number;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：LocalDateTime；<br>API声明：second?: number;<br>差异内容：second?: number;|api/@ohos.reminderAgent.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace reminderAgentManager<br>差异内容：declare namespace reminderAgentManager|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：function publishReminder(reminderReq: ReminderRequest, callback: AsyncCallback\<number>): void;<br>差异内容：function publishReminder(reminderReq: ReminderRequest, callback: AsyncCallback\<number>): void;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：function publishReminder(reminderReq: ReminderRequest): Promise\<number>;<br>差异内容：function publishReminder(reminderReq: ReminderRequest): Promise\<number>;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：function cancelReminder(reminderId: number, callback: AsyncCallback\<void>): void;<br>差异内容：function cancelReminder(reminderId: number, callback: AsyncCallback\<void>): void;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：function cancelReminder(reminderId: number): Promise\<void>;<br>差异内容：function cancelReminder(reminderId: number): Promise\<void>;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：function getValidReminders(callback: AsyncCallback\<Array\<ReminderRequest>>): void;<br>差异内容：function getValidReminders(callback: AsyncCallback\<Array\<ReminderRequest>>): void;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：function getValidReminders(): Promise\<Array\<ReminderRequest>>;<br>差异内容：function getValidReminders(): Promise\<Array\<ReminderRequest>>;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：function cancelAllReminders(callback: AsyncCallback\<void>): void;<br>差异内容：function cancelAllReminders(callback: AsyncCallback\<void>): void;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：function cancelAllReminders(): Promise\<void>;<br>差异内容：function cancelAllReminders(): Promise\<void>;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：function addNotificationSlot(slot: NotificationSlot, callback: AsyncCallback\<void>): void;<br>差异内容：function addNotificationSlot(slot: NotificationSlot, callback: AsyncCallback\<void>): void;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：function addNotificationSlot(slot: NotificationSlot): Promise\<void>;<br>差异内容：function addNotificationSlot(slot: NotificationSlot): Promise\<void>;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：function removeNotificationSlot(slotType: notification.SlotType, callback: AsyncCallback\<void>): void;<br>差异内容：function removeNotificationSlot(slotType: notification.SlotType, callback: AsyncCallback\<void>): void;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：function removeNotificationSlot(slotType: notification.SlotType): Promise\<void>;<br>差异内容：function removeNotificationSlot(slotType: notification.SlotType): Promise\<void>;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：export enum ActionButtonType<br>差异内容：export enum ActionButtonType|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ActionButtonType；<br>API声明：ACTION_BUTTON_TYPE_CLOSE = 0<br>差异内容：ACTION_BUTTON_TYPE_CLOSE = 0|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ActionButtonType；<br>API声明：ACTION_BUTTON_TYPE_SNOOZE = 1<br>差异内容：ACTION_BUTTON_TYPE_SNOOZE = 1|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：export enum ReminderType<br>差异内容：export enum ReminderType|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderType；<br>API声明：REMINDER_TYPE_TIMER = 0<br>差异内容：REMINDER_TYPE_TIMER = 0|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderType；<br>API声明：REMINDER_TYPE_CALENDAR = 1<br>差异内容：REMINDER_TYPE_CALENDAR = 1|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderType；<br>API声明：REMINDER_TYPE_ALARM = 2<br>差异内容：REMINDER_TYPE_ALARM = 2|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：interface ActionButton<br>差异内容：interface ActionButton|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ActionButton；<br>API声明：title: string;<br>差异内容：title: string;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ActionButton；<br>API声明：titleResource?: string;<br>差异内容：titleResource?: string;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ActionButton；<br>API声明：type: ActionButtonType;<br>差异内容：type: ActionButtonType;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：interface WantAgent<br>差异内容：interface WantAgent|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：WantAgent；<br>API声明：pkgName: string;<br>差异内容：pkgName: string;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：WantAgent；<br>API声明：abilityName: string;<br>差异内容：abilityName: string;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：interface MaxScreenWantAgent<br>差异内容：interface MaxScreenWantAgent|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：MaxScreenWantAgent；<br>API声明：pkgName: string;<br>差异内容：pkgName: string;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：MaxScreenWantAgent；<br>API声明：abilityName: string;<br>差异内容：abilityName: string;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：interface ReminderRequest<br>差异内容：interface ReminderRequest|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：reminderType: ReminderType;<br>差异内容：reminderType: ReminderType;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：actionButton?: [<br>            ActionButton?,<br>            ActionButton?,<br>            ActionButton?<br>        ];<br>差异内容：actionButton?: [<br>            ActionButton?,<br>            ActionButton?,<br>            ActionButton?<br>        ];|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：wantAgent?: WantAgent;<br>差异内容：wantAgent?: WantAgent;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：maxScreenWantAgent?: MaxScreenWantAgent;<br>差异内容：maxScreenWantAgent?: MaxScreenWantAgent;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：ringDuration?: number;<br>差异内容：ringDuration?: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：snoozeTimes?: number;<br>差异内容：snoozeTimes?: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：timeInterval?: number;<br>差异内容：timeInterval?: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：title?: string;<br>差异内容：title?: string;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：content?: string;<br>差异内容：content?: string;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：expiredContent?: string;<br>差异内容：expiredContent?: string;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：snoozeContent?: string;<br>差异内容：snoozeContent?: string;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：notificationId?: number;<br>差异内容：notificationId?: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：groupId?: string;<br>差异内容：groupId?: string;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：slotType?: notification.SlotType;<br>差异内容：slotType?: notification.SlotType;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：tapDismissed?: boolean;<br>差异内容：tapDismissed?: boolean;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：autoDeletedTime?: number;<br>差异内容：autoDeletedTime?: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：snoozeSlotType?: notification.SlotType;<br>差异内容：snoozeSlotType?: notification.SlotType;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：customRingUri?: string;<br>差异内容：customRingUri?: string;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：interface ReminderRequestCalendar<br>差异内容：interface ReminderRequestCalendar|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequestCalendar；<br>API声明：dateTime: LocalDateTime;<br>差异内容：dateTime: LocalDateTime;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequestCalendar；<br>API声明：repeatMonths?: Array\<number>;<br>差异内容：repeatMonths?: Array\<number>;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequestCalendar；<br>API声明：repeatDays?: Array\<number>;<br>差异内容：repeatDays?: Array\<number>;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequestCalendar；<br>API声明：daysOfWeek?: Array\<number>;<br>差异内容：daysOfWeek?: Array\<number>;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：interface ReminderRequestAlarm<br>差异内容：interface ReminderRequestAlarm|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequestAlarm；<br>API声明：hour: number;<br>差异内容：hour: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequestAlarm；<br>API声明：minute: number;<br>差异内容：minute: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequestAlarm；<br>API声明：daysOfWeek?: Array\<number>;<br>差异内容：daysOfWeek?: Array\<number>;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：interface ReminderRequestTimer<br>差异内容：interface ReminderRequestTimer|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequestTimer；<br>API声明：triggerTimeInSeconds: number;<br>差异内容：triggerTimeInSeconds: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：reminderAgentManager；<br>API声明：interface LocalDateTime<br>差异内容：interface LocalDateTime|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：LocalDateTime；<br>API声明：year: number;<br>差异内容：year: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：LocalDateTime；<br>API声明：month: number;<br>差异内容：month: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：LocalDateTime；<br>API声明：day: number;<br>差异内容：day: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：LocalDateTime；<br>API声明：hour: number;<br>差异内容：hour: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：LocalDateTime；<br>API声明：minute: number;<br>差异内容：minute: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：LocalDateTime；<br>API声明：second?: number;<br>差异内容：second?: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace backgroundTaskManager<br>差异内容：declare namespace backgroundTaskManager|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：interface DelaySuspendInfo<br>差异内容：interface DelaySuspendInfo|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：DelaySuspendInfo；<br>API声明：requestId: number;<br>差异内容：requestId: number;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：DelaySuspendInfo；<br>API声明：actualDelayTime: number;<br>差异内容：actualDelayTime: number;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function cancelSuspendDelay(requestId: number): void;<br>差异内容：function cancelSuspendDelay(requestId: number): void;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function getRemainingDelayTime(requestId: number, callback: AsyncCallback\<number>): void;<br>差异内容：function getRemainingDelayTime(requestId: number, callback: AsyncCallback\<number>): void;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function getRemainingDelayTime(requestId: number): Promise\<number>;<br>差异内容：function getRemainingDelayTime(requestId: number): Promise\<number>;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function requestSuspendDelay(reason: string, callback: Callback\<void>): DelaySuspendInfo;<br>差异内容：function requestSuspendDelay(reason: string, callback: Callback\<void>): DelaySuspendInfo;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent, callback: AsyncCallback\<void>): void;<br>差异内容：function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent, callback: AsyncCallback\<void>): void;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent): Promise\<void>;<br>差异内容：function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent): Promise\<void>;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function stopBackgroundRunning(context: Context, callback: AsyncCallback\<void>): void;<br>差异内容：function stopBackgroundRunning(context: Context, callback: AsyncCallback\<void>): void;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：function stopBackgroundRunning(context: Context): Promise\<void>;<br>差异内容：function stopBackgroundRunning(context: Context): Promise\<void>;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：export enum BackgroundMode<br>差异内容：export enum BackgroundMode|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：BackgroundMode；<br>API声明：DATA_TRANSFER = 1<br>差异内容：DATA_TRANSFER = 1|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：BackgroundMode；<br>API声明：AUDIO_PLAYBACK = 2<br>差异内容：AUDIO_PLAYBACK = 2|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：BackgroundMode；<br>API声明：AUDIO_RECORDING = 3<br>差异内容：AUDIO_RECORDING = 3|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：BackgroundMode；<br>API声明：LOCATION = 4<br>差异内容：LOCATION = 4|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：BackgroundMode；<br>API声明：BLUETOOTH_INTERACTION = 5<br>差异内容：BLUETOOTH_INTERACTION = 5|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：BackgroundMode；<br>API声明：MULTI_DEVICE_CONNECTION = 6<br>差异内容：MULTI_DEVICE_CONNECTION = 6|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：BackgroundMode；<br>API声明：TASK_KEEPING = 9<br>差异内容：TASK_KEEPING = 9|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace deviceStandby<br>差异内容：declare namespace deviceStandby|api/@ohos.resourceschedule.deviceStandby.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace usageStatistics<br>差异内容：declare namespace usageStatistics|api/@ohos.resourceschedule.usageStatistics.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace workScheduler<br>差异内容：declare namespace workScheduler|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：workScheduler；<br>API声明：export interface WorkInfo<br>差异内容：export interface WorkInfo|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：WorkInfo；<br>API声明：workId: number;<br>差异内容：workId: number;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：WorkInfo；<br>API声明：bundleName: string;<br>差异内容：bundleName: string;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：WorkInfo；<br>API声明：abilityName: string;<br>差异内容：abilityName: string;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：WorkInfo；<br>API声明：isPersisted?: boolean;<br>差异内容：isPersisted?: boolean;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：WorkInfo；<br>API声明：networkType?: NetworkType;<br>差异内容：networkType?: NetworkType;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：WorkInfo；<br>API声明：isCharging?: boolean;<br>差异内容：isCharging?: boolean;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：WorkInfo；<br>API声明：chargerType?: ChargingType;<br>差异内容：chargerType?: ChargingType;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：WorkInfo；<br>API声明：batteryLevel?: number;<br>差异内容：batteryLevel?: number;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：WorkInfo；<br>API声明：batteryStatus?: BatteryStatus;<br>差异内容：batteryStatus?: BatteryStatus;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：WorkInfo；<br>API声明：storageRequest?: StorageRequest;<br>差异内容：storageRequest?: StorageRequest;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：WorkInfo；<br>API声明：repeatCycleTime?: number;<br>差异内容：repeatCycleTime?: number;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：WorkInfo；<br>API声明：isRepeat?: boolean;<br>差异内容：isRepeat?: boolean;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：WorkInfo；<br>API声明：repeatCount?: number;<br>差异内容：repeatCount?: number;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：WorkInfo；<br>API声明：isDeepIdle?: boolean;<br>差异内容：isDeepIdle?: boolean;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：WorkInfo；<br>API声明：idleWaitTime?: number;<br>差异内容：idleWaitTime?: number;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：WorkInfo；<br>API声明：parameters?: Record\<string, number \| string \| boolean>;<br>差异内容：parameters?: Record\<string, number \| string \| boolean>;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：workScheduler；<br>API声明：function startWork(work: WorkInfo): void;<br>差异内容：function startWork(work: WorkInfo): void;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：workScheduler；<br>API声明：function stopWork(work: WorkInfo, needCancel?: boolean): void;<br>差异内容：function stopWork(work: WorkInfo, needCancel?: boolean): void;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：workScheduler；<br>API声明：function getWorkStatus(workId: number, callback: AsyncCallback\<WorkInfo>): void;<br>差异内容：function getWorkStatus(workId: number, callback: AsyncCallback\<WorkInfo>): void;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：workScheduler；<br>API声明：function getWorkStatus(workId: number): Promise\<WorkInfo>;<br>差异内容：function getWorkStatus(workId: number): Promise\<WorkInfo>;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：workScheduler；<br>API声明：function obtainAllWorks(callback: AsyncCallback\<void>): Array\<WorkInfo>;<br>差异内容：function obtainAllWorks(callback: AsyncCallback\<void>): Array\<WorkInfo>;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：workScheduler；<br>API声明：function obtainAllWorks(callback: AsyncCallback\<Array\<WorkInfo>>): void;<br>差异内容：function obtainAllWorks(callback: AsyncCallback\<Array\<WorkInfo>>): void;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：workScheduler；<br>API声明：function obtainAllWorks(): Promise\<Array\<WorkInfo>>;<br>差异内容：function obtainAllWorks(): Promise\<Array\<WorkInfo>>;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：workScheduler；<br>API声明：function stopAndClearWorks(): void;<br>差异内容：function stopAndClearWorks(): void;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：workScheduler；<br>API声明：function isLastWorkTimeOut(workId: number, callback: AsyncCallback\<void>): boolean;<br>差异内容：function isLastWorkTimeOut(workId: number, callback: AsyncCallback\<void>): boolean;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：workScheduler；<br>API声明：function isLastWorkTimeOut(workId: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：function isLastWorkTimeOut(workId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：workScheduler；<br>API声明：function isLastWorkTimeOut(workId: number): Promise\<boolean>;<br>差异内容：function isLastWorkTimeOut(workId: number): Promise\<boolean>;|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：workScheduler；<br>API声明：export enum NetworkType<br>差异内容：export enum NetworkType|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：NetworkType；<br>API声明：NETWORK_TYPE_ANY = 0<br>差异内容：NETWORK_TYPE_ANY = 0|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：NetworkType；<br>API声明：NETWORK_TYPE_MOBILE<br>差异内容：NETWORK_TYPE_MOBILE|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：NetworkType；<br>API声明：NETWORK_TYPE_WIFI<br>差异内容：NETWORK_TYPE_WIFI|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：NetworkType；<br>API声明：NETWORK_TYPE_BLUETOOTH<br>差异内容：NETWORK_TYPE_BLUETOOTH|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：NetworkType；<br>API声明：NETWORK_TYPE_WIFI_P2P<br>差异内容：NETWORK_TYPE_WIFI_P2P|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：NetworkType；<br>API声明：NETWORK_TYPE_ETHERNET<br>差异内容：NETWORK_TYPE_ETHERNET|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：workScheduler；<br>API声明：export enum ChargingType<br>差异内容：export enum ChargingType|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：ChargingType；<br>API声明：CHARGING_PLUGGED_ANY = 0<br>差异内容：CHARGING_PLUGGED_ANY = 0|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：ChargingType；<br>API声明：CHARGING_PLUGGED_AC<br>差异内容：CHARGING_PLUGGED_AC|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：ChargingType；<br>API声明：CHARGING_PLUGGED_USB<br>差异内容：CHARGING_PLUGGED_USB|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：ChargingType；<br>API声明：CHARGING_PLUGGED_WIRELESS<br>差异内容：CHARGING_PLUGGED_WIRELESS|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：workScheduler；<br>API声明：export enum BatteryStatus<br>差异内容：export enum BatteryStatus|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：BatteryStatus；<br>API声明：BATTERY_STATUS_LOW = 0<br>差异内容：BATTERY_STATUS_LOW = 0|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：BatteryStatus；<br>API声明：BATTERY_STATUS_OKAY<br>差异内容：BATTERY_STATUS_OKAY|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：BatteryStatus；<br>API声明：BATTERY_STATUS_LOW_OR_OKAY<br>差异内容：BATTERY_STATUS_LOW_OR_OKAY|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：workScheduler；<br>API声明：export enum StorageRequest<br>差异内容：export enum StorageRequest|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：StorageRequest；<br>API声明：STORAGE_LEVEL_LOW = 0<br>差异内容：STORAGE_LEVEL_LOW = 0|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：StorageRequest；<br>API声明：STORAGE_LEVEL_OKAY<br>差异内容：STORAGE_LEVEL_OKAY|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：StorageRequest；<br>API声明：STORAGE_LEVEL_LOW_OR_OKAY<br>差异内容：STORAGE_LEVEL_LOW_OR_OKAY|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增API|NA|类名：global；<br>API声明：export type WorkSchedulerExtensionContext = _WorkSchedulerExtensionContext;<br>差异内容：export type WorkSchedulerExtensionContext = _WorkSchedulerExtensionContext;|api/@ohos.WorkSchedulerExtensionAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class WorkSchedulerExtensionAbility<br>差异内容：export default class WorkSchedulerExtensionAbility|api/@ohos.WorkSchedulerExtensionAbility.d.ts|
|新增API|NA|类名：WorkSchedulerExtensionAbility；<br>API声明：context: WorkSchedulerExtensionContext;<br>差异内容：context: WorkSchedulerExtensionContext;|api/@ohos.WorkSchedulerExtensionAbility.d.ts|
|新增API|NA|类名：WorkSchedulerExtensionAbility；<br>API声明：onWorkStart(work: workScheduler.WorkInfo): void;<br>差异内容：onWorkStart(work: workScheduler.WorkInfo): void;|api/@ohos.WorkSchedulerExtensionAbility.d.ts|
|新增API|NA|类名：WorkSchedulerExtensionAbility；<br>API声明：onWorkStop(work: workScheduler.WorkInfo): void;<br>差异内容：onWorkStop(work: workScheduler.WorkInfo): void;|api/@ohos.WorkSchedulerExtensionAbility.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.backgroundTaskManager.d.ts<br>差异内容：BackgroundTasksKit|api/@ohos.backgroundTaskManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bundleState.d.ts<br>差异内容：BackgroundTasksKit|api/@ohos.bundleState.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.reminderAgent.d.ts<br>差异内容：BackgroundTasksKit|api/@ohos.reminderAgent.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.reminderAgentManager.d.ts<br>差异内容：BackgroundTasksKit|api/@ohos.reminderAgentManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.resourceschedule.backgroundTaskManager.d.ts<br>差异内容：BackgroundTasksKit|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.resourceschedule.deviceStandby.d.ts<br>差异内容：BackgroundTasksKit|api/@ohos.resourceschedule.deviceStandby.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.resourceschedule.usageStatistics.d.ts<br>差异内容：BackgroundTasksKit|api/@ohos.resourceschedule.usageStatistics.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.resourceschedule.workScheduler.d.ts<br>差异内容：BackgroundTasksKit|api/@ohos.resourceschedule.workScheduler.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.WorkSchedulerExtensionAbility.d.ts<br>差异内容：BackgroundTasksKit|api/@ohos.WorkSchedulerExtensionAbility.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.BackgroundTasksKit.d.ts<br>差异内容：BackgroundTasksKit|kits/@kit.BackgroundTasksKit.d.ts|
