# UIServiceProxy

```TypeScript
export default interface UIServiceProxy
```

UIServiceProxy functions as a proxy to send data from the UIServiceExtensionAbility client to the server.

> **NOTE:** 
> 
> - The APIs of this module must be used in the main thread, but not in child threads such as Worker and TaskPool.

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## sendData

```TypeScript
sendData(data: Record<string, Object>): void
```

Sends data to the UIServiceExtensionAbility server.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | Yes | Data to be sent to the UIServiceExtensionAbility server. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const TAG: string = '[Extension] ';

@Entry
@Component
struct UIServiceExtensionAbility {
  comProxy: common.UIServiceProxy | null = null;
  dataCallBack: common.UIServiceExtensionConnectCallback = {
    onData: (data: Record<string, Object>) => {
      console.info(`${TAG} dataCallBack received data: ${JSON.stringify(data)}.`);
    },
    onDisconnect: () => {
      console.info(`${TAG} dataCallBack onDisconnect.`);
      this.comProxy = null;
    }
  }

  build() {
    Scroll() {
      Column() {
        // Create a button for connecting to the UIServiceExtensionAbility.
        Button('connectUIServiceExtensionAbility', { type: ButtonType.Capsule, stateEffect: true })
          .margin({
            top: 5,
            left: 10,
            right: 10,
            bottom: 5
          })
          .alignRules({
            center: { anchor: '__container__', align: VerticalAlign.Center },
            middle: { anchor: '__container__', align: HorizontalAlign.Center }
          })
          .onClick(() => {
            this.myConnectUIServiceExtensionAbility()
          });
      }
      .width('100%')
    }
    .height('100%')
  }

  // Customize a function for connecting to the UIServiceExtensionAbility.
  myConnectUIServiceExtensionAbility() {
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    let startWant: Want = {
      deviceId: '',
      bundleName: 'com.acts.myapplication',
      abilityName: 'UiServiceExtensionAbility'
    };

    try {
      // Connect to the UIServiceExtensionAbility.
      context.connectUIServiceExtensionAbility(startWant, this.dataCallBack)
        .then((proxy: common.UIServiceProxy) => {
          console.info(TAG + `try to connectUIServiceExtensionAbility ${proxy}`);
          this.comProxy = proxy;
          let formData: Record<string, string> = {
            'PATH': '/tmp/aaa.jpg'
          };
          try {
            console.info(`${TAG} sendData.`);
            // Send data to the UIServiceExtensionAbility.
            this.comProxy.sendData(formData);
          } catch (err) {
            let code = (err as BusinessError).code;
            let message = (err as BusinessError).message;
            console.error(`${TAG} sendData failed, code is ${code}, message is ${message}.`);
          }
        }).catch((err: Error) => {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        console.error(`${TAG} connectUIServiceExtensionAbility failed, code is ${code}, message is ${message}.`);
      });
    } catch (err) {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`${TAG} connectUIServiceExtensionAbility failed, code is ${code}, message is ${message}.`);
    }
  }
}
```
