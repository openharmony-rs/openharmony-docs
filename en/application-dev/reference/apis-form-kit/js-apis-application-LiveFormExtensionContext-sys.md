# LiveFormExtensionContext (System API)
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @yangyuecheng-->
<!--Adviser: @HelloShuo-->

LiveFormExtensionContext, inherited from [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md), is the context of [LiveFormExtensionAbility](./js-apis-app-form-LiveFormExtensionAbility.md).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [LiveFormExtensionContext](./js-apis-application-LiveFormExtensionContext.md).
>
> - The APIs of this module can be used only in the stage model.

## Modules to Import
```ts
import { common } from '@kit.AbilityKit';
```

>  **NOTE**
>
> - In versions earlier than API version 22, you need to import LiveFormExtensionContext with `import LiveFormExtensionContext from 'application/LiveFormExtensionContext';`. This import mode is marked in red in DevEco Studio, but does not affect compilation and running. You can use LiveFormExtensionContext directly.
>
> - In API version 22 and later versions, you can import LiveFormExtensionContext with `import { common } from '@kit.AbilityKit';` and use it in the form of **common.LiveFormExtensionContext**.

## How to Use
LiveFormExtensionContext is used to query information about its associated LiveFormExtensionAbility and access resources of the LiveFormExtensionAbility.
```ts
import { LiveFormInfo, LiveFormExtensionAbility } from '@kit.FormKit';
import { UIExtensionContentSession } from '@kit.AbilityKit';

export default class MyLiveFormExtensionAbility extends LiveFormExtensionAbility {
  onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession) {
    let storage: LocalStorage = new LocalStorage();
    storage.setOrCreate('context', this.context);
    session.loadContent('pages/MyLiveFormPage', storage);
    session.sendData({['isFormReady']: true});
    console.info("current language is: ", this.context.config.language);
  }
};
```

## LiveFormExtensionContext

Context of the LiveFormExtensionAbility.

### connectServiceExtensionAbility<sup>21+<sup>

connectServiceExtensionAbility(want: Want, connection: ConnectOptions): number

Connects the current LiveFormExtensionAbility client to a [ServiceExtensionAbility](../../application-models/serviceextensionability-sys.md) server.

Before calling this API, you must implement the [ConnectOptions](../apis-ability-kit/js-apis-inner-ability-connectOptions.md) API.

