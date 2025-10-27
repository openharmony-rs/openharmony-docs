# Message (EAWorker消息)
Message表示消息队列中的一个消息，消息可以携带数据和回调函数。构造消息时需要指定[MessageHandler](./message_handler.md)来指定消息处理的逻辑。

## constructor
constructor(handler: MessageHandler)

Message的构造器，用于构造消息实例，需要传入[MessageHandler](./message_handler.md)来指定消息处理的逻辑。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数：**
|参数名|类型|必填|说明|
|-----|----|--|----|
|handler|[MessageHandler](./message_handler.md)|是|消息处理器，用于指定消息处理的逻辑。|

**示例：**
```ts
let eaw = new EAWorker();
let messageHandler = new concurrency.MessageHandler((msg:concurrency.Message)=>{
    //do nothing
}, eaw);

let msg = new concurrency.Message(messageHandler);
```

## constructor
constructor(what: int, handler: MessageHandler)

Message的构造器，用于构造消息实例，需要传入消息标识符和[MessageHandler](./message_handler.md)来指定消息处理的逻辑。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数：**
|参数名|类型|必填|说明|
|-----|----|--|----|
|what|int|是|消息标识符，用于表明消息的类型或者目的，由开发者自行约定。|
|handler|[MessageHandler](./message_handler.md)|是|消息处理器，用于指定消息处理的逻辑。|


**示例：**
```ts
let eaw = new EAWorker();
let messageHandler = new concurrency.MessageHandler((msg:concurrency.Message)=>{
    //do nothing
}, eaw);
let EmptyMessageType: int = 1;

let msg = new concurrency.Message(EmptyMessageType, messageHandler);
```

## constructor
constructor(what: int, obj: Object, handler: MessageHandler)

Message的构造器，用于构造消息，需要传入消息标识符、[MessageHandler](./message_handler.md)和消息数据来指定消息处理的逻辑。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数：**
|参数名|类型|必填|说明|
|-----|----|--|----|
|what|int|是|消息标识符。|
|obj|Object|是|消息携带的数据对象。|
|handler|[MessageHandler](./message_handler.md)|是|消息处理器，用于指定消息处理的逻辑。|

**示例：**
```ts
let eaw = new EAWorker();
let messageHandler = new concurrency.MessageHandler((msg:concurrency.Message)=>{
    //do nothing
}, eaw);

let StringMessage: int = 2;

let msg = new concurrency.Message(StringMessage, "hello", messageHandler);
```

## constructor
constructor(callback: ()=>void, handler: MessageHandler)

Message的构造器，用于构造消息实例，需要传入回调函数和[MessageHandler](./message_handler.md)来指定消息处理的逻辑。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数：**
|参数名|类型|必填|说明|
|-----|----|--|----|
|callback|()=>void|是|消息处理完成后的回调函数。|
|handler|[MessageHandler](./message_handler.md)|是|消息处理器，用于指定消息处理的逻辑。|

**示例：**
```ts
let eaw = new EAWorker();
let messageHandler = new concurrency.MessageHandler((msg:concurrency.Message)=>{
    //do nothing
}, eaw);

let callback = () => {
    console.info("this is callback message");
}

let msg = new concurrency.Message(callback, messageHandler);
```

## sendToTarget
sendToTarget(): void

将当前消息发送到构造时传入的消息处理器中进行处理。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**示例：**
```ts
let eaw = new EAWorker();
let messageHandler = new concurrency.MessageHandler((msg:concurrency.Message)=>{
    //do nothing
}, eaw);

let callback = () => {
    console.info("this is callback message");
}

let msg = new concurrency.Message(callback, messageHandler);
msg.sendToTarget();
```

## getWhat
getWhat(): int

返回消息的标识符。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| int   | 返回消息的标识符。 |

**示例：**
```ts
let eaw = new EAWorker();
let messageHandler = new concurrency.MessageHandler((msg:concurrency.Message)=>{
    //do nothing
}, eaw);
let EmptyMessage: int = 1;

let msg = new concurrency.Message(EmptyMessage, messageHandler);
console.info("message type is: ", msg.getWhat());// message type is: 1

```

## getObject
getObject(): Object | undefined

获取消息携带的数据对象。

**ArkTS版本：** 本接口仅支持ArkTS1.2

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| Object \| undefined  | 返回消息携带的数据对象。 |

**示例：**
```ts
let eaw = new EAWorker();
let messageHandler = new concurrency.MessageHandler((msg:concurrency.Message)=>{
    //do nothing
}, eaw);

let StringMessage: int = 2;

let msg = new concurrency.Message(StringMessage, "hello", messageHandler);
console.info("message get object is: ", msg.getObject());// message get object is: hello
```

## getCallback
getCallback(): ()=>void

获取消息的回调函数。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| ()=>void   | 返回消息的回调函数，如果消息没有设置回调函数返回undefined。 |

**示例：**
```ts
type CB = ()=>void
let eaw = new EAWorker();
let messageHandler = new concurrency.MessageHandler((msg:concurrency.Message)=>{
    //do nothing
}, eaw);

let callback = () => {
    console.info("this is callback message");
}

let msg = new concurrency.Message(callback, messageHandler)
let cb = msg.getCallback() as CB
cb();
```

## getTarget
getTarget(): MessageHandler

获取消息的目标处理器。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| [MessageHandler](./message_handler.md)   | 返回消息处理器。 |

**示例：**
```ts
let eaw = new EAWorker();
let messageHandler = new concurrency.MessageHandler((msg:concurrency.Message)=>{
    //do nothing
}, eaw);

let msg = new concurrency.Message(messageHandler);
let res = (messageHandler == msg.getTarget());
console.info("message handler equals: ", res);// message handler equals: true
```