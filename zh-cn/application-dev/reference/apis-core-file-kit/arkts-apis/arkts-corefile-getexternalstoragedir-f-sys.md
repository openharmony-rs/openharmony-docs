# getExternalStorageDir（系统接口）

## getExternalStorageDir

```TypeScript
function getExternalStorageDir(): string
```

获取外卡根目录的沙箱路径，该接口仅对具有该系统能力的设备开放。

**起始版本：** 11

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**系统能力：** SystemCapability.FileManagement.File.Environment.FolderObtain

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回外卡根目录的沙箱路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application usessystem API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| 13900042 | Unknown error. |

