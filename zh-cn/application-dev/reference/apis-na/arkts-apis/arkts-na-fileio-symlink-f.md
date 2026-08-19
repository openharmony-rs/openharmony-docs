# symlink

## 导入模块

```TypeScript
```

## symlink

```TypeScript
function symlink(target: string, srcPath: string): Promise<void>
```

基于文件路径创建符号链接。使用Promise异步回调。 > **说明：** > > 从API version 11开始，不支持三方应用使用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function symlink(target: string, srcPath: string): Promise<void>--><!--Device-fileIo-function symlink(target: string, srcPath: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | string | 是 | 要链接的目标文件的应用沙箱路径。 |
| srcPath | string | 是 | 符号链接文件的应用沙箱路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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
function symlink(target: string, srcPath: string, callback: AsyncCallback<void>): void
```

基于文件路径创建符号链接。使用callback异步回调。 > **说明：** > > 从API version 11开始，不支持三方应用使用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function symlink(target: string, srcPath: string, callback: AsyncCallback<void>): void--><!--Device-fileIo-function symlink(target: string, srcPath: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | string | 是 | 要链接的目标文件的应用沙箱路径。 |
| srcPath | string | 是 | 符号链接文件的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当创建符号链接成功，err为undefined，否则为错误对象。 |

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

