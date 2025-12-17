| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API|NA|Class name: global;<br>API declaration: declare namespace backgroundTaskManager<br>Differences: declare namespace backgroundTaskManager|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: interface DelaySuspendInfo<br>Differences: interface DelaySuspendInfo|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: DelaySuspendInfo;<br>API declaration: requestId: number;<br>Differences: requestId: number;|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: DelaySuspendInfo;<br>API declaration: actualDelayTime: number;<br>Differences: actualDelayTime: number;|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: function cancelSuspendDelay(requestId: number): void;<br>Differences: function cancelSuspendDelay(requestId: number): void;|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: function getRemainingDelayTime(requestId: number, callback: AsyncCallback\<number>): void;<br>Differences: function getRemainingDelayTime(requestId: number, callback: AsyncCallback\<number>): void;|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: function getRemainingDelayTime(requestId: number): Promise\<number>;<br>Differences: function getRemainingDelayTime(requestId: number): Promise\<number>;|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: function requestSuspendDelay(reason: string, callback: Callback\<void>): DelaySuspendInfo;<br>Differences: function requestSuspendDelay(reason: string, callback: Callback\<void>): DelaySuspendInfo;|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent, callback: AsyncCallback\<void>): void;<br>Differences: function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent, callback: AsyncCallback\<void>): void;|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent): Promise\<void>;<br>Differences: function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent): Promise\<void>;|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: function stopBackgroundRunning(context: Context, callback: AsyncCallback\<void>): void;<br>Differences: function stopBackgroundRunning(context: Context, callback: AsyncCallback\<void>): void;|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: function stopBackgroundRunning(context: Context): Promise\<void>;<br>Differences: function stopBackgroundRunning(context: Context): Promise\<void>;|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: export enum BackgroundMode<br>Differences: export enum BackgroundMode|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: BackgroundMode;<br>API declaration: DATA_TRANSFER = 1<br>Differences: DATA_TRANSFER = 1|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: BackgroundMode;<br>API declaration: AUDIO_PLAYBACK = 2<br>Differences: AUDIO_PLAYBACK = 2|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: BackgroundMode;<br>API declaration: AUDIO_RECORDING = 3<br>Differences: AUDIO_RECORDING = 3|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: BackgroundMode;<br>API declaration: LOCATION = 4<br>Differences: LOCATION = 4|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: BackgroundMode;<br>API declaration: BLUETOOTH_INTERACTION = 5<br>Differences: BLUETOOTH_INTERACTION = 5|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: BackgroundMode;<br>API declaration: MULTI_DEVICE_CONNECTION = 6<br>Differences: MULTI_DEVICE_CONNECTION = 6|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: BackgroundMode;<br>API declaration: TASK_KEEPING = 9<br>Differences: TASK_KEEPING = 9|api/@ohos.backgroundTaskManager.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace bundleState<br>Differences: declare namespace bundleState|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: bundleState;<br>API declaration: interface BundleStateInfo<br>Differences: interface BundleStateInfo|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: BundleStateInfo;<br>API declaration: id: number;<br>Differences: id: number;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: BundleStateInfo;<br>API declaration: abilityInFgTotalTime?: number;<br>Differences: abilityInFgTotalTime?: number;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: BundleStateInfo;<br>API declaration: abilityPrevAccessTime?: number;<br>Differences: abilityPrevAccessTime?: number;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: BundleStateInfo;<br>API declaration: abilityPrevSeenTime?: number;<br>Differences: abilityPrevSeenTime?: number;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: BundleStateInfo;<br>API declaration: abilitySeenTotalTime?: number;<br>Differences: abilitySeenTotalTime?: number;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: BundleStateInfo;<br>API declaration: bundleName?: string;<br>Differences: bundleName?: string;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: BundleStateInfo;<br>API declaration: fgAbilityAccessTotalTime?: number;<br>Differences: fgAbilityAccessTotalTime?: number;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: BundleStateInfo;<br>API declaration: fgAbilityPrevAccessTime?: number;<br>Differences: fgAbilityPrevAccessTime?: number;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: BundleStateInfo;<br>API declaration: infosBeginTime?: number;<br>Differences: infosBeginTime?: number;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: BundleStateInfo;<br>API declaration: infosEndTime?: number;<br>Differences: infosEndTime?: number;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: BundleStateInfo;<br>API declaration: merge(toMerge: BundleStateInfo): void;<br>Differences: merge(toMerge: BundleStateInfo): void;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: bundleState;<br>API declaration: interface BundleActiveState<br>Differences: interface BundleActiveState|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: BundleActiveState;<br>API declaration: appUsagePriorityGroup?: number;<br>Differences: appUsagePriorityGroup?: number;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: BundleActiveState;<br>API declaration: bundleName?: string;<br>Differences: bundleName?: string;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: BundleActiveState;<br>API declaration: indexOfLink?: string;<br>Differences: indexOfLink?: string;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: BundleActiveState;<br>API declaration: nameOfClass?: string;<br>Differences: nameOfClass?: string;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: BundleActiveState;<br>API declaration: stateOccurredTime?: number;<br>Differences: stateOccurredTime?: number;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: BundleActiveState;<br>API declaration: stateType?: number;<br>Differences: stateType?: number;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: bundleState;<br>API declaration: function isIdleState(bundleName: string, callback: AsyncCallback\<boolean>): void;<br>Differences: function isIdleState(bundleName: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: bundleState;<br>API declaration: function isIdleState(bundleName: string): Promise\<boolean>;<br>Differences: function isIdleState(bundleName: string): Promise\<boolean>;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: bundleState;<br>API declaration: function queryAppUsagePriorityGroup(callback: AsyncCallback\<number>): void;<br>Differences: function queryAppUsagePriorityGroup(callback: AsyncCallback\<number>): void;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: bundleState;<br>API declaration: function queryAppUsagePriorityGroup(): Promise\<number>;<br>Differences: function queryAppUsagePriorityGroup(): Promise\<number>;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: bundleState;<br>API declaration: interface BundleActiveInfoResponse<br>Differences: interface BundleActiveInfoResponse|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: BundleActiveInfoResponse;<br>API declaration: [key: string]: BundleStateInfo;<br>Differences: [key: string]: BundleStateInfo;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: bundleState;<br>API declaration: export enum IntervalType<br>Differences: export enum IntervalType|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: IntervalType;<br>API declaration: BY_OPTIMIZED = 0<br>Differences: BY_OPTIMIZED = 0|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: IntervalType;<br>API declaration: BY_DAILY = 1<br>Differences: BY_DAILY = 1|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: IntervalType;<br>API declaration: BY_WEEKLY = 2<br>Differences: BY_WEEKLY = 2|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: IntervalType;<br>API declaration: BY_MONTHLY = 3<br>Differences: BY_MONTHLY = 3|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: IntervalType;<br>API declaration: BY_ANNUALLY = 4<br>Differences: BY_ANNUALLY = 4|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: bundleState;<br>API declaration: function queryCurrentBundleActiveStates(begin: number, end: number, callback: AsyncCallback\<Array\<BundleActiveState>>): void;<br>Differences: function queryCurrentBundleActiveStates(begin: number, end: number, callback: AsyncCallback\<Array\<BundleActiveState>>): void;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: bundleState;<br>API declaration: function queryCurrentBundleActiveStates(begin: number, end: number): Promise\<Array\<BundleActiveState>>;<br>Differences: function queryCurrentBundleActiveStates(begin: number, end: number): Promise\<Array\<BundleActiveState>>;|api/@ohos.bundleState.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace reminderAgent<br>Differences: declare namespace reminderAgent|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: function publishReminder(reminderReq: ReminderRequest, callback: AsyncCallback\<number>): void;<br>Differences: function publishReminder(reminderReq: ReminderRequest, callback: AsyncCallback\<number>): void;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: function publishReminder(reminderReq: ReminderRequest): Promise\<number>;<br>Differences: function publishReminder(reminderReq: ReminderRequest): Promise\<number>;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: function cancelReminder(reminderId: number, callback: AsyncCallback\<void>): void;<br>Differences: function cancelReminder(reminderId: number, callback: AsyncCallback\<void>): void;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: function cancelReminder(reminderId: number): Promise\<void>;<br>Differences: function cancelReminder(reminderId: number): Promise\<void>;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: function getValidReminders(callback: AsyncCallback\<Array\<ReminderRequest>>): void;<br>Differences: function getValidReminders(callback: AsyncCallback\<Array\<ReminderRequest>>): void;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: function getValidReminders(): Promise\<Array\<ReminderRequest>>;<br>Differences: function getValidReminders(): Promise\<Array\<ReminderRequest>>;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: function cancelAllReminders(callback: AsyncCallback\<void>): void;<br>Differences: function cancelAllReminders(callback: AsyncCallback\<void>): void;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: function cancelAllReminders(): Promise\<void>;<br>Differences: function cancelAllReminders(): Promise\<void>;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: function addNotificationSlot(slot: NotificationSlot, callback: AsyncCallback\<void>): void;<br>Differences: function addNotificationSlot(slot: NotificationSlot, callback: AsyncCallback\<void>): void;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: function addNotificationSlot(slot: NotificationSlot): Promise\<void>;<br>Differences: function addNotificationSlot(slot: NotificationSlot): Promise\<void>;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: function removeNotificationSlot(slotType: notification.SlotType, callback: AsyncCallback\<void>): void;<br>Differences: function removeNotificationSlot(slotType: notification.SlotType, callback: AsyncCallback\<void>): void;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: function removeNotificationSlot(slotType: notification.SlotType): Promise\<void>;<br>Differences: function removeNotificationSlot(slotType: notification.SlotType): Promise\<void>;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: export enum ActionButtonType<br>Differences: export enum ActionButtonType|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ActionButtonType;<br>API declaration: ACTION_BUTTON_TYPE_CLOSE = 0<br>Differences: ACTION_BUTTON_TYPE_CLOSE = 0|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ActionButtonType;<br>API declaration: ACTION_BUTTON_TYPE_SNOOZE = 1<br>Differences: ACTION_BUTTON_TYPE_SNOOZE = 1|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: export enum ReminderType<br>Differences: export enum ReminderType|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderType;<br>API declaration: REMINDER_TYPE_TIMER = 0<br>Differences: REMINDER_TYPE_TIMER = 0|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderType;<br>API declaration: REMINDER_TYPE_CALENDAR = 1<br>Differences: REMINDER_TYPE_CALENDAR = 1|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderType;<br>API declaration: REMINDER_TYPE_ALARM = 2<br>Differences: REMINDER_TYPE_ALARM = 2|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: interface ActionButton<br>Differences: interface ActionButton|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ActionButton;<br>API declaration: title: string;<br>Differences: title: string;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ActionButton;<br>API declaration: type: ActionButtonType;<br>Differences: type: ActionButtonType;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: interface WantAgent<br>Differences: interface WantAgent|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: WantAgent;<br>API declaration: pkgName: string;<br>Differences: pkgName: string;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: WantAgent;<br>API declaration: abilityName: string;<br>Differences: abilityName: string;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: interface MaxScreenWantAgent<br>Differences: interface MaxScreenWantAgent|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: MaxScreenWantAgent;<br>API declaration: pkgName: string;<br>Differences: pkgName: string;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: MaxScreenWantAgent;<br>API declaration: abilityName: string;<br>Differences: abilityName: string;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: interface ReminderRequest<br>Differences: interface ReminderRequest|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: reminderType: ReminderType;<br>Differences: reminderType: ReminderType;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: actionButton?: [<br>            ActionButton?,<br>            ActionButton?<br>        ];<br>Differences: actionButton?: [<br>            ActionButton?,<br>            ActionButton?<br>        ];|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: wantAgent?: WantAgent;<br>Differences: wantAgent?: WantAgent;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: maxScreenWantAgent?: MaxScreenWantAgent;<br>Differences: maxScreenWantAgent?: MaxScreenWantAgent;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: ringDuration?: number;<br>Differences: ringDuration?: number;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: snoozeTimes?: number;<br>Differences: snoozeTimes?: number;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: timeInterval?: number;<br>Differences: timeInterval?: number;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: title?: string;<br>Differences: title?: string;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: content?: string;<br>Differences: content?: string;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: expiredContent?: string;<br>Differences: expiredContent?: string;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: snoozeContent?: string;<br>Differences: snoozeContent?: string;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: notificationId?: number;<br>Differences: notificationId?: number;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: slotType?: notification.SlotType;<br>Differences: slotType?: notification.SlotType;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: interface ReminderRequestCalendar<br>Differences: interface ReminderRequestCalendar|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequestCalendar;<br>API declaration: dateTime: LocalDateTime;<br>Differences: dateTime: LocalDateTime;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequestCalendar;<br>API declaration: repeatMonths?: Array\<number>;<br>Differences: repeatMonths?: Array\<number>;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequestCalendar;<br>API declaration: repeatDays?: Array\<number>;<br>Differences: repeatDays?: Array\<number>;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: interface ReminderRequestAlarm<br>Differences: interface ReminderRequestAlarm|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequestAlarm;<br>API declaration: hour: number;<br>Differences: hour: number;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequestAlarm;<br>API declaration: minute: number;<br>Differences: minute: number;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequestAlarm;<br>API declaration: daysOfWeek?: Array\<number>;<br>Differences: daysOfWeek?: Array\<number>;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: interface ReminderRequestTimer<br>Differences: interface ReminderRequestTimer|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: ReminderRequestTimer;<br>API declaration: triggerTimeInSeconds: number;<br>Differences: triggerTimeInSeconds: number;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: reminderAgent;<br>API declaration: interface LocalDateTime<br>Differences: interface LocalDateTime|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: LocalDateTime;<br>API declaration: year: number;<br>Differences: year: number;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: LocalDateTime;<br>API declaration: month: number;<br>Differences: month: number;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: LocalDateTime;<br>API declaration: day: number;<br>Differences: day: number;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: LocalDateTime;<br>API declaration: hour: number;<br>Differences: hour: number;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: LocalDateTime;<br>API declaration: minute: number;<br>Differences: minute: number;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: LocalDateTime;<br>API declaration: second?: number;<br>Differences: second?: number;|api/@ohos.reminderAgent.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace reminderAgentManager<br>Differences: declare namespace reminderAgentManager|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: function publishReminder(reminderReq: ReminderRequest, callback: AsyncCallback\<number>): void;<br>Differences: function publishReminder(reminderReq: ReminderRequest, callback: AsyncCallback\<number>): void;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: function publishReminder(reminderReq: ReminderRequest): Promise\<number>;<br>Differences: function publishReminder(reminderReq: ReminderRequest): Promise\<number>;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: function cancelReminder(reminderId: number, callback: AsyncCallback\<void>): void;<br>Differences: function cancelReminder(reminderId: number, callback: AsyncCallback\<void>): void;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: function cancelReminder(reminderId: number): Promise\<void>;<br>Differences: function cancelReminder(reminderId: number): Promise\<void>;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: function getValidReminders(callback: AsyncCallback\<Array\<ReminderRequest>>): void;<br>Differences: function getValidReminders(callback: AsyncCallback\<Array\<ReminderRequest>>): void;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: function getValidReminders(): Promise\<Array\<ReminderRequest>>;<br>Differences: function getValidReminders(): Promise\<Array\<ReminderRequest>>;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: function cancelAllReminders(callback: AsyncCallback\<void>): void;<br>Differences: function cancelAllReminders(callback: AsyncCallback\<void>): void;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: function cancelAllReminders(): Promise\<void>;<br>Differences: function cancelAllReminders(): Promise\<void>;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: function addNotificationSlot(slot: NotificationSlot, callback: AsyncCallback\<void>): void;<br>Differences: function addNotificationSlot(slot: NotificationSlot, callback: AsyncCallback\<void>): void;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: function addNotificationSlot(slot: NotificationSlot): Promise\<void>;<br>Differences: function addNotificationSlot(slot: NotificationSlot): Promise\<void>;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: function removeNotificationSlot(slotType: notification.SlotType, callback: AsyncCallback\<void>): void;<br>Differences: function removeNotificationSlot(slotType: notification.SlotType, callback: AsyncCallback\<void>): void;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: function removeNotificationSlot(slotType: notification.SlotType): Promise\<void>;<br>Differences: function removeNotificationSlot(slotType: notification.SlotType): Promise\<void>;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: export enum ActionButtonType<br>Differences: export enum ActionButtonType|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ActionButtonType;<br>API declaration: ACTION_BUTTON_TYPE_CLOSE = 0<br>Differences: ACTION_BUTTON_TYPE_CLOSE = 0|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ActionButtonType;<br>API declaration: ACTION_BUTTON_TYPE_SNOOZE = 1<br>Differences: ACTION_BUTTON_TYPE_SNOOZE = 1|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: export enum ReminderType<br>Differences: export enum ReminderType|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderType;<br>API declaration: REMINDER_TYPE_TIMER = 0<br>Differences: REMINDER_TYPE_TIMER = 0|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderType;<br>API declaration: REMINDER_TYPE_CALENDAR = 1<br>Differences: REMINDER_TYPE_CALENDAR = 1|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderType;<br>API declaration: REMINDER_TYPE_ALARM = 2<br>Differences: REMINDER_TYPE_ALARM = 2|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: interface ActionButton<br>Differences: interface ActionButton|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ActionButton;<br>API declaration: title: string;<br>Differences: title: string;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ActionButton;<br>API declaration: titleResource?: string;<br>Differences: titleResource?: string;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ActionButton;<br>API declaration: type: ActionButtonType;<br>Differences: type: ActionButtonType;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: interface WantAgent<br>Differences: interface WantAgent|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: WantAgent;<br>API declaration: pkgName: string;<br>Differences: pkgName: string;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: WantAgent;<br>API declaration: abilityName: string;<br>Differences: abilityName: string;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: interface MaxScreenWantAgent<br>Differences: interface MaxScreenWantAgent|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: MaxScreenWantAgent;<br>API declaration: pkgName: string;<br>Differences: pkgName: string;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: MaxScreenWantAgent;<br>API declaration: abilityName: string;<br>Differences: abilityName: string;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: interface ReminderRequest<br>Differences: interface ReminderRequest|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: reminderType: ReminderType;<br>Differences: reminderType: ReminderType;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: actionButton?: [<br>            ActionButton?,<br>            ActionButton?,<br>            ActionButton?<br>        ];<br>Differences: actionButton?: [<br>            ActionButton?,<br>            ActionButton?,<br>            ActionButton?<br>        ];|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: wantAgent?: WantAgent;<br>Differences: wantAgent?: WantAgent;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: maxScreenWantAgent?: MaxScreenWantAgent;<br>Differences: maxScreenWantAgent?: MaxScreenWantAgent;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: ringDuration?: number;<br>Differences: ringDuration?: number;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: snoozeTimes?: number;<br>Differences: snoozeTimes?: number;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: timeInterval?: number;<br>Differences: timeInterval?: number;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: title?: string;<br>Differences: title?: string;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: content?: string;<br>Differences: content?: string;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: expiredContent?: string;<br>Differences: expiredContent?: string;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: snoozeContent?: string;<br>Differences: snoozeContent?: string;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: notificationId?: number;<br>Differences: notificationId?: number;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: groupId?: string;<br>Differences: groupId?: string;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: slotType?: notification.SlotType;<br>Differences: slotType?: notification.SlotType;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: tapDismissed?: boolean;<br>Differences: tapDismissed?: boolean;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: autoDeletedTime?: number;<br>Differences: autoDeletedTime?: number;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: snoozeSlotType?: notification.SlotType;<br>Differences: snoozeSlotType?: notification.SlotType;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequest;<br>API declaration: customRingUri?: string;<br>Differences: customRingUri?: string;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: interface ReminderRequestCalendar<br>Differences: interface ReminderRequestCalendar|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequestCalendar;<br>API declaration: dateTime: LocalDateTime;<br>Differences: dateTime: LocalDateTime;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequestCalendar;<br>API declaration: repeatMonths?: Array\<number>;<br>Differences: repeatMonths?: Array\<number>;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequestCalendar;<br>API declaration: repeatDays?: Array\<number>;<br>Differences: repeatDays?: Array\<number>;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequestCalendar;<br>API declaration: daysOfWeek?: Array\<number>;<br>Differences: daysOfWeek?: Array\<number>;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: interface ReminderRequestAlarm<br>Differences: interface ReminderRequestAlarm|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequestAlarm;<br>API declaration: hour: number;<br>Differences: hour: number;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequestAlarm;<br>API declaration: minute: number;<br>Differences: minute: number;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequestAlarm;<br>API declaration: daysOfWeek?: Array\<number>;<br>Differences: daysOfWeek?: Array\<number>;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: interface ReminderRequestTimer<br>Differences: interface ReminderRequestTimer|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: ReminderRequestTimer;<br>API declaration: triggerTimeInSeconds: number;<br>Differences: triggerTimeInSeconds: number;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: reminderAgentManager;<br>API declaration: interface LocalDateTime<br>Differences: interface LocalDateTime|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: LocalDateTime;<br>API declaration: year: number;<br>Differences: year: number;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: LocalDateTime;<br>API declaration: month: number;<br>Differences: month: number;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: LocalDateTime;<br>API declaration: day: number;<br>Differences: day: number;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: LocalDateTime;<br>API declaration: hour: number;<br>Differences: hour: number;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: LocalDateTime;<br>API declaration: minute: number;<br>Differences: minute: number;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: LocalDateTime;<br>API declaration: second?: number;<br>Differences: second?: number;|api/@ohos.reminderAgentManager.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace backgroundTaskManager<br>Differences: declare namespace backgroundTaskManager|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: interface DelaySuspendInfo<br>Differences: interface DelaySuspendInfo|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: DelaySuspendInfo;<br>API declaration: requestId: number;<br>Differences: requestId: number;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: DelaySuspendInfo;<br>API declaration: actualDelayTime: number;<br>Differences: actualDelayTime: number;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: function cancelSuspendDelay(requestId: number): void;<br>Differences: function cancelSuspendDelay(requestId: number): void;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: function getRemainingDelayTime(requestId: number, callback: AsyncCallback\<number>): void;<br>Differences: function getRemainingDelayTime(requestId: number, callback: AsyncCallback\<number>): void;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: function getRemainingDelayTime(requestId: number): Promise\<number>;<br>Differences: function getRemainingDelayTime(requestId: number): Promise\<number>;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: function requestSuspendDelay(reason: string, callback: Callback\<void>): DelaySuspendInfo;<br>Differences: function requestSuspendDelay(reason: string, callback: Callback\<void>): DelaySuspendInfo;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent, callback: AsyncCallback\<void>): void;<br>Differences: function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent, callback: AsyncCallback\<void>): void;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent): Promise\<void>;<br>Differences: function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent): Promise\<void>;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: function stopBackgroundRunning(context: Context, callback: AsyncCallback\<void>): void;<br>Differences: function stopBackgroundRunning(context: Context, callback: AsyncCallback\<void>): void;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: function stopBackgroundRunning(context: Context): Promise\<void>;<br>Differences: function stopBackgroundRunning(context: Context): Promise\<void>;|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: backgroundTaskManager;<br>API declaration: export enum BackgroundMode<br>Differences: export enum BackgroundMode|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: BackgroundMode;<br>API declaration: DATA_TRANSFER = 1<br>Differences: DATA_TRANSFER = 1|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: BackgroundMode;<br>API declaration: AUDIO_PLAYBACK = 2<br>Differences: AUDIO_PLAYBACK = 2|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: BackgroundMode;<br>API declaration: AUDIO_RECORDING = 3<br>Differences: AUDIO_RECORDING = 3|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: BackgroundMode;<br>API declaration: LOCATION = 4<br>Differences: LOCATION = 4|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: BackgroundMode;<br>API declaration: BLUETOOTH_INTERACTION = 5<br>Differences: BLUETOOTH_INTERACTION = 5|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: BackgroundMode;<br>API declaration: MULTI_DEVICE_CONNECTION = 6<br>Differences: MULTI_DEVICE_CONNECTION = 6|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: BackgroundMode;<br>API declaration: TASK_KEEPING = 9<br>Differences: TASK_KEEPING = 9|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace deviceStandby<br>Differences: declare namespace deviceStandby|api/@ohos.resourceschedule.deviceStandby.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace usageStatistics<br>Differences: declare namespace usageStatistics|api/@ohos.resourceschedule.usageStatistics.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace workScheduler<br>Differences: declare namespace workScheduler|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: workScheduler;<br>API declaration: export interface WorkInfo<br>Differences: export interface WorkInfo|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: WorkInfo;<br>API declaration: workId: number;<br>Differences: workId: number;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: WorkInfo;<br>API declaration: bundleName: string;<br>Differences: bundleName: string;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: WorkInfo;<br>API declaration: abilityName: string;<br>Differences: abilityName: string;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: WorkInfo;<br>API declaration: isPersisted?: boolean;<br>Differences: isPersisted?: boolean;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: WorkInfo;<br>API declaration: networkType?: NetworkType;<br>Differences: networkType?: NetworkType;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: WorkInfo;<br>API declaration: isCharging?: boolean;<br>Differences: isCharging?: boolean;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: WorkInfo;<br>API declaration: chargerType?: ChargingType;<br>Differences: chargerType?: ChargingType;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: WorkInfo;<br>API declaration: batteryLevel?: number;<br>Differences: batteryLevel?: number;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: WorkInfo;<br>API declaration: batteryStatus?: BatteryStatus;<br>Differences: batteryStatus?: BatteryStatus;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: WorkInfo;<br>API declaration: storageRequest?: StorageRequest;<br>Differences: storageRequest?: StorageRequest;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: WorkInfo;<br>API declaration: repeatCycleTime?: number;<br>Differences: repeatCycleTime?: number;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: WorkInfo;<br>API declaration: isRepeat?: boolean;<br>Differences: isRepeat?: boolean;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: WorkInfo;<br>API declaration: repeatCount?: number;<br>Differences: repeatCount?: number;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: WorkInfo;<br>API declaration: isDeepIdle?: boolean;<br>Differences: isDeepIdle?: boolean;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: WorkInfo;<br>API declaration: idleWaitTime?: number;<br>Differences: idleWaitTime?: number;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: WorkInfo;<br>API declaration: parameters?: Record\<string, number \| string \| boolean>;<br>Differences: parameters?: Record\<string, number \| string \| boolean>;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: workScheduler;<br>API declaration: function startWork(work: WorkInfo): void;<br>Differences: function startWork(work: WorkInfo): void;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: workScheduler;<br>API declaration: function stopWork(work: WorkInfo, needCancel?: boolean): void;<br>Differences: function stopWork(work: WorkInfo, needCancel?: boolean): void;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: workScheduler;<br>API declaration: function getWorkStatus(workId: number, callback: AsyncCallback\<WorkInfo>): void;<br>Differences: function getWorkStatus(workId: number, callback: AsyncCallback\<WorkInfo>): void;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: workScheduler;<br>API declaration: function getWorkStatus(workId: number): Promise\<WorkInfo>;<br>Differences: function getWorkStatus(workId: number): Promise\<WorkInfo>;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: workScheduler;<br>API declaration: function obtainAllWorks(callback: AsyncCallback\<void>): Array\<WorkInfo>;<br>Differences: function obtainAllWorks(callback: AsyncCallback\<void>): Array\<WorkInfo>;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: workScheduler;<br>API declaration: function obtainAllWorks(callback: AsyncCallback\<Array\<WorkInfo>>): void;<br>Differences: function obtainAllWorks(callback: AsyncCallback\<Array\<WorkInfo>>): void;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: workScheduler;<br>API declaration: function obtainAllWorks(): Promise\<Array\<WorkInfo>>;<br>Differences: function obtainAllWorks(): Promise\<Array\<WorkInfo>>;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: workScheduler;<br>API declaration: function stopAndClearWorks(): void;<br>Differences: function stopAndClearWorks(): void;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: workScheduler;<br>API declaration: function isLastWorkTimeOut(workId: number, callback: AsyncCallback\<void>): boolean;<br>Differences: function isLastWorkTimeOut(workId: number, callback: AsyncCallback\<void>): boolean;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: workScheduler;<br>API declaration: function isLastWorkTimeOut(workId: number, callback: AsyncCallback\<boolean>): void;<br>Differences: function isLastWorkTimeOut(workId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: workScheduler;<br>API declaration: function isLastWorkTimeOut(workId: number): Promise\<boolean>;<br>Differences: function isLastWorkTimeOut(workId: number): Promise\<boolean>;|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: workScheduler;<br>API declaration: export enum NetworkType<br>Differences: export enum NetworkType|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: NetworkType;<br>API declaration: NETWORK_TYPE_ANY = 0<br>Differences: NETWORK_TYPE_ANY = 0|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: NetworkType;<br>API declaration: NETWORK_TYPE_MOBILE<br>Differences: NETWORK_TYPE_MOBILE|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: NetworkType;<br>API declaration: NETWORK_TYPE_WIFI<br>Differences: NETWORK_TYPE_WIFI|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: NetworkType;<br>API declaration: NETWORK_TYPE_BLUETOOTH<br>Differences: NETWORK_TYPE_BLUETOOTH|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: NetworkType;<br>API declaration: NETWORK_TYPE_WIFI_P2P<br>Differences: NETWORK_TYPE_WIFI_P2P|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: NetworkType;<br>API declaration: NETWORK_TYPE_ETHERNET<br>Differences: NETWORK_TYPE_ETHERNET|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: workScheduler;<br>API declaration: export enum ChargingType<br>Differences: export enum ChargingType|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: ChargingType;<br>API declaration: CHARGING_PLUGGED_ANY = 0<br>Differences: CHARGING_PLUGGED_ANY = 0|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: ChargingType;<br>API declaration: CHARGING_PLUGGED_AC<br>Differences: CHARGING_PLUGGED_AC|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: ChargingType;<br>API declaration: CHARGING_PLUGGED_USB<br>Differences: CHARGING_PLUGGED_USB|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: ChargingType;<br>API declaration: CHARGING_PLUGGED_WIRELESS<br>Differences: CHARGING_PLUGGED_WIRELESS|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: workScheduler;<br>API declaration: export enum BatteryStatus<br>Differences: export enum BatteryStatus|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: BatteryStatus;<br>API declaration: BATTERY_STATUS_LOW = 0<br>Differences: BATTERY_STATUS_LOW = 0|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: BatteryStatus;<br>API declaration: BATTERY_STATUS_OKAY<br>Differences: BATTERY_STATUS_OKAY|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: BatteryStatus;<br>API declaration: BATTERY_STATUS_LOW_OR_OKAY<br>Differences: BATTERY_STATUS_LOW_OR_OKAY|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: workScheduler;<br>API declaration: export enum StorageRequest<br>Differences: export enum StorageRequest|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: StorageRequest;<br>API declaration: STORAGE_LEVEL_LOW = 0<br>Differences: STORAGE_LEVEL_LOW = 0|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: StorageRequest;<br>API declaration: STORAGE_LEVEL_OKAY<br>Differences: STORAGE_LEVEL_OKAY|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: StorageRequest;<br>API declaration: STORAGE_LEVEL_LOW_OR_OKAY<br>Differences: STORAGE_LEVEL_LOW_OR_OKAY|api/@ohos.resourceschedule.workScheduler.d.ts|
|New API|NA|Class name: global;<br>API declaration: export type WorkSchedulerExtensionContext = _WorkSchedulerExtensionContext;<br>Differences: export type WorkSchedulerExtensionContext = _WorkSchedulerExtensionContext;|api/@ohos.WorkSchedulerExtensionAbility.d.ts|
|New API|NA|Class name: global;<br>API declaration: export default class WorkSchedulerExtensionAbility<br>Differences: export default class WorkSchedulerExtensionAbility|api/@ohos.WorkSchedulerExtensionAbility.d.ts|
|New API|NA|Class name: WorkSchedulerExtensionAbility;<br>API declaration: context: WorkSchedulerExtensionContext;<br>Differences: context: WorkSchedulerExtensionContext;|api/@ohos.WorkSchedulerExtensionAbility.d.ts|
|New API|NA|Class name: WorkSchedulerExtensionAbility;<br>API declaration: onWorkStart(work: workScheduler.WorkInfo): void;<br>Differences: onWorkStart(work: workScheduler.WorkInfo): void;|api/@ohos.WorkSchedulerExtensionAbility.d.ts|
|New API|NA|Class name: WorkSchedulerExtensionAbility;<br>API declaration: onWorkStop(work: workScheduler.WorkInfo): void;<br>Differences: onWorkStop(work: workScheduler.WorkInfo): void;|api/@ohos.WorkSchedulerExtensionAbility.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.backgroundTaskManager.d.ts<br>Differences: BackgroundTasksKit|api/@ohos.backgroundTaskManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.bundleState.d.ts<br>Differences: BackgroundTasksKit|api/@ohos.bundleState.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.reminderAgent.d.ts<br>Differences: BackgroundTasksKit|api/@ohos.reminderAgent.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.reminderAgentManager.d.ts<br>Differences: BackgroundTasksKit|api/@ohos.reminderAgentManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.resourceschedule.backgroundTaskManager.d.ts<br>Differences: BackgroundTasksKit|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.resourceschedule.deviceStandby.d.ts<br>Differences: BackgroundTasksKit|api/@ohos.resourceschedule.deviceStandby.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.resourceschedule.usageStatistics.d.ts<br>Differences: BackgroundTasksKit|api/@ohos.resourceschedule.usageStatistics.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.resourceschedule.workScheduler.d.ts<br>Differences: BackgroundTasksKit|api/@ohos.resourceschedule.workScheduler.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.WorkSchedulerExtensionAbility.d.ts<br>Differences: BackgroundTasksKit|api/@ohos.WorkSchedulerExtensionAbility.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.BackgroundTasksKit.d.ts<br>Differences: BackgroundTasksKit|kits/@kit.BackgroundTasksKit.d.ts|
