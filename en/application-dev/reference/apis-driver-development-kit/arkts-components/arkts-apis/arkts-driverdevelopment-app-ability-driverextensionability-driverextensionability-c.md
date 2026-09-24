# DriverExtensionAbility

```TypeScript
declare class DriverExtensionAbility
```

The **DriverExtensionAbility** module provides the ExtensionAbility related to drivers. It provides lifecycle callbacks to be invoked when a driver is created, destroyed, connected, or disconnected.

**Since:** 10

**System capability:** SystemCapability.Driver.ExternalDevice

## Modules to Import

```TypeScript
import { DriverExtensionAbility, DriverExtensionContext } from '@kit.DriverDevelopmentKit';
```

## onConnect

```TypeScript
onConnect(want: Want): rpc.RemoteObject | Promise<rpc.RemoteObject>
```

Called following **onCreate()** when a DriverExtensionAbility is started by calling **connectAbility()**. A **RemoteObject** object is returned for communication between the server and client.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Driver.ExternalDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want information related to this DriverExtensionAbility, including the ability name and bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| [rpc.RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md) &#124; Promise&lt;[rpc.RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md)&gt; | **RemoteObject** object used for communication between the server and client, or promise used to return the value. |

**Examples**

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { rpc } from '@kit.IPCKit';
import { Want } from '@kit.AbilityKit';

class StubTest extends rpc.RemoteObject{
    constructor(des : string) {
        super(des);
    }
    onRemoteMessageRequest(code : number, data : rpc.MessageSequence, reply : rpc.MessageSequence, option : rpc.MessageOption) {
      // This interface must be overridden.
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

If the returned [RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md) object depends on an asynchronous API, you can use the asynchronous lifecycle.

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { rpc } from '@kit.IPCKit';
import { Want } from '@kit.AbilityKit';

class StubTest extends rpc.RemoteObject{
    constructor(des : string) {
        super(des);
    }
    onRemoteMessageRequest(code : number, data : rpc.MessageSequence, reply : rpc.MessageSequence, option : rpc.MessageOption) {
      // This interface must be overridden.
      return true;
    }
}
async function getDescriptor() {
    // Call the asynchronous function.
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

## onDisconnect

```TypeScript
onDisconnect(want: Want): void | Promise<void>
```

Called when a client is disconnected from this DriverExtensionAbility.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Driver.ExternalDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want information related to this DriverExtensionAbility, including the ability name and bundle name. |

**Examples**

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { Want } from '@kit.AbilityKit';

class DriverExt extends DriverExtensionAbility {
  onDisconnect(want : Want) {
    console.info(`onDisconnect, want: ${want.abilityName}`);
  }
}
```

After the onDisconnect lifecycle callback is executed, the application may exit. As a result, the asynchronous function in onDisconnect may fail to be executed correctly, for example, asynchronously writing data to the database. The asynchronous lifecycle can be used to ensure that the subsequent lifecycle continues after the asynchronous onDisconnect is complete.

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { Want } from '@kit.AbilityKit';

class DriverExt extends DriverExtensionAbility {
  async onDisconnect(want : Want) {
    console.info(`onDisconnect, want: ${want.abilityName}`);
    // Call the asynchronous function.
  }
}
```

## onDump

```TypeScript
onDump(params: Array<string>): Array<string>
```

Dumps client information. It is recommended that developers don't DUMP sensitive information.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Driver.ExternalDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | Array&lt;string&gt; | Yes | Parameters in the form of a command. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | String array used to dump client information. |

**Examples**

```TypeScript
class DriverExt extends DriverExtensionAbility {
    onDump(params : Array<string>) {
        console.info(`dump, params: ${JSON.stringify(params)}`);
        return ['params'];
    }
}
```

## onInit

```TypeScript
onInit(want: Want): void
```

Called when a DriverExtensionAbility is created to initialize the service logic.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Driver.ExternalDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want information related to this DriverExtensionAbility, including the ability name and bundle name. |

**Examples**

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { Want } from '@kit.AbilityKit';

class DriverExt extends DriverExtensionAbility {
  onInit(want : Want) {
    console.info(`onInit, want: ${want.abilityName}`);
  }
}
```

## onRelease

```TypeScript
onRelease(): void
```

Called when this DriverExtensionAbility is destroyed to clear resources.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Driver.ExternalDevice

**Examples**

```TypeScript
class DriverExt extends DriverExtensionAbility {
  onRelease() {
    console.info('onRelease');
  }
}
```

## context

```TypeScript
context: DriverExtensionContext
```

Context of the **DriverExtension**. This context is inherited from **ExtensionContext**.

**Type:** [DriverExtensionContext](arkts-driverdevelopment-driverextensioncontext-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Driver.ExternalDevice
