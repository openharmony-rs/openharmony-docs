# @ohos.app.ability.ServiceExtensionAbility (ServiceExtensionAbility) (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @xialiangwei-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=7fe4eacae9c952d492316e40f501d71d3714186d translatedAt=2026-09-03T10:29:18.332Z pushedAt=2026-09-05T10:47:30.426Z -->

The ServiceExtensionAbility module provides extended capabilities for background services, including lifecycle callbacks for creating, destroying, connecting, and disconnecting background services. It is applicable to scenarios where services need to run in the background and handle long-running tasks, such as file download and background computing.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.
>
> The APIs of this module are system APIs.
>
> The APIs of this module do not support implementation or use in app clones.

## Modules to Import

```ts
import { ServiceExtensionAbility } from '@kit.AbilityKit';
```

## Required Permissions

None.

## ServiceExtensionAbility

### Properties

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| context | [ServiceExtensionContext](js-apis-inner-application-serviceExtensionContext-sys.md)  | No| No| Context of the ServiceExtensionAbility. This context inherits from **ExtensionContext**.|


### onCreate

onCreate(want: Want): void

Called to initialize the service logic when a ServiceExtensionAbility is being created.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want |  [Want](js-apis-app-ability-want.md) | Yes| Want information related to this ServiceExtensionAbility, including the ability name and bundle name.|

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onCreate(want: Want) {
    console.info(`onCreate, want: ${want.abilityName}`);
  }
}
```


### onDestroy

onDestroy(): void

Called to clear resources when this ServiceExtensionAbility is being destroyed.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Example**

```ts
import { ServiceExtensionAbility } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onDestroy() {
    console.info('onDestroy');
  }
}
```


### onRequest

onRequest(want: Want, startId: number): void

Extension lifecycle callback. If the service is started by [startServiceExtensionAbility](js-apis-inner-application-uiAbilityContext-sys.md#startserviceextensionability) or [requestDialogService](js-apis-inner-application-uiAbilityContext.md#requestdialogservice), this callback is invoked after [onCreate](#oncreate). It is invoked each time the service is started, and startId increments each time.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want |  [Want](js-apis-app-ability-want.md) | Yes| Want information related to this ServiceExtensionAbility, including the ability name and bundle name.|
| startId | number | Yes | Number of times the service is started. The initial value is 1 for the first start and increments automatically for subsequent starts. |

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    console.info(`onRequest, want: ${want.abilityName}`);
  }
}
```


### onConnect

onConnect(want: Want): rpc.RemoteObject | Promise<rpc.RemoteObject>

Extension lifecycle callback. If the service is connected through connectAbility, this callback is invoked after onCreate. It returns a RemoteObject object used for communication between the client and the server.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want |  [Want](js-apis-app-ability-want.md)| Yes| Want information related to this ServiceExtensionAbility, including the ability name and bundle name.|

**Return value**

| Type| Description|
| -------- | -------- |
| [rpc.RemoteObject](../apis-ipc-kit/js-apis-rpc.md#remoteobject) \| Promise\<[rpc.RemoteObject](../apis-ipc-kit/js-apis-rpc.md#remoteobject)> | RemoteObject or Promise used to return a RemoteObject, which is used for communication between the client and server.|

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';

class StubTest extends rpc.RemoteObject{
  constructor(des: string) {
    super(des);
  }
  onConnect(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence, option: rpc.MessageOption) {
  }
}
class ServiceExt extends ServiceExtensionAbility {
  onConnect(want: Want) {
    console.info(`onConnect, want: ${want.abilityName}`);
    return new StubTest('test');
  }
}
```

If the returned RemoteObject depends on an asynchronous API, you can use the asynchronous lifecycle.

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';

class StubTest extends rpc.RemoteObject{
  constructor(des: string) {
    super(des);
  }
  onConnect(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence, option: rpc.MessageOption) {
  }
}
async function getDescriptor() {
  // Call the asynchronous function.
  return "asyncTest"
}
class ServiceExt extends ServiceExtensionAbility {
  async onConnect(want: Want) {
    console.info(`onConnect , want: ${want.abilityName}`);
    let descriptor = await getDescriptor();
    return new StubTest(descriptor);
  }
}
```

### onDisconnect

onDisconnect(want: Want): void | Promise\<void>

Extension lifecycle callback. It is invoked when the client disconnects from the service.

This API returns the result synchronously or uses a promise to return the result.

> **NOTE**
>
> - Once the **onDisconnect** lifecycle callback completes, the application may exit. This can interrupt any pending asynchronous operations (such as asynchronously writing data to a database), preventing them from finishing successfully. For any non-instantaneous tasks, you are advised to use Promise-based asynchronous callbacks.
>
> - Be aware that asynchronous operations are subject to a default timeout of approximately 1 second. Even if this timeout is exceeded, the system may still force-terminate the application. Note that the exact timeout duration can vary by device.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want |[Want](js-apis-app-ability-want.md)| Yes| Want information related to this ServiceExtensionAbility, including the ability name and bundle name.|

**Return value**

| Type| Description|
| -------- | -------- |
| void \| Promise\<void> | No return value or a Promise object with no return value. |

**Example**

- A synchronous callback example is as follows:

  ```ts
  import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
  
  class ServiceExt extends ServiceExtensionAbility {
    onDisconnect(want: Want) {
      console.info(`onDisconnect, want: ${want.abilityName}`);
    }
  }
  ```

- A promise asynchronous callback example is as follows:

  ```ts
  import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
  
  class ServiceExt extends ServiceExtensionAbility {
    async onDisconnect(want: Want) {
      console.info(`onDisconnect, want: ${want.abilityName}`);
      // Call the asynchronous function.
    }
  }
  ```

### onReconnect

onReconnect(want: Want): void

Called when a new client attempts to connect to this ServiceExtensionAbility after all previous clients are disconnected. This capability is reserved.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want |[Want](js-apis-app-ability-want.md)| Yes| Want information related to this ServiceExtensionAbility, including the ability name and bundle name.|

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onReconnect(want: Want) {
    console.info(`onReconnect, want: ${want.abilityName}`);
  }
}
```

### onConfigurationUpdate

onConfigurationUpdate(newConfig: Configuration): void

Called when the configuration of this ServiceExtensionAbility is updated.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| newConfig | [Configuration](js-apis-app-ability-configuration.md) | Yes| New configuration.|

**Example**

```ts
import { ServiceExtensionAbility, Configuration } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onConfigurationUpdate(newConfig: Configuration) {
    console.info(`onConfigurationUpdate, config: ${JSON.stringify(newConfig)}`);
  }
}
```

### onDump

onDump(params: Array\<string>): Array\<string>

Dumps the client information.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| params | Array\<string> | Yes | Array of parameters passed in command line mode. |

**Return value**

| Type| Description|
| -------- | -------- |
| Array\<string> | Represents the array of dumped client information. |

**Example**

```ts
import { ServiceExtensionAbility } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onDump(params: Array<string>) {
    console.info(`dump, params: ${JSON.stringify(params)}`);
    return ['params'];
  }
}
```
