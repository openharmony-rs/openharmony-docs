# UIServiceExtensionContext (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @xhz-sz-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=7fe4eacae9c952d492316e40f501d71d3714186d translatedAt=2026-09-03T12:11:56.437Z pushedAt=2026-09-05T10:47:30.888Z -->

The UIServiceExtensionContext module provides the context environment for a [UIServiceExtensionAbility](js-apis-app-ability-uiServiceExtensionAbility-sys.md). It inherits from [ExtensionContext](js-apis-inner-application-extensionContext.md).

The UIServiceExtensionContext module provides access to the specific resources and capabilities of [UIServiceExtension](js-apis-app-ability-uiServiceExtensionAbility-sys.md), including starting an ability, destroying a UIServiceExtension, and connecting to and disconnecting from a UIExtensionAbility.

> **NOTE**
>
>  - The initial APIs of this module are supported since API version 14. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>  - The APIs of this module can be used only in the stage model.
>  - The APIs of this module must be used on the main thread, but not on child threads such as Worker and TaskPool.
>  - The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## How to Use

Before using the APIs of UIServiceExtensionContext, you must obtain the context through a child class instance [UIServiceExtensionAbility](js-apis-app-ability-uiServiceExtensionAbility-sys.md).

**Example**

```ts
import { common, UIServiceExtensionAbility } from '@kit.AbilityKit';

class UIServiceExtAbility extends UIServiceExtensionAbility {
  onCreate() {
    // Obtain the UIServiceExtensionContext.
    let context:common.UIServiceExtensionContext = this.context;
  }
}
```


## UIServiceExtensionContext.startAbility

startAbility(want: Want, options?: StartOptions): Promise&lt;void&gt;

Starts an ability. This API uses a promise to return the result.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md)  | Yes| Want information about the target ability, such as the ability name and bundle name.|
| options | [StartOptions](js-apis-app-ability-startOptions.md) | No | Parameters carried for starting the Ability, used to customize the startup configuration (such as window mode and display mode). Pass this parameter when custom startup behavior is required; otherwise, the system default startup configuration is used. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden.        |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled.        |
| 16000013 | The application is controlled by EDM.       |
| 16000019 | No matching ability is found.       |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16200001 | The caller has been released. |

**Example**

```ts
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


## UIServiceExtensionContext.terminateSelf

terminateSelf(): Promise&lt;void&gt;

Terminates this [UIServiceExtensionAbility](js-apis-app-ability-uiServiceExtensionAbility-sys.md). This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

```ts
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

## UIServiceExtensionContext.startAbilityByType

startAbilityByType(type: string, wantParam: Record&lt;string, Object&gt;, abilityStartCallback: AbilityStartCallback): Promise&lt;void&gt;

Starts a [UIAbility](js-apis-app-ability-uiAbility.md) or [UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md) based on the type of the target ability. This API can be called only by applications running in the foreground. This API uses a promise to return the result.


> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- |  -------- |
| type | string | Yes | Type of the target ability. Predefined type values are supported. If an unsupported type value is passed in, the API returns error code 401. |
| wantParam | Record&lt;string, Object&gt;| Yes| Want parameter.|
| abilityStartCallback | [AbilityStartCallback](js-apis-inner-application-abilityStartCallback.md) | Yes | Callback used to return the result of starting the UIExtensionAbility, including callback functions such as error handling. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050  | Internal error.                                                                                         |

**Example**

```ts
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

## UIServiceExtensionContext.connectServiceExtensionAbility

connectServiceExtensionAbility(want: Want, options: ConnectOptions): number

Connects to a [ServiceExtensionAbility](js-apis-app-ability-serviceExtensionAbility-sys.md#serviceextensionability) and returns the connection ID. This API is used when you need to establish a connection with a ServiceExtensionAbility for interaction, for example, connecting to a ServiceExtensionAbility provided by another application to use its services.


> **NOTE**
>
> - For details about the component startup rules, see [Intra-device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-cross-device-sys.md).
> - This API does not support connecting to the ServiceExtensionAbility of a cloned application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name              | Type                    | Mandatory| Description             |
| -------------------- | ------------------------ | ---- |----------------- |
| want                 | [Want](js-apis-app-ability-want.md) | Yes | Want parameter, used to pass in the information about the UIExtensionAbility to connect, such as the Ability name and bundle name.       |
| options              | [ConnectOptions](js-apis-inner-ability-connectOptions.md) | Yes| Connection options.|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Connection ID, which the developer needs to save for subsequent disconnection. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message |
| -------- | --- |
| 201     | The application does not have permission to call the interface.   |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001  | The specified ability does not exist.         |
| 16000002   | Incorrect ability type.         |
| 16000004   | Cannot start an invisible component.         |
| 16000005   | The specified process does not have the permission.         |
| 16000006   | Cross-user operations are not allowed.         |
| 16000008   | The crowdtesting application expires.        |
| 16000011   | The context does not exist.         |
| 16000012 | The application is controlled. |
| 16000013   | The application is controlled by EDM.       |
| 16000050   | Internal error.        |
| 16000053   | The ability is not on the top of the UI.        |
| 16000055   | Installation-free timed out.         |


**Example**

```ts
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

## UIServiceExtensionContext.disconnectServiceExtensionAbility

disconnectServiceExtensionAbility(connectionId: number): Promise&lt;void&gt;

Disconnects from a [UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md). This API is the reverse of [connectServiceExtensionAbility](#uiserviceextensioncontextconnectserviceextensionability) and uses a promise to return the result. This API is used when you no longer need to interact with a UIExtensionAbility, for example, to release resources after a service is complete.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name               | Type                    | Mandatory| Description             |
| -------------------- | ------------------------ | ---- | ----------------- |
| connectionId         | number                   | Yes | Connection ID returned by [connectServiceExtensionAbility](#uiserviceextensioncontextconnectserviceextensionability), which must be a valid connection ID. |


**Return value**

| Type               | Description                             |
| ------------------- | ---------------------------------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| -------- | --------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000011  | The context does not exist.      |
| 16000050 | Internal error.      |

**Example**

```ts
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
