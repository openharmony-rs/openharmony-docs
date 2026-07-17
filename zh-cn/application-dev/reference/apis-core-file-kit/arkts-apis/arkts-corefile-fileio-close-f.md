# close

## close

```TypeScript
declare function close(fd: number): Promise<void>
```

关闭文件，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:close](arkts-corefile-file-fs-close-f.md#close-1)

<!--Device-unnamed-declare function close(fd: number): Promise<void>--><!--Device-unnamed-declare function close(fd: number): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待关闭文件的文件描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回值。 |


## close

```TypeScript
declare function close(fd: number, callback: AsyncCallback<void>): void
```

关闭文件，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:close](arkts-corefile-file-fs-close-f.md#close-1)

<!--Device-unnamed-declare function close(fd: number, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function close(fd: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待关闭文件的文件描述符。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 异步关闭文件之后的回调。 |

