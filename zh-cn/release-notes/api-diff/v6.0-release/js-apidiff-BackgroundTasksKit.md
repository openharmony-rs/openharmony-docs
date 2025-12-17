| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace backgroundProcessManager<br>差异内容：declare namespace backgroundProcessManager|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|新增API|NA|类名：backgroundProcessManager；<br>API声明：export enum ProcessPriority<br>差异内容：export enum ProcessPriority|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|新增API|NA|类名：ProcessPriority；<br>API声明：PROCESS_BACKGROUND = 1<br>差异内容：PROCESS_BACKGROUND = 1|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|新增API|NA|类名：ProcessPriority；<br>API声明：PROCESS_INACTIVE = 2<br>差异内容：PROCESS_INACTIVE = 2|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|新增API|NA|类名：backgroundProcessManager；<br>API声明：function setProcessPriority(pid: number, priority: ProcessPriority): Promise\<void>;<br>差异内容：function setProcessPriority(pid: number, priority: ProcessPriority): Promise\<void>;|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|新增API|NA|类名：backgroundProcessManager；<br>API声明：function resetProcessPriority(pid: number): Promise\<void>;<br>差异内容：function resetProcessPriority(pid: number): Promise\<void>;|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：titleResourceId?: number;<br>差异内容：titleResourceId?: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：contentResourceId?: number;<br>差异内容：contentResourceId?: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：expiredContentResourceId?: number;<br>差异内容：expiredContentResourceId?: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：ReminderRequest；<br>API声明：snoozeContentResourceId?: number;<br>差异内容：snoozeContentResourceId?: number;|api/@ohos.reminderAgentManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：export enum BackgroundSubMode<br>差异内容：export enum BackgroundSubMode|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：BackgroundSubMode；<br>API声明：CAR_KEY = 1<br>差异内容：CAR_KEY = 1|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：backgroundTaskManager；<br>API声明：export enum BackgroundModeType<br>差异内容：export enum BackgroundModeType|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增API|NA|类名：BackgroundModeType；<br>API声明：SUB_MODE = 'subMode'<br>差异内容：SUB_MODE = 'subMode'|api/@ohos.resourceschedule.backgroundTaskManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.resourceschedule.backgroundProcessManager.d.ts<br>差异内容：BackgroundTasksKit|api/@ohos.resourceschedule.backgroundProcessManager.d.ts|
