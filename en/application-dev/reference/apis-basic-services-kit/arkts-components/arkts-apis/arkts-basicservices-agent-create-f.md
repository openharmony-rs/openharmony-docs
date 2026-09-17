# create

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## create

```TypeScript
function create(context: BaseContext, config: Config, callback: AsyncCallback<Task>): void
```

Creates an upload or download task and adds it to the queue. This API uses an asynchronous callback to return the result. HTTP/HTTPS is supported.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 10

**Required permissions:** ohos.permission.INTERNET

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | Yes | Application-based context. |
| config | [Config](arkts-basicservices-agent-config-i.md) | Yes | Task configuration. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[Task](arkts-basicservices-agent-task-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the **Task** object obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |
| [13400001](../errorcode-request.md#13400001-file-operation-error) | Invalid file or file system error. |
| [13400003](../errorcode-request.md#13400003-service-error) | Task service ability error. |
| [21900004](../errorcode-request.md#21900004-application-task-queue-full) | The application task queue is full. |
| [21900005](../errorcode-request.md#21900005-task-mode-error) | Operation with wrong task mode. |


## create

```TypeScript
function create(context: BaseContext, config: Config): Promise<Task>
```

Creates an upload or download task and adds it to the queue. This API uses a promise to return the result. HTTP/ HTTPS is supported.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 10

**Required permissions:** ohos.permission.INTERNET

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | Yes | Application-based context. |
| config | [Config](arkts-basicservices-agent-config-i.md) | Yes | Task configuration. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Task](arkts-basicservices-agent-task-i.md)&gt; | Promise used to return the created task. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |
| [13400001](../errorcode-request.md#13400001-file-operation-error) | Invalid file or file system error. |
| [13400003](../errorcode-request.md#13400003-service-error) | Task service ability error. |
| [21900004](../errorcode-request.md#21900004-application-task-queue-full) | The application task queue is full. |
| [21900005](../errorcode-request.md#21900005-task-mode-error) | Operation with wrong task mode. |
