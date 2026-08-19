# CommonEventSubscriber

表示公共事件的订阅者。CommonEventSubscriber提供了对有序公共事件的 处理能力，包括获取和设置事件传递的Code和Data数据、查询当前公共事件 是否为有序或粘性公共事件、中止或清理有序公共事件的中止状态、结束对 当前有序公共事件的处理，以及获取订阅者的订阅信息等，适用于订阅者需要 对接收到的公共事件进行数据处理和流程控制的场景。

**起始版本：** 23

<!--Device-unnamed-export interface CommonEventSubscriber--><!--Device-unnamed-export interface CommonEventSubscriber-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## abortCommonEvent

```TypeScript
abortCommonEvent(callback: AsyncCallback<void>): void
```

添加有序公共事件的中止状态。当该接口与 [finishCommonEvent](#finishcommonevent)配合使用时，可以中止当前的有序公共事 件，使该公共事件不再向下一个订阅者传递。使用callback异步回调。

**起始版本：** 23

<!--Device-CommonEventSubscriber-abortCommonEvent(callback: AsyncCallback<void>): void--><!--Device-CommonEventSubscriber-abortCommonEvent(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当添加有序公共事件中止状态成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.abortCommonEvent((err: BusinessError) => {
  if (err) {
    console.error(`Failed to abort common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in aborting common event.`);
});
subscriber.finishCommonEvent((err: BusinessError) => {
  if (err) {
    console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in finishing common event.`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.abortCommonEvent((err: BusinessError | null) => {
  if (err) {
    console.error(`Failed to abort common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in aborting common event.`);
});
subscriber.finishCommonEvent((err: BusinessError | null) => {
  if (err) {
    console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in finishing common event.`);
});
```

## abortCommonEvent

```TypeScript
abortCommonEvent(): Promise<void>
```

添加有序公共事件的中止状态。当该接口与 [finishCommonEvent](#finishcommonevent)配合使用时，可以中止当前的有序公共事 件，使该公共事件不再向下一个订阅者传递。使用Promise异步回调。

**起始版本：** 23

<!--Device-CommonEventSubscriber-abortCommonEvent(): Promise<void>--><!--Device-CommonEventSubscriber-abortCommonEvent(): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.abortCommonEvent().then(() => {
  console.info(`Succeeded in aborting common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to abort common event. Code is ${err.code}, message is ${err.message}`);
});
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.abortCommonEvent().then(() => {
  console.info(`Succeeded in aborting common event.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to abort common event. Code is ${error.code}, message is ${error.message}`);
});
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to finish common event. Code is ${error.code}, message is ${error.message}`);
});
```

## abortCommonEventSync

```TypeScript
abortCommonEventSync(): void
```

同步添加有序公共事件的中止状态。当该接口与 [finishCommonEvent](#finishcommonevent)配合使用时，可以中止当前的有序公共事 件，使该公共事件不再向下一个订阅者传递。

**起始版本：** 23

<!--Device-CommonEventSubscriber-abortCommonEventSync(): void--><!--Device-CommonEventSubscriber-abortCommonEventSync(): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.abortCommonEventSync();
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.abortCommonEventSync();
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to finish common event. Code is ${error.code}, message is ${error.message}`);
});
```

## clearAbortCommonEvent

```TypeScript
clearAbortCommonEvent(callback: AsyncCallback<void>): void
```

清理有序公共事件的中止状态。当该接口与 [finishCommonEvent](#finishcommonevent)配合使用时，可以使该公共事件继续向下 一个订阅者传递。使用callback异步回调。

**起始版本：** 23

<!--Device-CommonEventSubscriber-clearAbortCommonEvent(callback: AsyncCallback<void>): void--><!--Device-CommonEventSubscriber-clearAbortCommonEvent(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当清理有序公共事件中止状态成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.clearAbortCommonEvent((err: BusinessError) => {
  if (err) {
    console.error(`Failed to clear abort common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in clearing abort common event.`);
});
subscriber.finishCommonEvent((err: BusinessError) => {
  if (err) {
    console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in finishing common event.`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.clearAbortCommonEvent((err: BusinessError | null) => {
  if (err) {
    console.error(`Failed to clear abort common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in clearing abort common event.`);
});
subscriber.finishCommonEvent((err: BusinessError | null) => {
  if (err) {
    console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in finishing common event.`);
});
```

## clearAbortCommonEvent

```TypeScript
clearAbortCommonEvent(): Promise<void>
```

清理有序公共事件的中止状态。当该接口与 [finishCommonEvent](#finishcommonevent)配合使用时，可以使该公共事件继续向下 一个订阅者传递。使用Promise异步回调。

**起始版本：** 23

<!--Device-CommonEventSubscriber-clearAbortCommonEvent(): Promise<void>--><!--Device-CommonEventSubscriber-clearAbortCommonEvent(): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.clearAbortCommonEvent().then(() => {
  console.info(`Succeeded in clearing abort common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to clear abort common event. Code is ${err.code}, message is ${err.message}`);
});
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.clearAbortCommonEvent().then(() => {
  console.info(`Succeeded in clearing abort common event.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to clear abort common event. Code is ${error.code}, message is ${error.message}`);
});
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: Error): void  => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to finish common event. Code is ${error.code}, message is ${error.message}`);
});
```

## clearAbortCommonEventSync

```TypeScript
clearAbortCommonEventSync(): void
```

同步清理有序公共事件的中止状态。当该接口与 [finishCommonEvent](#finishcommonevent)配合使用时，可以使该公共事件继续向下 一个订阅者传递。

**起始版本：** 23

<!--Device-CommonEventSubscriber-clearAbortCommonEventSync(): void--><!--Device-CommonEventSubscriber-clearAbortCommonEventSync(): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.clearAbortCommonEventSync();
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.clearAbortCommonEventSync();
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to finish common event. Code is ${error.code}, message is ${error.message}`);
});
```

## finishCommonEvent

```TypeScript
finishCommonEvent(callback: AsyncCallback<void>): void
```

用于订阅者结束对当前有序公共事件的处理。使用callback异步回调。

**起始版本：** 23

<!--Device-CommonEventSubscriber-finishCommonEvent(callback: AsyncCallback<void>): void--><!--Device-CommonEventSubscriber-finishCommonEvent(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当订阅者结束当前有序公共事件成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.finishCommonEvent((err: BusinessError) => {
  if (err) {
    console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in finishing common event.`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.finishCommonEvent((err: BusinessError | null) => {
  if (err) {
    console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in finishing common event.`);
});
```

## finishCommonEvent

```TypeScript
finishCommonEvent(): Promise<void>
```

用于订阅者结束对当前有序公共事件的处理。使用Promise异步回调。

**起始版本：** 23

<!--Device-CommonEventSubscriber-finishCommonEvent(): Promise<void>--><!--Device-CommonEventSubscriber-finishCommonEvent(): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to finish common event. Code is ${error.code}, message is ${error.message}`);
});
```

## getAbortCommonEvent

```TypeScript
getAbortCommonEvent(callback: AsyncCallback<boolean>): void
```

获取当前有序公共事件是否处于中止状态。使用callback异步回调。

**起始版本：** 23

<!--Device-CommonEventSubscriber-getAbortCommonEvent(callback: AsyncCallback<boolean>): void--><!--Device-CommonEventSubscriber-getAbortCommonEvent(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 当查询成功时，err为undefined，data为true表示当前有序公共事件处于中止状态，data为false表示当前有序公共事件没有处于中止状态；否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.getAbortCommonEvent((err: BusinessError, abortEvent: boolean) => {
  if (err) {
    console.error(`Failed to get abort common event. Code is ${err.code}, message is ${err.message}`);
    return;
  } 
  console.info(`Succeeded in getting abort common event, abortEvent is ${JSON.stringify(abortEvent)}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.getAbortCommonEvent((err: BusinessError | null, abortEvent: boolean | undefined | null) => {
  if (err) {
    console.error(`Failed to get abort common event. Code is ${err.code}, message is ${err.message}`);
    return;
  } 
  console.info(`Succeeded in getting abort common event, abortEvent is ${JSON.stringify(abortEvent)}`);
});
```

## getAbortCommonEvent

```TypeScript
getAbortCommonEvent(): Promise<boolean>
```

获取当前有序公共事件是否处于中止状态。使用Promise异步回调。

**起始版本：** 23

<!--Device-CommonEventSubscriber-getAbortCommonEvent(): Promise<boolean>--><!--Device-CommonEventSubscriber-getAbortCommonEvent(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示当前有序公共事件处于中止状态；返回false表示当前有序公共事件未处于中止状态。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.getAbortCommonEvent().then((abortEvent: boolean) => {
  console.info(`Succeeded in getting abort common event, abortEvent is ${JSON.stringify(abortEvent)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get abort common event. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.getAbortCommonEvent().then((abortEvent: boolean) => {
  console.info(`Succeeded in getting abort common event, abortEvent is ${JSON.stringify(abortEvent)}`);
}).catch((err: Error): void  => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get abort common event. Code is ${error.code}, message is ${error.message}`);
});
```

## getAbortCommonEventSync

```TypeScript
getAbortCommonEventSync(): boolean
```

同步获取当前有序公共事件是否处于中止状态。

**起始版本：** 23

<!--Device-CommonEventSubscriber-getAbortCommonEventSync(): boolean--><!--Device-CommonEventSubscriber-getAbortCommonEventSync(): boolean-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示当前有序公共事件处于中止状态；返回false表示当前有序公共事件未处于中止状态。 |

**示例**

```TypeScript
let abortEvent: boolean = subscriber.getAbortCommonEventSync();
console.info(`Succeeded in getting abort common event, abortEvent is ${JSON.stringify(abortEvent)}`);
```

## getCode

```TypeScript
getCode(callback: AsyncCallback<int>): void
```

获取有序公共事件传递的数据。使用callback异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-getCode(callback: AsyncCallback<int>): void--><!--Device-CommonEventSubscriber-getCode(callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;int&gt; | 是 | 回调函数。当获取有序公共事件传递的数据成功时，err为undefined，data为获取到的数据；否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.getCode((err: BusinessError, code: number) => {
  if (err) {
    console.error(`Failed to get code. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting code, code is ${JSON.stringify(code)}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.getCode((err: BusinessError | null, code: int | undefined | null) => {
  if (err) {
    console.error(`Failed to get code. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting code, code is ${JSON.stringify(code)}`);
});
```

## getCode

```TypeScript
getCode(): Promise<int>
```

获取有序公共事件传递的数据。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-getCode(): Promise<int>--><!--Device-CommonEventSubscriber-getCode(): Promise<int>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象。返回有序公共事件传递的数据。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.getCode().then((code: number) => {
  console.info(`Succeeded in getting code, code is ${JSON.stringify(code)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get code. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.getCode().then((code: int) => {
  console.info(`Succeeded in getting code, code is ${JSON.stringify(code)}`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get code. Code is ${error.code}, message is ${error.message}`);
});
```

## getCodeSync

```TypeScript
getCodeSync(): int
```

同步获取有序公共事件传递的数据。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-getCodeSync(): int--><!--Device-CommonEventSubscriber-getCodeSync(): int-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 表示有序公共事件传递的数据。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
let code: number = subscriber.getCodeSync();
console.info(`Succeeded in getting code, code is ${JSON.stringify(code)}`);
```

ArkTS-Sta示例：

```TypeScript
let code: int = subscriber.getCodeSync();
console.info(`Succeeded in getting code, code is ${JSON.stringify(code)}`);
```

## getData

```TypeScript
getData(callback: AsyncCallback<string>): void
```

获取有序公共事件传递的数据。使用callback异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-getData(callback: AsyncCallback<string>): void--><!--Device-CommonEventSubscriber-getData(callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | 回调函数。当获取有序公共事件传递的数据成功时，err为undefined，data为获取到的数据；否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
// 获取有序公共事件传递的数据回调
subscriber.getData((err: BusinessError, data: string) => {
  if (err) {
    console.error(`Failed to get data. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting data, data is ${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```TypeScript
// 获取有序公共事件传递的数据回调
subscriber.getData((err: BusinessError | null, data: string | undefined | null) => {
  if (err) {
    console.error(`Failed to get data. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting data, data is ${JSON.stringify(data)}`);
});
```

## getData

```TypeScript
getData(): Promise<string>
```

获取有序公共事件传递的数据。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-getData(): Promise<string>--><!--Device-CommonEventSubscriber-getData(): Promise<string>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。返回有序公共事件传递的数据。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.getData().then((data: string) => {
  console.info(`Succeeded in getting data, data is ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get data. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.getData().then((data: string) => {
  console.info(`Succeeded in getting data, data is ${JSON.stringify(data)}`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get data. Code is ${error.code}, message is ${error.message}`);
});
```

## getDataSync

```TypeScript
getDataSync(): string
```

同步获取有序公共事件传递的数据。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-getDataSync(): string--><!--Device-CommonEventSubscriber-getDataSync(): string-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 有序公共事件传递的数据。 |

**示例**

```TypeScript
let data: string = subscriber.getDataSync();
console.info(`Succeeded in getting data, data is ${data}`);
```

## getSubscribeInfo

```TypeScript
getSubscribeInfo(callback: AsyncCallback<CommonEventSubscribeInfo>): void
```

获取订阅者的订阅信息。使用callback异步回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-getSubscribeInfo(callback: AsyncCallback<CommonEventSubscribeInfo>): void--><!--Device-CommonEventSubscriber-getSubscribeInfo(callback: AsyncCallback<CommonEventSubscribeInfo>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;[CommonEventSubscribeInfo](arkts-basicservices-commoneventsubscribeinfo-commoneventsubscribeinfo-i.md)&gt; | 是 | 回调函数。当获取成功时，err为undefined，data为订阅者的订阅信息；否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.getSubscribeInfo((err: BusinessError, subscribeInfo: commonEventManager.CommonEventSubscribeInfo) => {
  if (err) {
    console.error(`Failed to get subscribe info. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting subscribe info, subscribe info is ${JSON.stringify(subscribeInfo)}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.getSubscribeInfo((err: BusinessError | null, subscribeInfo: commonEventManager.CommonEventSubscribeInfo | undefined | null) => {
  if (err) {
    console.error(`Failed to get subscribe info. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting subscribe info, subscribe info is ${JSON.stringify(subscribeInfo)}`);
});
```

## getSubscribeInfo

```TypeScript
getSubscribeInfo(callback: AsyncCallback<CommonEventSubscribeInfo|null>): void
```

获取订阅者的订阅信息。使用callback异步回调。

**起始版本：** 23

<!--Device-CommonEventSubscriber-getSubscribeInfo(callback: AsyncCallback<CommonEventSubscribeInfo|null>): void--><!--Device-CommonEventSubscriber-getSubscribeInfo(callback: AsyncCallback<CommonEventSubscribeInfo|null>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;[CommonEventSubscribeInfo](arkts-basicservices-commoneventsubscribeinfo-commoneventsubscribeinfo-i.md) \| null&gt; | 是 | 回调函数。返回订阅者的订阅信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## getSubscribeInfo

```TypeScript
getSubscribeInfo(): Promise<CommonEventSubscribeInfo>
```

获取订阅者的订阅信息。使用Promise异步回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-getSubscribeInfo(): Promise<CommonEventSubscribeInfo>--><!--Device-CommonEventSubscriber-getSubscribeInfo(): Promise<CommonEventSubscribeInfo>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[CommonEventSubscribeInfo](arkts-basicservices-commoneventsubscribeinfo-commoneventsubscribeinfo-i.md)&gt; | Promise对象。返回订阅者的订阅信息。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.getSubscribeInfo().then((subscribeInfo: commonEventManager.CommonEventSubscribeInfo) => {
  console.info(`Succeeded in getting subscribe info, subscribe info is ${JSON.stringify(subscribeInfo)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get subscribe info. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.getSubscribeInfo().then((subscribeInfo: commonEventManager.CommonEventSubscribeInfo | null) => {
  console.info(`Succeeded in getting subscribe info, subscribe info is ${JSON.stringify(subscribeInfo)}`);
}).catch((err: BusinessError): void => {
  console.error(`Failed to get subscribe info. Code is ${err.code}, message is ${err.message}`);
});
```

## getSubscribeInfo

```TypeScript
getSubscribeInfo(): Promise<CommonEventSubscribeInfo|null>
```

获取订阅者的订阅信息。使用Promise异步回调。

**起始版本：** 23

<!--Device-CommonEventSubscriber-getSubscribeInfo(): Promise<CommonEventSubscribeInfo|null>--><!--Device-CommonEventSubscriber-getSubscribeInfo(): Promise<CommonEventSubscribeInfo|null>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[CommonEventSubscribeInfo](arkts-basicservices-commoneventsubscribeinfo-commoneventsubscribeinfo-i.md) \| null&gt; | Promise对象。返回订阅者的订阅信息。 |

## getSubscribeInfoSync

```TypeScript
getSubscribeInfoSync(): CommonEventSubscribeInfo
```

同步获取订阅者的订阅信息。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-getSubscribeInfoSync(): CommonEventSubscribeInfo--><!--Device-CommonEventSubscriber-getSubscribeInfoSync(): CommonEventSubscribeInfo-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CommonEventSubscribeInfo](arkts-basicservices-commoneventsubscribeinfo-commoneventsubscribeinfo-i.md) | 表示订阅者的订阅信息。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
let subscribeInfo1: commonEventManager.CommonEventSubscribeInfo = subscriber.getSubscribeInfoSync();
console.info(`Succeeded in getting subscribe info, subscribe info is ${JSON.stringify(subscribeInfo1)}`);
```

ArkTS-Sta示例：

```TypeScript
let getSubscribeInfo = subscriber.getSubscribeInfoSync();
console.info(`Succeeded in getting subscribe info, subscribe info is ${JSON.stringify(getSubscribeInfo)}`);
```

## getSubscribeInfoSync

```TypeScript
getSubscribeInfoSync(): CommonEventSubscribeInfo|null
```

同步获取订阅者的订阅信息。

**起始版本：** 23

<!--Device-CommonEventSubscriber-getSubscribeInfoSync(): CommonEventSubscribeInfo|null--><!--Device-CommonEventSubscriber-getSubscribeInfoSync(): CommonEventSubscribeInfo|null-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CommonEventSubscribeInfo](arkts-basicservices-commoneventsubscribeinfo-commoneventsubscribeinfo-i.md) | 表示订阅者的订阅信息。 |

## isOrderedCommonEvent

```TypeScript
isOrderedCommonEvent(callback: AsyncCallback<boolean>): void
```

查询当前公共事件是否为有序公共事件。使用callback异步回调。

**起始版本：** 23

<!--Device-CommonEventSubscriber-isOrderedCommonEvent(callback: AsyncCallback<boolean>): void--><!--Device-CommonEventSubscriber-isOrderedCommonEvent(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。当查询成功时，err为undefined，data为true表示有序公共事件，data为false表示不是有序公共事件；否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.isOrderedCommonEvent((err: BusinessError, isOrdered: boolean) => {
  if (err) {
    console.error(`isOrderedCommonEvent failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`isOrderedCommonEvent ${JSON.stringify(isOrdered)}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.isOrderedCommonEvent((err: BusinessError | null, isOrdered: boolean | undefined | null) => {
  if (err) {
    console.error(`isOrderedCommonEvent failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`isOrderedCommonEvent ${JSON.stringify(isOrdered)}`);
});
```

## isOrderedCommonEvent

```TypeScript
isOrderedCommonEvent(): Promise<boolean>
```

查询当前公共事件是否为有序公共事件。使用Promise异步回调。

**起始版本：** 23

<!--Device-CommonEventSubscriber-isOrderedCommonEvent(): Promise<boolean>--><!--Device-CommonEventSubscriber-isOrderedCommonEvent(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示有序公共事件；返回false表示无序公共事件。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.isOrderedCommonEvent().then((isOrdered: boolean) => {
  console.info(`isOrderedCommonEvent ${JSON.stringify(isOrdered)}`);
}).catch((err: BusinessError) => {
  console.error(`isOrderedCommonEvent failed, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.isOrderedCommonEvent().then((isOrdered: boolean) => {
  console.info(`isOrderedCommonEvent ${JSON.stringify(isOrdered)}`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`isOrderedCommonEvent failed, code is ${error.code}, message is ${error.message}`);
});
```

## isOrderedCommonEventSync

```TypeScript
isOrderedCommonEventSync(): boolean
```

同步查询当前公共事件是否为有序公共事件。

**起始版本：** 23

<!--Device-CommonEventSubscriber-isOrderedCommonEventSync(): boolean--><!--Device-CommonEventSubscriber-isOrderedCommonEventSync(): boolean-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示有序公共事件；返回false表示无序公共事件。 |

**示例**

```TypeScript
let isOrdered: boolean = subscriber.isOrderedCommonEventSync();
console.info(`isOrderedCommonEventSync ${JSON.stringify(isOrdered)}`);
```

## isStickyCommonEvent

```TypeScript
isStickyCommonEvent(callback: AsyncCallback<boolean>): void
```

查询当前公共事件是否为一个粘性公共事件。使用callback异步回调。

**起始版本：** 23

<!--Device-CommonEventSubscriber-isStickyCommonEvent(callback: AsyncCallback<boolean>): void--><!--Device-CommonEventSubscriber-isStickyCommonEvent(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。当查询成功时，err为undefined，data为true表示是粘性公共事件，data为false表示不是粘性公共事件；否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.isStickyCommonEvent((err: BusinessError, isSticky: boolean) => {
  if (err) {
    console.error(`isStickyCommonEvent failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`isStickyCommonEvent ${JSON.stringify(isSticky)}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.isStickyCommonEvent((err: BusinessError | null, isSticky: boolean | undefined | null) => {
  if (err) {
    console.error(`isStickyCommonEvent failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`isStickyCommonEvent ${JSON.stringify(isSticky)}`);
});
```

## isStickyCommonEvent

```TypeScript
isStickyCommonEvent(): Promise<boolean>
```

查询当前公共事件是否为一个粘性公共事件。使用Promise异步回调。

**起始版本：** 23

<!--Device-CommonEventSubscriber-isStickyCommonEvent(): Promise<boolean>--><!--Device-CommonEventSubscriber-isStickyCommonEvent(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示是粘性公共事件；返回false表示不是粘性公共事件。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.isStickyCommonEvent().then((isSticky: boolean) => {
  console.info(`isStickyCommonEvent ${JSON.stringify(isSticky)}`);
}).catch((err: BusinessError) => {
  console.error(`isStickyCommonEvent failed, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.isStickyCommonEvent().then((isSticky: boolean) => {
  console.info(`isStickyCommonEvent ${JSON.stringify(isSticky)}`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`isStickyCommonEvent failed, code is ${error.code}, message is ${error.message}`);
});
```

## isStickyCommonEventSync

```TypeScript
isStickyCommonEventSync(): boolean
```

同步检查当前公共事件是否为一个粘性公共事件。

**起始版本：** 23

<!--Device-CommonEventSubscriber-isStickyCommonEventSync(): boolean--><!--Device-CommonEventSubscriber-isStickyCommonEventSync(): boolean-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示是粘性公共事件；返回false表示不是粘性公共事件。 |

**示例**

```TypeScript
let isSticky: boolean = subscriber.isStickyCommonEventSync();
console.info(`isStickyCommonEventSync ${JSON.stringify(isSticky)}`);
```

## setCode

```TypeScript
setCode(code: int, callback: AsyncCallback<void>): void
```

设置有序公共事件传递的数据。使用callback异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-setCode(code: int, callback: AsyncCallback<void>): void--><!--Device-CommonEventSubscriber-setCode(code: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | int | 是 | 有序公共事件传递的数据。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当设置有序公共事件传递的数据成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.setCode(1, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set code. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting code.`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.setCode(1, (err: BusinessError | null) => {
  if (err) {
    console.error(`Failed to set code. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting code.`);
});
```

## setCode

```TypeScript
setCode(code: int): Promise<void>
```

设置有序公共事件传递的数据。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-setCode(code: int): Promise<void>--><!--Device-CommonEventSubscriber-setCode(code: int): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | int | 是 | 有序公共事件传递的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.setCode(1).then(() => {
  console.info(`Succeeded in setting code.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set code. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.setCode(1).then(() => {
  console.info(`Succeeded in setting code.`);
}).catch((err: Error): void  => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to set code. Code is ${error.code}, message is ${error.message}`);
});
```

## setCodeAndData

```TypeScript
setCodeAndData(code: int, data: string, callback: AsyncCallback<void>): void
```

设置有序公共事件传递的数据。使用callback异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-setCodeAndData(code: int, data: string, callback: AsyncCallback<void>): void--><!--Device-CommonEventSubscriber-setCodeAndData(code: int, data: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | int | 是 | 有序公共事件传递的数据。 |
| data | string | 是 | 有序公共事件传递的数据，长度不超过65536字符，若超过限制，接口设置失效。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当设置有序公共事件传递的数据成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.setCodeAndData(1, 'publish_data_changed', (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set code and data. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting code and data.`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.setCodeAndData(1, 'publish_data_changed', (err: BusinessError | null) => {
  if (err) {
    console.error(`Failed to set code and data. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting code and data.`);
});
```

## setCodeAndData

```TypeScript
setCodeAndData(code: int, data: string): Promise<void>
```

设置有序公共事件传递的数据。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-setCodeAndData(code: int, data: string): Promise<void>--><!--Device-CommonEventSubscriber-setCodeAndData(code: int, data: string): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | int | 是 | 有序公共事件传递的数据。 |
| data | string | 是 | 有序公共事件传递的数据，长度不超过65536字符，若超过限制，接口设置失效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.setCodeAndData(1, 'publish_data_changed').then(() => {
  console.info(`Succeeded in setting code and data.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set code and data. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.setCodeAndData(1, 'publish_data_changed').then(() => {
  console.info(`Succeeded in setting code and data.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to set code and data. Code is ${error.code}, message is ${error.message}`);
});
```

## setCodeAndDataSync

```TypeScript
setCodeAndDataSync(code: int, data: string): void
```

同步设置有序公共事件传递的数据。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-setCodeAndDataSync(code: int, data: string): void--><!--Device-CommonEventSubscriber-setCodeAndDataSync(code: int, data: string): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | int | 是 | 有序公共事件传递的数据。 |
| data | string | 是 | 有序公共事件传递的数据，长度不超过65536字符，若超过限制，接口设置失效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
try {
  subscriber.setCodeAndDataSync(1, 'publish_data_changed');
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to set code and data. Code is ${err.code}, message is ${err.message}`);
}
```

## setCodeSync

```TypeScript
setCodeSync(code: int): void
```

同步设置有序公共事件传递的数据。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-setCodeSync(code: int): void--><!--Device-CommonEventSubscriber-setCodeSync(code: int): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | int | 是 | 有序公共事件传递的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
try {
  subscriber.setCodeSync(1);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to set code. Code is ${err.code}, message is ${err.message}`);
}
```

## setData

```TypeScript
setData(data: string, callback: AsyncCallback<void>): void
```

设置有序公共事件传递的数据。使用callback异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-setData(data: string, callback: AsyncCallback<void>): void--><!--Device-CommonEventSubscriber-setData(data: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 | 有序公共事件传递的数据，长度不超过65536字符，若超过限制，接口设置失效。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当设置有序公共事件传递的数据成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.setData('publish_data_changed', (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set data. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting data.`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.setData('publish_data_changed', (err: BusinessError | null) => {
  if (err) {
    console.error(`Failed to set data. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting data.`);
});
```

## setData

```TypeScript
setData(data: string): Promise<void>
```

设置有序公共事件传递的数据。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-setData(data: string): Promise<void>--><!--Device-CommonEventSubscriber-setData(data: string): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 | 有序公共事件传递的数据，长度不超过65536字符，若超过限制，接口设置失效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
subscriber.setData('publish_data_changed').then(() => {
  console.info(`Succeeded in setting data.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set data. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
subscriber.setData('publish_data_changed').then(() => {
  console.info(`Succeeded in setting data.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to set data. Code is ${error.code}, message is ${error.message}`);
});
```

## setDataSync

```TypeScript
setDataSync(data: string): void
```

同步设置有序公共事件传递的数据。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-setDataSync(data: string): void--><!--Device-CommonEventSubscriber-setDataSync(data: string): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 | 有序公共事件传递的数据，长度不超过65536字符，若超过限制，接口设置失效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
try {
  subscriber.setDataSync('publish_data_changed');
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to set data. Code is ${err.code}, message is ${err.message}`);
}
```

