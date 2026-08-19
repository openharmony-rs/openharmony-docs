# MessageHandler

自定义通信对象。

**起始版本：** 23

<!--Device-inputMethod-interface MessageHandler--><!--Device-inputMethod-interface MessageHandler-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
import { inputMethodEngine } from '@kit.IMEKit';
import { InputMethodListDialog, PatternOptions, Pattern } from '@kit.IMEKit';
import { PanelInfo, PanelType, PanelFlag } from '@kit.IMEKit';
import { InputMethodExtraConfig } from '@kit.IMEKit';
import { inputMethodSystemPanelManager } from '@kit.IMEKit';
```

## onMessage

```TypeScript
onMessage(msgId: string, msgParam?: ArrayBuffer): void
```

接收输入法应用发送的自定义数据回调函数。

**起始版本：** 15

<!--Device-MessageHandler-onMessage(msgId: string, msgParam?: ArrayBuffer): void--><!--Device-MessageHandler-onMessage(msgId: string, msgParam?: ArrayBuffer): void-End-->

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

**起始版本：** 15

<!--Device-MessageHandler-onTerminated(): void--><!--Device-MessageHandler-onTerminated(): void-End-->

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

## onMessage

```TypeScript
onMessage: OnMessageCallback
```

onMessage(msgId: string, msgParam?: ArrayBuffer): void

**类型：** OnMessageCallback

**起始版本：** 23

<!--Device-MessageHandler-onMessage: OnMessageCallback--><!--Device-MessageHandler-onMessage: OnMessageCallback-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## onTerminated

```TypeScript
onTerminated: Callback<void>
```

onTerminated(): void 监听对象终止回调函数。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt;

**起始版本：** 23

<!--Device-MessageHandler-onTerminated: Callback<void>--><!--Device-MessageHandler-onTerminated: Callback<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

