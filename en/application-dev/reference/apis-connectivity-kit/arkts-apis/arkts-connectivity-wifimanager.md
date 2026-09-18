# @ohos.wifiManager

Provides methods to operate or manage Wi-Fi. @namespace wifiManager

**Since:** 12

**System capability:** SystemCapability.Communication.WiFi.STA

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addCandidateConfig](arkts-connectivity-wifimanager-addcandidateconfig-f.md) | Add a specified candidate hotspot configuration and returns the networkId. This method adds one configuration at a time. After this configuration is added, your device will determine whether to connect to the hotspot. The app must be in the foreground. |
| [addCandidateConfig](arkts-connectivity-wifimanager-addcandidateconfig-f.md) | Add a specified candidate hotspot configuration and returns the networkId. This method adds one configuration at a time. After this configuration is added, your device will determine whether to connect to the hotspot. The app must be in the foreground. |
| [addDeviceConfig](arkts-connectivity-wifimanager-adddeviceconfig-f.md) | Add Wi-Fi connection configuration to the device. The configuration will be updated when the configuration is added. |
| [addDeviceConfig](arkts-connectivity-wifimanager-adddeviceconfig-f.md) | Add Wi-Fi connection configuration to the device. The configuration will be updated when the configuration is added. |
| [addDnsSdLocalP2pService](arkts-connectivity-wifimanager-adddnssdlocalp2pservice-f.md) | Add a Bonjour (DNS-SD) local P2P service description and register it. |
| [addUpnpLocalP2pService](arkts-connectivity-wifimanager-addupnplocalp2pservice-f.md) | Add a UPnP local P2P service description and register it. |
| [connectToCandidateConfig](arkts-connectivity-wifimanager-connecttocandidateconfig-f.md) | Connect to a specified candidate hotspot by networkId, only the configuration which is added by ourself is allowed to be connected. This method connect to a configuration at a time. The app must be in the foreground. |
| [connectToCandidateConfig](arkts-connectivity-wifimanager-connecttocandidateconfig-f.md) | Connect to the specified candidate hotspot using connect settings. |
| [connectToCandidateConfigWithUserAction](arkts-connectivity-wifimanager-connecttocandidateconfigwithuseraction-f.md) | Connect to a specified candidate hotspot by networkId, and wait for user respond result. Only the configuration which is added by ourself is allowed to be connected. This method connect to a configuration at a time. The app must be in the foreground. |
| [connectToNetwork](arkts-connectivity-wifimanager-connecttonetwork-f.md) | Connect to Wi-Fi hotspot by networkId. |
| [createGroup](arkts-connectivity-wifimanager-creategroup-f.md) | Create a P2P group. |
| [disableWifi](arkts-connectivity-wifimanager-disablewifi-f.md) | Disable Wi-Fi. |
| [disconnect](arkts-connectivity-wifimanager-disconnect-f.md) | Disconnect connection between sta and Wi-Fi hotspot. |
| [enableWifi](arkts-connectivity-wifimanager-enablewifi-f.md) | Enable Wi-Fi. |
| [getCandidateConfigs](arkts-connectivity-wifimanager-getcandidateconfigs-f.md) | Obtain the list of all existed candidate Wi-Fi configurations which added by ourself. You can obtain only the Wi-Fi configurations you created on your own application. |
| [getCountryCode](arkts-connectivity-wifimanager-getcountrycode-f.md) | Obtain the country code of the device. |
| [getCurrentGroup](arkts-connectivity-wifimanager-getcurrentgroup-f.md) | Obtain information about the current p2p group. |
| [getCurrentGroup](arkts-connectivity-wifimanager-getcurrentgroup-f.md) | Obtain information about the current p2p group. |
| [getDeviceConfigs](arkts-connectivity-wifimanager-getdeviceconfigs-f.md) | Obtain the list of all existed Wi-Fi configurations. |
| [getDeviceMacAddress](arkts-connectivity-wifimanager-getdevicemacaddress-f.md) | Obtain the MAC address of a Wi-Fi device. Wi-Fi must be enabled. The MAC address is unique and cannot be changed. |
| [getIpInfo](arkts-connectivity-wifimanager-getipinfo-f.md) | Obtain the IPv4 information of the Wi-Fi connection. The IP information includes the host IP address, gateway address, and DNS information. |
| [getIpv6Info](arkts-connectivity-wifimanager-getipv6info-f.md) | Obtain the IPv6 information of the Wi-Fi connection. The IPv6 information includes the host IP address, gateway address, and DNS information. |
| [getLinkedInfo](arkts-connectivity-wifimanager-getlinkedinfo-f.md) | Obtain connection information about the Wi-Fi connection. If does't have the permission of ohos.permission.GET_WIFI_PEERS_MAC, return random bssid. |
| [getLinkedInfo](arkts-connectivity-wifimanager-getlinkedinfo-f.md) | Obtain connection information about the Wi-Fi connection. |
| [getLinkedInfoSync](arkts-connectivity-wifimanager-getlinkedinfosync-f.md) | Obtain connection information about the Wi-Fi connection.this apireturns the result syncchronously. If does't have the permission of ohos.permission.GET_WIFI_PEERS_MAC, return random bssid. |
| [getLocalP2pServices](arkts-connectivity-wifimanager-getlocalp2pservices-f.md) | Queries the local P2P services. This API uses a promise to return the result. |
| [getMultiLinkedInfo](arkts-connectivity-wifimanager-getmultilinkedinfo-f.md) | Obtain multiple Wi-Fi connection information when Wi-Fi linked in MLO(Muti-Link Operation) state. If does't have the permission of ohos.permission.GET_WIFI_PEERS_MAC, return random bssid. |
| [getP2pLinkedInfo](arkts-connectivity-wifimanager-getp2plinkedinfo-f.md) | Obtain information about the P2P connection. |
| [getP2pLinkedInfo](arkts-connectivity-wifimanager-getp2plinkedinfo-f.md) | Obtain information about the P2P connection. |
| [getP2pLocalDevice](arkts-connectivity-wifimanager-getp2plocaldevice-f.md) | Obtain the information about own device information. DeviceAddress in the returned WifiP2pDevice will be set "00:00:00:00:00:00", if ohos.permission.GET_WIFI_LOCAL_MAC is not granted. |
| [getP2pLocalDevice](arkts-connectivity-wifimanager-getp2plocaldevice-f.md) | Obtain the information about own device information. DeviceAddress in the returned WifiP2pDevice will be set "00:00:00:00:00:00", if ohos.permission.GET_WIFI_LOCAL_MAC is not granted. |
| [getP2pPeerDevices](arkts-connectivity-wifimanager-getp2ppeerdevices-f.md) | Obtain the information about the found devices. |
| [getP2pPeerDevices](arkts-connectivity-wifimanager-getp2ppeerdevices-f.md) | Obtain the information about the found devices. |
| [getScanInfoList](arkts-connectivity-wifimanager-getscaninfolist-f.md) | Obtain the scanned station list. If does't have the permission of ohos.permission.GET_WIFI_PEERS_MAC, return random bssid. |
| [getScanResults](arkts-connectivity-wifimanager-getscanresults-f.md) | Obtain the scanned sta list. |
| [getScanResults](arkts-connectivity-wifimanager-getscanresults-f.md) | Obtain the scanned sta list. |
| [getScanResultsSync](arkts-connectivity-wifimanager-getscanresultssync-f.md) | Obtain the scanned sta list. |
| [getSignalLevel](arkts-connectivity-wifimanager-getsignallevel-f.md) | Calculate the Wi-Fi signal level based on the Wi-Fi RSSI and frequency band. |
| [isBandTypeSupported](arkts-connectivity-wifimanager-isbandtypesupported-f.md) | Check whether the current device supports the specified band. |
| [isConnected](arkts-connectivity-wifimanager-isconnected-f.md) | Check whether the Wi-Fi connection has been set up. |
| [isFeatureSupported](arkts-connectivity-wifimanager-isfeaturesupported-f.md) | Check whether the device supports a specified feature. |
| [isMeteredHotspot](arkts-connectivity-wifimanager-ismeteredhotspot-f.md) | Whether the hotspot is metered hotspot or not. |
| [isWifiActive](arkts-connectivity-wifimanager-iswifiactive-f.md) | Query the Wi-Fi status |
| [isWlanSupported](arkts-connectivity-wifimanager-iswlansupported-f.md) | Query whether Wi-Fi is available |
| [off](arkts-connectivity-wifimanager-off-f.md#offwifistatechange) | Unsubscribe Wi-Fi status change events. |
| [off](arkts-connectivity-wifimanager-off-f.md#offwificonnectionchange) | Unsubscribe Wi-Fi connection change events. All callback functions will be deregistered If there is no specific callback parameter. |
| [off](arkts-connectivity-wifimanager-off-f.md#offwifiscanstatechange) | Unsubscribe Wi-Fi scan status change events. All callback functions will be deregistered If there is no specific callback parameter. |
| [off](arkts-connectivity-wifimanager-off-f.md#offwifirssichange) | Unsubscribe Wi-Fi rssi change events. All callback functions will be deregistered If there is no specific callback parameter. |
| [off](arkts-connectivity-wifimanager-off-f.md#offhotspotstatechange) | Unsubscribe Wi-Fi hotspot state change events. All callback functions will be deregistered If there is no specific callback parameter. |
| [off](arkts-connectivity-wifimanager-off-f.md#offp2pstatechange) | Unsubscribe P2P status change events. |
| [off](arkts-connectivity-wifimanager-off-f.md#offp2pconnectionchange) | Unsubscribe P2P connection change events. |
| [off](arkts-connectivity-wifimanager-off-f.md#offp2pdevicechange) | Unsubscribe P2P local device change events. |
| [off](arkts-connectivity-wifimanager-off-f.md#offp2ppeerdevicechange) | Unsubscribe P2P peer device change events. |
| [off](arkts-connectivity-wifimanager-off-f.md#offp2ppersistentgroupchange) | Unsubscribe P2P persistent group change events. |
| [off](arkts-connectivity-wifimanager-off-f.md#offp2pdiscoverychange) | Unsubscribe P2P discovery events. |
| [on](arkts-connectivity-wifimanager-on-f.md#onwifistatechange) | Subscribe Wi-Fi status change events. |
| [on](arkts-connectivity-wifimanager-on-f.md#onwificonnectionchange) | Subscribe Wi-Fi connection change events. |
| [on](arkts-connectivity-wifimanager-on-f.md#onwifiscanstatechange) | Subscribe Wi-Fi scan status change events. |
| [on](arkts-connectivity-wifimanager-on-f.md#onwifirssichange) | Subscribe Wi-Fi rssi change events. |
| [on](arkts-connectivity-wifimanager-on-f.md#onhotspotstatechange) | Subscribe Wi-Fi hotspot state change events. |
| [on](arkts-connectivity-wifimanager-on-f.md#onp2pstatechange) | Subscribe P2P status change events. |
| [on](arkts-connectivity-wifimanager-on-f.md#onp2pconnectionchange) | Subscribe P2P connection change events. |
| [on](arkts-connectivity-wifimanager-on-f.md#onp2pdevicechange) | Subscribe P2P local device change events. |
| [on](arkts-connectivity-wifimanager-on-f.md#onp2ppeerdevicechange) | Subscribe P2P peer device change events. |
| [on](arkts-connectivity-wifimanager-on-f.md#onp2ppersistentgroupchange) | Subscribe P2P persistent group change events. |
| [on](arkts-connectivity-wifimanager-on-f.md#onp2pdiscoverychange) | Subscribe P2P discovery events. |
| [p2pCancelConnect](arkts-connectivity-wifimanager-p2pcancelconnect-f.md) | Stop an ongoing p2p connection that is being established. |
| [p2pConnect](arkts-connectivity-wifimanager-p2pconnect-f.md) | Initiate a P2P connection to a device with the specified configuration. |
| [removeCandidateConfig](arkts-connectivity-wifimanager-removecandidateconfig-f.md) | Remove a specified candidate hotspot configuration, only the configuration which is added by ourself is allowed to be removed. The app must be in the foreground. |
| [removeCandidateConfig](arkts-connectivity-wifimanager-removecandidateconfig-f.md) | Remove a specified candidate hotspot configuration, only the configuration which is added by ourself is allowed to be removed. The app must be in the foreground. |
| [removeDevice](arkts-connectivity-wifimanager-removedevice-f.md) | Remove a Wi-Fi DeviceConfig with networkId. After a Wi-Fi DeviceConfig is removed, its configuration will be deleted from the list of Wi-Fi configurations. If the Wi-Fi DeviceConfig is being connected, the connection will be interrupted. The application can only delete Wi-Fi DeviceConfig it has created. |
| [removeGroup](arkts-connectivity-wifimanager-removegroup-f.md) | Remove a P2P group. |
| [removeLocalP2pService](arkts-connectivity-wifimanager-removelocalp2pservice-f.md) | Remove a registered local P2P service added with the [addDnsSdLocalP2pService](arkts-connectivity-wifimanager-adddnssdlocalp2pservice-f.md) or [addUpnpLocalP2pService](arkts-connectivity-wifimanager-addupnplocalp2pservice-f.md). |
| [scan](arkts-connectivity-wifimanager-scan-f.md) | Scan Wi-Fi hotspot. |
| [startDiscoverDevices](arkts-connectivity-wifimanager-startdiscoverdevices-f.md) | Start discover Wi-Fi P2P devices. |
| [startScan](arkts-connectivity-wifimanager-startscan-f.md) | Scan Wi-Fi hotspot. |
| [stopDiscoverDevices](arkts-connectivity-wifimanager-stopdiscoverdevices-f.md) | Stop discover Wi-Fi P2P devices. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addHotspotBlockList](arkts-connectivity-wifimanager-addhotspotblocklist-f-sys.md) | Add the station into the block list, the station can NOT access the hotspot. |
| [allowAutoConnect](arkts-connectivity-wifimanager-allowautoconnect-f-sys.md) | Set whther to allow automatic connnect by networkId. The network can be associated with again if isAllowed is true, else not. |
| [connectToDevice](arkts-connectivity-wifimanager-connecttodevice-f-sys.md) | Connect to Wi-Fi hotspot by WifiDeviceConfig. |
| [deletePersistentGroup](arkts-connectivity-wifimanager-deletepersistentgroup-f-sys.md) | Delete the persistent P2P group with the specified network ID. |
| [delHotspotBlockList](arkts-connectivity-wifimanager-delhotspotblocklist-f-sys.md) | Delete the station from block list, the station can access the hotspot. |
| [disableHotspot](arkts-connectivity-wifimanager-disablehotspot-f-sys.md) | Disable Wi-Fi hotspot function. This method is asynchronous. If Wi-Fi is enabled after the Wi-Fi hotspot is disabled, Wi-Fi may be re-enabled. |
| [disableNetwork](arkts-connectivity-wifimanager-disablenetwork-f-sys.md) | Disable the specified DeviceConfig by networkId. The disabled DeviceConfig will not be associated with again. |
| [disableNetwork](arkts-connectivity-wifimanager-disablenetwork-f-sys.md) | Disable the specified DeviceConfig by networkId for a period of time. The disabled DeviceConfig will not be associated with again. |
| [enableHiLinkHandshake](arkts-connectivity-wifimanager-enablehilinkhandshake-f-sys.md) | Enable hiLink handshake. |
| [enableHotspot](arkts-connectivity-wifimanager-enablehotspot-f-sys.md) | Enable Wi-Fi hotspot function. This method is asynchronous. After the Wi-Fi hotspot is enabled, Wi-Fi may be disabled. |
| [enableSemiWifi](arkts-connectivity-wifimanager-enablesemiwifi-f-sys.md) | Enable semi - Wifi. |
| [factoryReset](arkts-connectivity-wifimanager-factoryreset-f-sys.md) | Reset all saved device configure. |
| [get5GChannelList](arkts-connectivity-wifimanager-get5gchannellist-f-sys.md) | Obtain the supported 5G channel list of the device. |
| [getDeviceConfig](arkts-connectivity-wifimanager-getdeviceconfig-f-sys.md) | Obtain the single Wi-Fi configuration with Network ID. |
| [getDisconnectedReason](arkts-connectivity-wifimanager-getdisconnectedreason-f-sys.md) | Obtain the latest disconnected reason. |
| [getHotspotBlockList](arkts-connectivity-wifimanager-gethotspotblocklist-f-sys.md) | Get all the stations in the block list. If does't have the permission of ohos.permission.GET_WIFI_PEERS_MAC, return random bssid. |
| [getHotspotConfig](arkts-connectivity-wifimanager-gethotspotconfig-f-sys.md) | Obtain the Wi-Fi hotspot configuration. |
| [getP2pGroups](arkts-connectivity-wifimanager-getp2pgroups-f-sys.md) | Obtain information about the groups. |
| [getP2pGroups](arkts-connectivity-wifimanager-getp2pgroups-f-sys.md) | Obtain information about the groups. |
| [getScanAlwaysAllowed](arkts-connectivity-wifimanager-getscanalwaysallowed-f-sys.md) | Get scan always allowed flag. |
| [getStations](arkts-connectivity-wifimanager-getstations-f-sys.md) | Obtain the list of stations that are connected to the Wi-Fi hotspot. This method can only be used on a device that serves as a Wi-Fi hotspot. |
| [getSupportedFeatures](arkts-connectivity-wifimanager-getsupportedfeatures-f-sys.md) | Obtain the features supported by the device. To check whether this device supports a specified feature. |
| [getWifiCapability](arkts-connectivity-wifimanager-getwificapability-f-sys.md) | Get Wi-Fi capability |
| [getWifiDetailState](arkts-connectivity-wifimanager-getwifidetailstate-f-sys.md) | Obtains information about a Wi-Fi detail state. |
| [isHotspotActive](arkts-connectivity-wifimanager-ishotspotactive-f-sys.md) | Check whether Wi-Fi hotspot is active on a device. |
| [isHotspotDualBandSupported](arkts-connectivity-wifimanager-ishotspotdualbandsupported-f-sys.md) | Check whether a device serving as a Wi-Fi hotspot supports both the 2.4 GHz and 5 GHz Wi-Fi. |
| [isOpenSoftApAllowed](arkts-connectivity-wifimanager-isopensoftapallowed-f-sys.md) | Check whether Wi-Fi hotspot is can be operated under some situation. When the airplane mode is turned on and does not support the coexistence of softap and sta, nor does it support signal bridge, the hotspot switch cannot be operated. |
| [isRandomMacDisabled](arkts-connectivity-wifimanager-israndommacdisabled-f-sys.md) | is random mac disabled |
| [off](arkts-connectivity-wifimanager-off-f-sys.md#offstreamchange) | Unsubscribe Wi-Fi stream change events. All callback functions will be deregistered If there is no specific callback parameter. |
| [off](arkts-connectivity-wifimanager-off-f-sys.md#offdeviceconfigchange) | Subscribe Wi-Fi device config change events. |
| [off](arkts-connectivity-wifimanager-off-f-sys.md#offhotspotstajoin) | Unsubscribe Wi-Fi hotspot sta join events. All callback functions will be deregistered If there is no specific callback parameter. |
| [off](arkts-connectivity-wifimanager-off-f-sys.md#offhotspotstaleave) | Unsubscribe Wi-Fi hotspot sta leave events. |
| [on](arkts-connectivity-wifimanager-on-f-sys.md#onstreamchange) | Subscribe Wi-Fi stream change events. |
| [on](arkts-connectivity-wifimanager-on-f-sys.md#ondeviceconfigchange) | Subscribe Wi-Fi device config change events. |
| [on](arkts-connectivity-wifimanager-on-f-sys.md#onhotspotstajoin) | Subscribe Wi-Fi hotspot sta join events. |
| [on](arkts-connectivity-wifimanager-on-f-sys.md#onhotspotstaleave) | Subscribe Wi-Fi hotspot sta leave events. |
| [reassociate](arkts-connectivity-wifimanager-reassociate-f-sys.md) | Re-associate to current network. |
| [reconnect](arkts-connectivity-wifimanager-reconnect-f-sys.md) | Re-connect to current network. |
| [removeAllNetwork](arkts-connectivity-wifimanager-removeallnetwork-f-sys.md) | Remove all the saved Wi-Fi configurations. |
| [setDeviceName](arkts-connectivity-wifimanager-setdevicename-f-sys.md) | Set the name of the Wi-Fi P2P device. |
| [setHotspotConfig](arkts-connectivity-wifimanager-sethotspotconfig-f-sys.md) | Set the hotspot configuration for the device. |
| [setScanAlwaysAllowed](arkts-connectivity-wifimanager-setscanalwaysallowed-f-sys.md) | User can trigger scan even Wi-Fi is disabled. |
| [setWifiCapability](arkts-connectivity-wifimanager-setwificapability-f-sys.md) | Set Wi-Fi capability |
| [startPortalCertification](arkts-connectivity-wifimanager-startportalcertification-f-sys.md) | Start Portal certification. |
| [startWifiDetection](arkts-connectivity-wifimanager-startwifidetection-f-sys.md) | Start Wi-Fi network detection |
| [updateNetwork](arkts-connectivity-wifimanager-updatenetwork-f-sys.md) | Update the specified Wi-Fi configuration. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [ConnectSettings](arkts-connectivity-wifimanager-connectsettings-i.md) | Describes the settings for Wi-Fi connection. |
| [IpInfo](arkts-connectivity-wifimanager-ipinfo-i.md) | Wi-Fi IP information. @typedef IpInfo |
| [Ipv6Info](arkts-connectivity-wifimanager-ipv6info-i.md) | Wi-Fi IPv6 information. @typedef Ipv6Info |
| [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i.md) | Wi-Fi device configuration information. @typedef WifiDeviceConfig |
| [WifiEapConfig](arkts-connectivity-wifimanager-wifieapconfig-i.md) | Wi-Fi EAP config. @typedef WifiEapConfig |
| [WifiInfoElem](arkts-connectivity-wifimanager-wifiinfoelem-i.md) | Wi-Fi information elements. @typedef WifiInfoElem |
| [WifiLinkedInfo](arkts-connectivity-wifimanager-wifilinkedinfo-i.md) | Wi-Fi connection information. @typedef WifiLinkedInfo |
| [WifiP2PConfig](arkts-connectivity-wifimanager-wifip2pconfig-i.md) | P2P config. |
| [WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md) | P2P device information. |
| [WifiP2pGroupInfo](arkts-connectivity-wifimanager-wifip2pgroupinfo-i.md) | P2P group information. |
| [WifiP2pLinkedInfo](arkts-connectivity-wifimanager-wifip2plinkedinfo-i.md) | P2P linked information. |
| [WifiP2pServiceInfo](arkts-connectivity-wifimanager-wifip2pserviceinfo-i.md) | Represents the P2P service information. |
| [WifiScanInfo](arkts-connectivity-wifimanager-wifiscaninfo-i.md) | Describes the scanned Wi-Fi information. @typedef WifiScanInfo |
| [WifiWapiConfig](arkts-connectivity-wifimanager-wifiwapiconfig-i.md) | Wi-Fi WAPI config. @typedef WifiWapiConfig |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [HotspotConfig](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md) | Wi-Fi hotspot configuration information. @typedef HotspotConfig |
| [IpConfig](arkts-connectivity-wifimanager-ipconfig-i-sys.md) | Wi-Fi IP configuration information. @typedef IpConfig |
| [Ipv6Config](arkts-connectivity-wifimanager-ipv6config-i-sys.md) | Wi-Fi Ipv6 configuration information. @typedef Ipv6Config |
| [StationInfo](arkts-connectivity-wifimanager-stationinfo-i-sys.md) | Wi-Fi station information. @typedef StationInfo |
| [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i-sys.md) | Wi-Fi device configuration information. @typedef WifiDeviceConfig |
| [WifiLinkedInfo](arkts-connectivity-wifimanager-wifilinkedinfo-i-sys.md) | Wi-Fi connection information. @typedef WifiLinkedInfo |
| [WifiProxyConfig](arkts-connectivity-wifimanager-wifiproxyconfig-i-sys.md) | Wi-Fi Proxy config. @typedef WifiProxyConfig |
| [WifiScanInfo](arkts-connectivity-wifimanager-wifiscaninfo-i-sys.md) | Describes the scanned Wi-Fi information. @typedef WifiScanInfo |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ConnState](arkts-connectivity-wifimanager-connstate-e.md) | The state of Wi-Fi connection enumeration. |
| [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md) | Wi-Fi device address( mac / bssid ) type. @enum { int } |
| [EapMethod](arkts-connectivity-wifimanager-eapmethod-e.md) | Wi-Fi EAP method. @enum { int } |
| [GroupOwnerBand](arkts-connectivity-wifimanager-groupownerband-e.md) | P2P group owner band. |
| [P2pConnectState](arkts-connectivity-wifimanager-p2pconnectstate-e.md) | P2P connection status. |
| [P2pDeviceStatus](arkts-connectivity-wifimanager-p2pdevicestatus-e.md) | P2P device status. |
| [P2pServiceProtocolType](arkts-connectivity-wifimanager-p2pserviceprotocoltype-e.md) | Enumerates the P2P service protocol types. |
| [Phase2Method](arkts-connectivity-wifimanager-phase2method-e.md) | Wi-Fi phase 2 method. @enum { int } |
| [WapiPskType](arkts-connectivity-wifimanager-wapipsktype-e.md) | Describes the WAPI pre-shared key Type. @enum { int } |
| [WifiBandType](arkts-connectivity-wifimanager-wifibandtype-e.md) | Wi-Fi band type. @enum { int } |
| [WifiCapability](arkts-connectivity-wifimanager-wificapability-e.md) | Wi-Fi Capability |
| [WifiCategory](arkts-connectivity-wifimanager-wificategory-e.md) | Wi-Fi Category. @enum { int } |
| [WifiChannelWidth](arkts-connectivity-wifimanager-wifichannelwidth-e.md) | Describes the wifi channel width. @enum { int } |
| [WifiLinkType](arkts-connectivity-wifimanager-wifilinktype-e.md) | Wi-Fi link type. @enum { int } |
| [WifiSecurityType](arkts-connectivity-wifimanager-wifisecuritytype-e.md) | Describes the wifi security type. @enum { int } |
| [WifiStandard](arkts-connectivity-wifimanager-wifistandard-e.md) | Wi-Fi standard. @enum { int } |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [DisconnectedReason](arkts-connectivity-wifimanager-disconnectedreason-e-sys.md) | Wi-Fi disconnected reason. @enum { int } |
| [IpType](arkts-connectivity-wifimanager-iptype-e-sys.md) | Wi-Fi IP type enumeration. |
| [ProxyMethod](arkts-connectivity-wifimanager-proxymethod-e-sys.md) | Wi-Fi Proxy method. @enum { int } |
| [SuppState](arkts-connectivity-wifimanager-suppstate-e-sys.md) | The state of the supplicant enumeration. |
| [WifiDetailState](arkts-connectivity-wifimanager-wifidetailstate-e-sys.md) | Wi-Fi detail state. @enum { int } WifiDetailState |
<!--DelEnd-->
