# symlink

## symlink

```TypeScript
declare function symlink(target: string, srcPath: string): Promise<void>
```

基于文件路径创建符号链接，使用promise异步回调。 > **说明：** > > 从API version 11开始，不支持三方应用使用。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-unnamed-declare function symlink(target: string, srcPath: string): Promise<void>--><!--Device-unnamed-declare function symlink(target: string, srcPath: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | string | 是 | 要链接的目标文件的应用沙箱路径。 |
| srcPath | string | 是 | 符号链接文件的应用沙箱路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900018 | Not a directory |
| 13900030 | File name too long |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900005 | I/O error |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900015 | File exists |
| 13900008 | Bad file descriptor |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 13900011 | Out of memory |


## symlink

```TypeScript
declare function symlink(target: string, srcPath: string, callback: AsyncCallback<void>): void
```

基于文件路径创建符号链接，使用callback异步回调。 > **说明：** > > 从API version 11开始，不支持三方应用使用。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-unnamed-declare function symlink(target: string, srcPath: string, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function symlink(target: string, srcPath: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | string | 是 | 要链接的目标文件的应用沙箱路径。 |
| srcPath | string | 是 | 符号链接文件的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 异步创建符号链接信息之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900018 | Not a directory |
| 13900030 | File name too long |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900005 | I/O error |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900015 | File exists |
| 13900008 | Bad file descriptor |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 13900011 | Out of memory |

