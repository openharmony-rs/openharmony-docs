# VpnExtensionAbility

```TypeScript
export default class VpnExtensionAbility
```

**VpnExtensionContext** represents the context of **VpnExtensionAbility** and is inherited from [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md).

This module provides lifecycle callbacks for third-party VPNs, including VPN creation and destruction.

**Since:** 11

<!--Device-unnamed-export default class VpnExtensionAbility--><!--Device-unnamed-export default class VpnExtensionAbility-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## ExtensionAbility Usage Restrictions

To ensure system security and stability, VpnExtensionAbility is restricted from abusing system resources. The system controls its capabilities and does not support referencing some modules. For details, see [Appendix](#appendix).

## Modules to Import

```TypeScript
import { VpnExtensionAbility, VpnExtensionContext } from '@kit.NetworkKit';
```

## onCreate

```TypeScript
onCreate(want: Want): void
```

Called when the third-party VPN is initialized upon startup.

> **NOTE:** 
> 
> You are advised to call [onDestroy](#ondestroy) to listen to the destruction of the
> third-party VPN and clear resources in a timely manner.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-VpnExtensionAbility-onCreate(want: Want): void--><!--Device-VpnExtensionAbility-onCreate(want: Want): void-End-->

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

Called when the third-party VPN is destroyed to clear resources.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-VpnExtensionAbility-onDestroy(): void--><!--Device-VpnExtensionAbility-onDestroy(): void-End-->

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

Context of the VpnExtension. This context is inherited from [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md).

**Type:** [VpnExtensionContext](arkts-network-vpnextensioncontext-c.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-VpnExtensionAbility-context: VpnExtensionContext--><!--Device-VpnExtensionAbility-context: VpnExtensionContext-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Appendix

VpnExtensionAbility does not support referencing the following modules.

| Kit | Module |
| --- | --- |
| Contacts Kit | [@ohos.contact](../../apis-contacts-kit/arkts-apis/arkts-contacts-contact.md) |
| Location Kit | [@ohos.geolocation](../../apis-location-kit/arkts-apis/arkts-location-geolocation.md) |
| Location Kit | [@ohos.geoLocationManager](../../apis-location-kit/arkts-apis/arkts-location-geolocationmanager.md) |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Audio Kit | [@ohos.multimedia.audio](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audio.md) |
| Telephony Kit | [@ohos.telephony.call](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-call.md) |
| Telephony Kit | [@ohos.telephony.sim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sim.md) |
| Telephony Kit | [@ohos.telephony.sms](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sms.md) |
