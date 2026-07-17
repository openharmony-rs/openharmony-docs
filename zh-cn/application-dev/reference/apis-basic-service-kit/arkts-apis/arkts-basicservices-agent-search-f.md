# search

## 导入模块

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## search

```TypeScript
function search(callback: AsyncCallback<Array<string>>): void
```

根据默认[Filter](arkts-basicservices-agent-filter-i.md)过滤条件查找任务id，即查询调用时刻至24小时前的所有任务的任务id。使用callback异步回调。

**起始版本：** 10

<!--Device-agent-function search(callback: AsyncCallback<Array<string>>): void--><!--Device-agent-function search(callback: AsyncCallback<Array<string>>): void-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<Array<string>> | 是 | 回调函数。当根据过滤条件查找任务成功，err为undefined，data为满足条件的任务id；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Incorrect parameter type.<br> 2. Parameter verification failed. |
| [13400003](../../apis-basic-services-kit/errorcode-request.md#13400003-服务异常) | Task service ability error. |


## search

```TypeScript
function search(filter: Filter, callback: AsyncCallback<Array<string>>): void
```

根据[Filter](arkts-basicservices-agent-filter-i.md)过滤条件查找任务id。使用callback异步回调。

**起始版本：** 10

<!--Device-agent-function search(filter: Filter, callback: AsyncCallback<Array<string>>): void--><!--Device-agent-function search(filter: Filter, callback: AsyncCallback<Array<string>>): void-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [Filter](arkts-basicservices-agent-filter-i.md) | 是 | 过滤条件。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<Array<string>> | 是 | 回调函数。当根据过滤条件查找任务成功，err为undefined，data为满足条件的任务id；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Incorrect parameter type.<br> 2. Parameter verification failed. |
| [13400003](../../apis-basic-services-kit/errorcode-request.md#13400003-服务异常) | Task service ability error. |


## search

```TypeScript
function search(filter?: Filter): Promise<Array<string>>
```

根据[Filter](arkts-basicservices-agent-filter-i.md)过滤条件查找任务id。使用Promise异步回调。

**起始版本：** 10

<!--Device-agent-function search(filter?: Filter): Promise<Array<string>>--><!--Device-agent-function search(filter?: Filter): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [Filter](arkts-basicservices-agent-filter-i.md) | 否 | 过滤条件。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<string>> | Promise对象。返回满足条件任务id的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Incorrect parameter type.<br> 2. Parameter verification failed. |
| [13400003](../../apis-basic-services-kit/errorcode-request.md#13400003-服务异常) | Task service ability error. |

