# moveDir

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## moveDir

```TypeScript
declare function moveDir(src: string, dest: string, mode?: number): Promise<void>
```

移动源目录及其内容至目标路径下。使用Promise异步回调。

> **说明：**
> 
> 该接口不支持在分布式文件路径下操作。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| mode | number | 否 | 移动模式，默认值为0。   - mode为0，目录级别抛异常。若目标目录下存在与源目录名冲突的非空目录，则抛出异常。   - mode为1，文件级别抛异常。目标目录下存在与 源目录名冲突的目录，若冲突目录下存在同名文件，则抛出异常。源目录下未冲突的文件全部移动至目标目录下，目标目录下未冲突文件将继续保留，且冲突文件信息将在抛出异常的data属性中以Array&lt;[ConflictFiles](arkts-corefile-file-fs-conflictfiles-i.md)&gt;形式提供。   - mode为2，文件级别强制覆盖。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则强制覆盖冲突目录下所有同名文件 ，未冲突文件将继续保留。   - mode为3，目录级别强制覆盖。移动源目录至目标目录下，目标目录下移动的目录内容与源目录完全一致。若目标目录下存在与源目录名冲突的目录，该目录下的所有原始文件将被删除。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象。无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900016 | Cross-device link |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900028 | Too many links |
| 13900032 | Directory not empty |
| 13900033 | Too many symbolic links encountered |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let srcPath = pathDir + "/srcDir";
let destPath = pathDir + "/destDir";
fileIo.moveDir(srcPath, destPath, 1).then(() => {
  console.info(`Succeeded in moving directory.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to move directory. Code: ${err.code}, message: ${err.message}`);
});
```


## moveDir

```TypeScript
declare function moveDir(src: string, dest: string, callback: AsyncCallback<void>): void
```

移动源目录及其内容至目标路径下。使用callback异步回调。移动模式为目录级别抛异常。当目标目录下存在与源目录名冲突的目录，则抛出异常。

> **说明：**
> 
> 该接口不支持在分布式文件路径下操作。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当移动目录成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900016 | Cross-device link |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900028 | Too many links |
| 13900032 | Directory not empty |
| 13900033 | Too many symbolic links encountered |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let srcPath = pathDir + "/srcDir";
let destPath = pathDir + "/destDir";
fileIo.moveDir(srcPath, destPath, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to move directory. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in moving directory.`);
  }
});
```


## moveDir

```TypeScript
declare function moveDir(src: string, dest: string, callback: AsyncCallback<void, Array<ConflictFiles>>): void
```

移动源目录及其内容至目标路径下。使用callback异步回调。移动模式为目录级别抛异常。当目标目录下存在与源目录名冲突的目录，则抛出异常。

> **说明：**
> 
> 该接口不支持在分布式文件路径下操作。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void, Array&lt;[ConflictFiles](arkts-corefile-file-fs-conflictfiles-i.md)&gt;&gt; | 是 | 回调函数。当移动目录成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900015 | File exists |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { ConflictFiles } from '@kit.CoreFileKit';

let srcPath = pathDir + "/srcDir";
let destPath = pathDir + "/destDir";
fileIo.moveDir(srcPath, destPath, (err: BusinessError<Array<ConflictFiles>>) => {
  if (err && err.code == 13900015 && err.data?.length !== undefined) {
    for (let i = 0; i < err.data.length; i++) {
      console.error(`Failed to move directory, with conflicting files: ${err.data[i].srcFile} ${err.data[i].destFile}`);
    }
  } else if (err) {
    console.error(`Failed to move directory. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in moving directory.`);
  }
});
```


## moveDir

```TypeScript
declare function moveDir(src: string, dest: string, mode: number, callback: AsyncCallback<void>): void
```

移动源目录及其内容至目标路径下，支持设置冲突处理模式。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| mode | number | 是 | 移动模式。   - mode为0，目录级别抛异常。若目标目录下存在与源目录名冲突的目录，则抛出异常。  - mode为1，文件级别抛异常。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则抛出异常。源目录下未冲突的文件全部移动至目标目录下，目标目录下未冲突文件将继续保留。  - mode为2，文件级别强制覆盖。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则强制覆盖冲突目录下所有同名文件，未冲突文件将继续保留。  - mode为3，目录级别强制覆盖。移动源目录至目标目录下，目标目录下移动的目录内容与源目录完全一致。若目标目录下存在与源目录名冲突的目录，该目录下所有原始文件将被删除。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当移动目录成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900016 | Cross-device link |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900028 | Too many links |
| 13900032 | Directory not empty |
| 13900033 | Too many symbolic links encountered |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let srcPath = pathDir + "/srcDir";
let destPath = pathDir + "/destDir";
fileIo.moveDir(srcPath, destPath, 1, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to move directory. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in moving directory.`);
  }
});
```


## moveDir

```TypeScript
declare function moveDir(src: string, dest: string, mode: number, callback: AsyncCallback<void, Array<ConflictFiles>>): void
```

移动源目录及其内容至目标路径下，支持设置冲突处理模式。使用callback异步回调。

> **说明：**
> 
> 该接口不支持在分布式文件路径下操作。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| mode | number | 是 | 移动模式。   - mode为0，目录级别抛异常。若目标目录下存在与源目录名冲突的目录，则抛出异常。  - mode为1，文件级别抛异常。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则抛出异常。源目录下未冲突的文件全部移动至目标目录下，目标目录下未冲突文件将继续保留，   且冲突文件信息将在抛出异常的data属性中以Array&lt;[ConflictFiles](arkts-corefile-file-fs-conflictfiles-i.md)&gt;形式提供。  - mode为2，文件级别强制覆盖。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则强制覆盖冲突目录下所有同名文件   ，未冲突文件将继续保留。   - mode为3，目录级别强制覆盖。移动源目录至目标目录下，目标目录下移动的目录内容与源目录完全一致。若目标目录下存在与源目录名冲突的目录，该目录下所有原始文件将被删除。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void, Array&lt;[ConflictFiles](arkts-corefile-file-fs-conflictfiles-i.md)&gt;&gt; | 是 | 回调函数。当移动目录成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900015 | File exists |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { ConflictFiles } from '@kit.CoreFileKit';

let srcPath = pathDir + "/srcDir";
let destPath = pathDir + "/destDir";
fileIo.moveDir(srcPath, destPath, 1, (err: BusinessError<Array<ConflictFiles>>) => {
  if (err && err.code == 13900015 && err.data?.length !== undefined) {
    for (let i = 0; i < err.data.length; i++) {
      console.error(`Failed to move directory, with conflicting files: ${err.data[i].srcFile} ${err.data[i].destFile}`);
    }
  } else if (err) {
    console.error(`Failed to move directory. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in moving directory.`);
  }
});
```
