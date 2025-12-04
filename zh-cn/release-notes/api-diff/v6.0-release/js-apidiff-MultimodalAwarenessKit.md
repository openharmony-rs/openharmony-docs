| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace deviceStatus<br>差异内容：declare namespace deviceStatus|api/@ohos.multimodalAwareness.deviceStatus.d.ts|
|新增API|NA|类名：deviceStatus；<br>API声明：export enum SteadyStandingStatus<br>差异内容：export enum SteadyStandingStatus|api/@ohos.multimodalAwareness.deviceStatus.d.ts|
|新增API|NA|类名：SteadyStandingStatus；<br>API声明：STATUS_EXIT = 0<br>差异内容：STATUS_EXIT = 0|api/@ohos.multimodalAwareness.deviceStatus.d.ts|
|新增API|NA|类名：SteadyStandingStatus；<br>API声明：STATUS_ENTER = 1<br>差异内容：STATUS_ENTER = 1|api/@ohos.multimodalAwareness.deviceStatus.d.ts|
|新增API|NA|类名：deviceStatus；<br>API声明：function on(type: 'steadyStandingDetect', callback: Callback\<SteadyStandingStatus>): void;<br>差异内容：function on(type: 'steadyStandingDetect', callback: Callback\<SteadyStandingStatus>): void;|api/@ohos.multimodalAwareness.deviceStatus.d.ts|
|新增API|NA|类名：deviceStatus；<br>API声明：function off(type: 'steadyStandingDetect', callback?: Callback\<SteadyStandingStatus>): void;<br>差异内容：function off(type: 'steadyStandingDetect', callback?: Callback\<SteadyStandingStatus>): void;|api/@ohos.multimodalAwareness.deviceStatus.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace metadataBinding<br>差异内容：declare namespace metadataBinding|api/@ohos.multimodalAwareness.metadataBinding.d.ts|
|新增API|NA|类名：metadataBinding；<br>API声明：function submitMetadata(metadata: string): void;<br>差异内容：function submitMetadata(metadata: string): void;|api/@ohos.multimodalAwareness.metadataBinding.d.ts|
|新增API|NA|类名：metadataBinding；<br>API声明：function on(type: 'operationSubmitMetadata', bundleName: string, callback: Callback\<number>): void;<br>差异内容：function on(type: 'operationSubmitMetadata', bundleName: string, callback: Callback\<number>): void;|api/@ohos.multimodalAwareness.metadataBinding.d.ts|
|新增API|NA|类名：metadataBinding；<br>API声明：function off(type: 'operationSubmitMetadata', bundleName: string, callback?: Callback\<number>): void;<br>差异内容：function off(type: 'operationSubmitMetadata', bundleName: string, callback?: Callback\<number>): void;|api/@ohos.multimodalAwareness.metadataBinding.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.multimodalAwareness.deviceStatus.d.ts<br>差异内容：MultimodalAwarenessKit|api/@ohos.multimodalAwareness.deviceStatus.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.multimodalAwareness.metadataBinding.d.ts<br>差异内容：MultimodalAwarenessKit|api/@ohos.multimodalAwareness.metadataBinding.d.ts|
