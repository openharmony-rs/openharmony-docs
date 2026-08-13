# copyDir

## copyDir

```TypeScript
function copyDir(src: string, dest: string, mode?: int): Promise<void>
```

复制源目录及其内容至目标路径下，可设置冲突处理模式。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function copyDir(src: string, dest: string, mode?: int): Promise<void>--><!--Device-fileIo-function copyDir(src: string, dest: string, mode?: int): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| mode | int | 否 | 复制模式，默认值为0。&lt;br/&gt; - mode为0，文件级别抛异常。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则抛出异常。源目录下未冲突的文件全部拷贝至目标目录下，目 标目录下未冲突文件将继续保留，且冲突文件信息将在抛出异常的data属性中以Array&lt;[ConflictFiles](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-conflictfiles-i.md#ConflictFiles)&gt;形式提供。&lt;br/&gt; - mode为1，文件级别强制覆盖。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则强制覆盖冲突目录下所有同名文件，未冲突文件将继续保留。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900030 | File name too long |
| 13900031 | Function not implemented |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900038 | Value too large for defined data type |
| 13900033 | Too many symbolic links encountered |
| 13900002 | No such file or directory |
| 13900034 | Operation would block |
| 13900012 | Permission denied |
| 13900044 | Network is unreachable |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900042 | Unknown error |
| 13900011 | Out of memory |


## copyDir

```TypeScript
function copyDir(src: string, dest: string, callback: AsyncCallback<void>): void
```

复制源目录及其内容至目标路径下。使用callback异步回调。 如果目标目录下有与源目录名冲突的目录，且冲突目录下有同名文件，则抛出异常。源目录下未冲突的文件全部拷贝至目标目录下，目标目录下未冲突文件将继续保留。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function copyDir(src: string, dest: string, callback: AsyncCallback<void>): void--><!--Device-fileIo-function copyDir(src: string, dest: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当复制目录成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900030 | File name too long |
| 13900031 | Function not implemented |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900038 | Value too large for defined data type |
| 13900033 | Too many symbolic links encountered |
| 13900002 | No such file or directory |
| 13900034 | Operation would block |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900042 | Unknown error |
| 13900011 | Out of memory |


## copyDir

```TypeScript
function copyDir(src: string, dest: string, mode: int, callback: AsyncCallback<void>): void
```

复制源目录及其内容至目标路径下，可设置冲突处理模式。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function copyDir(src: string, dest: string, mode: int, callback: AsyncCallback<void>): void--><!--Device-fileIo-function copyDir(src: string, dest: string, mode: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| mode | int | 是 | 复制模式。&lt;br/&gt; - mode为0，文件级别抛异常。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则抛出异常。源目录下未冲突的文件全部拷贝至目标目录下，目标目录下未冲突文 件将继续保留。&lt;br/&gt;- mode为1，文件级别强制覆盖。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则强制覆盖冲突目录下所有同名文件，未冲突文件将继续保留。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当复制目录成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900030 | File name too long |
| 13900031 | Function not implemented |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900038 | Value too large for defined data type |
| 13900033 | Too many symbolic links encountered |
| 13900002 | No such file or directory |
| 13900034 | Operation would block |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900042 | Unknown error |
| 13900011 | Out of memory |

