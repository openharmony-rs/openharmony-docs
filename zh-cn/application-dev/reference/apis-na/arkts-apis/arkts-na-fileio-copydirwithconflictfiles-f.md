# copyDirWithConflictFiles

## copyDirWithConflictFiles

```TypeScript
function copyDirWithConflictFiles(src: string, dest: string, callback: AsyncCallback<void,
   Array<ConflictFiles>>): void
```

复制源目录及其内容至目标路径下，可设置冲突处理模式。使用callback异步回调。 如果目标目录下有与源目录名冲突的目录，且冲突目录下有同名文件，则抛出异常。 源目录下未冲突的文件全部移动至目标目录下，目标目录下冲突文件将继续保留，且冲突文件信息将在抛出异常的data属性中以Array&lt;ConflictFiles&gt;形式提供。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function copyDirWithConflictFiles(src: string, dest: string, callback: AsyncCallback<void,   Array<ConflictFiles>>): void--><!--Device-fileIo-function copyDirWithConflictFiles(src: string, dest: string, callback: AsyncCallback<void,   Array<ConflictFiles>>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void, Array&lt;[ConflictFiles](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-conflictfiles-i.md)&gt;&gt; | 是 | 回调函数。当复制目录成功，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900015 | File exists |


## copyDirWithConflictFiles

```TypeScript
function copyDirWithConflictFiles(src: string, dest: string, mode: int,
  callback: AsyncCallback<void, Array<ConflictFiles>>): void
```

复制源目录及其内容至目标路径下，可设置冲突处理模式。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function copyDirWithConflictFiles(src: string, dest: string, mode: int,  callback: AsyncCallback<void, Array<ConflictFiles>>): void--><!--Device-fileIo-function copyDirWithConflictFiles(src: string, dest: string, mode: int,  callback: AsyncCallback<void, Array<ConflictFiles>>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| mode | int | 是 | 复制模式。&lt;br/&gt; - mode为0，文件级别抛异常。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则抛出异常。源目录下未冲突的文件全部拷贝至目标目录下，目标目录下未冲突文 件将继续保留。&lt;br/&gt;- mode为1，文件级别强制覆盖。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则强制覆盖冲突目录下所有同名文件，未冲突文件将继续保留。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void, Array&lt;[ConflictFiles](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-conflictfiles-i.md)&gt;&gt; | 是 | 回调函数。当复制目录成功，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900015 | File exists |

