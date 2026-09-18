# UIServiceExtensionContext (System API)

The UIServiceExtensionContext module provides the context environment for a [UIServiceExtensionAbility](arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md). It inherits from [ExtensionContext](arkts-ability-extensioncontext-c.md).

UIServiceExtensionContext provides access to a [UIServiceExtensionAbility](arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md) and APIs for operating the ability, for example, starting, terminating, connecting, and disconnecting ability.

> **NOTE:** 
> 
> - The APIs of this module must be used on the main thread, but not on child threads such as Worker and TaskPool.

**Inheritance/Implementation:** UIServiceExtensionContext extends [ExtensionContext](arkts-ability-extensioncontext-c.md)

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## connectServiceExtensionAbility

```TypeScript
connectServiceExtensionAbility(want: Want, options: ConnectOptions): number
```

Connects to a [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) and returns the connection ID.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want parameter. |
| options | [ConnectOptions](arkts-ability-connectoptions-connectoptions-i.md) | Yes | Connection options. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Connection ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |

**Examples**

```TypeScript
import { common, Want } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[Page_ServiceExtensionAbility]';
const DOMAIN_NUMBER: number = 0xFF00;

// The connectionId must be obtained from the return value of the connectServiceExtensionAbility API and saved.
let connectionId: number = 0; // Example value. Use the connection ID returned by connectServiceExtensionAbility in practice.
// Set the information about the background service Ability to connect.
let want: Want = {
  deviceId: '',
  bundleName: 'com.samples.stagemodelabilitydevelop',
  abilityName: 'ServiceExtAbility'
  };

// Set the connection option callbacks.
let options: common.ConnectOptions = {
  // Callback invoked when the connection is successful.
  onConnect(elementName, remote: rpc.IRemoteObject): void {
    hilog.info(DOMAIN_NUMBER, TAG, 'onConnect callback');
  },
  // Callback invoked when the connection is disconnected.
  onDisconnect(elementName): void {
    hilog.info(DOMAIN_NUMBER, TAG, 'onDisconnect callback');
  },
  // Callback invoked when the connection fails.
  onFailed(code: number): void {
    hilog.info(DOMAIN_NUMBER, TAG, `onFailed callback, ${code}`);
  }
};

@Entry
@Component
struct Page_UIServiceExtensionAbility {
  build() {
    Column() {
      List({ initialIndex: 0 }) {
        ListItem() {
          Row() {
          }
          .onClick(() => {
            let context: common.UIServiceExtensionContext =
              this.getUIContext().getHostContext() as common.UIServiceExtensionContext;
            // Save the ID returned after a successful connection for subsequent disconnection.
            connectionId = context.connectServiceExtensionAbility(want, options);
            // The background service is connected.
            this.getUIContext().getPromptAction().showToast({
              message: 'SuccessfullyConnectBackendService'
            });
            // connectionId = context.connectAbility(want, options);
            hilog.info(DOMAIN_NUMBER, TAG, `connectionId is : ${connectionId}`);
          })
        }
      }
    }
  }
}
```

## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connectionId: number): Promise<void>
```

Disconnects from a [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md). This API is opposite to [connectServiceExtensionAbility](#connectserviceextensionability). This API uses a promise to return the result.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| connectionId | number | Yes | Connection ID returned by [connectServiceExtensionAbility](#connectserviceextensionability). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

const TAG: string = '[Page_ServiceExtensionAbility]';
const DOMAIN_NUMBER: number = 0xFF00;

// Obtain and save connectionId from the return value of the connectServiceExtensionAbility API.
let connectionId: number = 0; // Example value. Use the connection ID returned by connectServiceExtensionAbility in actual scenarios.

@Entry
@Component
struct Page_UIServiceExtensionAbility {
  build() {
    Column() {
      List({ initialIndex: 0 }) {
        ListItem() {
          Row() {
          }
          .onClick(() => {
            let context: common.UIServiceExtensionContext =
              this.getUIContext().getHostContext() as common.UIServiceExtensionContext;
            // connectionId is returned when connectServiceExtensionAbility is called and needs to be manually maintained.
            context.disconnectServiceExtensionAbility(connectionId).then(() => {
              hilog.info(DOMAIN_NUMBER, TAG, 'disconnectServiceExtensionAbility success');
              // The background service is disconnected.
              this.getUIContext().getPromptAction().showToast({
                message: 'SuccessfullyDisconnectBackendService'
              });
            }).catch((err: BusinessError) => {
              hilog.error(DOMAIN_NUMBER, TAG,
                `disconnectServiceExtensionAbility failed, err code: ${err.code}, err msg: ${err.message}`);
            });
          })
        }
      }
    }
  }
}
```

