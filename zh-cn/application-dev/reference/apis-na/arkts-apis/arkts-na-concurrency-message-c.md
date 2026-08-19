# Message(定义ArkTS的EAWorker消息)

表示消息队列中的一个消息，可携带数据和回调函数，发送至MessageHandler进行处理。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-concurrency-export class Message--><!--Device-concurrency-export class Message-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(handler: concurrency.MessageHandler)
```

构造一个Message实例，需要传入MessageHandler来指定消息处理的逻辑。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Message-constructor(handler: concurrency.MessageHandler)--><!--Device-Message-constructor(handler: concurrency.MessageHandler)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | concurrency.MessageHandler | 是 | 处理该消息的MessageHandler。 |

## constructor

```TypeScript
constructor(what: int, handler: concurrency.MessageHandler)
```

构造一个Message实例，需要传入消息标识符和MessageHandler。未指定标识符时默认值为-1000000，避免使用该值作为自定义标识符。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Message-constructor(what: int, handler: concurrency.MessageHandler)--><!--Device-Message-constructor(what: int, handler: concurrency.MessageHandler)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| what | int | 是 | 消息标识符，用于表明消息的类型或目的，由开发者自行约定。 <br>该值应为整数。 |
| handler | concurrency.MessageHandler | 是 | 处理该消息的MessageHandler。 |

## constructor

```TypeScript
constructor(what: int, obj: Any, handler: concurrency.MessageHandler)
```

构造一个Message实例，需要传入消息标识符、数据对象和MessageHandler。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Message-constructor(what: int, obj: Any, handler: concurrency.MessageHandler)--><!--Device-Message-constructor(what: int, obj: Any, handler: concurrency.MessageHandler)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| what | int | 是 | 消息标识符。 <br>该值应为整数。 |
| obj | Any | 是 | 消息携带的数据对象。 |
| handler | concurrency.MessageHandler | 是 | 处理该消息的MessageHandler。 |

## constructor

```TypeScript
constructor(callback: () => void, handler: concurrency.MessageHandler)
```

构造一个Message实例，需要传入回调函数和MessageHandler。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Message-constructor(callback: () => void, handler: concurrency.MessageHandler)--><!--Device-Message-constructor(callback: () => void, handler: concurrency.MessageHandler)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; void | 是 | 消息处理时执行的回调函数。 |
| handler | concurrency.MessageHandler | 是 | 处理该消息的MessageHandler。 |

## equals

```TypeScript
equals(other: concurrency.Message): boolean
```

判断当前消息是否与另一个消息相等。 如果两个消息的目标处理器不同，则返回false；对于回调消息，会继续比较回调函数是否相同； 对于携带标识符的消息，会继续比较标识符和数据对象是否相同。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Message-equals(other: concurrency.Message): boolean--><!--Device-Message-equals(other: concurrency.Message): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| other | [concurrency.Message](arkts-na-concurrency-message-c.md) | 是 | 用于比较的另一个消息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 两个消息相等则返回true，否则返回false。 |

## getCallback

```TypeScript
getCallback(): (() => void) | undefined
```

返回消息的回调函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Message-getCallback(): (() => void) | undefined--><!--Device-Message-getCallback(): (() => void) | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| (() =&gt; void) | 消息的回调函数，未设置时返回undefined。 |

## getObject

```TypeScript
getObject(): Any
```

返回消息携带的数据对象。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Message-getObject(): Any--><!--Device-Message-getObject(): Any-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Any | 消息携带的数据对象。 |

## getTarget

```TypeScript
getTarget(): concurrency.MessageHandler
```

返回消息的目标处理器。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Message-getTarget(): concurrency.MessageHandler--><!--Device-Message-getTarget(): concurrency.MessageHandler-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| concurrency.MessageHandler | 目标处理器。 |

## getWhat

```TypeScript
getWhat(): int
```

返回消息的标识符。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Message-getWhat(): int--><!--Device-Message-getWhat(): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 消息的标识符。 |

## sendToTarget

```TypeScript
sendToTarget(): void
```

将消息发送到构造时传入的目标处理器中进行处理。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Message-sendToTarget(): void--><!--Device-Message-sendToTarget(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

