# @ohos.wifiManager

提供操作或管理WLAN的方法。

**起始版本：** 23

<!--Device-unnamed-declare namespace wifiManager--><!--Device-unnamed-declare namespace wifiManager-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addCandidateConfig](arkts-connectivity-wifimanager-addcandidateconfig-f.md) | 添加指定的候选热点配置，并返回networkId。 此方法一次添加一个配置。添加此配置后，设备将决定是否连接到该热点。 应用必须在前台运行。 |
| [addCandidateConfig](arkts-connectivity-wifimanager-addcandidateconfig-f.md) | 添加指定的候选热点配置，并返回networkId。 此方法一次添加一个配置。添加此配置后，设备将决定是否连接到该热点。 应用必须在前台运行。 |
| [addDeviceConfig](arkts-connectivity-wifimanager-adddeviceconfig-f.md) | 添加WLAN连接配置到设备。添加配置时将更新配置。 |
| [addDeviceConfig](arkts-connectivity-wifimanager-adddeviceconfig-f.md) | 添加WLAN连接配置到设备。添加配置时将更新配置。 |
| [connectToCandidateConfig](arkts-connectivity-wifimanager-connecttocandidateconfig-f.md) | 通过networkId连接到指定的候选热点，只允许连接自己添加的配置。此方法一次连接一个配置。 应用必须在前台运行。 |
| [connectToCandidateConfig](arkts-connectivity-wifimanager-connecttocandidateconfig-f.md) | 使用连接设置连接到指定的候选热点。 |
| [connectToCandidateConfigWithUserAction](arkts-connectivity-wifimanager-connecttocandidateconfigwithuseraction-f.md) | 通过networkId连接到指定的候选热点，并等待用户响应结果。 只允许连接自己添加的配置。此方法一次连接一个配置。 应用必须在前台运行。 |
| [connectToNetwork](arkts-connectivity-wifimanager-connecttonetwork-f.md) | 通过networkId连接到WLAN热点。 |
| [createGroup](arkts-connectivity-wifimanager-creategroup-f.md) | 创建P2P群组。 |
| [disableWifi](arkts-connectivity-wifimanager-disablewifi-f.md) | 关闭WLAN。 |
| [disconnect](arkts-connectivity-wifimanager-disconnect-f.md) | 断开STA与WLAN热点之间的连接。 |
| [enableWifi](arkts-connectivity-wifimanager-enablewifi-f.md) | 启动WLAN。 |
| [getCandidateConfigs](arkts-connectivity-wifimanager-getcandidateconfigs-f.md) | 获取自己添加的所有已存在的候选WLAN配置列表。 只能获取自己在应用上创建的WLAN配置。 |
| [getCountryCode](arkts-connectivity-wifimanager-getcountrycode-f.md) | 获取设备的国家码。 |
| [getCurrentGroup](arkts-connectivity-wifimanager-getcurrentgroup-f.md) | 获取当前P2P群组信息。 |
| [getCurrentGroup](arkts-connectivity-wifimanager-getcurrentgroup-f.md) | 获取当前P2P群组信息。 |
| [getDeviceConfigs](arkts-connectivity-wifimanager-getdeviceconfigs-f.md) | 获取所有已存在的WLAN配置列表。 |
| [getDeviceMacAddress](arkts-connectivity-wifimanager-getdevicemacaddress-f.md) | 获取WLAN设备的MAC地址。必须先使能WLAN。 MAC地址是唯一的，无法更改。 |
| [getIpInfo](arkts-connectivity-wifimanager-getipinfo-f.md) | 获取WLAN连接的IPv4信息。 IP信息包括主机IP地址、网关地址和DNS信息。 |
| [getIpv6Info](arkts-connectivity-wifimanager-getipv6info-f.md) | 获取WLAN连接的IPv6信息。 IPv6信息包括主机IP地址、网关地址和DNS信息。 |
| [getLinkedInfo](arkts-connectivity-wifimanager-getlinkedinfo-f.md) | 获取WLAN连接信息。如果未获取ohos.permission.GET_WIFI_PEERS_MAC权限，返回随机bssid。 |
| [getLinkedInfo](arkts-connectivity-wifimanager-getlinkedinfo-f.md) | 获取WLAN连接信息。 |
| [getLinkedInfoSync](arkts-connectivity-wifimanager-getlinkedinfosync-f.md) | 获取WLAN连接信息。此接口同步返回结果。 如果未获取ohos.permission.GET_WIFI_PEERS_MAC权限，返回随机bssid。 |
| [getMultiLinkedInfo](arkts-connectivity-wifimanager-getmultilinkedinfo-f.md) | 当WLAN处于MLO（多链路操作）状态时，获取多个WLAN连接信息。 如果未获取ohos.permission.GET_WIFI_PEERS_MAC权限，返回随机bssid。 |
| [getP2pLinkedInfo](arkts-connectivity-wifimanager-getp2plinkedinfo-f.md) | 获取P2P连接信息。 |
| [getP2pLinkedInfo](arkts-connectivity-wifimanager-getp2plinkedinfo-f.md) | 获取P2P连接信息。 |
| [getP2pLocalDevice](arkts-connectivity-wifimanager-getp2plocaldevice-f.md) | 获取本设备的信息。 如果未获取ohos.permission.GET_WIFI_LOCAL_MAC权限，返回的WifiP2pDevice中的DeviceAddress将设置为"00:00:00:00:00:00"。 |
| [getP2pLocalDevice](arkts-connectivity-wifimanager-getp2plocaldevice-f.md) | 获取本设备的信息。 如果未获取ohos.permission.GET_WIFI_LOCAL_MAC权限，返回的WifiP2pDevice中的DeviceAddress将设置为"00:00:00:00:00:00"。 |
| [getP2pPeerDevices](arkts-connectivity-wifimanager-getp2ppeerdevices-f.md) | 获取已发现设备的信息。 |
| [getP2pPeerDevices](arkts-connectivity-wifimanager-getp2ppeerdevices-f.md) | 获取已发现设备的信息。 |
| [getScanInfoList](arkts-connectivity-wifimanager-getscaninfolist-f.md) | 获取扫描结果。如果未获取ohos.permission.GET_WIFI_PEERS_MAC权限，返回随机bssid。 |
| [getScanResults](arkts-connectivity-wifimanager-getscanresults-f.md) | 获取扫描结果，使用Promise异步回调。 |
| [getScanResults](arkts-connectivity-wifimanager-getscanresults-f.md) | 获取扫描结果，使用callback异步回调。 |
| [getScanResultsSync](arkts-connectivity-wifimanager-getscanresultssync-f.md) | 获取扫描结果，使用同步方式返回扫描到的WLAN热点信息（如果有）。 |
| [getSignalLevel](arkts-connectivity-wifimanager-getsignallevel-f.md) | 根据WLAN RSSI和频段计算WLAN信号强度。 |
| [isBandTypeSupported](arkts-connectivity-wifimanager-isbandtypesupported-f.md) | 检查当前设备是否支持指定频段。 |
| [isConnected](arkts-connectivity-wifimanager-isconnected-f.md) | 检查WLAN连接是否已建立。 |
| [isFeatureSupported](arkts-connectivity-wifimanager-isfeaturesupported-f.md) | 检查设备是否支持指定特性。 |
| [isHotspotActive](arkts-connectivity-wifimanager-ishotspotactive-f.md) | 检查设备上的WLAN热点是否已激活。 |
| [isMeteredHotspot](arkts-connectivity-wifimanager-ismeteredhotspot-f.md) | 查询热点是否为按流量计费热点。 |
| [isWifiActive](arkts-connectivity-wifimanager-iswifiactive-f.md) | 查询WLAN开关是否已使能。 |
| [isWlanSupported](arkts-connectivity-wifimanager-iswlansupported-f.md) | 查询WLAN是否可用。 |
| [offHotspotStateChange](arkts-connectivity-wifimanager-offhotspotstatechange-f.md) | 取消注册热点状态改变事件。 如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |
| [offP2pConnectionChange](arkts-connectivity-wifimanager-offp2pconnectionchange-f.md) | 取消注册P2P连接状态改变事件。 |
| [offP2pDeviceChange](arkts-connectivity-wifimanager-offp2pdevicechange-f.md) | 取消注册P2P本端设备状态改变事件。 |
| [offP2pDiscoveryChange](arkts-connectivity-wifimanager-offp2pdiscoverychange-f.md) | 取消注册发现设备状态改变事件。 |
| [offP2pPeerDeviceChange](arkts-connectivity-wifimanager-offp2ppeerdevicechange-f.md) | 取消注册P2P对端设备状态改变事件。 |
| [offP2pPersistentGroupChange](arkts-connectivity-wifimanager-offp2ppersistentgroupchange-f.md) | 取消注册P2P永久组状态改变事件。 |
| [offP2pStateChange](arkts-connectivity-wifimanager-offp2pstatechange-f.md) | 取消注册P2P开关状态改变事件。 |
| [offWifiConnectionChange](arkts-connectivity-wifimanager-offwificonnectionchange-f.md) | 取消注册WLAN连接状态改变事件。 如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |
| [offWifiRssiChange](arkts-connectivity-wifimanager-offwifirssichange-f.md) | 取消注册WLAN接收信号强度(RSSI)变化事件。 如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |
| [offWifiScanStateChange](arkts-connectivity-wifimanager-offwifiscanstatechange-f.md) | 取消注册扫描状态改变事件。 如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |
| [offWifiStateChange](arkts-connectivity-wifimanager-offwifistatechange-f.md) | 取消注册WLAN状态改变事件。 如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |
| [off_hotspotStateChange](arkts-connectivity-wifimanager-offhotspotstatechange-f.md) | 取消注册热点状态改变事件。 如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |
| [off_p2pConnectionChange](arkts-connectivity-wifimanager-offp2pconnectionchange-f.md) | 取消注册P2P连接状态改变事件。 |
| [off_p2pDeviceChange](arkts-connectivity-wifimanager-offp2pdevicechange-f.md) | 取消注册P2P本端设备状态改变事件。 |
| [off_p2pDiscoveryChange](arkts-connectivity-wifimanager-offp2pdiscoverychange-f.md) | 取消注册发现设备状态改变事件。 |
| [off_p2pPeerDeviceChange](arkts-connectivity-wifimanager-offp2ppeerdevicechange-f.md) | 取消注册P2P对端设备状态改变事件。 |
| [off_p2pPersistentGroupChange](arkts-connectivity-wifimanager-offp2ppersistentgroupchange-f.md) | 取消注册P2P永久组状态改变事件。 |
| [off_p2pStateChange](arkts-connectivity-wifimanager-offp2pstatechange-f.md) | 取消注册P2P开关状态改变事件。 |
| [off_wifiConnectionChange](arkts-connectivity-wifimanager-offwificonnectionchange-f.md) | 取消注册WLAN连接状态改变事件。 如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |
| [off_wifiRssiChange](arkts-connectivity-wifimanager-offwifirssichange-f.md) | 取消注册WLAN接收信号强度(RSSI)变化事件。 如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |
| [off_wifiScanStateChange](arkts-connectivity-wifimanager-offwifiscanstatechange-f.md) | 取消注册扫描状态改变事件。 如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |
| [off_wifiStateChange](arkts-connectivity-wifimanager-offwifistatechange-f.md) | 取消注册WLAN状态改变事件。 如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |
| [onHotspotStateChange](arkts-connectivity-wifimanager-onhotspotstatechange-f.md) | 注册热点状态改变事件。 |
| [onP2pConnectionChange](arkts-connectivity-wifimanager-onp2pconnectionchange-f.md) | 注册P2P连接状态改变事件。 |
| [onP2pDeviceChange](arkts-connectivity-wifimanager-onp2pdevicechange-f.md) | 注册P2P本端设备状态改变事件。 |
| [onP2pDiscoveryChange](arkts-connectivity-wifimanager-onp2pdiscoverychange-f.md) | 注册发现设备状态改变事件。 |
| [onP2pPeerDeviceChange](arkts-connectivity-wifimanager-onp2ppeerdevicechange-f.md) | 注册P2P对端设备状态改变事件。 |
| [onP2pPersistentGroupChange](arkts-connectivity-wifimanager-onp2ppersistentgroupchange-f.md) | 注册P2P永久组状态改变事件。 |
| [onP2pStateChange](arkts-connectivity-wifimanager-onp2pstatechange-f.md) | 注册P2P开关状态改变事件。 |
| [onWifiConnectionChange](arkts-connectivity-wifimanager-onwificonnectionchange-f.md) | 注册WLAN连接状态改变事件。 |
| [onWifiRssiChange](arkts-connectivity-wifimanager-onwifirssichange-f.md) | 注册WLAN接收信号强度(RSSI)变化事件。 |
| [onWifiScanStateChange](arkts-connectivity-wifimanager-onwifiscanstatechange-f.md) | 注册扫描状态改变事件。 |
| [onWifiStateChange](arkts-connectivity-wifimanager-onwifistatechange-f.md) | 注册WLAN状态改变事件。 |
| [on_hotspotStateChange](arkts-connectivity-wifimanager-onhotspotstatechange-f.md) | 注册热点状态改变事件。 |
| [on_p2pConnectionChange](arkts-connectivity-wifimanager-onp2pconnectionchange-f.md) | 注册P2P连接状态改变事件。 |
| [on_p2pDeviceChange](arkts-connectivity-wifimanager-onp2pdevicechange-f.md) | 注册P2P本端设备状态改变事件。 |
| [on_p2pDiscoveryChange](arkts-connectivity-wifimanager-onp2pdiscoverychange-f.md) | 注册发现设备状态改变事件。 |
| [on_p2pPeerDeviceChange](arkts-connectivity-wifimanager-onp2ppeerdevicechange-f.md) | 注册P2P对端设备状态改变事件。 |
| [on_p2pPersistentGroupChange](arkts-connectivity-wifimanager-onp2ppersistentgroupchange-f.md) | 注册P2P永久组状态改变事件。 |
| [on_p2pStateChange](arkts-connectivity-wifimanager-onp2pstatechange-f.md) | 注册P2P开关状态改变事件。 |
| [on_wifiConnectionChange](arkts-connectivity-wifimanager-onwificonnectionchange-f.md) | 注册WLAN连接状态改变事件。 |
| [on_wifiRssiChange](arkts-connectivity-wifimanager-onwifirssichange-f.md) | 注册WLAN接收信号强度(RSSI)变化事件。 |
| [on_wifiScanStateChange](arkts-connectivity-wifimanager-onwifiscanstatechange-f.md) | 注册扫描状态改变事件。 |
| [on_wifiStateChange](arkts-connectivity-wifimanager-onwifistatechange-f.md) | 注册WLAN状态改变事件。 |
| [p2pCancelConnect](arkts-connectivity-wifimanager-p2pcancelconnect-f.md) | 停止正在建立的P2P连接。 |
| [p2pConnect](arkts-connectivity-wifimanager-p2pconnect-f.md) | 使用指定配置发起与设备的P2P连接。 |
| [removeCandidateConfig](arkts-connectivity-wifimanager-removecandidateconfig-f.md) | 移除指定的候选热点配置，只允许移除自己添加的配置。 应用必须在前台运行。 |
| [removeCandidateConfig](arkts-connectivity-wifimanager-removecandidateconfig-f.md) | 移除指定的候选热点配置，只允许移除自己添加的配置。 应用必须在前台运行。 |
| [removeDevice](arkts-connectivity-wifimanager-removedevice-f.md) | 通过networkId移除WLAN DeviceConfig。 WLAN DeviceConfig移除后，其配置将从WLAN配置列表中删除。 如果该WLAN DeviceConfig正在连接中，则连接将被中断。 应用只能删除自己创建的WLAN DeviceConfig。 |
| [removeGroup](arkts-connectivity-wifimanager-removegroup-f.md) | 移除P2P群组。 |
| [scan](arkts-connectivity-wifimanager-scan-f.md) | 启动WLAN扫描。 |
| [startDiscoverDevices](arkts-connectivity-wifimanager-startdiscoverdevices-f.md) | 开始发现WLAN P2P设备。 |
| [startScan](arkts-connectivity-wifimanager-startscan-f.md) | 启动WLAN扫描。 |
| [stopDiscoverDevices](arkts-connectivity-wifimanager-stopdiscoverdevices-f.md) | 停止发现WLAN P2P设备。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addHotspotBlockList](arkts-connectivity-wifimanager-addhotspotblocklist-f-sys.md) | 将站点添加到黑名单，该站点无法访问热点。 |
| [allowAutoConnect](arkts-connectivity-wifimanager-allowautoconnect-f-sys.md) | 设置是否允许通过networkId自动连接。 如果isAllowed为true，则可以再次关联该网络，否则不可。 |
| [connectToDevice](arkts-connectivity-wifimanager-connecttodevice-f-sys.md) | 连接到指定网络（如果当前已经连接到热点，请先使用disconnect()接口断开连接）。 |
| [delHotspotBlockList](arkts-connectivity-wifimanager-delhotspotblocklist-f-sys.md) | 从黑名单中删除站点，该站点可以访问热点。 |
| [deletePersistentGroup](arkts-connectivity-wifimanager-deletepersistentgroup-f-sys.md) | 删除指定网络ID的持久P2P群组。 |
| [disableHotspot](arkts-connectivity-wifimanager-disablehotspot-f-sys.md) | 关闭WLAN热点功能。 此方法为异步方法。如果WLAN热点关闭后WLAN已使能，则WLAN可能会重新使能。 |
| [disableNetwork](arkts-connectivity-wifimanager-disablenetwork-f-sys.md) | 通过networkId去使能指定的DeviceConfig。 去使能后的DeviceConfig将不再被关联。 |
| [disableNetwork](arkts-connectivity-wifimanager-disablenetwork-f-sys.md) | 通过networkId在一段时间内去使能指定的DeviceConfig。 去使能后的DeviceConfig将不再被关联。 |
| [enableHiLinkHandshake](arkts-connectivity-wifimanager-enablehilinkhandshake-f-sys.md) | 启动hiLink握手。 |
| [enableHotspot](arkts-connectivity-wifimanager-enablehotspot-f-sys.md) | 启动WLAN热点功能。 此方法为异步方法。WLAN热点使能后，WLAN可能会被关闭。 |
| [enableSemiWifi](arkts-connectivity-wifimanager-enablesemiwifi-f-sys.md) | 使能WLAN半关闭（STA关闭、其他P2p、Hml可用）。 |
| [factoryReset](arkts-connectivity-wifimanager-factoryreset-f-sys.md) | 重置所有已保存的设备配置。 |
| [get5GChannelList](arkts-connectivity-wifimanager-get5gchannellist-f-sys.md) | 获取设备支持的5G信道列表。 |
| [getDeviceConfig](arkts-connectivity-wifimanager-getdeviceconfig-f-sys.md) | 根据网络ID获取单条WLAN配置。 |
| [getDisconnectedReason](arkts-connectivity-wifimanager-getdisconnectedreason-f-sys.md) | 获取最近的断开连接原因。 |
| [getHotspotBlockList](arkts-connectivity-wifimanager-gethotspotblocklist-f-sys.md) | 获取黑名单中的所有站点。如果未获取ohos.permission.GET_WIFI_PEERS_MAC权限，返回随机bssid。 |
| [getHotspotConfig](arkts-connectivity-wifimanager-gethotspotconfig-f-sys.md) | 获取WLAN热点配置。 |
| [getP2pGroups](arkts-connectivity-wifimanager-getp2pgroups-f-sys.md) | 获取群组信息。 |
| [getP2pGroups](arkts-connectivity-wifimanager-getp2pgroups-f-sys.md) | 获取群组信息。 |
| [getScanAlwaysAllowed](arkts-connectivity-wifimanager-getscanalwaysallowed-f-sys.md) | 获取是否始终允许扫描。 |
| [getStations](arkts-connectivity-wifimanager-getstations-f-sys.md) | 获取连接到WLAN热点的站点列表。 此方法只能在作为WLAN热点的设备上使用。 |
| [getSupportedFeatures](arkts-connectivity-wifimanager-getsupportedfeatures-f-sys.md) | 查询设备支持的特性。 检查此设备是否支持指定特性。 |
| [getWifiCapability](arkts-connectivity-wifimanager-getwificapability-f-sys.md) | 获取WLAN支持的能力。 |
| [getWifiDetailState](arkts-connectivity-wifimanager-getwifidetailstate-f-sys.md) | 获取WLAN开关详细状态。 |
| [isHotspotDualBandSupported](arkts-connectivity-wifimanager-ishotspotdualbandsupported-f-sys.md) | 检查作为WLAN热点的设备是否同时支持2.4 GHz和5 GHz WLAN。 |
| [isOpenSoftApAllowed](arkts-connectivity-wifimanager-isopensoftapallowed-f-sys.md) | 检查在某些情况下是否可以操作WLAN热点。当飞行模式开启 且不支持softap与sta共存，也不支持信号桥接时， 热点开关无法操作。 |
| [isRandomMacDisabled](arkts-connectivity-wifimanager-israndommacdisabled-f-sys.md) | 随机MAC地址是否被禁用。 |
| [offDeviceConfigChange](arkts-connectivity-wifimanager-offdeviceconfigchange-f-sys.md) | 注册设备配置改变事件。 |
| [offHotspotStaJoin](arkts-connectivity-wifimanager-offhotspotstajoin-f-sys.md) | 取消注册热点STA加入事件。 如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |
| [offHotspotStaLeave](arkts-connectivity-wifimanager-offhotspotstaleave-f-sys.md) | 取消注册热点STA离开事件。 |
| [offStreamChange](arkts-connectivity-wifimanager-offstreamchange-f-sys.md) | 取消注册WLAN流量改变事件。 如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |
| [off_deviceConfigChange](arkts-connectivity-wifimanager-offdeviceconfigchange-f-sys.md) | 注册设备配置改变事件。 |
| [off_hotspotStaJoin](arkts-connectivity-wifimanager-offhotspotstajoin-f-sys.md) | 取消注册热点STA加入事件。 如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |
| [off_hotspotStaLeave](arkts-connectivity-wifimanager-offhotspotstaleave-f-sys.md) | 取消注册热点STA离开事件。 |
| [off_streamChange](arkts-connectivity-wifimanager-offstreamchange-f-sys.md) | 取消注册WLAN流量改变事件。 如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |
| [onDeviceConfigChange](arkts-connectivity-wifimanager-ondeviceconfigchange-f-sys.md) | 注册设备配置改变事件。 |
| [onHotspotStaJoin](arkts-connectivity-wifimanager-onhotspotstajoin-f-sys.md) | 注册热点STA加入事件。 |
| [onHotspotStaLeave](arkts-connectivity-wifimanager-onhotspotstaleave-f-sys.md) | 注册热点STA离开事件。 |
| [onStreamChange](arkts-connectivity-wifimanager-onstreamchange-f-sys.md) | 注册WLAN流量改变事件。 |
| [on_deviceConfigChange](arkts-connectivity-wifimanager-ondeviceconfigchange-f-sys.md) | 注册设备配置改变事件。 |
| [on_hotspotStaJoin](arkts-connectivity-wifimanager-onhotspotstajoin-f-sys.md) | 注册热点STA加入事件。 |
| [on_hotspotStaLeave](arkts-connectivity-wifimanager-onhotspotstaleave-f-sys.md) | 注册热点STA离开事件。 |
| [on_streamChange](arkts-connectivity-wifimanager-onstreamchange-f-sys.md) | 注册WLAN流量改变事件。 |
| [reassociate](arkts-connectivity-wifimanager-reassociate-f-sys.md) | 重新关联当前网络。 |
| [reconnect](arkts-connectivity-wifimanager-reconnect-f-sys.md) | 重新连接当前网络。 |
| [removeAllNetwork](arkts-connectivity-wifimanager-removeallnetwork-f-sys.md) | 移除所有已保存的WLAN配置。 |
| [setDeviceName](arkts-connectivity-wifimanager-setdevicename-f-sys.md) | 设置WLAN P2P设备的名称。 |
| [setHotspotConfig](arkts-connectivity-wifimanager-sethotspotconfig-f-sys.md) | 设置设备的热点配置。 |
| [setScanAlwaysAllowed](arkts-connectivity-wifimanager-setscanalwaysallowed-f-sys.md) | 用户可以在WLAN关闭时触发扫描。 |
| [setWifiCapability](arkts-connectivity-wifimanager-setwificapability-f-sys.md) | 设置WLAN能力。 |
| [startPortalCertification](arkts-connectivity-wifimanager-startportalcertification-f-sys.md) | 启动Portal认证。 |
| [startWifiDetection](arkts-connectivity-wifimanager-startwifidetection-f-sys.md) | 发起WLAN网络探测。 |
| [updateNetwork](arkts-connectivity-wifimanager-updatenetwork-f-sys.md) | 更新指定的WLAN配置。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [ConnectSettings](arkts-connectivity-wifimanager-connectsettings-i.md) | 描述WLAN连接的设置信息。 |
| [IpInfo](arkts-connectivity-wifimanager-ipinfo-i.md) | WLAN IP信息。 |
| [Ipv6Info](arkts-connectivity-wifimanager-ipv6info-i.md) | WLAN IPv6信息。 |
| [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i.md) | WLAN设备配置信息。 |
| [WifiEapConfig](arkts-connectivity-wifimanager-wifieapconfig-i.md) | WLAN EAP配置。 |
| [WifiInfoElem](arkts-connectivity-wifimanager-wifiinfoelem-i.md) | WLAN信息元素。 |
| [WifiLinkedInfo](arkts-connectivity-wifimanager-wifilinkedinfo-i.md) | WLAN连接信息。 |
| [WifiP2PConfig](arkts-connectivity-wifimanager-wifip2pconfig-i.md) | P2P配置信息。 |
| [WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md) | P2P设备信息。 |
| [WifiP2pGroupInfo](arkts-connectivity-wifimanager-wifip2pgroupinfo-i.md) | P2P群组信息。 |
| [WifiP2pLinkedInfo](arkts-connectivity-wifimanager-wifip2plinkedinfo-i.md) | P2P连接信息。 |
| [WifiScanInfo](arkts-connectivity-wifimanager-wifiscaninfo-i.md) | 描述WLAN扫描信息。 |
| [WifiWapiConfig](arkts-connectivity-wifimanager-wifiwapiconfig-i.md) | WLAN WAPI配置。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [HotspotConfig](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md) | WLAN热点配置信息。 |
| [IpConfig](arkts-connectivity-wifimanager-ipconfig-i-sys.md) | WLAN IP配置信息。 |
| [Ipv6Config](arkts-connectivity-wifimanager-ipv6config-i-sys.md) | WLAN Ipv6配置信息。 |
| [StationInfo](arkts-connectivity-wifimanager-stationinfo-i-sys.md) | WLAN站点信息。 |
| [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i-sys.md) | WLAN设备配置信息。 |
| [WifiLinkedInfo](arkts-connectivity-wifimanager-wifilinkedinfo-i-sys.md) | WLAN连接信息。 |
| [WifiProxyConfig](arkts-connectivity-wifimanager-wifiproxyconfig-i-sys.md) | WLAN代理配置。 |
| [WifiScanInfo](arkts-connectivity-wifimanager-wifiscaninfo-i-sys.md) | 描述WLAN扫描信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ConnState](arkts-connectivity-wifimanager-connstate-e.md) | WLAN连接状态枚举。 |
| [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md) | WLAN设备地址（mac/bssid）类型。 |
| [EapMethod](arkts-connectivity-wifimanager-eapmethod-e.md) | WLAN EAP认证方式。 |
| [GroupOwnerBand](arkts-connectivity-wifimanager-groupownerband-e.md) | P2P群组带宽。 |
| [P2pConnectState](arkts-connectivity-wifimanager-p2pconnectstate-e.md) | P2P连接状态。 |
| [P2pDeviceStatus](arkts-connectivity-wifimanager-p2pdevicestatus-e.md) | P2P设备状态。 |
| [Phase2Method](arkts-connectivity-wifimanager-phase2method-e.md) | WLAN Phase 2认证方式。 |
| [WapiPskType](arkts-connectivity-wifimanager-wapipsktype-e.md) | 描述WAPI预共享密钥类型。 |
| [WifiBandType](arkts-connectivity-wifimanager-wifibandtype-e.md) | WLAN频段类型。 |
| [WifiCapability](arkts-connectivity-wifimanager-wificapability-e.md) | WLAN能力 |
| [WifiCategory](arkts-connectivity-wifimanager-wificategory-e.md) | WLAN类别。 |
| [WifiChannelWidth](arkts-connectivity-wifimanager-wifichannelwidth-e.md) | 描述WLAN信道带宽。 |
| [WifiLinkType](arkts-connectivity-wifimanager-wifilinktype-e.md) | WLAN连接类型。 |
| [WifiSecurityType](arkts-connectivity-wifimanager-wifisecuritytype-e.md) | 描述WLAN加密类型。 |
| [WifiStandard](arkts-connectivity-wifimanager-wifistandard-e.md) | WLAN标准。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DisconnectedReason](arkts-connectivity-wifimanager-disconnectedreason-e-sys.md) | WLAN断开原因。 |
| [IpType](arkts-connectivity-wifimanager-iptype-e-sys.md) | WLAN IP类型枚举。 |
| [ProxyMethod](arkts-connectivity-wifimanager-proxymethod-e-sys.md) | WLAN代理方式。 |
| [SuppState](arkts-connectivity-wifimanager-suppstate-e-sys.md) | supplicant状态枚举。 |
| [WifiDetailState](arkts-connectivity-wifimanager-wifidetailstate-e-sys.md) | WLAN详细状态。 |
<!--DelEnd-->

