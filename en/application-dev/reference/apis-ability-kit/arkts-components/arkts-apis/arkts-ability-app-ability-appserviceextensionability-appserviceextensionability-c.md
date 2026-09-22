# AppServiceExtensionAbility

```TypeScript
declare class AppServiceExtensionAbility extends ExtensionAbility
```

The AppServiceExtensionAbility module provides extended capabilities for background services, including lifecycle callbacks for creating, destroying, connecting, and disconnecting background services.

**Inheritance/Implementation:** AppServiceExtensionAbility extends [ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md)

**Since:** 20

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { AppServiceExtensionAbility } from '@kit.AbilityKit';
```

## onConnect

```TypeScript
onConnect(want: Want): rpc.RemoteObject
```

Called when an AppServiceExtensionAbility instance is connected by calling [connectAppServiceExtensionAbility()](arkts-ability-uiabilitycontext-c.md#connectappserviceextensionability).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target AppServiceExtensionAbility instance, including the ability name and bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| [rpc.RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md) | A RemoteObject used for communication between the server and client. |

**Examples**

```TypeScript
import { AppServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AppServiceExtAbility]';

class StubTest extends rpc.RemoteObject {
  constructor(des: string) {
    super(des);
  }

  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence, options: rpc.MessageOption): boolean {
    return true;
  }
}

export default class AppServiceExtAbility extends AppServiceExtensionAbility {
  onConnect(want: Want) {
    hilog.info(0x0000, TAG, `onConnect, want: ${want.abilityName}`);
    return new StubTest('test');
  }
}
```

## onCreate

```TypeScript
onCreate(want: Want): void
```

Called when an AppServiceExtensionAbility instance is created. Applications can perform initialization operations, such as registering common event listeners, in this callback.

> **NOTE:** 
> 
> If an AppServiceExtensionAbility instance has already been created, the **onCreate()** callback is not invoked
> again when the instance is started or connected.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target AppServiceExtensionAbility instance, including the ability name and bundle name. |

**Examples**

```TypeScript
import { AppServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AppServiceExtAbility]';

export default class AppServiceExtAbility extends AppServiceExtensionAbility {
  onCreate(want: Want) {
    hilog.info(0x0000, TAG, `onCreate, want: ${want.abilityName}`);
  }
}
```

## onDestroy

```TypeScript
onDestroy(): void
```

Called when an AppServiceExtensionAbility instance is destroyed. Applications can perform resource cleanup operations, such as unregistering listeners, in this callback.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Examples**

```TypeScript
import { AppServiceExtensionAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AppServiceExtAbility]';

export default class AppServiceExtAbility extends AppServiceExtensionAbility {
  onDestroy() {
    hilog.info(0x0000, TAG, `onDestroy`);
  }
}
```

## onDisconnect

```TypeScript
onDisconnect(want: Want): void
```

Called when all connections to an AppServiceExtensionAbility instance are interrupted.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information passed by the caller when the AppServiceExtensionAbility instance was most recently started or connected. This includes information such as the ability name and bundle name. |

**Examples**

```TypeScript
import { AppServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AppServiceExtAbility]';

export default class AppServiceExtAbility extends AppServiceExtensionAbility {
  onDisconnect(want: Want) {
    hilog.info(0x0000, TAG, `onDisconnect, want: ${want.abilityName}`);
  }
}
```

## onRequest

```TypeScript
onRequest(want: Want, startId: number): void
```

Called each time an AppServiceExtensionAbility instance is started by calling [startAppServiceExtensionAbility()](arkts-ability-uiabilitycontext-c.md#startappserviceextensionability).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target AppServiceExtensionAbility instance, including the ability name and bundle name. |
| startId | number | Yes | Number of times the instance has been started. The initial value is **1** for the first start, and it increments automatically for subsequent starts. |

**Examples**

```TypeScript
import { AppServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AppServiceExtAbility]';

export default class AppServiceExtAbility extends AppServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    hilog.info(0x0000, TAG, `onRequest, want: ${want.abilityName}, startId: ${startId}`);
  }
}
```

## context

```TypeScript
context: AppServiceExtensionContext
```

Context environment for an AppServiceExtensionAbility. This context inherits from [ExtensionContext](arkts-ability-extensioncontext-c.md).

**Type:** [AppServiceExtensionContext](arkts-ability-appserviceextensioncontext-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
