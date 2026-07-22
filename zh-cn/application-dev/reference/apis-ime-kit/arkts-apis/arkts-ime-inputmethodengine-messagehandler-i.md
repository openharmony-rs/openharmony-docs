# MessageHandler

自定义通信对象。

**起始版本：** 15

<!--Device-inputMethodEngine-interface MessageHandler--><!--Device-inputMethodEngine-interface MessageHandler-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## onMessage

```TypeScript
onMessage(msgId: string, msgParam?: ArrayBuffer): void
```

接收已绑定当前输入法应用的编辑框应用发送的自定义数据回调函数。

<p>当已注册的MessageHandler接收到来自已绑定当前输入法应用的编辑框应用所发送的自定义通信数据时，会触发该回调函数。</p><p>msgId为必选参数，msgParam为可选参数。存在收到仅有msgId自定义数据的可能，需与数据发送方确认自定义数据。</p>

**起始版本：** 15

<!--Device-MessageHandler-onMessage(msgId: string, msgParam?: ArrayBuffer): void--><!--Device-MessageHandler-onMessage(msgId: string, msgParam?: ArrayBuffer): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| msgId | string | 是 | 接收到的自定义通信数据的标识符。 |
| msgParam | ArrayBuffer | 否 | 接收到的自定义通信数据的消息体。 |

**示例：**

```TypeScript
inputMethodEngine.getInputMethodAbility()
  .on('inputStart',
    (keyboardController: inputMethodEngine.KeyboardController, inputClient: inputMethodEngine.InputClient) => {
      let messageHandler: inputMethodEngine.MessageHandler = {
        onTerminated(): void {
          console.info('OnTerminated.');
        },
        onMessage(msgId: string, msgParam?: ArrayBuffer): void {
          console.info(`recv message, msgId is ${msgId}, msgParam is ${JSON.stringify(msgParam)}`);
        }
      }
      inputClient.recvMessage(messageHandler);
    });

```

## onTerminated

```TypeScript
onTerminated(): void
```

监听对象终止回调函数。

<p>当应用注册新的MessageHandler对象时，会触发上一个已注册MessageHandler对象的onTerminated回调函数。</p><p>当应用取消注册时，会触发当前已注册MessageHandler对象的onTerminated回调函数。</p>

**起始版本：** 15

<!--Device-MessageHandler-onTerminated(): void--><!--Device-MessageHandler-onTerminated(): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**示例：**

```TypeScript
inputMethodEngine.getInputMethodAbility()
  .on('inputStart',
    (keyboardController: inputMethodEngine.KeyboardController, inputClient: inputMethodEngine.InputClient) => {
      let messageHandler: inputMethodEngine.MessageHandler = {
        onTerminated(): void {
          console.info('OnTerminated.');
        },
        onMessage(msgId: string, msgParam?: ArrayBuffer): void {
          console.info(`recv message, msgId is ${msgId}, msgParam is ${JSON.stringify(msgParam)}`);
        }
      }
      client.recvMessage(messageHandler);
    });

```

