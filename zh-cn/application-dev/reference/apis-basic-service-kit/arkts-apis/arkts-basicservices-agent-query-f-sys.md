# query（系统接口）

## 导入模块

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## query

```TypeScript
function query(id: string, callback: AsyncCallback<TaskInfo>): void
```

Queries specified task details.Creates a group based on GroupConfig

**起始版本：** 10

**需要权限：** ohos.permission.DOWNLOAD_SESSION_MANAGER or ohos.permission.UPLOAD_SESSION_MANAGER

<!--Device-agent-function query(id: string, callback: AsyncCallback<TaskInfo>): void--><!--Device-agent-function query(id: string, callback: AsyncCallback<TaskInfo>): void-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | the task id. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<TaskInfo> | 是 | callback function with a `TaskInfo` argument for informations of the |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type. |
| [13400003](../../apis-basic-services-kit/errorcode-request.md#13400003-服务异常) | Task service ability error. |
| [21900006](../../apis-basic-services-kit/errorcode-request.md#21900006-操作不存在的任务错误) | Task removed or not found. |


## query

```TypeScript
function query(id: string): Promise<TaskInfo>
```

Queries specified task details.

**起始版本：** 10

**需要权限：** ohos.permission.DOWNLOAD_SESSION_MANAGER or ohos.permission.UPLOAD_SESSION_MANAGER

<!--Device-agent-function query(id: string): Promise<TaskInfo>--><!--Device-agent-function query(id: string): Promise<TaskInfo>-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | the task id. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<TaskInfo> | the promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type. |
| [13400003](../../apis-basic-services-kit/errorcode-request.md#13400003-服务异常) | Task service ability error. |
| [21900006](../../apis-basic-services-kit/errorcode-request.md#21900006-操作不存在的任务错误) | Task removed or not found. |

