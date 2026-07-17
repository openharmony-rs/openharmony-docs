# copyDir

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## copyDir

```TypeScript
declare function copyDir(src: string, dest: string, mode?: number): Promise<void>
```

复制源目录至目标路径下，使用promise异步回调。

**起始版本：** 10

<!--Device-unnamed-declare function copyDir(src: string, dest: string, mode?: number): Promise<void>--><!--Device-unnamed-declare function copyDir(src: string, dest: string, mode?: number): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| mode | number | 否 | 复制模式，默认值为0。<br/>- mode为0，文件级别抛异常。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则抛出异常。源目录下未冲突的文件全部移动至目标目录下，目标目录下未冲突文件将继续保留，且冲突文件信息将在抛出异常的data属性中以Array&lt;[ConflictFiles](arkts-corefile-file-fs-conflictfiles-i.md)&gt;形式提供。<br/>- mode为1，文件级别强制覆盖。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则强制覆盖冲突目录下所有同名文件，未冲突文件将继续保留。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900030 | File name too long |
| 13900031 | Function not implemented |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900042 | Unknown error |
| 13900044 | Network is unreachable<br>**适用版本：** 12+ |


## copyDir

```TypeScript
declare function copyDir(src: string, dest: string, callback: AsyncCallback<void>): void
```

复制源目录至目标路径下，使用callback异步回调。

**起始版本：** 10

<!--Device-unnamed-declare function copyDir(src: string, dest: string, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function copyDir(src: string, dest: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 异步复制目录之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900030 | File name too long |
| 13900031 | Function not implemented |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900042 | Unknown error |


## copyDir

```TypeScript
declare function copyDir(src: string, dest: string, callback: AsyncCallback<void, Array<ConflictFiles>>): void
```

复制源目录至目标路径下，使用callback异步回调。

如果目标目录下有与源目录名冲突的目录，且冲突目录下有同名文件，则抛出异常。源目录下未冲突的文件全部移动至目标目录下，目标目录下未冲突文件将继续保留，且冲突文件信息将在抛出异常的data属性中以Array\<[ConflictFiles](arkts-corefile-file-fs-conflictfiles-i.md)>形式提供。

**起始版本：** 10

<!--Device-unnamed-declare function copyDir(src: string, dest: string, callback: AsyncCallback<void, Array<ConflictFiles>>): void--><!--Device-unnamed-declare function copyDir(src: string, dest: string, callback: AsyncCallback<void, Array<ConflictFiles>>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void, Array<ConflictFiles>> | 是 | 异步复制目录之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900015 | File exists |


## copyDir

```TypeScript
declare function copyDir(src: string, dest: string, mode: number, callback: AsyncCallback<void>): void
```

复制源目录至目标路径下，可设置复制模式。使用callback异步回调。

**起始版本：** 10

<!--Device-unnamed-declare function copyDir(src: string, dest: string, mode: number, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function copyDir(src: string, dest: string, mode: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| mode | number | 是 | 复制模式，默认值为0。<br/>- mode为0，文件级别抛异常。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则抛出异常。源目录下未冲突的文件全部移动至目标目录下，目标目录下未冲突文件将继续保留，且冲突文件信息将在抛出异常的data属性中以Array&lt;[ConflictFiles](arkts-corefile-file-fs-conflictfiles-i.md)&gt;形式提供。<br/>- mode为1，文件级别强制覆盖。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则强制覆盖冲突目录下所有同名文件，未冲突文件将继续保留。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 异步复制目录之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900030 | File name too long |
| 13900031 | Function not implemented |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900042 | Unknown error |


## copyDir

```TypeScript
declare function copyDir(src: string, dest: string, mode: number, callback: AsyncCallback<void, Array<ConflictFiles>>): void
```

复制源目录至目标路径下，可设置复制模式。使用callback异步回调。

**起始版本：** 10

<!--Device-unnamed-declare function copyDir(src: string, dest: string, mode: number, callback: AsyncCallback<void, Array<ConflictFiles>>): void--><!--Device-unnamed-declare function copyDir(src: string, dest: string, mode: number, callback: AsyncCallback<void, Array<ConflictFiles>>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| mode | number | 是 | 复制模式，默认值为0。<br/>- mode为0，文件级别抛异常。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则抛出异常。源目录下未冲突的文件全部移动至目标目录下，目标目录下未冲突文件将继续保留，且冲突文件信息将在抛出异常的data属性中以Array&lt;[ConflictFiles](arkts-corefile-file-fs-conflictfiles-i.md)&gt;形式提供。<br/>- mode为1，文件级别强制覆盖。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则强制覆盖冲突目录下所有同名文件，未冲突文件将继续保留。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void, Array<ConflictFiles>> | 是 | 异步复制目录之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900015 | File exists |