## startAbility

```TypeScript
startAbility(want: Want, options?: StartOptions): Promise<void>
```

Starts an ability. This API uses a promise to return the result.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target ability, such as the ability name and bundle name. |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | No | Parameters used for starting the ability. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |

**Examples**

```TypeScript
import { UIServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class UIEntryAbility extends UIServiceExtensionAbility {
  onCreate() {
    // Set the Want parameter for starting the Ability.
    let want: Want = {
      bundleName: 'com.example.myapp',
      abilityName: 'MyAbility'
    };
    // Set the startup option parameter.
    let options: StartOptions = {
      windowMode: 0,
    };

    try {
      this.context.startAbility(want, options)
        .then((data: void) => {
          // Carry out normal service processing.
          console.info('startAbility succeed');
        })
        .catch((error: BusinessError) => {
          // Process service logic errors.
          console.error(`startAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
    }
  }
}
```

## startAbilityByType

```TypeScript
startAbilityByType(type: string, wantParam: Record<string, Object>,
    abilityStartCallback: AbilityStartCallback): Promise<void>
```

Starts a [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) or [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) based on the type of the target ability. This API can be called only by applications running in the foreground. This API uses a promise to return the result.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the target ability. |
| wantParam | Record&lt;string, Object&gt; | Yes | Want parameter. |
| abilityStartCallback | [AbilityStartCallback](arkts-ability-abilitystartcallback-c.md) | Yes | Callback invoked to return the UIExtensionAbility startup result. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const TAG: string = '[Extension_Sub] ';

@Entry
@Component
struct SubIndex {
  build() {
    Row() {
      Column() {
        Button("startAbilityByType")
          .fontSize(10)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            let context = this.getUIContext().getHostContext() as common.UIServiceExtensionContext;
            let startWant: Record<string, Object> = {
              'sceneType': 1,
              'email': [encodeURI('xxx@example.com'),
                encodeURI('xxx@example.com')], // Email address of the recipient. Multiple values are separated by commas (,). The array content is URL-encoded using the **encodeURI()** method.
              'cc': [encodeURI('xxx@example.com'),
                encodeURI('xxx@example.com')], // Email addresses of the CC recipients, separated by commas. Use the encodeURI() method to URL-encode the array content.
              'bcc': [encodeURI('xxx@example.com'),
                encodeURI('xxx@example.com')], // Email address of the BCC recipient. Multiple values are separated by commas (,). The array content is URL-encoded using the **encodeURI()** method.
              'subject': encodeURI('Email subject'), // Email subject. The content is URL encoded using encodeURI().
              'body': encodeURI('Email body'), // Email body. The content is URL encoded using encodeURI().
              'ability.params.stream': [encodeURI ('attachment uri1'),
                encodeURI ('attachment uri2') ], // Attachment URI. Multiple values are separated by commas (,). The array content is URL-encoded using the encodeURI() method.
              'ability.want.params.uriPermissionFlag': 1
            };
            // Define the callback object for the startup result.
            let abilityStartCallback: common.AbilityStartCallback = {
              // Handle the error callback for startup failure.
              onError: (code: number, name: string, message: string) => {
                console.error(TAG + `code: ${code}  name:${name}  message:${message}`);
              }
            };
            try {
              // Start a UIAbility or UIExtensionAbility based on the type of the target ability.
              context.startAbilityByType("mail", startWant, abilityStartCallback)
                .then(() => {
                  console.info(TAG + `Succeeded in windows starting ability`);
                }).catch((err: BusinessError) => {
                console.error(TAG +
                  `Failed to windows starting ability, Code is ${err.code}, message is ${err.message}.`);
              })
            } catch (err) {
              let code = (err as BusinessError).code;
              let msg = (err as BusinessError).message;
              console.error(TAG + `Failed to windows starting ability, Code is ${code}, message is ${msg}.`);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## terminateSelf

```TypeScript
terminateSelf(): Promise<void>
```

Terminates this [UIServiceExtensionAbility](arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md). This API uses a promise to return the result.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { UIServiceExtensionAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class UIEntryAbility extends UIServiceExtensionAbility {
  onCreate() {
    // Destroy the UIServiceExtension.
    this.context.terminateSelf().then(() => {
      // Carry out normal service processing.
      console.info('terminateSelf succeed');
    }).catch((error: BusinessError) => {
      // Process service logic errors.
      console.error(`terminateSelf failed, error.code: ${error.code}, error.message: ${error.message}`);
    });
  }
}
```
