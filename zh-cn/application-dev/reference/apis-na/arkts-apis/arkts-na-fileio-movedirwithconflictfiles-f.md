# moveDirWithConflictFiles

## 导入模块

```TypeScript
```

## moveDirWithConflictFiles

```TypeScript
function moveDirWithConflictFiles(src: string, dest: string, callback:  AsyncCallback<void,
  Array<ConflictFiles>>): void
```

Moves the source directory to the destination directory. This API uses an asynchronous callback to return the result.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function moveDirWithConflictFiles(src: string, dest: string, callback:  AsyncCallback<void,  Array<ConflictFiles>>): void--><!--Device-fileIo-function moveDirWithConflictFiles(src: string, dest: string, callback:  AsyncCallback<void,  Array<ConflictFiles>>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | Application sandbox path of the source directory. |
| dest | string | 是 | Application sandbox path of the destination directory. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void, Array&lt;[ConflictFiles](arkts-na-file-fs-conflictfiles-i.md)&gt;&gt; | 是 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900015 | File exists |


## moveDirWithConflictFiles

```TypeScript
function moveDirWithConflictFiles(src: string, dest: string, mode: int,
  callback: AsyncCallback<void, Array<ConflictFiles>>): void
```

移动源目录及其内容至目标路径下，支持设置冲突处理模式。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function moveDirWithConflictFiles(src: string, dest: string, mode: int,  callback: AsyncCallback<void, Array<ConflictFiles>>): void--><!--Device-fileIo-function moveDirWithConflictFiles(src: string, dest: string, mode: int,  callback: AsyncCallback<void, Array<ConflictFiles>>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| mode | int | 是 | 移动模式。<br/>- mode为0，目录级别抛异常。若目标目录下存在与源目录名冲突的目录，则抛出异常。<br/> - mode为1，文件级别抛异常。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则抛出异常。源目录下未冲突的文件全部移动至目标目录下，目标目录下未冲突文件将继续保留。<br/> - mode为2，文件级别强制覆盖。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则强制覆盖冲突目录下所有同名文件，未冲突文件将继续保留。<br/> - mode为3，目录级别强制覆盖。移动源目录至目标目录下，目标目录下移动的目录内容与源目录完全一致。若目标目录下存在与源目录名冲突的目录，该目录下所有原始文件将被删除。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void, Array&lt;[ConflictFiles](arkts-na-file-fs-conflictfiles-i.md)&gt;&gt; | 是 | 异步移动目录之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900015 | File exists |

