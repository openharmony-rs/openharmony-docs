| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API跨平台权限变更|类名：global；<br>API声明：declare function copyDir(src: string, dest: string, mode?: number): Promise\<void>;<br>差异内容：NA|类名：global；<br>API声明：declare function copyDir(src: string, dest: string, mode?: number): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function copyDir(src: string, dest: string, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：global；<br>API声明：declare function copyDir(src: string, dest: string, callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function copyDir(src: string, dest: string, callback: AsyncCallback\<void, Array\<ConflictFiles>>): void;<br>差异内容：NA|类名：global；<br>API声明：declare function copyDir(src: string, dest: string, callback: AsyncCallback\<void, Array\<ConflictFiles>>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function copyDir(src: string, dest: string, mode: number, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：global；<br>API声明：declare function copyDir(src: string, dest: string, mode: number, callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function copyDir(src: string, dest: string, mode: number, callback: AsyncCallback\<void, Array\<ConflictFiles>>): void;<br>差异内容：NA|类名：global；<br>API声明：declare function copyDir(src: string, dest: string, mode: number, callback: AsyncCallback\<void, Array\<ConflictFiles>>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function copyDirSync(src: string, dest: string, mode?: number): void;<br>差异内容：NA|类名：global；<br>API声明：declare function copyDirSync(src: string, dest: string, mode?: number): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function createStream(path: string, mode: string): Promise\<Stream>;<br>差异内容：NA|类名：global；<br>API声明：declare function createStream(path: string, mode: string): Promise\<Stream>;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function createStream(path: string, mode: string, callback: AsyncCallback\<Stream>): void;<br>差异内容：NA|类名：global；<br>API声明：declare function createStream(path: string, mode: string, callback: AsyncCallback\<Stream>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function createStreamSync(path: string, mode: string): Stream;<br>差异内容：NA|类名：global；<br>API声明：declare function createStreamSync(path: string, mode: string): Stream;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function createRandomAccessFile(file: string \| File, mode?: number, options?: RandomAccessFileOptions): Promise\<RandomAccessFile>;<br>差异内容：NA|类名：global；<br>API声明：declare function createRandomAccessFile(file: string \| File, mode?: number, options?: RandomAccessFileOptions): Promise\<RandomAccessFile>;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function createRandomAccessFile(file: string \| File, callback: AsyncCallback\<RandomAccessFile>): void;<br>差异内容：NA|类名：global；<br>API声明：declare function createRandomAccessFile(file: string \| File, callback: AsyncCallback\<RandomAccessFile>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function createRandomAccessFile(file: string \| File, mode: number, callback: AsyncCallback\<RandomAccessFile>): void;<br>差异内容：NA|类名：global；<br>API声明：declare function createRandomAccessFile(file: string \| File, mode: number, callback: AsyncCallback\<RandomAccessFile>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function createRandomAccessFileSync(file: string \| File, mode?: number, options?: RandomAccessFileOptions): RandomAccessFile;<br>差异内容：NA|类名：global；<br>API声明：declare function createRandomAccessFileSync(file: string \| File, mode?: number, options?: RandomAccessFileOptions): RandomAccessFile;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function createReadStream(path: string, options?: ReadStreamOptions): ReadStream;<br>差异内容：NA|类名：global；<br>API声明：declare function createReadStream(path: string, options?: ReadStreamOptions): ReadStream;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function createWriteStream(path: string, options?: WriteStreamOptions): WriteStream;<br>差异内容：NA|类名：global；<br>API声明：declare function createWriteStream(path: string, options?: WriteStreamOptions): WriteStream;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function createWatcher(path: string, events: number, listener: WatchEventListener): Watcher;<br>差异内容：NA|类名：global；<br>API声明：declare function createWatcher(path: string, events: number, listener: WatchEventListener): Watcher;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function fdopenStream(fd: number, mode: string): Promise\<Stream>;<br>差异内容：NA|类名：global；<br>API声明：declare function fdopenStream(fd: number, mode: string): Promise\<Stream>;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function fdopenStream(fd: number, mode: string, callback: AsyncCallback\<Stream>): void;<br>差异内容：NA|类名：global；<br>API声明：declare function fdopenStream(fd: number, mode: string, callback: AsyncCallback\<Stream>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function fdopenStreamSync(fd: number, mode: string): Stream;<br>差异内容：NA|类名：global；<br>API声明：declare function fdopenStreamSync(fd: number, mode: string): Stream;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function lstat(path: string): Promise\<Stat>;<br>差异内容：NA|类名：global；<br>API声明：declare function lstat(path: string): Promise\<Stat>;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function lstat(path: string, callback: AsyncCallback\<Stat>): void;<br>差异内容：NA|类名：global；<br>API声明：declare function lstat(path: string, callback: AsyncCallback\<Stat>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function lstatSync(path: string): Stat;<br>差异内容：NA|类名：global；<br>API声明：declare function lstatSync(path: string): Stat;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function mkdir(path: string, recursion: boolean): Promise\<void>;<br>差异内容：NA|类名：global；<br>API声明：declare function mkdir(path: string, recursion: boolean): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function mkdir(path: string, recursion: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：global；<br>API声明：declare function mkdir(path: string, recursion: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function mkdirSync(path: string, recursion: boolean): void;<br>差异内容：NA|类名：global；<br>API声明：declare function mkdirSync(path: string, recursion: boolean): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function moveDir(src: string, dest: string, mode?: number): Promise\<void>;<br>差异内容：NA|类名：global；<br>API声明：declare function moveDir(src: string, dest: string, mode?: number): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function moveDir(src: string, dest: string, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：global；<br>API声明：declare function moveDir(src: string, dest: string, callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function moveDir(src: string, dest: string, callback: AsyncCallback\<void, Array\<ConflictFiles>>): void;<br>差异内容：NA|类名：global；<br>API声明：declare function moveDir(src: string, dest: string, callback: AsyncCallback\<void, Array\<ConflictFiles>>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function moveDir(src: string, dest: string, mode: number, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：global；<br>API声明：declare function moveDir(src: string, dest: string, mode: number, callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function moveDir(src: string, dest: string, mode: number, callback: AsyncCallback\<void, Array\<ConflictFiles>>): void;<br>差异内容：NA|类名：global；<br>API声明：declare function moveDir(src: string, dest: string, mode: number, callback: AsyncCallback\<void, Array\<ConflictFiles>>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function moveDirSync(src: string, dest: string, mode?: number): void;<br>差异内容：NA|类名：global；<br>API声明：declare function moveDirSync(src: string, dest: string, mode?: number): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function readLines(filePath: string, options?: Options): Promise\<ReaderIterator>;<br>差异内容：NA|类名：global；<br>API声明：declare function readLines(filePath: string, options?: Options): Promise\<ReaderIterator>;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function readLines(filePath: string, callback: AsyncCallback\<ReaderIterator>): void;<br>差异内容：NA|类名：global；<br>API声明：declare function readLines(filePath: string, callback: AsyncCallback\<ReaderIterator>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function readLines(filePath: string, options: Options, callback: AsyncCallback\<ReaderIterator>): void;<br>差异内容：NA|类名：global；<br>API声明：declare function readLines(filePath: string, options: Options, callback: AsyncCallback\<ReaderIterator>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function readLinesSync(filePath: string, options?: Options): ReaderIterator;<br>差异内容：NA|类名：global；<br>API声明：declare function readLinesSync(filePath: string, options?: Options): ReaderIterator;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function setxattr(path: string, key: string, value: string): Promise\<void>;<br>差异内容：NA|类名：global；<br>API声明：declare function setxattr(path: string, key: string, value: string): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function setxattrSync(path: string, key: string, value: string): void;<br>差异内容：NA|类名：global；<br>API声明：declare function setxattrSync(path: string, key: string, value: string): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function getxattr(path: string, key: string): Promise\<string>;<br>差异内容：NA|类名：global；<br>API声明：declare function getxattr(path: string, key: string): Promise\<string>;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare function getxattrSync(path: string, key: string): string;<br>差异内容：NA|类名：global；<br>API声明：declare function getxattrSync(path: string, key: string): string;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：File；<br>API声明：getParent(): string;<br>差异内容：NA|类名：File；<br>API声明：getParent(): string;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare interface RandomAccessFile<br>差异内容：NA|类名：global；<br>API声明：declare interface RandomAccessFile<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：RandomAccessFile；<br>API声明：readonly fd: number;<br>差异内容：NA|类名：RandomAccessFile；<br>API声明：readonly fd: number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：RandomAccessFile；<br>API声明：readonly filePointer: number;<br>差异内容：NA|类名：RandomAccessFile；<br>API声明：readonly filePointer: number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：RandomAccessFile；<br>API声明：setFilePointer(filePointer: number): void;<br>差异内容：NA|类名：RandomAccessFile；<br>API声明：setFilePointer(filePointer: number): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：RandomAccessFile；<br>API声明：close(): void;<br>差异内容：NA|类名：RandomAccessFile；<br>API声明：close(): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：RandomAccessFile；<br>API声明：write(buffer: ArrayBuffer \| string, options?: WriteOptions): Promise\<number>;<br>差异内容：NA|类名：RandomAccessFile；<br>API声明：write(buffer: ArrayBuffer \| string, options?: WriteOptions): Promise\<number>;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：RandomAccessFile；<br>API声明：write(buffer: ArrayBuffer \| string, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：RandomAccessFile；<br>API声明：write(buffer: ArrayBuffer \| string, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：RandomAccessFile；<br>API声明：write(buffer: ArrayBuffer \| string, options: WriteOptions, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：RandomAccessFile；<br>API声明：write(buffer: ArrayBuffer \| string, options: WriteOptions, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：RandomAccessFile；<br>API声明：writeSync(buffer: ArrayBuffer \| string, options?: WriteOptions): number;<br>差异内容：NA|类名：RandomAccessFile；<br>API声明：writeSync(buffer: ArrayBuffer \| string, options?: WriteOptions): number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：RandomAccessFile；<br>API声明：read(buffer: ArrayBuffer, options?: ReadOptions): Promise\<number>;<br>差异内容：NA|类名：RandomAccessFile；<br>API声明：read(buffer: ArrayBuffer, options?: ReadOptions): Promise\<number>;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：RandomAccessFile；<br>API声明：read(buffer: ArrayBuffer, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：RandomAccessFile；<br>API声明：read(buffer: ArrayBuffer, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：RandomAccessFile；<br>API声明：read(buffer: ArrayBuffer, options: ReadOptions, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：RandomAccessFile；<br>API声明：read(buffer: ArrayBuffer, options: ReadOptions, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：RandomAccessFile；<br>API声明：readSync(buffer: ArrayBuffer, options?: ReadOptions): number;<br>差异内容：NA|类名：RandomAccessFile；<br>API声明：readSync(buffer: ArrayBuffer, options?: ReadOptions): number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare class ReadStream<br>差异内容：NA|类名：global；<br>API声明：declare class ReadStream<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：ReadStream；<br>API声明：readonly bytesRead: number;<br>差异内容：NA|类名：ReadStream；<br>API声明：readonly bytesRead: number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：ReadStream；<br>API声明：readonly path: string;<br>差异内容：NA|类名：ReadStream；<br>API声明：readonly path: string;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：ReadStream；<br>API声明：seek(offset: number, whence?: WhenceType): number;<br>差异内容：NA|类名：ReadStream；<br>API声明：seek(offset: number, whence?: WhenceType): number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：ReadStream；<br>API声明：close(): void;<br>差异内容：NA|类名：ReadStream；<br>API声明：close(): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare class WriteStream<br>差异内容：NA|类名：global；<br>API声明：declare class WriteStream<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：WriteStream；<br>API声明：readonly bytesWritten: number;<br>差异内容：NA|类名：WriteStream；<br>API声明：readonly bytesWritten: number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：WriteStream；<br>API声明：readonly path: string;<br>差异内容：NA|类名：WriteStream；<br>API声明：readonly path: string;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：WriteStream；<br>API声明：seek(offset: number, whence?: WhenceType): number;<br>差异内容：NA|类名：WriteStream；<br>API声明：seek(offset: number, whence?: WhenceType): number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：WriteStream；<br>API声明：close(): void;<br>差异内容：NA|类名：WriteStream；<br>API声明：close(): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare interface Stream<br>差异内容：NA|类名：global；<br>API声明：declare interface Stream<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：Stream；<br>API声明：close(): Promise\<void>;<br>差异内容：NA|类名：Stream；<br>API声明：close(): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：Stream；<br>API声明：close(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Stream；<br>API声明：close(callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：Stream；<br>API声明：closeSync(): void;<br>差异内容：NA|类名：Stream；<br>API声明：closeSync(): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：Stream；<br>API声明：flush(): Promise\<void>;<br>差异内容：NA|类名：Stream；<br>API声明：flush(): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：Stream；<br>API声明：flush(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Stream；<br>API声明：flush(callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：Stream；<br>API声明：flushSync(): void;<br>差异内容：NA|类名：Stream；<br>API声明：flushSync(): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：Stream；<br>API声明：write(buffer: ArrayBuffer \| string, options?: WriteOptions): Promise\<number>;<br>差异内容：NA|类名：Stream；<br>API声明：write(buffer: ArrayBuffer \| string, options?: WriteOptions): Promise\<number>;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：Stream；<br>API声明：write(buffer: ArrayBuffer \| string, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：Stream；<br>API声明：write(buffer: ArrayBuffer \| string, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：Stream；<br>API声明：write(buffer: ArrayBuffer \| string, options: WriteOptions, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：Stream；<br>API声明：write(buffer: ArrayBuffer \| string, options: WriteOptions, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：Stream；<br>API声明：writeSync(buffer: ArrayBuffer \| string, options?: WriteOptions): number;<br>差异内容：NA|类名：Stream；<br>API声明：writeSync(buffer: ArrayBuffer \| string, options?: WriteOptions): number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, options?: ReadOptions): Promise\<number>;<br>差异内容：NA|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, options?: ReadOptions): Promise\<number>;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, options: ReadOptions, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, options: ReadOptions, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：Stream；<br>API声明：readSync(buffer: ArrayBuffer, options?: ReadOptions): number;<br>差异内容：NA|类名：Stream；<br>API声明：readSync(buffer: ArrayBuffer, options?: ReadOptions): number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：export interface WatchEventListener<br>差异内容：NA|类名：global；<br>API声明：export interface WatchEventListener<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：export interface WatchEvent<br>差异内容：NA|类名：global；<br>API声明：export interface WatchEvent<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：WatchEvent；<br>API声明：readonly fileName: string;<br>差异内容：NA|类名：WatchEvent；<br>API声明：readonly fileName: string;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：WatchEvent；<br>API声明：readonly event: number;<br>差异内容：NA|类名：WatchEvent；<br>API声明：readonly event: number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：WatchEvent；<br>API声明：readonly cookie: number;<br>差异内容：NA|类名：WatchEvent；<br>API声明：readonly cookie: number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：export interface Watcher<br>差异内容：NA|类名：global；<br>API声明：export interface Watcher<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：Watcher；<br>API声明：start(): void;<br>差异内容：NA|类名：Watcher；<br>API声明：start(): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：Watcher；<br>API声明：stop(): void;<br>差异内容：NA|类名：Watcher；<br>API声明：stop(): void;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：export interface ReaderIteratorResult<br>差异内容：NA|类名：global；<br>API声明：export interface ReaderIteratorResult<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：ReaderIteratorResult；<br>API声明：done: boolean;<br>差异内容：NA|类名：ReaderIteratorResult；<br>API声明：done: boolean;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：ReaderIteratorResult；<br>API声明：value: string;<br>差异内容：NA|类名：ReaderIteratorResult；<br>API声明：value: string;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare interface ReaderIterator<br>差异内容：NA|类名：global；<br>API声明：declare interface ReaderIterator<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：ReaderIterator；<br>API声明：next(): ReaderIteratorResult;<br>差异内容：NA|类名：ReaderIterator；<br>API声明：next(): ReaderIteratorResult;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：export interface ConflictFiles<br>差异内容：NA|类名：global；<br>API声明：export interface ConflictFiles<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：ConflictFiles；<br>API声明：srcFile: string;<br>差异内容：NA|类名：ConflictFiles；<br>API声明：srcFile: string;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：ConflictFiles；<br>API声明：destFile: string;<br>差异内容：NA|类名：ConflictFiles；<br>API声明：destFile: string;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：export interface Options<br>差异内容：NA|类名：global；<br>API声明：export interface Options<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：Options；<br>API声明：encoding?: string;<br>差异内容：NA|类名：Options；<br>API声明：encoding?: string;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：export interface ReadOptions<br>差异内容：NA|类名：global；<br>API声明：export interface ReadOptions<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：ReadOptions；<br>API声明：offset?: number;<br>差异内容：NA|类名：ReadOptions；<br>API声明：offset?: number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：ReadOptions；<br>API声明：length?: number;<br>差异内容：NA|类名：ReadOptions；<br>API声明：length?: number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：export interface ReadTextOptions<br>差异内容：NA|类名：global；<br>API声明：export interface ReadTextOptions<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：ReadTextOptions；<br>API声明：encoding?: string;<br>差异内容：NA|类名：ReadTextOptions；<br>API声明：encoding?: string;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：export interface WriteOptions<br>差异内容：NA|类名：global；<br>API声明：export interface WriteOptions<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：WriteOptions；<br>API声明：offset?: number;<br>差异内容：NA|类名：WriteOptions；<br>API声明：offset?: number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：WriteOptions；<br>API声明：length?: number;<br>差异内容：NA|类名：WriteOptions；<br>API声明：length?: number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：export interface RandomAccessFileOptions<br>差异内容：NA|类名：global；<br>API声明：export interface RandomAccessFileOptions<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：RandomAccessFileOptions；<br>API声明：start?: number;<br>差异内容：NA|类名：RandomAccessFileOptions；<br>API声明：start?: number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：RandomAccessFileOptions；<br>API声明：end?: number;<br>差异内容：NA|类名：RandomAccessFileOptions；<br>API声明：end?: number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：export interface ReadStreamOptions<br>差异内容：NA|类名：global；<br>API声明：export interface ReadStreamOptions<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：ReadStreamOptions；<br>API声明：start?: number;<br>差异内容：NA|类名：ReadStreamOptions；<br>API声明：start?: number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：ReadStreamOptions；<br>API声明：end?: number;<br>差异内容：NA|类名：ReadStreamOptions；<br>API声明：end?: number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：export interface WriteStreamOptions<br>差异内容：NA|类名：global；<br>API声明：export interface WriteStreamOptions<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：WriteStreamOptions；<br>API声明：mode?: number;<br>差异内容：NA|类名：WriteStreamOptions；<br>API声明：mode?: number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：WriteStreamOptions；<br>API声明：start?: number;<br>差异内容：NA|类名：WriteStreamOptions；<br>API声明：start?: number;<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare enum WhenceType<br>差异内容：NA|类名：global；<br>API声明：declare enum WhenceType<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：WhenceType；<br>API声明：SEEK_SET = 0<br>差异内容：NA|类名：WhenceType；<br>API声明：SEEK_SET = 0<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：WhenceType；<br>API声明：SEEK_CUR = 1<br>差异内容：NA|类名：WhenceType；<br>API声明：SEEK_CUR = 1<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：WhenceType；<br>API声明：SEEK_END = 2<br>差异内容：NA|类名：WhenceType；<br>API声明：SEEK_END = 2<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare enum AccessModeType<br>差异内容：NA|类名：global；<br>API声明：declare enum AccessModeType<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：AccessModeType；<br>API声明：EXIST = 0<br>差异内容：NA|类名：AccessModeType；<br>API声明：EXIST = 0<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：AccessModeType；<br>API声明：WRITE = 2<br>差异内容：NA|类名：AccessModeType；<br>API声明：WRITE = 2<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：AccessModeType；<br>API声明：READ = 4<br>差异内容：NA|类名：AccessModeType；<br>API声明：READ = 4<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：AccessModeType；<br>API声明：READ_WRITE = 6<br>差异内容：NA|类名：AccessModeType；<br>API声明：READ_WRITE = 6<br>差异内容：crossplatform|api/@ohos.file.fs.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare namespace hash<br>差异内容：NA|类名：global；<br>API声明：declare namespace hash<br>差异内容：crossplatform|api/@ohos.file.hash.d.ts|
|API跨平台权限变更|类名：hash；<br>API声明：function hash(path: string, algorithm: string): Promise\<string>;<br>差异内容：NA|类名：hash；<br>API声明：function hash(path: string, algorithm: string): Promise\<string>;<br>差异内容：crossplatform|api/@ohos.file.hash.d.ts|
|API跨平台权限变更|类名：hash；<br>API声明：function hash(path: string, algorithm: string, callback: AsyncCallback\<string>): void;<br>差异内容：NA|类名：hash；<br>API声明：function hash(path: string, algorithm: string, callback: AsyncCallback\<string>): void;<br>差异内容：crossplatform|api/@ohos.file.hash.d.ts|
|API跨平台权限变更|类名：hash；<br>API声明：class HashStream<br>差异内容：NA|类名：hash；<br>API声明：class HashStream<br>差异内容：crossplatform|api/@ohos.file.hash.d.ts|
|API跨平台权限变更|类名：HashStream；<br>API声明：digest(): string;<br>差异内容：NA|类名：HashStream；<br>API声明：digest(): string;<br>差异内容：crossplatform|api/@ohos.file.hash.d.ts|
|API跨平台权限变更|类名：HashStream；<br>API声明：update(data: ArrayBuffer): void;<br>差异内容：NA|类名：HashStream；<br>API声明：update(data: ArrayBuffer): void;<br>差异内容：crossplatform|api/@ohos.file.hash.d.ts|
|API跨平台权限变更|类名：hash；<br>API声明：function createHash(algorithm: string): HashStream;<br>差异内容：NA|类名：hash；<br>API声明：function createHash(algorithm: string): HashStream;<br>差异内容：crossplatform|api/@ohos.file.hash.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare namespace statfs<br>差异内容：NA|类名：global；<br>API声明：declare namespace statfs<br>差异内容：crossplatform|api/@ohos.file.statvfs.d.ts|
|API跨平台权限变更|类名：statfs；<br>API声明：function getFreeSize(path: string): Promise\<number>;<br>差异内容：NA|类名：statfs；<br>API声明：function getFreeSize(path: string): Promise\<number>;<br>差异内容：crossplatform|api/@ohos.file.statvfs.d.ts|
|API跨平台权限变更|类名：statfs；<br>API声明：function getFreeSize(path: string, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：statfs；<br>API声明：function getFreeSize(path: string, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|api/@ohos.file.statvfs.d.ts|
|API跨平台权限变更|类名：statfs；<br>API声明：function getFreeSizeSync(path: string): number;<br>差异内容：NA|类名：statfs；<br>API声明：function getFreeSizeSync(path: string): number;<br>差异内容：crossplatform|api/@ohos.file.statvfs.d.ts|
|API跨平台权限变更|类名：statfs；<br>API声明：function getTotalSize(path: string): Promise\<number>;<br>差异内容：NA|类名：statfs；<br>API声明：function getTotalSize(path: string): Promise\<number>;<br>差异内容：crossplatform|api/@ohos.file.statvfs.d.ts|
|API跨平台权限变更|类名：statfs；<br>API声明：function getTotalSize(path: string, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：statfs；<br>API声明：function getTotalSize(path: string, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|api/@ohos.file.statvfs.d.ts|
|API跨平台权限变更|类名：statfs；<br>API声明：function getTotalSizeSync(path: string): number;<br>差异内容：NA|类名：statfs；<br>API声明：function getTotalSizeSync(path: string): number;<br>差异内容：crossplatform|api/@ohos.file.statvfs.d.ts|
|API废弃版本变更|类名：PhotoViewMIMETypes；<br>API声明：IMAGE_TYPE = 'image/*'<br>差异内容：NA|类名：PhotoViewMIMETypes；<br>API声明：IMAGE_TYPE = 'image/*'<br>差异内容：18|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoViewMIMETypes；<br>API声明：VIDEO_TYPE = 'video/*'<br>差异内容：NA|类名：PhotoViewMIMETypes；<br>API声明：VIDEO_TYPE = 'video/*'<br>差异内容：18|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoViewMIMETypes；<br>API声明：IMAGE_VIDEO_TYPE = '*/*'<br>差异内容：NA|类名：PhotoViewMIMETypes；<br>API声明：IMAGE_VIDEO_TYPE = '*/*'<br>差异内容：18|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoSelectOptions；<br>API声明：MIMEType?: PhotoViewMIMETypes;<br>差异内容：NA|类名：PhotoSelectOptions；<br>API声明：MIMEType?: PhotoViewMIMETypes;<br>差异内容：18|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoSelectOptions；<br>API声明：maxSelectNumber?: number;<br>差异内容：NA|类名：PhotoSelectOptions；<br>API声明：maxSelectNumber?: number;<br>差异内容：18|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoSelectResult；<br>API声明：photoUris: Array\<string>;<br>差异内容：NA|类名：PhotoSelectResult；<br>API声明：photoUris: Array\<string>;<br>差异内容：18|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoSelectResult；<br>API声明：isOriginalPhoto: boolean;<br>差异内容：NA|类名：PhotoSelectResult；<br>API声明：isOriginalPhoto: boolean;<br>差异内容：18|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoSaveOptions；<br>API声明：newFileNames?: Array\<string>;<br>差异内容：NA|类名：PhotoSaveOptions；<br>API声明：newFileNames?: Array\<string>;<br>差异内容：18|api/@ohos.file.picker.d.ts|
|删除错误码|类名：fileShare；<br>API声明：function checkPersistentPermission(policies: Array\<PolicyInfo>): Promise\<Array\<boolean>>;<br>差异内容：201|类名：fileShare；<br>API声明：function checkPersistentPermission(policies: Array\<PolicyInfo>): Promise\<Array\<boolean>>;<br>差异内容：NA|api/@ohos.fileshare.d.ts|
|权限变更|类名：fileShare；<br>API声明：function checkPersistentPermission(policies: Array\<PolicyInfo>): Promise\<Array\<boolean>>;<br>差异内容：ohos.permission.FILE_ACCESS_PERSIST|类名：fileShare；<br>API声明：function checkPersistentPermission(policies: Array\<PolicyInfo>): Promise\<Array\<boolean>>;<br>差异内容：NA|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace keyManager<br>差异内容：declare namespace keyManager|api/@ohos.file.keyManager.d.ts|
|新增API|NA|类名：global；<br>API声明：export class AtomicFile<br>差异内容：export class AtomicFile|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：AtomicFile；<br>API声明：getBaseFile(): File;<br>差异内容：getBaseFile(): File;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：AtomicFile；<br>API声明：openRead(): ReadStream;<br>差异内容：openRead(): ReadStream;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：AtomicFile；<br>API声明：readFully(): ArrayBuffer;<br>差异内容：readFully(): ArrayBuffer;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：AtomicFile；<br>API声明：startWrite(): WriteStream;<br>差异内容：startWrite(): WriteStream;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：AtomicFile；<br>API声明：finishWrite(): void;<br>差异内容：finishWrite(): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：AtomicFile；<br>API声明：failWrite(): void;<br>差异内容：failWrite(): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：AtomicFile；<br>API声明：delete(): void;<br>差异内容：delete(): void;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly atimeNs?: bigint;<br>差异内容：readonly atimeNs?: bigint;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly mtimeNs?: bigint;<br>差异内容：readonly mtimeNs?: bigint;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：Stat；<br>API声明：readonly ctimeNs?: bigint;<br>差异内容：readonly ctimeNs?: bigint;|api/@ohos.file.fs.d.ts|
|新增API|NA|类名：BackupExtensionAbility；<br>API声明：onRelease(scenario: number): Promise\<void>;<br>差异内容：onRelease(scenario: number): Promise\<void>;|api/@ohos.application.BackupExtensionAbility.d.ts|
|新增API|NA|类名：picker；<br>API声明：export enum MergeTypeMode<br>差异内容：export enum MergeTypeMode|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：MergeTypeMode；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：MergeTypeMode；<br>API声明：AUDIO = 1<br>差异内容：AUDIO = 1|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：MergeTypeMode；<br>API声明：VIDEO = 2<br>差异内容：VIDEO = 2|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：MergeTypeMode；<br>API声明：DOCUMENT = 3<br>差异内容：DOCUMENT = 3|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：MergeTypeMode；<br>API声明：PICTURE = 4<br>差异内容：PICTURE = 4|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentSelectOptions；<br>API声明：multiAuthMode?: boolean;<br>差异内容：multiAuthMode?: boolean;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentSelectOptions；<br>API声明：multiUriArray?: Array\<string>;<br>差异内容：multiUriArray?: Array\<string>;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentSelectOptions；<br>API声明：mergeMode?: MergeTypeMode;<br>差异内容：mergeMode?: MergeTypeMode;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：DocumentSelectOptions；<br>API声明：isEncryptionSupported?: boolean;<br>差异内容：isEncryptionSupported?: boolean;|api/@ohos.file.picker.d.ts|
|新增API|NA|类名：OperationMode；<br>API声明：CREATE_MODE = 0b100<br>差异内容：CREATE_MODE = 0b100|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：OperationMode；<br>API声明：DELETE_MODE = 0b1000<br>差异内容：DELETE_MODE = 0b1000|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：OperationMode；<br>API声明：RENAME_MODE = 0b10000<br>差异内容：RENAME_MODE = 0b10000|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：fileShare；<br>API声明：export interface PathPolicyInfo<br>差异内容：export interface PathPolicyInfo|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：PathPolicyInfo；<br>API声明：path: string;<br>差异内容：path: string;|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：PathPolicyInfo；<br>API声明：operationMode: OperationMode;<br>差异内容：operationMode: OperationMode;|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：fileShare；<br>API声明：export enum PolicyType<br>差异内容：export enum PolicyType|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：PolicyType；<br>API声明：TEMPORARY_TYPE = 0<br>差异内容：TEMPORARY_TYPE = 0|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：PolicyType；<br>API声明：PERSISTENT_TYPE = 1<br>差异内容：PERSISTENT_TYPE = 1|api/@ohos.fileshare.d.ts|
|新增API|NA|类名：ErrorType；<br>API声明：REMOTE_SERVER_ABNORMAL = 8<br>差异内容：REMOTE_SERVER_ABNORMAL = 8|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：enum DownloadFileType<br>差异内容：enum DownloadFileType|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：DownloadFileType；<br>API声明：CONTENT = 0<br>差异内容：CONTENT = 0|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：DownloadFileType；<br>API声明：THUMBNAIL = 1<br>差异内容：THUMBNAIL = 1|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：DownloadFileType；<br>API声明：LCD = 2<br>差异内容：LCD = 2|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：interface FailedFileInfo<br>差异内容：interface FailedFileInfo|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FailedFileInfo；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FailedFileInfo；<br>API声明：error: DownloadErrorType;<br>差异内容：error: DownloadErrorType;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：class MultiDownloadProgress<br>差异内容：class MultiDownloadProgress|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：MultiDownloadProgress；<br>API声明：state: State;<br>差异内容：state: State;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：MultiDownloadProgress；<br>API声明：taskId: number;<br>差异内容：taskId: number;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：MultiDownloadProgress；<br>API声明：successfulCount: number;<br>差异内容：successfulCount: number;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：MultiDownloadProgress；<br>API声明：failedCount: number;<br>差异内容：failedCount: number;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：MultiDownloadProgress；<br>API声明：totalCount: number;<br>差异内容：totalCount: number;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：MultiDownloadProgress；<br>API声明：downloadedSize: number;<br>差异内容：downloadedSize: number;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：MultiDownloadProgress；<br>API声明：totalSize: number;<br>差异内容：totalSize: number;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：MultiDownloadProgress；<br>API声明：errType: DownloadErrorType;<br>差异内容：errType: DownloadErrorType;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：MultiDownloadProgress；<br>API声明：getFailedFiles(): Array\<FailedFileInfo>;<br>差异内容：getFailedFiles(): Array\<FailedFileInfo>;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：MultiDownloadProgress；<br>API声明：getSuccessfulFiles(): Array\<string>;<br>差异内容：getSuccessfulFiles(): Array\<string>;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：CloudFileCache；<br>API声明：on(event: 'batchDownload', callback: Callback\<MultiDownloadProgress>): void;<br>差异内容：on(event: 'batchDownload', callback: Callback\<MultiDownloadProgress>): void;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：CloudFileCache；<br>API声明：off(event: 'batchDownload', callback?: Callback\<MultiDownloadProgress>): void;<br>差异内容：off(event: 'batchDownload', callback?: Callback\<MultiDownloadProgress>): void;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：CloudFileCache；<br>API声明：startBatch(uris: Array\<string>, fileType?: DownloadFileType): Promise\<number>;<br>差异内容：startBatch(uris: Array\<string>, fileType?: DownloadFileType): Promise\<number>;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：CloudFileCache；<br>API声明：stopBatch(downloadId: number, needClean?: boolean): Promise\<void>;<br>差异内容：stopBatch(downloadId: number, needClean?: boolean): Promise\<void>;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：CloudFileCache；<br>API声明：cleanFileCache(uri: string): void;<br>差异内容：cleanFileCache(uri: string): void;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：enum FileState<br>差异内容：enum FileState|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileState；<br>API声明：INITIAL_AFTER_DOWNLOAD = 0<br>差异内容：INITIAL_AFTER_DOWNLOAD = 0|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileState；<br>API声明：UPLOADING = 1<br>差异内容：UPLOADING = 1|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileState；<br>API声明：STOPPED = 2<br>差异内容：STOPPED = 2|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileState；<br>API声明：TO_BE_UPLOADED = 3<br>差异内容：TO_BE_UPLOADED = 3|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileState；<br>API声明：UPLOAD_SUCCESS = 4<br>差异内容：UPLOAD_SUCCESS = 4|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileState；<br>API声明：UPLOAD_FAILURE = 5<br>差异内容：UPLOAD_FAILURE = 5|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：function getCoreFileSyncState(uri: string): FileState;<br>差异内容：function getCoreFileSyncState(uri: string): FileState;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：interface HistoryVersion<br>差异内容：interface HistoryVersion|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：HistoryVersion；<br>API声明：editedTime: number;<br>差异内容：editedTime: number;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：HistoryVersion；<br>API声明：fileSize: number;<br>差异内容：fileSize: number;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：HistoryVersion；<br>API声明：versionId: string;<br>差异内容：versionId: string;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：HistoryVersion；<br>API声明：originalFileName: string;<br>差异内容：originalFileName: string;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：HistoryVersion；<br>API声明：sha256: string;<br>差异内容：sha256: string;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：HistoryVersion；<br>API声明：autoResolved: boolean;<br>差异内容：autoResolved: boolean;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：interface VersionDownloadProgress<br>差异内容：interface VersionDownloadProgress|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：VersionDownloadProgress；<br>API声明：state: State;<br>差异内容：state: State;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：VersionDownloadProgress；<br>API声明：progress: number;<br>差异内容：progress: number;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：VersionDownloadProgress；<br>API声明：errType: DownloadErrorType;<br>差异内容：errType: DownloadErrorType;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSync；<br>API声明：class FileVersion<br>差异内容：class FileVersion|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileVersion；<br>API声明：getHistoryVersionList(uri: string, versionNumLimit: number): Promise\<Array\<HistoryVersion>>;<br>差异内容：getHistoryVersionList(uri: string, versionNumLimit: number): Promise\<Array\<HistoryVersion>>;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileVersion；<br>API声明：downloadHistoryVersion(uri: string, versionId: string, callback: Callback\<VersionDownloadProgress>): Promise\<string>;<br>差异内容：downloadHistoryVersion(uri: string, versionId: string, callback: Callback\<VersionDownloadProgress>): Promise\<string>;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileVersion；<br>API声明：replaceFileWithHistoryVersion(originalUri: string, versionUri: string): Promise\<void>;<br>差异内容：replaceFileWithHistoryVersion(originalUri: string, versionUri: string): Promise\<void>;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileVersion；<br>API声明：isFileConflict(uri: string): Promise\<boolean>;<br>差异内容：isFileConflict(uri: string): Promise\<boolean>;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：FileVersion；<br>API声明：clearFileConflict(uri: string): Promise\<void>;<br>差异内容：clearFileConflict(uri: string): Promise\<void>;|api/@ohos.file.cloudSync.d.ts|
|新增API|NA|类名：cloudSyncManager；<br>API声明：enum DownloadStopReason<br>差异内容：enum DownloadStopReason|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：DownloadStopReason；<br>API声明：NO_STOP = 0<br>差异内容：NO_STOP = 0|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：DownloadStopReason；<br>API声明：NETWORK_UNAVAILABLE = 1<br>差异内容：NETWORK_UNAVAILABLE = 1|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：DownloadStopReason；<br>API声明：LOCAL_STORAGE_FULL = 2<br>差异内容：LOCAL_STORAGE_FULL = 2|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：DownloadStopReason；<br>API声明：TEMPERATURE_LIMIT = 3<br>差异内容：TEMPERATURE_LIMIT = 3|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：DownloadStopReason；<br>API声明：USER_STOPPED = 4<br>差异内容：USER_STOPPED = 4|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：DownloadStopReason；<br>API声明：APP_UNLOAD = 5<br>差异内容：APP_UNLOAD = 5|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：DownloadStopReason；<br>API声明：OTHER_REASON = 6<br>差异内容：OTHER_REASON = 6|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：cloudSyncManager；<br>API声明：enum DownloadState<br>差异内容：enum DownloadState|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：DownloadState；<br>API声明：RUNNING = 0<br>差异内容：RUNNING = 0|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：DownloadState；<br>API声明：COMPLETED = 1<br>差异内容：COMPLETED = 1|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：DownloadState；<br>API声明：STOPPED = 2<br>差异内容：STOPPED = 2|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：cloudSyncManager；<br>API声明：interface CloudFileInfo<br>差异内容：interface CloudFileInfo|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：CloudFileInfo；<br>API声明：cloudFileCount: number;<br>差异内容：cloudFileCount: number;|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：CloudFileInfo；<br>API声明：cloudFileTotalSize: number;<br>差异内容：cloudFileTotalSize: number;|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：CloudFileInfo；<br>API声明：localFileCount: number;<br>差异内容：localFileCount: number;|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：CloudFileInfo；<br>API声明：localFileTotalSize: number;<br>差异内容：localFileTotalSize: number;|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：CloudFileInfo；<br>API声明：bothFileCount: number;<br>差异内容：bothFileCount: number;|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：CloudFileInfo；<br>API声明：bothFileTotalSize: number;<br>差异内容：bothFileTotalSize: number;|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：cloudSyncManager；<br>API声明：class DownloadProgress<br>差异内容：class DownloadProgress|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：DownloadProgress；<br>API声明：state: DownloadState;<br>差异内容：state: DownloadState;|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：DownloadProgress；<br>API声明：successfulCount: number;<br>差异内容：successfulCount: number;|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：DownloadProgress；<br>API声明：failedCount: number;<br>差异内容：failedCount: number;|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：DownloadProgress；<br>API声明：totalCount: number;<br>差异内容：totalCount: number;|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：DownloadProgress；<br>API声明：downloadedSize: number;<br>差异内容：downloadedSize: number;|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：DownloadProgress；<br>API声明：totalSize: number;<br>差异内容：totalSize: number;|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：DownloadProgress；<br>API声明：stopReason: DownloadStopReason;<br>差异内容：stopReason: DownloadStopReason;|api/@ohos.file.cloudSyncManager.d.ts|
|新增API|NA|类名：storageStatistics；<br>API声明：function getTotalSize(callback: AsyncCallback\<number>): void;<br>差异内容：function getTotalSize(callback: AsyncCallback\<number>): void;|api/@ohos.file.storageStatistics.d.ts|
|新增API|NA|类名：storageStatistics；<br>API声明：function getTotalSize(): Promise\<number>;<br>差异内容：function getTotalSize(): Promise\<number>;|api/@ohos.file.storageStatistics.d.ts|
|新增API|NA|类名：storageStatistics；<br>API声明：function getTotalSizeSync(): number;<br>差异内容：function getTotalSizeSync(): number;|api/@ohos.file.storageStatistics.d.ts|
|新增API|NA|类名：storageStatistics；<br>API声明：function getFreeSize(callback: AsyncCallback\<number>): void;<br>差异内容：function getFreeSize(callback: AsyncCallback\<number>): void;|api/@ohos.file.storageStatistics.d.ts|
|新增API|NA|类名：storageStatistics；<br>API声明：function getFreeSize(): Promise\<number>;<br>差异内容：function getFreeSize(): Promise\<number>;|api/@ohos.file.storageStatistics.d.ts|
|新增API|NA|类名：storageStatistics；<br>API声明：function getFreeSizeSync(): number;<br>差异内容：function getFreeSizeSync(): number;|api/@ohos.file.storageStatistics.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.file.keyManager.d.ts<br>差异内容：CoreFileKit|api/@ohos.file.keyManager.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare function createStream(path: string, mode: string): Promise\<Stream>;<br>差异内容：NA|类名：global；<br>API声明：declare function createStream(path: string, mode: string): Promise\<Stream>;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare function createStream(path: string, mode: string, callback: AsyncCallback\<Stream>): void;<br>差异内容：NA|类名：global；<br>API声明：declare function createStream(path: string, mode: string, callback: AsyncCallback\<Stream>): void;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare function createStreamSync(path: string, mode: string): Stream;<br>差异内容：NA|类名：global；<br>API声明：declare function createStreamSync(path: string, mode: string): Stream;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare function fdopenStream(fd: number, mode: string): Promise\<Stream>;<br>差异内容：NA|类名：global；<br>API声明：declare function fdopenStream(fd: number, mode: string): Promise\<Stream>;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare function fdopenStream(fd: number, mode: string, callback: AsyncCallback\<Stream>): void;<br>差异内容：NA|类名：global；<br>API声明：declare function fdopenStream(fd: number, mode: string, callback: AsyncCallback\<Stream>): void;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare function fdopenStreamSync(fd: number, mode: string): Stream;<br>差异内容：NA|类名：global；<br>API声明：declare function fdopenStreamSync(fd: number, mode: string): Stream;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface Stream<br>差异内容：NA|类名：global；<br>API声明：declare interface Stream<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：Stream；<br>API声明：close(): Promise\<void>;<br>差异内容：NA|类名：Stream；<br>API声明：close(): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：Stream；<br>API声明：close(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Stream；<br>API声明：close(callback: AsyncCallback\<void>): void;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：Stream；<br>API声明：closeSync(): void;<br>差异内容：NA|类名：Stream；<br>API声明：closeSync(): void;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：Stream；<br>API声明：flush(): Promise\<void>;<br>差异内容：NA|类名：Stream；<br>API声明：flush(): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：Stream；<br>API声明：flush(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Stream；<br>API声明：flush(callback: AsyncCallback\<void>): void;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：Stream；<br>API声明：flushSync(): void;<br>差异内容：NA|类名：Stream；<br>API声明：flushSync(): void;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：Stream；<br>API声明：write(buffer: ArrayBuffer \| string, options?: WriteOptions): Promise\<number>;<br>差异内容：NA|类名：Stream；<br>API声明：write(buffer: ArrayBuffer \| string, options?: WriteOptions): Promise\<number>;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：Stream；<br>API声明：write(buffer: ArrayBuffer \| string, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：Stream；<br>API声明：write(buffer: ArrayBuffer \| string, callback: AsyncCallback\<number>): void;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：Stream；<br>API声明：write(buffer: ArrayBuffer \| string, options: WriteOptions, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：Stream；<br>API声明：write(buffer: ArrayBuffer \| string, options: WriteOptions, callback: AsyncCallback\<number>): void;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：Stream；<br>API声明：writeSync(buffer: ArrayBuffer \| string, options?: WriteOptions): number;<br>差异内容：NA|类名：Stream；<br>API声明：writeSync(buffer: ArrayBuffer \| string, options?: WriteOptions): number;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, options?: ReadOptions): Promise\<number>;<br>差异内容：NA|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, options?: ReadOptions): Promise\<number>;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, callback: AsyncCallback\<number>): void;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, options: ReadOptions, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：Stream；<br>API声明：read(buffer: ArrayBuffer, options: ReadOptions, callback: AsyncCallback\<number>): void;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：Stream；<br>API声明：readSync(buffer: ArrayBuffer, options?: ReadOptions): number;<br>差异内容：NA|类名：Stream；<br>API声明：readSync(buffer: ArrayBuffer, options?: ReadOptions): number;<br>差异内容：atomicservice|api/@ohos.file.fs.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace fileUri<br>差异内容：NA|类名：global；<br>API声明：declare namespace fileUri<br>差异内容：atomicservice|api/@ohos.file.fileuri.d.ts|
|API从不支持元服务到支持元服务|类名：fileUri；<br>API声明：class FileUri<br>差异内容：NA|类名：fileUri；<br>API声明：class FileUri<br>差异内容：atomicservice|api/@ohos.file.fileuri.d.ts|
|API从不支持元服务到支持元服务|类名：FileUri；<br>API声明：readonly name: string;<br>差异内容：NA|类名：FileUri；<br>API声明：readonly name: string;<br>差异内容：atomicservice|api/@ohos.file.fileuri.d.ts|
|API从不支持元服务到支持元服务|类名：FileUri；<br>API声明：getFullDirectoryUri(): string;<br>差异内容：NA|类名：FileUri；<br>API声明：getFullDirectoryUri(): string;<br>差异内容：atomicservice|api/@ohos.file.fileuri.d.ts|
|API从不支持元服务到支持元服务|类名：FileUri；<br>API声明：isRemoteUri(): boolean;<br>差异内容：NA|类名：FileUri；<br>API声明：isRemoteUri(): boolean;<br>差异内容：atomicservice|api/@ohos.file.fileuri.d.ts|
|API从不支持元服务到支持元服务|类名：fileUri；<br>API声明：function getUriFromPath(path: string): string;<br>差异内容：NA|类名：fileUri；<br>API声明：function getUriFromPath(path: string): string;<br>差异内容：atomicservice|api/@ohos.file.fileuri.d.ts|
|新增导出符号|类名：global；<br>API声明：export class AtomicFile<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export class AtomicFile|api/@ohos.file.fs.d.ts|
|arkts演进版本整改兼容变化|类名：global；<br>API声明：export default class BackupExtensionAbility<br>差异内容：NA|类名：global；<br>API声明：declare class BackupExtensionAbility<br>差异内容：NA|api/@ohos.application.BackupExtensionAbility.d.ts|
