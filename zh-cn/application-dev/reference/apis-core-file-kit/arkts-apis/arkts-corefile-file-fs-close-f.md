# close

## close

```TypeScript
declare function close(file: number | File): Promise<void>
```

关闭文件或目录，使用promise异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function close(file: number | File): Promise<void>--><!--Device-unnamed-declare function close(file: number | File): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | number \| [File](arkts-corefile-file-fs-file-i.md) | 是 | 已打开的File对象或已打开的文件描述符fd。关闭后file对象或文件描述符fd不再具备实际意义，不可再用于进行读写等操作。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |


## close

```TypeScript
declare function close(file: number | File, callback: AsyncCallback<void>): void
```

关闭文件或目录，使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function close(file: number | File, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function close(file: number | File, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | number \| [File](arkts-corefile-file-fs-file-i.md) | 是 | 已打开的File对象或已打开的文件描述符fd。关闭后file对象或文件描述符fd不再具备实际意义，不可再用于进行读写等操作。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 异步关闭文件或目录之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

