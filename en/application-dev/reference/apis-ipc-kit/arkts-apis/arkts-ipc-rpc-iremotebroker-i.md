# IRemoteBroker

Represents the holder of a remote proxy object. It is used to obtain a proxy object.

**Since:** 7

**System capability:** SystemCapability.Communication.IPC.Core

## Modules to Import

```TypeScript
import { rpc } from '@kit.IPCKit';
```

## asObject

```TypeScript
asObject(): IRemoteObject
```

Obtains a proxy or remote object. This API must be implemented by its derived classes.

**Since:** 7

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md) | Returns the **RemoteObject** if it is the caller; returns the [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md), the holder of this **RemoteProxy** object, if the caller is a [RemoteProxy](arkts-ipc-rpc-remoteproxy-c.md) object. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';

class TestAbility extends rpc.RemoteObject {
  asObject() {
    return this;
  }
}
let remoteObject = new TestAbility("testObject").asObject();
```

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.getUIContext().getHostContext() is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

```TypeScript
The proxy object in the onConnect callback can be assigned a value only after the ability is connected asynchronously. Then, asObject() of the proxy object is called to obtain the proxy or remote object.
```