Upon successful connection, the LiveFormExtensionAbility can communicate with the ServiceExtensionAbility through the [IRemoteObject](../apis-ipc-kit/js-apis-rpc.md#iremoteobject) returned by **ConnectOptions**, allowing access to capabilities exposed by the ServiceExtensionAbility.

ServiceExtensionAbility is a special type of [ExtensionAbility](../../application-models/extensionability-overview.md) provided by the system. It is designed to deliver background services for specific scenarios and does not support developer customization.

ServiceExtensionAbility enables applications to run in the background and provide services. Third-party applications can connect to and communicate with this ExtensionAbility.
A successful connection via this API will start the ServiceExtensionAbility. For details, see [Component Startup Rules](../../application-models/component-startup-rules.md).

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes| Want information required for connecting to the ServiceExtensionAbility, including the ability name and bundle name.|
| connection | [ConnectOptions](../apis-ability-kit/js-apis-inner-ability-connectOptions.md) | Yes| Callback used to return the information indicating connection success, failure, or disconnection. If the connection is successful, the [IRemoteObject](../apis-ipc-kit/js-apis-rpc.md#iremoteobject) instance will be returned.|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Connection ID. The client can call [disconnectServiceExtensionAbility](#disconnectserviceextensionability21) with this ID for disconnection.|

**Error codes**

For details about the error codes, see [Form Error Codes](errorcode-form.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 16500100 | Failed to obtain the configuration information.              |
| 16501000 | An internal functional error occurred.                       |
| 16501011 | The form can not support this operation.                      |

**Example**

```ts
// MyLiveFormExtensionAbility.ets
import { LiveFormInfo, LiveFormExtensionAbility } from '@kit.FormKit';
import { UIExtensionContentSession } from '@kit.AbilityKit';

export default class MyLiveFormExtensionAbility extends LiveFormExtensionAbility {
  onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession) {
    // 1. Pass LiveFormExtensionContext to the widget page component.
    let storage: LocalStorage = new LocalStorage();
    storage.setOrCreate('context', this.context);
    session.loadContent('pages/MyLiveFormPage', storage);
    session.sendData({['isFormReady']: true});
  }
};
```
```ts
// pages/MyLiveFormPage.ets
import { Want, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

@Entry
@Component
struct MyLiveFormPage {
  private storageForMyLiveFormPage: LocalStorage | undefined = undefined;
  private liveFormContext: common.LiveFormExtensionContext | undefined = undefined;

  aboutToAppear(): void {
    // 2. Obtain LiveFormExtensionContext.
    this.storageForMyLiveFormPage = this.getUIContext().getSharedLocalStorage();
    this.liveFormContext = this.storageForMyLiveFormPage?.get<common.LiveFormExtensionContext>('context');
    if (!this.liveFormContext) {
        console.info('MyLiveFormPage liveFormContext is empty');
        return;
      }
    this.connectServiceExtensionAbility();
  }

  private connectServiceExtensionAbility(): void {
    // Replace the Want information with the actual one.
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'ServiceExtensionAbility'
    };
    let commRemote: rpc.IRemoteObject;
    let options: common.ConnectOptions = {
      onConnect(elementName, remote) {
        commRemote = remote;
        console.info('onConnect...');
      },
      onDisconnect(elementName) {
        console.info('onDisconnect...');
      },
      onFailed(code) {
        console.error(`onFailed, err code: ${code}.`);
      }
    };
    let connection: number | undefined;
    try {
      connection = this.liveFormContext?.connectServiceExtensionAbility(want, options);
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }

  build() {
    Stack() {
      // Replace the page with the actual one.
    }
  }
}
```

### disconnectServiceExtensionAbility<sup>21+<sup>

disconnectServiceExtensionAbility(connectionId: number): Promise\<void>

Disconnects from a [ServiceExtensionAbility](../../application-models/serviceextensionability-sys.md). Once the connection is terminated, set the **IRemoteObject**, which is returned when the connection is established, to null. This API uses a promise to return the result.

ServiceExtensionAbility is a special type of [ExtensionAbility](../../application-models/extensionability-overview.md) provided by the system. It is designed to deliver background services for specific scenarios and does not support developer customization. ServiceExtensionAbility enables applications to run in the background and provide services. Third-party applications can connect to and communicate with this ExtensionAbility.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| connectionId | number | Yes| Connection ID of the ServiceExtensionAbility, that is, the **connectionId** returned by [connectServiceExtensionAbility](#connectserviceextensionability21).|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Form Error Codes](errorcode-form.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed, application which is not a system application uses system API.|
| 16501000 | An internal functional error occurred.                       |
| 16501011 | The form can not support this operation.                      |

**Example**
```ts
// MyLiveFormExtensionAbility.ets
import { LiveFormInfo, LiveFormExtensionAbility } from '@kit.FormKit';
import { UIExtensionContentSession } from '@kit.AbilityKit';

export default class MyLiveFormExtensionAbility extends LiveFormExtensionAbility {
  onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession) {
    // 1. Pass LiveFormExtensionContext to the widget page component.
    let storage: LocalStorage = new LocalStorage();
    storage.setOrCreate('context', this.context);
    session.loadContent('pages/MyLiveFormPage', storage);
    session.sendData({['isFormReady']: true});
  }
};
```
```ts
// pages/MyLiveFormPage.ets
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

@Entry
@Component
struct MyLiveFormPage {
  private storageForMyLiveFormPage: LocalStorage | undefined = undefined;
  private liveFormContext: common.LiveFormExtensionContext | undefined = undefined;

  aboutToAppear(): void {
    // 2. Obtain LiveFormExtensionContext.
    this.storageForMyLiveFormPage = this.getUIContext().getSharedLocalStorage();
    this.liveFormContext = this.storageForMyLiveFormPage?.get<common.LiveFormExtensionContext>('context');
    if (!this.liveFormContext) {
        console.info('MyLiveFormPage liveFormContext is empty');
        return;
      }
    this.disconnectServiceExtensionAbility();
  }

  private async disconnectServiceExtensionAbility(): Promise<void> {
    // connection is the connection ID, which is usually the return value of the connectServiceExtensionAbility API. Replace it with the actual ID of the connection to be canceled.
    let connection = 1;
    let commRemote: rpc.IRemoteObject | null;

    try {
      await this.liveFormContext?.disconnectServiceExtensionAbility(connection);
      // Carry out normal service processing.
      console.info('disconnectServiceExtensionAbility succeed');
    } catch (err) {
      // Process the error.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`disconnectServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    } finally {
      commRemote = null;
    }
  }

  build() {
    Stack() {
      // Replace the page with the actual one.
    }
  }
}
```
