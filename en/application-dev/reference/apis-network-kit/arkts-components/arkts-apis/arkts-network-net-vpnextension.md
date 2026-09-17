# @ohos.net.vpnExtension(Enhanced VPN Management)

This module implements virtual private network (VPN) management, such as starting and stopping a third-party VPN. Third-party VPNs refer to VPN services provided by third parties. They usually support more security and privacy functions and more comprehensive customization options. Currently, the VPN capabilities provided to third-party applications are primarily used for creating virtual NICs and configuring VPN routing information. The connection tunnel process and internal connection protocols need to be implemented by the applications themselves.

> **NOTE:** 
> 
> The following modules cannot be referenced in the VpnExtensionAbility, as doing so may cause the program to exit
> abnormally:

> - [@ohos.contact (Contacts)](../../apis-contacts-kit/arkts-apis/arkts-contacts-contact.md)

> - [@ohos.geolocation](../../apis-location-kit/arkts-apis/arkts-location-geolocation.md),[@ohos.geoLocationManager (Geolocation Manager)](../../apis-location-kit/arkts-apis/arkts-location-geolocationmanager.md)

> - [@ohos.multimedia.audio (Audio Management)](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audio.md)

> - [@ohos.multimedia.camera (Camera Management)](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md)

> - [@ohos.telephony.call (Call)](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-call.md)

> - [@ohos.telephony.sim (SIM Management)](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sim.md)

> - [@ohos.telephony.sms (SMS)](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sms.md)

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Vpn

## Modules to Import

```TypeScript
import { vpnExtension } from '@kit.NetworkKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createVpnConnection](arkts-network-vpnextension-createvpnconnection-f.md) | Creates a **VpnConnection** object. |
| [createVpnObserver](arkts-network-vpnextension-createvpnobserver-f.md) | Creates a VPN observer object. It is used to listen for VPN-related events. |
| [startVpnExtensionAbility](arkts-network-vpnextension-startvpnextensionability-f.md) | Enables the VPN extension ability. This API uses a promise to return the result. |
| [stopVpnExtensionAbility](arkts-network-vpnextension-stopvpnextensionability-f.md) | Stops the VPN extension ability. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [isAlwaysOnVpnEnabled](arkts-network-vpnextension-isalwaysonvpnenabled-f-sys.md) | Obtains the status of the **always on** mode. This API uses a promise to return the result. |
| [setAlwaysOnVpnEnabled](arkts-network-vpnextension-setalwaysonvpnenabled-f-sys.md) | Enables or disables the **always on** mode. This API uses a promise to return the result. |
| [updateVpnAuthorizedState](arkts-network-vpnextension-updatevpnauthorizedstate-f-sys.md) | Updates the VPN pop-up authorization status. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [VpnConfig](arkts-network-vpnextension-vpnconfig-i.md) | Defines the VPN configuration. |
| [VpnConnection](arkts-network-vpnextension-vpnconnection-i.md) | Defines a VPN connection object. Before calling **VpnConnection** APIs, you need to create a VPN connection object by calling **vpnExt.createVpnConnection**. |
| [VpnObserver](arkts-network-vpnextension-vpnobserver-i.md) | Defines a VPN observer object. It is used to listen for VPN-related events. Before calling **VpnObserver** APIs, you need to create a VPN connection object by calling [vpnExtension.createVpnObserver](arkts-network-vpnextension-createvpnobserver-f.md). |

### Types

| Name | Description |
| --- | --- |
| [LinkAddress](arkts-network-vpnextension-linkaddress-t.md) | Defines the network link address information. |
| [RouteInfo](arkts-network-vpnextension-routeinfo-t.md) | Defines the network route information. |
| [VpnExtensionContext](arkts-network-vpnextension-vpnextensioncontext-t.md) | Defines the VPN extension context. It allows access to serviceExtension-specific resources. |
