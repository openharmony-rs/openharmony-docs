# access

<a id="access"></a>
## access

```TypeScript
declare function access(path: string, mode?: number): Promise<void>
```

检查当前进程是否可访问某文件，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:access](arkts-corefile-file-fs-access-f.md#access-1)

<!--Device-unnamed-declare function access(path: string, mode?: number): Promise<void>--><!--Device-unnamed-declare function access(path: string, mode?: number): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待访问文件的应用沙箱路径。 |
| mode | number | 否 | 访问文件时的选项，可给定如下选项，以按位或的方式使用多个选项，默认给定0。<br/>确认当前进程是否具有对应权限：<br/>-?0：确认文件是否存在。<br/>-?1：确认当前进程是否具有可执行权限。<br/>-?2：确认当前进程是否具有写权限。<br/>-?4：确认当前进程是否具有读权限。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |


<a id="access-1"></a>
## access

```TypeScript
declare function access(path: string, callback: AsyncCallback<void>): void
```

检查当前进程是否可访问某文件，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:access](arkts-corefile-file-fs-access-f.md#access-1)

<!--Device-unnamed-declare function access(path: string, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function access(path: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待访问文件的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步检查当前进程是否可访问某文件之后的回调。 |


<a id="access-2"></a>
## access

```TypeScript
declare function access(path: string, mode: number, callback: AsyncCallback<void>): void
```

检查当前进程是否可访问某文件，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:access](arkts-corefile-file-fs-access-f.md#access-1)

<!--Device-unnamed-declare function access(path: string, mode: number, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function access(path: string, mode: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待访问文件的应用沙箱路径。 |
| mode | number | 是 | 访问文件时的选项，可给定如下选项，以按位或的方式使用多个选项，默认给定0。<br/>确认当前进程是否具有对应权限：<br/>-?0：确认文件是否存在。<br/>-?1：确认当前进程是否具有可执行权限。<br/>-?2：确认当前进程是否具有写权限。<br/>-?4：确认当前进程是否具有读权限。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步检查当前进程是否可访问某文件之后的回调。 |

