# query（系统接口）

## query

```TypeScript
function query(id: string, callback: AsyncCallback<TaskInfo>): void
```

Queries specified task details.
Creates a group based on GroupConfig

**起始版本：** 10

**需要权限：** ohos.permission.DOWNLOAD_SESSION_MANAGER or ohos.permission.UPLOAD_SESSION_MANAGER

**系统能力：** SystemCapability.Request.FileTransferAgent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | the task id. |
| callback | AsyncCallback&lt;TaskInfo&gt; | 是 | callback function with a `TaskInfo` argument for informations of the |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission) | permission verification failed, application which is not a system application<br/>uses system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Missing mandatory parameters.<br/><br/>2. Incorrect parameter type. |
| [13400003](../../errorcode-universal.md#13400003-Task) | Task service ability error. |
| [21900006](../../errorcode-universal.md#21900006-Task) | Task removed or not found. |


## query

```TypeScript
function query(id: string): Promise<TaskInfo>
```

Queries specified task details.

**起始版本：** 10

**需要权限：** ohos.permission.DOWNLOAD_SESSION_MANAGER or ohos.permission.UPLOAD_SESSION_MANAGER

**系统能力：** SystemCapability.Request.FileTransferAgent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | the task id. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;TaskInfo&gt; | the promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission) | permission verification failed, application which is not a system application<br/>uses system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Missing mandatory parameters.<br/><br/>2. Incorrect parameter type. |
| [13400003](../../errorcode-universal.md#13400003-Task) | Task service ability error. |
| [21900006](../../errorcode-universal.md#21900006-Task) | Task removed or not found. |

