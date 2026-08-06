# @ohos.app.ability.DriverExtensionAbility (Driver Extension Ability)

<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=8d1ca05d9b18e147419c1df75bcc96772783cea1 translatedAt=2026-08-06T06:34:40.360Z pushedAt=2026-08-06T06:38:09.023Z -->

The **DriverExtensionAbility** module provides the ExtensionAbility related to drivers. It provides lifecycle callbacks to be invoked when a driver is created, destroyed, connected, or disconnected.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.  

## Modules to Import

```ts
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
```

## DriverExtensionAbility

### Properties

**DriverExtensionAbility** class, which contains the definition of driver lifecycle callbacks.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Driver.ExternalDevice

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| context | [DriverExtensionContext](js-apis-inner-application-driverExtensionContext.md) | No | No | Context of the DriverExtension, inherited from ExtensionContext. |

### onInit

onInit(want: Want): void

Called when a DriverExtensionAbility is created to initialize the service logic.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Driver.ExternalDevice

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| want |  [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes | Want type information related to the current Extension, including the ability name and bundle name. |

**Example**

  ```ts
  import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
  import { Want } from '@kit.AbilityKit';

  class DriverExt extends DriverExtensionAbility {
    onInit(want : Want) {
      console.info(`onInit, want: ${want.abilityName}`);
    }
  }
  ```

### onRelease

onRelease(): void

Called when this DriverExtensionAbility is destroyed to clear resources.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Driver.ExternalDevice

**Example**

  ```ts
  class DriverExt extends DriverExtensionAbility {
    onRelease() {
      console.info('onRelease');
    }
  }
  ```

### onConnect

onConnect(want: Want): rpc.RemoteObject | Promise&lt;rpc.RemoteObject&gt;

Called following [onCreate](../apis-ability-kit/js-apis-app-ability-abilityStage.md#oncreate). A [RemoteObject](../apis-ipc-kit/js-apis-rpc.md#remoteobject) object is returned for communication between the server and client.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Driver.ExternalDevice

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes | Want type information related to the current Extension, including the ability name, bundle name, etc. |

**Return value**

| Type | Description |
| -------- | -------- |
| rpc.[RemoteObject](../apis-ipc-kit/js-apis-rpc.md#remoteobject) \| Promise&lt;rpc.[RemoteObject](../apis-ipc-kit/js-apis-rpc.md#remoteobject)&gt; | A RemoteObject object used for communication between the client and server, or a Promise object that returns a RemoteObject object for communication. |

**Example**

  ```ts
  import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
  import { rpc } from '@kit.IPCKit';
  import { Want } from '@kit.AbilityKit';

  class StubTest extends rpc.RemoteObject{
      constructor(des : string) {
          super(des);
      }
      onRemoteMessageRequest(code : number, data : rpc.MessageSequence, reply : rpc.MessageSequence, option : rpc.MessageOption) {
        // Override this interface.
        return true;
      }
  }
  class DriverExt extends DriverExtensionAbility {
    onConnect(want : Want) {
      console.info(`onConnect , want: ${want.abilityName}`);
      return new StubTest('test');
    }
  }
  ```

If the returned [RemoteObject](../apis-ipc-kit/js-apis-rpc.md#remoteobject) object depends on an asynchronous API, you can use the asynchronous lifecycle.

  ```ts
  import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
  import { rpc } from '@kit.IPCKit';
  import { Want } from '@kit.AbilityKit';
  
  class StubTest extends rpc.RemoteObject{
      constructor(des : string) {
          super(des);
      }
      onRemoteMessageRequest(code : number, data : rpc.MessageSequence, reply : rpc.MessageSequence, option : rpc.MessageOption) {
        // Must override this API.
        return true;
      }
  }
  async function getDescriptor() {
      // Call the asynchronous function...
      return "asyncTest";
  }
  class DriverExt extends DriverExtensionAbility {
    async onConnect(want : Want) {
      console.info(`onConnect , want: ${want.abilityName}`);
      let descriptor = await getDescriptor();
      return new StubTest(descriptor);
    }
  }
  ```

### onDisconnect

onDisconnect(want: Want): void | Promise\<void>

Called when a client is disconnected from this **DriverExtensionAbility**.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Driver.ExternalDevice

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| want |[Want](../apis-ability-kit/js-apis-app-ability-want.md)| Yes | Want type information about the current Extension, including the ability name and bundle name. |

**Return value**

| Type | Description |
| -------- | -------- |
| void \| Promise\<void> | No return value; or a Promise object that returns no result. |

**Example**

  ```ts
  import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
  import { Want } from '@kit.AbilityKit';

  class DriverExt extends DriverExtensionAbility {
    onDisconnect(want : Want) {
      console.info(`onDisconnect, want: ${want.abilityName}`);
    }
  }
  ```

After the **onDisconnect** lifecycle callback is executed, the application may exit. As a result, the asynchronous function in **onDisconnect** may fail to be executed correctly, for example, asynchronously writing data to the database. The asynchronous lifecycle can be used to ensure that the subsequent lifecycle continues after the asynchronous **onDisconnect** is complete.

  ```ts
  import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
  import { Want } from '@kit.AbilityKit';

  class DriverExt extends DriverExtensionAbility {
    async onDisconnect(want : Want) {
      console.info(`onDisconnect, want: ${want.abilityName}`);
      // Call the asynchronous function...
    }
  }
  ```

### onDump

onDump(params: Array&lt;string&gt;): Array&lt;string&gt;

Dumps client information. You are advised not to dump sensitive information.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Driver.ExternalDevice

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| params | Array&lt;string&gt; | Yes | Command parameters. |

**Return value**

| Type | Description |
| -------- | -------- |
| Array&lt;string&gt; | Array of strings used to dump client information. |

**Example**

  ```ts
  class DriverExt extends DriverExtensionAbility {
      onDump(params : Array<string>) {
          console.info(`dump, params: ${JSON.stringify(params)}`);
          return ['params'];
      }
  }
  ```

## DriverExtensionContext

type DriverExtensionContext = _DriverExtensionContext;

**DriverExtensionAbility** context.

**System capability**: SystemCapability.Driver.ExternalDevice

| Type | Description |
| -------- | -------- |
| _DriverExtensionContext | Context of DriverExtensionAbility, which inherits from ExtensionContext. For details about how to use it, see [DriverExtensionContext](js-apis-inner-application-driverExtensionContext.md).|