| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace stationary<br>差异内容：declare namespace stationary|api/@ohos.stationary.d.ts|
|新增API|NA|类名：stationary；<br>API声明：interface ActivityResponse<br>差异内容：interface ActivityResponse|api/@ohos.stationary.d.ts|
|新增API|NA|类名：ActivityResponse；<br>API声明：state: ActivityState;<br>差异内容：state: ActivityState;|api/@ohos.stationary.d.ts|
|新增API|NA|类名：stationary；<br>API声明：type ActivityType = 'still' \| 'relativeStill';<br>差异内容：type ActivityType = 'still' \| 'relativeStill';|api/@ohos.stationary.d.ts|
|新增API|NA|类名：stationary；<br>API声明：enum ActivityEvent<br>差异内容：enum ActivityEvent|api/@ohos.stationary.d.ts|
|新增API|NA|类名：ActivityEvent；<br>API声明：ENTER = 1<br>差异内容：ENTER = 1|api/@ohos.stationary.d.ts|
|新增API|NA|类名：ActivityEvent；<br>API声明：EXIT = 2<br>差异内容：EXIT = 2|api/@ohos.stationary.d.ts|
|新增API|NA|类名：ActivityEvent；<br>API声明：ENTER_EXIT = 3<br>差异内容：ENTER_EXIT = 3|api/@ohos.stationary.d.ts|
|新增API|NA|类名：stationary；<br>API声明：enum ActivityState<br>差异内容：enum ActivityState|api/@ohos.stationary.d.ts|
|新增API|NA|类名：ActivityState；<br>API声明：ENTER = 1<br>差异内容：ENTER = 1|api/@ohos.stationary.d.ts|
|新增API|NA|类名：ActivityState；<br>API声明：EXIT = 2<br>差异内容：EXIT = 2|api/@ohos.stationary.d.ts|
|新增API|NA|类名：stationary；<br>API声明：function on(activity: ActivityType, event: ActivityEvent, reportLatencyNs: number, callback: Callback\<ActivityResponse>): void;<br>差异内容：function on(activity: ActivityType, event: ActivityEvent, reportLatencyNs: number, callback: Callback\<ActivityResponse>): void;|api/@ohos.stationary.d.ts|
|新增API|NA|类名：stationary；<br>API声明：function once(activity: ActivityType, callback: Callback\<ActivityResponse>): void;<br>差异内容：function once(activity: ActivityType, callback: Callback\<ActivityResponse>): void;|api/@ohos.stationary.d.ts|
|新增API|NA|类名：stationary；<br>API声明：function off(activity: ActivityType, event: ActivityEvent, callback?: Callback\<ActivityResponse>): void;<br>差异内容：function off(activity: ActivityType, event: ActivityEvent, callback?: Callback\<ActivityResponse>): void;|api/@ohos.stationary.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.stationary.d.ts<br>差异内容：MultimodalAwarenessKit|api/@ohos.stationary.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.MultimodalAwarenessKit.d.ts<br>差异内容：MultimodalAwarenessKit|kits/@kit.MultimodalAwarenessKit.d.ts|
