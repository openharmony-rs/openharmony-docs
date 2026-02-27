| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: global;<br>API declaration: declare namespace stationary<br>Differences: declare namespace stationary|api/@ohos.stationary.d.ts|
|New API |NA|Class name: stationary;<br>API declaration: interface ActivityResponse<br>Differences: interface ActivityResponse|api/@ohos.stationary.d.ts|
|New API |NA|Class name: ActivityResponse;<br>API declaration: state: ActivityState;<br>Differences: state: ActivityState;|api/@ohos.stationary.d.ts|
|New API |NA|Class name: stationary;<br>API declaration: type ActivityType = 'still' \| 'relativeStill';<br>Differences: type ActivityType = 'still' \| 'relativeStill';|api/@ohos.stationary.d.ts|
|New API |NA|Class name: stationary;<br>API declaration: enum ActivityEvent<br>Differences: enum ActivityEvent|api/@ohos.stationary.d.ts|
|New API |NA|Class name: ActivityEvent;<br>API declaration: ENTER = 1<br>Differences: ENTER = 1|api/@ohos.stationary.d.ts|
|New API |NA|Class name: ActivityEvent;<br>API declaration: EXIT = 2<br>Differences: EXIT = 2|api/@ohos.stationary.d.ts|
|New API |NA|Class name: ActivityEvent;<br>API declaration: ENTER_EXIT = 3<br>Differences: ENTER_EXIT = 3|api/@ohos.stationary.d.ts|
|New API |NA|Class name: stationary;<br>API declaration: enum ActivityState<br>Differences: enum ActivityState|api/@ohos.stationary.d.ts|
|New API |NA|Class name: ActivityState;<br>API declaration: ENTER = 1<br>Differences: ENTER = 1|api/@ohos.stationary.d.ts|
|New API |NA|Class name: ActivityState;<br>API declaration: EXIT = 2<br>Differences: EXIT = 2|api/@ohos.stationary.d.ts|
|New API |NA|Class name: stationary;<br>API declaration: function on(activity: ActivityType, event: ActivityEvent, reportLatencyNs: number, callback: Callback\<ActivityResponse>): void;<br>Differences: function on(activity: ActivityType, event: ActivityEvent, reportLatencyNs: number, callback: Callback\<ActivityResponse>): void;|api/@ohos.stationary.d.ts|
|New API |NA|Class name: stationary;<br>API declaration: function once(activity: ActivityType, callback: Callback\<ActivityResponse>): void;<br>Differences: function once(activity: ActivityType, callback: Callback\<ActivityResponse>): void;|api/@ohos.stationary.d.ts|
|New API |NA|Class name: stationary;<br>API declaration: function off(activity: ActivityType, event: ActivityEvent, callback?: Callback\<ActivityResponse>): void;<br>Differences: function off(activity: ActivityType, event: ActivityEvent, callback?: Callback\<ActivityResponse>): void;|api/@ohos.stationary.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.stationary.d.ts<br>Differences: MultimodalAwarenessKit|api/@ohos.stationary.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.MultimodalAwarenessKit.d.ts<br>Differences: MultimodalAwarenessKit|kits/@kit.MultimodalAwarenessKit.d.ts|
