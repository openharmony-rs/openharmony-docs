# LiveFormExtensionContext (System API)
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=e51968c7c56d4fd4ec628eff339eeb09ceb3837b translatedAt=2026-11-03T13:27:44.367Z pushedAt=2026-11-04T08:47:40.869Z nl=1 -->

**LiveFormExtensionContext** is the context of [LiveFormExtensionAbility](./js-apis-app-form-LiveFormExtensionAbility.md), which is inherited from [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This page contains only the system APIs of this module. For details about other public APIs, see [LiveFormExtensionContext](./js-apis-application-LiveFormExtensionContext.md).
>
> The APIs of this module can be used only in the stage model.

## Modules to Import
```ts
import { common } from '@kit.AbilityKit';
```

> **NOTE**
>
> - Before API version 22, LiveFormExtensionContext must be imported through `import LiveFormExtensionContext from 'application/LiveFormExtensionContext'; `. This import method is marked in red in DevEco Studio, but it does not affect compilation and running, and LiveFormExtensionContext can be used directly.
>
> - Since API version 22, LiveFormExtensionContext can be imported through `import { common } from '@kit.AbilityKit'; ` and used in the form of common.LiveFormExtensionContext.

## Instructions
**LiveFormExtensionContext** is mainly used to query the information of the **LiveFormExtensionAbility** to which it belongs, and provides the capability to access the resources of a specific **LiveFormExtensionAbility**.
```ts
import { LiveFormInfo, LiveFormExtensionAbility } from '@kit.FormKit';
import { UIExtensionContentSession } from '@kit.AbilityKit';

export default class MyLiveFormExtensionAbility extends LiveFormExtensionAbility {
  onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession) {
    let storage: LocalStorage = new LocalStorage();
    storage.setOrCreate('context', this.context);
    session.loadContent('pages/MyLiveFormPage', storage);
    session.sendData({ ['isFormReady']: true });
    console.info("current language is: ", this.context.config.language);
  }
};
```

## LiveFormExtensionContext

LiveFormExtensionContext is the context environment of LiveFormExtensionAbility.

### connectServiceExtensionAbility<sup>21+</sup>

connectServiceExtensionAbility(want: Want, connection: ConnectOptions): number

Connects the current LiveFormExtensionAbility client to a [ServiceExtensionAbility](../../application-models/serviceextensionability-sys.md) server.

Before calling this API, you must implement the [ConnectOptions](../apis-ability-kit/js-apis-inner-ability-connectOptions.md) interface.

After the connection is successful through this API, LiveFormExtensionAbility can communicate with ServiceExtensionAbility through the [IRemoteObject](../apis-ipc-kit/js-apis-rpc.md#iremoteobject) returned by ConnectOptions, so as to use the capabilities provided by ServiceExtensionAbility.

ServiceExtensionAbility is a special type of [ExtensionAbility](../../application-models/extensionability-overview.md) component. This type of component is provided by the system and is usually used to provide background service capabilities in specified scenarios. It does not support customization by developers.

ServiceExtensionAbility provides background service extension capabilities, supports running in the background, and provides corresponding capabilities to the outside. Third-party applications can connect to this ExtensionAbility and communicate with it.

After the connection is successful through this API, the ServiceExtensionAbility component is started. For details, see [Component Startup Rules](../../application-models/component-startup-rules.md).

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes | Want information for connecting to ServiceExtensionAbility, including the ability name, bundle name, and so on. |
| connection | [ConnectOptions](../apis-ability-kit/js-apis-inner-ability-connectOptions.md) | Yes | Callback function of the ConnectOptions type, which returns the information about successful connection, connection failure, and disconnection. If the connection is successful, an [IRemoteObject](../apis-ipc-kit/js-apis-rpc.md#iremoteobject) instance is returned. |

**Return value**

| Type | Description |
| -------- | -------- |
| number | Returns the connection ID. The client can pass this connection ID to [disconnectServiceExtensionAbility](#disconnectserviceextensionability21) to disconnect. |

**Error codes**

For details about the error codes, see [Form Error Codes](errorcode-form.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
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
    // 1. Pass the LiveFormExtensionContext to the page component of the interactive card.
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
    // 2. Obtain the LiveFormExtensionContext.
    this.storageForMyLiveFormPage = this.getUIContext().getSharedLocalStorage();
    this.liveFormContext = this.storageForMyLiveFormPage?.get<common.LiveFormExtensionContext>('context');
    if (!this.liveFormContext) {
        console.info('MyLiveFormPage liveFormContext is empty');
        return;
      }
    this.connectServiceExtensionAbility();
  }

  private connectServiceExtensionAbility(): void {
    // Replace it with the actual want.
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
      // Handle the input parameter error exception.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }

  build() {
    Stack() {
      // Replace it with the actual page.
    }
  }
}
```

### disconnectServiceExtensionAbility<sup>21+</sup>

disconnectServiceExtensionAbility(connectionId: number): Promise\<void>

Disconnects from the [ServiceExtensionAbility](../../application-models/serviceextensionability-sys.md). After the disconnection, the developer needs to set the IRemoteObject object returned upon successful connection to null. This API uses a promise to return the result asynchronously.

ServiceExtensionAbility is a special type of [ExtensionAbility](../../application-models/extensionability-overview.md) component. This type of component is provided by the system and is usually used to provide background service capabilities for specified scenarios. It does not support customization by developers. ServiceExtensionAbility provides background service extension capabilities, supports running in the background, and provides corresponding capabilities externally. Third-party applications can connect to this ExtensionAbility and communicate with it.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| connectionId | number | Yes | Connection ID of the connected ServiceExtensionAbility, that is, the connectionId returned by [connectServiceExtensionAbility](#connectserviceextensionability21). |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Form Error Codes](errorcode-form.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
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
    // 1. Pass LiveFormExtensionContext to the page component of the interactive card.
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
    // connection is the connection ID, which is usually the return value of the connectServiceExtensionAbility API. Replace it with the actual ID of the connection to be disconnected.
    let connection = 1;
    // Note: Save the IRemoteObject object when connectServiceExtensionAbility succeeds.
    // After the connection is disconnected, set the saved IRemoteObject object to null.
    try {
      await this.liveFormContext?.disconnectServiceExtensionAbility(connection);
      // Execute normal services.
      console.info('disconnectServiceExtensionAbility succeed');
      // Set the IRemoteObject object saved when the connection succeeds to null, for example: this.savedRemoteObject = null;
    } catch (err) {
      // Handle errors and exceptions.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`disconnectServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }

  build() {
    Stack() {
      // Replace it with the actual page.
    }
  }
}
```