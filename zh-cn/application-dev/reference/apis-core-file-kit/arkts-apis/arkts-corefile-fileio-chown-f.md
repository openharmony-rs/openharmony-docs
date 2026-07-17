# chown

## chown

```TypeScript
declare function chown(path: string, uid: number, gid: number): Promise<void>
```

基于文件路径改变文件所有者，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

<!--Device-unnamed-declare function chown(path: string, uid: number, gid: number): Promise<void>--><!--Device-unnamed-declare function chown(path: string, uid: number, gid: number): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待改变文件的应用沙箱路径。 |
| uid | number | 是 | 新的UID（UserID）。 |
| gid | number | 是 | 新的GID（GroupID）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回值。 |


## chown

```TypeScript
declare function chown(path: string, uid: number, gid: number, callback: AsyncCallback<void>): void
```

基于文件路径改变文件所有者，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

<!--Device-unnamed-declare function chown(path: string, uid: number, gid: number, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function chown(path: string, uid: number, gid: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待改变文件的应用沙箱路径。 |
| uid | number | 是 | 新的UID。 |
| gid | number | 是 | 新的GID。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 异步改变文件所有者之后的回调。 |

