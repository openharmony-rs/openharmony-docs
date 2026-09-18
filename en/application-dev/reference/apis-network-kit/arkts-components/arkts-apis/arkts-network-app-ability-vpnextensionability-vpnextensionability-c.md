# VpnExtensionAbility

**VpnExtensionContext** represents the context of **VpnExtensionAbility** and is inherited from [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md).

This module provides the context required for APIs to access the resources of a **VpnExtensionAbility** object.

**Since:** 11

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { VpnExtensionAbility, VpnExtensionContext } from '@kit.NetworkKit';
```

## onCreate

```TypeScript
onCreate(want: Want): void
```

Represents the callback triggered when the extended VPN is initialized.

> **NOTE:** 
> 
> You are advised to call [onDestroy](#ondestroy) to listen to the destruction of the
> extended VPN and clear resources in a timely manner.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want information. |

**Examples**

```TypeScript
import { VpnExtensionAbility } from '@kit.NetworkKit';
import { Want } from '@kit.AbilityKit';

class MyVpnExtAbility extends VpnExtensionAbility {
    onCreate(want: Want) {
       console.info('MyVpnExtAbility onCreate');
    }
}
```

## onDestroy

```TypeScript
onDestroy(): void
```

Represents the callback triggered when the extended VPN is destroyed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Examples**

```TypeScript
import { VpnExtensionAbility } from '@kit.NetworkKit';

class MyVpnExtAbility extends VpnExtensionAbility {
    onDestroy() {
       console.info('MyVpnExtAbility onDestroy');
    }
}
```

## context

```TypeScript
context: VpnExtensionContext
```

Specified context.

**Type:** [VpnExtensionContext](arkts-network-vpnextensioncontext-c.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
