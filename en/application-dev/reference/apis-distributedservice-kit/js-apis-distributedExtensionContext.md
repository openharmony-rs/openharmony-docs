# @ohos.application.DistributedExtensionContext (Distributed Extension Context)
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @w_Machine_cc-->

The **DistributedExtensionContext** module provides the context environment for **DistributedExtensionAbility**, inherited from **ExtensionContext**.

> **NOTE**
>
> The initial APIs of this module are supported since API version 26. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## How to Use

Before using the capabilities of **DistributedExtensionContext**, obtain the context through a **DistributedExtensionAbility** subclass instance.

```ts
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onCreate() {
    let context = this.context; // Obtain DistributedExtensionContext.
  }
}
```

## DistributedExtensionContext.connectServiceExtensionAbility

connectServiceExtensionAbility(want: Want, options: ConnectOptions): number

Connects to a remote ServiceExtensionAbility.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Parameters**

| Name    | Type                                                          | Mandatory| Description                                                                                                                                                   |
| ------- | ------------------------------------------------------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| want    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)       | Yes  | Want parameter, which carries the information about the remote ServiceExtensionAbility to connect, such as the ability name, bundle name, and deviceId. |
| options | [ConnectOptions](../apis-ability-kit/js-apis-inner-ability-connectOptions.md) | Yes  | Callback of the **ConnectOptions** type, which returns the connection result, disconnection notification, or failure information.                        |

**Return value**

| Type    | Description                                                                                                                                                       |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| number | Connection ID, which is returned by **connectServiceExtensionAbility**. You can use this ID to disconnect from the ability. The ID is an auto-increment number. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message                                                                                                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.                             |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. |
| 16000013 | The application is controlled by EDM. |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let connectionId: number = -1;

export default class DistributedExtension extends DistributedExtensionAbility {
    try {
      connectionId = this.context.connectServiceExtensionAbility(want, options);
      console.info(`connectServiceExtensionAbility success, connectionId: ${connectionId}`);
    } catch (err) {
      let error = err as BusinessError;
      console.error(`connectServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
    }
}
```



## DistributedExtensionContext.disconnectServiceExtensionAbility

disconnectServiceExtensionAbility(connection: number): Promise\<void\>

Disconnects from a remote ServiceExtensionAbility. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Parameters**

| Name       | Type    | Mandatory| Description                                                                |
| ---------- | ------- | ---- | ------------------------------------------------------------------ |
| connection | number  | Yes  | Connection ID, which is returned by **connectServiceExtensionAbility**. |

**Return value**

| Type           | Description                                 |
| -------------- | ------------------------------------------- |
| Promise\<void\> | Promise that returns no value.               |

**Error codes**

For details about the error codes, see [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message                                                                                                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 16000003 | The connection id does not exist. |
| 16000011 | The ability has been destroyed. The context is no longer valid, meaning the context does not exist. |
| 16000050 | Internal error. |                                                                                                                                                      |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';

// connectionId is returned by connectServiceExtensionAbility.
let connectionId: number = -1;

export default class DistributedExtension extends DistributedExtensionAbility {
  disconnectRemoteService() {
    try {
      this.context.disconnectServiceExtensionAbility(connectionId)
        .then(() => {
          console.info('disconnectServiceExtensionAbility success');
        })
        .catch((err: BusinessError) => {
          console.error(`disconnectServiceExtensionAbility failed, error.code: ${err.code}, error.message: ${err.message}`);
        });
    } catch (err) {
      let error = err as BusinessError;
      console.error(`disconnectServiceExtensionAbility catch error, code: ${error.code}, message: ${error.message}`);
    }
  }
}
```
