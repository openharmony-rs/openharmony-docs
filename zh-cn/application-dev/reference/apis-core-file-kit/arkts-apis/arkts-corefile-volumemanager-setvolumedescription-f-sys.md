# setVolumeDescription（系统接口）

## setVolumeDescription

```TypeScript
function setVolumeDescription(uuid: string, description: string, callback: AsyncCallback<void>): void
```

修改指定卷设备描述，使用callback异步回调。当前仅支持修改ntfs和exfat两种文件系统类型的设备描述， 只有处于卸载状态的卷设备可以修改设备描述。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MOUNT_UNMOUNT_MANAGER

<!--Device-volumeManager-function setVolumeDescription(uuid: string, description: string, callback: AsyncCallback<void>): void--><!--Device-volumeManager-function setVolumeDescription(uuid: string, description: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | string | 是 | 卷设备uuid。 |
| description | string | 是 | 卷设备描述。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 设置卷描述之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes: 1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types. |
| 13600008 | No such object. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13600005 | Incorrect volume state. |
| 13600002 | Not supported filesystem. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |


## setVolumeDescription

```TypeScript
function setVolumeDescription(uuid: string, description: string): Promise<void>
```

修改指定卷设备描述，使用Promise异步回调。当前仅支持修改ntfs和exfat两种文件系统类型的设备描述， 只有处于卸载状态的卷设备可以修改设备描述。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MOUNT_UNMOUNT_MANAGER

<!--Device-volumeManager-function setVolumeDescription(uuid: string, description: string): Promise<void>--><!--Device-volumeManager-function setVolumeDescription(uuid: string, description: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | string | 是 | 卷设备uuid。 |
| description | string | 是 | 卷设备描述。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes: 1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types. |
| 13600008 | No such object. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13600005 | Incorrect volume state. |
| 13600002 | Not supported filesystem. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

