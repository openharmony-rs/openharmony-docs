# @ohos.web.webNativeMessagingExtensionContext

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @csliutt-private-->
<!--Designer: @ringking0-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=bcbbbedf2234f156fe3ad4387f2cc76834ae7941 translatedAt=2026-08-03T09:43:27.463Z pushedAt=2026-08-07T10:52:00.162Z -->

WebNativeMessagingExtensionContext is the runtime context of the native web message extension ([WebNativeMessagingExtensionAbility](./arkts-apis-web-webNativeMessagingExtensionAbility.md)). It inherits from ExtensionContext and provides lifecycle management, ability startup, and native message connection control capabilities for the extension ability. In an extension that inherits from WebNativeMessagingExtensionAbility, developers can obtain this context through `this.context` and then call [startAbility](#startability) to start another ability, call [startAbilityForResult](#startabilityforresult) to start a UIAbility and receive the return result, call [terminateSelf](#terminateself) to terminate the current extension, or call [stopNativeConnection](#stopnativeconnection) to stop a specified native web message connection.

> **NOTE**
>
> The initial APIs of this module are supported since API version 21. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
```

## WebNativeMessagingExtensionContext

Represents the context of web native message extension, including the required interaction capabilities.

### startAbility

startAbility(want: Want, options?: StartOptions): Promise&lt;void&gt;

Starts an ability. This API uses a promise to return the result. To obtain the return result when the started UIAbility exits, use [startAbilityForResult](#startabilityforresult).

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
|-------|-------|-------|-------|
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes | Information about the Ability to start, including bundleName, abilityName, and other attributes, used to specify the target Ability to start. |
| options | [StartOptions](../apis-ability-kit/js-apis-app-ability-startOptions.md) | No | Start options used to specify the options when starting the target UIAbility, including but not limited to the window mode and the screen where the target UIAbility is started. This parameter is passed when custom startup configuration is needed; if not passed, the default system startup configuration is used. |

**Return value**

| Type| Description|
|------|------|
|Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message                                |
| -------- | ----------------------------------------|
| 201      | The application does not have permission to call the interface. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000008 | The crowdtesting application expires.  |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. |
| 16000013 | The application is controlled by EDM. |
| 16000019 | No matching ability is found. |
| 16000050 | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. |
| 16000072 | App clone or multi-instance is not supported. |
| 16000073 | The app clone index is invalid. |
| 16000076 | The app instance key is invalid. |
| 16000077 | The number of app instances reaches the limit. |
| 16000078 | The multi-instance is not supported. |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. |
| 16000080 | Creating a new instance is not supported. |

**Example**

```ts
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export class MyWebNativeMessagingExtension extends WebNativeMessagingExtensionAbility {
  onConnectNative(info: ConnectionInfo): void {
    const abilityWant: Want = {
      bundleName: 'com.example.mybundle',
      abilityName: 'MainAbility'
    };
    try {
      const context = this.context; // Obtain the WebNativeMessagingExtensionContext instance.
      context.startAbility(abilityWant).then(() => {
        console.info('Ability started successfully');
      }).catch((err: BusinessError) => {
        console.error(`Failed to start ability. Code: ${(err as BusinessError).code},
          Message: ${(err as BusinessError).message}`);
      });
    } catch (err) {
      console.error(`Failed to start ability. Code: ${(err as BusinessError).code},
      Message: ${(err as BusinessError).message}`);
    }
  }
}
```

### startAbilityForResult

startAbilityForResult(want: Want, options?: StartOptions): Promise&lt;AbilityResult&gt;

Starts a UIAbility. This API uses a promise to return the result when the started UIAbility exits.

After the UIAbility is started, the following situations may occur:

 - Under normal circumstances, [terminateSelfWithResult](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult) can be called to terminate the UIAbility and return the result to the caller.

 - In abnormal cases, such as when the UIAbility is destroyed, exception information is returned to the caller, with resultCode set to -1.

 - Only UIAbilities of the current app can be started.

**Since**: 26.0.0

**System capability:** SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
|-------|-------|-------|-------|
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes | Information about the UIAbility to start, including attributes such as bundleName and abilityName, used to specify the target UIAbility. |
| options | [StartOptions](../apis-ability-kit/js-apis-app-ability-startOptions.md) | No | Start options for configuring the window mode of the UIAbility. Pass this parameter when custom start configuration is required; otherwise, the default system start configuration is used. For details about the default values of each field, see [StartOptions](../apis-ability-kit/js-apis-app-ability-startOptions.md). |

**Return value**

| Type | Description |
|------|------|
|Promise&lt;[AbilityResult](../apis-ability-kit/js-apis-inner-ability-abilityResult.md)&gt; | Promise used to return the result code and data when the started ability exits. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID | Error Message                                 |
| -------- | ----------------------------------------|
| 201      | The application does not have permission to call the interface. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000008 | The crowdtesting application expires.  |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled by the AppGallery and cannot be started. |
| 16000013 | The application is controlled by Enterprise Device Manager and cannot be started. |
| 16000019 | No matching ability is found. |
| 16000050 | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module. |
| 16000055 | Installation-free timed out. |
| 16000071 | The application does not support appClone mode in multiAppMode. |
| 16000072 | The application does not support appClone and multi-instance mode in multiAppMode. |
| 16000073 | The app clone index is invalid. |
| 16000076 | The app instance key is invalid. |
| 16000077 | The number of app instances reaches the limit. |
| 16000078 | The application does not support multiple instances. |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. |
| 16000080 | Instances cannot be created for other applications during inter-application startup. |

**Example**

```ts
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { Want, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export class MyWebNativeMessagingExtension extends WebNativeMessagingExtensionAbility {
  onConnectNative(info: ConnectionInfo): void {
    const abilityWant: Want = {
      bundleName: 'com.example.mybundle', // Replace with the actual bundleName.
      abilityName: 'MainAbility' // Replace with the actual abilityName.
    };
    try {
      const context = this.context; // Obtain the WebNativeMessagingExtensionContext instance.
      context.startAbilityForResult(abilityWant).then((result: common.AbilityResult) => {
        console.info(`Ability started successfully, result code: ${result.resultCode}`);
        if (result.want) {
          console.info(`Result data: ${JSON.stringify(result.want)}`);
        }
      }).catch((err: BusinessError) => {
        console.error(`Failed to start ability. Code: ${(err as BusinessError).code},
        Message:${(err as BusinessError).message}`);
      });
    } catch (err) {
      console.error(`Failed to start ability. Code: ${(err as BusinessError).code},
      Message: ${(err as BusinessError).message}`);
    }
  }
}
```

### terminateSelf

terminateSelf(): Promise&lt;void&gt;

Destroys the current native web message extension. This method returns a promise for asynchronous processing. Calling this method automatically stops all native web message connections, so there is no need to call stopNativeConnection.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type| Description|
|------|------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | ------------------------- |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000011 | The context does not exist.      |
| 16000050 | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module. |

**Example**

```ts
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

export class MyWebNativeMessagingExtension extends WebNativeMessagingExtensionAbility {
  onConnectNative(info: ConnectionInfo): void {
    try {
        const context = this.context; // Obtain the WebNativeMessagingExtensionContext instance.
        context.terminateSelf().then(() => {
          console.info('Extension terminated successfully');
        }).catch((err: BusinessError) => {
          console.error(`Failed to terminate extension. Code: ${(err as BusinessError).code},
          Message: ${(err as BusinessError).message}`);
        });       
    } catch (err) {
        console.error(`Failed to terminate extension. Code: ${(err as BusinessError).code},
        Message: ${(err as BusinessError).message}`);
    }
  }
}
```

### stopNativeConnection

stopNativeConnection(connectionId: number): Promise&lt;void&gt;

Stops the specified native connection. This API uses a promise to return the result.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
|-------|-------|-------|-------|
| connectionId | number | Yes | ID of the connection to stop. The value must be a positive integer and a valid connection ID. If the connectionId value is invalid, a corresponding error code is returned. |

**Return value**

| Type| Description|
|------|------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
|---------|----------|
| 201 | The application does not have permission to call the interface. |
| 16000011 | The context does not exist.      |
| 16000050 | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module. |

**Example**

```ts
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

export class MyWebNativeMessagingExtension extends WebNativeMessagingExtensionAbility {
  onConnectNative(info: ConnectionInfo): void {
    const CONNECTION_ID = 12345; // Actual connection ID.
    try {
        const context = this.context;// Obtain the WebNativeMessagingExtensionContext instance.
        context.stopNativeConnection(CONNECTION_ID).then(() => {
          console.info('Native connection stopped successfully');
        }).catch((err: BusinessError) => {
          console.error(`Failed to stop native connection. Code: ${(err as BusinessError).code},
          Message: ${(err as BusinessError).message}`);
        })
    } catch (err) {
        console.error(`Failed to stop native connection. Code: ${(err as BusinessError).code},
        Message: ${(err as BusinessError).message}`);
    }
  }
}
```