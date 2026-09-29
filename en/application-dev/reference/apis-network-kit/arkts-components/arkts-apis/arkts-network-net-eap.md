# @ohos.net.eap(Extensible Authentication)

The **eap** module provides the extensible authentication mechanism to enable third-party clients to access custom 802.1X (a port-based network access control protocol) authentication, such as Extensible Authentication Protocol (EAP) authentication.

**Since:** 20

<!--Device-unnamed-declare namespace eap--><!--Device-unnamed-declare namespace eap-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

## Modules to Import

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [connect](arkts-network-eap-connect-f.md) | Manually triggers or disconnects the 802.1X EAP authentication of Ethernet. |
| [deleteEthEapConfig](arkts-network-eap-deleteetheapconfig-f.md) | Deletes the persisted 802.1X EAP configuration and stops any ongoing auto-authentication. Idempotent: resolves successfully even if no configuration has been stored. |
| [getEthEapConfig](arkts-network-eap-getetheapconfig-f.md) | Gets the 802.1X EAP configuration for Ethernet. Sensitive fields (password, certPassword, certEntry) are always returned empty. |
| [getEthEapStateInfo](arkts-network-eap-getetheapstateinfo-f.md) | Queries the current 802.1X EAP authentication state information. |
| [logOffEthEap](arkts-network-eap-logoffetheap-f.md) | Revokes the EAP-authenticated state of an Ethernet NIC. |
| [offStateChange](arkts-network-eap-offstatechange-f.md) | Unsubscribes from 802.1X EAP authentication state changes. |
| [onStateChange](arkts-network-eap-onstatechange-f.md) | Subscribes to 802.1X EAP authentication state changes. |
| [regCustomEapHandler](arkts-network-eap-regcustomeaphandler-f.md) | Registers a custom handler of Extensible Authentication Protocol (EAP) packets for extensible authentication. This API returns the result asynchronously through a callback. |
| [replyCustomEapData](arkts-network-eap-replycustomeapdata-f.md) | Notifies the system of the extensible authentication result. |
| [setEthEapConfig](arkts-network-eap-setetheapconfig-f.md) | Sets the 802.1X EAP configuration for Ethernet. The configuration is persisted and encrypted. |
| [startEthEap](arkts-network-eap-startetheap-f.md) | Starts EAP authentication on an Ethernet NIC. |
| [unregCustomEapHandler](arkts-network-eap-unregcustomeaphandler-f.md) | Unregisters the custom handler of EAP packets for extensible authentication. This API returns the result asynchronously through a callback. |

### Interfaces

| Name | Description |
| --- | --- |
| [EapData](arkts-network-eap-eapdata-i.md) | Defines the EAP data. |
| [EthEapConfig](arkts-network-eap-etheapconfig-i.md) | Represents the 802.1X Ethernet EAP configuration, including the EAP profile and feature toggles. |
| [EthEapProfile](arkts-network-eap-etheapprofile-i.md) | Represents the EAP profile information. |
| [EthEapStateInfo](arkts-network-eap-etheapstateinfo-i.md) | Represents the 802.1X EAP authentication state information, delivered via the stateChange callback. |

### Enums

| Name | Description |
| --- | --- |
| [CustomResult](arkts-network-eap-customresult-e.md) | Enumerates the EAP authentication results. |
| [EapMethod](arkts-network-eap-eapmethod-e.md) | Enumerates the EAP authentication methods. |
| [EthEapConnectAction](arkts-network-eap-etheapconnectaction-e.md) | Enumerates the manual connect actions for the 802.1X EAP authentication of Ethernet. |
| [EthEapState](arkts-network-eap-etheapstate-e.md) | Enumerates the 802.1X EAP authentication states. |
| [Phase2Method](arkts-network-eap-phase2method-e.md) | Enumerates the Phase 2 authentication methods. |
