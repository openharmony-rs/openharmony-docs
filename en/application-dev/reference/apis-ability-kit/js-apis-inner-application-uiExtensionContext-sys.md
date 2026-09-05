# UIExtensionContext (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=68b6c358aa355441ba00a2df89af84c41abac871 translatedAt=2026-09-03T12:07:11.031Z pushedAt=2026-09-05T10:47:30.873Z -->

UIExtensionContext provides the context environment for [UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md). It inherits from [ExtensionContext](js-apis-inner-application-extensionContext.md) and provides UIExtensionAbility-related configuration and APIs for operating the UIExtensionAbility. For example, you can use the APIs to start a UIExtensionAbility.

> **NOTE**
>
>  - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>  - The APIs of this module can be used only in the stage model.
>  - The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## UIExtensionContext

### startAbilityForResultAsCaller

startAbilityForResultAsCaller(want: Want, options?: StartOptions): Promise&lt;AbilityResult&gt;

Starts an ability with the caller information carried in **want**. The caller information is identified at the system service layer. The ability can obtain the caller information from the **want** parameter in the onCreate lifecycle. When the ability is started, the caller information in **want** is not overwritten by the current application information, and the system service layer can obtain the initial caller information. This API uses a promise to return the result.

 - Normally, you can call [terminateSelfWithResult](js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult) to terminate the ability. The result is returned to the caller.
 - If an exception occurs, for example, the ability is killed, an error message, in which **resultCode** is **-1**, is returned to the caller.
 - If different applications call this API to start an ability that uses the singleton mode and then call [terminateSelfWithResult](js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult) to terminate the ability, the normal result is returned to the last caller, and an exception message, in which **resultCode** is **-1**, is returned to others.

