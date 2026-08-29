# Task

上传或下载任务。使用该方法前需要先获取Task对象，promise形式通过 [request.agent.create](arkts-basicservices-agent-create-f.md)获取， callback形式通过 [request.agent.create](arkts-basicservices-agent-create-f.md)获取。

> **说明：**
> 
> Task对象及其挂载回调函数会在调用remove方法后释放并被系统自动回收。

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## 导入模块

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## off

```TypeScript
off(event: 'progress', callback?: (progress: Progress) => void): void
```

取消订阅任务进度事件。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'progress' | 是 | 取消订阅的事件类型。   - 取值为'progress'，表示任务进度。 |
| callback | (progress: Progress) =&gt; void | 否 | 回调函数，发生相关的事件时触发该回调方法。若无此参数，则取消订阅的所有进度回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Missing mandatory parameters.   2. Incorrect parameter type.   3. Parameter verification failed. |
| [21900005](../errorcode-request.md#21900005-任务模式错误) | task mode error.<br>**适用版本：** 10 |

## off

```TypeScript
off(event: 'completed', callback?: (progress: Progress) => void): void
```

取消订阅任务完成事件。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'completed' | 是 | 取消订阅的事件类型。   - 取值为'completed'，表示任务完成。 |
| callback | (progress: Progress) =&gt; void | 否 | 回调函数，发生相关的事件时触发该回调方法。若无此参数，则取消订阅的所有完成回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Missing mandatory parameters.   2. Incorrect parameter type.   3. Parameter verification failed. |
| [21900005](../errorcode-request.md#21900005-任务模式错误) | Operation with wrong task mode.<br>**适用版本：** 10 |

## off

```TypeScript
off(event: 'failed', callback?: (progress: Progress) => void): void
```

取消订阅任务失败事件。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'failed' | 是 | 取消订阅的事件类型。   - 取值为'failed'，表示任务失败。 |
| callback | (progress: Progress) =&gt; void | 否 | 回调函数，发生相关的事件时触发该回调方法。若无此参数，则取消订阅的所有失败回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Missing mandatory parameters.   2. Incorrect parameter type.   3. Parameter verification failed. |
| [21900005](../errorcode-request.md#21900005-任务模式错误) | Operation with wrong task mode.<br>**适用版本：** 10 |

## off

```TypeScript
off(event: 'pause', callback?: (progress: Progress) => void): void
```

取消订阅任务暂停事件。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 11

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'pause' | 是 | 取消订阅的事件类型。   - 取值为'pause'，表示任务暂停。 |
| callback | (progress: Progress) =&gt; void | 否 | 回调函数，发生相关的事件时触发该回调方法。若无此参数，则取消订阅的所有暂停回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Missing mandatory parameters.   2. Incorrect parameter type.   3. Parameter verification failed. |

## off

```TypeScript
off(event: 'resume', callback?: (progress: Progress) => void): void
```

取消订阅任务恢复事件。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 11

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'resume' | 是 | 取消订阅的事件类型。   - 取值为'resume'，表示任务恢复。 |
| callback | (progress: Progress) =&gt; void | 否 | 回调函数，发生相关的事件时触发该回调方法。若无此参数，则取消订阅的所有恢复回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Missing mandatory parameters.   2. Incorrect parameter type.   3. Parameter verification failed. |

## off

```TypeScript
off(event: 'remove', callback?: (progress: Progress) => void): void
```

取消订阅任务移除事件。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 11

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'remove' | 是 | 取消订阅的事件类型。   - 取值为'remove'，表示任务被移除。 |
| callback | (progress: Progress) =&gt; void | 否 | 回调函数，发生相关的事件时触发该回调方法。若无此参数，则取消订阅的所有移除回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameter types.   3. Parameter verification failed. |

## off

```TypeScript
off(event: 'response', callback?: Callback<HttpResponse>): void
```

取消订阅任务响应事件。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'response' | 是 | 取消订阅的事件类型。   - 取值为'response'，表示任务响应。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;HttpResponse&gt; | 否 | 需要取消订阅的回调函数。若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Missing mandatory parameters.   2. Incorrect parameter type.   3. Parameter verification failed. |

## off

```TypeScript
off(event: 'faultOccur', callback?: Callback<Faults>): void
```

取消订阅任务失败原因相关的事件。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'faultOccur' | 是 | 订阅的事件类型。   - 取值为'faultOccur'，表示任务失败。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[Faults](arkts-basicservices-agent-faults-e.md)&gt; | 否 | 需要取消订阅的回调函数。若无此参数，则默认取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Missing mandatory parameters.   2. Incorrect parameter type.   3. Parameter verification failed. |

## off

```TypeScript
off(event: 'wait', callback?: Callback<WaitingReason>): void
```

取消订阅任务等待原因相关的事件。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'wait' | 是 | 订阅的事件类型。   - 取值为'wait'，表示任务等待。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[WaitingReason](arkts-basicservices-agent-waitingreason-e.md)&gt; | 否 | 需要取消订阅的回调函数。若无此参数，则默认取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Missing mandatory parameters.   2. Incorrect parameter type.   3. Parameter verification failed. |

## on

```TypeScript
on(event: 'progress', callback: (progress: Progress) => void): void
```

订阅任务进度的事件，使用callback异步回调。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'progress' | 是 | 订阅的事件类型。   - 取值为'progress'，表示任务进度，任务进度有进展时触发该事件。 |
| callback | (progress: Progress) =&gt; void | 是 | 回调函数，发生相关的事件时触发该回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Missing mandatory parameters.   2. Incorrect parameter type.   3. Parameter verification failed. |
| [21900005](../errorcode-request.md#21900005-任务模式错误) | task mode error.<br>**适用版本：** 10 |

## on

```TypeScript
on(event: 'completed', callback: (progress: Progress) => void): void
```

订阅任务完成事件，使用callback异步回调。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'completed' | 是 | 订阅的事件类型。   - 取值为'completed'，表示任务完成，任务完成时触发该事件。 |
| callback | (progress: Progress) =&gt; void | 是 | 回调函数，发生相关的事件时触发该回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Missing mandatory parameters.   2. Incorrect parameter type.   3. Parameter verification failed. |
| [21900005](../errorcode-request.md#21900005-任务模式错误) | task mode error.<br>**适用版本：** 10 |

## on

```TypeScript
on(event: 'failed', callback: (progress: Progress) => void): void
```

订阅任务失败事件，使用callback异步回调。可通过调用 [request.agent.show](arkts-basicservices-agent-show-f.md)查看错误原因 。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'failed' | 是 | 订阅的事件类型。   - 取值为'failed'，表示任务失败，任务失败时触发该事件。 |
| callback | (progress: Progress) =&gt; void | 是 | 回调函数，发生相关的事件时触发该回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Missing mandatory parameters.   2. Incorrect parameter type.   3. Parameter verification failed. |
| [21900005](../errorcode-request.md#21900005-任务模式错误) | Operation with wrong task mode.<br>**适用版本：** 10 |

## on

```TypeScript
on(event: 'pause', callback: (progress: Progress) => void): void
```

订阅任务暂停事件，使用callback异步回调。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 11

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'pause' | 是 | 订阅的事件类型。   - 取值为'pause'，表示任务已暂停，任务暂停时触发该事件。 |
| callback | (progress: Progress) =&gt; void | 是 | 回调函数，发生相关的事件时触发该回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Missing mandatory parameters.   2. Incorrect parameter type.   3. Parameter verification failed. |

## on

```TypeScript
on(event: 'resume', callback: (progress: Progress) => void): void
```

订阅任务恢复事件，使用callback异步回调。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 11

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'resume' | 是 | 订阅的事件类型。   - 取值为'resume'，表示任务恢复，任务恢复时触发该事件。 |
| callback | (progress: Progress) =&gt; void | 是 | 回调函数，发生相关的事件时触发该回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Missing mandatory parameters.   2. Incorrect parameter type.   3. Parameter verification failed. |

## on

```TypeScript
on(event: 'remove', callback: (progress: Progress) => void): void
```

订阅任务移除事件，使用callback异步回调。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 11

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'remove' | 是 | 订阅的事件类型。   - 取值为'remove'，表示任务被移除，任务移除时触发该事件。 |
| callback | (progress: Progress) =&gt; void | 是 | 回调函数，发生相关的事件时触发该回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Missing mandatory parameters.   2. Incorrect parameter type.   3. Parameter verification failed. |

## on

```TypeScript
on(event: 'response', callback: Callback<HttpResponse>): void
```

订阅任务响应头，使用callback异步回调。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'response' | 是 | 订阅的事件类型。   - 取值为'response'，表示任务响应，请求接收到响应时触发该事件。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;HttpResponse&gt; | 是 | 回调函数，发生相关的事件时触发该回调方法，返回任务响应头的数据结构。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Missing mandatory parameters.   2. Incorrect parameter type.   3. Parameter verification failed. |

## on

```TypeScript
on(event: 'faultOccur', callback: Callback<Faults>): void
```

订阅任务失败原因，使用callback形式返回结果。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'faultOccur' | 是 | 订阅的事件类型。   - 取值为'faultOccur'，表示任务失败。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[Faults](arkts-basicservices-agent-faults-e.md)&gt; | 是 | 发生相关的事件时触发该回调方法，返回任务失败的原因。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Missing mandatory parameters.   2. Incorrect parameter type.   3. Parameter verification failed. |

## on

```TypeScript
on(event: 'wait', callback: Callback<WaitingReason>): void
```

订阅任务等待原因，使用callback形式返回结果。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'wait' | 是 | 订阅的事件类型。   - 取值为'wait'，表示任务等待。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[WaitingReason](arkts-basicservices-agent-waitingreason-e.md)&gt; | 是 | 发生相关的事件时触发该回调方法，返回任务等待的原因。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Missing mandatory parameters.   2. Incorrect parameter type.   3. Parameter verification failed. |

## pause

```TypeScript
pause(callback: AsyncCallback<void>): void
```

暂停任务，可以暂停正在等待/正在运行/正在重试的任务，已暂停的任务可被 [resume](#resume)恢复。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当暂停任务成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13400003](../errorcode-request.md#13400003-服务异常) | Task service ability error. |
| [21900005](../errorcode-request.md#21900005-任务模式错误) | Operation with wrong task mode.<br>**适用版本：** 10 |
| [21900007](../errorcode-request.md#21900007-在不支持的状态上的操作) | Operation with wrong task state. |

**示例**

```TypeScript
downloadTask.pause((err: BusinessError) => {
  if (err) {
    console.error(`Failed to pause the download task. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in pausing the download task.');
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let config: request.agent.Config = {
  action: request.agent.Action.DOWNLOAD,
  url: 'http://127.0.0.1', // 需要手动将url替换为真实服务器的HTTP协议地址
  title: 'taskPauseTest',
  description: 'Sample code for pause the download task',
  mode: request.agent.Mode.BACKGROUND,
  overwrite: false,
  method: "GET",
  data: "",
  saveas: "./",
  network: request.agent.Network.CELLULAR,
  metered: false,
  roaming: true,
  retry: true,
  redirect: true,
  index: 0,
  begins: 0,
  ends: -1,
  gauge: false,
  precise: false,
  token: "it is a secret"
};
request.agent.create(context, config).then(async (task: request.agent.Task) => {
  task.start();
  // 等待1秒再执行下一步操作，以防异步乱序
  await new Promise<void>((resolve) => {
    setTimeout(() => resolve(), 1000);
  })
  task.pause((err: BusinessError) => {
    if (err) {
      console.error(`Failed to pause the download task, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in pausing a download task. `);
  });
  console.info(`Succeeded in creating a download task. result: ${task.tid}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
});
```

## pause

```TypeScript
pause(): Promise<void>
```

暂停任务，可以暂停正在等待/正在运行/正在重试的任务，已暂停的任务可被 [resume](#resume)恢复。使用Promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13400003](../errorcode-request.md#13400003-服务异常) | Task service ability error. |
| [21900005](../errorcode-request.md#21900005-任务模式错误) | Operation with wrong task mode.<br>**适用版本：** 10 |
| [21900007](../errorcode-request.md#21900007-在不支持的状态上的操作) | Operation with wrong task state. |

**示例**

```TypeScript
downloadTask.pause().then(() => {    
  console.info('Succeeded in pausing the download task.');
}).catch((err: BusinessError) => {
  console.error(`Failed to pause the download task. Code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let config: request.agent.Config = {
  action: request.agent.Action.DOWNLOAD,
  url: 'http://127.0.0.1', // 需要手动将url替换为真实服务器的HTTP协议地址
  title: 'taskPauseTest',
  description: 'Sample code for pause the download task',
  mode: request.agent.Mode.BACKGROUND,
  overwrite: false,
  method: "GET",
  data: "",
  saveas: "./",
  network: request.agent.Network.CELLULAR,
  metered: false,
  roaming: true,
  retry: true,
  redirect: true,
  index: 0,
  begins: 0,
  ends: -1,
  gauge: false,
  precise: false,
  token: "it is a secret"
};
request.agent.create(context, config).then(async (task: request.agent.Task) => {
  task.start();
  // 等待1秒再执行下一步操作，以防异步乱序
  await new Promise<void>((resolve) => {
    setTimeout(() => resolve(), 1000);
  })
  task.pause().then(() => {
    console.info(`Succeeded in pausing a download task. `);
  }).catch((err: BusinessError) => {
    console.error(`Failed to pause the download task, Code: ${err.code}, message: ${err.message}`);
  });
  console.info(`Succeeded in creating a download task. result: ${task.tid}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
});
```

## resume

```TypeScript
resume(callback: AsyncCallback<void>): void
```

重新启动任务，可以恢复被暂停的任务。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.INTERNET

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当重新启动任务成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [13400003](../errorcode-request.md#13400003-服务异常) | Task service ability error. |
| [21900005](../errorcode-request.md#21900005-任务模式错误) | Operation with wrong task mode.<br>**适用版本：** 10 |
| [21900007](../errorcode-request.md#21900007-在不支持的状态上的操作) | Operation with wrong task state. |

**示例**

```TypeScript
downloadTask.resume((err: BusinessError) => {
  if (err) {
    console.error(`Failed to resume the download task. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in resuming the download task.');
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let config: request.agent.Config = {
  action: request.agent.Action.DOWNLOAD,
  url: 'http://127.0.0.1', // 需要手动将url替换为真实服务器的HTTP协议地址
  title: 'taskResumeTest',
  description: 'Sample code for resume the download task',
  mode: request.agent.Mode.BACKGROUND,
  overwrite: false,
  method: "GET",
  data: "",
  saveas: "./",
  network: request.agent.Network.CELLULAR,
  metered: false,
  roaming: true,
  retry: true,
  redirect: true,
  index: 0,
  begins: 0,
  ends: -1,
  gauge: false,
  precise: false,
  token: "it is a secret"
};
request.agent.create(context, config).then(async (task: request.agent.Task) => {
  task.start();
  // 等待1秒再执行下一步操作，以防异步乱序
  await new Promise<void>((resolve) => {
    setTimeout(() => resolve(), 1000);
  })
  task.pause();
  // 等待1秒再执行下一步操作，以防异步乱序
  await new Promise<void>((resolve) => {
    setTimeout(() => resolve(), 1000);
  })
  task.resume((err: BusinessError) => {
    if (err) {
      console.error(`Failed to resume the download task, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in resuming a download task. `);
  });
  console.info(`Succeeded in creating a download task. result: ${task.tid}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
});
```

## resume

```TypeScript
resume(): Promise<void>
```

重新启动任务，可以恢复被暂停的任务。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.INTERNET

**系统能力：** SystemCapability.Request.FileTransferAgent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [13400003](../errorcode-request.md#13400003-服务异常) | Task service ability error. |
| [21900005](../errorcode-request.md#21900005-任务模式错误) | Operation with wrong task mode.<br>**适用版本：** 10 |
| [21900007](../errorcode-request.md#21900007-在不支持的状态上的操作) | Operation with wrong task state. |

**示例**

```TypeScript
downloadTask.resume().then(() => {
  console.info('Succeeded in resuming the download task.');
}).catch((err: BusinessError) => {
  console.error(`Failed to resume the download task. Code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let config: request.agent.Config = {
  action: request.agent.Action.DOWNLOAD,
  url: 'http://127.0.0.1', // 需要手动将url替换为真实服务器的HTTP协议地址
  title: 'taskResumeTest',
  description: 'Sample code for resume the download task',
  mode: request.agent.Mode.BACKGROUND,
  overwrite: false,
  method: "GET",
  data: "",
  saveas: "./",
  network: request.agent.Network.CELLULAR,
  metered: false,
  roaming: true,
  retry: true,
  redirect: true,
  index: 0,
  begins: 0,
  ends: -1,
  gauge: false,
  precise: false,
  token: "it is a secret"
};
request.agent.create(context, config).then(async (task: request.agent.Task) => {
  task.start();
  // 等待1秒再执行下一步操作，以防异步乱序
  await new Promise<void>((resolve) => {
    setTimeout(() => resolve(), 1000);
  })
  task.pause();
  // 等待1秒再执行下一步操作，以防异步乱序
  await new Promise<void>((resolve) => {
    setTimeout(() => resolve(), 1000);
  })
  task.resume().then(() => {
    console.info(`Succeeded in resuming a download task. `);
  }).catch((err: BusinessError) => {
    console.error(`Failed to resume the download task, Code: ${err.code}, message: ${err.message}`);
  });
  console.info(`Succeeded in creating a download task. result: ${task.tid}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
});
```

## setMaxSpeed

```TypeScript
setMaxSpeed(speed: number): Promise<void>
```

设置任务每秒能传输的字节数上限。使用Promise异步回调。

**起始版本：** 18

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| speed | number | 是 | 设置任务每秒能传输的字节数上限，单位为字节（B），最小值为16384字节，同时该值不得低于 [MinSpeed](arkts-basicservices-agent-minspeed-i.md)设置的最低速度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Missing mandatory parameters.   2. Incorrect parameter type.   3. Parameter verification failed. |
| [13400003](../errorcode-request.md#13400003-服务异常) | Task service ability error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let config: request.agent.Config = {
  action: request.agent.Action.DOWNLOAD,
  url: 'http://127.0.0.1', // 需要手动将url替换为真实服务器的HTTP协议地址
  saveas: "./",
};
request.agent.create(context, config).then((task: request.agent.Task) => {
  // 设置任务速度上限。
  task.setMaxSpeed(10 * 1024 * 1024).then(() => {
    console.info(`Succeeded in setting the max speed of the task. result: ${task.tid}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the max speed of the task. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
});
```

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

启动一个任务。使用callback异步回调。以下状态的任务可以被启动：
1. 刚被request.agent.create接口创建的任务。
2. 使用request.agent.create接口创建的已经失败或者停止的下载任务。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 10

**需要权限：** ohos.permission.INTERNET

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当开启任务成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [13400003](../errorcode-request.md#13400003-服务异常) | Task service ability error. |
| [21900007](../errorcode-request.md#21900007-在不支持的状态上的操作) | Operation with wrong task state. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let config: request.agent.Config = {
  action: request.agent.Action.DOWNLOAD,
  url: 'http://127.0.0.1', // 需要手动将url替换为真实服务器的HTTP协议地址
  title: 'taskStartTest',
  description: 'Sample code for start the download task',
  mode: request.agent.Mode.BACKGROUND,
  overwrite: false,
  method: "GET",
  data: "",
  saveas: "./",
  network: request.agent.Network.CELLULAR,
  metered: false,
  roaming: true,
  retry: true,
  redirect: true,
  index: 0,
  begins: 0,
  ends: -1,
  gauge: false,
  precise: false,
  token: "it is a secret"
};
request.agent.create(context, config).then((task: request.agent.Task) => {
  task.start((err: BusinessError) => {
    if (err) {
      console.error(`Failed to start the download task, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in starting a download task.`);
  });
  console.info(`Succeeded in creating a download task. result: ${task.tid}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
});
```

## start

```TypeScript
start(): Promise<void>
```

启动一个任务。使用Promise异步回调。以下状态的任务可以被启动：
1. 刚被request.agent.create接口创建的任务。
2. 使用request.agent.create接口创建的已经失败或者停止的下载任务。

> **说明：**
> 
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 10

**需要权限：** ohos.permission.INTERNET

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [13400003](../errorcode-request.md#13400003-服务异常) | Task service ability error. |
| [21900007](../errorcode-request.md#21900007-在不支持的状态上的操作) | Operation with wrong task state. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let config: request.agent.Config = {
  action: request.agent.Action.DOWNLOAD,
  url: 'http://127.0.0.1', // 需要手动将url替换为真实服务器的HTTP协议地址
  title: 'taskStartTest',
  description: 'Sample code for start the download task',
  mode: request.agent.Mode.BACKGROUND,
  overwrite: false,
  method: "GET",
  data: "",
  saveas: "./",
  network: request.agent.Network.CELLULAR,
  metered: false,
  roaming: true,
  retry: true,
  redirect: true,
  index: 0,
  begins: 0,
  ends: -1,
  gauge: false,
  precise: false,
  token: "it is a secret"
};
request.agent.create(context, config).then((task: request.agent.Task) => {
  task.start().then(() => {
    console.info(`Succeeded in starting a download task.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to start the download task, Code: ${err.code}, message: ${err.message}`);
  });
  console.info(`Succeeded in creating a download task. result: ${task.tid}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
});
```

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

停止任务，可以停止正在运行/正在等待/正在重试的任务，已停止的任务可被 [start](#start)恢复。使用callback异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当停止任务成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13400003](../errorcode-request.md#13400003-服务异常) | Task service ability error. |
| [21900007](../errorcode-request.md#21900007-在不支持的状态上的操作) | Operation with wrong task state. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let config: request.agent.Config = {
  action: request.agent.Action.DOWNLOAD,
  url: 'http://127.0.0.1', // 需要手动将url替换为真实服务器的HTTP协议地址
  title: 'taskStopTest',
  description: 'Sample code for stop the download task',
  mode: request.agent.Mode.BACKGROUND,
  overwrite: false,
  method: "GET",
  data: "",
  saveas: "./",
  network: request.agent.Network.CELLULAR,
  metered: false,
  roaming: true,
  retry: true,
  redirect: true,
  index: 0,
  begins: 0,
  ends: -1,
  gauge: false,
  precise: false,
  token: "it is a secret"
};
request.agent.create(context, config).then(async (task: request.agent.Task) => {
  task.start();
  // 等待1秒再执行下一步操作，以防异步乱序
  await new Promise<void>((resolve) => {
    setTimeout(() => resolve(), 1000);
  })
  task.stop((err: BusinessError) => {
    if (err) {
      console.error(`Failed to stop the download task, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in stopping a download task. `);
  });
  console.info(`Succeeded in creating a download task. result: ${task.tid}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
});
```

## stop

```TypeScript
stop(): Promise<void>
```

停止任务，可以停止正在运行/正在等待/正在重试的任务，已停止的任务可被 [start](#start)恢复。使用Promise异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13400003](../errorcode-request.md#13400003-服务异常) | Task service ability error. |
| [21900007](../errorcode-request.md#21900007-在不支持的状态上的操作) | Operation with wrong task state. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let config: request.agent.Config = {
  action: request.agent.Action.DOWNLOAD,
  url: 'http://127.0.0.1', // 需要手动将url替换为真实服务器的HTTP协议地址
  title: 'taskStopTest',
  description: 'Sample code for stop the download task',
  mode: request.agent.Mode.BACKGROUND,
  overwrite: false,
  method: "GET",
  data: "",
  saveas: "./",
  network: request.agent.Network.CELLULAR,
  metered: false,
  roaming: true,
  retry: true,
  redirect: true,
  index: 0,
  begins: 0,
  ends: -1,
  gauge: false,
  precise: false,
  token: "it is a secret"
};
request.agent.create(context, config).then(async (task: request.agent.Task) => {
  task.start();
  // 等待1秒再执行下一步操作，以防异步乱序
  await new Promise<void>((resolve) => {
    setTimeout(() => resolve(), 1000);
  })
  task.stop().then(() => {
    console.info(`Succeeded in stopping a download task. `);
  }).catch((err: BusinessError) => {
    console.error(`Failed to stop the download task, Code: ${err.code}, message: ${err.message}`);
  });
  console.info(`Succeeded in creating a download task. result: ${task.tid}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
});
```

## config

```TypeScript
config: Config
```

任务的配置信息。

**类型：** Config

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## tid

```TypeScript
readonly tid: string
```

任务id，由系统自动生成且唯一。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent
