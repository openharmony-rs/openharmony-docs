# MessageHandler (EAWorker消息处理器)
MessageHandler用于定义消息（[Message](./message.md)）的处理逻辑。不同消息可以由不同的MessageHandler处理。

## constructor
constructor(handler: (msg:Message)=>void, worker?: EAWorker = EAWorker.current())

MessageHandler的构造器用于创建MessageHandler实例，需要传入消息处理函数，可选传入[EAWorker](./eaworker_managed.md)实例。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数：**
|参数名|类型|必填|说明|
|-----|----|--|----|
|handler|(msg:Message)=>void|是|消息处理函数，用于处理接收到的消息。|
|worker|[EAWorker](./eaworker_managed.md)|否|[EAWorker](./eaworker_managed.md)实例，默认为当前线程的[EAWorker](./eaworker_managed.md)实例。|

**示例：**
```ts
let eaw = new EAWorker();
let handler = new concurrency.MessageHandler((msg: concurrency.Message)=>{
    console.info("message type: ", msg.getWhat());
}, eaw);
```

## hasCallbacks
hasCallbacks(callback: ()=>void): boolean

查询当前MessageHandler对应的[EAWorker](./eaworker_managed.md)中是否存在由callback构造的消息。如果存在，返回true；否则，返回false。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数：**
|参数名|类型|必填|说明|
|-----|----|--|----|
|callback|()=>void|是|查询的消息中的回调函数。|

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| boolean   | 如果存在由指定的回调函数构造的消息则返回true，否则返回false。 |

**示例：** 
```ts
let eaw = new EAWorker();
let handler = new concurrency.MessageHandler((msg: concurrency.Message)=>{
    console.info("message type: ", msg.getWhat());
}, eaw);

let callback = ()=> {
    console.info("this is callback")
}

let msg = new concurrency.Message(callback, handler);
handler.sendMessage(msg);

console.info("has callback: ", handler.hasCallbacks(callback));// has callback: true

```

## hasMessages
hasMessages(what: int): boolean

检查消息中是否包含指定的标识符。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数：**
|参数名|类型|必填|说明|
|-----|----|--|----|
|what|int|是|指定的消息标识符。|

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| boolean   | 如果包含指定标识符的消息则返回true，否则返回false。 |

**示例：**
```ts
let eaw = new EAWorker();
let handler = new concurrency.MessageHandler((msg: concurrency.Message)=>{
    console.info("message type: ", msg.getWhat());
}, eaw);

let msg = new concurrency.Message(1, handler);
handler.sendMessage(msg);

console.info("has message: ", handler.hasMessages(1));// has message: true

```

## hasMessages
hasMessages(what: int, obj: Object): boolean

检查消息中是否包含指定的标识符和数据对象。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数：**
|参数名|类型|必填|说明|
|-----|----|--|----|
|what|int|是|消息标识符。|
|obj|Object|是|消息数据对象。|

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| boolean   | 如果包含指定标识符和数据对象构造的消息则返回true，否则返回false。 |

**示例：**
```ts
let eaw = new EAWorker();
let handler = new concurrency.MessageHandler((msg: concurrency.Message)=>{
    console.info("message type: ", msg.getWhat());
}, eaw);

let msg = new concurrency.Message(1, "test", handler);
handler.sendMessage(msg);

console.info("has message: ", handler.hasMessages(1, "test"));// has message: true

eaw.start();
eaw.join();
```

## post
post(callback: ()=>void): boolean

构造消息并添加到消息队列中执行。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数：**
|参数名|类型|必填|说明|
|-----|----|--|----|
|callback|()=>void|是|需要执行的回调函数。|

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| boolean   | 如果成功添加到消息队列则返回true，否则返回false。 |

**示例：**
```ts
let eaw = new EAWorker()
eaw.start();
let handler = new concurrency.MessageHandler((msg: concurrency.Message)=>{
    console.info("message get");
}, eaw);

handler.post(()=>{
    console.info("post task executed");
});
eaw.join();
```

## removeCallbacks
removeCallbacks(callback: ()=>void): boolean

从消息队列中删除指定的回调函数构造的消息。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数：**
|参数名|类型|必填|说明|
|-----|----|--|----|
|callback|()=>void|是|要移除的消息中的回调函数。|

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| boolean   | 如果成功移除消息则返回true，否则返回false。 |

**示例：**
```ts
let eaw = new EAWorker();
eaw.start();
let handler = new concurrency.MessageHandler((msg: concurrency.Message)=>{
    console.info("message type: ", msg.getWhat());
}, eaw);

let msg1 = new concurrency.Message(1, handler);
let msg2 = new concurrency.Message(2, handler);
let callback = ()=> {
    handler.sendMessage(msg1);
    handler.sendMessage(msg2);
    console.info("hasMessage 1: " + handler.hasMessages(1));// true
    console.info("hasMessage 2: " + handler.hasMessages(2));// true

    handler.removeMessages(1);
    handler.removeMessages(2);

    console.info("hasMessage 1: " + handler.hasMessages(1));// false
    console.info("hasMessage 2: " + handler.hasMessages(2));// false
}

let msg = new concurrency.Message(callback, handler);
handler.sendMessage(msg);

console.info("has callback: ", handler.hasCallbacks(callback));// has callback: true
eaw.join();
```

## removeMessages
removeMessages(what: int): boolean

从消息队列中移除指定标识符的消息。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数：**
|参数名|类型|必填|说明|
|-----|----|--|----|
|what|int|是|消息标识符。|

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| boolean   | 如果成功移除消息则返回true，否则返回false。 |

**示例：**
```ts
let eaw = new EAWorker();
eaw.start();
let handler = new concurrency.MessageHandler((msg: concurrency.Message)=>{
    console.info("message type: ", msg.getWhat());
}, eaw);

let msg1 = new concurrency.Message(1, handler);
let callback = ()=> {
    handler.sendMessage(msg1);
    console.info("hasMessage 1: " + handler.hasMessages(1, "test"));// true
    handler.removeMessages(1);
    console.info("hasMessage 1: " + handler.hasMessages(1, "test"));// false
}

let msg = new concurrency.Message(callback, handler);
handler.sendMessage(msg);

console.info("has callback: ", handler.hasCallbacks(callback));// has callback: true
eaw.join();
```

## removeMessages
removeMessages(what: int, obj: Object): boolean

从消息队列中移除指定标识符和数据对象构建的消息。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数：**
|参数名|类型|必填|说明|
|-----|----|--|----|
|what|int|是|消息标识符。|
|obj|Object|是|消息数据对象。|

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| boolean   | 如果成功移除消息则返回true，否则返回false。 |

**示例：**
```ts
let eaw = new EAWorker();
eaw.start();
let handler = new concurrency.MessageHandler((msg: concurrency.Message)=>{
    console.info("message type: ", msg.getWhat());
}, eaw);

let msg1 = new concurrency.Message(1, "test", handler);
let callback = ()=> {
    handler.sendMessage(msg1);
    console.info("hasMessage 1: " + handler.hasMessages(1, "test"));// true
    handler.removeMessages(1, "test");
    console.info("hasMessage 1: " + handler.hasMessages(1, "test"));// false
}

let msg = new concurrency.Message(callback, handler);
handler.sendMessage(msg);

console.info("has callback: ", handler.hasCallbacks(callback));// has callback: true
eaw.join();
```

## sendEmptyMessage
sendEmptyMessage(what: int): boolean

向消息队列发送一个空消息。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数：**
|参数名|类型|必填|说明|
|-----|----|--|----|
|what|int|是|消息标识符。|

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| boolean   | 如果成功发送消息则返回true，否则返回false。 |

**示例：**
```ts
let eaw = new EAWorker();
eaw.start();
let handler = new concurrency.MessageHandler((msg: concurrency.Message)=>{
    console.info("message type: ", msg.getWhat());// message type: 3
}, eaw);

handler.sendEmptyMessage(3)

eaw.join();
```

## sendMessage
sendMessage(msg: Message): boolean

将消息添加到消息队列。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数：**
|参数名|类型|必填|说明|
|-----|----|--|----|
|msg|[Message](./message.md#constructor)|是|要发送的消息对象。|

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| boolean   | 如果成功发送消息则返回true，否则返回false。 |

**示例：**
```ts
let eaw = new EAWorker();
eaw.start();
let handler = new concurrency.MessageHandler((msg: concurrency.Message)=>{
    console.info("message type: ", msg.getWhat());// message type: 1
    console.info("message obj: ", msg.getObject());// message obj: test
}, eaw);

let msg = new concurrency.Message(1, "test", handler);
handler.sendMessage(msg);

eaw.join();
```

## getWorker
getWorker(): EAWorker
获取当前MessageHandler关联的[EAWorker](./eaworker_managed.md)。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| [EAWorker](./eaworker_managed.md)   | 返回当前MessageHandler关联的[EAWorker](./eaworker_managed.md)实例。 |

**示例：**
```ts
let eaw = new EAWorker();
eaw.start();
let handler = new concurrency.MessageHandler((msg: concurrency.Message)=>{
    console.info("message type: ", msg.getWhat());
}, eaw);

let target = handler.getWorker();

eaw.join();
```
