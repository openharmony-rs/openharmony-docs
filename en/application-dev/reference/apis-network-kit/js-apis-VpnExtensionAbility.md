# @ohos.app.ability.VpnExtensionAbility (Enhanced VPN Management)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=108aa11c2ceb50c68f8417aa3c60f1dcb55dabdd translatedAt=2026-09-23T02:40:54.733Z pushedAt=2026-09-24T06:00:14.224Z -->

This module provides lifecycle callbacks for third-party VPNs, including VPN creation and destruction.

>  **NOTE**
>
>  - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
>  - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { VpnExtensionAbility } from '@kit.NetworkKit';
```

## Attributes

**System capability**: SystemCapability.Ability.AbilityRuntime.Core.

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| context | [VpnExtensionContext](js-apis-inner-application-VpnExtensionContext.md) | No | No | Context of the VpnExtension. This context is inherited from [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md). |

## VpnExtensionAbility.onCreate

onCreate(want: Want): void

Called when the third-party VPN is initialized upon startup.

>  **NOTE**
>
>  You are advised to call [onDestroy](#vpnextensionabilityondestroy) to listen to the destruction of the third-party VPN and clear resources in a timely manner.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core.

**Parameters**

| Name | Type                                      | Mandatory  | Description            |
| ---- | ---------------------------------------- | ---- | -------------- |
| want   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | Want information.|

**Example**

```ts
import { VpnExtensionAbility } from '@kit.NetworkKit';
import { Want } from '@kit.AbilityKit';

class MyVpnExtAbility extends VpnExtensionAbility {
    onCreate(want: Want) {
       console.info('MyVpnExtAbility onCreate');
    }
}
```

## VpnExtensionAbility.onDestroy

onDestroy(): void

Called when the third-party VPN is destroyed to clear resources.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core.

**Example**

```ts
import { VpnExtensionAbility } from '@kit.NetworkKit';

class MyVpnExtAbility extends VpnExtensionAbility {
    onDestroy() {
       console.info('MyVpnExtAbility onDestroy');
    }
}
```

