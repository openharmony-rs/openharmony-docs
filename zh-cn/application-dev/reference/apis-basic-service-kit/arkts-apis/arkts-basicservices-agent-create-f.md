# create

## 导入模块

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## create

```TypeScript
function create(context: BaseContext, config: Config, callback: AsyncCallback<Task>): void
```

创建需要上传或下载的任务，并将其排入队列。支持HTTP/HTTPS协议，使用callback异步回调。
> **说明：**  
>  
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 10

**需要权限：** ohos.permission.INTERNET

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-agent-function create(context: BaseContext, config: Config, callback: AsyncCallback<Task>): void--><!--Device-agent-function create(context: BaseContext, config: Config, callback: AsyncCallback<Task>): void-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 基于应用程序的上下文。 |
| config | [Config](arkts-basicservices-agent-config-i.md) | 是 | 上传/下载任务的配置信息。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Task&gt; | 是 | 回调函数。当创建上传或下载任务成功，err为undefined，data为获取到的Task对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type.<br> 3. Parameter verification failed. |
| [13400001](../../apis-basic-services-kit/errorcode-request.md#13400001-文件操作异常) | Invalid file or file system error. |
| [13400003](../../apis-basic-services-kit/errorcode-request.md#13400003-服务异常) | Task service ability error. |
| [21900004](../../apis-basic-services-kit/errorcode-request.md#21900004-应用任务队列已满) | The application task queue is full. |
| [21900005](../../apis-basic-services-kit/errorcode-request.md#21900005-任务模式错误) | Operation with wrong task mode. |


## create

```TypeScript
function create(context: BaseContext, config: Config): Promise<Task>
```

创建需要上传或下载的任务，并将其排入队列。支持HTTP/HTTPS协议，使用Promise异步回调。
> **说明：**  
>  
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 10

**需要权限：** ohos.permission.INTERNET

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-agent-function create(context: BaseContext, config: Config): Promise<Task>--><!--Device-agent-function create(context: BaseContext, config: Config): Promise<Task>-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 基于应用程序的上下文。 |
| config | [Config](arkts-basicservices-agent-config-i.md) | 是 | 上传/下载任务的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Task&gt; | Promise对象。返回任务配置信息的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type.<br> 3. Parameter verification failed. |
| [13400001](../../apis-basic-services-kit/errorcode-request.md#13400001-文件操作异常) | Invalid file or file system error. |
| [13400003](../../apis-basic-services-kit/errorcode-request.md#13400003-服务异常) | Task service ability error. |
| [21900004](../../apis-basic-services-kit/errorcode-request.md#21900004-应用任务队列已满) | The application task queue is full. |
| [21900005](../../apis-basic-services-kit/errorcode-request.md#21900005-任务模式错误) | Operation with wrong task mode. |

