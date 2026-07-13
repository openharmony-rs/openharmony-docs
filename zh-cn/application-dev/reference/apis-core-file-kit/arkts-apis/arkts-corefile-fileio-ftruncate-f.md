# ftruncate

## ftruncate

```TypeScript
declare function ftruncate(fd: number, len?: number): Promise<void>
```

基于文件描述符截断文件，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:truncate](arkts-corefile-file-fs-truncate-f.md#truncate-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待截断文件的文件描述符。 |
| len | number | 否 | 文件截断后的长度，单位为Byte。默认为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |


## ftruncate

```TypeScript
declare function ftruncate(fd: number, callback: AsyncCallback<void>): void
```

基于文件描述符截断文件，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:truncate](arkts-corefile-file-fs-truncate-f.md#truncate-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待截断文件的文件描述符。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，本调用无返回值。 |


## ftruncate

```TypeScript
declare function ftruncate(fd: number, len: number, callback: AsyncCallback<void>): void
```

基于文件描述符截断文件，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:truncate](arkts-corefile-file-fs-truncate-f.md#truncate-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待截断文件的文件描述符。 |
| len | number | 是 | 文件截断后的长度，单位为Byte。默认为0。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，本调用无返回值。 |

