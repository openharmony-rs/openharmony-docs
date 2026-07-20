# CommonEventSubscriber

表示公共事件的订阅者。

**起始版本：** 7

<!--Device-unnamed-export interface CommonEventSubscriber--><!--Device-unnamed-export interface CommonEventSubscriber-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

<a id="abortcommonevent"></a>
## abortCommonEvent

```TypeScript
abortCommonEvent(callback: AsyncCallback<void>): void
```

添加有序公共事件的中止状态。当该接口与[finishCommonEvent](arkts-basicservices-commoneventsubscriber-commoneventsubscriber-i.md#finishcommonevent-1)配合使用时，可以中止当前的有序公共事件，使该公共事件不再向下一个订阅者传递。使用callback异步回调。

**起始版本：** 7

<!--Device-CommonEventSubscriber-abortCommonEvent(callback: AsyncCallback<void>): void--><!--Device-CommonEventSubscriber-abortCommonEvent(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当添加有序公共事件中止状态成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="abortcommonevent-1"></a>
## abortCommonEvent

```TypeScript
abortCommonEvent(): Promise<void>
```

添加有序公共事件的中止状态。当该接口与[finishCommonEvent](arkts-basicservices-commoneventsubscriber-commoneventsubscriber-i.md#finishcommonevent-1)配合使用时，可以中止当前的有序公共事件，使该公共事件不再向下一个订阅者传递。使用Promise异步回调。

**起始版本：** 7

<!--Device-CommonEventSubscriber-abortCommonEvent(): Promise<void>--><!--Device-CommonEventSubscriber-abortCommonEvent(): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

<a id="abortcommoneventsync"></a>
## abortCommonEventSync

```TypeScript
abortCommonEventSync(): void
```

添加有序公共事件的中止状态。当该接口与[finishCommonEvent](arkts-basicservices-commoneventsubscriber-commoneventsubscriber-i.md#finishcommonevent-1)配合使用时，可以中止当前的有序公共事件，使该公共事件不再向下一个订阅者传递。

**起始版本：** 10

<!--Device-CommonEventSubscriber-abortCommonEventSync(): void--><!--Device-CommonEventSubscriber-abortCommonEventSync(): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

<a id="clearabortcommonevent"></a>
## clearAbortCommonEvent

```TypeScript
clearAbortCommonEvent(callback: AsyncCallback<void>): void
```

清理有序公共事件的中止状态。当该接口与[finishCommonEvent](arkts-basicservices-commoneventsubscriber-commoneventsubscriber-i.md#finishcommonevent-1)配合使用时，可以使该公共事件继续向下一个订阅者传递。使用callback异步回调。

**起始版本：** 7

<!--Device-CommonEventSubscriber-clearAbortCommonEvent(callback: AsyncCallback<void>): void--><!--Device-CommonEventSubscriber-clearAbortCommonEvent(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当清理有序公共事件中止状态成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="clearabortcommonevent-1"></a>
## clearAbortCommonEvent

```TypeScript
clearAbortCommonEvent(): Promise<void>
```

清理有序公共事件的中止状态。当该接口与[finishCommonEvent](arkts-basicservices-commoneventsubscriber-commoneventsubscriber-i.md#finishcommonevent-1)配合使用时，可以使该公共事件继续向下一个订阅者传递。使用Promise异步回调。

**起始版本：** 7

<!--Device-CommonEventSubscriber-clearAbortCommonEvent(): Promise<void>--><!--Device-CommonEventSubscriber-clearAbortCommonEvent(): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

<a id="clearabortcommoneventsync"></a>
## clearAbortCommonEventSync

```TypeScript
clearAbortCommonEventSync(): void
```

清理有序公共事件的中止状态。当该接口与[finishCommonEvent](arkts-basicservices-commoneventsubscriber-commoneventsubscriber-i.md#finishcommonevent-1)配合使用时，可以使该公共事件继续向下一个订阅者传递。

**起始版本：** 10

<!--Device-CommonEventSubscriber-clearAbortCommonEventSync(): void--><!--Device-CommonEventSubscriber-clearAbortCommonEventSync(): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

<a id="finishcommonevent"></a>
## finishCommonEvent

```TypeScript
finishCommonEvent(callback: AsyncCallback<void>): void
```

用于订阅者结束对当前有序公共事件的处理。使用callback异步回调。

**起始版本：** 9

<!--Device-CommonEventSubscriber-finishCommonEvent(callback: AsyncCallback<void>): void--><!--Device-CommonEventSubscriber-finishCommonEvent(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当订阅者结束当前有序公共事件成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="finishcommonevent-1"></a>
## finishCommonEvent

```TypeScript
finishCommonEvent(): Promise<void>
```

用于订阅者结束对当前有序公共事件的处理。使用Promise异步回调。

**起始版本：** 9

<!--Device-CommonEventSubscriber-finishCommonEvent(): Promise<void>--><!--Device-CommonEventSubscriber-finishCommonEvent(): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

<a id="getabortcommonevent"></a>
## getAbortCommonEvent

```TypeScript
getAbortCommonEvent(callback: AsyncCallback<boolean>): void
```

获取当前有序公共事件是否处于中止状态。使用callback异步回调。

**起始版本：** 7

<!--Device-CommonEventSubscriber-getAbortCommonEvent(callback: AsyncCallback<boolean>): void--><!--Device-CommonEventSubscriber-getAbortCommonEvent(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示当前有序公共事件处于中止状态；返回false表示当前有序公共事件没有处于中止状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="getabortcommonevent-1"></a>
## getAbortCommonEvent

```TypeScript
getAbortCommonEvent(): Promise<boolean>
```

获取当前有序公共事件是否处于中止状态。使用Promise异步回调。

**起始版本：** 7

<!--Device-CommonEventSubscriber-getAbortCommonEvent(): Promise<boolean>--><!--Device-CommonEventSubscriber-getAbortCommonEvent(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示当前有序公共事件处于中止状态；返回false表示当前有序公共事件没有处于中止状态。 |

<a id="getabortcommoneventsync"></a>
## getAbortCommonEventSync

```TypeScript
getAbortCommonEventSync(): boolean
```

获取当前有序公共事件是否处于中止状态。

**起始版本：** 10

<!--Device-CommonEventSubscriber-getAbortCommonEventSync(): boolean--><!--Device-CommonEventSubscriber-getAbortCommonEventSync(): boolean-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示当前有序公共事件处于中止状态；返回false表示当前有序公共事件没有处于中止状态。 |

<a id="getcode"></a>
## getCode

```TypeScript
getCode(callback: AsyncCallback<number>): void
```

获取有序公共事件传递的数据（number类型）。使用callback异步回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-getCode(callback: AsyncCallback<int>): void--><!--Device-CommonEventSubscriber-getCode(callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。返回有序公共事件传递的数据（number类型）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="getcode-1"></a>
## getCode

```TypeScript
getCode(): Promise<number>
```

获取有序公共事件传递的数据（number类型）。使用Promise异步回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-getCode(): Promise<int>--><!--Device-CommonEventSubscriber-getCode(): Promise<int>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回有序公共事件传递的数据（number类型）。 |

<a id="getcodesync"></a>
## getCodeSync

```TypeScript
getCodeSync(): number
```

获取有序公共事件传递的数据（number类型）。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-getCodeSync(): int--><!--Device-CommonEventSubscriber-getCodeSync(): int-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 表示有序公共事件传递的数据（number类型）。 |

<a id="getdata"></a>
## getData

```TypeScript
getData(callback: AsyncCallback<string>): void
```

获取有序公共事件传递的数据（string类型）。使用callback异步回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-getData(callback: AsyncCallback<string>): void--><!--Device-CommonEventSubscriber-getData(callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。返回有序公共事件传递的数据（string类型）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="getdata-1"></a>
## getData

```TypeScript
getData(): Promise<string>
```

获取有序公共事件传递的数据（string类型）。使用Promise异步回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-getData(): Promise<string>--><!--Device-CommonEventSubscriber-getData(): Promise<string>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。返回有序公共事件传递的数据（string类型）。 |

<a id="getdatasync"></a>
## getDataSync

```TypeScript
getDataSync(): string
```

获取有序公共事件传递的数据（string类型）。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-getDataSync(): string--><!--Device-CommonEventSubscriber-getDataSync(): string-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 有序公共事件传递的数据（string类型）。 |

<a id="getsubscribeinfo"></a>
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
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;CommonEventSubscribeInfo&gt; | 是 | 回调函数。返回订阅者的订阅信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="getsubscribeinfo-1"></a>
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
| Promise&lt;CommonEventSubscribeInfo&gt; | Promise对象。返回订阅者的订阅信息。 |

<a id="getsubscribeinfosync"></a>
## getSubscribeInfoSync

```TypeScript
getSubscribeInfoSync(): CommonEventSubscribeInfo
```

获取订阅者的订阅信息。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-getSubscribeInfoSync(): CommonEventSubscribeInfo--><!--Device-CommonEventSubscriber-getSubscribeInfoSync(): CommonEventSubscribeInfo-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CommonEventSubscribeInfo](arkts-basicservices-commoneventmanager-commoneventsubscribeinfo-t.md) | 表示订阅者的订阅信息。 |

<a id="isorderedcommonevent"></a>
## isOrderedCommonEvent

```TypeScript
isOrderedCommonEvent(callback: AsyncCallback<boolean>): void
```

查询当前公共事件是否为有序公共事件。使用callback异步回调。

**起始版本：** 7

<!--Device-CommonEventSubscriber-isOrderedCommonEvent(callback: AsyncCallback<boolean>): void--><!--Device-CommonEventSubscriber-isOrderedCommonEvent(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示有序公共事件；返回false表示无序公共事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="isorderedcommonevent-1"></a>
## isOrderedCommonEvent

```TypeScript
isOrderedCommonEvent(): Promise<boolean>
```

查询当前公共事件是否为有序公共事件。使用Promise异步回调。

**起始版本：** 7

<!--Device-CommonEventSubscriber-isOrderedCommonEvent(): Promise<boolean>--><!--Device-CommonEventSubscriber-isOrderedCommonEvent(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示有序公共事件；返回false表示无序公共事件。 |

<a id="isorderedcommoneventsync"></a>
## isOrderedCommonEventSync

```TypeScript
isOrderedCommonEventSync(): boolean
```

查询当前公共事件是否为有序公共事件。

**起始版本：** 10

<!--Device-CommonEventSubscriber-isOrderedCommonEventSync(): boolean--><!--Device-CommonEventSubscriber-isOrderedCommonEventSync(): boolean-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示有序公共事件；返回false表示无序公共事件。 |

<a id="isstickycommonevent"></a>
## isStickyCommonEvent

```TypeScript
isStickyCommonEvent(callback: AsyncCallback<boolean>): void
```

检查当前公共事件是否为一个粘性事件。使用callback异步回调。

**起始版本：** 7

<!--Device-CommonEventSubscriber-isStickyCommonEvent(callback: AsyncCallback<boolean>): void--><!--Device-CommonEventSubscriber-isStickyCommonEvent(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示是粘性公共事件；返回false表示不是粘性公共事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="isstickycommonevent-1"></a>
## isStickyCommonEvent

```TypeScript
isStickyCommonEvent(): Promise<boolean>
```

检查当前公共事件是否为一个粘性事件。使用Promise异步回调。

**起始版本：** 7

<!--Device-CommonEventSubscriber-isStickyCommonEvent(): Promise<boolean>--><!--Device-CommonEventSubscriber-isStickyCommonEvent(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示是粘性公共事件；返回false表示不是粘性公共事件。 |

<a id="isstickycommoneventsync"></a>
## isStickyCommonEventSync

```TypeScript
isStickyCommonEventSync(): boolean
```

检查当前公共事件是否为一个粘性事件。

**起始版本：** 10

<!--Device-CommonEventSubscriber-isStickyCommonEventSync(): boolean--><!--Device-CommonEventSubscriber-isStickyCommonEventSync(): boolean-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示是粘性公共事件；返回false表示不是粘性公共事件。 |

<a id="setcode"></a>
## setCode

```TypeScript
setCode(code: number, callback: AsyncCallback<void>): void
```

设置有序公共事件传递的数据（number类型）。使用callback异步回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-setCode(code: int, callback: AsyncCallback<void>): void--><!--Device-CommonEventSubscriber-setCode(code: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 有序公共事件传递的数据（number类型）。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置有序公共事件传递的数据（number类型）成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="setcode-1"></a>
## setCode

```TypeScript
setCode(code: number): Promise<void>
```

设置有序公共事件传递的数据（number类型）。使用Promise异步回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-setCode(code: int): Promise<void>--><!--Device-CommonEventSubscriber-setCode(code: int): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 有序公共事件传递的数据（number类型）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="setcodeanddata"></a>
## setCodeAndData

```TypeScript
setCodeAndData(code: number, data: string, callback: AsyncCallback<void>): void
```

设置有序公共事件数据。使用callback异步回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-setCodeAndData(code: int, data: string, callback: AsyncCallback<void>): void--><!--Device-CommonEventSubscriber-setCodeAndData(code: int, data: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 有序公共事件传递的数据（number类型）。 |
| data | string | 是 | 有序公共事件传递的数据（string类型）。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置有序公共事件传递的数据成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="setcodeanddata-1"></a>
## setCodeAndData

```TypeScript
setCodeAndData(code: number, data: string): Promise<void>
```

设置有序公共事件传递的数据。使用Promise异步回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-setCodeAndData(code: int, data: string): Promise<void>--><!--Device-CommonEventSubscriber-setCodeAndData(code: int, data: string): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 有序公共事件传递的数据（number类型）。 |
| data | string | 是 | 有序公共事件传递的数据（string类型）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="setcodeanddatasync"></a>
## setCodeAndDataSync

```TypeScript
setCodeAndDataSync(code: number, data: string): void
```

设置有序公共事件传递的数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-setCodeAndDataSync(code: int, data: string): void--><!--Device-CommonEventSubscriber-setCodeAndDataSync(code: int, data: string): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 有序公共事件传递的数据（number类型）。 |
| data | string | 是 | 有序公共事件传递的数据（string类型）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="setcodesync"></a>
## setCodeSync

```TypeScript
setCodeSync(code: number): void
```

设置有序公共事件传递的数据（number类型）。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-setCodeSync(code: int): void--><!--Device-CommonEventSubscriber-setCodeSync(code: int): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 有序公共事件传递的数据（number类型）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="setdata"></a>
## setData

```TypeScript
setData(data: string, callback: AsyncCallback<void>): void
```

设置有序公共事件传递的数据（string类型）。使用callback异步回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-setData(data: string, callback: AsyncCallback<void>): void--><!--Device-CommonEventSubscriber-setData(data: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 | 有序公共事件传递的数据（string类型）。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置有序公共事件传递的数据（string类型）成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="setdata-1"></a>
## setData

```TypeScript
setData(data: string): Promise<void>
```

设置有序公共事件传递的数据（string类型）。使用Promise异步回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-setData(data: string): Promise<void>--><!--Device-CommonEventSubscriber-setData(data: string): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 | 有序公共事件传递的数据（string类型）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="setdatasync"></a>
## setDataSync

```TypeScript
setDataSync(data: string): void
```

设置有序公共事件传递的数据（string类型）。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscriber-setDataSync(data: string): void--><!--Device-CommonEventSubscriber-setDataSync(data: string): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 | 有序公共事件传递的数据（string类型）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

