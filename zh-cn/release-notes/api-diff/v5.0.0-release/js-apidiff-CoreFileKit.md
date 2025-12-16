| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API跨平台权限变更|类名：global；<br>API声明：declare function lseek(fd: number, offset: number, whence?: WhenceType): number;<br>差异内容：NA|类名：global；<br>API声明：declare function lseek(fd: number, offset: number, whence?: WhenceType): number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function utimes(path: string, mtime: number): void;<br>差异内容：NA|类名：global；<br>API声明：declare function utimes(path: string, mtime: number): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare namespace picker<br>差异内容：NA|类名：global；<br>API声明：declare namespace picker<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：picker；<br>API声明：export enum DocumentSelectMode<br>差异内容：NA|类名：picker；<br>API声明：export enum DocumentSelectMode<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：DocumentSelectMode；<br>API声明：FILE = 0<br>差异内容：NA|类名：DocumentSelectMode；<br>API声明：FILE = 0<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：DocumentSelectMode；<br>API声明：FOLDER = 1<br>差异内容：NA|类名：DocumentSelectMode；<br>API声明：FOLDER = 1<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：picker；<br>API声明：class DocumentSelectOptions<br>差异内容：NA|类名：picker；<br>API声明：class DocumentSelectOptions<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：DocumentSelectOptions；<br>API声明：defaultFilePathUri?: string;<br>差异内容：NA|类名：DocumentSelectOptions；<br>API声明：defaultFilePathUri?: string;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：DocumentSelectOptions；<br>API声明：fileSuffixFilters?: Array\<string>;<br>差异内容：NA|类名：DocumentSelectOptions；<br>API声明：fileSuffixFilters?: Array\<string>;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：DocumentSelectOptions；<br>API声明：maxSelectNumber?: number;<br>差异内容：NA|类名：DocumentSelectOptions；<br>API声明：maxSelectNumber?: number;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：DocumentSelectOptions；<br>API声明：selectMode?: DocumentSelectMode;<br>差异内容：NA|类名：DocumentSelectOptions；<br>API声明：selectMode?: DocumentSelectMode;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：picker；<br>API声明：class DocumentSaveOptions<br>差异内容：NA|类名：picker；<br>API声明：class DocumentSaveOptions<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：DocumentSaveOptions；<br>API声明：newFileNames?: Array\<string>;<br>差异内容：NA|类名：DocumentSaveOptions；<br>API声明：newFileNames?: Array\<string>;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：DocumentSaveOptions；<br>API声明：defaultFilePathUri?: string;<br>差异内容：NA|类名：DocumentSaveOptions；<br>API声明：defaultFilePathUri?: string;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：picker；<br>API声明：class DocumentViewPicker<br>差异内容：NA|类名：picker；<br>API声明：class DocumentViewPicker<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：DocumentViewPicker；<br>API声明：select(option?: DocumentSelectOptions): Promise\<Array\<string>>;<br>差异内容：NA|类名：DocumentViewPicker；<br>API声明：select(option?: DocumentSelectOptions): Promise\<Array\<string>>;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：DocumentViewPicker；<br>API声明：select(option: DocumentSelectOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：NA|类名：DocumentViewPicker；<br>API声明：select(option: DocumentSelectOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：DocumentViewPicker；<br>API声明：select(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：NA|类名：DocumentViewPicker；<br>API声明：select(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：DocumentViewPicker；<br>API声明：save(option?: DocumentSaveOptions): Promise\<Array\<string>>;<br>差异内容：NA|类名：DocumentViewPicker；<br>API声明：save(option?: DocumentSaveOptions): Promise\<Array\<string>>;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：DocumentViewPicker；<br>API声明：save(option: DocumentSaveOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：NA|类名：DocumentViewPicker；<br>API声明：save(option: DocumentSaveOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：DocumentViewPicker；<br>API声明：save(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：NA|类名：DocumentViewPicker；<br>API声明：save(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：picker；<br>API声明：class AudioSelectOptions<br>差异内容：NA|类名：picker；<br>API声明：class AudioSelectOptions<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：picker；<br>API声明：class AudioSaveOptions<br>差异内容：NA|类名：picker；<br>API声明：class AudioSaveOptions<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：AudioSaveOptions；<br>API声明：newFileNames?: Array\<string>;<br>差异内容：NA|类名：AudioSaveOptions；<br>API声明：newFileNames?: Array\<string>;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：picker；<br>API声明：class AudioViewPicker<br>差异内容：NA|类名：picker；<br>API声明：class AudioViewPicker<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：AudioViewPicker；<br>API声明：select(option?: AudioSelectOptions): Promise\<Array\<string>>;<br>差异内容：NA|类名：AudioViewPicker；<br>API声明：select(option?: AudioSelectOptions): Promise\<Array\<string>>;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：AudioViewPicker；<br>API声明：select(option: AudioSelectOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：NA|类名：AudioViewPicker；<br>API声明：select(option: AudioSelectOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：AudioViewPicker；<br>API声明：select(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：NA|类名：AudioViewPicker；<br>API声明：select(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：AudioViewPicker；<br>API声明：save(option?: AudioSaveOptions): Promise\<Array\<string>>;<br>差异内容：NA|类名：AudioViewPicker；<br>API声明：save(option?: AudioSaveOptions): Promise\<Array\<string>>;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：AudioViewPicker；<br>API声明：save(option: AudioSaveOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：NA|类名：AudioViewPicker；<br>API声明：save(option: AudioSaveOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API跨平台权限变更|类名：AudioViewPicker；<br>API声明：save(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：NA|类名：AudioViewPicker；<br>API声明：save(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：crossplatform|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：picker；<br>API声明：export enum PhotoViewMIMETypes<br>差异内容：NA|类名：picker；<br>API声明：export enum PhotoViewMIMETypes<br>差异内容：12|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：picker；<br>API声明：class PhotoSelectOptions<br>差异内容：NA|类名：picker；<br>API声明：class PhotoSelectOptions<br>差异内容：12|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：picker；<br>API声明：class PhotoSelectResult<br>差异内容：NA|类名：picker；<br>API声明：class PhotoSelectResult<br>差异内容：12|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：picker；<br>API声明：class PhotoSaveOptions<br>差异内容：NA|类名：picker；<br>API声明：class PhotoSaveOptions<br>差异内容：12|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：picker；<br>API声明：class PhotoViewPicker<br>差异内容：NA|类名：picker；<br>API声明：class PhotoViewPicker<br>差异内容：12|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoViewPicker；<br>API声明：select(option?: PhotoSelectOptions): Promise\<PhotoSelectResult>;<br>差异内容：NA|类名：PhotoViewPicker；<br>API声明：select(option?: PhotoSelectOptions): Promise\<PhotoSelectResult>;<br>差异内容：12|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoViewPicker；<br>API声明：select(option: PhotoSelectOptions, callback: AsyncCallback\<PhotoSelectResult>): void;<br>差异内容：NA|类名：PhotoViewPicker；<br>API声明：select(option: PhotoSelectOptions, callback: AsyncCallback\<PhotoSelectResult>): void;<br>差异内容：12|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoViewPicker；<br>API声明：select(callback: AsyncCallback\<PhotoSelectResult>): void;<br>差异内容：NA|类名：PhotoViewPicker；<br>API声明：select(callback: AsyncCallback\<PhotoSelectResult>): void;<br>差异内容：12|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoViewPicker；<br>API声明：save(option?: PhotoSaveOptions): Promise\<Array\<string>>;<br>差异内容：NA|类名：PhotoViewPicker；<br>API声明：save(option?: PhotoSaveOptions): Promise\<Array\<string>>;<br>差异内容：12|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoViewPicker；<br>API声明：save(option: PhotoSaveOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：NA|类名：PhotoViewPicker；<br>API声明：save(option: PhotoSaveOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：12|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoViewPicker；<br>API声明：save(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：NA|类名：PhotoViewPicker；<br>API声明：save(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：12|api/@ohos.file.picker.d.ts|
|新增错误码|类名：global；<br>API声明：declare function copy(srcUri: string, destUri: string, options?: CopyOptions): Promise\<void>;<br>差异内容：NA|类名：global；<br>API声明：declare function copy(srcUri: string, destUri: string, options?: CopyOptions): Promise\<void>;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：global；<br>API声明：declare function copyDir(src: string, dest: string, mode?: number): Promise\<void>;<br>差异内容：NA|类名：global；<br>API声明：declare function copyDir(src: string, dest: string, mode?: number): Promise\<void>;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：global；<br>API声明：declare function copyDirSync(src: string, dest: string, mode?: number): void;<br>差异内容：NA|类名：global；<br>API声明：declare function copyDirSync(src: string, dest: string, mode?: number): void;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：global；<br>API声明：declare function copyFile(src: string \| number, dest: string \| number, mode?: number): Promise\<void>;<br>差异内容：NA|类名：global；<br>API声明：declare function copyFile(src: string \| number, dest: string \| number, mode?: number): Promise\<void>;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：global；<br>API声明：declare function copyFileSync(src: string \| number, dest: string \| number, mode?: number): void;<br>差异内容：NA|类名：global；<br>API声明：declare function copyFileSync(src: string \| number, dest: string \| number, mode?: number): void;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：global；<br>API声明：declare function createStream(path: string, mode: string): Promise\<Stream>;<br>差异内容：NA|类名：global；<br>API声明：declare function createStream(path: string, mode: string): Promise\<Stream>;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：global；<br>API声明：declare function createStreamSync(path: string, mode: string): Stream;<br>差异内容：NA|类名：global；<br>API声明：declare function createStreamSync(path: string, mode: string): Stream;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：global；<br>API声明：declare function createRandomAccessFile(file: string \| File, mode?: number): Promise\<RandomAccessFile>;<br>差异内容：NA|类名：global；<br>API声明：declare function createRandomAccessFile(file: string \| File, mode?: number, options?: RandomAccessFileOptions): Promise\<RandomAccessFile>;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：global；<br>API声明：declare function createRandomAccessFileSync(file: string \| File, mode?: number): RandomAccessFile;<br>差异内容：NA|类名：global；<br>API声明：declare function createRandomAccessFileSync(file: string \| File, mode?: number, options?: RandomAccessFileOptions): RandomAccessFile;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：global；<br>API声明：declare function open(path: string, mode?: number): Promise\<File>;<br>差异内容：NA|类名：global；<br>API声明：declare function open(path: string, mode?: number): Promise\<File>;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：global；<br>API声明：declare function openSync(path: string, mode?: number): File;<br>差异内容：NA|类名：global；<br>API声明：declare function openSync(path: string, mode?: number): File;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：global；<br>API声明：declare function read(fd: number, buffer: ArrayBuffer, options?: ReadOptions): Promise\<number>;<br>差异内容：NA|类名：global；<br>API声明：declare function read(fd: number, buffer: ArrayBuffer, options?: ReadOptions): Promise\<number>;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：global；<br>API声明：declare function readSync(fd: number, buffer: ArrayBuffer, options?: ReadOptions): number;<br>差异内容：NA|类名：global；<br>API声明：declare function readSync(fd: number, buffer: ArrayBuffer, options?: ReadOptions): number;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：global；<br>API声明：declare function readLines(filePath: string, options?: Options): Promise\<ReaderIterator>;<br>差异内容：NA|类名：global；<br>API声明：declare function readLines(filePath: string, options?: Options): Promise\<ReaderIterator>;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：global；<br>API声明：declare function readLinesSync(filePath: string, options?: Options): ReaderIterator;<br>差异内容：NA|类名：global；<br>API声明：declare function readLinesSync(filePath: string, options?: Options): ReaderIterator;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：global；<br>API声明：declare function readText(filePath: string, options?: ReadTextOptions): Promise\<string>;<br>差异内容：NA|类名：global；<br>API声明：declare function readText(filePath: string, options?: ReadTextOptions): Promise\<string>;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：global；<br>API声明：declare function readTextSync(filePath: string, options?: ReadTextOptions): string;<br>差异内容：NA|类名：global；<br>API声明：declare function readTextSync(filePath: string, options?: ReadTextOptions): string;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：RandomAccessFile；<br>API声明：read(buffer: ArrayBuffer, options?: ReadOptions): Promise\<number>;<br>差异内容：NA|类名：RandomAccessFile；<br>API声明：read(buffer: ArrayBuffer, options?: ReadOptions): Promise\<number>;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：RandomAccessFile；<br>API声明：readSync(buffer: ArrayBuffer, options?: ReadOptions): number;<br>差异内容：NA|类名：RandomAccessFile；<br>API声明：readSync(buffer: ArrayBuffer, options?: ReadOptions): number;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, options?: ReadOptions): Promise\<number>;<br>差异内容：NA|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, options?: ReadOptions): Promise\<number>;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|新增错误码|类名：Stream；<br>API声明：readSync(buffer: ArrayBuffer, options?: ReadOptions): number;<br>差异内容：NA|类名：Stream；<br>API声明：readSync(buffer: ArrayBuffer, options?: ReadOptions): number;<br>差异内容：13900044|api/@ohos.file.fs.d.ts|
|删除错误码|类名：Environment；<br>API声明：function getUserDownloadDir(): string;<br>差异内容：201|类名：Environment；<br>API声明：function getUserDownloadDir(): string;<br>差异内容：NA|api/@ohos.file.environment.d.ts|
|删除错误码|类名：Environment；<br>API声明：function getUserDesktopDir(): string;<br>差异内容：201|类名：Environment；<br>API声明：function getUserDesktopDir(): string;<br>差异内容：NA|api/@ohos.file.environment.d.ts|
|删除错误码|类名：Environment；<br>API声明：function getUserDocumentDir(): string;<br>差异内容：201|类名：Environment；<br>API声明：function getUserDocumentDir(): string;<br>差异内容：NA|api/@ohos.file.environment.d.ts|
|权限变更|类名：Environment；<br>API声明：function getUserDownloadDir(): string;<br>差异内容：ohos.permission.READ_WRITE_DOWNLOAD_DIRECTORY|类名：Environment；<br>API声明：function getUserDownloadDir(): string;<br>差异内容：NA|api/@ohos.file.environment.d.ts|
|权限变更|类名：Environment；<br>API声明：function getUserDesktopDir(): string;<br>差异内容：ohos.permission.READ_WRITE_DESKTOP_DIRECTORY|类名：Environment；<br>API声明：function getUserDesktopDir(): string;<br>差异内容：NA|api/@ohos.file.environment.d.ts|
|权限变更|类名：Environment；<br>API声明：function getUserDocumentDir(): string;<br>差异内容：ohos.permission.READ_WRITE_DOCUMENTS_DIRECTORY|类名：Environment；<br>API声明：function getUserDocumentDir(): string;<br>差异内容：NA|api/@ohos.file.environment.d.ts|
|函数变更|类名：global；<br>API声明：declare function access(path: string): Promise\<boolean>;<br>差异内容：NA|类名：global；<br>API声明：declare function access(path: string, mode?: AccessModeType): Promise\<boolean>;<br>差异内容：mode?: AccessModeType|api/@ohos.file.fs.d.ts|
|函数变更|类名：global；<br>API声明：declare function accessSync(path: string): boolean;<br>差异内容：NA|类名：global；<br>API声明：declare function accessSync(path: string, mode?: AccessModeType): boolean;<br>差异内容：mode?: AccessModeType|api/@ohos.file.fs.d.ts|
|函数变更|类名：global；<br>API声明：declare function createRandomAccessFile(file: string \| File, mode?: number): Promise\<RandomAccessFile>;<br>差异内容：NA|类名：global；<br>API声明：declare function createRandomAccessFile(file: string \| File, mode?: number, options?: RandomAccessFileOptions): Promise\<RandomAccessFile>;<br>差异内容：options?: RandomAccessFileOptions|api/@ohos.file.fs.d.ts|
|函数变更|类名：global；<br>API声明：declare function createRandomAccessFileSync(file: string \| File, mode?: number): RandomAccessFile;<br>差异内容：NA|类名：global；<br>API声明：declare function createRandomAccessFileSync(file: string \| File, mode?: number, options?: RandomAccessFileOptions): RandomAccessFile;<br>差异内容：options?: RandomAccessFileOptions|api/@ohos.file.fs.d.ts|
|函数变更|类名：CloudFileCache；<br>API声明：stop(uri: string): Promise\<void>;<br>差异内容：NA|类名：CloudFileCache；<br>API声明：stop(uri: string, needClean?: boolean): Promise\<void>;<br>差异内容：needClean?: boolean|api/@ohos.file.cloudSync.d.ts|
|属性变更|类名：BackupExtensionAbility；<br>API声明：context: ExtensionContext;<br>差异内容：ExtensionContext|类名：BackupExtensionAbility；<br>API声明：context: BackupExtensionContext;<br>差异内容：BackupExtensionContext|api/@ohos.application.BackupExtensionAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class BackupExtensionContext<br>差异内容：export default class BackupExtensionContext|api/@ohos.file.BackupExtensionContext.d.ts|
|新增API|NA|类名：BackupExtensionContext；<br>API声明：readonly backupDir: string;<br>差异内容：readonly backupDir: string;|api/@ohos.file.BackupExtensionContext.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function createReadStream(path: string, options?: ReadStreamOptions): ReadStream;<br>差异内容：declare function createReadStream(path: string, options?: ReadStreamOptions): ReadStream;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function createWriteStream(path: string, options?: WriteStreamOptions): WriteStream;<br>差异内容：declare function createWriteStream(path: string, options?: WriteStreamOptions): WriteStream;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function connectDfs(networkId: string, listeners: DfsListeners): Promise\<void>;<br>差异内容：declare function connectDfs(networkId: string, listeners: DfsListeners): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function disconnectDfs(networkId: string): Promise\<void>;<br>差异内容：declare function disconnectDfs(networkId: string): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function setxattr(path: string, key: string, value: string): Promise\<void>;<br>差异内容：declare function setxattr(path: string, key: string, value: string): Promise\<void>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function setxattrSync(path: string, key: string, value: string): void;<br>差异内容：declare function setxattrSync(path: string, key: string, value: string): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function getxattr(path: string, key: string): Promise\<string>;<br>差异内容：declare function getxattr(path: string, key: string): Promise\<string>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare function getxattrSync(path: string, key: string): string;<br>差异内容：declare function getxattrSync(path: string, key: string): string;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：export class TaskSignal<br>差异内容：export class TaskSignal|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：TaskSignal；<br>API声明：cancel(): void;<br>差异内容：cancel(): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：TaskSignal；<br>API声明：onCancel(): Promise\<string>;<br>差异内容：onCancel(): Promise\<string>;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：CopyOptions；<br>API声明：copySignal?: TaskSignal;<br>差异内容：copySignal?: TaskSignal;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：RandomAccessFile；<br>API声明：getReadStream(): ReadStream;<br>差异内容：getReadStream(): ReadStream;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：RandomAccessFile；<br>API声明：getWriteStream(): WriteStream;<br>差异内容：getWriteStream(): WriteStream;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class ReadStream<br>差异内容：declare class ReadStream|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：ReadStream；<br>API声明：readonly bytesRead: number;<br>差异内容：readonly bytesRead: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：ReadStream；<br>API声明：readonly path: string;<br>差异内容：readonly path: string;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：ReadStream；<br>API声明：seek(offset: number, whence?: WhenceType): number;<br>差异内容：seek(offset: number, whence?: WhenceType): number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：ReadStream；<br>API声明：close(): void;<br>差异内容：close(): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class WriteStream<br>差异内容：declare class WriteStream|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：WriteStream；<br>API声明：readonly bytesWritten: number;<br>差异内容：readonly bytesWritten: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：WriteStream；<br>API声明：readonly path: string;<br>差异内容：readonly path: string;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：WriteStream；<br>API声明：seek(offset: number, whence?: WhenceType): number;<br>差异内容：seek(offset: number, whence?: WhenceType): number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：WriteStream；<br>API声明：close(): void;<br>差异内容：close(): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface RandomAccessFileOptions<br>差异内容：export interface RandomAccessFileOptions|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：RandomAccessFileOptions；<br>API声明：start?: number;<br>差异内容：start?: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：RandomAccessFileOptions；<br>API声明：end?: number;<br>差异内容：end?: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface ReadStreamOptions<br>差异内容：export interface ReadStreamOptions|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：ReadStreamOptions；<br>API声明：start?: number;<br>差异内容：start?: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：ReadStreamOptions；<br>API声明：end?: number;<br>差异内容：end?: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface WriteStreamOptions<br>差异内容：export interface WriteStreamOptions|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：WriteStreamOptions；<br>API声明：mode?: number;<br>差异内容：mode?: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：WriteStreamOptions；<br>API声明：start?: number;<br>差异内容：start?: number;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：interface DfsListeners<br>差异内容：interface DfsListeners|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：DfsListeners；<br>API声明：onStatus(networkId: string, status: number): void;<br>差异内容：onStatus(networkId: string, status: number): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum AccessModeType<br>差异内容：declare enum AccessModeType|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：AccessModeType；<br>API声明：EXIST = 0<br>差异内容：EXIST = 0|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：AccessModeType；<br>API声明：WRITE = 2<br>差异内容：WRITE = 2|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：AccessModeType；<br>API声明：READ = 4<br>差异内容：READ = 4|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：AccessModeType；<br>API声明：READ_WRITE = 6<br>差异内容：READ_WRITE = 6|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum AccessFlagType<br>差异内容：declare enum AccessFlagType|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：AccessFlagType；<br>API声明：LOCAL = 0<br>差异内容：LOCAL = 0|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：BackupExtensionAbility；<br>API声明：onBackupEx(backupInfo: string): string \| Promise\<string>;<br>差异内容：onBackupEx(backupInfo: string): string \| Promise\<string>;|api/@ohos.application.BackupExtensionAbility.d.ts|
|新增API|NA|类名：BackupExtensionAbility；<br>API声明：onRestoreEx(bundleVersion: BundleVersion, restoreInfo: string): string \| Promise\<string>;<br>差异内容：onRestoreEx(bundleVersion: BundleVersion, restoreInfo: string): string \| Promise\<string>;|api/@ohos.application.BackupExtensionAbility.d.ts|
|新增API|NA|类名：BackupExtensionAbility；<br>API声明：onProcess(): string;<br>差异内容：onProcess(): string;|api/@ohos.application.BackupExtensionAbility.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：enum SyncState<br>差异内容：enum SyncState|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：SyncState；<br>API声明：UPLOADING<br>差异内容：UPLOADING|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：SyncState；<br>API声明：UPLOAD_FAILED<br>差异内容：UPLOAD_FAILED|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：SyncState；<br>API声明：DOWNLOADING<br>差异内容：DOWNLOADING|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：SyncState；<br>API声明：DOWNLOAD_FAILED<br>差异内容：DOWNLOAD_FAILED|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：SyncState；<br>API声明：COMPLETED<br>差异内容：COMPLETED|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：SyncState；<br>API声明：STOPPED<br>差异内容：STOPPED|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：enum ErrorType<br>差异内容：enum ErrorType|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：ErrorType；<br>API声明：NO_ERROR<br>差异内容：NO_ERROR|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：ErrorType；<br>API声明：NETWORK_UNAVAILABLE<br>差异内容：NETWORK_UNAVAILABLE|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：ErrorType；<br>API声明：WIFI_UNAVAILABLE<br>差异内容：WIFI_UNAVAILABLE|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：ErrorType；<br>API声明：BATTERY_LEVEL_LOW<br>差异内容：BATTERY_LEVEL_LOW|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：ErrorType；<br>API声明：BATTERY_LEVEL_WARNING<br>差异内容：BATTERY_LEVEL_WARNING|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：ErrorType；<br>API声明：CLOUD_STORAGE_FULL<br>差异内容：CLOUD_STORAGE_FULL|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：ErrorType；<br>API声明：LOCAL_STORAGE_FULL<br>差异内容：LOCAL_STORAGE_FULL|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：ErrorType；<br>API声明：DEVICE_TEMPERATURE_TOO_HIGH<br>差异内容：DEVICE_TEMPERATURE_TOO_HIGH|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：interface SyncProgress<br>差异内容：interface SyncProgress|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：SyncProgress；<br>API声明：state: SyncState;<br>差异内容：state: SyncState;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：SyncProgress；<br>API声明：error: ErrorType;<br>差异内容：error: ErrorType;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：class FileSync<br>差异内容：class FileSync|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileSync；<br>API声明：on(event: 'progress', callback: Callback\<SyncProgress>): void;<br>差异内容：on(event: 'progress', callback: Callback\<SyncProgress>): void;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileSync；<br>API声明：off(event: 'progress', callback?: Callback\<SyncProgress>): void;<br>差异内容：off(event: 'progress', callback?: Callback\<SyncProgress>): void;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileSync；<br>API声明：start(): Promise\<void>;<br>差异内容：start(): Promise\<void>;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileSync；<br>API声明：start(callback: AsyncCallback\<void>): void;<br>差异内容：start(callback: AsyncCallback\<void>): void;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileSync；<br>API声明：stop(): Promise\<void>;<br>差异内容：stop(): Promise\<void>;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileSync；<br>API声明：stop(callback: AsyncCallback\<void>): void;<br>差异内容：stop(callback: AsyncCallback\<void>): void;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileSync；<br>API声明：getLastSyncTime(): Promise\<number>;<br>差异内容：getLastSyncTime(): Promise\<number>;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileSync；<br>API声明：getLastSyncTime(callback: AsyncCallback\<number>): void;<br>差异内容：getLastSyncTime(callback: AsyncCallback\<number>): void;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：function registerChange(uri: string, recursion: boolean, callback: Callback\<ChangeData>): void;<br>差异内容：function registerChange(uri: string, recursion: boolean, callback: Callback\<ChangeData>): void;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：function unregisterChange(uri: string): void;<br>差异内容：function unregisterChange(uri: string): void;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：enum NotifyType<br>差异内容：enum NotifyType|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：NotifyType；<br>API声明：NOTIFY_ADDED<br>差异内容：NOTIFY_ADDED|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：NotifyType；<br>API声明：NOTIFY_MODIFIED<br>差异内容：NOTIFY_MODIFIED|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：NotifyType；<br>API声明：NOTIFY_DELETED<br>差异内容：NOTIFY_DELETED|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：NotifyType；<br>API声明：NOTIFY_RENAMED<br>差异内容：NOTIFY_RENAMED|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：interface ChangeData<br>差异内容：interface ChangeData|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：ChangeData；<br>API声明：type: NotifyType;<br>差异内容：type: NotifyType;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：ChangeData；<br>API声明：isDirectory: Array\<boolean>;<br>差异内容：isDirectory: Array\<boolean>;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：ChangeData；<br>API声明：uris: Array\<string>;<br>差异内容：uris: Array\<string>;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：picker；<br>API声明：export enum DocumentPickerMode<br>差异内容：export enum DocumentPickerMode|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentPickerMode；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentPickerMode；<br>API声明：DOWNLOAD = 1<br>差异内容：DOWNLOAD = 1|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentSelectOptions；<br>API声明：authMode?: boolean;<br>差异内容：authMode?: boolean;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentSaveOptions；<br>API声明：pickerMode?: DocumentPickerMode;<br>差异内容：pickerMode?: DocumentPickerMode;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：AudioSelectOptions；<br>API声明：maxSelectNumber?: number;<br>差异内容：maxSelectNumber?: number;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：FileUri；<br>API声明：isRemoteUri(): boolean;<br>差异内容：isRemoteUri(): boolean;|api/@ohos.file.fileuri.d.ts|
|新增API|NA|类名：hash；<br>API声明：class HashStream<br>差异内容：class HashStream|api/@ohos.file.hash.d.ts|
|新增API|NA|类名：HashStream；<br>API声明：digest(): string;<br>差异内容：digest(): string;|api/@ohos.file.hash.d.ts|
|新增API|NA|类名：HashStream；<br>API声明：update(data: ArrayBuffer): void;<br>差异内容：update(data: ArrayBuffer): void;|api/@ohos.file.hash.d.ts|
|新增API|NA|类名：hash；<br>API声明：function createHash(algorithm: string): HashStream;<br>差异内容：function createHash(algorithm: string): HashStream;|api/@ohos.file.hash.d.ts|
|新增API|NA|类名：PolicyErrorCode；<br>API声明：PERMISSION_NOT_PERSISTED = 4<br>差异内容：PERMISSION_NOT_PERSISTED = 4|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：fileShare；<br>API声明：function checkPersistentPermission(policies: Array\<PolicyInfo>): Promise\<Array\<boolean>>;<br>差异内容：function checkPersistentPermission(policies: Array\<PolicyInfo>): Promise\<Array\<boolean>>;|api/@ohos.fileshare.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.file.BackupExtensionContext.d.ts<br>差异内容：CoreFileKit|api/@ohos.file.BackupExtensionContext.d.ts|
|API从不支持元服务到支持元服务|类名：picker；<br>API声明：export enum DocumentSelectMode<br>差异内容：NA|类名：picker；<br>API声明：export enum DocumentSelectMode<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：DocumentSelectMode；<br>API声明：FILE = 0<br>差异内容：NA|类名：DocumentSelectMode；<br>API声明：FILE = 0<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：DocumentSelectMode；<br>API声明：FOLDER = 1<br>差异内容：NA|类名：DocumentSelectMode；<br>API声明：FOLDER = 1<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：DocumentSelectMode；<br>API声明：MIXED = 2<br>差异内容：NA|类名：DocumentSelectMode；<br>API声明：MIXED = 2<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：picker；<br>API声明：class DocumentSelectOptions<br>差异内容：NA|类名：picker；<br>API声明：class DocumentSelectOptions<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：DocumentSelectOptions；<br>API声明：defaultFilePathUri?: string;<br>差异内容：NA|类名：DocumentSelectOptions；<br>API声明：defaultFilePathUri?: string;<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：DocumentSelectOptions；<br>API声明：fileSuffixFilters?: Array\<string>;<br>差异内容：NA|类名：DocumentSelectOptions；<br>API声明：fileSuffixFilters?: Array\<string>;<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：DocumentSelectOptions；<br>API声明：maxSelectNumber?: number;<br>差异内容：NA|类名：DocumentSelectOptions；<br>API声明：maxSelectNumber?: number;<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：DocumentSelectOptions；<br>API声明：selectMode?: DocumentSelectMode;<br>差异内容：NA|类名：DocumentSelectOptions；<br>API声明：selectMode?: DocumentSelectMode;<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：picker；<br>API声明：class DocumentSaveOptions<br>差异内容：NA|类名：picker；<br>API声明：class DocumentSaveOptions<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：DocumentSaveOptions；<br>API声明：newFileNames?: Array\<string>;<br>差异内容：NA|类名：DocumentSaveOptions；<br>API声明：newFileNames?: Array\<string>;<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：DocumentSaveOptions；<br>API声明：defaultFilePathUri?: string;<br>差异内容：NA|类名：DocumentSaveOptions；<br>API声明：defaultFilePathUri?: string;<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：DocumentSaveOptions；<br>API声明：fileSuffixChoices?: Array\<string>;<br>差异内容：NA|类名：DocumentSaveOptions；<br>API声明：fileSuffixChoices?: Array\<string>;<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：picker；<br>API声明：class DocumentViewPicker<br>差异内容：NA|类名：picker；<br>API声明：class DocumentViewPicker<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：DocumentViewPicker；<br>API声明：select(option?: DocumentSelectOptions): Promise\<Array\<string>>;<br>差异内容：NA|类名：DocumentViewPicker；<br>API声明：select(option?: DocumentSelectOptions): Promise\<Array\<string>>;<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：DocumentViewPicker；<br>API声明：select(option: DocumentSelectOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：NA|类名：DocumentViewPicker；<br>API声明：select(option: DocumentSelectOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：DocumentViewPicker；<br>API声明：select(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：NA|类名：DocumentViewPicker；<br>API声明：select(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：DocumentViewPicker；<br>API声明：save(option?: DocumentSaveOptions): Promise\<Array\<string>>;<br>差异内容：NA|类名：DocumentViewPicker；<br>API声明：save(option?: DocumentSaveOptions): Promise\<Array\<string>>;<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：DocumentViewPicker；<br>API声明：save(option: DocumentSaveOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：NA|类名：DocumentViewPicker；<br>API声明：save(option: DocumentSaveOptions, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：DocumentViewPicker；<br>API声明：save(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：NA|类名：DocumentViewPicker；<br>API声明：save(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：picker；<br>API声明：class AudioSelectOptions<br>差异内容：NA|类名：picker；<br>API声明：class AudioSelectOptions<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：picker；<br>API声明：class AudioSaveOptions<br>差异内容：NA|类名：picker；<br>API声明：class AudioSaveOptions<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：AudioSaveOptions；<br>API声明：newFileNames?: Array\<string>;<br>差异内容：NA|类名：AudioSaveOptions；<br>API声明：newFileNames?: Array\<string>;<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：picker；<br>API声明：class AudioViewPicker<br>差异内容：NA|类名：picker；<br>API声明：class AudioViewPicker<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：AudioViewPicker；<br>API声明：select(option?: AudioSelectOptions): Promise\<Array\<string>>;<br>差异内容：NA|类名：AudioViewPicker；<br>API声明：select(option?: AudioSelectOptions): Promise\<Array\<string>>;<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|API从不支持元服务到支持元服务|类名：AudioViewPicker；<br>API声明：save(option?: AudioSaveOptions): Promise\<Array\<string>>;<br>差异内容：NA|类名：AudioViewPicker；<br>API声明：save(option?: AudioSaveOptions): Promise\<Array\<string>>;<br>差异内容：atomicservice|api/@ohos.file.picker.d.ts|
|新增导出符号|类名：global；<br>API声明：export interface RandomAccessFileOptions<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export interface RandomAccessFileOptions|api/@ohos.file.fs.d.ts|
|新增导出符号|类名：global；<br>API声明：export interface ReadStreamOptions<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export interface ReadStreamOptions|api/@ohos.file.fs.d.ts|
|新增导出符号|类名：global；<br>API声明：export interface WriteStreamOptions<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export interface WriteStreamOptions|api/@ohos.file.fs.d.ts|
