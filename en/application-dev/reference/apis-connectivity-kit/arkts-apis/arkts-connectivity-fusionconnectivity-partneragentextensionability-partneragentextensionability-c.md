# PartnerAgentExtensionAbility

```TypeScript
export default declare class PartnerAgentExtensionAbility extends ExtensionAbility
```

Class for the PartnerAgentExtensionAbility. Applications can use this ability to discover devices.

**Inheritance/Implementation:** PartnerAgentExtensionAbility extends [ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-extensionability-extensionability-c.md)

**Since:** 23

<!--Device-unnamed-export default declare class PartnerAgentExtensionAbility extends ExtensionAbility--><!--Device-unnamed-export default declare class PartnerAgentExtensionAbility extends ExtensionAbility-End-->

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

## ExtensionAbility Usage Restrictions

To ensure system security and stability, PartnerAgentExtensionAbility is restricted from abusing system resources. The system controls its capabilities and does not support referencing some modules. For details, see [Appendix](#appendix).

## Modules to Import

```TypeScript
import { PartnerAgentExtensionAbility } from '@kit.ConnectivityKit';
```

## onDestroyWithReason

```TypeScript
onDestroyWithReason(reason: PartnerAgentExtensionAbilityDestroyReason): void
```

Called when the PartnerAgentExtensionAbility is to be destroyed. Applications can clean up resources in this callback function.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PartnerAgentExtensionAbility-onDestroyWithReason(reason: PartnerAgentExtensionAbilityDestroyReason): void--><!--Device-PartnerAgentExtensionAbility-onDestroyWithReason(reason: PartnerAgentExtensionAbilityDestroyReason): void-End-->

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reason | [PartnerAgentExtensionAbilityDestroyReason](arkts-connectivity-partneragentextensionabilitydestroyreason-t.md) | Yes | The reason for Ability destruction. |

**Examples**

```TypeScript
export default class PartnerAgentExtAbility extends PartnerAgentExtensionAbility {
  onDestroyWithReason(reason: partnerAgent.PartnerAgentExtensionAbilityDestroyReason): void {
    console.info(`onDestroyWithReason is: ${reason}`);
  }
}
```

## onDeviceDiscovered

```TypeScript
onDeviceDiscovered(deviceAddress: PartnerDeviceAddress): void
```

Called when a device is discovered.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PartnerAgentExtensionAbility-onDeviceDiscovered(deviceAddress: PartnerDeviceAddress): void--><!--Device-PartnerAgentExtensionAbility-onDeviceDiscovered(deviceAddress: PartnerDeviceAddress): void-End-->

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceAddress | [PartnerDeviceAddress](arkts-connectivity-partnerdeviceaddress-t.md) | Yes | Address of the discovered device. |

**Examples**

```TypeScript
export default class PartnerAgentExtAbility extends PartnerAgentExtensionAbility {
  onDeviceDiscovered(deviceAddress: partnerAgent.PartnerDeviceAddress): void {
    console.info(`onDeviceDiscovered success: ${deviceAddress.bluetoothAddress}`);
  }
}
```

## context

```TypeScript
context: PartnerAgentExtensionContext
```

Context of the PartnerAgentExtensionAbility.

**Type:** [PartnerAgentExtensionContext](arkts-connectivity-fusionconnectivity-partneragentextensioncontext-partneragentextensioncontext-c.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PartnerAgentExtensionAbility-context: PartnerAgentExtensionContext--><!--Device-PartnerAgentExtensionAbility-context: PartnerAgentExtensionContext-End-->

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

## Appendix

PartnerAgentExtensionAbility does not support referencing the following modules.

| Kit | Module |
| --- | --- |
| Background Tasks Kit | [@ohos.backgroundTaskManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-backgroundtaskmanager.md) |
| Connectivity Kit | [@ohos.connectedTag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-connectedtag.md) |
| Background Tasks Kit | [@ohos.resourceschedule.backgroundTaskManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-resourceschedule-backgroundtaskmanager.md) |
| Location Kit | [@ohos.geolocation](../../apis-location-kit/arkts-apis/arkts-location-geolocation.md) |
| Location Kit | [@ohos.geoLocationManager](../../apis-location-kit/arkts-apis/arkts-location-geolocationmanager.md) |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Camera Kit | [@ohos.multimedia.cameraPicker](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camerapicker.md) |
| Media Kit | [@ohos.multimedia.media](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media.md) |
| Media Library Kit | [@ohos.multimedia.movingphotoview](../../apis-media-library-kit/arkts-components/arkts-medialibrary-multimedia-movingphotoview.md) |
| Connectivity Kit | [@ohos.nfc.cardEmulation](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-cardemulation.md) |
| Connectivity Kit | [@ohos.nfc.controller](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-controller.md) |
| Connectivity Kit | [@ohos.nfc.tag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-tag.md) |
| Connectivity Kit | [tagSession](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-tagsession.md) |
| Telephony Kit | [@ohos.telephony.sim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sim.md) |
| Telephony Kit | [@ohos.telephony.sms](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sms.md) |
| Connectivity Kit | [@ohos.wifiext](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifiext.md) |
| Connectivity Kit | [@ohos.wifiManager](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifimanager.md) |
| Connectivity Kit | [@ohos.wifiManagerExt](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifimanagerext.md) |
