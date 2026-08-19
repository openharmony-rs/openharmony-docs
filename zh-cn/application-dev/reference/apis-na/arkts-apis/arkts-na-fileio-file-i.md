# File

由open接口打开的File对象，持有文件描述符fd，提供文件锁和获取父目录等能力。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-interface File--><!--Device-fileIo-interface File-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
```

## getParent

```TypeScript
getParent(): string
```

获取File对象对应文件的父目录路径。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-File-getParent(): string--><!--Device-File-getParent(): string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回父目录路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900005 | I/O error |
| 14300002 | Invalid URI |
| 13900042 | Unknown error |

## lock

```TypeScript
lock(exclusive?: boolean): Promise<void>
```

对文件阻塞式施加共享锁或独占锁。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-File-lock(exclusive?: boolean): Promise<void>--><!--Device-File-lock(exclusive?: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| exclusive | boolean | 否 | 是否施加独占锁，默认false。true：施加独占锁；false：不施加独占锁。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900020 | Invalid argument |
| 13900034 | Operation would block |
| 13900008 | Bad file descriptor |
| 13900042 | Unknown error |
| 13900043 | No record locks available |

## lock

```TypeScript
lock(callback: AsyncCallback<void>): void
```

对文件阻塞式施加共享锁。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-File-lock(callback: AsyncCallback<void>): void--><!--Device-File-lock(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当文件上锁成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900020 | Invalid argument |
| 13900034 | Operation would block |
| 13900008 | Bad file descriptor |
| 13900042 | Unknown error |
| 13900043 | No record locks available |

## lock

```TypeScript
lock(exclusive: boolean, callback: AsyncCallback<void>): void
```

对文件阻塞式施加共享锁或独占锁。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-File-lock(exclusive: boolean, callback: AsyncCallback<void>): void--><!--Device-File-lock(exclusive: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| exclusive | boolean | 是 | 是否施加独占锁。true：施加独占锁；false：不施加独占锁。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当文件上锁成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900020 | Invalid argument |
| 13900034 | Operation would block |
| 13900008 | Bad file descriptor |
| 13900042 | Unknown error |
| 13900043 | No record locks available |

## tryLock

```TypeScript
tryLock(exclusive?: boolean): void
```

文件非阻塞式施加共享锁或独占锁。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-File-tryLock(exclusive?: boolean): void--><!--Device-File-tryLock(exclusive?: boolean): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| exclusive | boolean | 否 | 是否施加独占锁，默认false。true：施加独占锁；false：不施加独占锁。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900020 | Invalid argument |
| 13900034 | Operation would block |
| 13900008 | Bad file descriptor |
| 13900042 | Unknown error |
| 13900043 | No record locks available |

## unlock

```TypeScript
unlock(): void
```

以同步方式解锁文件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-File-unlock(): void--><!--Device-File-unlock(): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900020 | Invalid argument |
| 13900034 | Operation would block |
| 13900008 | Bad file descriptor |
| 13900042 | Unknown error |
| 13900043 | No record locks available |

## fd

```TypeScript
readonly fd: int
```

已打开的文件描述符fd。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-File-readonly fd: int--><!--Device-File-readonly fd: int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## name

```TypeScript
readonly name: string
```

文件名。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-File-readonly name: string--><!--Device-File-readonly name: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## path

```TypeScript
readonly path: string
```

文件路径。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-File-readonly path: string--><!--Device-File-readonly path: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

