# lstat

## 导入模块

```TypeScript
```

## lstat

```TypeScript
function lstat(path: string): Promise<Stat>
```

获取符号链接文件信息，返回符号链接本身的属性而非目标文件的属性。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function lstat(path: string): Promise<Stat>--><!--Device-fileIo-function lstat(path: string): Promise<Stat>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件的应用沙箱路径path或URI。 <br>**说明：**从API version 22开始，支持传入URI。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Stat](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-stat-i.md)&gt; | Promise对象，返回Stat对象，表示文件的具体信息，详情见Stat。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900038 | Value too large for defined data type |
| 13900033 | Too many symbolic links encountered |
| 13900002 | No such file or directory |
| 13900018 | Not a directory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900030 | File name too long |
| 13900008 | Bad file descriptor |
| 13900042 | Unknown error |
| 13900011 | Out of memory |


## lstat

```TypeScript
function lstat(path: string, callback: AsyncCallback<Stat>): void
```

获取符号链接文件信息，返回符号链接本身的属性而非目标文件的属性。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function lstat(path: string, callback: AsyncCallback<Stat>): void--><!--Device-fileIo-function lstat(path: string, callback: AsyncCallback<Stat>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件的应用沙箱路径path或URI。 <br>**说明：**从API version 22开始，支持传入URI。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[Stat](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-stat-i.md)&gt; | 是 | 回调函数，返回Stat对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900038 | Value too large for defined data type |
| 13900033 | Too many symbolic links encountered |
| 13900002 | No such file or directory |
| 13900018 | Not a directory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900030 | File name too long |
| 13900008 | Bad file descriptor |
| 13900042 | Unknown error |
| 13900011 | Out of memory |

