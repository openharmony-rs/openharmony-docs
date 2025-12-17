| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace dlpPermission<br>差异内容：declare namespace dlpPermission|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：export enum ActionFlagType<br>差异内容：export enum ActionFlagType|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：ActionFlagType；<br>API声明：ACTION_VIEW = 0x00000001<br>差异内容：ACTION_VIEW = 0x00000001|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：ActionFlagType；<br>API声明：ACTION_SAVE = 0x00000002<br>差异内容：ACTION_SAVE = 0x00000002|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：ActionFlagType；<br>API声明：ACTION_SAVE_AS = 0x00000004<br>差异内容：ACTION_SAVE_AS = 0x00000004|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：ActionFlagType；<br>API声明：ACTION_EDIT = 0x00000008<br>差异内容：ACTION_EDIT = 0x00000008|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：ActionFlagType；<br>API声明：ACTION_SCREEN_CAPTURE = 0x00000010<br>差异内容：ACTION_SCREEN_CAPTURE = 0x00000010|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：ActionFlagType；<br>API声明：ACTION_SCREEN_SHARE = 0x00000020<br>差异内容：ACTION_SCREEN_SHARE = 0x00000020|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：ActionFlagType；<br>API声明：ACTION_SCREEN_RECORD = 0x00000040<br>差异内容：ACTION_SCREEN_RECORD = 0x00000040|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：ActionFlagType；<br>API声明：ACTION_COPY = 0x00000080<br>差异内容：ACTION_COPY = 0x00000080|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：ActionFlagType；<br>API声明：ACTION_PRINT = 0x00000100<br>差异内容：ACTION_PRINT = 0x00000100|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：ActionFlagType；<br>API声明：ACTION_EXPORT = 0x00000200<br>差异内容：ACTION_EXPORT = 0x00000200|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：ActionFlagType；<br>API声明：ACTION_PERMISSION_CHANGE = 0x00000400<br>差异内容：ACTION_PERMISSION_CHANGE = 0x00000400|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：export enum DLPFileAccess<br>差异内容：export enum DLPFileAccess|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：DLPFileAccess；<br>API声明：NO_PERMISSION = 0<br>差异内容：NO_PERMISSION = 0|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：DLPFileAccess；<br>API声明：READ_ONLY = 1<br>差异内容：READ_ONLY = 1|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：DLPFileAccess；<br>API声明：CONTENT_EDIT = 2<br>差异内容：CONTENT_EDIT = 2|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：DLPFileAccess；<br>API声明：FULL_CONTROL = 3<br>差异内容：FULL_CONTROL = 3|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：export interface DLPPermissionInfo<br>差异内容：export interface DLPPermissionInfo|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：DLPPermissionInfo；<br>API声明：dlpFileAccess: DLPFileAccess;<br>差异内容：dlpFileAccess: DLPFileAccess;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：DLPPermissionInfo；<br>API声明：flags: number;<br>差异内容：flags: number;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：export interface AccessedDLPFileInfo<br>差异内容：export interface AccessedDLPFileInfo|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：AccessedDLPFileInfo；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：AccessedDLPFileInfo；<br>API声明：lastOpenTime: number;<br>差异内容：lastOpenTime: number;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：export interface RetentionSandboxInfo<br>差异内容：export interface RetentionSandboxInfo|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：RetentionSandboxInfo；<br>API声明：appIndex: number;<br>差异内容：appIndex: number;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：RetentionSandboxInfo；<br>API声明：bundleName: string;<br>差异内容：bundleName: string;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：RetentionSandboxInfo；<br>API声明：docUris: Array\<string>;<br>差异内容：docUris: Array\<string>;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function isDLPFile(fd: number): Promise\<boolean>;<br>差异内容：function isDLPFile(fd: number): Promise\<boolean>;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function isDLPFile(fd: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：function isDLPFile(fd: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function getDLPPermissionInfo(): Promise\<DLPPermissionInfo>;<br>差异内容：function getDLPPermissionInfo(): Promise\<DLPPermissionInfo>;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function getDLPPermissionInfo(callback: AsyncCallback\<DLPPermissionInfo>): void;<br>差异内容：function getDLPPermissionInfo(callback: AsyncCallback\<DLPPermissionInfo>): void;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function getOriginalFileName(fileName: string): string;<br>差异内容：function getOriginalFileName(fileName: string): string;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function getDLPSuffix(): string;<br>差异内容：function getDLPSuffix(): string;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function on(type: 'openDLPFile', listener: Callback\<AccessedDLPFileInfo>): void;<br>差异内容：function on(type: 'openDLPFile', listener: Callback\<AccessedDLPFileInfo>): void;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function off(type: 'openDLPFile', listener?: Callback\<AccessedDLPFileInfo>): void;<br>差异内容：function off(type: 'openDLPFile', listener?: Callback\<AccessedDLPFileInfo>): void;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function isInSandbox(): Promise\<boolean>;<br>差异内容：function isInSandbox(): Promise\<boolean>;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function isInSandbox(callback: AsyncCallback\<boolean>): void;<br>差异内容：function isInSandbox(callback: AsyncCallback\<boolean>): void;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function getDLPSupportedFileTypes(): Promise\<Array\<string>>;<br>差异内容：function getDLPSupportedFileTypes(): Promise\<Array\<string>>;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function getDLPSupportedFileTypes(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：function getDLPSupportedFileTypes(callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function setRetentionState(docUris: Array\<string>): Promise\<void>;<br>差异内容：function setRetentionState(docUris: Array\<string>): Promise\<void>;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function setRetentionState(docUris: Array\<string>, callback: AsyncCallback\<void>): void;<br>差异内容：function setRetentionState(docUris: Array\<string>, callback: AsyncCallback\<void>): void;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function cancelRetentionState(docUris: Array\<string>): Promise\<void>;<br>差异内容：function cancelRetentionState(docUris: Array\<string>): Promise\<void>;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function cancelRetentionState(docUris: Array\<string>, callback: AsyncCallback\<void>): void;<br>差异内容：function cancelRetentionState(docUris: Array\<string>, callback: AsyncCallback\<void>): void;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function getRetentionSandboxList(bundleName?: string): Promise\<Array\<RetentionSandboxInfo>>;<br>差异内容：function getRetentionSandboxList(bundleName?: string): Promise\<Array\<RetentionSandboxInfo>>;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function getRetentionSandboxList(bundleName: string, callback: AsyncCallback\<Array\<RetentionSandboxInfo>>): void;<br>差异内容：function getRetentionSandboxList(bundleName: string, callback: AsyncCallback\<Array\<RetentionSandboxInfo>>): void;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function getRetentionSandboxList(callback: AsyncCallback\<Array\<RetentionSandboxInfo>>): void;<br>差异内容：function getRetentionSandboxList(callback: AsyncCallback\<Array\<RetentionSandboxInfo>>): void;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function getDLPFileAccessRecords(): Promise\<Array\<AccessedDLPFileInfo>>;<br>差异内容：function getDLPFileAccessRecords(): Promise\<Array\<AccessedDLPFileInfo>>;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function getDLPFileAccessRecords(callback: AsyncCallback\<Array\<AccessedDLPFileInfo>>): void;<br>差异内容：function getDLPFileAccessRecords(callback: AsyncCallback\<Array\<AccessedDLPFileInfo>>): void;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：export interface DLPManagerResult<br>差异内容：export interface DLPManagerResult|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：DLPManagerResult；<br>API声明：resultCode: number;<br>差异内容：resultCode: number;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：DLPManagerResult；<br>API声明：want: Want;<br>差异内容：want: Want;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function startDLPManagerForResult(context: common.UIAbilityContext, want: Want): Promise\<DLPManagerResult>;<br>差异内容：function startDLPManagerForResult(context: common.UIAbilityContext, want: Want): Promise\<DLPManagerResult>;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function setSandboxAppConfig(configInfo: string): Promise\<void>;<br>差异内容：function setSandboxAppConfig(configInfo: string): Promise\<void>;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function cleanSandboxAppConfig(): Promise\<void>;<br>差异内容：function cleanSandboxAppConfig(): Promise\<void>;|api/@ohos.dlpPermission.d.ts|
|新增API|NA|类名：dlpPermission；<br>API声明：function getSandboxAppConfig(): Promise\<string>;<br>差异内容：function getSandboxAppConfig(): Promise\<string>;|api/@ohos.dlpPermission.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.dlpPermission.d.ts<br>差异内容：DataLossPreventionKit|api/@ohos.dlpPermission.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.DataLossPreventionKit.d.ts<br>差异内容：DataLossPreventionKit|kits/@kit.DataLossPreventionKit.d.ts|
