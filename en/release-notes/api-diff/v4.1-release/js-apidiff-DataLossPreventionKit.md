| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API|NA|Class name: global;<br>API declaration: declare namespace dlpPermission<br>Differences: declare namespace dlpPermission|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: export enum ActionFlagType<br>Differences: export enum ActionFlagType|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: ActionFlagType;<br>API declaration: ACTION_VIEW = 0x00000001<br>Differences: ACTION_VIEW = 0x00000001|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: ActionFlagType;<br>API declaration: ACTION_SAVE = 0x00000002<br>Differences: ACTION_SAVE = 0x00000002|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: ActionFlagType;<br>API declaration: ACTION_SAVE_AS = 0x00000004<br>Differences: ACTION_SAVE_AS = 0x00000004|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: ActionFlagType;<br>API declaration: ACTION_EDIT = 0x00000008<br>Differences: ACTION_EDIT = 0x00000008|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: ActionFlagType;<br>API declaration: ACTION_SCREEN_CAPTURE = 0x00000010<br>Differences: ACTION_SCREEN_CAPTURE = 0x00000010|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: ActionFlagType;<br>API declaration: ACTION_SCREEN_SHARE = 0x00000020<br>Differences: ACTION_SCREEN_SHARE = 0x00000020|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: ActionFlagType;<br>API declaration: ACTION_SCREEN_RECORD = 0x00000040<br>Differences: ACTION_SCREEN_RECORD = 0x00000040|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: ActionFlagType;<br>API declaration: ACTION_COPY = 0x00000080<br>Differences: ACTION_COPY = 0x00000080|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: ActionFlagType;<br>API declaration: ACTION_PRINT = 0x00000100<br>Differences: ACTION_PRINT = 0x00000100|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: ActionFlagType;<br>API declaration: ACTION_EXPORT = 0x00000200<br>Differences: ACTION_EXPORT = 0x00000200|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: ActionFlagType;<br>API declaration: ACTION_PERMISSION_CHANGE = 0x00000400<br>Differences: ACTION_PERMISSION_CHANGE = 0x00000400|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: export enum DLPFileAccess<br>Differences: export enum DLPFileAccess|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: DLPFileAccess;<br>API declaration: NO_PERMISSION = 0<br>Differences: NO_PERMISSION = 0|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: DLPFileAccess;<br>API declaration: READ_ONLY = 1<br>Differences: READ_ONLY = 1|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: DLPFileAccess;<br>API declaration: CONTENT_EDIT = 2<br>Differences: CONTENT_EDIT = 2|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: DLPFileAccess;<br>API declaration: FULL_CONTROL = 3<br>Differences: FULL_CONTROL = 3|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: export interface DLPPermissionInfo<br>Differences: export interface DLPPermissionInfo|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: DLPPermissionInfo;<br>API declaration: dlpFileAccess: DLPFileAccess;<br>Differences: dlpFileAccess: DLPFileAccess;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: DLPPermissionInfo;<br>API declaration: flags: number;<br>Differences: flags: number;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: export interface AccessedDLPFileInfo<br>Differences: export interface AccessedDLPFileInfo|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: AccessedDLPFileInfo;<br>API declaration: uri: string;<br>Differences: uri: string;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: AccessedDLPFileInfo;<br>API declaration: lastOpenTime: number;<br>Differences: lastOpenTime: number;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: export interface RetentionSandboxInfo<br>Differences: export interface RetentionSandboxInfo|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: RetentionSandboxInfo;<br>API declaration: appIndex: number;<br>Differences: appIndex: number;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: RetentionSandboxInfo;<br>API declaration: bundleName: string;<br>Differences: bundleName: string;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: RetentionSandboxInfo;<br>API declaration: docUris: Array\<string>;<br>Differences: docUris: Array\<string>;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function isDLPFile(fd: number): Promise\<boolean>;<br>Differences: function isDLPFile(fd: number): Promise\<boolean>;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function isDLPFile(fd: number, callback: AsyncCallback\<boolean>): void;<br>Differences: function isDLPFile(fd: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function getDLPPermissionInfo(): Promise\<DLPPermissionInfo>;<br>Differences: function getDLPPermissionInfo(): Promise\<DLPPermissionInfo>;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function getDLPPermissionInfo(callback: AsyncCallback\<DLPPermissionInfo>): void;<br>Differences: function getDLPPermissionInfo(callback: AsyncCallback\<DLPPermissionInfo>): void;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function getOriginalFileName(fileName: string): string;<br>Differences: function getOriginalFileName(fileName: string): string;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function getDLPSuffix(): string;<br>Differences: function getDLPSuffix(): string;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function on(type: 'openDLPFile', listener: Callback\<AccessedDLPFileInfo>): void;<br>Differences: function on(type: 'openDLPFile', listener: Callback\<AccessedDLPFileInfo>): void;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function off(type: 'openDLPFile', listener?: Callback\<AccessedDLPFileInfo>): void;<br>Differences: function off(type: 'openDLPFile', listener?: Callback\<AccessedDLPFileInfo>): void;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function isInSandbox(): Promise\<boolean>;<br>Differences: function isInSandbox(): Promise\<boolean>;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function isInSandbox(callback: AsyncCallback\<boolean>): void;<br>Differences: function isInSandbox(callback: AsyncCallback\<boolean>): void;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function getDLPSupportedFileTypes(): Promise\<Array\<string>>;<br>Differences: function getDLPSupportedFileTypes(): Promise\<Array\<string>>;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function getDLPSupportedFileTypes(callback: AsyncCallback\<Array\<string>>): void;<br>Differences: function getDLPSupportedFileTypes(callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function setRetentionState(docUris: Array\<string>): Promise\<void>;<br>Differences: function setRetentionState(docUris: Array\<string>): Promise\<void>;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function setRetentionState(docUris: Array\<string>, callback: AsyncCallback\<void>): void;<br>Differences: function setRetentionState(docUris: Array\<string>, callback: AsyncCallback\<void>): void;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function cancelRetentionState(docUris: Array\<string>): Promise\<void>;<br>Differences: function cancelRetentionState(docUris: Array\<string>): Promise\<void>;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function cancelRetentionState(docUris: Array\<string>, callback: AsyncCallback\<void>): void;<br>Differences: function cancelRetentionState(docUris: Array\<string>, callback: AsyncCallback\<void>): void;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function getRetentionSandboxList(bundleName?: string): Promise\<Array\<RetentionSandboxInfo>>;<br>Differences: function getRetentionSandboxList(bundleName?: string): Promise\<Array\<RetentionSandboxInfo>>;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function getRetentionSandboxList(bundleName: string, callback: AsyncCallback\<Array\<RetentionSandboxInfo>>): void;<br>Differences: function getRetentionSandboxList(bundleName: string, callback: AsyncCallback\<Array\<RetentionSandboxInfo>>): void;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function getRetentionSandboxList(callback: AsyncCallback\<Array\<RetentionSandboxInfo>>): void;<br>Differences: function getRetentionSandboxList(callback: AsyncCallback\<Array\<RetentionSandboxInfo>>): void;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function getDLPFileAccessRecords(): Promise\<Array\<AccessedDLPFileInfo>>;<br>Differences: function getDLPFileAccessRecords(): Promise\<Array\<AccessedDLPFileInfo>>;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function getDLPFileAccessRecords(callback: AsyncCallback\<Array\<AccessedDLPFileInfo>>): void;<br>Differences: function getDLPFileAccessRecords(callback: AsyncCallback\<Array\<AccessedDLPFileInfo>>): void;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: export interface DLPManagerResult<br>Differences: export interface DLPManagerResult|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: DLPManagerResult;<br>API declaration: resultCode: number;<br>Differences: resultCode: number;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: DLPManagerResult;<br>API declaration: want: Want;<br>Differences: want: Want;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function startDLPManagerForResult(context: common.UIAbilityContext, want: Want): Promise\<DLPManagerResult>;<br>Differences: function startDLPManagerForResult(context: common.UIAbilityContext, want: Want): Promise\<DLPManagerResult>;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function setSandboxAppConfig(configInfo: string): Promise\<void>;<br>Differences: function setSandboxAppConfig(configInfo: string): Promise\<void>;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function cleanSandboxAppConfig(): Promise\<void>;<br>Differences: function cleanSandboxAppConfig(): Promise\<void>;|api/@ohos.dlpPermission.d.ts|
|New API|NA|Class name: dlpPermission;<br>API declaration: function getSandboxAppConfig(): Promise\<string>;<br>Differences: function getSandboxAppConfig(): Promise\<string>;|api/@ohos.dlpPermission.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.dlpPermission.d.ts<br>Differences: DataLossPreventionKit|api/@ohos.dlpPermission.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.DataLossPreventionKit.d.ts<br>Differences: DataLossPreventionKit|kits/@kit.DataLossPreventionKit.d.ts|
