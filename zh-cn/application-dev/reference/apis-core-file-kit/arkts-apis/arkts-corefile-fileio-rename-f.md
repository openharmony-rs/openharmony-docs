# rename

<a id="rename"></a>
## rename

```TypeScript
declare function rename(oldPath: string, newPath: string): Promise<void>
```

重命名文件，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:rename](arkts-corefile-file-fs-rename-f.md#rename-1)

<!--Device-unnamed-declare function rename(oldPath: string, newPath: string): Promise<void>--><!--Device-unnamed-declare function rename(oldPath: string, newPath: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oldPath | string | 是 | 目标文件的当前应用沙箱路径。 |
| newPath | string | 是 | 目标文件的新应用沙箱路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |


<a id="rename-1"></a>
## rename

```TypeScript
declare function rename(oldPath: string, newPath: string, callback: AsyncCallback<void>): void
```

重命名文件，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:rename](arkts-corefile-file-fs-rename-f.md#rename-1)

<!--Device-unnamed-declare function rename(oldPath: string, newPath: string, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function rename(oldPath: string, newPath: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oldPath | string | 是 | 目标文件的当前应用沙箱路径。 |
| newPath | string | 是 | 目标文件的新应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步重命名文件之后的回调。 |

