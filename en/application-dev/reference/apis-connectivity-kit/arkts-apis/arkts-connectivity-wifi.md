# @ohos.wifi(WLAN)

This module provides basic Wi-Fi functions (such as Wi-Fi scanning, connection management, connection information query, and signal strength acquisition), peer-to-peer (P2P) functions (such as device discovery, group creation and management, and P2P connection), and Wi-Fi notifications. It is applicable to scenarios where apps access the network or perform P2P data transmission and connection with other devices over Wi-Fi.

> **NOTE:** 
> 
> Since API version 9, this API is no longer maintained. You are advised to use
> [@ohos.wifiManager (WLAN)](arkts-connectivity-wifimanager.md).

**Since:** 6

<!--Device-unnamed-declare namespace wifi--><!--Device-unnamed-declare namespace wifi-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addUntrustedConfig](arkts-connectivity-wifi-adduntrustedconfig-f.md#adduntrustedconfig-1) | Adds the configuration of an untrusted network. This API uses a promise to return the result. |
| [addUntrustedConfig](arkts-connectivity-wifi-adduntrustedconfig-f.md#adduntrustedconfig-2) | Adds the configuration of an untrusted network. This API uses an asynchronous callback to return the result. |
| [createGroup](arkts-connectivity-wifi-creategroup-f.md#creategroup-1) | Creates a P2P group. |
| [getCountryCode](arkts-connectivity-wifi-getcountrycode-f.md#getcountrycode-1) | Obtains the country code. |
| [getCurrentGroup](arkts-connectivity-wifi-getcurrentgroup-f.md#getcurrentgroup-1) | Obtains the current P2P group information. This API uses a promise to return the result. |
| [getCurrentGroup](arkts-connectivity-wifi-getcurrentgroup-f.md#getcurrentgroup-2) | Obtains the current P2P group information. This API uses an asynchronous callback to return the result. |
| [getIpInfo](arkts-connectivity-wifi-getipinfo-f.md#getipinfo-1) | Obtains IP information. |
| [getLinkedInfo](arkts-connectivity-wifi-getlinkedinfo-f.md#getlinkedinfo-1) | Obtains Wi-Fi connection information. This API uses a promise to return the result. |
| [getLinkedInfo](arkts-connectivity-wifi-getlinkedinfo-f.md#getlinkedinfo-2) | Obtains Wi-Fi connection information. This API uses an asynchronous callback to return the result. |
| [getP2pLinkedInfo](arkts-connectivity-wifi-getp2plinkedinfo-f.md#getp2plinkedinfo-1) | Obtains P2P connection information. This API uses a promise to return the result. |
| [getP2pLinkedInfo](arkts-connectivity-wifi-getp2plinkedinfo-f.md#getp2plinkedinfo-2) | Obtains P2P connection information. This API uses an asynchronous callback to return the result. |
| [getP2pPeerDevices](arkts-connectivity-wifi-getp2ppeerdevices-f.md#getp2ppeerdevices-1) | Obtains the P2P peer device list. This API uses a promise to return the result. |
| [getP2pPeerDevices](arkts-connectivity-wifi-getp2ppeerdevices-f.md#getp2ppeerdevices-2) | Obtains the P2P peer device list. This API uses an asynchronous callback to return the result. |
| [getScanInfos](arkts-connectivity-wifi-getscaninfos-f.md#getscaninfos-1) | Obtains the scan result. This API uses a promise to return the result. |
| [getScanInfos](arkts-connectivity-wifi-getscaninfos-f.md#getscaninfos-2) | Obtains the scan result. This API uses an asynchronous callback to return the result. |
| [getSignalLevel](arkts-connectivity-wifi-getsignallevel-f.md#getsignallevel-1) | Calculates the Wi-Fi signal level based on the RSSI and frequency band. |
| [isConnected](arkts-connectivity-wifi-isconnected-f.md#isconnected-1) | Checks whether the Wi-Fi connection is established. |
| [isFeatureSupported](arkts-connectivity-wifi-isfeaturesupported-f.md#isfeaturesupported-1) | Checks whether the device supports the Wi-Fi feature specified by the feature ID. |
| [isWifiActive](arkts-connectivity-wifi-iswifiactive-f.md#iswifiactive-1) | Checks whether Wi-Fi is enabled. |
| [off('wifiStateChange')](arkts-connectivity-wifi-off-f.md#offwifistatechange) | Unsubscribes from Wi-Fi status change events. |
| [off('wifiConnectionChange')](arkts-connectivity-wifi-off-f.md#offwificonnectionchange) | Unsubscribes from Wi-Fi connection status change events. |
| [off('wifiScanStateChange')](arkts-connectivity-wifi-off-f.md#offwifiscanstatechange) | Unsubscribes from WLAN scan state changes. |
| [off('wifiRssiChange')](arkts-connectivity-wifi-off-f.md#offwifirssichange) | Unsubscribes from RSSI changes. |
| [off('hotspotStateChange')](arkts-connectivity-wifi-off-f.md#offhotspotstatechange) | Unsubscribes from hotspot state changes. |
| [off('p2pStateChange')](arkts-connectivity-wifi-off-f.md#offp2pstatechange) | Unsubscribes from P2P state changes. |
| [off('p2pConnectionChange')](arkts-connectivity-wifi-off-f.md#offp2pconnectionchange) | Unsubscribes from P2P connection state changes. |
| [off('p2pDeviceChange')](arkts-connectivity-wifi-off-f.md#offp2pdevicechange) | Unsubscribes from P2P device state changes. |
| [off('p2pPeerDeviceChange')](arkts-connectivity-wifi-off-f.md#offp2ppeerdevicechange) | Unsubscribes from P2P peer device state changes. |
| [off('p2pPersistentGroupChange')](arkts-connectivity-wifi-off-f.md#offp2ppersistentgroupchange) | Unsubscribes from P2P persistent group state changes. |
| [off('p2pDiscoveryChange')](arkts-connectivity-wifi-off-f.md#offp2pdiscoverychange) | Unsubscribes from P2P device discovery state changes. |
| [on('wifiStateChange')](arkts-connectivity-wifi-on-f.md#onwifistatechange) | Subscribes to Wi-Fi status change events. |
| [on('wifiConnectionChange')](arkts-connectivity-wifi-on-f.md#onwificonnectionchange) | Subscribes to Wi-Fi connection status change events. |
| [on('wifiScanStateChange')](arkts-connectivity-wifi-on-f.md#onwifiscanstatechange) | Subscribes to WLAN scan state changes. |
| [on('wifiRssiChange')](arkts-connectivity-wifi-on-f.md#onwifirssichange) | Subscribes to RSSI changes. |
| [on('hotspotStateChange')](arkts-connectivity-wifi-on-f.md#onhotspotstatechange) | Subscribes to hotspot state changes. |
| [on('p2pStateChange')](arkts-connectivity-wifi-on-f.md#onp2pstatechange) | Subscribes to P2P state changes. |
| [on('p2pConnectionChange')](arkts-connectivity-wifi-on-f.md#onp2pconnectionchange) | Subscribes to P2P connection state changes. |
| [on('p2pDeviceChange')](arkts-connectivity-wifi-on-f.md#onp2pdevicechange) | Subscribes to P2P device state changes. |
| [on('p2pPeerDeviceChange')](arkts-connectivity-wifi-on-f.md#onp2ppeerdevicechange) | Subscribes to P2P peer device state changes. |
| [on('p2pPersistentGroupChange')](arkts-connectivity-wifi-on-f.md#onp2ppersistentgroupchange) | Subscribes to P2P persistent group state changes. |
| [on('p2pDiscoveryChange')](arkts-connectivity-wifi-on-f.md#onp2pdiscoverychange) | Subscribes to P2P device discovery state changes. |
| [p2pCancelConnect](arkts-connectivity-wifi-p2pcancelconnect-f.md#p2pcancelconnect-1) | Cancels this P2P connection. |
| [p2pConnect](arkts-connectivity-wifi-p2pconnect-f.md#p2pconnect-1) | Sets up a P2P connection. |
| [removeGroup](arkts-connectivity-wifi-removegroup-f.md#removegroup-1) | Removes this P2P group. |
| [removeUntrustedConfig](arkts-connectivity-wifi-removeuntrustedconfig-f.md#removeuntrustedconfig-1) | Removes the configuration of an untrusted network. This API uses a promise to return the result. |
| [removeUntrustedConfig](arkts-connectivity-wifi-removeuntrustedconfig-f.md#removeuntrustedconfig-2) | Removes the configuration of an untrusted network. This API uses an asynchronous callback to return the result. |
| [scan](arkts-connectivity-wifi-scan-f.md#scan-1) | Starts Wi-Fi scanning. |
| [startDiscoverDevices](arkts-connectivity-wifi-startdiscoverdevices-f.md#startdiscoverdevices-1) | Starts to discover devices. |
| [stopDiscoverDevices](arkts-connectivity-wifi-stopdiscoverdevices-f.md#stopdiscoverdevices-1) | Stops discovering devices. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addDeviceConfig](arkts-connectivity-wifi-adddeviceconfig-f-sys.md#adddeviceconfig-1) | Adds Wi-Fi connection configuration to the device. |
| [addDeviceConfig](arkts-connectivity-wifi-adddeviceconfig-f-sys.md#adddeviceconfig-2) | Adds Wi-Fi connection configuration to the device. |
| [connectToDevice](arkts-connectivity-wifi-connecttodevice-f-sys.md#connecttodevice-1) | Connects to Wi-Fi network. |
| [connectToNetwork](arkts-connectivity-wifi-connecttonetwork-f-sys.md#connecttonetwork-1) | Connects to Wi-Fi network. |
| [deletePersistentGroup](arkts-connectivity-wifi-deletepersistentgroup-f-sys.md#deletepersistentgroup-1) | Deletes the persistent P2P group with the specified network ID. |
| [disableHotspot](arkts-connectivity-wifi-disablehotspot-f-sys.md#disablehotspot-1) | Disables a Wi-Fi hotspot. |
| [disableNetwork](arkts-connectivity-wifi-disablenetwork-f-sys.md#disablenetwork-1) | Disables a specified network. |
| [disableWifi](arkts-connectivity-wifi-disablewifi-f-sys.md#disablewifi-1) | Disables Wi-Fi. |
| [disconnect](arkts-connectivity-wifi-disconnect-f-sys.md#disconnect-1) | Disconnect Wi-Fi network. |
| [enableHotspot](arkts-connectivity-wifi-enablehotspot-f-sys.md#enablehotspot-1) | Enables a Wi-Fi hotspot. |
| [enableWifi](arkts-connectivity-wifi-enablewifi-f-sys.md#enablewifi-1) | Enables Wi-Fi. |
| [getDeviceConfigs](arkts-connectivity-wifi-getdeviceconfigs-f-sys.md#getdeviceconfigs-1) | Obtains the list of all existing Wi-Fi configurations. |
| [getDeviceMacAddress](arkts-connectivity-wifi-getdevicemacaddress-f-sys.md#getdevicemacaddress-1) | Obtains the MAC address of a Wi-Fi device. Wi-Fi must be enabled. |
| [getHotspotConfig](arkts-connectivity-wifi-gethotspotconfig-f-sys.md#gethotspotconfig-1) | Obtains the Wi-Fi hotspot configuration. |
| [getStations](arkts-connectivity-wifi-getstations-f-sys.md#getstations-1) | Obtains the list of clients that are connected to a Wi-Fi hotspot. |
| [getSupportedFeatures](arkts-connectivity-wifi-getsupportedfeatures-f-sys.md#getsupportedfeatures-1) | Obtains the features supported by this device. |
| [isHotspotActive](arkts-connectivity-wifi-ishotspotactive-f-sys.md#ishotspotactive-1) | Checks whether Wi-Fi hotspot is active on a device. |
| [isHotspotDualBandSupported](arkts-connectivity-wifi-ishotspotdualbandsupported-f-sys.md#ishotspotdualbandsupported-1) | Checks whether a device serving as a Wi-Fi hotspot supports both the 2.4 GHz and 5 GHz Wi-Fi. |
| [off('streamChange')](arkts-connectivity-wifi-off-f-sys.md#offstreamchange) | Unsubscribe Wi-Fi stream change events. |
| [off('hotspotStaJoin')](arkts-connectivity-wifi-off-f-sys.md#offhotspotstajoin) | Unsubscribe Wi-Fi hotspot sta join events. |
| [off('hotspotStaLeave')](arkts-connectivity-wifi-off-f-sys.md#offhotspotstaleave) | Unsubscribe Wi-Fi hotspot sta leave events. |
| [on('streamChange')](arkts-connectivity-wifi-on-f-sys.md#onstreamchange) | Subscribe Wi-Fi stream change events. |
| [on('hotspotStaJoin')](arkts-connectivity-wifi-on-f-sys.md#onhotspotstajoin) | Subscribe Wi-Fi hotspot sta join events. |
| [on('hotspotStaLeave')](arkts-connectivity-wifi-on-f-sys.md#onhotspotstaleave) | Subscribe Wi-Fi hotspot sta leave events. |
| [reassociate](arkts-connectivity-wifi-reassociate-f-sys.md#reassociate-1) | Re-associate to current network. |
| [reconnect](arkts-connectivity-wifi-reconnect-f-sys.md#reconnect-1) | Re-connects to current network. |
| [removeAllNetwork](arkts-connectivity-wifi-removeallnetwork-f-sys.md#removeallnetwork-1) | Removes all the saved Wi-Fi configurations. |
| [removeDevice](arkts-connectivity-wifi-removedevice-f-sys.md#removedevice-1) | Deletes a Wi-Fi network with a specified ID. |
| [setDeviceName](arkts-connectivity-wifi-setdevicename-f-sys.md#setdevicename-1) | Sets the name of the Wi-Fi P2P device. |
| [setHotspotConfig](arkts-connectivity-wifi-sethotspotconfig-f-sys.md#sethotspotconfig-1) | Sets the hotspot for a device. |
| [updateNetwork](arkts-connectivity-wifi-updatenetwork-f-sys.md#updatenetwork-1) | Updates the specified Wi-Fi configuration. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [IpInfo](arkts-connectivity-wifi-ipinfo-i.md) | Represents the IP information obtained. |
| [WifiDeviceConfig](arkts-connectivity-wifi-wifideviceconfig-i.md) | Represents the Wi-Fi configuration information. |
| [WifiLinkedInfo](arkts-connectivity-wifi-wifilinkedinfo-i.md) | Provides information about a Wi-Fi connection. |
| [WifiP2PConfig](arkts-connectivity-wifi-wifip2pconfig-i.md) | Represents P2P group configuration. |
| [WifiP2pDevice](arkts-connectivity-wifi-wifip2pdevice-i.md) | Represents the P2P device information. |
| [WifiP2pGroupInfo](arkts-connectivity-wifi-wifip2pgroupinfo-i.md) | Represents the P2P group information. |
| [WifiP2pLinkedInfo](arkts-connectivity-wifi-wifip2plinkedinfo-i.md) | Provides information about the P2P connection. |
| [WifiScanInfo](arkts-connectivity-wifi-wifiscaninfo-i.md) | Represents the Wi-Fi hotspot information. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [HotspotConfig](arkts-connectivity-wifi-hotspotconfig-i-sys.md) | Wi-Fi hotspot configuration information. |
| [IpConfig](arkts-connectivity-wifi-ipconfig-i-sys.md) | Wi-Fi IP configuration information. |
| [StationInfo](arkts-connectivity-wifi-stationinfo-i-sys.md) | Wi-Fi station information. |
| [WifiDeviceConfig](arkts-connectivity-wifi-wifideviceconfig-i-sys.md) | Represents the Wi-Fi configuration information. |
| [WifiLinkedInfo](arkts-connectivity-wifi-wifilinkedinfo-i-sys.md) | Provides information about a Wi-Fi connection. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ConnState](arkts-connectivity-wifi-connstate-e.md) | Enumerates the Wi-Fi connection statuses. |
| [GroupOwnerBand](arkts-connectivity-wifi-groupownerband-e.md) | Enumerates the P2P group frequency bands. |
| [P2pConnectState](arkts-connectivity-wifi-p2pconnectstate-e.md) | Enumerates the P2P connection states. |
| [P2pDeviceStatus](arkts-connectivity-wifi-p2pdevicestatus-e.md) | Enumerates the P2P device states. |
| [WifiSecurityType](arkts-connectivity-wifi-wifisecuritytype-e.md) | Enumerates the Wi-Fi security types. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [IpType](arkts-connectivity-wifi-iptype-e-sys.md) | Wi-Fi IP type enumeration. |
| [SuppState](arkts-connectivity-wifi-suppstate-e-sys.md) | The state of the supplicant enumeration. |
<!--DelEnd-->
