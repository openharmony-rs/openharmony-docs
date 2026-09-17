# MessageHandler

Represents a custom communication object. <br> <br>  
> **NOTE:** <br>
> <br>
> You can register this object to receive custom communication data sent by the input method application. When the custom communication data is received, the [onMessage](#onmessage) callback in this object is triggered. <br>
> <br>
> This object is globally unique. After multiple registrations, only the last registered object is valid and retained, and the [onTerminated](#onterminated) callback of the penultimate registered object is triggered. <br>
> <br>
> If this object is unregistered, its [onTerminated](#onterminated) callback will be triggered.

**Since:** 15

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## onMessage

```TypeScript
onMessage(msgId: string, msgParam?: ArrayBuffer): void
```

This method is called when a custom message is received.

**Since:** 15

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| msgId | string | Yes | the identifier of the message. |
| msgParam | ArrayBuffer | No | the parameter of the custom message. |

**Examples**

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

This method is called when a new message handler is set.

**Since:** 15

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Examples**

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
