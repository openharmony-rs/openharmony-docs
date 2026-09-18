# @ohos.telephony.observer(Telephony Status Observer)

The **observer** module provides event subscription management functions. You can register or unregister an observer that listens for the following events: network status change, signal status change, call status change, cellular data connection status, uplink and downlink data flow status of cellular data services, and SIM status change.

**Since:** 6

**System capability:** SystemCapability.Telephony.StateRegistry

## Modules to Import

```TypeScript
import { observer } from '@kit.TelephonyKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [off](arkts-telephony-observer-off-f.md#offnetworkstatechange) | Unregisters the observer for network status change events. This API uses an asynchronous callback to return the execution result. |
| [off](arkts-telephony-observer-off-f.md#offsignalinfochange) | Unregisters the observer for signal status change events. This API uses an asynchronous callback to return the execution result. |
| [off](arkts-telephony-observer-off-f.md#offcellulardataconnectionstatechange) | Unregisters the observer for connection status change events of the cellular data link. This API uses an asynchronous callback to return the result. |
| [off](arkts-telephony-observer-off-f.md#offcellulardataflowchange) | Unregisters the observer for the uplink and downlink data flow status change events of the cellular data service. This API uses an asynchronous callback to return the result. |
| [off](arkts-telephony-observer-off-f.md#offcallstatechange) | Unregisters the observer for call status change events. This API uses an asynchronous callback to return the execution result. |
| [off](arkts-telephony-observer-off-f.md#offcallstatechangeex) | Unregisters the observer for extended call status change events. This API uses an asynchronous callback to return the execution result. |
| [off](arkts-telephony-observer-off-f.md#offsimstatechange) | Unregisters the observer for SIM card status change events. This API uses an asynchronous callback to return the result. |
| [off](arkts-telephony-observer-off-f.md#officcaccountinfochange) | Unregisters the observer for account information change events of the SIM card. This API uses an asynchronous callback to return the result. |
| [offCCallStateChange](arkts-telephony-observer-offccallstatechange-f.md) | Cancels the listening on the carrier call status and obtaining of the call number by a third-party application. This method uses an asynchronous callback to return the result. |
| [offCommunicationStateChange](arkts-telephony-observer-offcommunicationstatechange-f.md) | Unsubscribes from the callback for listening to the 5A state. |
| [offGetSimActiveState](arkts-telephony-observer-offgetsimactivestate-f.md) | Unregisters an observer for SIM card activation state changes. This API uses an asynchronous callback to return the execution result. |
| [on](arkts-telephony-observer-on-f.md#onnetworkstatechange) | Registers an observer for network status change events. This API uses an asynchronous callback to return the execution result. |
| [on](arkts-telephony-observer-on-f.md#onnetworkstatechange) | Registers an observer for network status change events of the SIM card in the specified slot. This API uses an asynchronous callback to return the execution result. |
| [on](arkts-telephony-observer-on-f.md#onsignalinfochange) | Registers an observer for signal status change events. This API uses an asynchronous callback to return the execution result. |
| [on](arkts-telephony-observer-on-f.md#onsignalinfochange) | Registers an observer for signal status change events of the SIM card in the specified slot. This API uses an asynchronous callback to return the execution result. |
| [on](arkts-telephony-observer-on-f.md#oncellulardataconnectionstatechange) | Registers an observer for connection status change events of the cellular data link. This API uses an asynchronous callback to return the result. |
| [on](arkts-telephony-observer-on-f.md#oncellulardataconnectionstatechange) | Registers an observer for connection status change events of the cellular data link over the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [on](arkts-telephony-observer-on-f.md#oncellulardataflowchange) | Registers an observer for the uplink and downlink data flow status change events of the cellular data service. This API uses an asynchronous callback to return the result. |
| [on](arkts-telephony-observer-on-f.md#oncellulardataflowchange) | Registers an observer for the uplink and downlink data flow status change events of the cellular data service on the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [on](arkts-telephony-observer-on-f.md#oncallstatechange) | Registers an observer for call status change events. This API uses an asynchronous callback to return the execution result. |
| [on](arkts-telephony-observer-on-f.md#oncallstatechange) | Registers an observer for call status change events. This API uses an asynchronous callback to return the execution result. |
| [on](arkts-telephony-observer-on-f.md#oncallstatechangeex) | Registers an observer for extended call status change events. This API uses an asynchronous callback to return the execution result. |
| [on](arkts-telephony-observer-on-f.md#onsimstatechange) | Registers an observer for SIM card status change events. This API uses an asynchronous callback to return the result. |
| [on](arkts-telephony-observer-on-f.md#onsimstatechange) | Registers an observer for status change events of the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [on](arkts-telephony-observer-on-f.md#oniccaccountinfochange) | Registers an observer for account information change events of the SIM card. This API uses an asynchronous callback to return the result. |
| [onCCallStateChange](arkts-telephony-observer-onccallstatechange-f.md) | Subscribes to the carrier call state changes and obtains the call number. This method uses an asynchronous callback to return the execution result. |
| [onCommunicationStateChange](arkts-telephony-observer-oncommunicationstatechange-f.md) | This API uses an asynchronous callback to return the result. |
| [onGetSimActiveState](arkts-telephony-observer-ongetsimactivestate-f.md) | Registers an observer for SIM card activation state changes. This API uses an asynchronous callback to return the execution result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [off](arkts-telephony-observer-off-f-sys.md#offcellinfochange) | Unregisters the observer for cell information change events. This API uses an asynchronous callback to return the result. |
| [on](arkts-telephony-observer-on-f-sys.md#oncellinfochange) | Registers an observer for cell information change events. This API uses an asynchronous callback to return the result. |
| [on](arkts-telephony-observer-on-f-sys.md#oncellinfochange) | Registers an observer for signal status change events of the SIM card in the specified slot. This API uses an asynchronous callback to return the execution result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [CallStateInfo](arkts-telephony-observer-callstateinfo-i.md) | Defines information about the call status. |
| [CCallStateInfo](arkts-telephony-observer-ccallstateinfo-i.md) | Defines information about the call status. |
| [DataConnectionStateInfo](arkts-telephony-observer-dataconnectionstateinfo-i.md) | Defines information about the data connection status. |
| [ObserverOptions](arkts-telephony-observer-observeroptions-i.md) | Defines event subscription parameters. |
| [SimStateData](arkts-telephony-observer-simstatedata-i.md) | Enumerates SIM card types and states. |

### Enums

| Name | Description |
| --- | --- |
| [LockReason](arkts-telephony-observer-lockreason-e.md) | Enumerates SIM card lock types. |

### Types

| Name | Description |
| --- | --- |
| [CallState](arkts-telephony-observer-callstate-t.md) | Enumerates call states. |
| [CardType](arkts-telephony-observer-cardtype-t.md) | Enumerates SIM card types. |
| [CCallState](arkts-telephony-observer-ccallstate-t.md) | Enumerates carrier call states. |
| [DataConnectState](arkts-telephony-observer-dataconnectstate-t.md) | Describes the connection status of a cellular data link. |
| [DataFlowType](arkts-telephony-observer-dataflowtype-t.md) | Defines the cellular data flow type. |
| [NetworkState](arkts-telephony-observer-networkstate-t.md) | Defines the network status. |
| [RatType](arkts-telephony-observer-rattype-t.md) | Enumerates the radio access technologies. |
| [SignalInformation](arkts-telephony-observer-signalinformation-t.md) | Defines the signal strength. |
| [SimState](arkts-telephony-observer-simstate-t.md) | SIM card state. |
| [TelCallState](arkts-telephony-observer-telcallstate-t.md) | Enumerates call states. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [CellInformation](arkts-telephony-observer-cellinformation-t-sys.md) | Describes current cell information. |
| [NetworkSearchRealTimeResult](arkts-telephony-observer-networksearchrealtimeresult-t-sys.md) | Indicates the result of network search. |
<!--DelEnd-->
