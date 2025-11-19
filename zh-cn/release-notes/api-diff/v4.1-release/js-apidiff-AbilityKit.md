| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace ability<br>差异内容：declare namespace ability|api/@ohos.ability.ability.d.ts|
|新增API|NA|类名：ability；<br>API声明：export type DataAbilityHelper = _DataAbilityHelper;<br>差异内容：export type DataAbilityHelper = _DataAbilityHelper;|api/@ohos.ability.ability.d.ts|
|新增API|NA|类名：ability；<br>API声明：export type PacMap = _PacMap;<br>差异内容：export type PacMap = _PacMap;|api/@ohos.ability.ability.d.ts|
|新增API|NA|类名：ability；<br>API声明：export type DataAbilityOperation = _DataAbilityOperation;<br>差异内容：export type DataAbilityOperation = _DataAbilityOperation;|api/@ohos.ability.ability.d.ts|
|新增API|NA|类名：ability；<br>API声明：export type DataAbilityResult = _DataAbilityResult;<br>差异内容：export type DataAbilityResult = _DataAbilityResult;|api/@ohos.ability.ability.d.ts|
|新增API|NA|类名：ability；<br>API声明：export type AbilityResult = _AbilityResult;<br>差异内容：export type AbilityResult = _AbilityResult;|api/@ohos.ability.ability.d.ts|
|新增API|NA|类名：ability；<br>API声明：export type ConnectOptions = _ConnectOptions;<br>差异内容：export type ConnectOptions = _ConnectOptions;|api/@ohos.ability.ability.d.ts|
|新增API|NA|类名：ability；<br>API声明：export type StartAbilityParameter = _StartAbilityParameter;<br>差异内容：export type StartAbilityParameter = _StartAbilityParameter;|api/@ohos.ability.ability.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace dataUriUtils<br>差异内容：declare namespace dataUriUtils|api/@ohos.ability.dataUriUtils.d.ts|
|新增API|NA|类名：dataUriUtils；<br>API声明：function getId(uri: string): number;<br>差异内容：function getId(uri: string): number;|api/@ohos.ability.dataUriUtils.d.ts|
|新增API|NA|类名：dataUriUtils；<br>API声明：function attachId(uri: string, id: number): string;<br>差异内容：function attachId(uri: string, id: number): string;|api/@ohos.ability.dataUriUtils.d.ts|
|新增API|NA|类名：dataUriUtils；<br>API声明：function deleteId(uri: string): string;<br>差异内容：function deleteId(uri: string): string;|api/@ohos.ability.dataUriUtils.d.ts|
|新增API|NA|类名：dataUriUtils；<br>API声明：function updateId(uri: string, id: number): string;<br>差异内容：function updateId(uri: string, id: number): string;|api/@ohos.ability.dataUriUtils.d.ts|
|新增API|NA|类名：global；<br>API声明：export enum ErrorCode<br>差异内容：export enum ErrorCode|api/@ohos.ability.errorCode.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：PERMISSION_DENY = -3<br>差异内容：PERMISSION_DENY = -3|api/@ohos.ability.errorCode.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：ABILITY_NOT_FOUND = -2<br>差异内容：ABILITY_NOT_FOUND = -2|api/@ohos.ability.errorCode.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：INVALID_PARAMETER = -1<br>差异内容：INVALID_PARAMETER = -1|api/@ohos.ability.errorCode.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：NO_ERROR = 0<br>差异内容：NO_ERROR = 0|api/@ohos.ability.errorCode.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace featureAbility<br>差异内容：declare namespace featureAbility|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function getWant(callback: AsyncCallback\<Want>): void;<br>差异内容：function getWant(callback: AsyncCallback\<Want>): void;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function getWant(): Promise\<Want>;<br>差异内容：function getWant(): Promise\<Want>;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function startAbility(parameter: StartAbilityParameter, callback: AsyncCallback\<number>): void;<br>差异内容：function startAbility(parameter: StartAbilityParameter, callback: AsyncCallback\<number>): void;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function startAbility(parameter: StartAbilityParameter): Promise\<number>;<br>差异内容：function startAbility(parameter: StartAbilityParameter): Promise\<number>;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function getContext(): Context;<br>差异内容：function getContext(): Context;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function startAbilityForResult(parameter: StartAbilityParameter, callback: AsyncCallback\<AbilityResult>): void;<br>差异内容：function startAbilityForResult(parameter: StartAbilityParameter, callback: AsyncCallback\<AbilityResult>): void;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function startAbilityForResult(parameter: StartAbilityParameter): Promise\<AbilityResult>;<br>差异内容：function startAbilityForResult(parameter: StartAbilityParameter): Promise\<AbilityResult>;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function terminateSelfWithResult(parameter: AbilityResult, callback: AsyncCallback\<void>): void;<br>差异内容：function terminateSelfWithResult(parameter: AbilityResult, callback: AsyncCallback\<void>): void;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function terminateSelfWithResult(parameter: AbilityResult): Promise\<void>;<br>差异内容：function terminateSelfWithResult(parameter: AbilityResult): Promise\<void>;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function terminateSelf(callback: AsyncCallback\<void>): void;<br>差异内容：function terminateSelf(callback: AsyncCallback\<void>): void;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function terminateSelf(): Promise\<void>;<br>差异内容：function terminateSelf(): Promise\<void>;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function acquireDataAbilityHelper(uri: string): DataAbilityHelper;<br>差异内容：function acquireDataAbilityHelper(uri: string): DataAbilityHelper;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function hasWindowFocus(callback: AsyncCallback\<boolean>): void;<br>差异内容：function hasWindowFocus(callback: AsyncCallback\<boolean>): void;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function hasWindowFocus(): Promise\<boolean>;<br>差异内容：function hasWindowFocus(): Promise\<boolean>;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function connectAbility(request: Want, options: ConnectOptions): number;<br>差异内容：function connectAbility(request: Want, options: ConnectOptions): number;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function disconnectAbility(connection: number, callback: AsyncCallback\<void>): void;<br>差异内容：function disconnectAbility(connection: number, callback: AsyncCallback\<void>): void;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function disconnectAbility(connection: number): Promise\<void>;<br>差异内容：function disconnectAbility(connection: number): Promise\<void>;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function getWindow(callback: AsyncCallback\<window.Window>): void;<br>差异内容：function getWindow(callback: AsyncCallback\<window.Window>): void;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：function getWindow(): Promise\<window.Window>;<br>差异内容：function getWindow(): Promise\<window.Window>;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：export enum AbilityWindowConfiguration<br>差异内容：export enum AbilityWindowConfiguration|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：AbilityWindowConfiguration；<br>API声明：WINDOW_MODE_UNDEFINED = 0<br>差异内容：WINDOW_MODE_UNDEFINED = 0|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：AbilityWindowConfiguration；<br>API声明：WINDOW_MODE_FULLSCREEN = 1<br>差异内容：WINDOW_MODE_FULLSCREEN = 1|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：AbilityWindowConfiguration；<br>API声明：WINDOW_MODE_SPLIT_PRIMARY = 100<br>差异内容：WINDOW_MODE_SPLIT_PRIMARY = 100|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：AbilityWindowConfiguration；<br>API声明：WINDOW_MODE_SPLIT_SECONDARY = 101<br>差异内容：WINDOW_MODE_SPLIT_SECONDARY = 101|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：AbilityWindowConfiguration；<br>API声明：WINDOW_MODE_FLOATING = 102<br>差异内容：WINDOW_MODE_FLOATING = 102|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：export enum AbilityStartSetting<br>差异内容：export enum AbilityStartSetting|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：AbilityStartSetting；<br>API声明：BOUNDS_KEY = 'abilityBounds'<br>差异内容：BOUNDS_KEY = 'abilityBounds'|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：AbilityStartSetting；<br>API声明：WINDOW_MODE_KEY = 'windowMode'<br>差异内容：WINDOW_MODE_KEY = 'windowMode'|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：AbilityStartSetting；<br>API声明：DISPLAY_ID_KEY = 'displayId'<br>差异内容：DISPLAY_ID_KEY = 'displayId'|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：export enum ErrorCode<br>差异内容：export enum ErrorCode|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：NO_ERROR = 0<br>差异内容：NO_ERROR = 0|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：INVALID_PARAMETER = -1<br>差异内容：INVALID_PARAMETER = -1|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：ABILITY_NOT_FOUND = -2<br>差异内容：ABILITY_NOT_FOUND = -2|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：PERMISSION_DENY = -3<br>差异内容：PERMISSION_DENY = -3|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：export enum DataAbilityOperationType<br>差异内容：export enum DataAbilityOperationType|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：DataAbilityOperationType；<br>API声明：TYPE_INSERT = 1<br>差异内容：TYPE_INSERT = 1|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：DataAbilityOperationType；<br>API声明：TYPE_UPDATE = 2<br>差异内容：TYPE_UPDATE = 2|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：DataAbilityOperationType；<br>API声明：TYPE_DELETE = 3<br>差异内容：TYPE_DELETE = 3|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：DataAbilityOperationType；<br>API声明：TYPE_ASSERT = 4<br>差异内容：TYPE_ASSERT = 4|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：export type Context = _Context;<br>差异内容：export type Context = _Context;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：export type AppVersionInfo = _AppVersionInfo;<br>差异内容：export type AppVersionInfo = _AppVersionInfo;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：featureAbility；<br>API声明：export type ProcessInfo = _ProcessInfo;<br>差异内容：export type ProcessInfo = _ProcessInfo;|api/@ohos.ability.featureAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace particleAbility<br>差异内容：declare namespace particleAbility|api/@ohos.ability.particleAbility.d.ts|
|新增API|NA|类名：particleAbility；<br>API声明：function startAbility(parameter: StartAbilityParameter, callback: AsyncCallback\<void>): void;<br>差异内容：function startAbility(parameter: StartAbilityParameter, callback: AsyncCallback\<void>): void;|api/@ohos.ability.particleAbility.d.ts|
|新增API|NA|类名：particleAbility；<br>API声明：function startAbility(parameter: StartAbilityParameter): Promise\<void>;<br>差异内容：function startAbility(parameter: StartAbilityParameter): Promise\<void>;|api/@ohos.ability.particleAbility.d.ts|
|新增API|NA|类名：particleAbility；<br>API声明：function terminateSelf(callback: AsyncCallback\<void>): void;<br>差异内容：function terminateSelf(callback: AsyncCallback\<void>): void;|api/@ohos.ability.particleAbility.d.ts|
|新增API|NA|类名：particleAbility；<br>API声明：function terminateSelf(): Promise\<void>;<br>差异内容：function terminateSelf(): Promise\<void>;|api/@ohos.ability.particleAbility.d.ts|
|新增API|NA|类名：particleAbility；<br>API声明：function acquireDataAbilityHelper(uri: string): DataAbilityHelper;<br>差异内容：function acquireDataAbilityHelper(uri: string): DataAbilityHelper;|api/@ohos.ability.particleAbility.d.ts|
|新增API|NA|类名：particleAbility；<br>API声明：function startBackgroundRunning(id: number, request: NotificationRequest, callback: AsyncCallback\<void>): void;<br>差异内容：function startBackgroundRunning(id: number, request: NotificationRequest, callback: AsyncCallback\<void>): void;|api/@ohos.ability.particleAbility.d.ts|
|新增API|NA|类名：particleAbility；<br>API声明：function startBackgroundRunning(id: number, request: NotificationRequest): Promise\<void>;<br>差异内容：function startBackgroundRunning(id: number, request: NotificationRequest): Promise\<void>;|api/@ohos.ability.particleAbility.d.ts|
|新增API|NA|类名：particleAbility；<br>API声明：function cancelBackgroundRunning(callback: AsyncCallback\<void>): void;<br>差异内容：function cancelBackgroundRunning(callback: AsyncCallback\<void>): void;|api/@ohos.ability.particleAbility.d.ts|
|新增API|NA|类名：particleAbility；<br>API声明：function cancelBackgroundRunning(): Promise\<void>;<br>差异内容：function cancelBackgroundRunning(): Promise\<void>;|api/@ohos.ability.particleAbility.d.ts|
|新增API|NA|类名：particleAbility；<br>API声明：function connectAbility(request: Want, options: ConnectOptions): number;<br>差异内容：function connectAbility(request: Want, options: ConnectOptions): number;|api/@ohos.ability.particleAbility.d.ts|
|新增API|NA|类名：particleAbility；<br>API声明：function disconnectAbility(connection: number, callback: AsyncCallback\<void>): void;<br>差异内容：function disconnectAbility(connection: number, callback: AsyncCallback\<void>): void;|api/@ohos.ability.particleAbility.d.ts|
|新增API|NA|类名：particleAbility；<br>API声明：function disconnectAbility(connection: number): Promise\<void>;<br>差异内容：function disconnectAbility(connection: number): Promise\<void>;|api/@ohos.ability.particleAbility.d.ts|
|新增API|NA|类名：particleAbility；<br>API声明：export enum ErrorCode<br>差异内容：export enum ErrorCode|api/@ohos.ability.particleAbility.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：INVALID_PARAMETER = -1<br>差异内容：INVALID_PARAMETER = -1|api/@ohos.ability.particleAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace wantConstant<br>差异内容：declare namespace wantConstant|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：wantConstant；<br>API声明：export enum Action<br>差异内容：export enum Action|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_HOME = 'ohos.want.action.home'<br>差异内容：ACTION_HOME = 'ohos.want.action.home'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_DIAL = 'ohos.want.action.dial'<br>差异内容：ACTION_DIAL = 'ohos.want.action.dial'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_SEARCH = 'ohos.want.action.search'<br>差异内容：ACTION_SEARCH = 'ohos.want.action.search'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_WIRELESS_SETTINGS = 'ohos.settings.wireless'<br>差异内容：ACTION_WIRELESS_SETTINGS = 'ohos.settings.wireless'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_MANAGE_APPLICATIONS_SETTINGS = 'ohos.settings.manage.applications'<br>差异内容：ACTION_MANAGE_APPLICATIONS_SETTINGS = 'ohos.settings.manage.applications'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_APPLICATION_DETAILS_SETTINGS = 'ohos.settings.application.details'<br>差异内容：ACTION_APPLICATION_DETAILS_SETTINGS = 'ohos.settings.application.details'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_SET_ALARM = 'ohos.want.action.setAlarm'<br>差异内容：ACTION_SET_ALARM = 'ohos.want.action.setAlarm'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_SHOW_ALARMS = 'ohos.want.action.showAlarms'<br>差异内容：ACTION_SHOW_ALARMS = 'ohos.want.action.showAlarms'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_SNOOZE_ALARM = 'ohos.want.action.snoozeAlarm'<br>差异内容：ACTION_SNOOZE_ALARM = 'ohos.want.action.snoozeAlarm'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_DISMISS_ALARM = 'ohos.want.action.dismissAlarm'<br>差异内容：ACTION_DISMISS_ALARM = 'ohos.want.action.dismissAlarm'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_DISMISS_TIMER = 'ohos.want.action.dismissTimer'<br>差异内容：ACTION_DISMISS_TIMER = 'ohos.want.action.dismissTimer'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_SEND_SMS = 'ohos.want.action.sendSms'<br>差异内容：ACTION_SEND_SMS = 'ohos.want.action.sendSms'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_CHOOSE = 'ohos.want.action.choose'<br>差异内容：ACTION_CHOOSE = 'ohos.want.action.choose'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_IMAGE_CAPTURE = 'ohos.want.action.imageCapture'<br>差异内容：ACTION_IMAGE_CAPTURE = 'ohos.want.action.imageCapture'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_VIDEO_CAPTURE = 'ohos.want.action.videoCapture'<br>差异内容：ACTION_VIDEO_CAPTURE = 'ohos.want.action.videoCapture'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_SELECT = 'ohos.want.action.select'<br>差异内容：ACTION_SELECT = 'ohos.want.action.select'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_SEND_DATA = 'ohos.want.action.sendData'<br>差异内容：ACTION_SEND_DATA = 'ohos.want.action.sendData'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_SEND_MULTIPLE_DATA = 'ohos.want.action.sendMultipleData'<br>差异内容：ACTION_SEND_MULTIPLE_DATA = 'ohos.want.action.sendMultipleData'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_SCAN_MEDIA_FILE = 'ohos.want.action.scanMediaFile'<br>差异内容：ACTION_SCAN_MEDIA_FILE = 'ohos.want.action.scanMediaFile'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_VIEW_DATA = 'ohos.want.action.viewData'<br>差异内容：ACTION_VIEW_DATA = 'ohos.want.action.viewData'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_EDIT_DATA = 'ohos.want.action.editData'<br>差异内容：ACTION_EDIT_DATA = 'ohos.want.action.editData'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：INTENT_PARAMS_INTENT = 'ability.want.params.INTENT'<br>差异内容：INTENT_PARAMS_INTENT = 'ability.want.params.INTENT'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：INTENT_PARAMS_TITLE = 'ability.want.params.TITLE'<br>差异内容：INTENT_PARAMS_TITLE = 'ability.want.params.TITLE'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_FILE_SELECT = 'ohos.action.fileSelect'<br>差异内容：ACTION_FILE_SELECT = 'ohos.action.fileSelect'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：PARAMS_STREAM = 'ability.params.stream'<br>差异内容：PARAMS_STREAM = 'ability.params.stream'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Action；<br>API声明：ACTION_APP_ACCOUNT_OAUTH = 'ohos.account.appAccount.action.oauth'<br>差异内容：ACTION_APP_ACCOUNT_OAUTH = 'ohos.account.appAccount.action.oauth'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：wantConstant；<br>API声明：export enum Entity<br>差异内容：export enum Entity|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Entity；<br>API声明：ENTITY_DEFAULT = 'entity.system.default'<br>差异内容：ENTITY_DEFAULT = 'entity.system.default'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Entity；<br>API声明：ENTITY_HOME = 'entity.system.home'<br>差异内容：ENTITY_HOME = 'entity.system.home'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Entity；<br>API声明：ENTITY_VOICE = 'entity.system.voice'<br>差异内容：ENTITY_VOICE = 'entity.system.voice'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Entity；<br>API声明：ENTITY_BROWSABLE = 'entity.system.browsable'<br>差异内容：ENTITY_BROWSABLE = 'entity.system.browsable'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Entity；<br>API声明：ENTITY_VIDEO = 'entity.system.video'<br>差异内容：ENTITY_VIDEO = 'entity.system.video'|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：wantConstant；<br>API声明：export enum Flags<br>差异内容：export enum Flags|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Flags；<br>API声明：FLAG_AUTH_READ_URI_PERMISSION = 0x00000001<br>差异内容：FLAG_AUTH_READ_URI_PERMISSION = 0x00000001|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Flags；<br>API声明：FLAG_AUTH_WRITE_URI_PERMISSION = 0x00000002<br>差异内容：FLAG_AUTH_WRITE_URI_PERMISSION = 0x00000002|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Flags；<br>API声明：FLAG_ABILITY_FORWARD_RESULT = 0x00000004<br>差异内容：FLAG_ABILITY_FORWARD_RESULT = 0x00000004|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Flags；<br>API声明：FLAG_ABILITY_CONTINUATION = 0x00000008<br>差异内容：FLAG_ABILITY_CONTINUATION = 0x00000008|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Flags；<br>API声明：FLAG_NOT_OHOS_COMPONENT = 0x00000010<br>差异内容：FLAG_NOT_OHOS_COMPONENT = 0x00000010|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Flags；<br>API声明：FLAG_ABILITY_FORM_ENABLED = 0x00000020<br>差异内容：FLAG_ABILITY_FORM_ENABLED = 0x00000020|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Flags；<br>API声明：FLAG_ABILITYSLICE_MULTI_DEVICE = 0x00000100<br>差异内容：FLAG_ABILITYSLICE_MULTI_DEVICE = 0x00000100|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Flags；<br>API声明：FLAG_START_FOREGROUND_ABILITY = 0x00000200<br>差异内容：FLAG_START_FOREGROUND_ABILITY = 0x00000200|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Flags；<br>API声明：FLAG_INSTALL_ON_DEMAND = 0x00000800<br>差异内容：FLAG_INSTALL_ON_DEMAND = 0x00000800|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Flags；<br>API声明：FLAG_INSTALL_WITH_BACKGROUND_MODE = 0x80000000<br>差异内容：FLAG_INSTALL_WITH_BACKGROUND_MODE = 0x80000000|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Flags；<br>API声明：FLAG_ABILITY_CLEAR_MISSION = 0x00008000<br>差异内容：FLAG_ABILITY_CLEAR_MISSION = 0x00008000|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Flags；<br>API声明：FLAG_ABILITY_NEW_MISSION = 0x10000000<br>差异内容：FLAG_ABILITY_NEW_MISSION = 0x10000000|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：Flags；<br>API声明：FLAG_ABILITY_MISSION_TOP = 0x20000000<br>差异内容：FLAG_ABILITY_MISSION_TOP = 0x20000000|api/@ohos.ability.wantConstant.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace abilityAccessCtrl<br>差异内容：declare namespace abilityAccessCtrl|api/@ohos.abilityAccessCtrl.d.ts|
|新增API|NA|类名：abilityAccessCtrl；<br>API声明：function createAtManager(): AtManager;<br>差异内容：function createAtManager(): AtManager;|api/@ohos.abilityAccessCtrl.d.ts|
|新增API|NA|类名：abilityAccessCtrl；<br>API声明：interface AtManager<br>差异内容：interface AtManager|api/@ohos.abilityAccessCtrl.d.ts|
|新增API|NA|类名：AtManager；<br>API声明：verifyAccessToken(tokenID: number, permissionName: Permissions): Promise\<GrantStatus>;<br>差异内容：verifyAccessToken(tokenID: number, permissionName: Permissions): Promise\<GrantStatus>;|api/@ohos.abilityAccessCtrl.d.ts|
|新增API|NA|类名：AtManager；<br>API声明：verifyAccessToken(tokenID: number, permissionName: string): Promise\<GrantStatus>;<br>差异内容：verifyAccessToken(tokenID: number, permissionName: string): Promise\<GrantStatus>;|api/@ohos.abilityAccessCtrl.d.ts|
|新增API|NA|类名：AtManager；<br>API声明：verifyAccessTokenSync(tokenID: number, permissionName: Permissions): GrantStatus;<br>差异内容：verifyAccessTokenSync(tokenID: number, permissionName: Permissions): GrantStatus;|api/@ohos.abilityAccessCtrl.d.ts|
|新增API|NA|类名：AtManager；<br>API声明：checkAccessToken(tokenID: number, permissionName: Permissions): Promise\<GrantStatus>;<br>差异内容：checkAccessToken(tokenID: number, permissionName: Permissions): Promise\<GrantStatus>;|api/@ohos.abilityAccessCtrl.d.ts|
|新增API|NA|类名：AtManager；<br>API声明：checkAccessTokenSync(tokenID: number, permissionName: Permissions): GrantStatus;<br>差异内容：checkAccessTokenSync(tokenID: number, permissionName: Permissions): GrantStatus;|api/@ohos.abilityAccessCtrl.d.ts|
|新增API|NA|类名：AtManager；<br>API声明：requestPermissionsFromUser(context: Context, permissionList: Array\<Permissions>, requestCallback: AsyncCallback\<PermissionRequestResult>): void;<br>差异内容：requestPermissionsFromUser(context: Context, permissionList: Array\<Permissions>, requestCallback: AsyncCallback\<PermissionRequestResult>): void;|api/@ohos.abilityAccessCtrl.d.ts|
|新增API|NA|类名：AtManager；<br>API声明：requestPermissionsFromUser(context: Context, permissionList: Array\<Permissions>): Promise\<PermissionRequestResult>;<br>差异内容：requestPermissionsFromUser(context: Context, permissionList: Array\<Permissions>): Promise\<PermissionRequestResult>;|api/@ohos.abilityAccessCtrl.d.ts|
|新增API|NA|类名：abilityAccessCtrl；<br>API声明：export enum GrantStatus<br>差异内容：export enum GrantStatus|api/@ohos.abilityAccessCtrl.d.ts|
|新增API|NA|类名：GrantStatus；<br>API声明：PERMISSION_DENIED = -1<br>差异内容：PERMISSION_DENIED = -1|api/@ohos.abilityAccessCtrl.d.ts|
|新增API|NA|类名：GrantStatus；<br>API声明：PERMISSION_GRANTED = 0<br>差异内容：PERMISSION_GRANTED = 0|api/@ohos.abilityAccessCtrl.d.ts|
|新增API|NA|类名：global；<br>API声明：export type PermissionRequestResult = _PermissionRequestResult;<br>差异内容：export type PermissionRequestResult = _PermissionRequestResult;|api/@ohos.abilityAccessCtrl.d.ts|
|新增API|NA|类名：global；<br>API声明：export type Context = _Context;<br>差异内容：export type Context = _Context;|api/@ohos.abilityAccessCtrl.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class Ability<br>差异内容：export default class Ability|api/@ohos.app.ability.Ability.d.ts|
|新增API|NA|类名：Ability；<br>API声明：onConfigurationUpdate(newConfig: Configuration): void;<br>差异内容：onConfigurationUpdate(newConfig: Configuration): void;|api/@ohos.app.ability.Ability.d.ts|
|新增API|NA|类名：Ability；<br>API声明：onMemoryLevel(level: AbilityConstant.MemoryLevel): void;<br>差异内容：onMemoryLevel(level: AbilityConstant.MemoryLevel): void;|api/@ohos.app.ability.Ability.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace AbilityConstant<br>差异内容：declare namespace AbilityConstant|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：AbilityConstant；<br>API声明：export interface LaunchParam<br>差异内容：export interface LaunchParam|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LaunchParam；<br>API声明：launchReason: LaunchReason;<br>差异内容：launchReason: LaunchReason;|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LaunchParam；<br>API声明：lastExitReason: LastExitReason;<br>差异内容：lastExitReason: LastExitReason;|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：AbilityConstant；<br>API声明：export enum LaunchReason<br>差异内容：export enum LaunchReason|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LaunchReason；<br>API声明：UNKNOWN = 0<br>差异内容：UNKNOWN = 0|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LaunchReason；<br>API声明：START_ABILITY = 1<br>差异内容：START_ABILITY = 1|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LaunchReason；<br>API声明：CALL = 2<br>差异内容：CALL = 2|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LaunchReason；<br>API声明：CONTINUATION = 3<br>差异内容：CONTINUATION = 3|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LaunchReason；<br>API声明：APP_RECOVERY = 4<br>差异内容：APP_RECOVERY = 4|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LaunchReason；<br>API声明：SHARE = 5<br>差异内容：SHARE = 5|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LaunchReason；<br>API声明：AUTO_STARTUP = 8<br>差异内容：AUTO_STARTUP = 8|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LaunchReason；<br>API声明：INSIGHT_INTENT = 9<br>差异内容：INSIGHT_INTENT = 9|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：AbilityConstant；<br>API声明：export enum LastExitReason<br>差异内容：export enum LastExitReason|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LastExitReason；<br>API声明：UNKNOWN = 0<br>差异内容：UNKNOWN = 0|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LastExitReason；<br>API声明：ABILITY_NOT_RESPONDING = 1<br>差异内容：ABILITY_NOT_RESPONDING = 1|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LastExitReason；<br>API声明：NORMAL = 2<br>差异内容：NORMAL = 2|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LastExitReason；<br>API声明：CPP_CRASH = 3<br>差异内容：CPP_CRASH = 3|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LastExitReason；<br>API声明：JS_ERROR = 4<br>差异内容：JS_ERROR = 4|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LastExitReason；<br>API声明：APP_FREEZE = 5<br>差异内容：APP_FREEZE = 5|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LastExitReason；<br>API声明：PERFORMANCE_CONTROL = 6<br>差异内容：PERFORMANCE_CONTROL = 6|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LastExitReason；<br>API声明：RESOURCE_CONTROL = 7<br>差异内容：RESOURCE_CONTROL = 7|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：LastExitReason；<br>API声明：UPGRADE = 8<br>差异内容：UPGRADE = 8|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：AbilityConstant；<br>API声明：export enum OnContinueResult<br>差异内容：export enum OnContinueResult|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：OnContinueResult；<br>API声明：AGREE = 0<br>差异内容：AGREE = 0|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：OnContinueResult；<br>API声明：REJECT = 1<br>差异内容：REJECT = 1|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：OnContinueResult；<br>API声明：MISMATCH = 2<br>差异内容：MISMATCH = 2|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：AbilityConstant；<br>API声明：export enum MemoryLevel<br>差异内容：export enum MemoryLevel|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：MemoryLevel；<br>API声明：MEMORY_LEVEL_MODERATE = 0<br>差异内容：MEMORY_LEVEL_MODERATE = 0|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：MemoryLevel；<br>API声明：MEMORY_LEVEL_LOW = 1<br>差异内容：MEMORY_LEVEL_LOW = 1|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：MemoryLevel；<br>API声明：MEMORY_LEVEL_CRITICAL = 2<br>差异内容：MEMORY_LEVEL_CRITICAL = 2|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：AbilityConstant；<br>API声明：export enum OnSaveResult<br>差异内容：export enum OnSaveResult|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：OnSaveResult；<br>API声明：ALL_AGREE = 0<br>差异内容：ALL_AGREE = 0|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：OnSaveResult；<br>API声明：CONTINUATION_REJECT = 1<br>差异内容：CONTINUATION_REJECT = 1|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：OnSaveResult；<br>API声明：CONTINUATION_MISMATCH = 2<br>差异内容：CONTINUATION_MISMATCH = 2|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：OnSaveResult；<br>API声明：RECOVERY_AGREE = 3<br>差异内容：RECOVERY_AGREE = 3|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：OnSaveResult；<br>API声明：RECOVERY_REJECT = 4<br>差异内容：RECOVERY_REJECT = 4|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：OnSaveResult；<br>API声明：ALL_REJECT<br>差异内容：ALL_REJECT|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：AbilityConstant；<br>API声明：export enum StateType<br>差异内容：export enum StateType|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：StateType；<br>API声明：CONTINUATION = 0<br>差异内容：CONTINUATION = 0|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：StateType；<br>API声明：APP_RECOVERY = 1<br>差异内容：APP_RECOVERY = 1|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：AbilityConstant；<br>API声明：export enum ContinueState<br>差异内容：export enum ContinueState|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：ContinueState；<br>API声明：ACTIVE = 0<br>差异内容：ACTIVE = 0|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：ContinueState；<br>API声明：INACTIVE = 1<br>差异内容：INACTIVE = 1|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class AbilityLifecycleCallback<br>差异内容：export default class AbilityLifecycleCallback|api/@ohos.app.ability.AbilityLifecycleCallback.d.ts|
|新增API|NA|类名：AbilityLifecycleCallback；<br>API声明：onAbilityCreate(ability: UIAbility): void;<br>差异内容：onAbilityCreate(ability: UIAbility): void;|api/@ohos.app.ability.AbilityLifecycleCallback.d.ts|
|新增API|NA|类名：AbilityLifecycleCallback；<br>API声明：onWindowStageCreate(ability: UIAbility, windowStage: window.WindowStage): void;<br>差异内容：onWindowStageCreate(ability: UIAbility, windowStage: window.WindowStage): void;|api/@ohos.app.ability.AbilityLifecycleCallback.d.ts|
|新增API|NA|类名：AbilityLifecycleCallback；<br>API声明：onWindowStageActive(ability: UIAbility, windowStage: window.WindowStage): void;<br>差异内容：onWindowStageActive(ability: UIAbility, windowStage: window.WindowStage): void;|api/@ohos.app.ability.AbilityLifecycleCallback.d.ts|
|新增API|NA|类名：AbilityLifecycleCallback；<br>API声明：onWindowStageInactive(ability: UIAbility, windowStage: window.WindowStage): void;<br>差异内容：onWindowStageInactive(ability: UIAbility, windowStage: window.WindowStage): void;|api/@ohos.app.ability.AbilityLifecycleCallback.d.ts|
|新增API|NA|类名：AbilityLifecycleCallback；<br>API声明：onWindowStageDestroy(ability: UIAbility, windowStage: window.WindowStage): void;<br>差异内容：onWindowStageDestroy(ability: UIAbility, windowStage: window.WindowStage): void;|api/@ohos.app.ability.AbilityLifecycleCallback.d.ts|
|新增API|NA|类名：AbilityLifecycleCallback；<br>API声明：onAbilityDestroy(ability: UIAbility): void;<br>差异内容：onAbilityDestroy(ability: UIAbility): void;|api/@ohos.app.ability.AbilityLifecycleCallback.d.ts|
|新增API|NA|类名：AbilityLifecycleCallback；<br>API声明：onAbilityForeground(ability: UIAbility): void;<br>差异内容：onAbilityForeground(ability: UIAbility): void;|api/@ohos.app.ability.AbilityLifecycleCallback.d.ts|
|新增API|NA|类名：AbilityLifecycleCallback；<br>API声明：onAbilityBackground(ability: UIAbility): void;<br>差异内容：onAbilityBackground(ability: UIAbility): void;|api/@ohos.app.ability.AbilityLifecycleCallback.d.ts|
|新增API|NA|类名：AbilityLifecycleCallback；<br>API声明：onAbilityContinue(ability: UIAbility): void;<br>差异内容：onAbilityContinue(ability: UIAbility): void;|api/@ohos.app.ability.AbilityLifecycleCallback.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class AbilityStage<br>差异内容：export default class AbilityStage|api/@ohos.app.ability.AbilityStage.d.ts|
|新增API|NA|类名：AbilityStage；<br>API声明：context: AbilityStageContext;<br>差异内容：context: AbilityStageContext;|api/@ohos.app.ability.AbilityStage.d.ts|
|新增API|NA|类名：AbilityStage；<br>API声明：onCreate(): void;<br>差异内容：onCreate(): void;|api/@ohos.app.ability.AbilityStage.d.ts|
|新增API|NA|类名：AbilityStage；<br>API声明：onAcceptWant(want: Want): string;<br>差异内容：onAcceptWant(want: Want): string;|api/@ohos.app.ability.AbilityStage.d.ts|
|新增API|NA|类名：AbilityStage；<br>API声明：onNewProcessRequest(want: Want): string;<br>差异内容：onNewProcessRequest(want: Want): string;|api/@ohos.app.ability.AbilityStage.d.ts|
|新增API|NA|类名：AbilityStage；<br>API声明：onConfigurationUpdate(newConfig: Configuration): void;<br>差异内容：onConfigurationUpdate(newConfig: Configuration): void;|api/@ohos.app.ability.AbilityStage.d.ts|
|新增API|NA|类名：AbilityStage；<br>API声明：onMemoryLevel(level: AbilityConstant.MemoryLevel): void;<br>差异内容：onMemoryLevel(level: AbilityConstant.MemoryLevel): void;|api/@ohos.app.ability.AbilityStage.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class ActionExtensionAbility<br>差异内容：export default class ActionExtensionAbility|api/@ohos.app.ability.ActionExtensionAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class ApplicationStateChangeCallback<br>差异内容：export default class ApplicationStateChangeCallback|api/@ohos.app.ability.ApplicationStateChangeCallback.d.ts|
|新增API|NA|类名：ApplicationStateChangeCallback；<br>API声明：onApplicationForeground(): void;<br>差异内容：onApplicationForeground(): void;|api/@ohos.app.ability.ApplicationStateChangeCallback.d.ts|
|新增API|NA|类名：ApplicationStateChangeCallback；<br>API声明：onApplicationBackground(): void;<br>差异内容：onApplicationBackground(): void;|api/@ohos.app.ability.ApplicationStateChangeCallback.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace appManager<br>差异内容：declare namespace appManager|api/@ohos.app.ability.appManager.d.ts|
|新增API|NA|类名：appManager；<br>API声明：export enum ProcessState<br>差异内容：export enum ProcessState|api/@ohos.app.ability.appManager.d.ts|
|新增API|NA|类名：ProcessState；<br>API声明：STATE_CREATE<br>差异内容：STATE_CREATE|api/@ohos.app.ability.appManager.d.ts|
|新增API|NA|类名：ProcessState；<br>API声明：STATE_FOREGROUND<br>差异内容：STATE_FOREGROUND|api/@ohos.app.ability.appManager.d.ts|
|新增API|NA|类名：ProcessState；<br>API声明：STATE_ACTIVE<br>差异内容：STATE_ACTIVE|api/@ohos.app.ability.appManager.d.ts|
|新增API|NA|类名：ProcessState；<br>API声明：STATE_BACKGROUND<br>差异内容：STATE_BACKGROUND|api/@ohos.app.ability.appManager.d.ts|
|新增API|NA|类名：ProcessState；<br>API声明：STATE_DESTROY<br>差异内容：STATE_DESTROY|api/@ohos.app.ability.appManager.d.ts|
|新增API|NA|类名：appManager；<br>API声明：function isRunningInStabilityTest(callback: AsyncCallback\<boolean>): void;<br>差异内容：function isRunningInStabilityTest(callback: AsyncCallback\<boolean>): void;|api/@ohos.app.ability.appManager.d.ts|
|新增API|NA|类名：appManager；<br>API声明：function isRunningInStabilityTest(): Promise\<boolean>;<br>差异内容：function isRunningInStabilityTest(): Promise\<boolean>;|api/@ohos.app.ability.appManager.d.ts|
|新增API|NA|类名：appManager；<br>API声明：function isRamConstrainedDevice(): Promise\<boolean>;<br>差异内容：function isRamConstrainedDevice(): Promise\<boolean>;|api/@ohos.app.ability.appManager.d.ts|
|新增API|NA|类名：appManager；<br>API声明：function isRamConstrainedDevice(callback: AsyncCallback\<boolean>): void;<br>差异内容：function isRamConstrainedDevice(callback: AsyncCallback\<boolean>): void;|api/@ohos.app.ability.appManager.d.ts|
|新增API|NA|类名：appManager；<br>API声明：function getAppMemorySize(): Promise\<number>;<br>差异内容：function getAppMemorySize(): Promise\<number>;|api/@ohos.app.ability.appManager.d.ts|
|新增API|NA|类名：appManager；<br>API声明：function getAppMemorySize(callback: AsyncCallback\<number>): void;<br>差异内容：function getAppMemorySize(callback: AsyncCallback\<number>): void;|api/@ohos.app.ability.appManager.d.ts|
|新增API|NA|类名：appManager；<br>API声明：function getRunningProcessInformation(): Promise\<Array\<ProcessInformation>>;<br>差异内容：function getRunningProcessInformation(): Promise\<Array\<ProcessInformation>>;|api/@ohos.app.ability.appManager.d.ts|
|新增API|NA|类名：appManager；<br>API声明：function getRunningProcessInformation(callback: AsyncCallback\<Array\<ProcessInformation>>): void;<br>差异内容：function getRunningProcessInformation(callback: AsyncCallback\<Array\<ProcessInformation>>): void;|api/@ohos.app.ability.appManager.d.ts|
|新增API|NA|类名：appManager；<br>API声明：export type ProcessInformation = _ProcessInformation;<br>差异内容：export type ProcessInformation = _ProcessInformation;|api/@ohos.app.ability.appManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace appRecovery<br>差异内容：declare namespace appRecovery|api/@ohos.app.ability.appRecovery.d.ts|
|新增API|NA|类名：appRecovery；<br>API声明：enum RestartFlag<br>差异内容：enum RestartFlag|api/@ohos.app.ability.appRecovery.d.ts|
|新增API|NA|类名：RestartFlag；<br>API声明：ALWAYS_RESTART = 0<br>差异内容：ALWAYS_RESTART = 0|api/@ohos.app.ability.appRecovery.d.ts|
|新增API|NA|类名：RestartFlag；<br>API声明：RESTART_WHEN_JS_CRASH = 0x0001<br>差异内容：RESTART_WHEN_JS_CRASH = 0x0001|api/@ohos.app.ability.appRecovery.d.ts|
|新增API|NA|类名：RestartFlag；<br>API声明：RESTART_WHEN_APP_FREEZE = 0x0002<br>差异内容：RESTART_WHEN_APP_FREEZE = 0x0002|api/@ohos.app.ability.appRecovery.d.ts|
|新增API|NA|类名：RestartFlag；<br>API声明：NO_RESTART = 0xFFFF<br>差异内容：NO_RESTART = 0xFFFF|api/@ohos.app.ability.appRecovery.d.ts|
|新增API|NA|类名：appRecovery；<br>API声明：enum SaveOccasionFlag<br>差异内容：enum SaveOccasionFlag|api/@ohos.app.ability.appRecovery.d.ts|
|新增API|NA|类名：SaveOccasionFlag；<br>API声明：SAVE_WHEN_ERROR = 0x0001<br>差异内容：SAVE_WHEN_ERROR = 0x0001|api/@ohos.app.ability.appRecovery.d.ts|
|新增API|NA|类名：SaveOccasionFlag；<br>API声明：SAVE_WHEN_BACKGROUND = 0x0002<br>差异内容：SAVE_WHEN_BACKGROUND = 0x0002|api/@ohos.app.ability.appRecovery.d.ts|
|新增API|NA|类名：appRecovery；<br>API声明：enum SaveModeFlag<br>差异内容：enum SaveModeFlag|api/@ohos.app.ability.appRecovery.d.ts|
|新增API|NA|类名：SaveModeFlag；<br>API声明：SAVE_WITH_FILE = 0x0001<br>差异内容：SAVE_WITH_FILE = 0x0001|api/@ohos.app.ability.appRecovery.d.ts|
|新增API|NA|类名：SaveModeFlag；<br>API声明：SAVE_WITH_SHARED_MEMORY = 0x0002<br>差异内容：SAVE_WITH_SHARED_MEMORY = 0x0002|api/@ohos.app.ability.appRecovery.d.ts|
|新增API|NA|类名：appRecovery；<br>API声明：function enableAppRecovery(restart?: RestartFlag, saveOccasion?: SaveOccasionFlag, saveMode?: SaveModeFlag): void;<br>差异内容：function enableAppRecovery(restart?: RestartFlag, saveOccasion?: SaveOccasionFlag, saveMode?: SaveModeFlag): void;|api/@ohos.app.ability.appRecovery.d.ts|
|新增API|NA|类名：appRecovery；<br>API声明：function restartApp(): void;<br>差异内容：function restartApp(): void;|api/@ohos.app.ability.appRecovery.d.ts|
|新增API|NA|类名：appRecovery；<br>API声明：function setRestartWant(want: Want): void;<br>差异内容：function setRestartWant(want: Want): void;|api/@ohos.app.ability.appRecovery.d.ts|
|新增API|NA|类名：appRecovery；<br>API声明：function saveAppState(): boolean;<br>差异内容：function saveAppState(): boolean;|api/@ohos.app.ability.appRecovery.d.ts|
|新增API|NA|类名：appRecovery；<br>API声明：function saveAppState(context?: UIAbilityContext): boolean;<br>差异内容：function saveAppState(context?: UIAbilityContext): boolean;|api/@ohos.app.ability.appRecovery.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace autoFillManager<br>差异内容：declare namespace autoFillManager|api/@ohos.app.ability.autoFillManager.d.ts|
|新增API|NA|类名：autoFillManager；<br>API声明：export interface AutoSaveCallback<br>差异内容：export interface AutoSaveCallback|api/@ohos.app.ability.autoFillManager.d.ts|
|新增API|NA|类名：AutoSaveCallback；<br>API声明：onSuccess(): void;<br>差异内容：onSuccess(): void;|api/@ohos.app.ability.autoFillManager.d.ts|
|新增API|NA|类名：AutoSaveCallback；<br>API声明：onFailure(): void;<br>差异内容：onFailure(): void;|api/@ohos.app.ability.autoFillManager.d.ts|
|新增API|NA|类名：autoFillManager；<br>API声明：export function requestAutoSave(context: UIContext, callback?: AutoSaveCallback): void;<br>差异内容：export function requestAutoSave(context: UIContext, callback?: AutoSaveCallback): void;|api/@ohos.app.ability.autoFillManager.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class ChildProcess<br>差异内容：export default class ChildProcess|api/@ohos.app.ability.ChildProcess.d.ts|
|新增API|NA|类名：ChildProcess；<br>API声明：onStart(): void;<br>差异内容：onStart(): void;|api/@ohos.app.ability.ChildProcess.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace childProcessManager<br>差异内容：declare namespace childProcessManager|api/@ohos.app.ability.childProcessManager.d.ts|
|新增API|NA|类名：childProcessManager；<br>API声明：export const enum StartMode<br>差异内容：export const enum StartMode|api/@ohos.app.ability.childProcessManager.d.ts|
|新增API|NA|类名：StartMode；<br>API声明：SELF_FORK = 0<br>差异内容：SELF_FORK = 0|api/@ohos.app.ability.childProcessManager.d.ts|
|新增API|NA|类名：StartMode；<br>API声明：APP_SPAWN_FORK = 1<br>差异内容：APP_SPAWN_FORK = 1|api/@ohos.app.ability.childProcessManager.d.ts|
|新增API|NA|类名：childProcessManager；<br>API声明：function startChildProcess(srcEntry: string, startMode: StartMode): Promise\<number>;<br>差异内容：function startChildProcess(srcEntry: string, startMode: StartMode): Promise\<number>;|api/@ohos.app.ability.childProcessManager.d.ts|
|新增API|NA|类名：childProcessManager；<br>API声明：function startChildProcess(srcEntry: string, startMode: StartMode, callback: AsyncCallback\<number>): void;<br>差异内容：function startChildProcess(srcEntry: string, startMode: StartMode, callback: AsyncCallback\<number>): void;|api/@ohos.app.ability.childProcessManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace common<br>差异内容：declare namespace common|api/@ohos.app.ability.common.d.ts|
|新增API|NA|类名：common；<br>API声明：export type UIAbilityContext = _UIAbilityContext.default;<br>差异内容：export type UIAbilityContext = _UIAbilityContext.default;|api/@ohos.app.ability.common.d.ts|
|新增API|NA|类名：common；<br>API声明：export type AbilityStageContext = _AbilityStageContext.default;<br>差异内容：export type AbilityStageContext = _AbilityStageContext.default;|api/@ohos.app.ability.common.d.ts|
|新增API|NA|类名：common；<br>API声明：export type ApplicationContext = _ApplicationContext.default;<br>差异内容：export type ApplicationContext = _ApplicationContext.default;|api/@ohos.app.ability.common.d.ts|
|新增API|NA|类名：common；<br>API声明：export type BaseContext = _BaseContext.default;<br>差异内容：export type BaseContext = _BaseContext.default;|api/@ohos.app.ability.common.d.ts|
|新增API|NA|类名：common；<br>API声明：export type Context = _Context.default;<br>差异内容：export type Context = _Context.default;|api/@ohos.app.ability.common.d.ts|
|新增API|NA|类名：common；<br>API声明：export type ExtensionContext = _ExtensionContext.default;<br>差异内容：export type ExtensionContext = _ExtensionContext.default;|api/@ohos.app.ability.common.d.ts|
|新增API|NA|类名：common；<br>API声明：export type FormExtensionContext = _FormExtensionContext.default;<br>差异内容：export type FormExtensionContext = _FormExtensionContext.default;|api/@ohos.app.ability.common.d.ts|
|新增API|NA|类名：common；<br>API声明：export type EventHub = _EventHub.default;<br>差异内容：export type EventHub = _EventHub.default;|api/@ohos.app.ability.common.d.ts|
|新增API|NA|类名：common；<br>API声明：export type PacMap = _PacMap;<br>差异内容：export type PacMap = _PacMap;|api/@ohos.app.ability.common.d.ts|
|新增API|NA|类名：common；<br>API声明：export type AbilityResult = _AbilityResult;<br>差异内容：export type AbilityResult = _AbilityResult;|api/@ohos.app.ability.common.d.ts|
|新增API|NA|类名：common；<br>API声明：export type ConnectOptions = _ConnectOptions;<br>差异内容：export type ConnectOptions = _ConnectOptions;|api/@ohos.app.ability.common.d.ts|
|新增API|NA|类名：common；<br>API声明：export type UIExtensionContext = _UIExtensionContext.default;<br>差异内容：export type UIExtensionContext = _UIExtensionContext.default;|api/@ohos.app.ability.common.d.ts|
|新增API|NA|类名：common；<br>API声明：export type AbilityStartCallback = _AbilityStartCallback;<br>差异内容：export type AbilityStartCallback = _AbilityStartCallback;|api/@ohos.app.ability.common.d.ts|
|新增API|NA|类名：common；<br>API声明：export type VpnExtensionContext = _VpnExtensionContext.default;<br>差异内容：export type VpnExtensionContext = _VpnExtensionContext.default;|api/@ohos.app.ability.common.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Configuration<br>差异内容：export interface Configuration|api/@ohos.app.ability.Configuration.d.ts|
|新增API|NA|类名：Configuration；<br>API声明：language?: string;<br>差异内容：language?: string;|api/@ohos.app.ability.Configuration.d.ts|
|新增API|NA|类名：Configuration；<br>API声明：colorMode?: ConfigurationConstant.ColorMode;<br>差异内容：colorMode?: ConfigurationConstant.ColorMode;|api/@ohos.app.ability.Configuration.d.ts|
|新增API|NA|类名：Configuration；<br>API声明：direction?: ConfigurationConstant.Direction;<br>差异内容：direction?: ConfigurationConstant.Direction;|api/@ohos.app.ability.Configuration.d.ts|
|新增API|NA|类名：Configuration；<br>API声明：screenDensity?: ConfigurationConstant.ScreenDensity;<br>差异内容：screenDensity?: ConfigurationConstant.ScreenDensity;|api/@ohos.app.ability.Configuration.d.ts|
|新增API|NA|类名：Configuration；<br>API声明：displayId?: number;<br>差异内容：displayId?: number;|api/@ohos.app.ability.Configuration.d.ts|
|新增API|NA|类名：Configuration；<br>API声明：hasPointerDevice?: boolean;<br>差异内容：hasPointerDevice?: boolean;|api/@ohos.app.ability.Configuration.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace ConfigurationConstant<br>差异内容：declare namespace ConfigurationConstant|api/@ohos.app.ability.ConfigurationConstant.d.ts|
|新增API|NA|类名：ConfigurationConstant；<br>API声明：export enum ColorMode<br>差异内容：export enum ColorMode|api/@ohos.app.ability.ConfigurationConstant.d.ts|
|新增API|NA|类名：ColorMode；<br>API声明：COLOR_MODE_NOT_SET = -1<br>差异内容：COLOR_MODE_NOT_SET = -1|api/@ohos.app.ability.ConfigurationConstant.d.ts|
|新增API|NA|类名：ColorMode；<br>API声明：COLOR_MODE_DARK = 0<br>差异内容：COLOR_MODE_DARK = 0|api/@ohos.app.ability.ConfigurationConstant.d.ts|
|新增API|NA|类名：ColorMode；<br>API声明：COLOR_MODE_LIGHT = 1<br>差异内容：COLOR_MODE_LIGHT = 1|api/@ohos.app.ability.ConfigurationConstant.d.ts|
|新增API|NA|类名：ConfigurationConstant；<br>API声明：export enum Direction<br>差异内容：export enum Direction|api/@ohos.app.ability.ConfigurationConstant.d.ts|
|新增API|NA|类名：Direction；<br>API声明：DIRECTION_NOT_SET = -1<br>差异内容：DIRECTION_NOT_SET = -1|api/@ohos.app.ability.ConfigurationConstant.d.ts|
|新增API|NA|类名：Direction；<br>API声明：DIRECTION_VERTICAL = 0<br>差异内容：DIRECTION_VERTICAL = 0|api/@ohos.app.ability.ConfigurationConstant.d.ts|
|新增API|NA|类名：Direction；<br>API声明：DIRECTION_HORIZONTAL = 1<br>差异内容：DIRECTION_HORIZONTAL = 1|api/@ohos.app.ability.ConfigurationConstant.d.ts|
|新增API|NA|类名：ConfigurationConstant；<br>API声明：export enum ScreenDensity<br>差异内容：export enum ScreenDensity|api/@ohos.app.ability.ConfigurationConstant.d.ts|
|新增API|NA|类名：ScreenDensity；<br>API声明：SCREEN_DENSITY_NOT_SET = 0<br>差异内容：SCREEN_DENSITY_NOT_SET = 0|api/@ohos.app.ability.ConfigurationConstant.d.ts|
|新增API|NA|类名：ScreenDensity；<br>API声明：SCREEN_DENSITY_SDPI = 120<br>差异内容：SCREEN_DENSITY_SDPI = 120|api/@ohos.app.ability.ConfigurationConstant.d.ts|
|新增API|NA|类名：ScreenDensity；<br>API声明：SCREEN_DENSITY_MDPI = 160<br>差异内容：SCREEN_DENSITY_MDPI = 160|api/@ohos.app.ability.ConfigurationConstant.d.ts|
|新增API|NA|类名：ScreenDensity；<br>API声明：SCREEN_DENSITY_LDPI = 240<br>差异内容：SCREEN_DENSITY_LDPI = 240|api/@ohos.app.ability.ConfigurationConstant.d.ts|
|新增API|NA|类名：ScreenDensity；<br>API声明：SCREEN_DENSITY_XLDPI = 320<br>差异内容：SCREEN_DENSITY_XLDPI = 320|api/@ohos.app.ability.ConfigurationConstant.d.ts|
|新增API|NA|类名：ScreenDensity；<br>API声明：SCREEN_DENSITY_XXLDPI = 480<br>差异内容：SCREEN_DENSITY_XXLDPI = 480|api/@ohos.app.ability.ConfigurationConstant.d.ts|
|新增API|NA|类名：ScreenDensity；<br>API声明：SCREEN_DENSITY_XXXLDPI = 640<br>差异内容：SCREEN_DENSITY_XXXLDPI = 640|api/@ohos.app.ability.ConfigurationConstant.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace contextConstant<br>差异内容：declare namespace contextConstant|api/@ohos.app.ability.contextConstant.d.ts|
|新增API|NA|类名：contextConstant；<br>API声明：export enum AreaMode<br>差异内容：export enum AreaMode|api/@ohos.app.ability.contextConstant.d.ts|
|新增API|NA|类名：AreaMode；<br>API声明：EL1 = 0<br>差异内容：EL1 = 0|api/@ohos.app.ability.contextConstant.d.ts|
|新增API|NA|类名：AreaMode；<br>API声明：EL2 = 1<br>差异内容：EL2 = 1|api/@ohos.app.ability.contextConstant.d.ts|
|新增API|NA|类名：AreaMode；<br>API声明：EL3 = 2<br>差异内容：EL3 = 2|api/@ohos.app.ability.contextConstant.d.ts|
|新增API|NA|类名：AreaMode；<br>API声明：EL4 = 3<br>差异内容：EL4 = 3|api/@ohos.app.ability.contextConstant.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace dataUriUtils<br>差异内容：declare namespace dataUriUtils|api/@ohos.app.ability.dataUriUtils.d.ts|
|新增API|NA|类名：dataUriUtils；<br>API声明：function getId(uri: string): number;<br>差异内容：function getId(uri: string): number;|api/@ohos.app.ability.dataUriUtils.d.ts|
|新增API|NA|类名：dataUriUtils；<br>API声明：function attachId(uri: string, id: number): string;<br>差异内容：function attachId(uri: string, id: number): string;|api/@ohos.app.ability.dataUriUtils.d.ts|
|新增API|NA|类名：dataUriUtils；<br>API声明：function deleteId(uri: string): string;<br>差异内容：function deleteId(uri: string): string;|api/@ohos.app.ability.dataUriUtils.d.ts|
|新增API|NA|类名：dataUriUtils；<br>API声明：function updateId(uri: string, id: number): string;<br>差异内容：function updateId(uri: string, id: number): string;|api/@ohos.app.ability.dataUriUtils.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace dialogRequest<br>差异内容：declare namespace dialogRequest|api/@ohos.app.ability.dialogRequest.d.ts|
|新增API|NA|类名：dialogRequest；<br>API声明：export interface WindowRect<br>差异内容：export interface WindowRect|api/@ohos.app.ability.dialogRequest.d.ts|
|新增API|NA|类名：WindowRect；<br>API声明：left: number;<br>差异内容：left: number;|api/@ohos.app.ability.dialogRequest.d.ts|
|新增API|NA|类名：WindowRect；<br>API声明：top: number;<br>差异内容：top: number;|api/@ohos.app.ability.dialogRequest.d.ts|
|新增API|NA|类名：WindowRect；<br>API声明：width: number;<br>差异内容：width: number;|api/@ohos.app.ability.dialogRequest.d.ts|
|新增API|NA|类名：WindowRect；<br>API声明：height: number;<br>差异内容：height: number;|api/@ohos.app.ability.dialogRequest.d.ts|
|新增API|NA|类名：dialogRequest；<br>API声明：export interface RequestInfo<br>差异内容：export interface RequestInfo|api/@ohos.app.ability.dialogRequest.d.ts|
|新增API|NA|类名：RequestInfo；<br>API声明：windowRect?: WindowRect;<br>差异内容：windowRect?: WindowRect;|api/@ohos.app.ability.dialogRequest.d.ts|
|新增API|NA|类名：dialogRequest；<br>API声明：export enum ResultCode<br>差异内容：export enum ResultCode|api/@ohos.app.ability.dialogRequest.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：RESULT_OK = 0<br>差异内容：RESULT_OK = 0|api/@ohos.app.ability.dialogRequest.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：RESULT_CANCEL = 1<br>差异内容：RESULT_CANCEL = 1|api/@ohos.app.ability.dialogRequest.d.ts|
|新增API|NA|类名：dialogRequest；<br>API声明：export interface RequestResult<br>差异内容：export interface RequestResult|api/@ohos.app.ability.dialogRequest.d.ts|
|新增API|NA|类名：RequestResult；<br>API声明：result: ResultCode;<br>差异内容：result: ResultCode;|api/@ohos.app.ability.dialogRequest.d.ts|
|新增API|NA|类名：RequestResult；<br>API声明：want?: Want;<br>差异内容：want?: Want;|api/@ohos.app.ability.dialogRequest.d.ts|
|新增API|NA|类名：dialogRequest；<br>API声明：export interface RequestCallback<br>差异内容：export interface RequestCallback|api/@ohos.app.ability.dialogRequest.d.ts|
|新增API|NA|类名：RequestCallback；<br>API声明：setRequestResult(result: RequestResult): void;<br>差异内容：setRequestResult(result: RequestResult): void;|api/@ohos.app.ability.dialogRequest.d.ts|
|新增API|NA|类名：dialogRequest；<br>API声明：function getRequestInfo(want: Want): RequestInfo;<br>差异内容：function getRequestInfo(want: Want): RequestInfo;|api/@ohos.app.ability.dialogRequest.d.ts|
|新增API|NA|类名：dialogRequest；<br>API声明：function getRequestCallback(want: Want): RequestCallback;<br>差异内容：function getRequestCallback(want: Want): RequestCallback;|api/@ohos.app.ability.dialogRequest.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class EnvironmentCallback<br>差异内容：export default class EnvironmentCallback|api/@ohos.app.ability.EnvironmentCallback.d.ts|
|新增API|NA|类名：EnvironmentCallback；<br>API声明：onConfigurationUpdated(config: Configuration): void;<br>差异内容：onConfigurationUpdated(config: Configuration): void;|api/@ohos.app.ability.EnvironmentCallback.d.ts|
|新增API|NA|类名：EnvironmentCallback；<br>API声明：onMemoryLevel(level: AbilityConstant.MemoryLevel): void;<br>差异内容：onMemoryLevel(level: AbilityConstant.MemoryLevel): void;|api/@ohos.app.ability.EnvironmentCallback.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace errorManager<br>差异内容：declare namespace errorManager|api/@ohos.app.ability.errorManager.d.ts|
|新增API|NA|类名：errorManager；<br>API声明：function on(type: 'error', observer: ErrorObserver): number;<br>差异内容：function on(type: 'error', observer: ErrorObserver): number;|api/@ohos.app.ability.errorManager.d.ts|
|新增API|NA|类名：errorManager；<br>API声明：function off(type: 'error', observerId: number, callback: AsyncCallback\<void>): void;<br>差异内容：function off(type: 'error', observerId: number, callback: AsyncCallback\<void>): void;|api/@ohos.app.ability.errorManager.d.ts|
|新增API|NA|类名：errorManager；<br>API声明：function off(type: 'error', observerId: number): Promise\<void>;<br>差异内容：function off(type: 'error', observerId: number): Promise\<void>;|api/@ohos.app.ability.errorManager.d.ts|
|新增API|NA|类名：errorManager；<br>API声明：export type ErrorObserver = _ErrorObserver.default;<br>差异内容：export type ErrorObserver = _ErrorObserver.default;|api/@ohos.app.ability.errorManager.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class ExtensionAbility<br>差异内容：export default class ExtensionAbility|api/@ohos.app.ability.ExtensionAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace insightIntent<br>差异内容：declare namespace insightIntent|api/@ohos.app.ability.insightIntent.d.ts|
|新增API|NA|类名：insightIntent；<br>API声明：enum ExecuteMode<br>差异内容：enum ExecuteMode|api/@ohos.app.ability.insightIntent.d.ts|
|新增API|NA|类名：ExecuteMode；<br>API声明：UI_ABILITY_FOREGROUND = 0<br>差异内容：UI_ABILITY_FOREGROUND = 0|api/@ohos.app.ability.insightIntent.d.ts|
|新增API|NA|类名：ExecuteMode；<br>API声明：UI_ABILITY_BACKGROUND = 1<br>差异内容：UI_ABILITY_BACKGROUND = 1|api/@ohos.app.ability.insightIntent.d.ts|
|新增API|NA|类名：ExecuteMode；<br>API声明：UI_EXTENSION_ABILITY = 2<br>差异内容：UI_EXTENSION_ABILITY = 2|api/@ohos.app.ability.insightIntent.d.ts|
|新增API|NA|类名：insightIntent；<br>API声明：interface ExecuteResult<br>差异内容：interface ExecuteResult|api/@ohos.app.ability.insightIntent.d.ts|
|新增API|NA|类名：ExecuteResult；<br>API声明：code: number;<br>差异内容：code: number;|api/@ohos.app.ability.insightIntent.d.ts|
|新增API|NA|类名：ExecuteResult；<br>API声明：result?: Record\<string, Object>;<br>差异内容：result?: Record\<string, Object>;|api/@ohos.app.ability.insightIntent.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class InsightIntentContext<br>差异内容：export default class InsightIntentContext|api/@ohos.app.ability.InsightIntentContext.d.ts|
|新增API|NA|类名：InsightIntentContext；<br>API声明：startAbility(want: Want, callback: AsyncCallback\<void>): void;<br>差异内容：startAbility(want: Want, callback: AsyncCallback\<void>): void;|api/@ohos.app.ability.InsightIntentContext.d.ts|
|新增API|NA|类名：InsightIntentContext；<br>API声明：startAbility(want: Want): Promise\<void>;<br>差异内容：startAbility(want: Want): Promise\<void>;|api/@ohos.app.ability.InsightIntentContext.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class InsightIntentExecutor<br>差异内容：export default class InsightIntentExecutor|api/@ohos.app.ability.InsightIntentExecutor.d.ts|
|新增API|NA|类名：InsightIntentExecutor；<br>API声明：context: InsightIntentContext;<br>差异内容：context: InsightIntentContext;|api/@ohos.app.ability.InsightIntentExecutor.d.ts|
|新增API|NA|类名：InsightIntentExecutor；<br>API声明：onExecuteInUIAbilityForegroundMode(name: string, param: Record\<string, Object>, pageLoader: window.WindowStage): insightIntent.ExecuteResult \| Promise\<insightIntent.ExecuteResult>;<br>差异内容：onExecuteInUIAbilityForegroundMode(name: string, param: Record\<string, Object>, pageLoader: window.WindowStage): insightIntent.ExecuteResult \| Promise\<insightIntent.ExecuteResult>;|api/@ohos.app.ability.InsightIntentExecutor.d.ts|
|新增API|NA|类名：InsightIntentExecutor；<br>API声明：onExecuteInUIAbilityBackgroundMode(name: string, param: Record\<string, Object>): insightIntent.ExecuteResult \| Promise\<insightIntent.ExecuteResult>;<br>差异内容：onExecuteInUIAbilityBackgroundMode(name: string, param: Record\<string, Object>): insightIntent.ExecuteResult \| Promise\<insightIntent.ExecuteResult>;|api/@ohos.app.ability.InsightIntentExecutor.d.ts|
|新增API|NA|类名：InsightIntentExecutor；<br>API声明：onExecuteInUIExtensionAbility(name: string, param: Record\<string, Object>, pageLoader: UIExtensionContentSession): insightIntent.ExecuteResult \| Promise\<insightIntent.ExecuteResult>;<br>差异内容：onExecuteInUIExtensionAbility(name: string, param: Record\<string, Object>, pageLoader: UIExtensionContentSession): insightIntent.ExecuteResult \| Promise\<insightIntent.ExecuteResult>;|api/@ohos.app.ability.InsightIntentExecutor.d.ts|
|新增API|NA|类名：InsightIntentExecutor；<br>API声明：onExecuteInServiceExtensionAbility(name: string, param: Record\<string, Object>): insightIntent.ExecuteResult \| Promise\<insightIntent.ExecuteResult>;<br>差异内容：onExecuteInServiceExtensionAbility(name: string, param: Record\<string, Object>): insightIntent.ExecuteResult \| Promise\<insightIntent.ExecuteResult>;|api/@ohos.app.ability.InsightIntentExecutor.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class ShareExtensionAbility<br>差异内容：export default class ShareExtensionAbility|api/@ohos.app.ability.ShareExtensionAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class StartOptions<br>差异内容：export default class StartOptions|api/@ohos.app.ability.StartOptions.d.ts|
|新增API|NA|类名：StartOptions；<br>API声明：displayId?: number;<br>差异内容：displayId?: number;|api/@ohos.app.ability.StartOptions.d.ts|
|新增API|NA|类名：StartOptions；<br>API声明：withAnimation?: boolean;<br>差异内容：withAnimation?: boolean;|api/@ohos.app.ability.StartOptions.d.ts|
|新增API|NA|类名：StartOptions；<br>API声明：windowLeft?: number;<br>差异内容：windowLeft?: number;|api/@ohos.app.ability.StartOptions.d.ts|
|新增API|NA|类名：StartOptions；<br>API声明：windowTop?: number;<br>差异内容：windowTop?: number;|api/@ohos.app.ability.StartOptions.d.ts|
|新增API|NA|类名：StartOptions；<br>API声明：windowWidth?: number;<br>差异内容：windowWidth?: number;|api/@ohos.app.ability.StartOptions.d.ts|
|新增API|NA|类名：StartOptions；<br>API声明：windowHeight?: number;<br>差异内容：windowHeight?: number;|api/@ohos.app.ability.StartOptions.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface OnReleaseCallback<br>差异内容：export interface OnReleaseCallback|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface OnRemoteStateChangeCallback<br>差异内容：export interface OnRemoteStateChangeCallback|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface CalleeCallback<br>差异内容：export interface CalleeCallback|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Caller<br>差异内容：export interface Caller|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：Caller；<br>API声明：call(method: string, data: rpc.Parcelable): Promise\<void>;<br>差异内容：call(method: string, data: rpc.Parcelable): Promise\<void>;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：Caller；<br>API声明：callWithResult(method: string, data: rpc.Parcelable): Promise\<rpc.MessageSequence>;<br>差异内容：callWithResult(method: string, data: rpc.Parcelable): Promise\<rpc.MessageSequence>;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：Caller；<br>API声明：release(): void;<br>差异内容：release(): void;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：Caller；<br>API声明：onRelease(callback: OnReleaseCallback): void;<br>差异内容：onRelease(callback: OnReleaseCallback): void;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：Caller；<br>API声明：onRemoteStateChange(callback: OnRemoteStateChangeCallback): void;<br>差异内容：onRemoteStateChange(callback: OnRemoteStateChangeCallback): void;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：Caller；<br>API声明：on(type: 'release', callback: OnReleaseCallback): void;<br>差异内容：on(type: 'release', callback: OnReleaseCallback): void;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：Caller；<br>API声明：off(type: 'release', callback: OnReleaseCallback): void;<br>差异内容：off(type: 'release', callback: OnReleaseCallback): void;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：Caller；<br>API声明：off(type: 'release'): void;<br>差异内容：off(type: 'release'): void;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Callee<br>差异内容：export interface Callee|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：Callee；<br>API声明：on(method: string, callback: CalleeCallback): void;<br>差异内容：on(method: string, callback: CalleeCallback): void;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：Callee；<br>API声明：off(method: string): void;<br>差异内容：off(method: string): void;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class UIAbility<br>差异内容：export default class UIAbility|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：UIAbility；<br>API声明：context: UIAbilityContext;<br>差异内容：context: UIAbilityContext;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：UIAbility；<br>API声明：launchWant: Want;<br>差异内容：launchWant: Want;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：UIAbility；<br>API声明：lastRequestWant: Want;<br>差异内容：lastRequestWant: Want;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：UIAbility；<br>API声明：callee: Callee;<br>差异内容：callee: Callee;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：UIAbility；<br>API声明：onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void;<br>差异内容：onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：UIAbility；<br>API声明：onWindowStageCreate(windowStage: window.WindowStage): void;<br>差异内容：onWindowStageCreate(windowStage: window.WindowStage): void;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：UIAbility；<br>API声明：onWindowStageDestroy(): void;<br>差异内容：onWindowStageDestroy(): void;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：UIAbility；<br>API声明：onWindowStageRestore(windowStage: window.WindowStage): void;<br>差异内容：onWindowStageRestore(windowStage: window.WindowStage): void;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：UIAbility；<br>API声明：onDestroy(): void \| Promise\<void>;<br>差异内容：onDestroy(): void \| Promise\<void>;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：UIAbility；<br>API声明：onForeground(): void;<br>差异内容：onForeground(): void;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：UIAbility；<br>API声明：onBackground(): void;<br>差异内容：onBackground(): void;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：UIAbility；<br>API声明：onContinue(wantParam: Record\<string, Object>): AbilityConstant.OnContinueResult;<br>差异内容：onContinue(wantParam: Record\<string, Object>): AbilityConstant.OnContinueResult;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：UIAbility；<br>API声明：onNewWant(want: Want, launchParam: AbilityConstant.LaunchParam): void;<br>差异内容：onNewWant(want: Want, launchParam: AbilityConstant.LaunchParam): void;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：UIAbility；<br>API声明：onDump(params: Array\<string>): Array\<string>;<br>差异内容：onDump(params: Array\<string>): Array\<string>;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：UIAbility；<br>API声明：onSaveState(reason: AbilityConstant.StateType, wantParam: Record\<string, Object>): AbilityConstant.OnSaveResult;<br>差异内容：onSaveState(reason: AbilityConstant.StateType, wantParam: Record\<string, Object>): AbilityConstant.OnSaveResult;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：UIAbility；<br>API声明：onShare(wantParam: Record\<string, Object>): void;<br>差异内容：onShare(wantParam: Record\<string, Object>): void;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：UIAbility；<br>API声明：onPrepareToTerminate(): boolean;<br>差异内容：onPrepareToTerminate(): boolean;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：UIAbility；<br>API声明：onBackPressed(): boolean;<br>差异内容：onBackPressed(): boolean;|api/@ohos.app.ability.UIAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class UIExtensionAbility<br>差异内容：export default class UIExtensionAbility|api/@ohos.app.ability.UIExtensionAbility.d.ts|
|新增API|NA|类名：UIExtensionAbility；<br>API声明：context: UIExtensionContext;<br>差异内容：context: UIExtensionContext;|api/@ohos.app.ability.UIExtensionAbility.d.ts|
|新增API|NA|类名：UIExtensionAbility；<br>API声明：onCreate(): void;<br>差异内容：onCreate(): void;|api/@ohos.app.ability.UIExtensionAbility.d.ts|
|新增API|NA|类名：UIExtensionAbility；<br>API声明：onSessionCreate(want: Want, session: UIExtensionContentSession): void;<br>差异内容：onSessionCreate(want: Want, session: UIExtensionContentSession): void;|api/@ohos.app.ability.UIExtensionAbility.d.ts|
|新增API|NA|类名：UIExtensionAbility；<br>API声明：onSessionDestroy(session: UIExtensionContentSession): void;<br>差异内容：onSessionDestroy(session: UIExtensionContentSession): void;|api/@ohos.app.ability.UIExtensionAbility.d.ts|
|新增API|NA|类名：UIExtensionAbility；<br>API声明：onForeground(): void;<br>差异内容：onForeground(): void;|api/@ohos.app.ability.UIExtensionAbility.d.ts|
|新增API|NA|类名：UIExtensionAbility；<br>API声明：onBackground(): void;<br>差异内容：onBackground(): void;|api/@ohos.app.ability.UIExtensionAbility.d.ts|
|新增API|NA|类名：UIExtensionAbility；<br>API声明：onDestroy(): void \| Promise\<void>;<br>差异内容：onDestroy(): void \| Promise\<void>;|api/@ohos.app.ability.UIExtensionAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class UIExtensionContentSession<br>差异内容：export default class UIExtensionContentSession|api/@ohos.app.ability.UIExtensionContentSession.d.ts|
|新增API|NA|类名：UIExtensionContentSession；<br>API声明：loadContent(path: string, storage?: LocalStorage): void;<br>差异内容：loadContent(path: string, storage?: LocalStorage): void;|api/@ohos.app.ability.UIExtensionContentSession.d.ts|
|新增API|NA|类名：UIExtensionContentSession；<br>API声明：terminateSelf(callback: AsyncCallback\<void>): void;<br>差异内容：terminateSelf(callback: AsyncCallback\<void>): void;|api/@ohos.app.ability.UIExtensionContentSession.d.ts|
|新增API|NA|类名：UIExtensionContentSession；<br>API声明：terminateSelf(): Promise\<void>;<br>差异内容：terminateSelf(): Promise\<void>;|api/@ohos.app.ability.UIExtensionContentSession.d.ts|
|新增API|NA|类名：UIExtensionContentSession；<br>API声明：terminateSelfWithResult(parameter: AbilityResult, callback: AsyncCallback\<void>): void;<br>差异内容：terminateSelfWithResult(parameter: AbilityResult, callback: AsyncCallback\<void>): void;|api/@ohos.app.ability.UIExtensionContentSession.d.ts|
|新增API|NA|类名：UIExtensionContentSession；<br>API声明：terminateSelfWithResult(parameter: AbilityResult): Promise\<void>;<br>差异内容：terminateSelfWithResult(parameter: AbilityResult): Promise\<void>;|api/@ohos.app.ability.UIExtensionContentSession.d.ts|
|新增API|NA|类名：UIExtensionContentSession；<br>API声明：setWindowPrivacyMode(isPrivacyMode: boolean): Promise\<void>;<br>差异内容：setWindowPrivacyMode(isPrivacyMode: boolean): Promise\<void>;|api/@ohos.app.ability.UIExtensionContentSession.d.ts|
|新增API|NA|类名：UIExtensionContentSession；<br>API声明：setWindowPrivacyMode(isPrivacyMode: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：setWindowPrivacyMode(isPrivacyMode: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.app.ability.UIExtensionContentSession.d.ts|
|新增API|NA|类名：UIExtensionContentSession；<br>API声明：startAbilityByType(type: string, wantParam: Record\<string, Object>, abilityStartCallback: AbilityStartCallback, callback: AsyncCallback\<void>): void;<br>差异内容：startAbilityByType(type: string, wantParam: Record\<string, Object>, abilityStartCallback: AbilityStartCallback, callback: AsyncCallback\<void>): void;|api/@ohos.app.ability.UIExtensionContentSession.d.ts|
|新增API|NA|类名：UIExtensionContentSession；<br>API声明：startAbilityByType(type: string, wantParam: Record\<string, Object>, abilityStartCallback: AbilityStartCallback): Promise\<void>;<br>差异内容：startAbilityByType(type: string, wantParam: Record\<string, Object>, abilityStartCallback: AbilityStartCallback): Promise\<void>;|api/@ohos.app.ability.UIExtensionContentSession.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class Want<br>差异内容：export default class Want|api/@ohos.app.ability.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：bundleName?: string;<br>差异内容：bundleName?: string;|api/@ohos.app.ability.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：abilityName?: string;<br>差异内容：abilityName?: string;|api/@ohos.app.ability.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：deviceId?: string;<br>差异内容：deviceId?: string;|api/@ohos.app.ability.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：uri?: string;<br>差异内容：uri?: string;|api/@ohos.app.ability.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：type?: string;<br>差异内容：type?: string;|api/@ohos.app.ability.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：flags?: number;<br>差异内容：flags?: number;|api/@ohos.app.ability.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：action?: string;<br>差异内容：action?: string;|api/@ohos.app.ability.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：parameters?: Record\<string, Object>;<br>差异内容：parameters?: Record\<string, Object>;|api/@ohos.app.ability.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：entities?: Array\<string>;<br>差异内容：entities?: Array\<string>;|api/@ohos.app.ability.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：moduleName?: string;<br>差异内容：moduleName?: string;|api/@ohos.app.ability.Want.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace wantAgent<br>差异内容：declare namespace wantAgent|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function getBundleName(agent: WantAgent, callback: AsyncCallback\<string>): void;<br>差异内容：function getBundleName(agent: WantAgent, callback: AsyncCallback\<string>): void;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function getBundleName(agent: WantAgent): Promise\<string>;<br>差异内容：function getBundleName(agent: WantAgent): Promise\<string>;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function getUid(agent: WantAgent, callback: AsyncCallback\<number>): void;<br>差异内容：function getUid(agent: WantAgent, callback: AsyncCallback\<number>): void;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function getUid(agent: WantAgent): Promise\<number>;<br>差异内容：function getUid(agent: WantAgent): Promise\<number>;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function cancel(agent: WantAgent, callback: AsyncCallback\<void>): void;<br>差异内容：function cancel(agent: WantAgent, callback: AsyncCallback\<void>): void;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function cancel(agent: WantAgent): Promise\<void>;<br>差异内容：function cancel(agent: WantAgent): Promise\<void>;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function trigger(agent: WantAgent, triggerInfo: TriggerInfo, callback?: AsyncCallback\<CompleteData>): void;<br>差异内容：function trigger(agent: WantAgent, triggerInfo: TriggerInfo, callback?: AsyncCallback\<CompleteData>): void;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function equal(agent: WantAgent, otherAgent: WantAgent, callback: AsyncCallback\<boolean>): void;<br>差异内容：function equal(agent: WantAgent, otherAgent: WantAgent, callback: AsyncCallback\<boolean>): void;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function equal(agent: WantAgent, otherAgent: WantAgent): Promise\<boolean>;<br>差异内容：function equal(agent: WantAgent, otherAgent: WantAgent): Promise\<boolean>;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function getWantAgent(info: WantAgentInfo, callback: AsyncCallback\<WantAgent>): void;<br>差异内容：function getWantAgent(info: WantAgentInfo, callback: AsyncCallback\<WantAgent>): void;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function getWantAgent(info: WantAgentInfo): Promise\<WantAgent>;<br>差异内容：function getWantAgent(info: WantAgentInfo): Promise\<WantAgent>;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function getOperationType(agent: WantAgent, callback: AsyncCallback\<number>): void;<br>差异内容：function getOperationType(agent: WantAgent, callback: AsyncCallback\<number>): void;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function getOperationType(agent: WantAgent): Promise\<number>;<br>差异内容：function getOperationType(agent: WantAgent): Promise\<number>;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：export enum WantAgentFlags<br>差异内容：export enum WantAgentFlags|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：ONE_TIME_FLAG = 0<br>差异内容：ONE_TIME_FLAG = 0|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：NO_BUILD_FLAG<br>差异内容：NO_BUILD_FLAG|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：CANCEL_PRESENT_FLAG<br>差异内容：CANCEL_PRESENT_FLAG|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：UPDATE_PRESENT_FLAG<br>差异内容：UPDATE_PRESENT_FLAG|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：CONSTANT_FLAG<br>差异内容：CONSTANT_FLAG|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：REPLACE_ELEMENT<br>差异内容：REPLACE_ELEMENT|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：REPLACE_ACTION<br>差异内容：REPLACE_ACTION|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：REPLACE_URI<br>差异内容：REPLACE_URI|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：REPLACE_ENTITIES<br>差异内容：REPLACE_ENTITIES|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：REPLACE_BUNDLE<br>差异内容：REPLACE_BUNDLE|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：export enum OperationType<br>差异内容：export enum OperationType|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：OperationType；<br>API声明：UNKNOWN_TYPE = 0<br>差异内容：UNKNOWN_TYPE = 0|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：OperationType；<br>API声明：START_ABILITY<br>差异内容：START_ABILITY|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：OperationType；<br>API声明：START_ABILITIES<br>差异内容：START_ABILITIES|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：OperationType；<br>API声明：START_SERVICE<br>差异内容：START_SERVICE|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：OperationType；<br>API声明：SEND_COMMON_EVENT<br>差异内容：SEND_COMMON_EVENT|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：export interface CompleteData<br>差异内容：export interface CompleteData|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：CompleteData；<br>API声明：info: WantAgent;<br>差异内容：info: WantAgent;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：CompleteData；<br>API声明：want: Want;<br>差异内容：want: Want;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：CompleteData；<br>API声明：finalCode: number;<br>差异内容：finalCode: number;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：CompleteData；<br>API声明：finalData: string;<br>差异内容：finalData: string;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：CompleteData；<br>API声明：extraInfo?: Record\<string, Object>;<br>差异内容：extraInfo?: Record\<string, Object>;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：export type TriggerInfo = _TriggerInfo;<br>差异内容：export type TriggerInfo = _TriggerInfo;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：export type WantAgentInfo = _WantAgentInfo;<br>差异内容：export type WantAgentInfo = _WantAgentInfo;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：global；<br>API声明：export type WantAgent = object;<br>差异内容：export type WantAgent = object;|api/@ohos.app.ability.wantAgent.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace wantConstant<br>差异内容：declare namespace wantConstant|api/@ohos.app.ability.wantConstant.d.ts|
|新增API|NA|类名：wantConstant；<br>API声明：export enum Params<br>差异内容：export enum Params|api/@ohos.app.ability.wantConstant.d.ts|
|新增API|NA|类名：Params；<br>API声明：ABILITY_BACK_TO_OTHER_MISSION_STACK = 'ability.params.backToOtherMissionStack'<br>差异内容：ABILITY_BACK_TO_OTHER_MISSION_STACK = 'ability.params.backToOtherMissionStack'|api/@ohos.app.ability.wantConstant.d.ts|
|新增API|NA|类名：Params；<br>API声明：ABILITY_RECOVERY_RESTART = 'ohos.ability.params.abilityRecoveryRestart'<br>差异内容：ABILITY_RECOVERY_RESTART = 'ohos.ability.params.abilityRecoveryRestart'|api/@ohos.app.ability.wantConstant.d.ts|
|新增API|NA|类名：Params；<br>API声明：CONTENT_TITLE_KEY = 'ohos.extra.param.key.contentTitle'<br>差异内容：CONTENT_TITLE_KEY = 'ohos.extra.param.key.contentTitle'|api/@ohos.app.ability.wantConstant.d.ts|
|新增API|NA|类名：Params；<br>API声明：SHARE_ABSTRACT_KEY = 'ohos.extra.param.key.shareAbstract'<br>差异内容：SHARE_ABSTRACT_KEY = 'ohos.extra.param.key.shareAbstract'|api/@ohos.app.ability.wantConstant.d.ts|
|新增API|NA|类名：Params；<br>API声明：SHARE_URL_KEY = 'ohos.extra.param.key.shareUrl'<br>差异内容：SHARE_URL_KEY = 'ohos.extra.param.key.shareUrl'|api/@ohos.app.ability.wantConstant.d.ts|
|新增API|NA|类名：Params；<br>API声明：SUPPORT_CONTINUE_PAGE_STACK_KEY = 'ohos.extra.param.key.supportContinuePageStack'<br>差异内容：SUPPORT_CONTINUE_PAGE_STACK_KEY = 'ohos.extra.param.key.supportContinuePageStack'|api/@ohos.app.ability.wantConstant.d.ts|
|新增API|NA|类名：Params；<br>API声明：SUPPORT_CONTINUE_SOURCE_EXIT_KEY = 'ohos.extra.param.key.supportContinueSourceExit'<br>差异内容：SUPPORT_CONTINUE_SOURCE_EXIT_KEY = 'ohos.extra.param.key.supportContinueSourceExit'|api/@ohos.app.ability.wantConstant.d.ts|
|新增API|NA|类名：wantConstant；<br>API声明：export enum Flags<br>差异内容：export enum Flags|api/@ohos.app.ability.wantConstant.d.ts|
|新增API|NA|类名：Flags；<br>API声明：FLAG_AUTH_READ_URI_PERMISSION = 0x00000001<br>差异内容：FLAG_AUTH_READ_URI_PERMISSION = 0x00000001|api/@ohos.app.ability.wantConstant.d.ts|
|新增API|NA|类名：Flags；<br>API声明：FLAG_AUTH_WRITE_URI_PERMISSION = 0x00000002<br>差异内容：FLAG_AUTH_WRITE_URI_PERMISSION = 0x00000002|api/@ohos.app.ability.wantConstant.d.ts|
|新增API|NA|类名：Flags；<br>API声明：FLAG_INSTALL_ON_DEMAND = 0x00000800<br>差异内容：FLAG_INSTALL_ON_DEMAND = 0x00000800|api/@ohos.app.ability.wantConstant.d.ts|
|新增API|NA|类名：Flags；<br>API声明：FLAG_START_WITHOUT_TIPS = 0x40000000<br>差异内容：FLAG_START_WITHOUT_TIPS = 0x40000000|api/@ohos.app.ability.wantConstant.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace appManager<br>差异内容：declare namespace appManager|api/@ohos.application.appManager.d.ts|
|新增API|NA|类名：appManager；<br>API声明：function isRunningInStabilityTest(callback: AsyncCallback\<boolean>): void;<br>差异内容：function isRunningInStabilityTest(callback: AsyncCallback\<boolean>): void;|api/@ohos.application.appManager.d.ts|
|新增API|NA|类名：appManager；<br>API声明：function isRunningInStabilityTest(): Promise\<boolean>;<br>差异内容：function isRunningInStabilityTest(): Promise\<boolean>;|api/@ohos.application.appManager.d.ts|
|新增API|NA|类名：appManager；<br>API声明：function getProcessRunningInfos(): Promise\<Array\<ProcessRunningInfo>>;<br>差异内容：function getProcessRunningInfos(): Promise\<Array\<ProcessRunningInfo>>;|api/@ohos.application.appManager.d.ts|
|新增API|NA|类名：appManager；<br>API声明：function getProcessRunningInfos(callback: AsyncCallback\<Array\<ProcessRunningInfo>>): void;<br>差异内容：function getProcessRunningInfos(callback: AsyncCallback\<Array\<ProcessRunningInfo>>): void;|api/@ohos.application.appManager.d.ts|
|新增API|NA|类名：appManager；<br>API声明：function isRamConstrainedDevice(): Promise\<boolean>;<br>差异内容：function isRamConstrainedDevice(): Promise\<boolean>;|api/@ohos.application.appManager.d.ts|
|新增API|NA|类名：appManager；<br>API声明：function isRamConstrainedDevice(callback: AsyncCallback\<boolean>): void;<br>差异内容：function isRamConstrainedDevice(callback: AsyncCallback\<boolean>): void;|api/@ohos.application.appManager.d.ts|
|新增API|NA|类名：appManager；<br>API声明：function getAppMemorySize(): Promise\<number>;<br>差异内容：function getAppMemorySize(): Promise\<number>;|api/@ohos.application.appManager.d.ts|
|新增API|NA|类名：appManager；<br>API声明：function getAppMemorySize(callback: AsyncCallback\<number>): void;<br>差异内容：function getAppMemorySize(callback: AsyncCallback\<number>): void;|api/@ohos.application.appManager.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Configuration<br>差异内容：export interface Configuration|api/@ohos.application.Configuration.d.ts|
|新增API|NA|类名：Configuration；<br>API声明：language?: string;<br>差异内容：language?: string;|api/@ohos.application.Configuration.d.ts|
|新增API|NA|类名：Configuration；<br>API声明：colorMode?: ConfigurationConstant.ColorMode;<br>差异内容：colorMode?: ConfigurationConstant.ColorMode;|api/@ohos.application.Configuration.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace ConfigurationConstant<br>差异内容：declare namespace ConfigurationConstant|api/@ohos.application.ConfigurationConstant.d.ts|
|新增API|NA|类名：ConfigurationConstant；<br>API声明：export enum ColorMode<br>差异内容：export enum ColorMode|api/@ohos.application.ConfigurationConstant.d.ts|
|新增API|NA|类名：ColorMode；<br>API声明：COLOR_MODE_NOT_SET = -1<br>差异内容：COLOR_MODE_NOT_SET = -1|api/@ohos.application.ConfigurationConstant.d.ts|
|新增API|NA|类名：ColorMode；<br>API声明：COLOR_MODE_DARK = 0<br>差异内容：COLOR_MODE_DARK = 0|api/@ohos.application.ConfigurationConstant.d.ts|
|新增API|NA|类名：ColorMode；<br>API声明：COLOR_MODE_LIGHT = 1<br>差异内容：COLOR_MODE_LIGHT = 1|api/@ohos.application.ConfigurationConstant.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace uriPermissionManager<br>差异内容：declare namespace uriPermissionManager|api/@ohos.application.uriPermissionManager.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class Want<br>差异内容：export default class Want|api/@ohos.application.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：deviceId?: string;<br>差异内容：deviceId?: string;|api/@ohos.application.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：bundleName?: string;<br>差异内容：bundleName?: string;|api/@ohos.application.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：abilityName?: string;<br>差异内容：abilityName?: string;|api/@ohos.application.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：uri?: string;<br>差异内容：uri?: string;|api/@ohos.application.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：type?: string;<br>差异内容：type?: string;|api/@ohos.application.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：flags?: number;<br>差异内容：flags?: number;|api/@ohos.application.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：action?: string;<br>差异内容：action?: string;|api/@ohos.application.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：parameters?: {<br>        [key: string]: any;<br>    };<br>差异内容：parameters?: {<br>        [key: string]: any;<br>    };|api/@ohos.application.Want.d.ts|
|新增API|NA|类名：Want；<br>API声明：entities?: Array\<string>;<br>差异内容：entities?: Array\<string>;|api/@ohos.application.Want.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace bundleManager<br>差异内容：declare namespace bundleManager|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：enum BundleFlag<br>差异内容：enum BundleFlag|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_BUNDLE_INFO_DEFAULT = 0x00000000<br>差异内容：GET_BUNDLE_INFO_DEFAULT = 0x00000000|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_BUNDLE_INFO_WITH_APPLICATION = 0x00000001<br>差异内容：GET_BUNDLE_INFO_WITH_APPLICATION = 0x00000001|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_BUNDLE_INFO_WITH_HAP_MODULE = 0x00000002<br>差异内容：GET_BUNDLE_INFO_WITH_HAP_MODULE = 0x00000002|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_BUNDLE_INFO_WITH_ABILITY = 0x00000004<br>差异内容：GET_BUNDLE_INFO_WITH_ABILITY = 0x00000004|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY = 0x00000008<br>差异内容：GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY = 0x00000008|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION = 0x00000010<br>差异内容：GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION = 0x00000010|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_BUNDLE_INFO_WITH_METADATA = 0x00000020<br>差异内容：GET_BUNDLE_INFO_WITH_METADATA = 0x00000020|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_BUNDLE_INFO_WITH_DISABLE = 0x00000040<br>差异内容：GET_BUNDLE_INFO_WITH_DISABLE = 0x00000040|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_BUNDLE_INFO_WITH_SIGNATURE_INFO = 0x00000080<br>差异内容：GET_BUNDLE_INFO_WITH_SIGNATURE_INFO = 0x00000080|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_BUNDLE_INFO_WITH_MENU = 0x00000100<br>差异内容：GET_BUNDLE_INFO_WITH_MENU = 0x00000100|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export enum ExtensionAbilityType<br>差异内容：export enum ExtensionAbilityType|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：FORM = 0<br>差异内容：FORM = 0|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：WORK_SCHEDULER = 1<br>差异内容：WORK_SCHEDULER = 1|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：INPUT_METHOD = 2<br>差异内容：INPUT_METHOD = 2|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：SERVICE = 3<br>差异内容：SERVICE = 3|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：ACCESSIBILITY = 4<br>差异内容：ACCESSIBILITY = 4|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：DATA_SHARE = 5<br>差异内容：DATA_SHARE = 5|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：FILE_SHARE = 6<br>差异内容：FILE_SHARE = 6|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：STATIC_SUBSCRIBER = 7<br>差异内容：STATIC_SUBSCRIBER = 7|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：WALLPAPER = 8<br>差异内容：WALLPAPER = 8|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：BACKUP = 9<br>差异内容：BACKUP = 9|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：WINDOW = 10<br>差异内容：WINDOW = 10|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：ENTERPRISE_ADMIN = 11<br>差异内容：ENTERPRISE_ADMIN = 11|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：THUMBNAIL = 13<br>差异内容：THUMBNAIL = 13|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：PREVIEW = 14<br>差异内容：PREVIEW = 14|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：PRINT = 15<br>差异内容：PRINT = 15|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：SHARE = 16<br>差异内容：SHARE = 16|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：PUSH = 17<br>差异内容：PUSH = 17|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：DRIVER = 18<br>差异内容：DRIVER = 18|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：ACTION = 19<br>差异内容：ACTION = 19|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：ADS_SERVICE = 20<br>差异内容：ADS_SERVICE = 20|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ExtensionAbilityType；<br>API声明：UNSPECIFIED = 255<br>差异内容：UNSPECIFIED = 255|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export enum PermissionGrantState<br>差异内容：export enum PermissionGrantState|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：PermissionGrantState；<br>API声明：PERMISSION_DENIED = -1<br>差异内容：PERMISSION_DENIED = -1|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：PermissionGrantState；<br>API声明：PERMISSION_GRANTED = 0<br>差异内容：PERMISSION_GRANTED = 0|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export enum SupportWindowMode<br>差异内容：export enum SupportWindowMode|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：SupportWindowMode；<br>API声明：FULL_SCREEN = 0<br>差异内容：FULL_SCREEN = 0|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：SupportWindowMode；<br>API声明：SPLIT = 1<br>差异内容：SPLIT = 1|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：SupportWindowMode；<br>API声明：FLOATING = 2<br>差异内容：FLOATING = 2|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export enum LaunchType<br>差异内容：export enum LaunchType|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：LaunchType；<br>API声明：SINGLETON = 0<br>差异内容：SINGLETON = 0|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：LaunchType；<br>API声明：MULTITON = 1<br>差异内容：MULTITON = 1|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：LaunchType；<br>API声明：SPECIFIED = 2<br>差异内容：SPECIFIED = 2|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export enum AbilityType<br>差异内容：export enum AbilityType|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：AbilityType；<br>API声明：PAGE = 1<br>差异内容：PAGE = 1|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：AbilityType；<br>API声明：SERVICE = 2<br>差异内容：SERVICE = 2|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：AbilityType；<br>API声明：DATA = 3<br>差异内容：DATA = 3|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export enum DisplayOrientation<br>差异内容：export enum DisplayOrientation|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：DisplayOrientation；<br>API声明：UNSPECIFIED<br>差异内容：UNSPECIFIED|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：DisplayOrientation；<br>API声明：LANDSCAPE<br>差异内容：LANDSCAPE|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：DisplayOrientation；<br>API声明：PORTRAIT<br>差异内容：PORTRAIT|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：DisplayOrientation；<br>API声明：FOLLOW_RECENT<br>差异内容：FOLLOW_RECENT|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：DisplayOrientation；<br>API声明：LANDSCAPE_INVERTED<br>差异内容：LANDSCAPE_INVERTED|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：DisplayOrientation；<br>API声明：PORTRAIT_INVERTED<br>差异内容：PORTRAIT_INVERTED|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：DisplayOrientation；<br>API声明：AUTO_ROTATION<br>差异内容：AUTO_ROTATION|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：DisplayOrientation；<br>API声明：AUTO_ROTATION_LANDSCAPE<br>差异内容：AUTO_ROTATION_LANDSCAPE|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：DisplayOrientation；<br>API声明：AUTO_ROTATION_PORTRAIT<br>差异内容：AUTO_ROTATION_PORTRAIT|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：DisplayOrientation；<br>API声明：AUTO_ROTATION_RESTRICTED<br>差异内容：AUTO_ROTATION_RESTRICTED|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：DisplayOrientation；<br>API声明：AUTO_ROTATION_LANDSCAPE_RESTRICTED<br>差异内容：AUTO_ROTATION_LANDSCAPE_RESTRICTED|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：DisplayOrientation；<br>API声明：AUTO_ROTATION_PORTRAIT_RESTRICTED<br>差异内容：AUTO_ROTATION_PORTRAIT_RESTRICTED|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：DisplayOrientation；<br>API声明：LOCKED<br>差异内容：LOCKED|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export enum ModuleType<br>差异内容：export enum ModuleType|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ModuleType；<br>API声明：ENTRY = 1<br>差异内容：ENTRY = 1|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ModuleType；<br>API声明：FEATURE = 2<br>差异内容：FEATURE = 2|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：ModuleType；<br>API声明：SHARED = 3<br>差异内容：SHARED = 3|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export enum BundleType<br>差异内容：export enum BundleType|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：BundleType；<br>API声明：APP = 0<br>差异内容：APP = 0|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：BundleType；<br>API声明：ATOMIC_SERVICE = 1<br>差异内容：ATOMIC_SERVICE = 1|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export enum CompatiblePolicy<br>差异内容：export enum CompatiblePolicy|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：CompatiblePolicy；<br>API声明：BACKWARD_COMPATIBILITY = 1<br>差异内容：BACKWARD_COMPATIBILITY = 1|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function getBundleInfoForSelf(bundleFlags: number): Promise\<BundleInfo>;<br>差异内容：function getBundleInfoForSelf(bundleFlags: number): Promise\<BundleInfo>;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function getBundleInfoForSelf(bundleFlags: number, callback: AsyncCallback\<BundleInfo>): void;<br>差异内容：function getBundleInfoForSelf(bundleFlags: number, callback: AsyncCallback\<BundleInfo>): void;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function getBundleInfoForSelfSync(bundleFlags: number): BundleInfo;<br>差异内容：function getBundleInfoForSelfSync(bundleFlags: number): BundleInfo;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function getProfileByAbility(moduleName: string, abilityName: string, metadataName: string, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：function getProfileByAbility(moduleName: string, abilityName: string, metadataName: string, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function getProfileByAbility(moduleName: string, abilityName: string, metadataName?: string): Promise\<Array\<string>>;<br>差异内容：function getProfileByAbility(moduleName: string, abilityName: string, metadataName?: string): Promise\<Array\<string>>;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function getProfileByAbilitySync(moduleName: string, abilityName: string, metadataName?: string): Array\<string>;<br>差异内容：function getProfileByAbilitySync(moduleName: string, abilityName: string, metadataName?: string): Array\<string>;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function getProfileByExtensionAbility(moduleName: string, extensionAbilityName: string, metadataName: string, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：function getProfileByExtensionAbility(moduleName: string, extensionAbilityName: string, metadataName: string, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function getProfileByExtensionAbility(moduleName: string, extensionAbilityName: string, metadataName?: string): Promise\<Array\<string>>;<br>差异内容：function getProfileByExtensionAbility(moduleName: string, extensionAbilityName: string, metadataName?: string): Promise\<Array\<string>>;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function getProfileByExtensionAbilitySync(moduleName: string, extensionAbilityName: string, metadataName?: string): Array\<string>;<br>差异内容：function getProfileByExtensionAbilitySync(moduleName: string, extensionAbilityName: string, metadataName?: string): Array\<string>;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function verifyAbc(abcPaths: Array\<string>, deleteOriginalFiles: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：function verifyAbc(abcPaths: Array\<string>, deleteOriginalFiles: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function verifyAbc(abcPaths: Array\<string>, deleteOriginalFiles: boolean): Promise\<void>;<br>差异内容：function verifyAbc(abcPaths: Array\<string>, deleteOriginalFiles: boolean): Promise\<void>;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function deleteAbc(abcPath: string): Promise\<void>;<br>差异内容：function deleteAbc(abcPath: string): Promise\<void>;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export type ApplicationInfo = _ApplicationInfo;<br>差异内容：export type ApplicationInfo = _ApplicationInfo;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export type ModuleMetadata = _ModuleMetadata;<br>差异内容：export type ModuleMetadata = _ModuleMetadata;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export type Metadata = _Metadata;<br>差异内容：export type Metadata = _Metadata;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export type BundleInfo = _BundleInfo.BundleInfo;<br>差异内容：export type BundleInfo = _BundleInfo.BundleInfo;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export type UsedScene = _BundleInfo.UsedScene;<br>差异内容：export type UsedScene = _BundleInfo.UsedScene;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export type ReqPermissionDetail = _BundleInfo.ReqPermissionDetail;<br>差异内容：export type ReqPermissionDetail = _BundleInfo.ReqPermissionDetail;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export type SignatureInfo = _BundleInfo.SignatureInfo;<br>差异内容：export type SignatureInfo = _BundleInfo.SignatureInfo;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export type HapModuleInfo = _HapModuleInfo.HapModuleInfo;<br>差异内容：export type HapModuleInfo = _HapModuleInfo.HapModuleInfo;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export type PreloadItem = _HapModuleInfo.PreloadItem;<br>差异内容：export type PreloadItem = _HapModuleInfo.PreloadItem;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export type Dependency = _HapModuleInfo.Dependency;<br>差异内容：export type Dependency = _HapModuleInfo.Dependency;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export type AbilityInfo = _AbilityInfo.AbilityInfo;<br>差异内容：export type AbilityInfo = _AbilityInfo.AbilityInfo;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export type WindowSize = _AbilityInfo.WindowSize;<br>差异内容：export type WindowSize = _AbilityInfo.WindowSize;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export type ExtensionAbilityInfo = _ExtensionAbilityInfo.ExtensionAbilityInfo;<br>差异内容：export type ExtensionAbilityInfo = _ExtensionAbilityInfo.ExtensionAbilityInfo;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：export type ElementName = _ElementName;<br>差异内容：export type ElementName = _ElementName;|api/@ohos.bundle.bundleManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace bundle<br>差异内容：declare namespace bundle|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：enum BundleFlag<br>差异内容：enum BundleFlag|api/@ohos.bundle.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_BUNDLE_DEFAULT = 0x00000000<br>差异内容：GET_BUNDLE_DEFAULT = 0x00000000|api/@ohos.bundle.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_BUNDLE_WITH_ABILITIES = 0x00000001<br>差异内容：GET_BUNDLE_WITH_ABILITIES = 0x00000001|api/@ohos.bundle.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_ABILITY_INFO_WITH_PERMISSION = 0x00000002<br>差异内容：GET_ABILITY_INFO_WITH_PERMISSION = 0x00000002|api/@ohos.bundle.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_ABILITY_INFO_WITH_APPLICATION = 0x00000004<br>差异内容：GET_ABILITY_INFO_WITH_APPLICATION = 0x00000004|api/@ohos.bundle.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_APPLICATION_INFO_WITH_PERMISSION = 0x00000008<br>差异内容：GET_APPLICATION_INFO_WITH_PERMISSION = 0x00000008|api/@ohos.bundle.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_BUNDLE_WITH_REQUESTED_PERMISSION = 0x00000010<br>差异内容：GET_BUNDLE_WITH_REQUESTED_PERMISSION = 0x00000010|api/@ohos.bundle.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_ALL_APPLICATION_INFO = 0xFFFF0000<br>差异内容：GET_ALL_APPLICATION_INFO = 0xFFFF0000|api/@ohos.bundle.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_ABILITY_INFO_WITH_METADATA = 0x00000020<br>差异内容：GET_ABILITY_INFO_WITH_METADATA = 0x00000020|api/@ohos.bundle.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_APPLICATION_INFO_WITH_METADATA = 0x00000040<br>差异内容：GET_APPLICATION_INFO_WITH_METADATA = 0x00000040|api/@ohos.bundle.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_ABILITY_INFO_SYSTEMAPP_ONLY = 0x00000080<br>差异内容：GET_ABILITY_INFO_SYSTEMAPP_ONLY = 0x00000080|api/@ohos.bundle.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_ABILITY_INFO_WITH_DISABLE = 0x00000100<br>差异内容：GET_ABILITY_INFO_WITH_DISABLE = 0x00000100|api/@ohos.bundle.d.ts|
|新增API|NA|类名：BundleFlag；<br>API声明：GET_APPLICATION_INFO_WITH_DISABLE = 0x00000200<br>差异内容：GET_APPLICATION_INFO_WITH_DISABLE = 0x00000200|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：export enum ColorMode<br>差异内容：export enum ColorMode|api/@ohos.bundle.d.ts|
|新增API|NA|类名：ColorMode；<br>API声明：AUTO_MODE = -1<br>差异内容：AUTO_MODE = -1|api/@ohos.bundle.d.ts|
|新增API|NA|类名：ColorMode；<br>API声明：DARK_MODE = 0<br>差异内容：DARK_MODE = 0|api/@ohos.bundle.d.ts|
|新增API|NA|类名：ColorMode；<br>API声明：LIGHT_MODE = 1<br>差异内容：LIGHT_MODE = 1|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：export enum GrantStatus<br>差异内容：export enum GrantStatus|api/@ohos.bundle.d.ts|
|新增API|NA|类名：GrantStatus；<br>API声明：PERMISSION_DENIED = -1<br>差异内容：PERMISSION_DENIED = -1|api/@ohos.bundle.d.ts|
|新增API|NA|类名：GrantStatus；<br>API声明：PERMISSION_GRANTED = 0<br>差异内容：PERMISSION_GRANTED = 0|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：export enum AbilityType<br>差异内容：export enum AbilityType|api/@ohos.bundle.d.ts|
|新增API|NA|类名：AbilityType；<br>API声明：UNKNOWN<br>差异内容：UNKNOWN|api/@ohos.bundle.d.ts|
|新增API|NA|类名：AbilityType；<br>API声明：PAGE<br>差异内容：PAGE|api/@ohos.bundle.d.ts|
|新增API|NA|类名：AbilityType；<br>API声明：SERVICE<br>差异内容：SERVICE|api/@ohos.bundle.d.ts|
|新增API|NA|类名：AbilityType；<br>API声明：DATA<br>差异内容：DATA|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：export enum AbilitySubType<br>差异内容：export enum AbilitySubType|api/@ohos.bundle.d.ts|
|新增API|NA|类名：AbilitySubType；<br>API声明：UNSPECIFIED = 0<br>差异内容：UNSPECIFIED = 0|api/@ohos.bundle.d.ts|
|新增API|NA|类名：AbilitySubType；<br>API声明：CA = 1<br>差异内容：CA = 1|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：export enum DisplayOrientation<br>差异内容：export enum DisplayOrientation|api/@ohos.bundle.d.ts|
|新增API|NA|类名：DisplayOrientation；<br>API声明：UNSPECIFIED<br>差异内容：UNSPECIFIED|api/@ohos.bundle.d.ts|
|新增API|NA|类名：DisplayOrientation；<br>API声明：LANDSCAPE<br>差异内容：LANDSCAPE|api/@ohos.bundle.d.ts|
|新增API|NA|类名：DisplayOrientation；<br>API声明：PORTRAIT<br>差异内容：PORTRAIT|api/@ohos.bundle.d.ts|
|新增API|NA|类名：DisplayOrientation；<br>API声明：FOLLOW_RECENT<br>差异内容：FOLLOW_RECENT|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：export enum LaunchMode<br>差异内容：export enum LaunchMode|api/@ohos.bundle.d.ts|
|新增API|NA|类名：LaunchMode；<br>API声明：SINGLETON = 0<br>差异内容：SINGLETON = 0|api/@ohos.bundle.d.ts|
|新增API|NA|类名：LaunchMode；<br>API声明：STANDARD = 1<br>差异内容：STANDARD = 1|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：export interface BundleOptions<br>差异内容：export interface BundleOptions|api/@ohos.bundle.d.ts|
|新增API|NA|类名：BundleOptions；<br>API声明：userId?: number;<br>差异内容：userId?: number;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：export enum InstallErrorCode<br>差异内容：export enum InstallErrorCode|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：SUCCESS = 0<br>差异内容：SUCCESS = 0|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_INSTALL_FAILURE = 1<br>差异内容：STATUS_INSTALL_FAILURE = 1|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_INSTALL_FAILURE_ABORTED = 2<br>差异内容：STATUS_INSTALL_FAILURE_ABORTED = 2|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_INSTALL_FAILURE_INVALID = 3<br>差异内容：STATUS_INSTALL_FAILURE_INVALID = 3|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_INSTALL_FAILURE_CONFLICT = 4<br>差异内容：STATUS_INSTALL_FAILURE_CONFLICT = 4|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_INSTALL_FAILURE_STORAGE = 5<br>差异内容：STATUS_INSTALL_FAILURE_STORAGE = 5|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_INSTALL_FAILURE_INCOMPATIBLE = 6<br>差异内容：STATUS_INSTALL_FAILURE_INCOMPATIBLE = 6|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_UNINSTALL_FAILURE = 7<br>差异内容：STATUS_UNINSTALL_FAILURE = 7|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_UNINSTALL_FAILURE_BLOCKED = 8<br>差异内容：STATUS_UNINSTALL_FAILURE_BLOCKED = 8|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_UNINSTALL_FAILURE_ABORTED = 9<br>差异内容：STATUS_UNINSTALL_FAILURE_ABORTED = 9|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_UNINSTALL_FAILURE_CONFLICT = 10<br>差异内容：STATUS_UNINSTALL_FAILURE_CONFLICT = 10|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_INSTALL_FAILURE_DOWNLOAD_TIMEOUT = 0x0B<br>差异内容：STATUS_INSTALL_FAILURE_DOWNLOAD_TIMEOUT = 0x0B|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_INSTALL_FAILURE_DOWNLOAD_FAILED = 0x0C<br>差异内容：STATUS_INSTALL_FAILURE_DOWNLOAD_FAILED = 0x0C|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_RECOVER_FAILURE_INVALID = 0x0D<br>差异内容：STATUS_RECOVER_FAILURE_INVALID = 0x0D|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_ABILITY_NOT_FOUND = 0x40<br>差异内容：STATUS_ABILITY_NOT_FOUND = 0x40|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_BMS_SERVICE_ERROR = 0x41<br>差异内容：STATUS_BMS_SERVICE_ERROR = 0x41|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_FAILED_NO_SPACE_LEFT = 0x42<br>差异内容：STATUS_FAILED_NO_SPACE_LEFT = 0x42|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_GRANT_REQUEST_PERMISSIONS_FAILED = 0x43<br>差异内容：STATUS_GRANT_REQUEST_PERMISSIONS_FAILED = 0x43|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_INSTALL_PERMISSION_DENIED = 0x44<br>差异内容：STATUS_INSTALL_PERMISSION_DENIED = 0x44|api/@ohos.bundle.d.ts|
|新增API|NA|类名：InstallErrorCode；<br>API声明：STATUS_UNINSTALL_PERMISSION_DENIED = 0x45<br>差异内容：STATUS_UNINSTALL_PERMISSION_DENIED = 0x45|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getBundleInfo(bundleName: string, bundleFlags: number, options: BundleOptions, callback: AsyncCallback\<BundleInfo>): void;<br>差异内容：function getBundleInfo(bundleName: string, bundleFlags: number, options: BundleOptions, callback: AsyncCallback\<BundleInfo>): void;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getBundleInfo(bundleName: string, bundleFlags: number, callback: AsyncCallback\<BundleInfo>): void;<br>差异内容：function getBundleInfo(bundleName: string, bundleFlags: number, callback: AsyncCallback\<BundleInfo>): void;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getBundleInfo(bundleName: string, bundleFlags: number, options?: BundleOptions): Promise\<BundleInfo>;<br>差异内容：function getBundleInfo(bundleName: string, bundleFlags: number, options?: BundleOptions): Promise\<BundleInfo>;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getAbilityInfo(bundleName: string, abilityName: string, callback: AsyncCallback\<AbilityInfo>): void;<br>差异内容：function getAbilityInfo(bundleName: string, abilityName: string, callback: AsyncCallback\<AbilityInfo>): void;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getAbilityInfo(bundleName: string, abilityName: string): Promise\<AbilityInfo>;<br>差异内容：function getAbilityInfo(bundleName: string, abilityName: string): Promise\<AbilityInfo>;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getApplicationInfo(bundleName: string, bundleFlags: number, userId: number, callback: AsyncCallback\<ApplicationInfo>): void;<br>差异内容：function getApplicationInfo(bundleName: string, bundleFlags: number, userId: number, callback: AsyncCallback\<ApplicationInfo>): void;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getApplicationInfo(bundleName: string, bundleFlags: number, callback: AsyncCallback\<ApplicationInfo>): void;<br>差异内容：function getApplicationInfo(bundleName: string, bundleFlags: number, callback: AsyncCallback\<ApplicationInfo>): void;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getApplicationInfo(bundleName: string, bundleFlags: number, userId?: number): Promise\<ApplicationInfo>;<br>差异内容：function getApplicationInfo(bundleName: string, bundleFlags: number, userId?: number): Promise\<ApplicationInfo>;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function queryAbilityByWant(want: Want, bundleFlags: number, userId: number, callback: AsyncCallback\<Array\<AbilityInfo>>): void;<br>差异内容：function queryAbilityByWant(want: Want, bundleFlags: number, userId: number, callback: AsyncCallback\<Array\<AbilityInfo>>): void;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function queryAbilityByWant(want: Want, bundleFlags: number, callback: AsyncCallback\<Array\<AbilityInfo>>): void;<br>差异内容：function queryAbilityByWant(want: Want, bundleFlags: number, callback: AsyncCallback\<Array\<AbilityInfo>>): void;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function queryAbilityByWant(want: Want, bundleFlags: number, userId?: number): Promise\<Array\<AbilityInfo>>;<br>差异内容：function queryAbilityByWant(want: Want, bundleFlags: number, userId?: number): Promise\<Array\<AbilityInfo>>;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getAllBundleInfo(bundleFlag: BundleFlag, userId: number, callback: AsyncCallback\<Array\<BundleInfo>>): void;<br>差异内容：function getAllBundleInfo(bundleFlag: BundleFlag, userId: number, callback: AsyncCallback\<Array\<BundleInfo>>): void;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getAllBundleInfo(bundleFlag: BundleFlag, callback: AsyncCallback\<Array\<BundleInfo>>): void;<br>差异内容：function getAllBundleInfo(bundleFlag: BundleFlag, callback: AsyncCallback\<Array\<BundleInfo>>): void;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getAllBundleInfo(bundleFlag: BundleFlag, userId?: number): Promise\<Array\<BundleInfo>>;<br>差异内容：function getAllBundleInfo(bundleFlag: BundleFlag, userId?: number): Promise\<Array\<BundleInfo>>;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getAllApplicationInfo(bundleFlags: number, userId: number, callback: AsyncCallback\<Array\<ApplicationInfo>>): void;<br>差异内容：function getAllApplicationInfo(bundleFlags: number, userId: number, callback: AsyncCallback\<Array\<ApplicationInfo>>): void;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getAllApplicationInfo(bundleFlags: number, callback: AsyncCallback\<Array\<ApplicationInfo>>): void;<br>差异内容：function getAllApplicationInfo(bundleFlags: number, callback: AsyncCallback\<Array\<ApplicationInfo>>): void;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getAllApplicationInfo(bundleFlags: number, userId?: number): Promise\<Array\<ApplicationInfo>>;<br>差异内容：function getAllApplicationInfo(bundleFlags: number, userId?: number): Promise\<Array\<ApplicationInfo>>;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getNameForUid(uid: number, callback: AsyncCallback\<string>): void;<br>差异内容：function getNameForUid(uid: number, callback: AsyncCallback\<string>): void;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getNameForUid(uid: number): Promise\<string>;<br>差异内容：function getNameForUid(uid: number): Promise\<string>;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getBundleArchiveInfo(hapFilePath: string, bundleFlags: number, callback: AsyncCallback\<BundleInfo>): void;<br>差异内容：function getBundleArchiveInfo(hapFilePath: string, bundleFlags: number, callback: AsyncCallback\<BundleInfo>): void;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getBundleArchiveInfo(hapFilePath: string, bundleFlags: number): Promise\<BundleInfo>;<br>差异内容：function getBundleArchiveInfo(hapFilePath: string, bundleFlags: number): Promise\<BundleInfo>;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getLaunchWantForBundle(bundleName: string, callback: AsyncCallback\<Want>): void;<br>差异内容：function getLaunchWantForBundle(bundleName: string, callback: AsyncCallback\<Want>): void;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getLaunchWantForBundle(bundleName: string): Promise\<Want>;<br>差异内容：function getLaunchWantForBundle(bundleName: string): Promise\<Want>;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getAbilityLabel(bundleName: string, abilityName: string, callback: AsyncCallback\<string>): void;<br>差异内容：function getAbilityLabel(bundleName: string, abilityName: string, callback: AsyncCallback\<string>): void;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getAbilityLabel(bundleName: string, abilityName: string): Promise\<string>;<br>差异内容：function getAbilityLabel(bundleName: string, abilityName: string): Promise\<string>;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getAbilityIcon(bundleName: string, abilityName: string, callback: AsyncCallback\<image.PixelMap>): void;<br>差异内容：function getAbilityIcon(bundleName: string, abilityName: string, callback: AsyncCallback\<image.PixelMap>): void;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function getAbilityIcon(bundleName: string, abilityName: string): Promise\<image.PixelMap>;<br>差异内容：function getAbilityIcon(bundleName: string, abilityName: string): Promise\<image.PixelMap>;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function isAbilityEnabled(info: AbilityInfo, callback: AsyncCallback\<boolean>): void;<br>差异内容：function isAbilityEnabled(info: AbilityInfo, callback: AsyncCallback\<boolean>): void;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function isAbilityEnabled(info: AbilityInfo): Promise\<boolean>;<br>差异内容：function isAbilityEnabled(info: AbilityInfo): Promise\<boolean>;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function isApplicationEnabled(bundleName: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：function isApplicationEnabled(bundleName: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：bundle；<br>API声明：function isApplicationEnabled(bundleName: string): Promise\<boolean>;<br>差异内容：function isApplicationEnabled(bundleName: string): Promise\<boolean>;|api/@ohos.bundle.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace defaultAppManager<br>差异内容：declare namespace defaultAppManager|api/@ohos.bundle.defaultAppManager.d.ts|
|新增API|NA|类名：defaultAppManager；<br>API声明：export enum ApplicationType<br>差异内容：export enum ApplicationType|api/@ohos.bundle.defaultAppManager.d.ts|
|新增API|NA|类名：ApplicationType；<br>API声明：BROWSER = 'Web Browser'<br>差异内容：BROWSER = 'Web Browser'|api/@ohos.bundle.defaultAppManager.d.ts|
|新增API|NA|类名：ApplicationType；<br>API声明：IMAGE = 'Image Gallery'<br>差异内容：IMAGE = 'Image Gallery'|api/@ohos.bundle.defaultAppManager.d.ts|
|新增API|NA|类名：ApplicationType；<br>API声明：AUDIO = 'Audio Player'<br>差异内容：AUDIO = 'Audio Player'|api/@ohos.bundle.defaultAppManager.d.ts|
|新增API|NA|类名：ApplicationType；<br>API声明：VIDEO = 'Video Player'<br>差异内容：VIDEO = 'Video Player'|api/@ohos.bundle.defaultAppManager.d.ts|
|新增API|NA|类名：ApplicationType；<br>API声明：PDF = 'PDF Viewer'<br>差异内容：PDF = 'PDF Viewer'|api/@ohos.bundle.defaultAppManager.d.ts|
|新增API|NA|类名：ApplicationType；<br>API声明：WORD = 'Word Viewer'<br>差异内容：WORD = 'Word Viewer'|api/@ohos.bundle.defaultAppManager.d.ts|
|新增API|NA|类名：ApplicationType；<br>API声明：EXCEL = 'Excel Viewer'<br>差异内容：EXCEL = 'Excel Viewer'|api/@ohos.bundle.defaultAppManager.d.ts|
|新增API|NA|类名：ApplicationType；<br>API声明：PPT = 'PPT Viewer'<br>差异内容：PPT = 'PPT Viewer'|api/@ohos.bundle.defaultAppManager.d.ts|
|新增API|NA|类名：defaultAppManager；<br>API声明：function isDefaultApplication(type: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：function isDefaultApplication(type: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.bundle.defaultAppManager.d.ts|
|新增API|NA|类名：defaultAppManager；<br>API声明：function isDefaultApplication(type: string): Promise\<boolean>;<br>差异内容：function isDefaultApplication(type: string): Promise\<boolean>;|api/@ohos.bundle.defaultAppManager.d.ts|
|新增API|NA|类名：defaultAppManager；<br>API声明：function isDefaultApplicationSync(type: string): boolean;<br>差异内容：function isDefaultApplicationSync(type: string): boolean;|api/@ohos.bundle.defaultAppManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace overlay<br>差异内容：declare namespace overlay|api/@ohos.bundle.overlay.d.ts|
|新增API|NA|类名：overlay；<br>API声明：function setOverlayEnabled(moduleName: string, isEnabled: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：function setOverlayEnabled(moduleName: string, isEnabled: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.bundle.overlay.d.ts|
|新增API|NA|类名：overlay；<br>API声明：function setOverlayEnabled(moduleName: string, isEnabled: boolean): Promise\<void>;<br>差异内容：function setOverlayEnabled(moduleName: string, isEnabled: boolean): Promise\<void>;|api/@ohos.bundle.overlay.d.ts|
|新增API|NA|类名：overlay；<br>API声明：function getOverlayModuleInfo(moduleName: string, callback: AsyncCallback\<OverlayModuleInfo>): void;<br>差异内容：function getOverlayModuleInfo(moduleName: string, callback: AsyncCallback\<OverlayModuleInfo>): void;|api/@ohos.bundle.overlay.d.ts|
|新增API|NA|类名：overlay；<br>API声明：function getOverlayModuleInfo(moduleName: string): Promise\<OverlayModuleInfo>;<br>差异内容：function getOverlayModuleInfo(moduleName: string): Promise\<OverlayModuleInfo>;|api/@ohos.bundle.overlay.d.ts|
|新增API|NA|类名：overlay；<br>API声明：function getTargetOverlayModuleInfos(targetModuleName: string, callback: AsyncCallback\<Array\<OverlayModuleInfo>>): void;<br>差异内容：function getTargetOverlayModuleInfos(targetModuleName: string, callback: AsyncCallback\<Array\<OverlayModuleInfo>>): void;|api/@ohos.bundle.overlay.d.ts|
|新增API|NA|类名：overlay；<br>API声明：function getTargetOverlayModuleInfos(targetModuleName: string): Promise\<Array\<OverlayModuleInfo>>;<br>差异内容：function getTargetOverlayModuleInfos(targetModuleName: string): Promise\<Array\<OverlayModuleInfo>>;|api/@ohos.bundle.overlay.d.ts|
|新增API|NA|类名：overlay；<br>API声明：export type OverlayModuleInfo = _OverlayModuleInfo.OverlayModuleInfo;<br>差异内容：export type OverlayModuleInfo = _OverlayModuleInfo.OverlayModuleInfo;|api/@ohos.bundle.overlay.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace continuationManager<br>差异内容：declare namespace continuationManager|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function on(type: 'deviceSelected', token: number, callback: Callback\<Array\<ContinuationResult>>): void;<br>差异内容：function on(type: 'deviceSelected', token: number, callback: Callback\<Array\<ContinuationResult>>): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function off(type: 'deviceSelected', token: number): void;<br>差异内容：function off(type: 'deviceSelected', token: number): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function on(type: 'deviceUnselected', token: number, callback: Callback\<Array\<ContinuationResult>>): void;<br>差异内容：function on(type: 'deviceUnselected', token: number, callback: Callback\<Array\<ContinuationResult>>): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function off(type: 'deviceUnselected', token: number): void;<br>差异内容：function off(type: 'deviceUnselected', token: number): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function on(type: 'deviceConnect', callback: Callback\<ContinuationResult>): void;<br>差异内容：function on(type: 'deviceConnect', callback: Callback\<ContinuationResult>): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function off(type: 'deviceConnect', callback?: Callback\<ContinuationResult>): void;<br>差异内容：function off(type: 'deviceConnect', callback?: Callback\<ContinuationResult>): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function on(type: 'deviceDisconnect', callback: Callback\<string>): void;<br>差异内容：function on(type: 'deviceDisconnect', callback: Callback\<string>): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function off(type: 'deviceDisconnect', callback?: Callback\<string>): void;<br>差异内容：function off(type: 'deviceDisconnect', callback?: Callback\<string>): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function register(callback: AsyncCallback\<number>): void;<br>差异内容：function register(callback: AsyncCallback\<number>): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function register(options: ContinuationExtraParams, callback: AsyncCallback\<number>): void;<br>差异内容：function register(options: ContinuationExtraParams, callback: AsyncCallback\<number>): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function register(options?: ContinuationExtraParams): Promise\<number>;<br>差异内容：function register(options?: ContinuationExtraParams): Promise\<number>;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function unregister(token: number, callback: AsyncCallback\<void>): void;<br>差异内容：function unregister(token: number, callback: AsyncCallback\<void>): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function unregister(token: number): Promise\<void>;<br>差异内容：function unregister(token: number): Promise\<void>;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function updateConnectStatus(token: number, deviceId: string, status: DeviceConnectState, callback: AsyncCallback\<void>): void;<br>差异内容：function updateConnectStatus(token: number, deviceId: string, status: DeviceConnectState, callback: AsyncCallback\<void>): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function updateConnectStatus(token: number, deviceId: string, status: DeviceConnectState): Promise\<void>;<br>差异内容：function updateConnectStatus(token: number, deviceId: string, status: DeviceConnectState): Promise\<void>;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function startDeviceManager(token: number, callback: AsyncCallback\<void>): void;<br>差异内容：function startDeviceManager(token: number, callback: AsyncCallback\<void>): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function startDeviceManager(token: number, options: ContinuationExtraParams, callback: AsyncCallback\<void>): void;<br>差异内容：function startDeviceManager(token: number, options: ContinuationExtraParams, callback: AsyncCallback\<void>): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function startDeviceManager(token: number, options?: ContinuationExtraParams): Promise\<void>;<br>差异内容：function startDeviceManager(token: number, options?: ContinuationExtraParams): Promise\<void>;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function registerContinuation(callback: AsyncCallback\<number>): void;<br>差异内容：function registerContinuation(callback: AsyncCallback\<number>): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function registerContinuation(options: ContinuationExtraParams, callback: AsyncCallback\<number>): void;<br>差异内容：function registerContinuation(options: ContinuationExtraParams, callback: AsyncCallback\<number>): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function registerContinuation(options?: ContinuationExtraParams): Promise\<number>;<br>差异内容：function registerContinuation(options?: ContinuationExtraParams): Promise\<number>;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function unregisterContinuation(token: number, callback: AsyncCallback\<void>): void;<br>差异内容：function unregisterContinuation(token: number, callback: AsyncCallback\<void>): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function unregisterContinuation(token: number): Promise\<void>;<br>差异内容：function unregisterContinuation(token: number): Promise\<void>;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function updateContinuationState(token: number, deviceId: string, status: DeviceConnectState, callback: AsyncCallback\<void>): void;<br>差异内容：function updateContinuationState(token: number, deviceId: string, status: DeviceConnectState, callback: AsyncCallback\<void>): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function updateContinuationState(token: number, deviceId: string, status: DeviceConnectState): Promise\<void>;<br>差异内容：function updateContinuationState(token: number, deviceId: string, status: DeviceConnectState): Promise\<void>;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function startContinuationDeviceManager(token: number, callback: AsyncCallback\<void>): void;<br>差异内容：function startContinuationDeviceManager(token: number, callback: AsyncCallback\<void>): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function startContinuationDeviceManager(token: number, options: ContinuationExtraParams, callback: AsyncCallback\<void>): void;<br>差异内容：function startContinuationDeviceManager(token: number, options: ContinuationExtraParams, callback: AsyncCallback\<void>): void;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：function startContinuationDeviceManager(token: number, options?: ContinuationExtraParams): Promise\<void>;<br>差异内容：function startContinuationDeviceManager(token: number, options?: ContinuationExtraParams): Promise\<void>;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：export enum DeviceConnectState<br>差异内容：export enum DeviceConnectState|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：DeviceConnectState；<br>API声明：IDLE = 0<br>差异内容：IDLE = 0|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：DeviceConnectState；<br>API声明：CONNECTING = 1<br>差异内容：CONNECTING = 1|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：DeviceConnectState；<br>API声明：CONNECTED = 2<br>差异内容：CONNECTED = 2|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：DeviceConnectState；<br>API声明：DISCONNECTING = 3<br>差异内容：DISCONNECTING = 3|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：export enum ContinuationMode<br>差异内容：export enum ContinuationMode|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：ContinuationMode；<br>API声明：COLLABORATION_SINGLE = 0<br>差异内容：COLLABORATION_SINGLE = 0|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：ContinuationMode；<br>API声明：COLLABORATION_MULTIPLE = 1<br>差异内容：COLLABORATION_MULTIPLE = 1|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：export type ContinuationResult = _ContinuationResult;<br>差异内容：export type ContinuationResult = _ContinuationResult;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：continuationManager；<br>API声明：export type ContinuationExtraParams = _ContinuationExtraParams;<br>差异内容：export type ContinuationExtraParams = _ContinuationExtraParams;|api/@ohos.continuation.continuationManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace privacyManager<br>差异内容：declare namespace privacyManager|api/@ohos.privacyManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace wantAgent<br>差异内容：declare namespace wantAgent|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function getBundleName(agent: WantAgent, callback: AsyncCallback\<string>): void;<br>差异内容：function getBundleName(agent: WantAgent, callback: AsyncCallback\<string>): void;|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function getBundleName(agent: WantAgent): Promise\<string>;<br>差异内容：function getBundleName(agent: WantAgent): Promise\<string>;|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function getUid(agent: WantAgent, callback: AsyncCallback\<number>): void;<br>差异内容：function getUid(agent: WantAgent, callback: AsyncCallback\<number>): void;|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function getUid(agent: WantAgent): Promise\<number>;<br>差异内容：function getUid(agent: WantAgent): Promise\<number>;|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function cancel(agent: WantAgent, callback: AsyncCallback\<void>): void;<br>差异内容：function cancel(agent: WantAgent, callback: AsyncCallback\<void>): void;|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function cancel(agent: WantAgent): Promise\<void>;<br>差异内容：function cancel(agent: WantAgent): Promise\<void>;|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function trigger(agent: WantAgent, triggerInfo: TriggerInfo, callback?: Callback\<CompleteData>): void;<br>差异内容：function trigger(agent: WantAgent, triggerInfo: TriggerInfo, callback?: Callback\<CompleteData>): void;|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function equal(agent: WantAgent, otherAgent: WantAgent, callback: AsyncCallback\<boolean>): void;<br>差异内容：function equal(agent: WantAgent, otherAgent: WantAgent, callback: AsyncCallback\<boolean>): void;|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function equal(agent: WantAgent, otherAgent: WantAgent): Promise\<boolean>;<br>差异内容：function equal(agent: WantAgent, otherAgent: WantAgent): Promise\<boolean>;|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function getWantAgent(info: WantAgentInfo, callback: AsyncCallback\<WantAgent>): void;<br>差异内容：function getWantAgent(info: WantAgentInfo, callback: AsyncCallback\<WantAgent>): void;|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：function getWantAgent(info: WantAgentInfo): Promise\<WantAgent>;<br>差异内容：function getWantAgent(info: WantAgentInfo): Promise\<WantAgent>;|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：export enum WantAgentFlags<br>差异内容：export enum WantAgentFlags|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：ONE_TIME_FLAG = 0<br>差异内容：ONE_TIME_FLAG = 0|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：NO_BUILD_FLAG<br>差异内容：NO_BUILD_FLAG|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：CANCEL_PRESENT_FLAG<br>差异内容：CANCEL_PRESENT_FLAG|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：UPDATE_PRESENT_FLAG<br>差异内容：UPDATE_PRESENT_FLAG|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：CONSTANT_FLAG<br>差异内容：CONSTANT_FLAG|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：REPLACE_ELEMENT<br>差异内容：REPLACE_ELEMENT|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：REPLACE_ACTION<br>差异内容：REPLACE_ACTION|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：REPLACE_URI<br>差异内容：REPLACE_URI|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：REPLACE_ENTITIES<br>差异内容：REPLACE_ENTITIES|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：WantAgentFlags；<br>API声明：REPLACE_BUNDLE<br>差异内容：REPLACE_BUNDLE|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：export enum OperationType<br>差异内容：export enum OperationType|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：OperationType；<br>API声明：UNKNOWN_TYPE = 0<br>差异内容：UNKNOWN_TYPE = 0|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：OperationType；<br>API声明：START_ABILITY<br>差异内容：START_ABILITY|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：OperationType；<br>API声明：START_ABILITIES<br>差异内容：START_ABILITIES|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：OperationType；<br>API声明：START_SERVICE<br>差异内容：START_SERVICE|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：OperationType；<br>API声明：SEND_COMMON_EVENT<br>差异内容：SEND_COMMON_EVENT|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：wantAgent；<br>API声明：export interface CompleteData<br>差异内容：export interface CompleteData|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：CompleteData；<br>API声明：info: WantAgent;<br>差异内容：info: WantAgent;|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：CompleteData；<br>API声明：want: Want;<br>差异内容：want: Want;|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：CompleteData；<br>API声明：finalCode: number;<br>差异内容：finalCode: number;|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：CompleteData；<br>API声明：finalData: string;<br>差异内容：finalData: string;|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：CompleteData；<br>API声明：extraInfo?: {<br>            [key: string]: any;<br>        };<br>差异内容：extraInfo?: {<br>            [key: string]: any;<br>        };|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：global；<br>API声明：export type WantAgent = object;<br>差异内容：export type WantAgent = object;|api/@ohos.wantAgent.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface CheckPackageHasInstalledResponse<br>差异内容：export interface CheckPackageHasInstalledResponse|api/@system.package.d.ts|
|新增API|NA|类名：CheckPackageHasInstalledResponse；<br>API声明：result: boolean;<br>差异内容：result: boolean;|api/@system.package.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface CheckPackageHasInstalledOptions<br>差异内容：export interface CheckPackageHasInstalledOptions|api/@system.package.d.ts|
|新增API|NA|类名：CheckPackageHasInstalledOptions；<br>API声明：bundleName: string;<br>差异内容：bundleName: string;|api/@system.package.d.ts|
|新增API|NA|类名：CheckPackageHasInstalledOptions；<br>API声明：success?: (data: CheckPackageHasInstalledResponse) => void;<br>差异内容：success?: (data: CheckPackageHasInstalledResponse) => void;|api/@system.package.d.ts|
|新增API|NA|类名：CheckPackageHasInstalledOptions；<br>API声明：fail?: (data: any, code: number) => void;<br>差异内容：fail?: (data: any, code: number) => void;|api/@system.package.d.ts|
|新增API|NA|类名：CheckPackageHasInstalledOptions；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.package.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class Package<br>差异内容：export default class Package|api/@system.package.d.ts|
|新增API|NA|类名：Package；<br>API声明：static hasInstalled(options: CheckPackageHasInstalledOptions): void;<br>差异内容：static hasInstalled(options: CheckPackageHasInstalledOptions): void;|api/@system.package.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.ability.ability.d.ts<br>差异内容：AbilityKit|api/@ohos.ability.ability.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.ability.dataUriUtils.d.ts<br>差异内容：AbilityKit|api/@ohos.ability.dataUriUtils.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.ability.errorCode.d.ts<br>差异内容：AbilityKit|api/@ohos.ability.errorCode.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.ability.featureAbility.d.ts<br>差异内容：AbilityKit|api/@ohos.ability.featureAbility.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.ability.particleAbility.d.ts<br>差异内容：AbilityKit|api/@ohos.ability.particleAbility.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.ability.wantConstant.d.ts<br>差异内容：AbilityKit|api/@ohos.ability.wantConstant.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.abilityAccessCtrl.d.ts<br>差异内容：AbilityKit|api/@ohos.abilityAccessCtrl.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.Ability.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.Ability.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.AbilityConstant.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.AbilityConstant.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.AbilityLifecycleCallback.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.AbilityLifecycleCallback.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.AbilityStage.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.AbilityStage.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.ActionExtensionAbility.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.ActionExtensionAbility.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.ApplicationStateChangeCallback.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.ApplicationStateChangeCallback.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.appManager.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.appManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.appRecovery.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.appRecovery.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.autoFillManager.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.autoFillManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.ChildProcess.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.ChildProcess.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.childProcessManager.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.childProcessManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.common.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.common.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.Configuration.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.Configuration.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.ConfigurationConstant.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.ConfigurationConstant.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.contextConstant.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.contextConstant.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.dataUriUtils.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.dataUriUtils.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.dialogRequest.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.dialogRequest.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.EnvironmentCallback.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.EnvironmentCallback.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.errorManager.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.errorManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.ExtensionAbility.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.ExtensionAbility.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.insightIntent.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.insightIntent.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.InsightIntentContext.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.InsightIntentContext.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.InsightIntentExecutor.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.InsightIntentExecutor.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.ShareExtensionAbility.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.ShareExtensionAbility.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.StartOptions.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.StartOptions.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.UIAbility.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.UIAbility.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.UIExtensionAbility.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.UIExtensionAbility.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.UIExtensionContentSession.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.UIExtensionContentSession.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.Want.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.Want.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.wantAgent.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.wantAgent.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.wantConstant.d.ts<br>差异内容：AbilityKit|api/@ohos.app.ability.wantConstant.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.application.appManager.d.ts<br>差异内容：AbilityKit|api/@ohos.application.appManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.application.Configuration.d.ts<br>差异内容：AbilityKit|api/@ohos.application.Configuration.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.application.ConfigurationConstant.d.ts<br>差异内容：AbilityKit|api/@ohos.application.ConfigurationConstant.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.application.uriPermissionManager.d.ts<br>差异内容：AbilityKit|api/@ohos.application.uriPermissionManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.application.Want.d.ts<br>差异内容：AbilityKit|api/@ohos.application.Want.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bundle.bundleManager.d.ts<br>差异内容：AbilityKit|api/@ohos.bundle.bundleManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bundle.d.ts<br>差异内容：AbilityKit|api/@ohos.bundle.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bundle.defaultAppManager.d.ts<br>差异内容：AbilityKit|api/@ohos.bundle.defaultAppManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bundle.overlay.d.ts<br>差异内容：AbilityKit|api/@ohos.bundle.overlay.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.continuation.continuationManager.d.ts<br>差异内容：AbilityKit|api/@ohos.continuation.continuationManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.privacyManager.d.ts<br>差异内容：AbilityKit|api/@ohos.privacyManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.wantAgent.d.ts<br>差异内容：AbilityKit|api/@ohos.wantAgent.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@system.package.d.ts<br>差异内容：AbilityKit|api/@system.package.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.AbilityKit.d.ts<br>差异内容：AbilityKit|kits/@kit.AbilityKit.d.ts|
