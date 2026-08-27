# MessageHandler

自定义通信对象。   
> **说明：**
   
> 
   
> 开发者可通过注册此对象来接收输入法应用发送的自定义通信数据，接收到自定义通信数据时会触发此对象中
   
> [onMessage](#onmessage)回调函数。
   
> 
   
> 此对象全局唯一，多次注册仅保留最后一次注册的对象及有效性，并触发上一个已注册对象的[onTerminated](#onterminated)回调函数。
   
> 
   
> 若取消注册全局已注册的对象时，会触发被取消对象中[onTerminated](#onterminated)回调函数。

**起始版本：** 15

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## onMessage

```TypeScript
onMessage(msgId: string, msgParam?: ArrayBuffer): void
```

接收输入法应用发送的自定义数据回调函数。   
> **说明：**
   
> 
   
> 当已注册的MessageHandler接收到来自输入法应用发送的自定义通信数据时，会触发该回调函数。
   
> 
   
> msgId为必选参数，msgParam为可选参数。存在收到仅有msgId自定义数据的可能，需与数据发送方确认自定义数据。

**起始版本：** 15

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| msgId | string | 是 | 接收到的自定义通信数据的标识符。 |
| msgParam | ArrayBuffer | 否 | 接收到的自定义通信数据的消息体。 |

**示例**

```TypeScript
let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();

let messageHandler: inputMethod.MessageHandler = {
  onTerminated(): void {
    console.info('OnTerminated.');
  },
  onMessage(msgId: string, msgParam?: ArrayBuffer): void {
    console.info(`recv message, msg: ${msgId}, msgParam: ${JSON.stringify(msgParam)}`);
  }
};
inputMethodController.recvMessage(messageHandler);
```

## onTerminated

```TypeScript
onTerminated(): void
```

监听对象终止回调函数。   
> **说明：**
   
> 
   
> 当应用注册新的MessageHandler对象时，会触发上一个已注册MessageHandler对象的OnTerminated回调函数。
   
> 
   
> 当应用取消注册时，会触发当前已注册MessageHandler对象的OnTerminated回调函数。

**起始版本：** 15

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**示例**

```TypeScript
let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();

let messageHandler: inputMethod.MessageHandler = {
  onTerminated(): void {
    console.info('OnTerminated.');
  },
  onMessage(msgId: string, msgParam?: ArrayBuffer): void {
    console.info(`recv message, msg: ${msgId}, msgParam: ${JSON.stringify(msgParam)}`);
  }
};
inputMethodController.recvMessage(messageHandler);
```
