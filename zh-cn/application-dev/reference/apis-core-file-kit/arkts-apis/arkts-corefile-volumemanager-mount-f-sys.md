# mount（系统接口）

## mount

```TypeScript
function mount(volumeId: string, callback: AsyncCallback<void>): void
```

挂载指定卷设备，使用callback异步回调。当前仅支持vfat、exfat以及ntfs三种文件系统的卷设备挂载。

**起始版本：** 9

**需要权限：** ohos.permission.MOUNT_UNMOUNT_MANAGER

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeId | string | 是 | 卷设备id。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 挂载指定卷设备之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:<br/>1.Mandatory parameters are left unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |
| [13600002](../../errorcode-universal.md#13600002-Not) | Not supported filesystem. |
| [13600003](../../errorcode-universal.md#13600003-Failed) | Failed to mount. |
| [13600005](../../errorcode-universal.md#13600005-Incorrect) | Incorrect volume state. |
| [13600008](../../errorcode-universal.md#13600008-No) | No such object. |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error. |


## mount

```TypeScript
function mount(volumeId: string): Promise<void>
```

挂载指定卷设备，使用Promise异步回调。当前仅支持vfat、exfat以及ntfs三种文件系统的卷设备挂载。

**起始版本：** 9

**需要权限：** ohos.permission.MOUNT_UNMOUNT_MANAGER

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeId | string | 是 | 卷设备id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:<br/>1.Mandatory parameters are left unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |
| [13600002](../../errorcode-universal.md#13600002-Not) | Not supported filesystem. |
| [13600003](../../errorcode-universal.md#13600003-Failed) | Failed to mount. |
| [13600005](../../errorcode-universal.md#13600005-Incorrect) | Incorrect volume state. |
| [13600008](../../errorcode-universal.md#13600008-No) | No such object. |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error. |

