# copyFile

## copyFile

```TypeScript
function copyFile(src: string | int, dest: string | int, mode?: int): Promise<void>
```

复制文件。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function copyFile(src: string | int, dest: string | int, mode?: int): Promise<void>--><!--Device-fileIo-function copyFile(src: string | int, dest: string | int, mode?: int): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string \| int | 是 | 待复制文件的路径或待复制文件的文件描述符。 |
| dest | string \| int | 是 | 目标文件路径或目标文件的文件描述符。 |
| mode | int | 否 | mode提供覆盖文件的选项，当前仅支持0，且默认为0。&lt;br/&gt;0：完全覆盖目标文件，未覆盖部分将被裁剪掉。 |

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


## copyFile

```TypeScript
function copyFile(src: string | int, dest: string | int, callback: AsyncCallback<void>): void
```

复制文件，覆盖方式为完全覆盖目标文件，未覆盖部分将被裁剪。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function copyFile(src: string | int, dest: string | int, callback: AsyncCallback<void>): void--><!--Device-fileIo-function copyFile(src: string | int, dest: string | int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string \| int | 是 | 待复制文件的路径或待复制文件的文件描述符。 |
| dest | string \| int | 是 | 目标文件路径或目标文件的文件描述符。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当复制文件成功，err为undefined，否则为错误对象。 |

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


## copyFile

```TypeScript
function copyFile(
  src: string | int,
  dest: string | int,
  mode: int,
  callback: AsyncCallback<void>
): void
```

复制文件，可设置覆盖文件的方式。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function copyFile(  src: string | int,  dest: string | int,  mode: int,  callback: AsyncCallback<void>): void--><!--Device-fileIo-function copyFile(  src: string | int,  dest: string | int,  mode: int,  callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string \| int | 是 | 待复制文件的路径或待复制文件的文件描述符。 |
| dest | string \| int | 是 | 目标文件路径或目标文件的文件描述符。 |
| mode | int | 是 | mode提供覆盖文件的选项，当前仅支持0，且默认为0。&lt;br/&gt;0：完全覆盖目标文件，未覆盖部分将被裁剪掉。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当复制文件成功，err为undefined，否则为错误对象。 |

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

