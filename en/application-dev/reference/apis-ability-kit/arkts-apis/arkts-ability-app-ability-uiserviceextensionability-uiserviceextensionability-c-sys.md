# UIServiceExtensionAbility (System API)

```TypeScript
declare class UIServiceExtensionAbility extends ExtensionAbility
```

UIServiceExtensionAbility provides extended capabilities related to the floating window component. It inherits from [ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md). It is mainly used to provide services with UIs for third-party applications.

> **NOTE:** 
> 
> The APIs of this module must be used in the main thread, but not in child threads such as Worker and TaskPool.

**Inheritance/Implementation:** UIServiceExtensionAbility extends [ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md)

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { UIServiceExtensionAbility } from '@kit.AbilityKit';
```

## onConnect

```TypeScript
onConnect(want: Want, proxy: UIServiceHostProxy): void
```

Called when the connection to a [UIServiceExtensionAbility](arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md) is established. If the UIServiceExtensionAbility is started by calling [connectUIServiceExtensionAbility()](arkts-ability-uiextensioncontext-c.md#connectuiserviceextensionability), this callback will be invoked after [onCreate()](#oncreate). This callback receives a [UIServiceHostProxy](arkts-ability-uiservicehostproxy-i-sys.md) object for communication between the client and server.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | [Want](arkts-ability-app-ability-want-want-c.md) information about the [UIServiceExtensionAbility](arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md), including the ability name and bundle name. |
| proxy | [UIServiceHostProxy](arkts-ability-uiservicehostproxy-i-sys.md) | Yes | [UIServiceHostProxy](arkts-ability-uiservicehostproxy-i-sys.md) object, used for communication between the client and server. |

**Examples**

```TypeScript
import { UIServiceExtensionAbility, Want, common} from '@kit.AbilityKit';

class UIServiceExt extends UIServiceExtensionAbility {
  onConnect(want: Want, proxy: common.UIServiceHostProxy){
    console.info(`onConnect, want: ${want.abilityName}`);
  }
}
```

## onCreate

```TypeScript
onCreate(want: Want): void
```

Called to initialize the service logic.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | [Want](arkts-ability-app-ability-want-want-c.md) information about the [UIServiceExtensionAbility](arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md), including the ability name and bundle name. |

**Examples**

```TypeScript
import { UIServiceExtensionAbility, Want } from '@kit.AbilityKit';

class UIServiceExt extends UIServiceExtensionAbility {
  // Create a UIServiceExtensionAbility.
  onCreate(want: Want) {
    console.info(`onCreate, want: ${want.abilityName}`);
  }
}
```

## onData

```TypeScript
onData(proxy: UIServiceHostProxy, data: Record<string, Object>): void
```

Callback invoked when data is received.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| proxy | [UIServiceHostProxy](arkts-ability-uiservicehostproxy-i-sys.md) | Yes | Proxy that sends data to the client. |
| data | Record&lt;string, Object&gt; | Yes | Data received. |

**Examples**

```TypeScript
import { UIServiceExtensionAbility, common} from '@kit.AbilityKit';

class ServiceExt extends UIServiceExtensionAbility {
  onData(proxy : common.UIServiceHostProxy, data : Record<string, Object> ){
    console.info('onData');
  }
}
```

## onDestroy

```TypeScript
onDestroy(): void
```

Called to clear resources when this [UIServiceExtensionAbility](arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md) is destroyed.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Examples**

```TypeScript
import { UIServiceExtensionAbility } from '@kit.AbilityKit';

class ServiceExt extends UIServiceExtensionAbility {
  onDestroy() {
    console.info('onDestroy');
  }
}
```

## onDisconnect

```TypeScript
onDisconnect(want: Want, proxy: UIServiceHostProxy): void
```

Called when the connection to a [UIServiceExtensionAbility](arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md) is interrupted.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | [Want](arkts-ability-app-ability-want-want-c.md) information about the [UIServiceExtensionAbility](arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md), including the ability name and bundle name. |
| proxy | [UIServiceHostProxy](arkts-ability-uiservicehostproxy-i-sys.md) | Yes | Proxy that sends data to the sender. |

**Examples**

```TypeScript
import { UIServiceExtensionAbility, Want, common } from '@kit.AbilityKit';

class UIServiceExt extends UIServiceExtensionAbility {
  onDisconnect(want: Want, proxy: common.UIServiceHostProxy) {
    console.info(`onDisconnect, want: ${want.abilityName}`);
  }
}
```

## onRequest

```TypeScript
onRequest(want: Want, startId: number): void
```

Called to request to start a [UIServiceExtensionAbility](arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md). If the UIServiceExtensionAbility is started by calling [startAbility](arkts-ability-uiabilitycontext-c.md#startability) or [startUIServiceExtensionAbility](arkts-ability-uiabilitycontext-c.md#startuiserviceextensionability), this callback will be invoked after [onCreate](#oncreate). The value of **startId** is incremented for each UIServiceExtensionAbility that is started.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | [Want](arkts-ability-app-ability-want-want-c.md) information about the [UIServiceExtensionAbility](arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md), including the ability name and bundle name. |
| startId | number | Yes | Number of times the instance has been started. The initial value is **1** for the first start, and it increments automatically for subsequent starts. |

**Examples**

```TypeScript
import { UIServiceExtensionAbility, Want} from '@kit.AbilityKit';

class UIServiceExt extends UIServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    console.info(`onRequest, want: ${want.abilityName}, startId: ${startId}`);
  }
}
```

## onWindowDidCreate

```TypeScript
onWindowDidCreate(window: window.Window): void
```

Called when a window is created for the [UIServiceExtensionAbility](arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md). Through this callback, the [UIServiceExtensionAbility](arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md) passes the created window object to the foreground application.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| window | [window.Window](../../apis-arkui/arkts-apis/arkts-arkui-window-window-i.md) | Yes | Window object created. |

**Examples**

```TypeScript
import { UIServiceExtensionAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

class ServiceExt extends UIServiceExtensionAbility {
  onWindowDidCreate(window : window.Window){
    console.info('onWindowDidCreate');
  }
}
```

## onWindowWillCreate

```TypeScript
onWindowWillCreate(config: window.ExtensionWindowConfig): void
```

Called when a window will be created for the [UIServiceExtensionAbility](arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md). Through **window.ExtensionWindowConfig** in the callback, the foreground application sends the parameters for creating the window to the [UIServiceExtensionAbility](arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [window.ExtensionWindowConfig](../../apis-arkui/arkts-apis/arkts-arkui-window-extensionwindowconfig-i-sys.md) | Yes | Window configuration information. |

**Examples**

```TypeScript
import { UIServiceExtensionAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

class UIServiceExt extends UIServiceExtensionAbility {
  onWindowWillCreate(config : window.ExtensionWindowConfig){
    console.info('onWindowWillCreate');
  }
}
```

## context

```TypeScript
context: UIServiceExtensionContext
```

Context environment for a [UIServiceExtensionAbility](arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md). This context inherits from [ExtensionContext](arkts-ability-extensioncontext-c.md).

**Type:** [UIServiceExtensionContext](arkts-ability-uiserviceextensioncontext-c-sys.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
