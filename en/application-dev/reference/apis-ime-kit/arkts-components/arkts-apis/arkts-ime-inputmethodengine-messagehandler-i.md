# MessageHandler

Represents a custom communication object. <br> <br>  
> **NOTE:** <br>
> <br>
> You can register this object to receive custom communication data sent by the edit box application attached to the input method application. When the custom communication data is received, the [onMessage](#onmessage) callback in this object is triggered. <br>
> <br>
> This object is globally unique. After multiple registrations, only the last registered object is valid and retained, and the [onTerminated](#onterminated) callback of the penultimate registered object is triggered. <br>
> <br>
> If this object is unregistered, its [onTerminated](#onterminated) callback will be triggered.

**Since:** 15

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## onMessage

```TypeScript
onMessage(msgId: string, msgParam?: ArrayBuffer): void
```

Receives the custom data callback sent by the edit box application attached to the input method application. <br> <br>  
> **NOTE:** <br>
> <br>
> This callback is triggered when the registered [MessageHandler](arkts-ime-inputmethodengine-messagehandler-i.md) receives custom communication data sent by the edit box application attached to the input method application. <br>
> <br>
> The **msgId** parameter is mandatory, and the **msgParam** parameter is optional. If only the custom **msgId** data is received, confirm it with the data sender.

**Since:** 15

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| msgId | string | Yes | Identifier of the received custom communication data. |
| msgParam | ArrayBuffer | No | Message body of the received custom communication data. |

**Examples**

```TypeScript
inputMethodEngine.getInputMethodAbility()
  .on('inputStart',
    (kbController: inputMethodEngine.KeyboardController, client: inputMethodEngine.InputClient) => {
      let keyboardController: inputMethodEngine.KeyboardController = kbController;
      let inputClient: inputMethodEngine.InputClient = client;
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

Listens for MessageHandler termination. <br> <br>  
> **NOTE:** <br>
> <br>
> When an application registers a new [MessageHandler](arkts-ime-inputmethodengine-messagehandler-i.md) object, the [onTerminated](#onterminated) callback of the penultimate registered [MessageHandler](arkts-ime-inputmethodengine-messagehandler-i.md) object is triggered. <br>
> <br>
> When an application unregisters a new [MessageHandler](arkts-ime-inputmethodengine-messagehandler-i.md) object, the [onTerminated](#onterminated) callback of the registered [MessageHandler](arkts-ime-inputmethodengine-messagehandler-i.md) object is triggered.

**Since:** 15

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Examples**

```TypeScript
inputMethodEngine.getInputMethodAbility()
  .on('inputStart',
    (kbController: inputMethodEngine.KeyboardController, client: inputMethodEngine.InputClient) => {
      let keyboardController: inputMethodEngine.KeyboardController = kbController;
      let inputClient: inputMethodEngine.InputClient = client;
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
