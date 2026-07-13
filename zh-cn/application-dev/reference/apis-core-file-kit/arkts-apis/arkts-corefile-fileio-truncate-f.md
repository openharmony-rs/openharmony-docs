# truncate

## truncate

```TypeScript
declare function truncate(path: string, len?: number): Promise<void>
```

基于文件路径截断文件，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:truncate](arkts-corefile-file-fs-truncate-f.md#truncate-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待截断文件的应用沙箱路径。 |
| len | number | 否 | 文件截断后的长度，单位为Byte。默认为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |


## truncate

```TypeScript
declare function truncate(path: string, callback: AsyncCallback<void>): void
```

基于文件路径截断文件，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:truncate](arkts-corefile-file-fs-truncate-f.md#truncate-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待截断文件的应用沙箱路径。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，本调用无返回值。 |


## truncate

```TypeScript
declare function truncate(path: string, len: number, callback: AsyncCallback<void>): void
```

基于文件路径截断文件，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:truncate](arkts-corefile-file-fs-truncate-f.md#truncate-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待截断文件的应用沙箱路径。 |
| len | number | 是 | 文件截断后的长度，单位为Byte。默认为0。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，本调用无返回值。 |

