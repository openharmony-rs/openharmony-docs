# ServiceExtensionAbility (System API)

```TypeScript
declare class ServiceExtensionAbility
```

The ServiceExtensionAbility module provides extended capabilities for background services, including lifecycle callbacks for creating, destroying, connecting, and disconnecting background services.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { ServiceExtensionAbility } from '@kit.AbilityKit';
```

## onConfigurationUpdate

```TypeScript
onConfigurationUpdate(newConfig: Configuration): void
```

Called when the configuration of this ServiceExtensionAbility is updated.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newConfig | [Configuration](arkts-ability-app-ability-configuration-configuration-i.md) | Yes | New configuration. |

**Examples**

```TypeScript
import { ServiceExtensionAbility, Configuration } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onConfigurationUpdate(newConfig: Configuration) {
    console.info(`onConfigurationUpdate, config: ${JSON.stringify(newConfig)}`);
  }
}
```

## onConnect

```TypeScript
onConnect(want: Want): rpc.RemoteObject | Promise<rpc.RemoteObject>
```

Called following **onCreate()** when a ServiceExtensionAbility is started by calling **connectAbility()**. A RemoteObject is returned for communication between the server and client.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information related to this ServiceExtensionAbility, including the ability name and bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| [rpc.RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md) &#124; Promise&lt;[rpc.RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md)&gt; | RemoteObject or Promise used to return a RemoteObject, which is used for communication between the client and server. |

**Examples**

```TypeScript
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

```TypeScript
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

## onCreate

```TypeScript
onCreate(want: Want): void
```

Called to initialize the service logic when a ServiceExtensionAbility is being created.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information related to this ServiceExtensionAbility, including the ability name and bundle name. |

**Examples**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onCreate(want: Want) {
    console.info(`onCreate, want: ${want.abilityName}`);
  }
}
```

## onDestroy

```TypeScript
onDestroy(): void
```

Called to clear resources when this ServiceExtensionAbility is being destroyed.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Examples**

```TypeScript
import { ServiceExtensionAbility } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onDestroy() {
    console.info('onDestroy');
  }
}
```

## onDisconnect

```TypeScript
onDisconnect(want: Want): void | Promise<void>
```

Called when a client is disconnected from this ServiceExtensionAbility. This API returns the result synchronously or uses a promise to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information related to this ServiceExtensionAbility, including the ability name and bundle name. |

**Examples**

A synchronous callback example is as follows:

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onDisconnect(want: Want) {
    console.info(`onDisconnect, want: ${want.abilityName}`);
  }
}
```

A promise asynchronous callback example is as follows:

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  async onDisconnect(want: Want) {
    console.info(`onDisconnect, want: ${want.abilityName}`);
    // Call the asynchronous function.
  }
}
```

## onDump

```TypeScript
onDump(params: Array<string>): Array<string>
```

Dumps the client information.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | Array&lt;string&gt; | Yes | Parameters in the form of a command. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Array of client information. |

**Examples**

```TypeScript
import { ServiceExtensionAbility } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onDump(params: Array<string>) {
    console.info(`dump, params: ${JSON.stringify(params)}`);
    return ['params'];
  }
}
```

## onReconnect

```TypeScript
onReconnect(want: Want): void
```

Called when a new client attempts to connect to this ServiceExtensionAbility after all previous clients are disconnected. This capability is reserved.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information related to this ServiceExtensionAbility, including the ability name and bundle name. |

**Examples**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onReconnect(want: Want) {
    console.info(`onReconnect, want: ${want.abilityName}`);
  }
}
```

## onRequest

```TypeScript
onRequest(want: Want, startId: number): void
```

Called following **onCreate()** when a ServiceExtensionAbility is started by calling **startAbility()** or **startServiceExtensionAbility()**. The value of **startId** is incremented for each ServiceExtensionAbility that is started.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information related to this ServiceExtensionAbility, including the ability name and bundle name. |
| startId | number | Yes | Number of times the instance has been started. The initial value is **1** for the first start, and it increments automatically for subsequent starts. |

**Examples**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    console.info(`onRequest, want: ${want.abilityName}`);
  }
}
```

## context

```TypeScript
context: ServiceExtensionContext
```

Context of the ServiceExtensionAbility. This context inherits from **ExtensionContext**.

**Type:** [ServiceExtensionContext](arkts-ability-serviceextensioncontext-c-sys.md)

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
