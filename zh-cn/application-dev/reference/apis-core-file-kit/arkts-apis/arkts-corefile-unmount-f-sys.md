# unmount（系统接口）

## unmount

```TypeScript
function unmount(volumeId: string, callback: AsyncCallback<void>): void
```

卸载指定卷设备，使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MOUNT_UNMOUNT_MANAGER

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeId | string | 是 | 卷设备id。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 卸载指定卷设备之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600004 | Failed to unmount. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |


## unmount

```TypeScript
function unmount(volumeId: string): Promise<void>
```

卸载指定卷设备，使用Promise异步回调。

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
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600004 | Failed to unmount. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

