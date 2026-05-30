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
|新增API|NA|类名：global；<br>API声明：declare namespace motion<br>差异内容：declare namespace motion|api/@ohos.multimodalAwareness.motion.d.ts|
|新增API|NA|类名：motion；<br>API声明：export enum OperatingHandStatus<br>差异内容：export enum OperatingHandStatus|api/@ohos.multimodalAwareness.motion.d.ts|
|新增API|NA|类名：OperatingHandStatus；<br>API声明：UNKNOWN_STATUS = 0<br>差异内容：UNKNOWN_STATUS = 0|api/@ohos.multimodalAwareness.motion.d.ts|
|新增API|NA|类名：OperatingHandStatus；<br>API声明：LEFT_HAND_OPERATED = 1<br>差异内容：LEFT_HAND_OPERATED = 1|api/@ohos.multimodalAwareness.motion.d.ts|
|新增API|NA|类名：OperatingHandStatus；<br>API声明：RIGHT_HAND_OPERATED = 2<br>差异内容：RIGHT_HAND_OPERATED = 2|api/@ohos.multimodalAwareness.motion.d.ts|
|新增API|NA|类名：motion；<br>API声明：export enum HoldingHandStatus<br>差异内容：export enum HoldingHandStatus|api/@ohos.multimodalAwareness.motion.d.ts|
|新增API|NA|类名：HoldingHandStatus；<br>API声明：NOT_HELD = 0<br>差异内容：NOT_HELD = 0|api/@ohos.multimodalAwareness.motion.d.ts|
|新增API|NA|类名：HoldingHandStatus；<br>API声明：LEFT_HAND_HELD = 1<br>差异内容：LEFT_HAND_HELD = 1|api/@ohos.multimodalAwareness.motion.d.ts|
|新增API|NA|类名：HoldingHandStatus；<br>API声明：RIGHT_HAND_HELD = 2<br>差异内容：RIGHT_HAND_HELD = 2|api/@ohos.multimodalAwareness.motion.d.ts|
|新增API|NA|类名：HoldingHandStatus；<br>API声明：BOTH_HANDS_HELD = 3<br>差异内容：BOTH_HANDS_HELD = 3|api/@ohos.multimodalAwareness.motion.d.ts|
|新增API|NA|类名：HoldingHandStatus；<br>API声明：UNKNOWN_STATUS = 16<br>差异内容：UNKNOWN_STATUS = 16|api/@ohos.multimodalAwareness.motion.d.ts|
|新增API|NA|类名：motion；<br>API声明：function on(type: 'operatingHandChanged', callback: Callback\<OperatingHandStatus>): void;<br>差异内容：function on(type: 'operatingHandChanged', callback: Callback\<OperatingHandStatus>): void;|api/@ohos.multimodalAwareness.motion.d.ts|
|新增API|NA|类名：motion；<br>API声明：function off(type: 'operatingHandChanged', callback?: Callback\<OperatingHandStatus>): void;<br>差异内容：function off(type: 'operatingHandChanged', callback?: Callback\<OperatingHandStatus>): void;|api/@ohos.multimodalAwareness.motion.d.ts|
|新增API|NA|类名：motion；<br>API声明：function getRecentOperatingHandStatus(): OperatingHandStatus;<br>差异内容：function getRecentOperatingHandStatus(): OperatingHandStatus;|api/@ohos.multimodalAwareness.motion.d.ts|
|新增API|NA|类名：motion；<br>API声明：function on(type: 'holdingHandChanged', callback: Callback\<HoldingHandStatus>): void;<br>差异内容：function on(type: 'holdingHandChanged', callback: Callback\<HoldingHandStatus>): void;|api/@ohos.multimodalAwareness.motion.d.ts|
|新增API|NA|类名：motion；<br>API声明：function off(type: 'holdingHandChanged', callback?: Callback\<HoldingHandStatus>): void;<br>差异内容：function off(type: 'holdingHandChanged', callback?: Callback\<HoldingHandStatus>): void;|api/@ohos.multimodalAwareness.motion.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace onScreen<br>差异内容：declare namespace onScreen|api/@ohos.multimodalAwareness.onScreen.d.ts|
|新增API|NA|类名：onScreen；<br>API声明：export enum Scenario<br>差异内容：export enum Scenario|api/@ohos.multimodalAwareness.onScreen.d.ts|
|新增API|NA|类名：onScreen；<br>API声明：export enum EventType<br>差异内容：export enum EventType|api/@ohos.multimodalAwareness.onScreen.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace userStatus<br>差异内容：declare namespace userStatus|api/@ohos.multimodalAwareness.userStatus.d.ts|
|新增API|NA|类名：userStatus；<br>API声明：export interface UserClassification<br>差异内容：export interface UserClassification|api/@ohos.multimodalAwareness.userStatus.d.ts|
|新增API|NA|类名：UserClassification；<br>API声明：ageGroup?: UserAgeGroup;<br>差异内容：ageGroup?: UserAgeGroup;|api/@ohos.multimodalAwareness.userStatus.d.ts|
|新增API|NA|类名：UserClassification；<br>API声明：confidence?: float;<br>差异内容：confidence?: float;|api/@ohos.multimodalAwareness.userStatus.d.ts|
|新增API|NA|类名：userStatus；<br>API声明：export enum UserAgeGroup<br>差异内容：export enum UserAgeGroup|api/@ohos.multimodalAwareness.userStatus.d.ts|
|新增API|NA|类名：UserAgeGroup；<br>API声明：OTHERS = 0<br>差异内容：OTHERS = 0|api/@ohos.multimodalAwareness.userStatus.d.ts|
|新增API|NA|类名：UserAgeGroup；<br>API声明：CHILD = 1<br>差异内容：CHILD = 1|api/@ohos.multimodalAwareness.userStatus.d.ts|
|新增API|NA|类名：userStatus；<br>API声明：function on(type: 'userAgeGroupDetected', callback: Callback\<UserClassification>): void;<br>差异内容：function on(type: 'userAgeGroupDetected', callback: Callback\<UserClassification>): void;|api/@ohos.multimodalAwareness.userStatus.d.ts|
|新增API|NA|类名：userStatus；<br>API声明：function off(type: 'userAgeGroupDetected', callback?: Callback\<UserClassification>): void;<br>差异内容：function off(type: 'userAgeGroupDetected', callback?: Callback\<UserClassification>): void;|api/@ohos.multimodalAwareness.userStatus.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.multimodalAwareness.deviceStatus.d.ts<br>差异内容：MultimodalAwarenessKit|api/@ohos.multimodalAwareness.deviceStatus.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.multimodalAwareness.metadataBinding.d.ts<br>差异内容：MultimodalAwarenessKit|api/@ohos.multimodalAwareness.metadataBinding.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.multimodalAwareness.motion.d.ts<br>差异内容：MultimodalAwarenessKit|api/@ohos.multimodalAwareness.motion.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.multimodalAwareness.onScreen.d.ts<br>差异内容：MultimodalAwarenessKit|api/@ohos.multimodalAwareness.onScreen.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.multimodalAwareness.userStatus.d.ts<br>差异内容：MultimodalAwarenessKit|api/@ohos.multimodalAwareness.userStatus.d.ts|
