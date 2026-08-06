# ftruncate

## ftruncate

```TypeScript
declare function ftruncate(fd: number, len?: number): Promise<void>
```

基于文件描述符截断文件，使用Promise异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [@ohos.file.fs:truncate](arkts-corefile-fileio-truncate-f.md#truncate)

<!--Device-unnamed-declare function ftruncate(fd: number, len?: number): Promise<void>--><!--Device-unnamed-declare function ftruncate(fd: number, len?: number): Promise<void>-End-->

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [@ohos.file.fs:truncate](arkts-corefile-fileio-truncate-f.md#truncate)

<!--Device-unnamed-declare function ftruncate(fd: number, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function ftruncate(fd: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待截断文件的文件描述符。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数，本调用无返回值。 |


## ftruncate

```TypeScript
declare function ftruncate(fd: number, len: number, callback: AsyncCallback<void>): void
```

基于文件描述符截断文件，使用callback异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [@ohos.file.fs:truncate](arkts-corefile-fileio-truncate-f.md#truncate)

<!--Device-unnamed-declare function ftruncate(fd: number, len: number, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function ftruncate(fd: number, len: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待截断文件的文件描述符。 |
| len | number | 是 | 文件截断后的长度，单位为Byte。默认为0。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数，本调用无返回值。 |

