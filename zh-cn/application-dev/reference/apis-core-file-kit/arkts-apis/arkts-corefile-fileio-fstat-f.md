# fstat

## fstat

```TypeScript
declare function fstat(fd: number): Promise<Stat>
```

基于文件描述符获取文件状态信息，使用Promise异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [stat](arkts-corefile-file-fs-stat-f.md#stat)

<!--Device-unnamed-declare function fstat(fd: number): Promise<Stat>--><!--Device-unnamed-declare function fstat(fd: number): Promise<Stat>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待获取文件状态的文件描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Stat](arkts-corefile-fileio-stat-depr-i.md)&gt; | Promise对象。返回表示文件状态的具体信息。 |


## fstat

```TypeScript
declare function fstat(fd: number, callback: AsyncCallback<Stat>): void
```

基于文件描述符获取文件状态信息，使用callback异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [stat](arkts-corefile-file-fs-stat-f.md#stat)

<!--Device-unnamed-declare function fstat(fd: number, callback: AsyncCallback<Stat>): void--><!--Device-unnamed-declare function fstat(fd: number, callback: AsyncCallback<Stat>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待获取文件状态的文件描述符。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[Stat](arkts-corefile-fileio-stat-depr-i.md)&gt; | 是 | 异步获取文件状态信息之后的回调。 |

