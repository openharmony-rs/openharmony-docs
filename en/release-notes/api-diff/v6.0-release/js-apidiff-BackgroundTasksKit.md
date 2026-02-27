| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: global;<br>API declaration: declare namespace backgroundProcessManager<br>DIfferences: declare namespace backgroundProcessManager|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|New API |NA|Class name: backgroundProcessManager;<br>API declaration: export enum ProcessPriority<br>DIfferences: export enum ProcessPriority|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|New API |NA|Class name: ProcessPriority;<br>API declaration: PROCESS_BACKGROUND = 1<br>DIfferences: PROCESS_BACKGROUND = 1|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|New API |NA|Class name: ProcessPriority;<br>API declaration: PROCESS_INACTIVE = 2<br>DIfferences: PROCESS_INACTIVE = 2|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|New API |NA|Class name: backgroundProcessManager;<br>API declaration: function setProcessPriority(pid: number, priority: ProcessPriority): Promise\<void>;<br>DIfferences: function setProcessPriority(pid: number, priority: ProcessPriority): Promise\<void>;|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|New API |NA|Class name: backgroundProcessManager;<br>API declaration: function resetProcessPriority(pid: number): Promise\<void>;<br>DIfferences: function resetProcessPriority(pid: number): Promise\<void>;|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|New API |NA|Class name: ReminderRequest;<br>API declaration: titleResourceId?: number;<br>DIfferences: titleResourceId?: number;|api/@ohos.reminderAgentManager.d.ts|
|New API |NA|Class name: ReminderRequest;<br>API declaration: contentResourceId?: number;<br>DIfferences: contentResourceId?: number;|api/@ohos.reminderAgentManager.d.ts|
|New API |NA|Class name: ReminderRequest;<br>API declaration: expiredContentResourceId?: number;<br>DIfferences: expiredContentResourceId?: number;|api/@ohos.reminderAgentManager.d.ts|
|New API |NA|Class name: ReminderRequest;<br>API declaration: snoozeContentResourceId?: number;<br>DIfferences: snoozeContentResourceId?: number;|api/@ohos.reminderAgentManager.d.ts|
|New API |NA|Class name: backgroundTaskManager;<br>API declaration: export enum BackgroundSubMode<br>DIfferences: export enum BackgroundSubMode|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API |NA|Class name: BackgroundSubMode;<br>API declaration: CAR_KEY = 1<br>DIfferences: CAR_KEY = 1|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API |NA|Class name: backgroundTaskManager;<br>API declaration: export enum BackgroundModeType<br>DIfferences: export enum BackgroundModeType|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New API |NA|Class name: BackgroundModeType;<br>API declaration: SUB_MODE = 'subMode'<br>DIfferences: SUB_MODE = 'subMode'|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>DIfferences: NA|Class name: global;<br>API declaration: api\@ohos.resourceschedule.backgroundProcessManager.d.ts<br>DIfferences: BackgroundTasksKit|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
