# @ohos.wifi

Provides methods to operate or manage Wi-Fi. @namespace wifi

**Since:** 6

**System capability:** SystemCapability.Communication.WiFi.STA

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addUntrustedConfig](arkts-connectivity-wifi-adduntrustedconfig-f.md) | Adds a specified untrusted hotspot configuration. |
| [addUntrustedConfig](arkts-connectivity-wifi-adduntrustedconfig-f.md) | Adds a specified untrusted hotspot configuration. |
| [createGroup](arkts-connectivity-wifi-creategroup-f.md) | Creates a P2P group. |
| [getCountryCode](arkts-connectivity-wifi-getcountrycode-f.md) | Obtains the country code of this device. |
| [getCurrentGroup](arkts-connectivity-wifi-getcurrentgroup-f.md) | Obtains information about the current group. |
| [getCurrentGroup](arkts-connectivity-wifi-getcurrentgroup-f.md) | Obtains information about the current group. |
| [getIpInfo](arkts-connectivity-wifi-getipinfo-f.md) | Obtains the IP information of a Wi-Fi connection. |
| [getLinkedInfo](arkts-connectivity-wifi-getlinkedinfo-f.md) | Obtains information about a Wi-Fi connection. |
| [getLinkedInfo](arkts-connectivity-wifi-getlinkedinfo-f.md) | Obtains information about a Wi-Fi connection. |
| [getP2pLinkedInfo](arkts-connectivity-wifi-getp2plinkedinfo-f.md) | Obtains information about a P2P connection. |
| [getP2pLinkedInfo](arkts-connectivity-wifi-getp2plinkedinfo-f.md) | Obtains information about a P2P connection. |
| [getP2pPeerDevices](arkts-connectivity-wifi-getp2ppeerdevices-f.md) | Obtains the information about the found devices. |
| [getP2pPeerDevices](arkts-connectivity-wifi-getp2ppeerdevices-f.md) | Obtains the information about the found devices. |
| [getScanInfos](arkts-connectivity-wifi-getscaninfos-f.md) | Obtains the hotspot information that scanned. |
| [getScanInfos](arkts-connectivity-wifi-getscaninfos-f.md) | Obtains the hotspot information that scanned. |
| [getSignalLevel](arkts-connectivity-wifi-getsignallevel-f.md) | Calculates the Wi-Fi signal level based on the Wi-Fi RSSI and frequency band. |
| [isConnected](arkts-connectivity-wifi-isconnected-f.md) | Checks whether a Wi-Fi connection has been set up. |
| [isFeatureSupported](arkts-connectivity-wifi-isfeaturesupported-f.md) | Checks whether this device supports a specified feature. |
| [isWifiActive](arkts-connectivity-wifi-iswifiactive-f.md) | Queries the Wi-Fi status |
| [off](arkts-connectivity-wifi-off-f.md#offwifistatechange) | Unsubscribe Wi-Fi status change events. |
| [off](arkts-connectivity-wifi-off-f.md#offwificonnectionchange) | Unsubscribe Wi-Fi connection change events. |
| [off](arkts-connectivity-wifi-off-f.md#offwifiscanstatechange) | Unsubscribe Wi-Fi scan status change events. |
| [off](arkts-connectivity-wifi-off-f.md#offwifirssichange) | Unsubscribe Wi-Fi rssi change events. |
| [off](arkts-connectivity-wifi-off-f.md#offhotspotstatechange) | Unsubscribe Wi-Fi hotspot state change events. |
| [off](arkts-connectivity-wifi-off-f.md#offp2pstatechange) | Unsubscribe P2P status change events. |
| [off](arkts-connectivity-wifi-off-f.md#offp2pconnectionchange) | Unsubscribe P2P connection change events. |
| [off](arkts-connectivity-wifi-off-f.md#offp2pdevicechange) | Unsubscribe P2P local device change events. |
| [off](arkts-connectivity-wifi-off-f.md#offp2ppeerdevicechange) | Unsubscribe P2P peer device change events. |
| [off](arkts-connectivity-wifi-off-f.md#offp2ppersistentgroupchange) | Unsubscribe P2P persistent group change events. |
| [off](arkts-connectivity-wifi-off-f.md#offp2pdiscoverychange) | Unsubscribe P2P discovery events. |
| [on](arkts-connectivity-wifi-on-f.md#onwifistatechange) | Subscribe Wi-Fi status change events. |
| [on](arkts-connectivity-wifi-on-f.md#onwificonnectionchange) | Subscribe Wi-Fi connection change events. |
| [on](arkts-connectivity-wifi-on-f.md#onwifiscanstatechange) | Subscribe Wi-Fi scan status change events. |
| [on](arkts-connectivity-wifi-on-f.md#onwifirssichange) | Subscribe Wi-Fi rssi change events. |
| [on](arkts-connectivity-wifi-on-f.md#onhotspotstatechange) | Subscribe Wi-Fi hotspot state change events. |
| [on](arkts-connectivity-wifi-on-f.md#onp2pstatechange) | Subscribe P2P status change events. |
| [on](arkts-connectivity-wifi-on-f.md#onp2pconnectionchange) | Subscribe P2P connection change events. |
| [on](arkts-connectivity-wifi-on-f.md#onp2pdevicechange) | Subscribe P2P local device change events. |
| [on](arkts-connectivity-wifi-on-f.md#onp2ppeerdevicechange) | Subscribe P2P peer device change events. |
| [on](arkts-connectivity-wifi-on-f.md#onp2ppersistentgroupchange) | Subscribe P2P persistent group change events. |
| [on](arkts-connectivity-wifi-on-f.md#onp2pdiscoverychange) | Subscribe P2P discovery events. |
| [p2pCancelConnect](arkts-connectivity-wifi-p2pcancelconnect-f.md) | Canceling a P2P connection. |
| [p2pConnect](arkts-connectivity-wifi-p2pconnect-f.md) | Initiates a P2P connection to a device with the specified configuration. |
| [removeGroup](arkts-connectivity-wifi-removegroup-f.md) | Removes a P2P group. |
| [removeUntrustedConfig](arkts-connectivity-wifi-removeuntrustedconfig-f.md) | Removes a specified untrusted hotspot configuration. |
| [removeUntrustedConfig](arkts-connectivity-wifi-removeuntrustedconfig-f.md) | Removes a specified untrusted hotspot configuration. |
| [scan](arkts-connectivity-wifi-scan-f.md) | Scans Wi-Fi hotspot. |
| [startDiscoverDevices](arkts-connectivity-wifi-startdiscoverdevices-f.md) | Discover Wi-Fi P2P devices. |
| [stopDiscoverDevices](arkts-connectivity-wifi-stopdiscoverdevices-f.md) | Stops discovering Wi-Fi P2P devices. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addDeviceConfig](arkts-connectivity-wifi-adddeviceconfig-f-sys.md) | Adds Wi-Fi connection configuration to the device. |
| [addDeviceConfig](arkts-connectivity-wifi-adddeviceconfig-f-sys.md) | Adds Wi-Fi connection configuration to the device. |
| [connectToDevice](arkts-connectivity-wifi-connecttodevice-f-sys.md) | Connects to Wi-Fi network. |
| [connectToNetwork](arkts-connectivity-wifi-connecttonetwork-f-sys.md) | Connects to Wi-Fi network. |
| [deletePersistentGroup](arkts-connectivity-wifi-deletepersistentgroup-f-sys.md) | Deletes the persistent P2P group with the specified network ID. |
| [disableHotspot](arkts-connectivity-wifi-disablehotspot-f-sys.md) | Disables a Wi-Fi hotspot. |
| [disableNetwork](arkts-connectivity-wifi-disablenetwork-f-sys.md) | Disables a specified network. |
| [disableWifi](arkts-connectivity-wifi-disablewifi-f-sys.md) | Disables Wi-Fi. |
| [disconnect](arkts-connectivity-wifi-disconnect-f-sys.md) | Disconnect Wi-Fi network. |
| [enableHotspot](arkts-connectivity-wifi-enablehotspot-f-sys.md) | Enables a Wi-Fi hotspot. |
| [enableWifi](arkts-connectivity-wifi-enablewifi-f-sys.md) | Enables Wi-Fi. |
| [getDeviceConfigs](arkts-connectivity-wifi-getdeviceconfigs-f-sys.md) | Obtains the list of all existing Wi-Fi configurations. |
| [getDeviceMacAddress](arkts-connectivity-wifi-getdevicemacaddress-f-sys.md) | Obtains the MAC address of a Wi-Fi device. Wi-Fi must be enabled. |
| [getHotspotConfig](arkts-connectivity-wifi-gethotspotconfig-f-sys.md) | Obtains the Wi-Fi hotspot configuration. |
| [getStations](arkts-connectivity-wifi-getstations-f-sys.md) | Obtains the list of clients that are connected to a Wi-Fi hotspot. |
| [getSupportedFeatures](arkts-connectivity-wifi-getsupportedfeatures-f-sys.md) | Obtains the features supported by this device. |
| [isHotspotActive](arkts-connectivity-wifi-ishotspotactive-f-sys.md) | Checks whether Wi-Fi hotspot is active on a device. |
| [isHotspotDualBandSupported](arkts-connectivity-wifi-ishotspotdualbandsupported-f-sys.md) | Checks whether a device serving as a Wi-Fi hotspot supports both the 2.4 GHz and 5 GHz Wi-Fi. |
| [off](arkts-connectivity-wifi-off-f-sys.md#offstreamchange) | Unsubscribe Wi-Fi stream change events. |
| [off](arkts-connectivity-wifi-off-f-sys.md#offhotspotstajoin) | Unsubscribe Wi-Fi hotspot sta join events. |
| [off](arkts-connectivity-wifi-off-f-sys.md#offhotspotstaleave) | Unsubscribe Wi-Fi hotspot sta leave events. |
| [on](arkts-connectivity-wifi-on-f-sys.md#onstreamchange) | Subscribe Wi-Fi stream change events. |
| [on](arkts-connectivity-wifi-on-f-sys.md#onhotspotstajoin) | Subscribe Wi-Fi hotspot sta join events. |
| [on](arkts-connectivity-wifi-on-f-sys.md#onhotspotstaleave) | Subscribe Wi-Fi hotspot sta leave events. |
| [reassociate](arkts-connectivity-wifi-reassociate-f-sys.md) | Re-associate to current network. |
| [reconnect](arkts-connectivity-wifi-reconnect-f-sys.md) | Re-connects to current network. |
| [removeAllNetwork](arkts-connectivity-wifi-removeallnetwork-f-sys.md) | Removes all the saved Wi-Fi configurations. |
| [removeDevice](arkts-connectivity-wifi-removedevice-f-sys.md) | Deletes a Wi-Fi network with a specified ID. |
| [setDeviceName](arkts-connectivity-wifi-setdevicename-f-sys.md) | Sets the name of the Wi-Fi P2P device. |
| [setHotspotConfig](arkts-connectivity-wifi-sethotspotconfig-f-sys.md) | Sets the hotspot for a device. |
| [updateNetwork](arkts-connectivity-wifi-updatenetwork-f-sys.md) | Updates the specified Wi-Fi configuration. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [IpInfo](arkts-connectivity-wifi-ipinfo-i.md) | Wi-Fi IP information. |
| [WifiDeviceConfig](arkts-connectivity-wifi-wifideviceconfig-i.md) | Wi-Fi device configuration information. |
| [WifiLinkedInfo](arkts-connectivity-wifi-wifilinkedinfo-i.md) | Wi-Fi connection information. |
| [WifiP2PConfig](arkts-connectivity-wifi-wifip2pconfig-i.md) | P2P config. @interface WifiP2PConfig |
| [WifiP2pDevice](arkts-connectivity-wifi-wifip2pdevice-i.md) | P2P device information. |
| [WifiP2pGroupInfo](arkts-connectivity-wifi-wifip2pgroupinfo-i.md) | P2P group information. @interface WifiP2pGroupInfo |
| [WifiP2pLinkedInfo](arkts-connectivity-wifi-wifip2plinkedinfo-i.md) | P2P linked information. @typedef WifiP2pLinkedInfo |
| [WifiScanInfo](arkts-connectivity-wifi-wifiscaninfo-i.md) | Describes the scanned Wi-Fi information. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [HotspotConfig](arkts-connectivity-wifi-hotspotconfig-i-sys.md) | Wi-Fi hotspot configuration information. |
| [IpConfig](arkts-connectivity-wifi-ipconfig-i-sys.md) | Wi-Fi IP configuration information. |
| [StationInfo](arkts-connectivity-wifi-stationinfo-i-sys.md) | Wi-Fi station information. |
| [WifiDeviceConfig](arkts-connectivity-wifi-wifideviceconfig-i-sys.md) | Wi-Fi device configuration information. |
| [WifiLinkedInfo](arkts-connectivity-wifi-wifilinkedinfo-i-sys.md) | Wi-Fi connection information. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ConnState](arkts-connectivity-wifi-connstate-e.md) | The state of Wi-Fi connection enumeration. |
| [GroupOwnerBand](arkts-connectivity-wifi-groupownerband-e.md) | P2P group owner band. |
| [P2pConnectState](arkts-connectivity-wifi-p2pconnectstate-e.md) | P2P connection status. |
| [P2pDeviceStatus](arkts-connectivity-wifi-p2pdevicestatus-e.md) | P2P device status. |
| [WifiSecurityType](arkts-connectivity-wifi-wifisecuritytype-e.md) | Describes the wifi security type. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [IpType](arkts-connectivity-wifi-iptype-e-sys.md) | Wi-Fi IP type enumeration. |
| [SuppState](arkts-connectivity-wifi-suppstate-e-sys.md) | The state of the supplicant enumeration. |
<!--DelEnd-->
