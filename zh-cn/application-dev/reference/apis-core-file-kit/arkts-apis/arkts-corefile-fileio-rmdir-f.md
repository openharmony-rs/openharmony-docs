# rmdir

## rmdir

```TypeScript
declare function rmdir(path: string): Promise<void>
```

删除目录，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:rmdir](arkts-corefile-fileio-rmdir-f.md#rmdir)

<!--Device-unnamed-declare function rmdir(path: string): Promise<void>--><!--Device-unnamed-declare function rmdir(path: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待删除目录的应用沙箱路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |


## rmdir

```TypeScript
declare function rmdir(path: string, callback: AsyncCallback<void>): void
```

删除目录，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:rmdir](arkts-corefile-fileio-rmdir-f.md#rmdir)

<!--Device-unnamed-declare function rmdir(path: string, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function rmdir(path: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待删除目录的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步删除目录之后的回调。 |

