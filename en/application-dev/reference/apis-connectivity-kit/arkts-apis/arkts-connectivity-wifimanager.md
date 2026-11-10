# @ohos.wifiManager(WLAN)

This module provides basic Wi-Fi functions, peer-to-peer (P2P) functions, and Wi-Fi message notification services. It allows applications to communicate with devices over Wi-Fi.

**Since:** 9

<!--Device-unnamed-declare namespace wifiManager--><!--Device-unnamed-declare namespace wifiManager-End-->

**System capability:** 
- API version 12 and later: SystemCapability.Communication.WiFi.STA

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addCandidateConfig](arkts-connectivity-wifimanager-addcandidateconfig-f.md#addcandidateconfig-1) | Add a specified candidate hotspot configuration and returns the networkId. This method adds one configuration at a time. After this configuration is added, your device will determine whether to connect to the hotspot. The app must be in the foreground. |
| [addCandidateConfig](arkts-connectivity-wifimanager-addcandidateconfig-f.md#addcandidateconfig-2) | Add a specified candidate hotspot configuration and returns the networkId. This method adds one configuration at a time. After this configuration is added, your device will determine whether to connect to the hotspot. The app must be in the foreground. |
| [addDeviceConfig](arkts-connectivity-wifimanager-adddeviceconfig-f.md#adddeviceconfig-1) | Add Wi-Fi connection configuration to the device. The configuration will be updated when the configuration is added. |
| [addDeviceConfig](arkts-connectivity-wifimanager-adddeviceconfig-f.md#adddeviceconfig-2) | Add Wi-Fi connection configuration to the device. The configuration will be updated when the configuration is added. |
| [addDnsSdLocalP2pService](arkts-connectivity-wifimanager-adddnssdlocalp2pservice-f.md#adddnssdlocalp2pservice-1) | Adds and registers the local P2P service description of DNS-SD (DNS service discovery) to be discovered by the peer device. |
| [addDnsSdServiceRequest](arkts-connectivity-wifimanager-adddnssdservicerequest-f.md#adddnssdservicerequest-1) | Adds a DNS-SD service discovery request that matches DNS-SD services. |
| [addUpnpLocalP2pService](arkts-connectivity-wifimanager-addupnplocalp2pservice-f.md#addupnplocalp2pservice-1) | Adds and registers the local P2P service description of the UPnP (Universal Plug and Play) service to be discovered by the peer device. |
| [addUpnpServiceRequest](arkts-connectivity-wifimanager-addupnpservicerequest-f.md#addupnpservicerequest-1) | Adds a UPnP service discovery request that matches the specified search target. |
| [connectToCandidateConfig](arkts-connectivity-wifimanager-connecttocandidateconfig-f.md#connecttocandidateconfig-1) | Connect to a specified candidate hotspot by networkId, only the configuration which is added by ourself is allowed to be connected. This method connect to a configuration at a time. The app must be in the foreground. |
| [connectToCandidateConfig](arkts-connectivity-wifimanager-connecttocandidateconfig-f.md#connecttocandidateconfig-2) | Connect to the specified candidate hotspot using connect settings. |
| [connectToCandidateConfigWithUserAction](arkts-connectivity-wifimanager-connecttocandidateconfigwithuseraction-f.md#connecttocandidateconfigwithuseraction-1) | Connect to a specified candidate hotspot by networkId, and wait for user respond result. Only the configuration which is added by ourself is allowed to be connected. This method connect to a configuration at a time. The app must be in the foreground. |
| [connectToNetwork](arkts-connectivity-wifimanager-connecttonetwork-f.md#connecttonetwork-1) | Connect to Wi-Fi hotspot by networkId. |
| [createGroup](arkts-connectivity-wifimanager-creategroup-f.md#creategroup-1) | Create a P2P group. |
| [disableWifi](arkts-connectivity-wifimanager-disablewifi-f.md#disablewifi-1) | Disable Wi-Fi. |
| [disconnect](arkts-connectivity-wifimanager-disconnect-f.md#disconnect-1) | Disconnect connection between sta and Wi-Fi hotspot. |
| [disconnectFromCandidateConfig](arkts-connectivity-wifimanager-disconnectfromcandidateconfig-f.md#disconnectfromcandidateconfig-1) | Disconnects a candidate network identified by networkId for a period of time. The disconnected candidate network will not be re-associated during the block duration. You can only disconnect candidate networks that were added by the caller. |
| [discoverServices](arkts-connectivity-wifimanager-discoverservices-f.md#discoverservices-1) | Starts P2P service discovery. The pending requests' TLV queries are used, falling back to all service types if the pending list is empty. Use [addDnsSdServiceRequest](arkts-connectivity-wifimanager-adddnssdservicerequest-f.md) or [addUpnpServiceRequest](arkts-connectivity-wifimanager-addupnpservicerequest-f.md) to add a service request before starting discovery. |
| [enableWifi](arkts-connectivity-wifimanager-enablewifi-f.md#enablewifi-1) | Enable Wi-Fi. |
| [getCandidateConfigs](arkts-connectivity-wifimanager-getcandidateconfigs-f.md#getcandidateconfigs-1) | Obtain the list of all existed candidate Wi-Fi configurations which added by ourself. You can obtain only the Wi-Fi configurations you created on your own application. |
| [getCountryCode](arkts-connectivity-wifimanager-getcountrycode-f.md#getcountrycode-1) | Obtain the country code of the device. |
| [getCurrentGroup](arkts-connectivity-wifimanager-getcurrentgroup-f.md#getcurrentgroup-1) | Obtain information about the current p2p group. |
| [getCurrentGroup](arkts-connectivity-wifimanager-getcurrentgroup-f.md#getcurrentgroup-2) | Obtain information about the current p2p group. |
| [getDeviceConfigs](arkts-connectivity-wifimanager-getdeviceconfigs-f.md#getdeviceconfigs-1) | Obtain the list of all existed Wi-Fi configurations. |
| [getDeviceMacAddress](arkts-connectivity-wifimanager-getdevicemacaddress-f.md#getdevicemacaddress-1) | Obtain the MAC address of a Wi-Fi device. Wi-Fi must be enabled. The MAC address is unique and cannot be changed. |
| [getIpInfo](arkts-connectivity-wifimanager-getipinfo-f.md#getipinfo-1) | Obtain the IPv4 information of the Wi-Fi connection. The IP information includes the host IP address, gateway address, and DNS information. |
| [getIpv6Info](arkts-connectivity-wifimanager-getipv6info-f.md#getipv6info-1) | Obtain the IPv6 information of the Wi-Fi connection. The IPv6 information includes the host IP address, gateway address, and DNS information. |
| [getLinkedInfo](arkts-connectivity-wifimanager-getlinkedinfo-f.md#getlinkedinfo-1) | Obtain connection information about the Wi-Fi connection. If does't have the permission of ohos.permission.GET_WIFI_PEERS_MAC, return random bssid. |
| [getLinkedInfo](arkts-connectivity-wifimanager-getlinkedinfo-f.md#getlinkedinfo-2) | Obtain connection information about the Wi-Fi connection. |
| [getLinkedInfoSync](arkts-connectivity-wifimanager-getlinkedinfosync-f.md#getlinkedinfosync-1) | Obtain connection information about the Wi-Fi connection.this apireturns the result syncchronously. If does't have the permission of ohos.permission.GET_WIFI_PEERS_MAC, return random bssid. |
| [getLocalP2pServices](arkts-connectivity-wifimanager-getlocalp2pservices-f.md#getlocalp2pservices-1) | Queries the local P2P services. This API uses a promise to return the result. |
| [getMultiLinkedInfo](arkts-connectivity-wifimanager-getmultilinkedinfo-f.md#getmultilinkedinfo-1) | Obtain multiple Wi-Fi connection information when Wi-Fi linked in MLO(Muti-Link Operation) state. If does't have the permission of ohos.permission.GET_WIFI_PEERS_MAC, return random bssid. |
| [getP2pLinkedInfo](arkts-connectivity-wifimanager-getp2plinkedinfo-f.md#getp2plinkedinfo-1) | Obtain information about the P2P connection. |
| [getP2pLinkedInfo](arkts-connectivity-wifimanager-getp2plinkedinfo-f.md#getp2plinkedinfo-2) | Obtain information about the P2P connection. |
| [getP2pLocalDevice](arkts-connectivity-wifimanager-getp2plocaldevice-f.md#getp2plocaldevice-1) | Obtain the information about own device information. DeviceAddress in the returned WifiP2pDevice will be set "00:00:00:00:00:00", if ohos.permission.GET_WIFI_LOCAL_MAC is not granted. |
| [getP2pLocalDevice](arkts-connectivity-wifimanager-getp2plocaldevice-f.md#getp2plocaldevice-2) | Obtain the information about own device information. DeviceAddress in the returned WifiP2pDevice will be set "00:00:00:00:00:00", if ohos.permission.GET_WIFI_LOCAL_MAC is not granted. |
| [getP2pPeerDevices](arkts-connectivity-wifimanager-getp2ppeerdevices-f.md#getp2ppeerdevices-1) | Obtain the information about the found devices. |
| [getP2pPeerDevices](arkts-connectivity-wifimanager-getp2ppeerdevices-f.md#getp2ppeerdevices-2) | Obtain the information about the found devices. |
| [getP2pServiceRequest](arkts-connectivity-wifimanager-getp2pservicerequest-f.md#getp2pservicerequest-1) | Queries the pending P2P service discovery requests. This API uses a promise to return the result. |
| [getScanInfoList](arkts-connectivity-wifimanager-getscaninfolist-f.md#getscaninfolist-1) | Obtain the scanned station list. If does't have the permission of ohos.permission.GET_WIFI_PEERS_MAC, return random bssid. |
| [getSignalLevel](arkts-connectivity-wifimanager-getsignallevel-f.md#getsignallevel-1) | Calculate the Wi-Fi signal level based on the Wi-Fi RSSI and frequency band. |
| [isBandTypeSupported](arkts-connectivity-wifimanager-isbandtypesupported-f.md#isbandtypesupported-1) | Check whether the current device supports the specified band. |
| [isConnected](arkts-connectivity-wifimanager-isconnected-f.md#isconnected-1) | Check whether the Wi-Fi connection has been set up. |
| [isFeatureSupported](arkts-connectivity-wifimanager-isfeaturesupported-f.md#isfeaturesupported-1) | Check whether the device supports a specified feature. |
| [isHotspotActive](arkts-connectivity-wifimanager-ishotspotactive-f.md#ishotspotactive-1) | Check whether Wi-Fi hotspot is active on a device. |
| [isMeteredHotspot](arkts-connectivity-wifimanager-ismeteredhotspot-f.md#ismeteredhotspot-1) | Whether the hotspot is metered hotspot or not. |
| [isWifiActive](arkts-connectivity-wifimanager-iswifiactive-f.md#iswifiactive-1) | Query the Wi-Fi status |
| [isWlanSupported](arkts-connectivity-wifimanager-iswlansupported-f.md#iswlansupported-1) | Query whether Wi-Fi is available |
| [off('wifiStateChange')](arkts-connectivity-wifimanager-off-f.md#offwifistatechange) | Unsubscribe Wi-Fi status change events. |
| [off('wifiConnectionChange')](arkts-connectivity-wifimanager-off-f.md#offwificonnectionchange) | Unsubscribe Wi-Fi connection change events. All callback functions will be deregistered If there is no specific callback parameter. |
| [off('wifiScanStateChange')](arkts-connectivity-wifimanager-off-f.md#offwifiscanstatechange) | Unsubscribe Wi-Fi scan status change events. All callback functions will be deregistered If there is no specific callback parameter. |
| [off('wifiRssiChange')](arkts-connectivity-wifimanager-off-f.md#offwifirssichange) | Unsubscribe Wi-Fi rssi change events. All callback functions will be deregistered If there is no specific callback parameter. |
| [off('hotspotStateChange')](arkts-connectivity-wifimanager-off-f.md#offhotspotstatechange) | Unsubscribe Wi-Fi hotspot state change events. All callback functions will be deregistered If there is no specific callback parameter. |
| [off('p2pStateChange')](arkts-connectivity-wifimanager-off-f.md#offp2pstatechange) | Unsubscribe P2P status change events. |
| [off('p2pConnectionChange')](arkts-connectivity-wifimanager-off-f.md#offp2pconnectionchange) | Unsubscribe P2P connection change events. |
| [off('p2pDeviceChange')](arkts-connectivity-wifimanager-off-f.md#offp2pdevicechange) | Unsubscribe P2P local device change events. |
| [off('p2pPeerDeviceChange')](arkts-connectivity-wifimanager-off-f.md#offp2ppeerdevicechange) | Unsubscribe P2P peer device change events. |
| [off('p2pPersistentGroupChange')](arkts-connectivity-wifimanager-off-f.md#offp2ppersistentgroupchange) | Unsubscribe P2P persistent group change events. |
| [off('p2pDiscoveryChange')](arkts-connectivity-wifimanager-off-f.md#offp2pdiscoverychange) | Unsubscribe P2P discovery events. |
| [offP2pServiceDiscovery](arkts-connectivity-wifimanager-offp2pservicediscovery-f.md#offp2pservicediscovery-1) | Unsubscribes from generic service response events. |
| [on('wifiStateChange')](arkts-connectivity-wifimanager-on-f.md#onwifistatechange) | Subscribe Wi-Fi status change events. |
| [on('wifiConnectionChange')](arkts-connectivity-wifimanager-on-f.md#onwificonnectionchange) | Subscribe Wi-Fi connection change events. |
| [on('wifiScanStateChange')](arkts-connectivity-wifimanager-on-f.md#onwifiscanstatechange) | Subscribe Wi-Fi scan status change events. |
| [on('wifiRssiChange')](arkts-connectivity-wifimanager-on-f.md#onwifirssichange) | Subscribe Wi-Fi rssi change events. |
| [on('hotspotStateChange')](arkts-connectivity-wifimanager-on-f.md#onhotspotstatechange) | Subscribe Wi-Fi hotspot state change events. |
| [on('p2pStateChange')](arkts-connectivity-wifimanager-on-f.md#onp2pstatechange) | Subscribe P2P status change events. |
| [on('p2pConnectionChange')](arkts-connectivity-wifimanager-on-f.md#onp2pconnectionchange) | Subscribe P2P connection change events. |
| [on('p2pDeviceChange')](arkts-connectivity-wifimanager-on-f.md#onp2pdevicechange) | Subscribe P2P local device change events. |
| [on('p2pPeerDeviceChange')](arkts-connectivity-wifimanager-on-f.md#onp2ppeerdevicechange) | Subscribe P2P peer device change events. |
| [on('p2pPersistentGroupChange')](arkts-connectivity-wifimanager-on-f.md#onp2ppersistentgroupchange) | Subscribe P2P persistent group change events. |
| [on('p2pDiscoveryChange')](arkts-connectivity-wifimanager-on-f.md#onp2pdiscoverychange) | Subscribe P2P discovery events. |
| [onP2pServiceDiscovery](arkts-connectivity-wifimanager-onp2pservicediscovery-f.md#onp2pservicediscovery-1) | Subscribes to generic service response events from peer devices. |
| [p2pCancelConnect](arkts-connectivity-wifimanager-p2pcancelconnect-f.md#p2pcancelconnect-1) | Stop an ongoing p2p connection that is being established. |
| [p2pConnect](arkts-connectivity-wifimanager-p2pconnect-f.md#p2pconnect-1) | Initiate a P2P connection to a device with the specified configuration. |
| [removeAllP2pServiceRequests](arkts-connectivity-wifimanager-removeallp2pservicerequests-f.md#removeallp2pservicerequests-1) | Removes all pending service discovery requests. |
| [removeCandidateConfig](arkts-connectivity-wifimanager-removecandidateconfig-f.md#removecandidateconfig-1) | Remove a specified candidate hotspot configuration, only the configuration which is added by ourself is allowed to be removed. The app must be in the foreground. |
| [removeCandidateConfig](arkts-connectivity-wifimanager-removecandidateconfig-f.md#removecandidateconfig-2) | Remove a specified candidate hotspot configuration, only the configuration which is added by ourself is allowed to be removed. The app must be in the foreground. |
| [removeDevice](arkts-connectivity-wifimanager-removedevice-f.md#removedevice-1) | Remove a Wi-Fi DeviceConfig with networkId. After a Wi-Fi DeviceConfig is removed, its configuration will be deleted from the list of Wi-Fi configurations. If the Wi-Fi DeviceConfig is being connected, the connection will be interrupted. The application can only delete Wi-Fi DeviceConfig it has created. |
| [removeGroup](arkts-connectivity-wifimanager-removegroup-f.md#removegroup-1) | Remove a P2P group. |
| [removeLocalP2pService](arkts-connectivity-wifimanager-removelocalp2pservice-f.md#removelocalp2pservice-1) | Removes a registered local service that was added through [addDnsSdLocalP2pService](arkts-connectivity-wifimanager-adddnssdlocalp2pservice-f.md) or [addUpnpLocalP2pService](arkts-connectivity-wifimanager-addupnplocalp2pservice-f.md). |
| [removeP2pServiceRequest](arkts-connectivity-wifimanager-removep2pservicerequest-f.md#removep2pservicerequest-1) | Removes a specified service discovery request. You can obtain the list of registered service discovery requests by calling [getP2pServiceRequest](arkts-connectivity-wifimanager-getp2pservicerequest-f.md). |
| [startDiscoverDevices](arkts-connectivity-wifimanager-startdiscoverdevices-f.md#startdiscoverdevices-1) | Start discover Wi-Fi P2P devices. |
| [startScan](arkts-connectivity-wifimanager-startscan-f.md#startscan-1) | Scan Wi-Fi hotspot. |
| [stopDiscoverDevices](arkts-connectivity-wifimanager-stopdiscoverdevices-f.md#stopdiscoverdevices-1) | Stop discover Wi-Fi P2P devices. |
| [getScanResults](arkts-connectivity-wifimanager-getscanresults-f.md#getscanresults-1) | Obtain the scanned sta list. |
| [getScanResults](arkts-connectivity-wifimanager-getscanresults-f.md#getscanresults-2) | Obtain the scanned sta list. |
| [getScanResultsSync](arkts-connectivity-wifimanager-getscanresultssync-f.md#getscanresultssync-1) | Obtain the scanned sta list. |
| [scan](arkts-connectivity-wifimanager-scan-f.md#scan-1) | Scan Wi-Fi hotspot. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addHotspotBlockList](arkts-connectivity-wifimanager-addhotspotblocklist-f-sys.md#addhotspotblocklist-1) | Adds a device to the list of blocked devices of the hotspot. Devices in the list cannot access the hotspot. |
| [allowAutoConnect](arkts-connectivity-wifimanager-allowautoconnect-f-sys.md#allowautoconnect-1) | Set whther to allow automatic connnect by networkId. The network can be associated with again if isAllowed is true, else not. |
| [connectToDevice](arkts-connectivity-wifimanager-connecttodevice-f-sys.md#connecttodevice-1) | Connects to the specified network. If the device is already connected to a hotspot, disconnect it from the hotspot first. |
| [deletePersistentGroup](arkts-connectivity-wifimanager-deletepersistentgroup-f-sys.md#deletepersistentgroup-1) | Deletes the permanent Wi-Fi group configuration of a specified network. This API is used to clear the saved Wi-Fi network configuration information so that the WLAN network cannot be automatically connected. |
| [delHotspotBlockList](arkts-connectivity-wifimanager-delhotspotblocklist-f-sys.md#delhotspotblocklist-1) | Deletes a device from the list of blocked devices of the hotspot. |
| [disableHotspot](arkts-connectivity-wifimanager-disablehotspot-f-sys.md#disablehotspot-1) | Disables this hotspot. This API is an asynchronous interface. The **hotspotStateChange** callback must be registered and listened for. |
| [disableNetwork](arkts-connectivity-wifimanager-disablenetwork-f-sys.md#disablenetwork-1) | Disables the network configuration. |
| [disableNetwork](arkts-connectivity-wifimanager-disablenetwork-f-sys.md#disablenetwork-2) | Disables the network connection, disconnects the connected network, and does not automatically reconnect to the network within the specified time range. |
| [enableHiLinkHandshake](arkts-connectivity-wifimanager-enablehilinkhandshake-f-sys.md#enablehilinkhandshake-1) | Enables or disables HiLink. |
| [enableHotspot](arkts-connectivity-wifimanager-enablehotspot-f-sys.md#enablehotspot-1) | Enables this hotspot. This API is an asynchronous interface. The **hotspotStateChange** callback must be registered and listened for. |
| [enableSemiWifi](arkts-connectivity-wifimanager-enablesemiwifi-f-sys.md#enablesemiwifi-1) | Enables Wi-Fi partially, that is, enables P2P and Huawei Magneto Link (HML) while disabling STA. You need to register a callback for the **wifiStateChange** event to return the operation result. |
| [factoryReset](arkts-connectivity-wifimanager-factoryreset-f-sys.md#factoryreset-1) |  |
| [get5GChannelList](arkts-connectivity-wifimanager-get5gchannellist-f-sys.md#get5gchannellist-1) | Obtains the list of 5 GHz channels supported by this device. |
| [getDeviceConfig](arkts-connectivity-wifimanager-getdeviceconfig-f-sys.md#getdeviceconfig-1) | Obtains the configuration of a single network based on the network ID. |
| [getDisconnectedReason](arkts-connectivity-wifimanager-getdisconnectedreason-f-sys.md#getdisconnectedreason-1) | Obtains the reason of the latest disconnection. |
| [getHotspotBlockList](arkts-connectivity-wifimanager-gethotspotblocklist-f-sys.md#gethotspotblocklist-1) | Obtains the list of devices that are in the blocklist of the current Wi-Fi hotspot. This API is valid when the device is in hotspot (AP) mode. |
| [getHotspotConfig](arkts-connectivity-wifimanager-gethotspotconfig-f-sys.md#gethotspotconfig-1) | Obtains the Wi-Fi hotspot configuration information, including the SSID, encryption mode, password, bandwidth, channel, and maximum number of connected STAs. |
| [getP2pGroups](arkts-connectivity-wifimanager-getp2pgroups-f-sys.md#getp2pgroups-1) | Obtains information about all P2P groups. This API uses a promise to return the result. |
| [getP2pGroups](arkts-connectivity-wifimanager-getp2pgroups-f-sys.md#getp2pgroups-2) | Obtains information about all P2P groups. This API uses an asynchronous callback to return the result. |
| [getScanAlwaysAllowed](arkts-connectivity-wifimanager-getscanalwaysallowed-f-sys.md#getscanalwaysallowed-1) | Obtains whether scan is always allowed. |
| [getSpecialWifiInfo](arkts-connectivity-wifimanager-getspecialwifiinfo-f-sys.md#getspecialwifiinfo-1) | Get special Wi-Fi info |
| [getStations](arkts-connectivity-wifimanager-getstations-f-sys.md#getstations-1) | Obtains the list of all devices that are currently connected to the hotspot of the device. |
| [getSupportedFeatures](arkts-connectivity-wifimanager-getsupportedfeatures-f-sys.md#getsupportedfeatures-1) | Obtains the features supported by this device. |
| [getWifiCapability](arkts-connectivity-wifimanager-getwificapability-f-sys.md#getwificapability-1) | Obtains the Wi-Fi capabilities. |
| [getWifiDetailState](arkts-connectivity-wifimanager-getwifidetailstate-f-sys.md#getwifidetailstate-1) | Obtains the Wi-Fi state. |
| [isHotspotDualBandSupported](arkts-connectivity-wifimanager-ishotspotdualbandsupported-f-sys.md#ishotspotdualbandsupported-1) | Checks whether the Wi-Fi hotspot function of the current device supports dual bands (both 2.4 GHz and 5 GHz). |
| [isOpenSoftApAllowed](arkts-connectivity-wifimanager-isopensoftapallowed-f-sys.md#isopensoftapallowed-1) | Checks whether Wi-Fi hotspot operations are allowed under certain circumstances. When Airplane mode is enabled, if the system does not support the coexistence of SoftAP and STA or signal bridging, the hotspot switch cannot be operated. |
| [isRandomMacDisabled](arkts-connectivity-wifimanager-israndommacdisabled-f-sys.md#israndommacdisabled-1) | Whether the random MAC address is disabled. |
| [off('streamChange')](arkts-connectivity-wifimanager-off-f-sys.md#offstreamchange) | Unsubscribes from Wi-Fi stream changes. |
| [off('deviceConfigChange')](arkts-connectivity-wifimanager-off-f-sys.md#offdeviceconfigchange) | Unsubscribes from Wi-Fi device configuration changes. |
| [off('hotspotStaJoin')](arkts-connectivity-wifimanager-off-f-sys.md#offhotspotstajoin) | Unsubscribes from the connection of an STA to a Wi-Fi hotspot. |
| [off('hotspotStaLeave')](arkts-connectivity-wifimanager-off-f-sys.md#offhotspotstaleave) | Unsubscribes from the disconnection of a STA from a Wi-Fi hotspot. |
| [on('streamChange')](arkts-connectivity-wifimanager-on-f-sys.md#onstreamchange) | Subscribes to Wi-Fi stream changes. When the service exits, call **off(type: 'streamChange', callback?: Callback<number>)** to unregister the callback registered. This API uses an asynchronous callback to return the result. |
| [on('deviceConfigChange')](arkts-connectivity-wifimanager-on-f-sys.md#ondeviceconfigchange) | Subscribes to Wi-Fi device configuration changes. When the service exits, call off(type: 'deviceConfigChange', callback?: Callback<number>) to unregister the callback registered. This API uses an asynchronous callback to return the result. |
| [on('hotspotStaJoin')](arkts-connectivity-wifimanager-on-f-sys.md#onhotspotstajoin) | Subscribes to the event of an STA joining a Wi-Fi hotspot. When the service exits, call **off(type: 'hotspotStaJoin', callback?: Callback<StationInfo>)** to unregister the callback registered. This API uses an asynchronous callback to return the result. |
| [on('hotspotStaLeave')](arkts-connectivity-wifimanager-on-f-sys.md#onhotspotstaleave) | Subscribes to the event of an STA leaving a Wi-Fi hotspot. When the service exits, call **off(type: 'hotspotStaLeave', callback?: Callback<StationInfo>)** to unregister the callback registered. This API uses an asynchronous callback to return the result. |
| [reassociate](arkts-connectivity-wifimanager-reassociate-f-sys.md#reassociate-1) | Re-associates with the network. |
| [reconnect](arkts-connectivity-wifimanager-reconnect-f-sys.md#reconnect-1) | Reconnects to the network. |
| [removeAllNetwork](arkts-connectivity-wifimanager-removeallnetwork-f-sys.md#removeallnetwork-1) | Removes the configuration of all networks. |
| [setDeviceName](arkts-connectivity-wifimanager-setdevicename-f-sys.md#setdevicename-1) | Sets the device name. |
| [setHotspotConfig](arkts-connectivity-wifimanager-sethotspotconfig-f-sys.md#sethotspotconfig-1) | Sets the Wi-Fi hotspot configuration information, including the SSID, encryption mode, password, bandwidth, channel, and maximum number of connected STAs. |
| [setScanAlwaysAllowed](arkts-connectivity-wifimanager-setscanalwaysallowed-f-sys.md#setscanalwaysallowed-1) | Sets whether scan is always allowed. |
| [setWifiCapability](arkts-connectivity-wifimanager-setwificapability-f-sys.md#setwificapability-1) | Sets the Wi-Fi capability. |
| [startPortalCertification](arkts-connectivity-wifimanager-startportalcertification-f-sys.md#startportalcertification-1) | Starts the Portal authentication process, which is used to process public Wi-Fi networks (such as networks in hotels, airports, and cafes) that require web page authentication. |
| [startWifiDetection](arkts-connectivity-wifimanager-startwifidetection-f-sys.md#startwifidetection-1) | Starts Wi-Fi network detections. |
| [updateNetwork](arkts-connectivity-wifimanager-updatenetwork-f-sys.md#updatenetwork-1) | Updates network configuration. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [ConnectSettings](arkts-connectivity-wifimanager-connectsettings-i.md) | Describes the settings for Wi-Fi connection. |
| [IpInfo](arkts-connectivity-wifimanager-ipinfo-i.md) | Wi-Fi IP information. |
| [Ipv6Info](arkts-connectivity-wifimanager-ipv6info-i.md) | Wi-Fi IPv6 information. |
| [P2pDnsSdInfo](arkts-connectivity-wifimanager-p2pdnssdinfo-i.md) | Represents the DNS-SD service response information received from a peer device. |
| [P2pDnsSdTxtInfo](arkts-connectivity-wifimanager-p2pdnssdtxtinfo-i.md) | Represents the DNS-SD TXT record information received from a peer device. |
| [P2pGenericInfo](arkts-connectivity-wifimanager-p2pgenericinfo-i.md) | Represents the generic service response information received from a peer device. |
| [P2pUpnpInfo](arkts-connectivity-wifimanager-p2pupnpinfo-i.md) | Represents the UPnP service response information received from a peer device. |
| [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i.md) | Represents the Wi-Fi configuration information. |
| [WifiEapConfig](arkts-connectivity-wifimanager-wifieapconfig-i.md) | Wi-Fi EAP config. |
| [WifiInfoElem](arkts-connectivity-wifimanager-wifiinfoelem-i.md) | Wi-Fi information elements. |
| [WifiLinkedInfo](arkts-connectivity-wifimanager-wifilinkedinfo-i.md) | Wi-Fi connection information. |
| [WifiP2PConfig](arkts-connectivity-wifimanager-wifip2pconfig-i.md) | P2P config. |
| [WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md) | P2P device information. |
| [WifiP2pGroupInfo](arkts-connectivity-wifimanager-wifip2pgroupinfo-i.md) | P2P group information. |
| [WifiP2pLinkedInfo](arkts-connectivity-wifimanager-wifip2plinkedinfo-i.md) | P2P linked information. |
| [WifiP2pServiceInfo](arkts-connectivity-wifimanager-wifip2pserviceinfo-i.md) | Represents the P2P service information. |
| [WifiP2pServiceRequest](arkts-connectivity-wifimanager-wifip2pservicerequest-i.md) | Represents the P2P service discovery request (TLV query). |
| [WifiScanInfo](arkts-connectivity-wifimanager-wifiscaninfo-i.md) | Provides information about Wi-Fi scanning. |
| [WifiWapiConfig](arkts-connectivity-wifimanager-wifiwapiconfig-i.md) | Wi-Fi WAPI config. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [HotspotConfig](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md) | Represents the hotspot configuration. |
| [IpConfig](arkts-connectivity-wifimanager-ipconfig-i-sys.md) | Represents IP configuration information. |
| [Ipv6Config](arkts-connectivity-wifimanager-ipv6config-i-sys.md) | Wi-Fi Ipv6 configuration information. |
| [SpecialWifiInfo](arkts-connectivity-wifimanager-specialwifiinfo-i-sys.md) | Special Wi-Fi info |
| [StationInfo](arkts-connectivity-wifimanager-stationinfo-i-sys.md) | Represents the station information. This information contains details about the device that is connected to Wi-Fi. |
| [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i-sys.md) | Represents the Wi-Fi configuration information. |
| [WifiLinkedInfo](arkts-connectivity-wifimanager-wifilinkedinfo-i-sys.md) | Wi-Fi connection information. |
| [WifiProxyConfig](arkts-connectivity-wifimanager-wifiproxyconfig-i-sys.md) | Represents the Wi-Fi proxy configuration. |
| [WifiScanInfo](arkts-connectivity-wifimanager-wifiscaninfo-i-sys.md) | Provides information about Wi-Fi scanning. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [P2pServiceDiscoveryInfo](arkts-connectivity-wifimanager-p2pservicediscoveryinfo-t.md) | Represents the P2P service discovery response information received from a peer device. The specific type is determined by the service protocol type of the response. |

### Enums

| Name | Description |
| --- | --- |
| [ConnState](arkts-connectivity-wifimanager-connstate-e.md) | The state of Wi-Fi connection enumeration. |
| [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md) | Wi-Fi device address( mac / bssid ) type. |
| [EapMethod](arkts-connectivity-wifimanager-eapmethod-e.md) | Wi-Fi EAP method. |
| [GroupOwnerBand](arkts-connectivity-wifimanager-groupownerband-e.md) | P2P group owner band. |
| [P2pConnectState](arkts-connectivity-wifimanager-p2pconnectstate-e.md) | P2P connection status. |
| [P2pDeviceStatus](arkts-connectivity-wifimanager-p2pdevicestatus-e.md) | P2P device status. |
| [P2pServiceProtocolType](arkts-connectivity-wifimanager-p2pserviceprotocoltype-e.md) | Enumerates the P2P service protocol types. |
| [Phase2Method](arkts-connectivity-wifimanager-phase2method-e.md) | Wi-Fi phase 2 method. |
| [WapiPskType](arkts-connectivity-wifimanager-wapipsktype-e.md) | Describes the WAPI pre-shared key Type. |
| [WifiBandType](arkts-connectivity-wifimanager-wifibandtype-e.md) | Wi-Fi band type. |
| [WifiCapability](arkts-connectivity-wifimanager-wificapability-e.md) | Describes the capabilities supported by the Wi-Fi module. |
| [WifiCategory](arkts-connectivity-wifimanager-wificategory-e.md) | Wi-Fi Category. |
| [WifiChannelWidth](arkts-connectivity-wifimanager-wifichannelwidth-e.md) | Describes the wifi channel width. |
| [WifiLinkType](arkts-connectivity-wifimanager-wifilinktype-e.md) | Wi-Fi link type. |
| [WifiSecurityType](arkts-connectivity-wifimanager-wifisecuritytype-e.md) | Describes the wifi security type. |
| [WifiStandard](arkts-connectivity-wifimanager-wifistandard-e.md) | Wi-Fi standard. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [DisconnectedReason](arkts-connectivity-wifimanager-disconnectedreason-e-sys.md) | Enumerates the reasons why the Wi-Fi connection is disconnected. This API is used to diagnose network connection problems and optimize connection policies. |
| [IpType](arkts-connectivity-wifimanager-iptype-e-sys.md) | Enumerates the IP address types. |
| [ProxyMethod](arkts-connectivity-wifimanager-proxymethod-e-sys.md) | Enumerates the Wi-Fi proxy methods. |
| [SuppState](arkts-connectivity-wifimanager-suppstate-e-sys.md) | Enumerates the supplicant states. |
| [WifiDetailState](arkts-connectivity-wifimanager-wifidetailstate-e-sys.md) | Enumerates Wi-Fi states. |
<!--DelEnd-->
