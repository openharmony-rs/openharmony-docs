# AppServiceExtensionContext (ExtensionAbility Context for Application Background Services)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @xialiangwei-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=7fe4eacae9c952d492316e40f501d71d3714186d translatedAt=2026-09-03T11:44:15.834Z pushedAt=2026-09-05T10:47:30.683Z -->

The AppServiceExtensionContext module is the context environment of [AppServiceExtensionAbility](js-apis-app-ability-appServiceExtensionAbility.md) and inherits from [ExtensionContext](js-apis-inner-application-extensionContext.md). It provides the capabilities to connect to and disconnect from a ServiceExtensionAbility (an ExtensionAbility for system application background services), as well as the capability for an AppServiceExtensionAbility to terminate itself. It can be used by third-party applications to communicate with system background services.


> **NOTE**
> 
>  - The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>  - The APIs of this module can be used only in the stage model.
>  - The APIs of this module must be used in the main thread, but not in child threads such as Worker and TaskPool.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## Instructions

Before using the AppServiceExtensionContext module, obtain an AppServiceExtensionContext instance through an AppServiceExtensionAbility subclass instance.

**Example**

```ts
import { AppServiceExtensionAbility, Want } from '@kit.AbilityKit';

export default class AppServiceExtension extends AppServiceExtensionAbility {
  onCreate(want: Want) {
    let context = this.context; // Obtain an AppServiceExtensionContext instance.
  }
}
```

## AppServiceExtensionContext

### startAbility

startAbility(want: Want, options?: StartOptions): Promise&lt;void&gt;

Starts a UIAbility. After this API is called, the system starts the target UIAbility based on the Want information. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md)  | Yes| Want information about the target ability, such as the ability name and bundle name.|
| options | [StartOptions](js-apis-app-ability-startOptions.md) | No | Parameters carried for starting the ability. Pass this parameter when you need to specify startup parameters such as the window mode, display device, and process mode. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden.        |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled.        |
| 16000013 | The application is controlled by EDM.       |
| 16000019 | No matching ability is found. |
| 16000050 | Internal error. |
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
import { AppServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAppServiceExtensionAbility extends AppServiceExtensionAbility {
  onCreate(want: Want) {
    let wantInfo: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      displayId: 0
    };

    try {
      this.context.startAbility(wantInfo, options)
        .then(() => {
          // Carry out normal service processing.
          console.info('startAbility succeed');
        })
        .catch((err: BusinessError) => {
          // Process service logic errors.
          console.error(`startAbility failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### connectServiceExtensionAbility

connectServiceExtensionAbility(want: Want, callback: ConnectOptions): number

Connects this AppServiceExtensionAbility to a ServiceExtensionAbility (a ServiceExtensionAbility can be developed only by system applications, but third-party applications can connect to it). It enables communication with the ServiceExtensionAbility through the remote object returned by the onConnect callback of ConnectOptions, allowing access to the capabilities exposed by the ServiceExtensionAbility. You can use the returned connectionID to call disconnectServiceExtensionAbility() to disconnect.

> **NOTE**
>
> This API does not support connecting to the ServiceExtensionAbility of a cloned application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes | Want type parameter, which carries the information about the Ability to connect, such as the Ability name and bundle name. |
| callback | [ConnectOptions](js-apis-inner-ability-connectOptions.md) | Yes | ConnectOptions type callback used to listen for service connection state changes, including connection success, connection failure, and disconnection. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Connection identifier, used to disconnect the connection later via [disconnectServiceExtensionAbility](#disconnectserviceextensionability). |

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist.        |
| 16000050 | Internal error. |

**Example**

```ts
import { AppServiceExtensionAbility, Want, common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let commRemote: rpc.IRemoteObject | null = null; // Release the instance when the connection is disconnected.
const TAG: string = '[AppServiceExtensionAbility]';

export default class AppServiceExtension extends AppServiceExtensionAbility {
  connection: number = 0;

  onCreate(want: Want) {
    let wantInfo: Want = {
      bundleName: 'com.example.myapp',
      abilityName: 'MyAbility'
    };
    let callback: common.ConnectOptions = {
      onConnect(elementName, remote) {
        commRemote = remote;
        hilog.info(0x0000, TAG, '----------- onConnect -----------');
      },
      onDisconnect(elementName) {
        hilog.info(0x0000, TAG, '----------- onDisconnect -----------');
      },
      onFailed(code) {
        hilog.error(0x0000, TAG, '----------- onFailed -----------');
      }
    };


    try {
      this.connection = this.context.connectServiceExtensionAbility(wantInfo, callback);
    } catch (paramError) {
      commRemote = null;
      // Process input parameter errors.
      hilog.error(0x0000, TAG, `error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }

  onDestroy(): void {
    this.context.disconnectServiceExtensionAbility(this.connection).then(() => {
      commRemote = null;
      // Carry out normal service processing.
      hilog.info(0x0000, TAG, '----------- disconnectServiceExtensionAbility success -----------');
    })
      .catch((error: BusinessError) => {
        commRemote = null;
        // Process service logic errors.
        hilog.error(0x0000, TAG, `disconnectServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
      });
  }
}
```

### disconnectServiceExtensionAbility

disconnectServiceExtensionAbility(connection: number): Promise&lt;void&gt;

Disconnects this AppServiceExtensionAbility from a connected ServiceExtensionAbility. The connection parameter is the connection ID returned by connectServiceExtensionAbility(). This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| connection | number | Yes | Connection ID returned by [connectServiceExtensionAbility](#connectserviceextensionability). |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object that returns no value. |

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 16000011 | The context does not exist.        |
| 16000050 | Internal error. |

**Example**

For details, see [connectServiceExtensionAbility](#connectserviceextensionability).

### terminateSelf

terminateSelf(): Promise&lt;void&gt;

Destroys this AppServiceExtensionAbility. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object that returns no value. |

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000011 | The context does not exist.        |
| 16000050 | Internal error. |

**Example**

```ts
import { AppServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AppServiceExtensionAbility]';

export default class AppServiceExtension extends AppServiceExtensionAbility {
  onCreate(want: Want) {
    this.context.terminateSelf().then(() => {
      // Carry out normal service processing.
      hilog.info(0x0000, TAG, '----------- terminateSelf succeed -----------');
    }).catch((error: BusinessError) => {
      // Process service logic errors.
      hilog.error(0x0000, TAG, `terminateSelf failed, error.code: ${error.code}, error.message: ${error.message}`);
    });
  }
}
```
