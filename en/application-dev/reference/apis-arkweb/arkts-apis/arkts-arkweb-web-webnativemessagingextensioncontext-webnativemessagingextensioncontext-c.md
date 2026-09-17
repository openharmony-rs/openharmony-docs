# WebNativeMessagingExtensionContext

WebNativeMessagingExtensionContext is the runtime context of the native web message extension ([WebNativeMessagingExtensionAbility](arkts-arkweb-web-webnativemessagingextensionability-webnativemessagingextensionability-c.md)). It inherits from ExtensionContext and provides lifecycle management, ability startup, and native message connection control capabilities for the extension ability. In an extension that inherits from WebNativeMessagingExtensionAbility, developers can obtain this context through `this.context` and then call [startAbility](#startability) to start another ability, call [startAbilityForResult](#startabilityforresult) to start a UIAbility and receive the return result, call [terminateSelf](#terminateself) to terminate the current extension, or call [stopNativeConnection](#stopnativeconnection) to stop a specified native web message connection.

**Inheritance/Implementation:** WebNativeMessagingExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## startAbility

```TypeScript
startAbility(want: Want, options?: StartOptions): Promise<void>
```

Starts an ability. This API uses a promise to return the result. To obtain the return result when the started UIAbility exits, use [startAbilityForResult](#startabilityforresult).

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Information about the Ability to start, including bundleName, abilityName, and other attributes, used to specify the target Ability to start. |
| options | [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md) | No | Start options used to specify the options when starting the target UIAbility, including but not limited to the window mode and the screen where the target UIAbility is started. This parameter is passed when custom startup configuration is needed; if not passed, the default system startup configuration is used. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16000071](../../apis-ability-kit/errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported. |
| [16000072](../../apis-ability-kit/errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported. |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid. |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid. |
| [16000077](../../apis-ability-kit/errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit. |
| [16000078](../../apis-ability-kit/errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported. |
| [16000079](../../apis-ability-kit/errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified. |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported. |

**Examples**

```TypeScript
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

## startAbilityForResult

```TypeScript
startAbilityForResult(want: Want, options?: StartOptions): Promise<AbilityResult>
```

Starts a UIAbility. This API uses a promise to return the result when the started UIAbility exits.

After the UIAbility is started, the following situations may occur:

- Under normal circumstances,[terminateSelfWithResult](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md#terminateselfwithresult) can be called to terminate the UIAbility and return the result to the caller.  
- In abnormal cases, such as when the UIAbility is destroyed, exception information is returned to the caller, with  
resultCode set to -1.  
- Only UIAbilities of the current app can be started.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Information about the UIAbility to start, including attributes such as bundleName and abilityName, used to specify the target UIAbility. |
| options | [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md) | No | Start options for configuring the window mode of the UIAbility. Pass this parameter when custom start configuration is required; otherwise, the default system start configuration is used. For details about the default values of each field, see [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AbilityResult](../../apis-ability-kit/arkts-apis/arkts-ability-abilityresult-abilityresult-i.md)&gt; | Promise used to return the result code and data when the started ability exits. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-application-under-control) | The application is controlled by the AppGallery and cannot be started. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by Enterprise Device Manager and cannot be started. |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16000071](../../apis-ability-kit/errorcode-ability.md#16000071-application-clone-is-not-supported) | The application does not support appClone mode in multiAppMode. |
| [16000072](../../apis-ability-kit/errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | The application does not support appClone and multi-instance mode in multiAppMode. |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid. |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid. |
| [16000077](../../apis-ability-kit/errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit. |
| [16000078](../../apis-ability-kit/errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The application does not support multiple instances. |
| [16000079](../../apis-ability-kit/errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified. |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-new-instances-cannot-be-created) | Instances cannot be created for other applications during inter-application startup. |

**Examples**

```TypeScript
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

## stopNativeConnection

```TypeScript
stopNativeConnection(connectionId: number): Promise<void>
```

Stops the specified native connection. This API uses a promise to return the result.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| connectionId | number | Yes | ID of the connection to stop. The value must be a positive integer and a valid connection ID. If the connectionId value is invalid, a corresponding error code is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module. |

**Examples**

```TypeScript
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

## terminateSelf

```TypeScript
terminateSelf(): Promise<void>
```

Destroys the current native web message extension. This method returns a promise for asynchronous processing. Calling this method automatically stops all native web message connections, so there is no need to call stopNativeConnection.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module. |

**Examples**

```TypeScript
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
