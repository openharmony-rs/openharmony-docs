# @ohos.telephony.radio(Network Search)

The **radio** module provides basic network search management functions. Using the APIs provided by this module, you can obtain the radio access technology (RAT) used in the CS and PS domains, network status, current network selection mode, ISO country code of the registered network, ID of the slot in which the primary card is located, list of signal strengths of the registered network for the SIM card in the specified slot, and carrier name. Besides, you can check whether the current device supports New Radio \(NR\) and whether the radio service is enabled on the primary SIM card. The CS domain refers to the Circuit Switched domain, and the PS domain refers to the Packet Switched domain.

**Since:** 6

**System capability:** SystemCapability.Telephony.CoreService

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getISOCountryCodeForNetwork](arkts-telephony-radio-getisocountrycodefornetwork-f.md) | Obtains the ISO country code of the network with which the SIM card in the specified slot is registered. This API uses an asynchronous callback to return the result. |
| [getISOCountryCodeForNetwork](arkts-telephony-radio-getisocountrycodefornetwork-f.md) | Obtains the ISO country code of the network with which the SIM card in the specified slot is registered. This API uses a promise to return the result. |
| [getISOCountryCodeForNetworkSync](arkts-telephony-radio-getisocountrycodefornetworksync-f.md) | Obtains the ISO country code of the network with which the SIM card in the specified slot is registered. |
| [getNetworkSelectionMode](arkts-telephony-radio-getnetworkselectionmode-f.md) | Obtains the network selection mode of the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [getNetworkSelectionMode](arkts-telephony-radio-getnetworkselectionmode-f.md) | Obtains the network selection mode of the SIM card in the specified slot. This API uses a promise to return the result. |
| [getNetworkState](arkts-telephony-radio-getnetworkstate-f.md) | Obtains the network status of the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [getNetworkState](arkts-telephony-radio-getnetworkstate-f.md) | Obtains the network status of the SIM card in the specified slot. This API uses a promise to return the result. |
| [getNetworkState](arkts-telephony-radio-getnetworkstate-f.md) | Obtains the network status. This API uses an asynchronous callback to return the result. |
| [getOperatorName](arkts-telephony-radio-getoperatorname-f.md) | Obtains the carrier name of the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [getOperatorName](arkts-telephony-radio-getoperatorname-f.md) | Obtains the carrier name of the SIM card in the specified slot. This API uses a promise to return the result. |
| [getOperatorNameSync](arkts-telephony-radio-getoperatornamesync-f.md) | Obtains the carrier name of the SIM card in the specified slot. |
| [getPrimarySlotId](arkts-telephony-radio-getprimaryslotid-f.md) | Obtains the ID of the slot in which the primary card is located. This API uses an asynchronous callback to return the result. |
| [getPrimarySlotId](arkts-telephony-radio-getprimaryslotid-f.md) | Obtains the ID of the slot in which the primary card is located. This API uses a promise to return the result. |
| [getRadioTech](arkts-telephony-radio-getradiotech-f.md) | Obtains the RAT used in the CS and PS domains for the SIM card in the specified slot. This API uses an asynchronous callback to return the result. The CS domain refers to the Circuit Switched domain, and the PS domain refers to the Packet Switched domain. |
| [getRadioTech](arkts-telephony-radio-getradiotech-f.md) | Obtains the RAT used in the CS and PS domains for the SIM card in the specified slot. This API uses a promise to return the result. The CS domain refers to the Circuit Switched domain, and the PS domain refers to the Packet Switched domain. |
| [getRadioTechSync](arkts-telephony-radio-getradiotechsync-f.md) | Obtains the RAT used in the CS and PS domains for the SIM card in the specified slot. The CS domain refers to the Circuit Switched domain, and the PS domain refers to the Packet Switched domain. |
| [getSignalInformation](arkts-telephony-radio-getsignalinformation-f.md) | Obtains a list of signal strengths of the network with which the SIM card in the specified slot is registered. This API uses an asynchronous callback to return the result. |
| [getSignalInformation](arkts-telephony-radio-getsignalinformation-f.md) | Obtains a list of signal strengths of the network with which the SIM card in the specified slot is registered. This API uses a promise to return the result. |
| [getSignalInformationSync](arkts-telephony-radio-getsignalinformationsync-f.md) | Obtains a list of signal strengths of the network with which the SIM card in the specified slot is registered. |
| [isNrSupported](arkts-telephony-radio-isnrsupported-f.md) | Checks whether the current device supports NR. |
| [isNrSupported](arkts-telephony-radio-isnrsupported-f.md) | Checks whether the SIM card in the specified slot supports NR. |
| [isNRSupported](arkts-telephony-radio-isnrsupported-f.md) | Checks whether the current device supports NR. |
| [isNRSupported](arkts-telephony-radio-isnrsupported-f.md) | Checks whether the SIM card in the specified slot supports NR. |
| [isRadioOn](arkts-telephony-radio-isradioon-f.md) | Checks whether the radio service is enabled on the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [isRadioOn](arkts-telephony-radio-isradioon-f.md) | Checks whether the radio service is enabled on the SIM card in the specified slot. This API uses a promise to return the result. |
| [isRadioOn](arkts-telephony-radio-isradioon-f.md) | Checks whether the radio service is enabled on the primary SIM card. This API uses an asynchronous callback to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [factoryReset](arkts-telephony-radio-factoryreset-f-sys.md) | Reset all network settings of telephony. |
| [getBasebandVersion](arkts-telephony-radio-getbasebandversion-f-sys.md) | Get the version of Baseband. |
| [getBasebandVersion](arkts-telephony-radio-getbasebandversion-f-sys.md) | Get the version of Baseband. |
| [getCellInformation](arkts-telephony-radio-getcellinformation-f-sys.md) | Get the current cell information. |
| [getCellInformation](arkts-telephony-radio-getcellinformation-f-sys.md) | Get the current cell information. |
| [getCellInformation](arkts-telephony-radio-getcellinformation-f-sys.md) | Get the current cell information. |
| [getIMEI](arkts-telephony-radio-getimei-f-sys.md) | Obtains the IMEI of a specified card slot of the device. |
| [getIMEI](arkts-telephony-radio-getimei-f-sys.md) | Obtains the IMEI of a specified card slot of the device. |
| [getIMEI](arkts-telephony-radio-getimei-f-sys.md) | Obtains the IMEI of a specified card slot of the device. |
| [getIMEISV](arkts-telephony-radio-getimeisv-f-sys.md) | Obtains the software version number of a specified card slot of the device. |
| [getImsRegInfo](arkts-telephony-radio-getimsreginfo-f-sys.md) | Get the IMS registration state info of specified IMS service type. |
| [getImsRegInfo](arkts-telephony-radio-getimsreginfo-f-sys.md) | Get the IMS registration state info of specified IMS service type. |
| [getMEID](arkts-telephony-radio-getmeid-f-sys.md) | Obtains the MEID of a specified card slot of the device. |
| [getMEID](arkts-telephony-radio-getmeid-f-sys.md) | Obtains the MEID of a specified card slot of the device. |
| [getMEID](arkts-telephony-radio-getmeid-f-sys.md) | Obtains the MEID of a specified card slot of the device. |
| [getNetworkCapability](arkts-telephony-radio-getnetworkcapability-f-sys.md) | Get the network capability state according to the specified capability type. |
| [getNetworkCapability](arkts-telephony-radio-getnetworkcapability-f-sys.md) | Get the network capability state according to the specified capability type. |
| [getNetworkSearchInformation](arkts-telephony-radio-getnetworksearchinformation-f-sys.md) | Get network search information. |
| [getNetworkSearchInformation](arkts-telephony-radio-getnetworksearchinformation-f-sys.md) | Get network search information. |
| [getNrOptionMode](arkts-telephony-radio-getnroptionmode-f-sys.md) | Get the option mode of NR. |
| [getNrOptionMode](arkts-telephony-radio-getnroptionmode-f-sys.md) | Get the option mode of NR. |
| [getNrOptionMode](arkts-telephony-radio-getnroptionmode-f-sys.md) | Get the option mode of NR. |
| [getNROptionMode](arkts-telephony-radio-getnroptionmode-f-sys.md) | Get the option mode of NR. |
| [getNROptionMode](arkts-telephony-radio-getnroptionmode-f-sys.md) | Get the option mode of NR. |
| [getPreferredNetwork](arkts-telephony-radio-getpreferrednetwork-f-sys.md) | Get the preferred network for the specified SIM card slot. |
| [getPreferredNetwork](arkts-telephony-radio-getpreferrednetwork-f-sys.md) | Get the preferred network for the specified SIM card slot. |
| [getUniqueDeviceId](arkts-telephony-radio-getuniquedeviceid-f-sys.md) | Obtains the unique device ID of a specified card slot of the device. |
| [getUniqueDeviceId](arkts-telephony-radio-getuniquedeviceid-f-sys.md) | Obtains the unique device ID of a specified card slot of the device. |
| [getUniqueDeviceId](arkts-telephony-radio-getuniquedeviceid-f-sys.md) | Obtains the unique device ID of a specified card slot of the device. |
| [isManualNetworkScanning](arkts-telephony-radio-ismanualnetworkscanning-f-sys.md) | Determine whether the current manual network scan is in progress. |
| [off](arkts-telephony-radio-off-f-sys.md#offimsregstatechange) | Unsubscribe from imsRegStateChange event. |
| [on](arkts-telephony-radio-on-f-sys.md#onimsregstatechange) | Called when the IMS registration state of specified IMS service type corresponding to a monitored `slotId` updates. |
| [sendUpdateCellLocationRequest](arkts-telephony-radio-sendupdatecelllocationrequest-f-sys.md) | Actively requests to update location information. |
| [sendUpdateCellLocationRequest](arkts-telephony-radio-sendupdatecelllocationrequest-f-sys.md) | Actively requests to update location information. |
| [sendUpdateCellLocationRequest](arkts-telephony-radio-sendupdatecelllocationrequest-f-sys.md) | Actively requests to update location information. |
| [setNetworkCapability](arkts-telephony-radio-setnetworkcapability-f-sys.md) | Set the type and state for the specified network capability. |
| [setNetworkCapability](arkts-telephony-radio-setnetworkcapability-f-sys.md) | Set the type and state for the specified network capability. |
| [setNetworkSelectionMode](arkts-telephony-radio-setnetworkselectionmode-f-sys.md) | Set the current network selection mode. |
| [setNetworkSelectionMode](arkts-telephony-radio-setnetworkselectionmode-f-sys.md) | Set the current network selection mode. |
| [setNROptionMode](arkts-telephony-radio-setnroptionmode-f-sys.md) | Set the NR option mode. |
| [setNROptionMode](arkts-telephony-radio-setnroptionmode-f-sys.md) | Set the NR option mode. |
| [setPreferredNetwork](arkts-telephony-radio-setpreferrednetwork-f-sys.md) | Set the preferred network for the specified SIM card slot. |
| [setPreferredNetwork](arkts-telephony-radio-setpreferrednetwork-f-sys.md) | Set the preferred network for the specified SIM card slot. |
| [setPrimarySlotId](arkts-telephony-radio-setprimaryslotid-f-sys.md) | Set the index number of the main SIM card slot. |
| [setPrimarySlotId](arkts-telephony-radio-setprimaryslotid-f-sys.md) | Set the index number of the main SIM card slot. |
| [startManualNetworkScan](arkts-telephony-radio-startmanualnetworkscan-f-sys.md) | start ManualNetworkScan , Real-time report. |
| [stopManualNetworkScan](arkts-telephony-radio-stopmanualnetworkscan-f-sys.md) | Stop ManualNetworkScan. |
| [turnOffRadio](arkts-telephony-radio-turnoffradio-f-sys.md) | Turn off the radio service. |
| [turnOffRadio](arkts-telephony-radio-turnoffradio-f-sys.md) | Turn off the radio service. |
| [turnOffRadio](arkts-telephony-radio-turnoffradio-f-sys.md) | Turn off the radio service. |
| [turnOnRadio](arkts-telephony-radio-turnonradio-f-sys.md) | Turn on the radio service. |
| [turnOnRadio](arkts-telephony-radio-turnonradio-f-sys.md) | Turn on the radio service. |
| [turnOnRadio](arkts-telephony-radio-turnonradio-f-sys.md) | Turn on the radio service. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [CellInformation](arkts-telephony-radio-cellinformation-i.md) | Defines the cell information. |
| [NetworkRadioTech](arkts-telephony-radio-networkradiotech-i.md) | Defines the radio access technology for the packet switched (PS) or circuit switched (CS) network. |
| [NetworkState](arkts-telephony-radio-networkstate-i.md) | Defines the network status. |
| [SignalInformation](arkts-telephony-radio-signalinformation-i.md) | Defines the signal strength. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [CdmaCellInformation](arkts-telephony-radio-cdmacellinformation-i-sys.md) | Obtains CDMA cell information. |
| [CellInformation](arkts-telephony-radio-cellinformation-i-sys.md) | Defines the cell information. |
| [GsmCellInformation](arkts-telephony-radio-gsmcellinformation-i-sys.md) | Obtains GSM cell information. |
| [ImsRegInfo](arkts-telephony-radio-imsreginfo-i-sys.md) | Indicates IMS registration information. |
| [LteCellInformation](arkts-telephony-radio-ltecellinformation-i-sys.md) | Obtains LTE cell information. |
| [NetworkInformation](arkts-telephony-radio-networkinformation-i-sys.md) | Obtains the network information. |
| [NetworkSearchRealTimeResult](arkts-telephony-radio-networksearchrealtimeresult-i-sys.md) | Indicates the results of manual network scan |
| [NetworkSearchResult](arkts-telephony-radio-networksearchresult-i-sys.md) | Obtains the network search results. |
| [NetworkSelectionModeOptions](arkts-telephony-radio-networkselectionmodeoptions-i-sys.md) | Obtains the network selection mode option. |
| [NrCellInformation](arkts-telephony-radio-nrcellinformation-i-sys.md) | Obtains NR cell information. |
| [TdscdmaCellInformation](arkts-telephony-radio-tdscdmacellinformation-i-sys.md) | Obtains TDSCDMA cell information. |
| [WcdmaCellInformation](arkts-telephony-radio-wcdmacellinformation-i-sys.md) | Obtains WCDMA cell information. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [NetworkSelectionMode](arkts-telephony-radio-networkselectionmode-e.md) | Enumerates network selection modes. |
| [NetworkType](arkts-telephony-radio-networktype-e.md) | Enumerates network types. |
| [NsaState](arkts-telephony-radio-nsastate-e.md) | Enumerates NSA network states. |
| [RadioTechnology](arkts-telephony-radio-radiotechnology-e.md) | Enumerates radio access technologies. |
| [RegState](arkts-telephony-radio-regstate-e.md) | Defines the network registration status of the device. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ImsRegState](arkts-telephony-radio-imsregstate-e-sys.md) | Obtains IMS registration status. |
| [ImsRegTech](arkts-telephony-radio-imsregtech-e-sys.md) | Indicates IMS registration technology. |
| [ImsServiceType](arkts-telephony-radio-imsservicetype-e-sys.md) | Indicates the type of IMS service. |
| [NetworkCapabilityState](arkts-telephony-radio-networkcapabilitystate-e-sys.md) | Enum for network capability state. |
| [NetworkCapabilityType](arkts-telephony-radio-networkcapabilitytype-e-sys.md) | Enum for network capability type. |
| [NetworkInformationState](arkts-telephony-radio-networkinformationstate-e-sys.md) | Obtains network information status. |
| [NrOptionMode](arkts-telephony-radio-nroptionmode-e-sys.md) | Obtains the option mode of NR. |
| [NROptionMode](arkts-telephony-radio-nroptionmode-e-sys.md) | Obtains the option mode of NR. |
| [PreferredNetworkMode](arkts-telephony-radio-preferrednetworkmode-e-sys.md) | Indicates the preferred network. |
<!--DelEnd-->
