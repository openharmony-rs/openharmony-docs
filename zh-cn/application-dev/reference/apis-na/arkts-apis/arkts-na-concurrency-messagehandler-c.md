# MessageHandler(定义ArkTS的EAWorker消息处理器)

处理消息并提供消息调度能力。不同消息可由不同的MessageHandler处理。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-concurrency-export class MessageHandler--><!--Device-concurrency-export class MessageHandler-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(handler: (message: concurrency.Message) => void, worker: EAWorker | undefined = EAWorker.current())
```

构造一个MessageHandler实例，需要传入消息处理函数，可选传入EAWorker实例。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MessageHandler-constructor(handler: (message: concurrency.Message) => void, worker: EAWorker | undefined = EAWorker.current())--><!--Device-MessageHandler-constructor(handler: (message: concurrency.Message) => void, worker: EAWorker | undefined = EAWorker.current())-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | (message: concurrency.Message) =&gt; void | 是 | 处理消息的函数。 |
| worker | [EAWorker](arkts-na-eaworker-c.md) \| undefined | 是 | 与该处理器关联的Worker，默认为当前线程的Worker。 |

## getWorker

```TypeScript
getWorker(): EAWorker
```

返回与该处理器关联的Worker。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MessageHandler-getWorker(): EAWorker--><!--Device-MessageHandler-getWorker(): EAWorker-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EAWorker](arkts-na-eaworker-c.md) | 关联的Worker实例。 |

## hasCallbacks

```TypeScript
hasCallbacks(callback: () => void): boolean
```

检查处理器中是否有指定的回调函数在等待执行。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MessageHandler-hasCallbacks(callback: () => void): boolean--><!--Device-MessageHandler-hasCallbacks(callback: () => void): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; void | 是 | 要检查的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 存在则返回true，否则返回false。 |

## hasMessages

```TypeScript
hasMessages(what: int): boolean
```

检查处理器中是否有指定标识符的消息。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MessageHandler-hasMessages(what: int): boolean--><!--Device-MessageHandler-hasMessages(what: int): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| what | int | 是 | 要检查的消息标识符。 <br>该值应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 存在则返回true，否则返回false。 |

## hasMessages

```TypeScript
hasMessages(what: int, obj: Any): boolean
```

检查处理器中是否有指定标识符和数据对象的消息。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MessageHandler-hasMessages(what: int, obj: Any): boolean--><!--Device-MessageHandler-hasMessages(what: int, obj: Any): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| what | int | 是 | 要检查的消息标识符。 <br>该值应为整数。 |
| obj | Any | 是 | 要检查的数据对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 存在则返回true，否则返回false。 |

## post

```TypeScript
post(callback: () => void): boolean
```

构造消息并添加到消息队列中执行。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MessageHandler-post(callback: () => void): boolean--><!--Device-MessageHandler-post(callback: () => void): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; void | 是 | 要执行的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功添加到消息队列则返回true，否则返回false。 |

## removeCallbacks

```TypeScript
removeCallbacks(callback: () => void): boolean
```

从消息队列中移除匹配指定回调函数的待执行回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MessageHandler-removeCallbacks(callback: () => void): boolean--><!--Device-MessageHandler-removeCallbacks(callback: () => void): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; void | 是 | 要移除的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功移除则返回true，否则返回false。 |

## removeMessages

```TypeScript
removeMessages(what: int): boolean
```

从消息队列中移除指定标识符的待执行消息。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MessageHandler-removeMessages(what: int): boolean--><!--Device-MessageHandler-removeMessages(what: int): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| what | int | 是 | 要移除的消息标识符。 <br>该值应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功移除则返回true，否则返回false。 |

## removeMessages

```TypeScript
removeMessages(what: int, obj: Any): boolean
```

从消息队列中移除指定标识符和数据对象的待执行消息。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MessageHandler-removeMessages(what: int, obj: Any): boolean--><!--Device-MessageHandler-removeMessages(what: int, obj: Any): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| what | int | 是 | 要移除的消息标识符。 <br>该值应为整数。 |
| obj | Any | 是 | 要匹配的数据对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功移除则返回true，否则返回false。 |

## sendEmptyMessage

```TypeScript
sendEmptyMessage(what: int): boolean
```

发送指定标识符的空消息。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MessageHandler-sendEmptyMessage(what: int): boolean--><!--Device-MessageHandler-sendEmptyMessage(what: int): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| what | int | 是 | 要发送的消息标识符。 <br>该值应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功发送则返回true，否则返回false。 |

## sendMessage

```TypeScript
sendMessage(message: concurrency.Message): boolean
```

将消息添加到消息队列。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MessageHandler-sendMessage(message: concurrency.Message): boolean--><!--Device-MessageHandler-sendMessage(message: concurrency.Message): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | concurrency.Message | 是 | 要发送的消息对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功发送则返回true，否则返回false。 |

