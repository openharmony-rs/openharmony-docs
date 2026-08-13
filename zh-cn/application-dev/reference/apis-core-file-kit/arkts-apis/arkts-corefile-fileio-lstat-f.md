# lstat

## lstat

```TypeScript
declare function lstat(path: string): Promise<Stat>
```

获取链接信息，使用Promise异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [lstat](arkts-corefile-file-fs-lstat-f.md#lstat)

<!--Device-unnamed-declare function lstat(path: string): Promise<Stat>--><!--Device-unnamed-declare function lstat(path: string): Promise<Stat>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目标文件的应用沙箱路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Stat](arkts-corefile-fileio-stat-depr-i.md)&gt; | promise对象，返回文件对象，表示文件的具体信息，详情见stat。 |


## lstat

```TypeScript
declare function lstat(path: string, callback: AsyncCallback<Stat>): void
```

获取链接信息，使用callback异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [lstat](arkts-corefile-file-fs-lstat-f.md#lstat)

<!--Device-unnamed-declare function lstat(path: string, callback: AsyncCallback<Stat>): void--><!--Device-unnamed-declare function lstat(path: string, callback: AsyncCallback<Stat>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目标文件的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[Stat](arkts-corefile-fileio-stat-depr-i.md)&gt; | 是 | 回调函数，返回文件的具体信息。 |

