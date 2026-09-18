# connectAbility

## Modules to Import

```TypeScript
import { particleAbility } from '@kit.AbilityKit';
```

## connectAbility

```TypeScript
function connectAbility(request: Want, options: ConnectOptions): number
```

Connects this ability to a ServiceAbility.

> **NOTE:** 
> 
> For details about the startup rules for the components in the FA model, see
> [Component Startup Rules (FA Model)](../../../application-models/component-startup-rules-fa.md).
> 
> To connect to a ServiceAbility of another application, the target application must be configured with
> associated startup (**AssociateWakeUp** set to **true**).

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | ServiceAbility to connect. |
| options | [ConnectOptions](arkts-ability-connectoptions-connectoptions-i.md) | Yes | Connection options. |

**Return value:**

| Type | Description |
| --- | --- |
| number | ID of the connected ServiceAbility. The ID starts from 0 and is incremented by 1 each time a connection is set up. |

**Examples**

```TypeScript
import { particleAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

let connId = particleAbility.connectAbility(
  {
    bundleName: 'com.ix.ServiceAbility',
    abilityName: 'ServiceAbilityA',
  },
  {
    onConnect: (element, remote) => {
      console.info(`ConnectAbility onConnect remote is proxy: ${(remote instanceof rpc.RemoteProxy)}`);
    },
    onDisconnect: (element) => {
      console.info(`ConnectAbility onDisconnect element.deviceId: ${element.deviceId}`);
    },
    onFailed: (code) => {
      console.error(`particleAbilityTest ConnectAbility onFailed errCode: ${code}`);
    },
  },
);

particleAbility.disconnectAbility(connId).then((data) => {
  console.info(`data: ${data}`);
}).catch((error: BusinessError) => {
  console.error(`particleAbilityTest result errCode: ${error.code}`);
});
```
