# readLines

## readLines

```TypeScript
declare function readLines(filePath: string, options?: Options): Promise<ReaderIterator>
```

逐行读取文件文本内容，使用promise异步回调。只支持读取utf-8格式文件。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-unnamed-declare function readLines(filePath: string, options?: Options): Promise<ReaderIterator>--><!--Device-unnamed-declare function readLines(filePath: string, options?: Options): Promise<ReaderIterator>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 文件的应用沙箱路径。 |
| options | [Options](arkts-corefile-file-fs-options-i.md) | 否 | 可选项。支持以下选项：&lt;br/&gt;- encoding，string类型，当数据是string类型时有效，表示数据的编码方式，默认'utf-8'，仅支持'utf-8' 。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ReaderIterator](arkts-corefile-file-fs-readeriterator-i.md)&gt; | Promise对象。返回文件读取迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900019 | Is a directory |
| 13900030 | File name too long |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900033 | Too many symbolic links encountered |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900044 | Network is unreachable<br>**适用版本：** 12+ |
| 13900015 | File exists |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |


## readLines

```TypeScript
declare function readLines(filePath: string, callback: AsyncCallback<ReaderIterator>): void
```

逐行读取文件文本内容，使用callback异步回调，只支持读取utf-8格式文件。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-unnamed-declare function readLines(filePath: string, callback: AsyncCallback<ReaderIterator>): void--><!--Device-unnamed-declare function readLines(filePath: string, callback: AsyncCallback<ReaderIterator>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 文件的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[ReaderIterator](arkts-corefile-file-fs-readeriterator-i.md)&gt; | 是 | 逐行读取文件文本内容回调。返回文件读取迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900033 | Too many symbolic links encountered |
| 13900002 | No such file or directory |
| 13900019 | Is a directory |
| 13900012 | Permission denied |
| 13900030 | File name too long |
| 13900015 | File exists |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 13900027 | Read-only file system |


## readLines

```TypeScript
declare function readLines(filePath: string, options: Options, callback: AsyncCallback<ReaderIterator>): void
```

逐行读取文件文本内容，使用callback异步回调，只支持读取utf-8格式文件。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-unnamed-declare function readLines(filePath: string, options: Options, callback: AsyncCallback<ReaderIterator>): void--><!--Device-unnamed-declare function readLines(filePath: string, options: Options, callback: AsyncCallback<ReaderIterator>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 文件的应用沙箱路径。 |
| options | [Options](arkts-corefile-file-fs-options-i.md) | 是 | 可选项。支持以下选项：&lt;br/&gt;- encoding，string类型，当数据是string类型时有效，表示数据的编码方式，默认'utf-8'，仅支持'utf-8'。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[ReaderIterator](arkts-corefile-file-fs-readeriterator-i.md)&gt; | 是 | 逐行读取文件文本内容回调。返回文件读取迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900033 | Too many symbolic links encountered |
| 13900002 | No such file or directory |
| 13900019 | Is a directory |
| 13900012 | Permission denied |
| 13900030 | File name too long |
| 13900015 | File exists |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 13900027 | Read-only file system |