> **NOTE**
>
> For details about the component startup rules, see [Intra-Device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-Device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type                                               | Mandatory| Description                     |
| ------- | --------------------------------------------------- | ---- | ------------------------- |
| want    | [Want](js-apis-app-ability-want.md)                 | Yes  | Want information about the target ability.  |
| options | [StartOptions](js-apis-app-ability-startOptions.md) | No | Parameters carried when starting the ability. If this parameter is not passed, the default startup configuration is used. |

**Return value**

| Type                                                        | Description                     |
| ------------------------------------------------------------ | ------------------------- |
| Promise&lt;[AbilityResult](js-apis-inner-ability-abilityResult.md)&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 201 | The application does not have permission to call the interface. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist.                   |
| 16000004 | Cannot start an invisible component.                    |
| 16000050 | Internal error.                                         |
| 16000069 | The extension cannot start the third party application. |
| 16000070 | The extension cannot start the service. |
| 16000071 | App clone is not supported. <br>Applicable Version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000073 | The app clone index is invalid. |
| 16000076 | The app instance key is invalid. <br>Applicable Version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>Applicable Version: 14+ |
| 16000078 | The multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>Applicable Version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>Applicable Version: 14+ |

**Example**

```ts
import { UIExtensionAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UIExtension extends UIExtensionAbility {
  onForeground() {
    // Start the ability using the caller information.
    this.context.startAbilityForResultAsCaller({
      bundleName: 'com.example.startabilityforresultascaller',
      abilityName: 'EntryAbility',
      moduleName: 'entry'
    }).then((data) => {
      console.info(`StartAbilityForResultAsCaller success, data: ${JSON.stringify(data)}.`);
    }).catch((error: BusinessError) => {
      console.error(`StartAbilityForResultAsCaller failed, err code: ${error.code}, err msg: ${error.message}.`);
    });
  }
}
```

### startServiceExtensionAbility<sup>18+</sup>

startServiceExtensionAbility(want: Want): Promise\<void>

Starts a [ServiceExtensionAbility](../apis-ability-kit/js-apis-app-ability-serviceExtensionAbility-sys.md) to provide background service capabilities. This API uses a promise to return the result.

> **NOTE**
>
> For details about the component startup rules, see [Intra-Device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-Device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ------ | ------ |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information for starting the ServiceExtensionAbility.|

**Return value**

| Type| Description|
| ------ | ------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------ | ------ |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. |
| 16000013 | The application is controlled by EDM. |
| 16000019 | No matching ability is found. |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UIExtAbility extends UIExtensionAbility {
  onForeground() {
    let want: Want = {
      bundleName: 'com.example.myapplication',
      moduleName: 'entry',
      abilityName: 'ServiceExtensionAbility'
    };

    try {
      // Start ServiceExtensionAbility.
      this.context.startServiceExtensionAbility(want)
        .then(() => {
          // Carry out normal service processing.
          console.info('startServiceExtensionAbility succeed');
        })
        .catch((err: BusinessError) => {
          // Process service logic errors.
          console.error(`startServiceExtensionAbility failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### startServiceExtensionAbilityWithAccount<sup>18+</sup>

startServiceExtensionAbilityWithAccount(want: Want, accountId: number): Promise\<void>

Starts a [ServiceExtensionAbility](../apis-ability-kit/js-apis-app-ability-serviceExtensionAbility-sys.md) under a specified system account to provide background service capabilities. This API uses a promise to return the result.

> **NOTE**
>
> For details about the component startup rules, see [Intra-Device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-Device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-cross-device-sys.md).
>
> When **accountId** is the current user, no permission verification is required.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ------ | ------ |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information for starting the ServiceExtensionAbility.|
| accountId | number | Yes | System account ID, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |

**Return value**

| Type| Description|
| ------ | ------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------ | ------ |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. |
| 16000013 | The application is controlled by EDM. |
| 16000019 | No matching ability is found. |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UIExtAbility extends UIExtensionAbility {
  onForeground() {
    let want: Want = {
      bundleName: 'com.example.myapplication',
      moduleName: 'entry',
      abilityName: 'ServiceExtensionAbility'
    };
    let accountId = 100;

    try {
      // Start ServiceExtensionAbility under the specified system account.
      this.context.startServiceExtensionAbilityWithAccount(want, accountId)
        .then(() => {
          // Carry out normal service processing.
          console.info('startServiceExtensionAbilityWithAccount succeed');
        })
        .catch((err: BusinessError) => {
          // Process service logic errors.
          console.error(`startServiceExtensionAbilityWithAccount failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startServiceExtensionAbilityWithAccount failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### setHostPageOverlayForbidden<sup>15+</sup>

setHostPageOverlayForbidden(isForbidden: boolean) : void

Sets whether the page started by the [UIExtensionAbility](../apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md) is forbidden from being overlaid by the page of the user.

> **NOTE**
>
> For details about the component startup rules, see [Intra-Device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-Device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-cross-device-sys.md).
>
> This API must be called before the window is created. It is recommended to call it in the [onCreate](../apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md#oncreate) lifecycle of the [UIExtensionAbility](../apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md).

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ------ | ------ |
| isForbidden | boolean | Required | Whether to forbid the page started by [UIExtensionAbility](../apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md) from being covered by the page of the caller. The value true means to forbid, and false means to allow. |


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------ | ------ |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { UIExtensionAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UIExtAbility extends UIExtensionAbility {
  onCreate() {
    try {
      // Set to prevent the page started by UIExtensionAbility from being covered.
      this.context.setHostPageOverlayForbidden(true)
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`setHostPageOverlayForbidden failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### startUIAbilities<sup>20+</sup>

startUIAbilities(wantList: Array\<Want>): Promise\<void>

Starts multiple UIAbility components simultaneously. This API uses a promise to return the result.

You can pass the Want information of multiple UIAbility instances, which can point to one or more applications. If all the UIAbility instances can be started successfully, the system displays these UIAbility instances in multiple windows simultaneously. Depending on the window handling, different devices may have varying display effects (including window shape, quantity, and layout).

> **NOTE**
>
> For details about the component startup rules, see [Intra-Device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md).

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**: This API can be properly called only on phones and tablets. If it is called on other device types, error code 801 is returned.

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ------ | ------ |
| wantList | Array\<[Want](js-apis-app-ability-want.md)> | Yes| List of launch parameters for multiple UIAbility components to be started simultaneously. A maximum of four Want objects can be passed. The **Want** parameter does not support implicit launch, cross-user launch, distributed launch, instant installation, or on-demand loading. By default, the main application is launched unless specified otherwise.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------ | ------ |
| 201 | The application does not have permission to call the interface. |
| 202 | Not system application. |
| 801 | Capability not supported. |
| 16000001 | The specified ability does not exist. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |
| 16000073 | The app clone index is invalid. |
| 16000076 | The app instance key is invalid. |
| 16000080 | Creating a new instance is not supported. |
| 16000120 | A maximum of four UIAbility instances can be started simultaneously. The current parameter exceeds the maximum number or is less than 1.|
| 16000121 | The target component type is not a UIAbility. |
| 16000122 | The target component is blocked by the system module and does not support startup. |
| 16000123 | Implicit startup is not supported. |
| 16000124 | Starting a remote UIAbility is not supported. |
| 16000125 | Starting a plugin UIAbility is not supported. |
| 16000126 | Starting DLP files is not supported. |

**Example**

```ts
import { UIExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryUIExtAbility extends UIExtensionAbility {
  onForeground() {
    let want1: Want = {
      bundleName: 'com.example.myapplication1',
      abilityName: 'EntryAbility'
    };
    let want2: Want = {
      bundleName: 'com.example.myapplication2',
      abilityName: 'EntryAbility'
    };
    let wantList: Array<Want> = [want1, want2];
    try {
      // Start multiple UIAbility instances simultaneously.
      this.context.startUIAbilities(wantList).then(() => {
        console.info(`TestTag:: start succeeded.`);
      }).catch((error: BusinessError) => {
        console.error(`TestTag:: startUIAbilities failed. Code: ${error.code}, message: ${error.message}`);
      });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
    }
  }
}
```
### startUIAbilitiesInSplitWindowMode<sup>21+</sup>

startUIAbilitiesInSplitWindowMode(primaryWindowId: number, secondaryWant: Want): Promise\<void>

Starts a second UIAbility after the first UIAbility instance is created, and displays them in split-screen mode. This API uses a promise to return the result.

> **NOTE**
>
> If the first UIAbility instance is destroyed, the second UIAbility is started in full-screen mode.
>
> The second UIAbility supports only [explicit startup](../../application-models/explicit-implicit-want-mappings.md#explicit-want-matching-principle).
>
> If the caller is in the background, the ohos.permission.START_ABILITIES_FROM_BACKGROUND permission is also required (this permission is available only to system applications).
>
> For details about the component startup rules, see [Intra-Device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md).

**System API**: This is a system API.

**Required permissions:** ohos.permission.START_ABILITIES_FROM_BACKGROUND

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**: This API can be properly called only on phones. If it is called on other device types, error code 801 is returned.

**Parameters**

| Name| Type| Mandatory| Description                                                                                                                                                                                                                    |
| ------ |--------| ------ |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| primaryWindowId | number | Yes| ID of the main window of the first UIAbility. The window ID is a property defined in [WindowProperties](../apis-arkui/arkts-apis-window-i.md#windowproperties), which can be obtained by calling [getWindowProperties()](../apis-arkui/arkts-apis-window-Window.md#getwindowproperties9).|
| secondaryWant | [Want](js-apis-app-ability-want.md) | Yes| Want information required for starting the second UIAbility.                                                                                                                                                                                              |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------ | ------ |
| 201 | The application does not have permission to call the interface. |
| 202 | Not system application. |
| 801 | Capability not supported. |
| 16000001 | Target UIAbility does not exist. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000011 | The context does not exist. |
| 16000050 | Failed to connect to the system service or system server handle failed. |
| 16000073 | The app clone index is invalid. |
| 16000076 | The app instance key is invalid. |
| 16000080 | Creating a new instance is not supported. |
| 16000122 | The target component is blocked by the system module and does not support startup. |
| 16000123 | Implicit startup is not supported. |
| 16000124 | Starting a remote UIAbility is not supported. |
| 16000125 | Starting a plugin UIAbility is not supported. |
| 16000126 | Starting DLP files is not supported. |

**Example**

```ts
import { UIExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryUIExtAbility extends UIExtensionAbility {
  onForeground() {
    // Main window ID of the first UIAbility. Replace it with the actual one.
    let primaryWindowId = 123;
    let secondaryWant: Want = {
      bundleName: 'com.example.myapplication1',
      abilityName: 'EntryAbility'
    };
    try {
      // Start the second UIAbility in split-screen mode.
      this.context.startUIAbilitiesInSplitWindowMode(primaryWindowId, secondaryWant).then(() => {
        console.info(`TestTag:: start succeeded.`);
      }).catch((error: BusinessError) => {
        console.error(`TestTag:: startUIAbilitiesInSplitWindowMode failed. Code: ${error.code}, message: ${error.message}`);
      });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
    }
  }
}
```

### connectServiceExtensionAbilityWithRootHostToken

connectServiceExtensionAbilityWithRootHostToken(want: Want, connect: ConnectOptions): number

Connects the current UIExtensionAbility to a [ServiceExtensionAbility](../apis-ability-kit/js-apis-app-ability-serviceExtensionAbility-sys.md), and communicates with the ServiceExtensionAbility through the returned remote proxy object to use the capabilities provided by the ServiceExtensionAbility. Meanwhile, this method passes the token of the original host ability of the UIExtensionAbility to the connected ServiceExtensionAbility. The ServiceExtensionAbility can obtain the token through the [UI_EXTENSION_ROOT_TOKEN](js-apis-app-ability-wantConstant-sys.md#params) parameter of Want in the [onCreate()](../apis-ability-kit/js-apis-app-ability-serviceExtensionAbility-sys.md#oncreate) or [onConnect()](../apis-ability-kit/js-apis-app-ability-serviceExtensionAbility-sys.md#onconnect) method.

> **NOTE**
>
> For details about the component startup rules, see [Intra-Device Component Startup Rules (Available Only to System Applications)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-Device Component Startup Rules (Available Only to System Applications)](../../application-models/component-startup-rules-cross-device-sys.md).

**System API**: This is a system API.

**Since**: 26.0.0

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type | Required | Description |
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes | Want information for connecting to the ServiceExtensionAbility, including the ability name, bundle name, and so on. |
| connect | [ConnectOptions](js-apis-inner-ability-connectOptions.md) | Yes | Callback of the ConnectOptions type, which returns the information about successful connection, failed connection, and disconnection of the service. |

**Return value**

| Type | Description |
| -------- | -------- |
| number | Connection identifier returned. The client can pass this connection identifier to [disconnectServiceExtensionAbility](js-apis-inner-application-uiExtensionContext.md#disconnectserviceextensionability) to disconnect the connection. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. Possible cause: target service extension ability is in cross-device and needed designated permission to be started, but call ability do not have this permission. |
| 202 | Not system application |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled. |
| 16000013 | The application is controlled by EDM. |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed; 2.Send restart message to system service failed; 3.System service failed to communicate with dependency module.|
| 16000053 | The ability is not on the top of the UI. |
| 16000070 | The extension cannot start the service. |

**Example**

```ts
// UIExtensionAbility does not support direct inheritance by third-party applications, so the derived class ShareExtensionAbility is used as an example.
import { ShareExtensionAbility, Want, common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class ShareExtAbility extends ShareExtensionAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'ServiceExtensionAbility'
    };
    let commRemote: rpc.IRemoteObject;
    let options: common.ConnectOptions = {
      onConnect: (elementName, remote) => {
        commRemote = remote;
        console.info('onConnect...');
      },
      onDisconnect: (elementName) => {
        console.info('onDisconnect...');
      },
      onFailed: (code) => {
        console.error(`onFailed, err code: ${code}.`);
      }
    };
    let connection: number;
    try {
      // Connect to the ServiceExtensionAbility and pass the token of the original host ability.
      connection = this.context.connectServiceExtensionAbilityWithRootHostToken(want, options);
    } catch (err) {
      // Handle the input parameter error.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectServiceExtensionAbilityWithRootHostToken failed, code is ${code}, message is ${message}`);
    }
  }
}
```
