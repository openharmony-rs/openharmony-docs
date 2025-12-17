| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：export interface BundleVersion<br>差异内容：export interface BundleVersion|api/@ohos.application.BackupExtensionAbility.d.ts|
|新增API|NA|类名：BundleVersion；<br>API声明：code: number;<br>差异内容：code: number;|api/@ohos.application.BackupExtensionAbility.d.ts|
|新增API|NA|类名：BundleVersion；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.application.BackupExtensionAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class BackupExtensionAbility<br>差异内容：export default class BackupExtensionAbility|api/@ohos.application.BackupExtensionAbility.d.ts|
|新增API|NA|类名：BackupExtensionAbility；<br>API声明：context: ExtensionContext;<br>差异内容：context: ExtensionContext;|api/@ohos.application.BackupExtensionAbility.d.ts|
|新增API|NA|类名：BackupExtensionAbility；<br>API声明：onBackup(): void;<br>差异内容：onBackup(): void;|api/@ohos.application.BackupExtensionAbility.d.ts|
|新增API|NA|类名：BackupExtensionAbility；<br>API声明：onRestore(bundleVersion: BundleVersion): void;<br>差异内容：onRestore(bundleVersion: BundleVersion): void;|api/@ohos.application.BackupExtensionAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace document<br>差异内容：declare namespace document|api/@ohos.document.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function choose(types?: string[]): Promise\<string>;<br>差异内容：declare function choose(types?: string[]): Promise\<string>;|api/@ohos.document.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function choose(callback: AsyncCallback\<string>): void;<br>差异内容：declare function choose(callback: AsyncCallback\<string>): void;|api/@ohos.document.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function choose(types: string[], callback: AsyncCallback\<string>): void;<br>差异内容：declare function choose(types: string[], callback: AsyncCallback\<string>): void;|api/@ohos.document.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function show(uri: string, type: string): Promise\<void>;<br>差异内容：declare function show(uri: string, type: string): Promise\<void>;|api/@ohos.document.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function show(uri: string, type: string, callback: AsyncCallback\<void>): void;<br>差异内容：declare function show(uri: string, type: string, callback: AsyncCallback\<void>): void;|api/@ohos.document.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace cloudSync<br>差异内容：declare namespace cloudSync|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：enum State<br>差异内容：enum State|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：State；<br>API声明：RUNNING<br>差异内容：RUNNING|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：State；<br>API声明：COMPLETED<br>差异内容：COMPLETED|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：State；<br>API声明：FAILED<br>差异内容：FAILED|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：State；<br>API声明：STOPPED<br>差异内容：STOPPED|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：enum DownloadErrorType<br>差异内容：enum DownloadErrorType|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：DownloadErrorType；<br>API声明：NO_ERROR<br>差异内容：NO_ERROR|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：DownloadErrorType；<br>API声明：UNKNOWN_ERROR<br>差异内容：UNKNOWN_ERROR|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：DownloadErrorType；<br>API声明：NETWORK_UNAVAILABLE<br>差异内容：NETWORK_UNAVAILABLE|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：DownloadErrorType；<br>API声明：LOCAL_STORAGE_FULL<br>差异内容：LOCAL_STORAGE_FULL|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：DownloadErrorType；<br>API声明：CONTENT_NOT_FOUND<br>差异内容：CONTENT_NOT_FOUND|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：DownloadErrorType；<br>API声明：FREQUENT_USER_REQUESTS<br>差异内容：FREQUENT_USER_REQUESTS|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：interface DownloadProgress<br>差异内容：interface DownloadProgress|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：DownloadProgress；<br>API声明：state: State;<br>差异内容：state: State;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：DownloadProgress；<br>API声明：processed: number;<br>差异内容：processed: number;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：DownloadProgress；<br>API声明：size: number;<br>差异内容：size: number;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：DownloadProgress；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：DownloadProgress；<br>API声明：error: DownloadErrorType;<br>差异内容：error: DownloadErrorType;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：class CloudFileCache<br>差异内容：class CloudFileCache|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：CloudFileCache；<br>API声明：on(event: 'progress', callback: Callback\<DownloadProgress>): void;<br>差异内容：on(event: 'progress', callback: Callback\<DownloadProgress>): void;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：CloudFileCache；<br>API声明：off(event: 'progress', callback?: Callback\<DownloadProgress>): void;<br>差异内容：off(event: 'progress', callback?: Callback\<DownloadProgress>): void;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：CloudFileCache；<br>API声明：start(uri: string): Promise\<void>;<br>差异内容：start(uri: string): Promise\<void>;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：CloudFileCache；<br>API声明：start(uri: string, callback: AsyncCallback\<void>): void;<br>差异内容：start(uri: string, callback: AsyncCallback\<void>): void;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：CloudFileCache；<br>API声明：stop(uri: string): Promise\<void>;<br>差异内容：stop(uri: string): Promise\<void>;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：CloudFileCache；<br>API声明：stop(uri: string, callback: AsyncCallback\<void>): void;<br>差异内容：stop(uri: string, callback: AsyncCallback\<void>): void;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace cloudSyncManager<br>差异内容：declare namespace cloudSyncManager|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace Environment<br>差异内容：declare namespace Environment|api/@ohos.file.environment.d.ts|
|新增API|NA|类名：Environment；<br>API声明：function getUserDownloadDir(): string;<br>差异内容：function getUserDownloadDir(): string;|api/@ohos.file.environment.d.ts|
|新增API|NA|类名：Environment；<br>API声明：function getUserDesktopDir(): string;<br>差异内容：function getUserDesktopDir(): string;|api/@ohos.file.environment.d.ts|
|新增API|NA|类名：Environment；<br>API声明：function getUserDocumentDir(): string;<br>差异内容：function getUserDocumentDir(): string;|api/@ohos.file.environment.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace fileAccess<br>差异内容：declare namespace fileAccess|api/@ohos.file.fileAccess.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace fileUri<br>差异内容：declare namespace fileUri|api/@ohos.file.fileuri.d.ts|
|新增API|NA|类名：fileUri；<br>API声明：class FileUri<br>差异内容：class FileUri|api/@ohos.file.fileuri.d.ts|
|新增API|NA|类名：FileUri；<br>API声明：readonly name: string;<br>差异内容：readonly name: string;|api/@ohos.file.fileuri.d.ts|
|新增API|NA|类名：FileUri；<br>API声明：getFullDirectoryUri(): string;<br>差异内容：getFullDirectoryUri(): string;|api/@ohos.file.fileuri.d.ts|
|新增API|NA|类名：fileUri；<br>API声明：function getUriFromPath(path: string): string;<br>差异内容：function getUriFromPath(path: string): string;|api/@ohos.file.fileuri.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace fileIo<br>差异内容：declare namespace fileIo|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：fileIo；<br>API声明：namespace OpenMode<br>差异内容：namespace OpenMode|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：OpenMode；<br>API声明：const READ_ONLY = 0o0;<br>差异内容：const READ_ONLY = 0o0;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：OpenMode；<br>API声明：const WRITE_ONLY = 0o1;<br>差异内容：const WRITE_ONLY = 0o1;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：OpenMode；<br>API声明：const READ_WRITE = 0o2;<br>差异内容：const READ_WRITE = 0o2;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：OpenMode；<br>API声明：const CREATE = 0o100;<br>差异内容：const CREATE = 0o100;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：OpenMode；<br>API声明：const TRUNC = 0o1000;<br>差异内容：const TRUNC = 0o1000;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：OpenMode；<br>API声明：const APPEND = 0o2000;<br>差异内容：const APPEND = 0o2000;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：OpenMode；<br>API声明：const NONBLOCK = 0o4000;<br>差异内容：const NONBLOCK = 0o4000;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：OpenMode；<br>API声明：const DIR = 0o200000;<br>差异内容：const DIR = 0o200000;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：OpenMode；<br>API声明：const NOFOLLOW = 0o400000;<br>差异内容：const NOFOLLOW = 0o400000;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：OpenMode；<br>API声明：const SYNC = 0o4010000;<br>差异内容：const SYNC = 0o4010000;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function access(path: string): Promise\<boolean>;<br>差异内容：declare function access(path: string): Promise\<boolean>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function access(path: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：declare function access(path: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function accessSync(path: string): boolean;<br>差异内容：declare function accessSync(path: string): boolean;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function close(file: number \| File): Promise\<void>;<br>差异内容：declare function close(file: number \| File): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function close(file: number \| File, callback: AsyncCallback\<void>): void;<br>差异内容：declare function close(file: number \| File, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function closeSync(file: number \| File): void;<br>差异内容：declare function closeSync(file: number \| File): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function copy(srcUri: string, destUri: string, options?: CopyOptions): Promise\<void>;<br>差异内容：declare function copy(srcUri: string, destUri: string, options?: CopyOptions): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function copy(srcUri: string, destUri: string, callback: AsyncCallback\<void>): void;<br>差异内容：declare function copy(srcUri: string, destUri: string, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function copy(srcUri: string, destUri: string, options: CopyOptions, callback: AsyncCallback\<void>): void;<br>差异内容：declare function copy(srcUri: string, destUri: string, options: CopyOptions, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function copyDir(src: string, dest: string, mode?: number): Promise\<void>;<br>差异内容：declare function copyDir(src: string, dest: string, mode?: number): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function copyDir(src: string, dest: string, callback: AsyncCallback\<void>): void;<br>差异内容：declare function copyDir(src: string, dest: string, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function copyDir(src: string, dest: string, callback: AsyncCallback\<void, Array\<ConflictFiles>>): void;<br>差异内容：declare function copyDir(src: string, dest: string, callback: AsyncCallback\<void, Array\<ConflictFiles>>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function copyDir(src: string, dest: string, mode: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function copyDir(src: string, dest: string, mode: number, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function copyDir(src: string, dest: string, mode: number, callback: AsyncCallback\<void, Array\<ConflictFiles>>): void;<br>差异内容：declare function copyDir(src: string, dest: string, mode: number, callback: AsyncCallback\<void, Array\<ConflictFiles>>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function copyDirSync(src: string, dest: string, mode?: number): void;<br>差异内容：declare function copyDirSync(src: string, dest: string, mode?: number): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function copyFile(src: string \| number, dest: string \| number, mode?: number): Promise\<void>;<br>差异内容：declare function copyFile(src: string \| number, dest: string \| number, mode?: number): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function copyFile(src: string \| number, dest: string \| number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function copyFile(src: string \| number, dest: string \| number, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function copyFile(src: string \| number, dest: string \| number, mode: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function copyFile(src: string \| number, dest: string \| number, mode: number, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function copyFileSync(src: string \| number, dest: string \| number, mode?: number): void;<br>差异内容：declare function copyFileSync(src: string \| number, dest: string \| number, mode?: number): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function createStream(path: string, mode: string): Promise\<Stream>;<br>差异内容：declare function createStream(path: string, mode: string): Promise\<Stream>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function createStream(path: string, mode: string, callback: AsyncCallback\<Stream>): void;<br>差异内容：declare function createStream(path: string, mode: string, callback: AsyncCallback\<Stream>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function createStreamSync(path: string, mode: string): Stream;<br>差异内容：declare function createStreamSync(path: string, mode: string): Stream;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function createRandomAccessFile(file: string \| File, mode?: number): Promise\<RandomAccessFile>;<br>差异内容：declare function createRandomAccessFile(file: string \| File, mode?: number): Promise\<RandomAccessFile>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function createRandomAccessFile(file: string \| File, callback: AsyncCallback\<RandomAccessFile>): void;<br>差异内容：declare function createRandomAccessFile(file: string \| File, callback: AsyncCallback\<RandomAccessFile>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function createRandomAccessFile(file: string \| File, mode: number, callback: AsyncCallback\<RandomAccessFile>): void;<br>差异内容：declare function createRandomAccessFile(file: string \| File, mode: number, callback: AsyncCallback\<RandomAccessFile>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function createRandomAccessFileSync(file: string \| File, mode?: number): RandomAccessFile;<br>差异内容：declare function createRandomAccessFileSync(file: string \| File, mode?: number): RandomAccessFile;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function createWatcher(path: string, events: number, listener: WatchEventListener): Watcher;<br>差异内容：declare function createWatcher(path: string, events: number, listener: WatchEventListener): Watcher;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function dup(fd: number): File;<br>差异内容：declare function dup(fd: number): File;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fdatasync(fd: number): Promise\<void>;<br>差异内容：declare function fdatasync(fd: number): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fdatasync(fd: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function fdatasync(fd: number, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fdatasyncSync(fd: number): void;<br>差异内容：declare function fdatasyncSync(fd: number): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fdopenStream(fd: number, mode: string): Promise\<Stream>;<br>差异内容：declare function fdopenStream(fd: number, mode: string): Promise\<Stream>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fdopenStream(fd: number, mode: string, callback: AsyncCallback\<Stream>): void;<br>差异内容：declare function fdopenStream(fd: number, mode: string, callback: AsyncCallback\<Stream>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fdopenStreamSync(fd: number, mode: string): Stream;<br>差异内容：declare function fdopenStreamSync(fd: number, mode: string): Stream;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fsync(fd: number): Promise\<void>;<br>差异内容：declare function fsync(fd: number): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fsync(fd: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function fsync(fd: number, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fsyncSync(fd: number): void;<br>差异内容：declare function fsyncSync(fd: number): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function listFile(path: string, options?: ListFileOptions): Promise\<string[]>;<br>差异内容：declare function listFile(path: string, options?: ListFileOptions): Promise\<string[]>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function listFile(path: string, callback: AsyncCallback\<string[]>): void;<br>差异内容：declare function listFile(path: string, callback: AsyncCallback\<string[]>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function listFile(path: string, options: ListFileOptions, callback: AsyncCallback\<string[]>): void;<br>差异内容：declare function listFile(path: string, options: ListFileOptions, callback: AsyncCallback\<string[]>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function listFileSync(path: string, options?: ListFileOptions): string[];<br>差异内容：declare function listFileSync(path: string, options?: ListFileOptions): string[];|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function lseek(fd: number, offset: number, whence?: WhenceType): number;<br>差异内容：declare function lseek(fd: number, offset: number, whence?: WhenceType): number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function lstat(path: string): Promise\<Stat>;<br>差异内容：declare function lstat(path: string): Promise\<Stat>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function lstat(path: string, callback: AsyncCallback\<Stat>): void;<br>差异内容：declare function lstat(path: string, callback: AsyncCallback\<Stat>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function lstatSync(path: string): Stat;<br>差异内容：declare function lstatSync(path: string): Stat;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function mkdir(path: string): Promise\<void>;<br>差异内容：declare function mkdir(path: string): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function mkdir(path: string, recursion: boolean): Promise\<void>;<br>差异内容：declare function mkdir(path: string, recursion: boolean): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function mkdir(path: string, callback: AsyncCallback\<void>): void;<br>差异内容：declare function mkdir(path: string, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function mkdir(path: string, recursion: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：declare function mkdir(path: string, recursion: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function mkdirSync(path: string): void;<br>差异内容：declare function mkdirSync(path: string): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function mkdirSync(path: string, recursion: boolean): void;<br>差异内容：declare function mkdirSync(path: string, recursion: boolean): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function mkdtemp(prefix: string): Promise\<string>;<br>差异内容：declare function mkdtemp(prefix: string): Promise\<string>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function mkdtemp(prefix: string, callback: AsyncCallback\<string>): void;<br>差异内容：declare function mkdtemp(prefix: string, callback: AsyncCallback\<string>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function mkdtempSync(prefix: string): string;<br>差异内容：declare function mkdtempSync(prefix: string): string;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function moveDir(src: string, dest: string, mode?: number): Promise\<void>;<br>差异内容：declare function moveDir(src: string, dest: string, mode?: number): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function moveDir(src: string, dest: string, callback: AsyncCallback\<void>): void;<br>差异内容：declare function moveDir(src: string, dest: string, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function moveDir(src: string, dest: string, callback: AsyncCallback\<void, Array\<ConflictFiles>>): void;<br>差异内容：declare function moveDir(src: string, dest: string, callback: AsyncCallback\<void, Array\<ConflictFiles>>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function moveDir(src: string, dest: string, mode: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function moveDir(src: string, dest: string, mode: number, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function moveDir(src: string, dest: string, mode: number, callback: AsyncCallback\<void, Array\<ConflictFiles>>): void;<br>差异内容：declare function moveDir(src: string, dest: string, mode: number, callback: AsyncCallback\<void, Array\<ConflictFiles>>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function moveDirSync(src: string, dest: string, mode?: number): void;<br>差异内容：declare function moveDirSync(src: string, dest: string, mode?: number): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function moveFile(src: string, dest: string, mode?: number): Promise\<void>;<br>差异内容：declare function moveFile(src: string, dest: string, mode?: number): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function moveFile(src: string, dest: string, callback: AsyncCallback\<void>): void;<br>差异内容：declare function moveFile(src: string, dest: string, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function moveFile(src: string, dest: string, mode: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function moveFile(src: string, dest: string, mode: number, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function moveFileSync(src: string, dest: string, mode?: number): void;<br>差异内容：declare function moveFileSync(src: string, dest: string, mode?: number): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function open(path: string, mode?: number): Promise\<File>;<br>差异内容：declare function open(path: string, mode?: number): Promise\<File>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function open(path: string, callback: AsyncCallback\<File>): void;<br>差异内容：declare function open(path: string, callback: AsyncCallback\<File>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function open(path: string, mode: number, callback: AsyncCallback\<File>): void;<br>差异内容：declare function open(path: string, mode: number, callback: AsyncCallback\<File>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function openSync(path: string, mode?: number): File;<br>差异内容：declare function openSync(path: string, mode?: number): File;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function read(fd: number, buffer: ArrayBuffer, options?: ReadOptions): Promise\<number>;<br>差异内容：declare function read(fd: number, buffer: ArrayBuffer, options?: ReadOptions): Promise\<number>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function read(fd: number, buffer: ArrayBuffer, callback: AsyncCallback\<number>): void;<br>差异内容：declare function read(fd: number, buffer: ArrayBuffer, callback: AsyncCallback\<number>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function read(fd: number, buffer: ArrayBuffer, options: ReadOptions, callback: AsyncCallback\<number>): void;<br>差异内容：declare function read(fd: number, buffer: ArrayBuffer, options: ReadOptions, callback: AsyncCallback\<number>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function readSync(fd: number, buffer: ArrayBuffer, options?: ReadOptions): number;<br>差异内容：declare function readSync(fd: number, buffer: ArrayBuffer, options?: ReadOptions): number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function readLines(filePath: string, options?: Options): Promise\<ReaderIterator>;<br>差异内容：declare function readLines(filePath: string, options?: Options): Promise\<ReaderIterator>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function readLines(filePath: string, callback: AsyncCallback\<ReaderIterator>): void;<br>差异内容：declare function readLines(filePath: string, callback: AsyncCallback\<ReaderIterator>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function readLines(filePath: string, options: Options, callback: AsyncCallback\<ReaderIterator>): void;<br>差异内容：declare function readLines(filePath: string, options: Options, callback: AsyncCallback\<ReaderIterator>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function readLinesSync(filePath: string, options?: Options): ReaderIterator;<br>差异内容：declare function readLinesSync(filePath: string, options?: Options): ReaderIterator;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function readText(filePath: string, options?: ReadTextOptions): Promise\<string>;<br>差异内容：declare function readText(filePath: string, options?: ReadTextOptions): Promise\<string>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function readText(filePath: string, callback: AsyncCallback\<string>): void;<br>差异内容：declare function readText(filePath: string, callback: AsyncCallback\<string>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function readText(filePath: string, options: ReadTextOptions, callback: AsyncCallback\<string>): void;<br>差异内容：declare function readText(filePath: string, options: ReadTextOptions, callback: AsyncCallback\<string>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function readTextSync(filePath: string, options?: ReadTextOptions): string;<br>差异内容：declare function readTextSync(filePath: string, options?: ReadTextOptions): string;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function rename(oldPath: string, newPath: string): Promise\<void>;<br>差异内容：declare function rename(oldPath: string, newPath: string): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function rename(oldPath: string, newPath: string, callback: AsyncCallback\<void>): void;<br>差异内容：declare function rename(oldPath: string, newPath: string, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function renameSync(oldPath: string, newPath: string): void;<br>差异内容：declare function renameSync(oldPath: string, newPath: string): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function rmdir(path: string): Promise\<void>;<br>差异内容：declare function rmdir(path: string): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function rmdir(path: string, callback: AsyncCallback\<void>): void;<br>差异内容：declare function rmdir(path: string, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function rmdirSync(path: string): void;<br>差异内容：declare function rmdirSync(path: string): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function stat(file: string \| number): Promise\<Stat>;<br>差异内容：declare function stat(file: string \| number): Promise\<Stat>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function stat(file: string \| number, callback: AsyncCallback\<Stat>): void;<br>差异内容：declare function stat(file: string \| number, callback: AsyncCallback\<Stat>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function statSync(file: string \| number): Stat;<br>差异内容：declare function statSync(file: string \| number): Stat;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function symlink(target: string, srcPath: string): Promise\<void>;<br>差异内容：declare function symlink(target: string, srcPath: string): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function symlink(target: string, srcPath: string, callback: AsyncCallback\<void>): void;<br>差异内容：declare function symlink(target: string, srcPath: string, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function symlinkSync(target: string, srcPath: string): void;<br>差异内容：declare function symlinkSync(target: string, srcPath: string): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function truncate(file: string \| number, len?: number): Promise\<void>;<br>差异内容：declare function truncate(file: string \| number, len?: number): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function truncate(file: string \| number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function truncate(file: string \| number, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function truncate(file: string \| number, len: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function truncate(file: string \| number, len: number, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function truncateSync(file: string \| number, len?: number): void;<br>差异内容：declare function truncateSync(file: string \| number, len?: number): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function unlink(path: string): Promise\<void>;<br>差异内容：declare function unlink(path: string): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function unlink(path: string, callback: AsyncCallback\<void>): void;<br>差异内容：declare function unlink(path: string, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function unlinkSync(path: string): void;<br>差异内容：declare function unlinkSync(path: string): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function utimes(path: string, mtime: number): void;<br>差异内容：declare function utimes(path: string, mtime: number): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function write(fd: number, buffer: ArrayBuffer \| string, options?: WriteOptions): Promise\<number>;<br>差异内容：declare function write(fd: number, buffer: ArrayBuffer \| string, options?: WriteOptions): Promise\<number>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function write(fd: number, buffer: ArrayBuffer \| string, callback: AsyncCallback\<number>): void;<br>差异内容：declare function write(fd: number, buffer: ArrayBuffer \| string, callback: AsyncCallback\<number>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function write(fd: number, buffer: ArrayBuffer \| string, options: WriteOptions, callback: AsyncCallback\<number>): void;<br>差异内容：declare function write(fd: number, buffer: ArrayBuffer \| string, options: WriteOptions, callback: AsyncCallback\<number>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function writeSync(fd: number, buffer: ArrayBuffer \| string, options?: WriteOptions): number;<br>差异内容：declare function writeSync(fd: number, buffer: ArrayBuffer \| string, options?: WriteOptions): number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：interface Progress<br>差异内容：interface Progress|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Progress；<br>API声明：readonly processedSize: number;<br>差异内容：readonly processedSize: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Progress；<br>API声明：readonly totalSize: number;<br>差异内容：readonly totalSize: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：interface CopyOptions<br>差异内容：interface CopyOptions|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：CopyOptions；<br>API声明：progressListener?: ProgressListener;<br>差异内容：progressListener?: ProgressListener;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：type ProgressListener = (progress: Progress) => void;<br>差异内容：type ProgressListener = (progress: Progress) => void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface File<br>差异内容：declare interface File|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：File；<br>API声明：readonly fd: number;<br>差异内容：readonly fd: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：File；<br>API声明：readonly path: string;<br>差异内容：readonly path: string;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：File；<br>API声明：readonly name: string;<br>差异内容：readonly name: string;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：File；<br>API声明：getParent(): string;<br>差异内容：getParent(): string;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：File；<br>API声明：lock(exclusive?: boolean): Promise\<void>;<br>差异内容：lock(exclusive?: boolean): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：File；<br>API声明：lock(callback: AsyncCallback\<void>): void;<br>差异内容：lock(callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：File；<br>API声明：lock(exclusive: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：lock(exclusive: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：File；<br>API声明：tryLock(exclusive?: boolean): void;<br>差异内容：tryLock(exclusive?: boolean): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：File；<br>API声明：unlock(): void;<br>差异内容：unlock(): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface RandomAccessFile<br>差异内容：declare interface RandomAccessFile|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：RandomAccessFile；<br>API声明：readonly fd: number;<br>差异内容：readonly fd: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：RandomAccessFile；<br>API声明：readonly filePointer: number;<br>差异内容：readonly filePointer: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：RandomAccessFile；<br>API声明：setFilePointer(filePointer: number): void;<br>差异内容：setFilePointer(filePointer: number): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：RandomAccessFile；<br>API声明：close(): void;<br>差异内容：close(): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：RandomAccessFile；<br>API声明：write(buffer: ArrayBuffer \| string, options?: WriteOptions): Promise\<number>;<br>差异内容：write(buffer: ArrayBuffer \| string, options?: WriteOptions): Promise\<number>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：RandomAccessFile；<br>API声明：write(buffer: ArrayBuffer \| string, callback: AsyncCallback\<number>): void;<br>差异内容：write(buffer: ArrayBuffer \| string, callback: AsyncCallback\<number>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：RandomAccessFile；<br>API声明：write(buffer: ArrayBuffer \| string, options: WriteOptions, callback: AsyncCallback\<number>): void;<br>差异内容：write(buffer: ArrayBuffer \| string, options: WriteOptions, callback: AsyncCallback\<number>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：RandomAccessFile；<br>API声明：writeSync(buffer: ArrayBuffer \| string, options?: WriteOptions): number;<br>差异内容：writeSync(buffer: ArrayBuffer \| string, options?: WriteOptions): number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：RandomAccessFile；<br>API声明：read(buffer: ArrayBuffer, options?: ReadOptions): Promise\<number>;<br>差异内容：read(buffer: ArrayBuffer, options?: ReadOptions): Promise\<number>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：RandomAccessFile；<br>API声明：read(buffer: ArrayBuffer, callback: AsyncCallback\<number>): void;<br>差异内容：read(buffer: ArrayBuffer, callback: AsyncCallback\<number>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：RandomAccessFile；<br>API声明：read(buffer: ArrayBuffer, options: ReadOptions, callback: AsyncCallback\<number>): void;<br>差异内容：read(buffer: ArrayBuffer, options: ReadOptions, callback: AsyncCallback\<number>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：RandomAccessFile；<br>API声明：readSync(buffer: ArrayBuffer, options?: ReadOptions): number;<br>差异内容：readSync(buffer: ArrayBuffer, options?: ReadOptions): number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface Stat<br>差异内容：declare interface Stat|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly ino: bigint;<br>差异内容：readonly ino: bigint;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly mode: number;<br>差异内容：readonly mode: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly uid: number;<br>差异内容：readonly uid: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly gid: number;<br>差异内容：readonly gid: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly size: number;<br>差异内容：readonly size: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly atime: number;<br>差异内容：readonly atime: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly mtime: number;<br>差异内容：readonly mtime: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly ctime: number;<br>差异内容：readonly ctime: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly location: LocationType;<br>差异内容：readonly location: LocationType;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：isBlockDevice(): boolean;<br>差异内容：isBlockDevice(): boolean;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：isCharacterDevice(): boolean;<br>差异内容：isCharacterDevice(): boolean;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：isDirectory(): boolean;<br>差异内容：isDirectory(): boolean;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：isFIFO(): boolean;<br>差异内容：isFIFO(): boolean;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：isFile(): boolean;<br>差异内容：isFile(): boolean;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：isSocket(): boolean;<br>差异内容：isSocket(): boolean;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：isSymbolicLink(): boolean;<br>差异内容：isSymbolicLink(): boolean;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface Stream<br>差异内容：declare interface Stream|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stream；<br>API声明：close(): Promise\<void>;<br>差异内容：close(): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stream；<br>API声明：close(callback: AsyncCallback\<void>): void;<br>差异内容：close(callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stream；<br>API声明：closeSync(): void;<br>差异内容：closeSync(): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stream；<br>API声明：flush(): Promise\<void>;<br>差异内容：flush(): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stream；<br>API声明：flush(callback: AsyncCallback\<void>): void;<br>差异内容：flush(callback: AsyncCallback\<void>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stream；<br>API声明：flushSync(): void;<br>差异内容：flushSync(): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stream；<br>API声明：write(buffer: ArrayBuffer \| string, options?: WriteOptions): Promise\<number>;<br>差异内容：write(buffer: ArrayBuffer \| string, options?: WriteOptions): Promise\<number>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stream；<br>API声明：write(buffer: ArrayBuffer \| string, callback: AsyncCallback\<number>): void;<br>差异内容：write(buffer: ArrayBuffer \| string, callback: AsyncCallback\<number>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stream；<br>API声明：write(buffer: ArrayBuffer \| string, options: WriteOptions, callback: AsyncCallback\<number>): void;<br>差异内容：write(buffer: ArrayBuffer \| string, options: WriteOptions, callback: AsyncCallback\<number>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stream；<br>API声明：writeSync(buffer: ArrayBuffer \| string, options?: WriteOptions): number;<br>差异内容：writeSync(buffer: ArrayBuffer \| string, options?: WriteOptions): number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, options?: ReadOptions): Promise\<number>;<br>差异内容：read(buffer: ArrayBuffer, options?: ReadOptions): Promise\<number>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, callback: AsyncCallback\<number>): void;<br>差异内容：read(buffer: ArrayBuffer, callback: AsyncCallback\<number>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, options: ReadOptions, callback: AsyncCallback\<number>): void;<br>差异内容：read(buffer: ArrayBuffer, options: ReadOptions, callback: AsyncCallback\<number>): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stream；<br>API声明：readSync(buffer: ArrayBuffer, options?: ReadOptions): number;<br>差异内容：readSync(buffer: ArrayBuffer, options?: ReadOptions): number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface WatchEventListener<br>差异内容：export interface WatchEventListener|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface WatchEvent<br>差异内容：export interface WatchEvent|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：WatchEvent；<br>API声明：readonly fileName: string;<br>差异内容：readonly fileName: string;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：WatchEvent；<br>API声明：readonly event: number;<br>差异内容：readonly event: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：WatchEvent；<br>API声明：readonly cookie: number;<br>差异内容：readonly cookie: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Watcher<br>差异内容：export interface Watcher|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Watcher；<br>API声明：start(): void;<br>差异内容：start(): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Watcher；<br>API声明：stop(): void;<br>差异内容：stop(): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface ReaderIteratorResult<br>差异内容：export interface ReaderIteratorResult|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：ReaderIteratorResult；<br>API声明：done: boolean;<br>差异内容：done: boolean;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：ReaderIteratorResult；<br>API声明：value: string;<br>差异内容：value: string;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface ReaderIterator<br>差异内容：declare interface ReaderIterator|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：ReaderIterator；<br>API声明：next(): ReaderIteratorResult;<br>差异内容：next(): ReaderIteratorResult;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Filter<br>差异内容：export interface Filter|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Filter；<br>API声明：suffix?: Array\<string>;<br>差异内容：suffix?: Array\<string>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Filter；<br>API声明：displayName?: Array\<string>;<br>差异内容：displayName?: Array\<string>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Filter；<br>API声明：mimeType?: Array\<string>;<br>差异内容：mimeType?: Array\<string>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Filter；<br>API声明：fileSizeOver?: number;<br>差异内容：fileSizeOver?: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Filter；<br>API声明：lastModifiedAfter?: number;<br>差异内容：lastModifiedAfter?: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Filter；<br>API声明：excludeMedia?: boolean;<br>差异内容：excludeMedia?: boolean;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface ConflictFiles<br>差异内容：export interface ConflictFiles|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：ConflictFiles；<br>API声明：srcFile: string;<br>差异内容：srcFile: string;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：ConflictFiles；<br>API声明：destFile: string;<br>差异内容：destFile: string;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Options<br>差异内容：export interface Options|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Options；<br>API声明：encoding?: string;<br>差异内容：encoding?: string;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface ReadOptions<br>差异内容：export interface ReadOptions|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：ReadOptions；<br>API声明：offset?: number;<br>差异内容：offset?: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：ReadOptions；<br>API声明：length?: number;<br>差异内容：length?: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface ReadTextOptions<br>差异内容：export interface ReadTextOptions|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：ReadTextOptions；<br>API声明：encoding?: string;<br>差异内容：encoding?: string;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface WriteOptions<br>差异内容：export interface WriteOptions|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：WriteOptions；<br>API声明：offset?: number;<br>差异内容：offset?: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：WriteOptions；<br>API声明：length?: number;<br>差异内容：length?: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface ListFileOptions<br>差异内容：export interface ListFileOptions|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：ListFileOptions；<br>API声明：recursion?: boolean;<br>差异内容：recursion?: boolean;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：ListFileOptions；<br>API声明：listNum?: number;<br>差异内容：listNum?: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：ListFileOptions；<br>API声明：filter?: Filter;<br>差异内容：filter?: Filter;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum WhenceType<br>差异内容：declare enum WhenceType|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：WhenceType；<br>API声明：SEEK_SET = 0<br>差异内容：SEEK_SET = 0|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：WhenceType；<br>API声明：SEEK_CUR = 1<br>差异内容：SEEK_CUR = 1|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：WhenceType；<br>API声明：SEEK_END = 2<br>差异内容：SEEK_END = 2|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum LocationType<br>差异内容：declare enum LocationType|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：LocationType；<br>API声明：LOCAL = 1 \<\< 0<br>差异内容：LOCAL = 1 \<\< 0|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：LocationType；<br>API声明：CLOUD = 1 \<\< 1<br>差异内容：CLOUD = 1 \<\< 1|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace hash<br>差异内容：declare namespace hash|api/@ohos.file.hash.d.ts|
|新增API|NA|类名：hash；<br>API声明：function hash(path: string, algorithm: string): Promise\<string>;<br>差异内容：function hash(path: string, algorithm: string): Promise\<string>;|api/@ohos.file.hash.d.ts|
|新增API|NA|类名：hash；<br>API声明：function hash(path: string, algorithm: string, callback: AsyncCallback\<string>): void;<br>差异内容：function hash(path: string, algorithm: string, callback: AsyncCallback\<string>): void;|api/@ohos.file.hash.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace picker<br>差异内容：declare namespace picker|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：picker；<br>API声明：export enum PhotoViewMIMETypes<br>差异内容：export enum PhotoViewMIMETypes|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：PhotoViewMIMETypes；<br>API声明：IMAGE_TYPE = 'image/*'<br>差异内容：IMAGE_TYPE = 'image/*'|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：PhotoViewMIMETypes；<br>API声明：VIDEO_TYPE = 'video/*'<br>差异内容：VIDEO_TYPE = 'video/*'|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：PhotoViewMIMETypes；<br>API声明：IMAGE_VIDEO_TYPE = '*/*'<br>差异内容：IMAGE_VIDEO_TYPE = '*/*'|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：picker；<br>API声明：class PhotoSelectOptions<br>差异内容：class PhotoSelectOptions|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：PhotoSelectOptions；<br>API声明：MIMEType?: PhotoViewMIMETypes;<br>差异内容：MIMEType?: PhotoViewMIMETypes;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：PhotoSelectOptions；<br>API声明：maxSelectNumber?: number;<br>差异内容：maxSelectNumber?: number;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：picker；<br>API声明：class PhotoSelectResult<br>差异内容：class PhotoSelectResult|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：PhotoSelectResult；<br>API声明：photoUris: Array\<string>;<br>差异内容：photoUris: Array\<string>;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：PhotoSelectResult；<br>API声明：isOriginalPhoto: boolean;<br>差异内容：isOriginalPhoto: boolean;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：picker；<br>API声明：class PhotoSaveOptions<br>差异内容：class PhotoSaveOptions|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：PhotoSaveOptions；<br>API声明：newFileNames?: Array\<string>;<br>差异内容：newFileNames?: Array\<string>;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：picker；<br>API声明：class PhotoViewPicker<br>差异内容：class PhotoViewPicker|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：PhotoViewPicker；<br>API声明：select(option?: PhotoSelectOptions): Promise\<PhotoSelectResult>;<br>差异内容：select(option?: PhotoSelectOptions): Promise\<PhotoSelectResult>;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：PhotoViewPicker；<br>API声明：select(option: PhotoSelectOptions, callback: AsyncCallback\<PhotoSelectResult>): void;<br>差异内容：select(option: PhotoSelectOptions, callback: AsyncCallback\<PhotoSelectResult>): void;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：PhotoViewPicker；<br>API声明：select(callback: AsyncCallback\<PhotoSelectResult>): void;<br>差异内容：select(callback: AsyncCallback\<PhotoSelectResult>): void;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：PhotoViewPicker；<br>API声明：save(option?: PhotoSaveOptions): Promise\<Array\<string>>;<br>差异内容：save(option?: PhotoSaveOptions): Promise\<Array\<string>>;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：PhotoViewPicker；<br>API声明：save(option: PhotoSaveOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：save(option: PhotoSaveOptions, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：PhotoViewPicker；<br>API声明：save(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：save(callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：picker；<br>API声明：export enum DocumentSelectMode<br>差异内容：export enum DocumentSelectMode|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentSelectMode；<br>API声明：FILE = 0<br>差异内容：FILE = 0|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentSelectMode；<br>API声明：FOLDER = 1<br>差异内容：FOLDER = 1|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentSelectMode；<br>API声明：MIXED = 2<br>差异内容：MIXED = 2|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：picker；<br>API声明：class DocumentSelectOptions<br>差异内容：class DocumentSelectOptions|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentSelectOptions；<br>API声明：defaultFilePathUri?: string;<br>差异内容：defaultFilePathUri?: string;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentSelectOptions；<br>API声明：fileSuffixFilters?: Array\<string>;<br>差异内容：fileSuffixFilters?: Array\<string>;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentSelectOptions；<br>API声明：maxSelectNumber?: number;<br>差异内容：maxSelectNumber?: number;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentSelectOptions；<br>API声明：selectMode?: DocumentSelectMode;<br>差异内容：selectMode?: DocumentSelectMode;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：picker；<br>API声明：class DocumentSaveOptions<br>差异内容：class DocumentSaveOptions|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentSaveOptions；<br>API声明：newFileNames?: Array\<string>;<br>差异内容：newFileNames?: Array\<string>;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentSaveOptions；<br>API声明：defaultFilePathUri?: string;<br>差异内容：defaultFilePathUri?: string;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentSaveOptions；<br>API声明：fileSuffixChoices?: Array\<string>;<br>差异内容：fileSuffixChoices?: Array\<string>;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：picker；<br>API声明：class DocumentViewPicker<br>差异内容：class DocumentViewPicker|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentViewPicker；<br>API声明：select(option?: DocumentSelectOptions): Promise\<Array\<string>>;<br>差异内容：select(option?: DocumentSelectOptions): Promise\<Array\<string>>;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentViewPicker；<br>API声明：select(option: DocumentSelectOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：select(option: DocumentSelectOptions, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentViewPicker；<br>API声明：select(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：select(callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentViewPicker；<br>API声明：save(option?: DocumentSaveOptions): Promise\<Array\<string>>;<br>差异内容：save(option?: DocumentSaveOptions): Promise\<Array\<string>>;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentViewPicker；<br>API声明：save(option: DocumentSaveOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：save(option: DocumentSaveOptions, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentViewPicker；<br>API声明：save(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：save(callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：picker；<br>API声明：class AudioSelectOptions<br>差异内容：class AudioSelectOptions|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：picker；<br>API声明：class AudioSaveOptions<br>差异内容：class AudioSaveOptions|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：AudioSaveOptions；<br>API声明：newFileNames?: Array\<string>;<br>差异内容：newFileNames?: Array\<string>;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：picker；<br>API声明：class AudioViewPicker<br>差异内容：class AudioViewPicker|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：AudioViewPicker；<br>API声明：select(option?: AudioSelectOptions): Promise\<Array\<string>>;<br>差异内容：select(option?: AudioSelectOptions): Promise\<Array\<string>>;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：AudioViewPicker；<br>API声明：select(option: AudioSelectOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：select(option: AudioSelectOptions, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：AudioViewPicker；<br>API声明：select(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：select(callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：AudioViewPicker；<br>API声明：save(option?: AudioSaveOptions): Promise\<Array\<string>>;<br>差异内容：save(option?: AudioSaveOptions): Promise\<Array\<string>>;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：AudioViewPicker；<br>API声明：save(option: AudioSaveOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：save(option: AudioSaveOptions, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：AudioViewPicker；<br>API声明：save(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：save(callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace securityLabel<br>差异内容：declare namespace securityLabel|api/@ohos.file.securityLabel.d.ts|
|新增API|NA|类名：securityLabel；<br>API声明：type DataLevel = 's0' \| 's1' \| 's2' \| 's3' \| 's4';<br>差异内容：type DataLevel = 's0' \| 's1' \| 's2' \| 's3' \| 's4';|api/@ohos.file.securityLabel.d.ts|
|新增API|NA|类名：securityLabel；<br>API声明：function setSecurityLabel(path: string, type: DataLevel): Promise\<void>;<br>差异内容：function setSecurityLabel(path: string, type: DataLevel): Promise\<void>;|api/@ohos.file.securityLabel.d.ts|
|新增API|NA|类名：securityLabel；<br>API声明：function setSecurityLabel(path: string, type: DataLevel, callback: AsyncCallback\<void>): void;<br>差异内容：function setSecurityLabel(path: string, type: DataLevel, callback: AsyncCallback\<void>): void;|api/@ohos.file.securityLabel.d.ts|
|新增API|NA|类名：securityLabel；<br>API声明：function setSecurityLabelSync(path: string, type: DataLevel): void;<br>差异内容：function setSecurityLabelSync(path: string, type: DataLevel): void;|api/@ohos.file.securityLabel.d.ts|
|新增API|NA|类名：securityLabel；<br>API声明：function getSecurityLabel(path: string): Promise\<string>;<br>差异内容：function getSecurityLabel(path: string): Promise\<string>;|api/@ohos.file.securityLabel.d.ts|
|新增API|NA|类名：securityLabel；<br>API声明：function getSecurityLabel(path: string, callback: AsyncCallback\<string>): void;<br>差异内容：function getSecurityLabel(path: string, callback: AsyncCallback\<string>): void;|api/@ohos.file.securityLabel.d.ts|
|新增API|NA|类名：securityLabel；<br>API声明：function getSecurityLabelSync(path: string): string;<br>差异内容：function getSecurityLabelSync(path: string): string;|api/@ohos.file.securityLabel.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace statfs<br>差异内容：declare namespace statfs|api/@ohos.file.statvfs.d.ts|
|新增API|NA|类名：statfs；<br>API声明：function getFreeSize(path: string): Promise\<number>;<br>差异内容：function getFreeSize(path: string): Promise\<number>;|api/@ohos.file.statvfs.d.ts|
|新增API|NA|类名：statfs；<br>API声明：function getFreeSize(path: string, callback: AsyncCallback\<number>): void;<br>差异内容：function getFreeSize(path: string, callback: AsyncCallback\<number>): void;|api/@ohos.file.statvfs.d.ts|
|新增API|NA|类名：statfs；<br>API声明：function getFreeSizeSync(path: string): number;<br>差异内容：function getFreeSizeSync(path: string): number;|api/@ohos.file.statvfs.d.ts|
|新增API|NA|类名：statfs；<br>API声明：function getTotalSize(path: string): Promise\<number>;<br>差异内容：function getTotalSize(path: string): Promise\<number>;|api/@ohos.file.statvfs.d.ts|
|新增API|NA|类名：statfs；<br>API声明：function getTotalSize(path: string, callback: AsyncCallback\<number>): void;<br>差异内容：function getTotalSize(path: string, callback: AsyncCallback\<number>): void;|api/@ohos.file.statvfs.d.ts|
|新增API|NA|类名：statfs；<br>API声明：function getTotalSizeSync(path: string): number;<br>差异内容：function getTotalSizeSync(path: string): number;|api/@ohos.file.statvfs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace storageStatistics<br>差异内容：declare namespace storageStatistics|api/@ohos.file.storageStatistics.d.ts|
|新增API|NA|类名：storageStatistics；<br>API声明：export interface BundleStats<br>差异内容：export interface BundleStats|api/@ohos.file.storageStatistics.d.ts|
|新增API|NA|类名：BundleStats；<br>API声明：appSize: number;<br>差异内容：appSize: number;|api/@ohos.file.storageStatistics.d.ts|
|新增API|NA|类名：BundleStats；<br>API声明：cacheSize: number;<br>差异内容：cacheSize: number;|api/@ohos.file.storageStatistics.d.ts|
|新增API|NA|类名：BundleStats；<br>API声明：dataSize: number;<br>差异内容：dataSize: number;|api/@ohos.file.storageStatistics.d.ts|
|新增API|NA|类名：storageStatistics；<br>API声明：function getCurrentBundleStats(callback: AsyncCallback\<BundleStats>): void;<br>差异内容：function getCurrentBundleStats(callback: AsyncCallback\<BundleStats>): void;|api/@ohos.file.storageStatistics.d.ts|
|新增API|NA|类名：storageStatistics；<br>API声明：function getCurrentBundleStats(): Promise\<BundleStats>;<br>差异内容：function getCurrentBundleStats(): Promise\<BundleStats>;|api/@ohos.file.storageStatistics.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace fileIO<br>差异内容：declare namespace fileIO|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function access(path: string, mode?: number): Promise\<void>;<br>差异内容：declare function access(path: string, mode?: number): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function access(path: string, callback: AsyncCallback\<void>): void;<br>差异内容：declare function access(path: string, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function access(path: string, mode: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function access(path: string, mode: number, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function accessSync(path: string, mode?: number): void;<br>差异内容：declare function accessSync(path: string, mode?: number): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function close(fd: number): Promise\<void>;<br>差异内容：declare function close(fd: number): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function close(fd: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function close(fd: number, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function closeSync(fd: number): void;<br>差异内容：declare function closeSync(fd: number): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function copyFile(src: string \| number, dest: string \| number, mode?: number): Promise\<void>;<br>差异内容：declare function copyFile(src: string \| number, dest: string \| number, mode?: number): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function copyFile(src: string \| number, dest: string \| number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function copyFile(src: string \| number, dest: string \| number, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function copyFile(src: string \| number, dest: string \| number, mode: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function copyFile(src: string \| number, dest: string \| number, mode: number, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function copyFileSync(src: string \| number, dest: string \| number, mode?: number): void;<br>差异内容：declare function copyFileSync(src: string \| number, dest: string \| number, mode?: number): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function createStream(path: string, mode: string): Promise\<Stream>;<br>差异内容：declare function createStream(path: string, mode: string): Promise\<Stream>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function createStream(path: string, mode: string, callback: AsyncCallback\<Stream>): void;<br>差异内容：declare function createStream(path: string, mode: string, callback: AsyncCallback\<Stream>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function createStreamSync(path: string, mode: string): Stream;<br>差异内容：declare function createStreamSync(path: string, mode: string): Stream;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function chown(path: string, uid: number, gid: number): Promise\<void>;<br>差异内容：declare function chown(path: string, uid: number, gid: number): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function chown(path: string, uid: number, gid: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function chown(path: string, uid: number, gid: number, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function chownSync(path: string, uid: number, gid: number): void;<br>差异内容：declare function chownSync(path: string, uid: number, gid: number): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function chmod(path: string, mode: number): Promise\<void>;<br>差异内容：declare function chmod(path: string, mode: number): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function chmod(path: string, mode: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function chmod(path: string, mode: number, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function chmodSync(path: string, mode: number): void;<br>差异内容：declare function chmodSync(path: string, mode: number): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function ftruncate(fd: number, len?: number): Promise\<void>;<br>差异内容：declare function ftruncate(fd: number, len?: number): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function ftruncate(fd: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function ftruncate(fd: number, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function ftruncate(fd: number, len: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function ftruncate(fd: number, len: number, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function ftruncateSync(fd: number, len?: number): void;<br>差异内容：declare function ftruncateSync(fd: number, len?: number): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fsync(fd: number): Promise\<void>;<br>差异内容：declare function fsync(fd: number): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fsync(fd: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function fsync(fd: number, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fsyncSync(fd: number): void;<br>差异内容：declare function fsyncSync(fd: number): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fstat(fd: number): Promise\<Stat>;<br>差异内容：declare function fstat(fd: number): Promise\<Stat>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fstat(fd: number, callback: AsyncCallback\<Stat>): void;<br>差异内容：declare function fstat(fd: number, callback: AsyncCallback\<Stat>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fstatSync(fd: number): Stat;<br>差异内容：declare function fstatSync(fd: number): Stat;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fdatasync(fd: number): Promise\<void>;<br>差异内容：declare function fdatasync(fd: number): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fdatasync(fd: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function fdatasync(fd: number, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fdatasyncSync(fd: number): void;<br>差异内容：declare function fdatasyncSync(fd: number): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fchown(fd: number, uid: number, gid: number): Promise\<void>;<br>差异内容：declare function fchown(fd: number, uid: number, gid: number): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fchown(fd: number, uid: number, gid: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function fchown(fd: number, uid: number, gid: number, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fchownSync(fd: number, uid: number, gid: number): void;<br>差异内容：declare function fchownSync(fd: number, uid: number, gid: number): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fchmod(fd: number, mode: number): Promise\<void>;<br>差异内容：declare function fchmod(fd: number, mode: number): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fchmod(fd: number, mode: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function fchmod(fd: number, mode: number, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fchmodSync(fd: number, mode: number): void;<br>差异内容：declare function fchmodSync(fd: number, mode: number): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fdopenStream(fd: number, mode: string): Promise\<Stream>;<br>差异内容：declare function fdopenStream(fd: number, mode: string): Promise\<Stream>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fdopenStream(fd: number, mode: string, callback: AsyncCallback\<Stream>): void;<br>差异内容：declare function fdopenStream(fd: number, mode: string, callback: AsyncCallback\<Stream>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function fdopenStreamSync(fd: number, mode: string): Stream;<br>差异内容：declare function fdopenStreamSync(fd: number, mode: string): Stream;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function hash(path: string, algorithm: string): Promise\<string>;<br>差异内容：declare function hash(path: string, algorithm: string): Promise\<string>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function hash(path: string, algorithm: string, callback: AsyncCallback\<string>): void;<br>差异内容：declare function hash(path: string, algorithm: string, callback: AsyncCallback\<string>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function lchown(path: string, uid: number, gid: number): Promise\<void>;<br>差异内容：declare function lchown(path: string, uid: number, gid: number): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function lchown(path: string, uid: number, gid: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function lchown(path: string, uid: number, gid: number, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function lchownSync(path: string, uid: number, gid: number): void;<br>差异内容：declare function lchownSync(path: string, uid: number, gid: number): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function lstat(path: string): Promise\<Stat>;<br>差异内容：declare function lstat(path: string): Promise\<Stat>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function lstat(path: string, callback: AsyncCallback\<Stat>): void;<br>差异内容：declare function lstat(path: string, callback: AsyncCallback\<Stat>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function lstatSync(path: string): Stat;<br>差异内容：declare function lstatSync(path: string): Stat;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function mkdir(path: string, mode?: number): Promise\<void>;<br>差异内容：declare function mkdir(path: string, mode?: number): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function mkdir(path: string, callback: AsyncCallback\<void>): void;<br>差异内容：declare function mkdir(path: string, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function mkdir(path: string, mode: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function mkdir(path: string, mode: number, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function mkdirSync(path: string, mode?: number): void;<br>差异内容：declare function mkdirSync(path: string, mode?: number): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function mkdtemp(prefix: string): Promise\<string>;<br>差异内容：declare function mkdtemp(prefix: string): Promise\<string>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function mkdtemp(prefix: string, callback: AsyncCallback\<string>): void;<br>差异内容：declare function mkdtemp(prefix: string, callback: AsyncCallback\<string>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function mkdtempSync(prefix: string): string;<br>差异内容：declare function mkdtempSync(prefix: string): string;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function open(path: string, flags?: number, mode?: number): Promise\<number>;<br>差异内容：declare function open(path: string, flags?: number, mode?: number): Promise\<number>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function open(path: string, callback: AsyncCallback\<number>): void;<br>差异内容：declare function open(path: string, callback: AsyncCallback\<number>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function open(path: string, flags: number, callback: AsyncCallback\<number>): void;<br>差异内容：declare function open(path: string, flags: number, callback: AsyncCallback\<number>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function open(path: string, flags: number, mode: number, callback: AsyncCallback\<number>): void;<br>差异内容：declare function open(path: string, flags: number, mode: number, callback: AsyncCallback\<number>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function openSync(path: string, flags?: number, mode?: number): number;<br>差异内容：declare function openSync(path: string, flags?: number, mode?: number): number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function opendir(path: string): Promise\<Dir>;<br>差异内容：declare function opendir(path: string): Promise\<Dir>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function opendir(path: string, callback: AsyncCallback\<Dir>): void;<br>差异内容：declare function opendir(path: string, callback: AsyncCallback\<Dir>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function opendirSync(path: string): Dir;<br>差异内容：declare function opendirSync(path: string): Dir;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function readText(filePath: string, options?: {<br>    position?: number;<br>    length?: number;<br>    encoding?: string;<br>}): Promise\<string>;<br>差异内容：declare function readText(filePath: string, options?: {<br>    position?: number;<br>    length?: number;<br>    encoding?: string;<br>}): Promise\<string>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function readText(filePath: string, options: {<br>    position?: number;<br>    length?: number;<br>    encoding?: string;<br>}, callback: AsyncCallback\<string>): void;<br>差异内容：declare function readText(filePath: string, options: {<br>    position?: number;<br>    length?: number;<br>    encoding?: string;<br>}, callback: AsyncCallback\<string>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function readTextSync(filePath: string, options?: {<br>    position?: number;<br>    length?: number;<br>    encoding?: string;<br>}): string;<br>差异内容：declare function readTextSync(filePath: string, options?: {<br>    position?: number;<br>    length?: number;<br>    encoding?: string;<br>}): string;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function read(fd: number, buffer: ArrayBuffer, options?: {<br>    offset?: number;<br>    length?: number;<br>    position?: number;<br>}): Promise\<ReadOut>;<br>差异内容：declare function read(fd: number, buffer: ArrayBuffer, options?: {<br>    offset?: number;<br>    length?: number;<br>    position?: number;<br>}): Promise\<ReadOut>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function read(fd: number, buffer: ArrayBuffer, callback: AsyncCallback\<ReadOut>): void;<br>差异内容：declare function read(fd: number, buffer: ArrayBuffer, callback: AsyncCallback\<ReadOut>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function read(fd: number, buffer: ArrayBuffer, options: {<br>    offset?: number;<br>    length?: number;<br>    position?: number;<br>}, callback: AsyncCallback\<ReadOut>): void;<br>差异内容：declare function read(fd: number, buffer: ArrayBuffer, options: {<br>    offset?: number;<br>    length?: number;<br>    position?: number;<br>}, callback: AsyncCallback\<ReadOut>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function readSync(fd: number, buffer: ArrayBuffer, options?: {<br>    offset?: number;<br>    length?: number;<br>    position?: number;<br>}): number;<br>差异内容：declare function readSync(fd: number, buffer: ArrayBuffer, options?: {<br>    offset?: number;<br>    length?: number;<br>    position?: number;<br>}): number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function rename(oldPath: string, newPath: string): Promise\<void>;<br>差异内容：declare function rename(oldPath: string, newPath: string): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function rename(oldPath: string, newPath: string, callback: AsyncCallback\<void>): void;<br>差异内容：declare function rename(oldPath: string, newPath: string, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function renameSync(oldPath: string, newPath: string): void;<br>差异内容：declare function renameSync(oldPath: string, newPath: string): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function rmdir(path: string): Promise\<void>;<br>差异内容：declare function rmdir(path: string): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function rmdir(path: string, callback: AsyncCallback\<void>): void;<br>差异内容：declare function rmdir(path: string, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function rmdirSync(path: string): void;<br>差异内容：declare function rmdirSync(path: string): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function stat(path: string): Promise\<Stat>;<br>差异内容：declare function stat(path: string): Promise\<Stat>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function stat(path: string, callback: AsyncCallback\<Stat>): void;<br>差异内容：declare function stat(path: string, callback: AsyncCallback\<Stat>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function statSync(path: string): Stat;<br>差异内容：declare function statSync(path: string): Stat;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function symlink(target: string, srcPath: string): Promise\<void>;<br>差异内容：declare function symlink(target: string, srcPath: string): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function symlink(target: string, srcPath: string, callback: AsyncCallback\<void>): void;<br>差异内容：declare function symlink(target: string, srcPath: string, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function symlinkSync(target: string, srcPath: string): void;<br>差异内容：declare function symlinkSync(target: string, srcPath: string): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function truncate(path: string, len?: number): Promise\<void>;<br>差异内容：declare function truncate(path: string, len?: number): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function truncate(path: string, callback: AsyncCallback\<void>): void;<br>差异内容：declare function truncate(path: string, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function truncate(path: string, len: number, callback: AsyncCallback\<void>): void;<br>差异内容：declare function truncate(path: string, len: number, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function truncateSync(path: string, len?: number): void;<br>差异内容：declare function truncateSync(path: string, len?: number): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function unlink(path: string): Promise\<void>;<br>差异内容：declare function unlink(path: string): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function unlink(path: string, callback: AsyncCallback\<void>): void;<br>差异内容：declare function unlink(path: string, callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function unlinkSync(path: string): void;<br>差异内容：declare function unlinkSync(path: string): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function write(fd: number, buffer: ArrayBuffer \| string, options?: {<br>    offset?: number;<br>    length?: number;<br>    position?: number;<br>    encoding?: string;<br>}): Promise\<number>;<br>差异内容：declare function write(fd: number, buffer: ArrayBuffer \| string, options?: {<br>    offset?: number;<br>    length?: number;<br>    position?: number;<br>    encoding?: string;<br>}): Promise\<number>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function write(fd: number, buffer: ArrayBuffer \| string, callback: AsyncCallback\<number>): void;<br>差异内容：declare function write(fd: number, buffer: ArrayBuffer \| string, callback: AsyncCallback\<number>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function write(fd: number, buffer: ArrayBuffer \| string, options: {<br>    offset?: number;<br>    length?: number;<br>    position?: number;<br>    encoding?: string;<br>}, callback: AsyncCallback\<number>): void;<br>差异内容：declare function write(fd: number, buffer: ArrayBuffer \| string, options: {<br>    offset?: number;<br>    length?: number;<br>    position?: number;<br>    encoding?: string;<br>}, callback: AsyncCallback\<number>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function writeSync(fd: number, buffer: ArrayBuffer \| string, options?: {<br>    offset?: number;<br>    length?: number;<br>    position?: number;<br>    encoding?: string;<br>}): number;<br>差异内容：declare function writeSync(fd: number, buffer: ArrayBuffer \| string, options?: {<br>    offset?: number;<br>    length?: number;<br>    position?: number;<br>    encoding?: string;<br>}): number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function createWatcher(filename: string, events: number, callback: AsyncCallback\<number>): Watcher;<br>差异内容：declare function createWatcher(filename: string, events: number, callback: AsyncCallback\<number>): Watcher;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface Dir<br>差异内容：declare interface Dir|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Dir；<br>API声明：read(): Promise\<Dirent>;<br>差异内容：read(): Promise\<Dirent>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Dir；<br>API声明：read(callback: AsyncCallback\<Dirent>): void;<br>差异内容：read(callback: AsyncCallback\<Dirent>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Dir；<br>API声明：readSync(): Dirent;<br>差异内容：readSync(): Dirent;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Dir；<br>API声明：close(): Promise\<void>;<br>差异内容：close(): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Dir；<br>API声明：close(callback: AsyncCallback\<void>): void;<br>差异内容：close(callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Dir；<br>API声明：closeSync(): void;<br>差异内容：closeSync(): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface Dirent<br>差异内容：declare interface Dirent|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Dirent；<br>API声明：readonly name: string;<br>差异内容：readonly name: string;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Dirent；<br>API声明：isBlockDevice(): boolean;<br>差异内容：isBlockDevice(): boolean;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Dirent；<br>API声明：isCharacterDevice(): boolean;<br>差异内容：isCharacterDevice(): boolean;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Dirent；<br>API声明：isDirectory(): boolean;<br>差异内容：isDirectory(): boolean;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Dirent；<br>API声明：isFIFO(): boolean;<br>差异内容：isFIFO(): boolean;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Dirent；<br>API声明：isFile(): boolean;<br>差异内容：isFile(): boolean;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Dirent；<br>API声明：isSocket(): boolean;<br>差异内容：isSocket(): boolean;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Dirent；<br>API声明：isSymbolicLink(): boolean;<br>差异内容：isSymbolicLink(): boolean;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface Stat<br>差异内容：declare interface Stat|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly dev: number;<br>差异内容：readonly dev: number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly ino: number;<br>差异内容：readonly ino: number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly mode: number;<br>差异内容：readonly mode: number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly nlink: number;<br>差异内容：readonly nlink: number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly uid: number;<br>差异内容：readonly uid: number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly gid: number;<br>差异内容：readonly gid: number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly rdev: number;<br>差异内容：readonly rdev: number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly size: number;<br>差异内容：readonly size: number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly blocks: number;<br>差异内容：readonly blocks: number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly atime: number;<br>差异内容：readonly atime: number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly mtime: number;<br>差异内容：readonly mtime: number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly ctime: number;<br>差异内容：readonly ctime: number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：isBlockDevice(): boolean;<br>差异内容：isBlockDevice(): boolean;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：isCharacterDevice(): boolean;<br>差异内容：isCharacterDevice(): boolean;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：isDirectory(): boolean;<br>差异内容：isDirectory(): boolean;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：isFIFO(): boolean;<br>差异内容：isFIFO(): boolean;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：isFile(): boolean;<br>差异内容：isFile(): boolean;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：isSocket(): boolean;<br>差异内容：isSocket(): boolean;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stat；<br>API声明：isSymbolicLink(): boolean;<br>差异内容：isSymbolicLink(): boolean;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface Stream<br>差异内容：declare interface Stream|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stream；<br>API声明：close(): Promise\<void>;<br>差异内容：close(): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stream；<br>API声明：close(callback: AsyncCallback\<void>): void;<br>差异内容：close(callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stream；<br>API声明：closeSync(): void;<br>差异内容：closeSync(): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stream；<br>API声明：flush(): Promise\<void>;<br>差异内容：flush(): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stream；<br>API声明：flush(callback: AsyncCallback\<void>): void;<br>差异内容：flush(callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stream；<br>API声明：flushSync(): void;<br>差异内容：flushSync(): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stream；<br>API声明：write(buffer: ArrayBuffer \| string, options?: {<br>        offset?: number;<br>        length?: number;<br>        position?: number;<br>        encoding?: string;<br>    }): Promise\<number>;<br>差异内容：write(buffer: ArrayBuffer \| string, options?: {<br>        offset?: number;<br>        length?: number;<br>        position?: number;<br>        encoding?: string;<br>    }): Promise\<number>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stream；<br>API声明：write(buffer: ArrayBuffer \| string, callback: AsyncCallback\<number>): void;<br>差异内容：write(buffer: ArrayBuffer \| string, callback: AsyncCallback\<number>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stream；<br>API声明：write(buffer: ArrayBuffer \| string, options: {<br>        offset?: number;<br>        length?: number;<br>        position?: number;<br>        encoding?: string;<br>    }, callback: AsyncCallback\<number>): void;<br>差异内容：write(buffer: ArrayBuffer \| string, options: {<br>        offset?: number;<br>        length?: number;<br>        position?: number;<br>        encoding?: string;<br>    }, callback: AsyncCallback\<number>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stream；<br>API声明：writeSync(buffer: ArrayBuffer \| string, options?: {<br>        offset?: number;<br>        length?: number;<br>        position?: number;<br>        encoding?: string;<br>    }): number;<br>差异内容：writeSync(buffer: ArrayBuffer \| string, options?: {<br>        offset?: number;<br>        length?: number;<br>        position?: number;<br>        encoding?: string;<br>    }): number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, options?: {<br>        position?: number;<br>        offset?: number;<br>        length?: number;<br>    }): Promise\<ReadOut>;<br>差异内容：read(buffer: ArrayBuffer, options?: {<br>        position?: number;<br>        offset?: number;<br>        length?: number;<br>    }): Promise\<ReadOut>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, callback: AsyncCallback\<ReadOut>): void;<br>差异内容：read(buffer: ArrayBuffer, callback: AsyncCallback\<ReadOut>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, options: {<br>        position?: number;<br>        offset?: number;<br>        length?: number;<br>    }, callback: AsyncCallback\<ReadOut>): void;<br>差异内容：read(buffer: ArrayBuffer, options: {<br>        position?: number;<br>        offset?: number;<br>        length?: number;<br>    }, callback: AsyncCallback\<ReadOut>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Stream；<br>API声明：readSync(buffer: ArrayBuffer, options?: {<br>        position?: number;<br>        offset?: number;<br>        length?: number;<br>    }): number;<br>差异内容：readSync(buffer: ArrayBuffer, options?: {<br>        position?: number;<br>        offset?: number;<br>        length?: number;<br>    }): number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface ReadOut<br>差异内容：declare interface ReadOut|api/@ohos.fileio.d.ts|
|新增API|NA|类名：ReadOut；<br>API声明：bytesRead: number;<br>差异内容：bytesRead: number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：ReadOut；<br>API声明：offset: number;<br>差异内容：offset: number;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：ReadOut；<br>API声明：buffer: ArrayBuffer;<br>差异内容：buffer: ArrayBuffer;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface Watcher<br>差异内容：declare interface Watcher|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Watcher；<br>API声明：stop(): Promise\<void>;<br>差异内容：stop(): Promise\<void>;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：Watcher；<br>API声明：stop(callback: AsyncCallback\<void>): void;<br>差异内容：stop(callback: AsyncCallback\<void>): void;|api/@ohos.fileio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace fileShare<br>差异内容：declare namespace fileShare|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：fileShare；<br>API声明：export enum OperationMode<br>差异内容：export enum OperationMode|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：OperationMode；<br>API声明：READ_MODE = 0b1<br>差异内容：READ_MODE = 0b1|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：OperationMode；<br>API声明：WRITE_MODE = 0b10<br>差异内容：WRITE_MODE = 0b10|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：fileShare；<br>API声明：export enum PolicyErrorCode<br>差异内容：export enum PolicyErrorCode|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：PolicyErrorCode；<br>API声明：PERSISTENCE_FORBIDDEN = 1<br>差异内容：PERSISTENCE_FORBIDDEN = 1|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：PolicyErrorCode；<br>API声明：INVALID_MODE = 2<br>差异内容：INVALID_MODE = 2|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：PolicyErrorCode；<br>API声明：INVALID_PATH = 3<br>差异内容：INVALID_PATH = 3|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：fileShare；<br>API声明：export type PolicyErrorResult = {<br>        /**<br>         * Indicates the failed uri of the policy information.<br>         *<br>         * @type { string }<br>         * @syscap SystemCapability.FileManagement.AppFileService.FolderAuthorization<br>         * @since 11<br>         */<br>        uri: string;<br>        /**<br>         * Indicates the error code of the failure in the policy information.<br>         *<br>         * @type { PolicyErrorCode }<br>         * @syscap SystemCapability.FileManagement.AppFileService.FolderAuthorization<br>         * @since 11<br>         */<br>        code: PolicyErrorCode;<br>        /**<br>         * Indicates the reason of the failure in the policy information.<br>         *<br>         * @type { string }<br>         * @syscap SystemCapability.FileManagement.AppFileService.FolderAuthorization<br>         * @since 11<br>         */<br>        message: string;<br>    };<br>差异内容：export type PolicyErrorResult = {<br>        /**<br>         * Indicates the failed uri of the policy information.<br>         *<br>         * @type { string }<br>         * @syscap SystemCapability.FileManagement.AppFileService.FolderAuthorization<br>         * @since 11<br>         */<br>        uri: string;<br>        /**<br>         * Indicates the error code of the failure in the policy information.<br>         *<br>         * @type { PolicyErrorCode }<br>         * @syscap SystemCapability.FileManagement.AppFileService.FolderAuthorization<br>         * @since 11<br>         */<br>        code: PolicyErrorCode;<br>        /**<br>         * Indicates the reason of the failure in the policy information.<br>         *<br>         * @type { string }<br>         * @syscap SystemCapability.FileManagement.AppFileService.FolderAuthorization<br>         * @since 11<br>         */<br>        message: string;<br>    };|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：fileShare；<br>API声明：export interface PolicyInfo<br>差异内容：export interface PolicyInfo|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：PolicyInfo；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：PolicyInfo；<br>API声明：operationMode: number;<br>差异内容：operationMode: number;|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：fileShare；<br>API声明：function persistPermission(policies: Array\<PolicyInfo>): Promise\<void>;<br>差异内容：function persistPermission(policies: Array\<PolicyInfo>): Promise\<void>;|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：fileShare；<br>API声明：function revokePermission(policies: Array\<PolicyInfo>): Promise\<void>;<br>差异内容：function revokePermission(policies: Array\<PolicyInfo>): Promise\<void>;|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：fileShare；<br>API声明：function activatePermission(policies: Array\<PolicyInfo>): Promise\<void>;<br>差异内容：function activatePermission(policies: Array\<PolicyInfo>): Promise\<void>;|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：fileShare；<br>API声明：function deactivatePermission(policies: Array\<PolicyInfo>): Promise\<void>;<br>差异内容：function deactivatePermission(policies: Array\<PolicyInfo>): Promise\<void>;|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace Statfs<br>差异内容：declare namespace Statfs|api/@ohos.statfs.d.ts|
|新增API|NA|类名：Statfs；<br>API声明：function getFreeBytes(path: string, callback: AsyncCallback\<number>): void;<br>差异内容：function getFreeBytes(path: string, callback: AsyncCallback\<number>): void;|api/@ohos.statfs.d.ts|
|新增API|NA|类名：Statfs；<br>API声明：function getFreeBytes(path: string): Promise\<number>;<br>差异内容：function getFreeBytes(path: string): Promise\<number>;|api/@ohos.statfs.d.ts|
|新增API|NA|类名：Statfs；<br>API声明：function getTotalBytes(path: string, callback: AsyncCallback\<number>): void;<br>差异内容：function getTotalBytes(path: string, callback: AsyncCallback\<number>): void;|api/@ohos.statfs.d.ts|
|新增API|NA|类名：Statfs；<br>API声明：function getTotalBytes(path: string): Promise\<number>;<br>差异内容：function getTotalBytes(path: string): Promise\<number>;|api/@ohos.statfs.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface FileResponse<br>差异内容：export interface FileResponse|api/@system.file.d.ts|
|新增API|NA|类名：FileResponse；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@system.file.d.ts|
|新增API|NA|类名：FileResponse；<br>API声明：length: number;<br>差异内容：length: number;|api/@system.file.d.ts|
|新增API|NA|类名：FileResponse；<br>API声明：lastModifiedTime: number;<br>差异内容：lastModifiedTime: number;|api/@system.file.d.ts|
|新增API|NA|类名：FileResponse；<br>API声明：type: 'dir' \| 'file';<br>差异内容：type: 'dir' \| 'file';|api/@system.file.d.ts|
|新增API|NA|类名：FileResponse；<br>API声明：subFiles?: Array\<FileResponse>;<br>差异内容：subFiles?: Array\<FileResponse>;|api/@system.file.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface FileMoveOption<br>差异内容：export interface FileMoveOption|api/@system.file.d.ts|
|新增API|NA|类名：FileMoveOption；<br>API声明：srcUri: string;<br>差异内容：srcUri: string;|api/@system.file.d.ts|
|新增API|NA|类名：FileMoveOption；<br>API声明：dstUri: string;<br>差异内容：dstUri: string;|api/@system.file.d.ts|
|新增API|NA|类名：FileMoveOption；<br>API声明：success?: (uri: string) => void;<br>差异内容：success?: (uri: string) => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileMoveOption；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileMoveOption；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.file.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface FileListResponse<br>差异内容：export interface FileListResponse|api/@system.file.d.ts|
|新增API|NA|类名：FileListResponse；<br>API声明：fileList: Array\<FileResponse>;<br>差异内容：fileList: Array\<FileResponse>;|api/@system.file.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface FileListOption<br>差异内容：export interface FileListOption|api/@system.file.d.ts|
|新增API|NA|类名：FileListOption；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@system.file.d.ts|
|新增API|NA|类名：FileListOption；<br>API声明：success?: (data: FileListResponse) => void;<br>差异内容：success?: (data: FileListResponse) => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileListOption；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileListOption；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.file.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface FileCopyOption<br>差异内容：export interface FileCopyOption|api/@system.file.d.ts|
|新增API|NA|类名：FileCopyOption；<br>API声明：srcUri: string;<br>差异内容：srcUri: string;|api/@system.file.d.ts|
|新增API|NA|类名：FileCopyOption；<br>API声明：dstUri: string;<br>差异内容：dstUri: string;|api/@system.file.d.ts|
|新增API|NA|类名：FileCopyOption；<br>API声明：success?: (uri: string) => void;<br>差异内容：success?: (uri: string) => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileCopyOption；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileCopyOption；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.file.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface FileGetOption<br>差异内容：export interface FileGetOption|api/@system.file.d.ts|
|新增API|NA|类名：FileGetOption；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@system.file.d.ts|
|新增API|NA|类名：FileGetOption；<br>API声明：recursive?: boolean;<br>差异内容：recursive?: boolean;|api/@system.file.d.ts|
|新增API|NA|类名：FileGetOption；<br>API声明：success?: (file: FileResponse) => void;<br>差异内容：success?: (file: FileResponse) => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileGetOption；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileGetOption；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.file.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface FileDeleteOption<br>差异内容：export interface FileDeleteOption|api/@system.file.d.ts|
|新增API|NA|类名：FileDeleteOption；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@system.file.d.ts|
|新增API|NA|类名：FileDeleteOption；<br>API声明：success?: () => void;<br>差异内容：success?: () => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileDeleteOption；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileDeleteOption；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.file.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface FileWriteTextOption<br>差异内容：export interface FileWriteTextOption|api/@system.file.d.ts|
|新增API|NA|类名：FileWriteTextOption；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@system.file.d.ts|
|新增API|NA|类名：FileWriteTextOption；<br>API声明：text: string;<br>差异内容：text: string;|api/@system.file.d.ts|
|新增API|NA|类名：FileWriteTextOption；<br>API声明：encoding?: string;<br>差异内容：encoding?: string;|api/@system.file.d.ts|
|新增API|NA|类名：FileWriteTextOption；<br>API声明：append?: boolean;<br>差异内容：append?: boolean;|api/@system.file.d.ts|
|新增API|NA|类名：FileWriteTextOption；<br>API声明：success?: () => void;<br>差异内容：success?: () => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileWriteTextOption；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileWriteTextOption；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.file.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface FileReadTextResponse<br>差异内容：export interface FileReadTextResponse|api/@system.file.d.ts|
|新增API|NA|类名：FileReadTextResponse；<br>API声明：text: string;<br>差异内容：text: string;|api/@system.file.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface FileReadTextOption<br>差异内容：export interface FileReadTextOption|api/@system.file.d.ts|
|新增API|NA|类名：FileReadTextOption；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@system.file.d.ts|
|新增API|NA|类名：FileReadTextOption；<br>API声明：encoding?: string;<br>差异内容：encoding?: string;|api/@system.file.d.ts|
|新增API|NA|类名：FileReadTextOption；<br>API声明：position?: number;<br>差异内容：position?: number;|api/@system.file.d.ts|
|新增API|NA|类名：FileReadTextOption；<br>API声明：length?: number;<br>差异内容：length?: number;|api/@system.file.d.ts|
|新增API|NA|类名：FileReadTextOption；<br>API声明：success?: (data: FileReadTextResponse) => void;<br>差异内容：success?: (data: FileReadTextResponse) => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileReadTextOption；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileReadTextOption；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.file.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface FileWriteArrayBufferOption<br>差异内容：export interface FileWriteArrayBufferOption|api/@system.file.d.ts|
|新增API|NA|类名：FileWriteArrayBufferOption；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@system.file.d.ts|
|新增API|NA|类名：FileWriteArrayBufferOption；<br>API声明：buffer: Uint8Array;<br>差异内容：buffer: Uint8Array;|api/@system.file.d.ts|
|新增API|NA|类名：FileWriteArrayBufferOption；<br>API声明：position?: number;<br>差异内容：position?: number;|api/@system.file.d.ts|
|新增API|NA|类名：FileWriteArrayBufferOption；<br>API声明：append?: boolean;<br>差异内容：append?: boolean;|api/@system.file.d.ts|
|新增API|NA|类名：FileWriteArrayBufferOption；<br>API声明：success?: () => void;<br>差异内容：success?: () => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileWriteArrayBufferOption；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileWriteArrayBufferOption；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.file.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface FileReadArrayBufferResponse<br>差异内容：export interface FileReadArrayBufferResponse|api/@system.file.d.ts|
|新增API|NA|类名：FileReadArrayBufferResponse；<br>API声明：buffer: Uint8Array;<br>差异内容：buffer: Uint8Array;|api/@system.file.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface FileReadArrayBufferOption<br>差异内容：export interface FileReadArrayBufferOption|api/@system.file.d.ts|
|新增API|NA|类名：FileReadArrayBufferOption；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@system.file.d.ts|
|新增API|NA|类名：FileReadArrayBufferOption；<br>API声明：position?: number;<br>差异内容：position?: number;|api/@system.file.d.ts|
|新增API|NA|类名：FileReadArrayBufferOption；<br>API声明：length?: number;<br>差异内容：length?: number;|api/@system.file.d.ts|
|新增API|NA|类名：FileReadArrayBufferOption；<br>API声明：success?: (data: FileReadArrayBufferResponse) => void;<br>差异内容：success?: (data: FileReadArrayBufferResponse) => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileReadArrayBufferOption；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileReadArrayBufferOption；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.file.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface FileAccessOption<br>差异内容：export interface FileAccessOption|api/@system.file.d.ts|
|新增API|NA|类名：FileAccessOption；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@system.file.d.ts|
|新增API|NA|类名：FileAccessOption；<br>API声明：success?: () => void;<br>差异内容：success?: () => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileAccessOption；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileAccessOption；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.file.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface FileMkdirOption<br>差异内容：export interface FileMkdirOption|api/@system.file.d.ts|
|新增API|NA|类名：FileMkdirOption；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@system.file.d.ts|
|新增API|NA|类名：FileMkdirOption；<br>API声明：recursive?: boolean;<br>差异内容：recursive?: boolean;|api/@system.file.d.ts|
|新增API|NA|类名：FileMkdirOption；<br>API声明：success?: () => void;<br>差异内容：success?: () => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileMkdirOption；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileMkdirOption；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.file.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface FileRmdirOption<br>差异内容：export interface FileRmdirOption|api/@system.file.d.ts|
|新增API|NA|类名：FileRmdirOption；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@system.file.d.ts|
|新增API|NA|类名：FileRmdirOption；<br>API声明：recursive?: boolean;<br>差异内容：recursive?: boolean;|api/@system.file.d.ts|
|新增API|NA|类名：FileRmdirOption；<br>API声明：success?: () => void;<br>差异内容：success?: () => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileRmdirOption；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.file.d.ts|
|新增API|NA|类名：FileRmdirOption；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.file.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class File<br>差异内容：export default class File|api/@system.file.d.ts|
|新增API|NA|类名：File；<br>API声明：static move(options: FileMoveOption): void;<br>差异内容：static move(options: FileMoveOption): void;|api/@system.file.d.ts|
|新增API|NA|类名：File；<br>API声明：static copy(options: FileCopyOption): void;<br>差异内容：static copy(options: FileCopyOption): void;|api/@system.file.d.ts|
|新增API|NA|类名：File；<br>API声明：static list(options: FileListOption): void;<br>差异内容：static list(options: FileListOption): void;|api/@system.file.d.ts|
|新增API|NA|类名：File；<br>API声明：static get(options: FileGetOption): void;<br>差异内容：static get(options: FileGetOption): void;|api/@system.file.d.ts|
|新增API|NA|类名：File；<br>API声明：static delete(options: FileDeleteOption): void;<br>差异内容：static delete(options: FileDeleteOption): void;|api/@system.file.d.ts|
|新增API|NA|类名：File；<br>API声明：static writeText(options: FileWriteTextOption): void;<br>差异内容：static writeText(options: FileWriteTextOption): void;|api/@system.file.d.ts|
|新增API|NA|类名：File；<br>API声明：static readText(options: FileReadTextOption): void;<br>差异内容：static readText(options: FileReadTextOption): void;|api/@system.file.d.ts|
|新增API|NA|类名：File；<br>API声明：static writeArrayBuffer(options: FileWriteArrayBufferOption): void;<br>差异内容：static writeArrayBuffer(options: FileWriteArrayBufferOption): void;|api/@system.file.d.ts|
|新增API|NA|类名：File；<br>API声明：static readArrayBuffer(options: FileReadArrayBufferOption): void;<br>差异内容：static readArrayBuffer(options: FileReadArrayBufferOption): void;|api/@system.file.d.ts|
|新增API|NA|类名：File；<br>API声明：static access(options: FileAccessOption): void;<br>差异内容：static access(options: FileAccessOption): void;|api/@system.file.d.ts|
|新增API|NA|类名：File；<br>API声明：static mkdir(options: FileMkdirOption): void;<br>差异内容：static mkdir(options: FileMkdirOption): void;|api/@system.file.d.ts|
|新增API|NA|类名：File；<br>API声明：static rmdir(options: FileRmdirOption): void;<br>差异内容：static rmdir(options: FileRmdirOption): void;|api/@system.file.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.application.BackupExtensionAbility.d.ts<br>差异内容：CoreFileKit|api/@ohos.application.BackupExtensionAbility.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.document.d.ts<br>差异内容：CoreFileKit|api/@ohos.document.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.file.cloudSync.d.ts<br>差异内容：CoreFileKit|api/@ohos.file.cloudSync.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.file.cloudSyncManager.d.ts<br>差异内容：CoreFileKit|api/@ohos.file.cloudSyncManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.file.environment.d.ts<br>差异内容：CoreFileKit|api/@ohos.file.environment.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.file.fileAccess.d.ts<br>差异内容：CoreFileKit|api/@ohos.file.fileAccess.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.file.fileuri.d.ts<br>差异内容：CoreFileKit|api/@ohos.file.fileuri.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.file.fs.d.ts<br>差异内容：CoreFileKit|api/@ohos.file.fs.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.file.hash.d.ts<br>差异内容：CoreFileKit|api/@ohos.file.hash.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.file.picker.d.ts<br>差异内容：CoreFileKit|api/@ohos.file.picker.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.file.securityLabel.d.ts<br>差异内容：CoreFileKit|api/@ohos.file.securityLabel.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.file.statvfs.d.ts<br>差异内容：CoreFileKit|api/@ohos.file.statvfs.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.file.storageStatistics.d.ts<br>差异内容：CoreFileKit|api/@ohos.file.storageStatistics.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.fileio.d.ts<br>差异内容：CoreFileKit|api/@ohos.fileio.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.fileshare.d.ts<br>差异内容：CoreFileKit|api/@ohos.fileshare.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.statfs.d.ts<br>差异内容：CoreFileKit|api/@ohos.statfs.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@system.file.d.ts<br>差异内容：CoreFileKit|api/@system.file.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.CoreFileKit.d.ts<br>差异内容：CoreFileKit|kits/@kit.CoreFileKit.d.ts|
