# @ohos.wifiManager(WLAN)

该模块主要提供Wi-Fi基础功能（无线接入、无线加密、无线漫游等）、P2P（peer-to-peer）服务的基础功能和Wi-Fi消息通知的相应服务，让应用可以通过Wi-Fi和其他设备互联互通。

**起始版本：** 9

**系统能力：** 
- API版本12+：SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addCandidateConfig](arkts-connectivity-wifimanager-addcandidateconfig-f.md) | 添加候选网络配置，使用Promise异步回调，使用前先开启Wi-Fi。 |
| [addCandidateConfig](arkts-connectivity-wifimanager-addcandidateconfig-f.md) | 添加候选网络配置，使用callback异步回调。 |
| [addDeviceConfig](arkts-connectivity-wifimanager-adddeviceconfig-f.md) | 添加网络配置。使用Promise异步回调。 |
| [addDeviceConfig](arkts-connectivity-wifimanager-adddeviceconfig-f.md) | 添加网络配置。使用callback异步回调。 |
| [connectToCandidateConfig](arkts-connectivity-wifimanager-connecttocandidateconfig-f.md) | 应用使用该接口连接到自己添加的候选网络。 |
| [connectToCandidateConfig](arkts-connectivity-wifimanager-connecttocandidateconfig-f.md) | 应用使用该接口连接到自己添加的候选网络，支持设置自定义参数。 |
| [connectToCandidateConfigWithUserAction](arkts-connectivity-wifimanager-connecttocandidateconfigwithuseraction-f.md) | 该接口用于应用连接到用户添加的候选网络，并在连接时提示用户进行信任确认。使用Promise异步回调。 |
| [connectToNetwork](arkts-connectivity-wifimanager-connecttonetwork-f.md) | 应用使用该接口连接到热点。 |
| [createGroup](arkts-connectivity-wifimanager-creategroup-f.md) | 创建群组。创建群组后，可调用[removeGroup](arkts-connectivity-wifimanager-removegroup-f.md)移除已创建的群组。 |
| [disableWifi](arkts-connectivity-wifimanager-disablewifi-f.md) | 关闭Wi-Fi。 |
| [disconnect](arkts-connectivity-wifimanager-disconnect-f.md) | 断开Wi-Fi连接。 |
| [enableWifi](arkts-connectivity-wifimanager-enablewifi-f.md) | 启动Wi-Fi。 |
| [getCandidateConfigs](arkts-connectivity-wifimanager-getcandidateconfigs-f.md) | 获取候选网络配置。 |
| [getCountryCode](arkts-connectivity-wifimanager-getcountrycode-f.md) | 获取国家码信息。 |
| [getCurrentGroup](arkts-connectivity-wifimanager-getcurrentgroup-f.md) | 获取P2P当前组信息。使用Promise异步回调。 |
| [getCurrentGroup](arkts-connectivity-wifimanager-getcurrentgroup-f.md) | 获取P2P当前组信息。使用callback异步回调。 |
| [getDeviceConfigs](arkts-connectivity-wifimanager-getdeviceconfigs-f.md) | 获取网络配置。 |
| [getDeviceMacAddress](arkts-connectivity-wifimanager-getdevicemacaddress-f.md) | 获取设备的MAC地址。 |
| [getIpInfo](arkts-connectivity-wifimanager-getipinfo-f.md) | 获取IPV4信息。 |
| [getIpv6Info](arkts-connectivity-wifimanager-getipv6info-f.md) | 获取IPV6信息。 |
| [getLinkedInfo](arkts-connectivity-wifimanager-getlinkedinfo-f.md) | 获取Wi-Fi连接信息。使用Promise异步回调。 |
| [getLinkedInfo](arkts-connectivity-wifimanager-getlinkedinfo-f.md) | 获取Wi-Fi连接信息。使用callback异步回调。 |
| [getLinkedInfoSync](arkts-connectivity-wifimanager-getlinkedinfosync-f.md) | 获取Wi-Fi连接信息，使用同步方式返回结果。 |
| [getMultiLinkedInfo](arkts-connectivity-wifimanager-getmultilinkedinfo-f.md) | 获取MLO(Multi-Link Operation，多链路操作)Wi-Fi连接信息。 |
| [getP2pLinkedInfo](arkts-connectivity-wifimanager-getp2plinkedinfo-f.md) | 获取P2P连接信息。使用Promise异步回调。 |
| [getP2pLinkedInfo](arkts-connectivity-wifimanager-getp2plinkedinfo-f.md) | 获取P2P连接信息。使用callback异步回调。 |
| [getP2pLocalDevice](arkts-connectivity-wifimanager-getp2plocaldevice-f.md) | 获取P2P本端设备信息，使用Promise异步回调。 |
| [getP2pLocalDevice](arkts-connectivity-wifimanager-getp2plocaldevice-f.md) | 获取P2P本端设备信息，使用callback异步回调。 |
| [getP2pPeerDevices](arkts-connectivity-wifimanager-getp2ppeerdevices-f.md) | 获取P2P对端设备列表信息。使用Promise异步回调。 |
| [getP2pPeerDevices](arkts-connectivity-wifimanager-getp2ppeerdevices-f.md) | 获取P2P对端设备列表信息。使用callback异步回调。 |
| [getScanInfoList](arkts-connectivity-wifimanager-getscaninfolist-f.md) | 获取包含当前时间点前30s内的缓存扫描结果。 |
| [getScanResults](arkts-connectivity-wifimanager-getscanresults-f.md) | 获取扫描结果，使用Promise异步回调。 |
| [getScanResults](arkts-connectivity-wifimanager-getscanresults-f.md) | 获取扫描结果，使用callback异步回调。 |
| [getScanResultsSync](arkts-connectivity-wifimanager-getscanresultssync-f.md) | 获取扫描结果，使用同步方式返回一个包含多个WifiScanInfo对象的数组，每个对象表示一个Wi-Fi网络的扫描信息。 |
| [getSignalLevel](arkts-connectivity-wifimanager-getsignallevel-f.md) | 查询Wi-Fi信号强度。 |
| [isBandTypeSupported](arkts-connectivity-wifimanager-isbandtypesupported-f.md) | 判断当前频段是否支持。 |
| [isConnected](arkts-connectivity-wifimanager-isconnected-f.md) | 查询Wi-Fi是否已连接。 |
| [isFeatureSupported](arkts-connectivity-wifimanager-isfeaturesupported-f.md) | 判断设备是否支持指定的Wi-Fi特性。 |
| [isHotspotActive](arkts-connectivity-wifimanager-ishotspotactive-f.md) | 热点是否已开启。 |
| [isMeteredHotspot](arkts-connectivity-wifimanager-ismeteredhotspot-f.md) | 查询设备当前连接的wifi是否是手机热点。 |
| [isWifiActive](arkts-connectivity-wifimanager-iswifiactive-f.md) | 查询Wi-Fi开关是否已激活。 |
| [isWlanSupported](arkts-connectivity-wifimanager-iswlansupported-f.md) | 查询是否可用Wi-Fi网络。 |
| [off](arkts-connectivity-wifimanager-off-f.md#offwifistatechange) | 取消注册Wi-Fi状态改变事件。使用callback异步回调。 |
| [off](arkts-connectivity-wifimanager-off-f.md#offwificonnectionchange) | 取消注册Wi-Fi连接状态改变事件。使用callback异步回调。 |
| [off](arkts-connectivity-wifimanager-off-f.md#offwifiscanstatechange) | 取消注册扫描状态改变事件。使用callback异步回调。 |
| [off](arkts-connectivity-wifimanager-off-f.md#offwifirssichange) | 取消注册Wi-Fi接收信号强度(RSSI)变化事件。使用callback异步回调。 |
| [off](arkts-connectivity-wifimanager-off-f.md#offhotspotstatechange) | 取消注册热点状态改变事件。使用callback异步回调。 |
| [off](arkts-connectivity-wifimanager-off-f.md#offp2pstatechange) | 取消注册P2P开关状态改变事件。使用callback异步回调。 |
| [off](arkts-connectivity-wifimanager-off-f.md#offp2pconnectionchange) | 取消注册P2P连接状态改变事件。使用callback异步回调。 |
| [off](arkts-connectivity-wifimanager-off-f.md#offp2pdevicechange) | 取消注册P2P设备状态改变事件。使用callback异步回调。 |
| [off](arkts-connectivity-wifimanager-off-f.md#offp2ppeerdevicechange) | 取消注册P2P对端设备状态改变事件。使用callback异步回调。 |
| [off](arkts-connectivity-wifimanager-off-f.md#offp2ppersistentgroupchange) | 取消注册P2P永久组状态改变事件。使用callback异步回调。 |
| [off](arkts-connectivity-wifimanager-off-f.md#offp2pdiscoverychange) | 取消注册发现设备状态改变事件。使用callback异步回调。 |
| [on](arkts-connectivity-wifimanager-on-f.md#onwifistatechange) | 注册Wi-Fi状态改变事件，在业务退出时，要调用off(type: 'wifiStateChange', callback?: Callback&lt;number&gt;)接口去掉之前的注册回调。使用callback异步回调。 |
| [on](arkts-connectivity-wifimanager-on-f.md#onwificonnectionchange) | 注册Wi-Fi连接状态改变事件，在业务退出时，要调用off(type: 'wifiConnectionChange', callback?: Callback&lt;number&gt;)接口去掉之前的注册回调。使用callback异步回调。 |
| [on](arkts-connectivity-wifimanager-on-f.md#onwifiscanstatechange) | 注册扫描状态改变事件，在业务退出时，要调用off(type: 'wifiScanStateChange', callback?: Callback&lt;number&gt;)接口去掉之前的注册回调。使用callback异步回调。 |
| [on](arkts-connectivity-wifimanager-on-f.md#onwifirssichange) | 注册Wi-Fi接收信号强度(RSSI)变化事件，在业务退出时，要调用off(type: 'wifiRssiChange', callback?: Callback&lt;number&gt;)接口去掉之前的注册回调。使用callback异步回调。 |
| [on](arkts-connectivity-wifimanager-on-f.md#onhotspotstatechange) | 注册热点状态改变事件，在业务退出时，要调用off(type: 'hotspotStateChange', callback?: Callback&lt;number&gt;)接口去掉之前的注册回调。使用callback异步回调。 |
| [on](arkts-connectivity-wifimanager-on-f.md#onp2pstatechange) | 注册P2P开关状态改变事件，在业务退出时，要调用off(type: 'p2pStateChange', callback?: Callback&lt;number&gt;)接口去掉之前的注册回调。使用callback异步回调。 |
| [on](arkts-connectivity-wifimanager-on-f.md#onp2pconnectionchange) | 注册P2P连接状态改变事件，在业务退出时，要调用off(type: 'p2pConnectionChange', callback?: Callback&lt;WifiP2pLinkedInfo&gt;)接口去掉之前的注册回调。使用callback异步回调。 |
| [on](arkts-connectivity-wifimanager-on-f.md#onp2pdevicechange) | 注册P2P设备状态改变事件，在业务退出时，要调用off(type: 'p2pDeviceChange', callback?: Callback&lt;WifiP2pDevice&gt;)接口去掉之前的注册回调。使用callback异步回调。 |
| [on](arkts-connectivity-wifimanager-on-f.md#onp2ppeerdevicechange) | 注册P2P对端设备状态改变事件，在业务退出时，要调用off(type: 'p2pPeerDeviceChange', callback?: Callback&lt;WifiP2pDevice[]&gt;)接口去掉之前的注册回调。使用callback异步回调。 |
| [on](arkts-connectivity-wifimanager-on-f.md#onp2ppersistentgroupchange) | 注册P2P永久组状态改变事件，在业务退出时，要调用off(type: 'p2pPersistentGroupChange', callback?: Callback&lt;void&gt;)接口去掉之前的注册回调。使用callback异步回调。 |
| [on](arkts-connectivity-wifimanager-on-f.md#onp2pdiscoverychange) | 注册发现设备状态改变事件，在业务退出时，要调用off(type: 'p2pDiscoveryChange', callback?: Callback&lt;number&gt;)接口去掉之前的注册回调。使用callback异步回调。 |
| [p2pCancelConnect](arkts-connectivity-wifimanager-p2pcancelconnect-f.md) | 在P2P连接过程中，取消P2P连接。 |
| [p2pConnect](arkts-connectivity-wifimanager-p2pconnect-f.md) | 执行P2P连接。调用此方法连接后，如需取消可调用[p2pCancelConnect](arkts-connectivity-wifimanager-p2pcancelconnect-f.md)。 |
| [removeCandidateConfig](arkts-connectivity-wifimanager-removecandidateconfig-f.md) | 移除候选网络配置，使用Promise异步回调。 |
| [removeCandidateConfig](arkts-connectivity-wifimanager-removecandidateconfig-f.md) | 移除指定的候选网络配置，使用callback异步回调。 |
| [removeDevice](arkts-connectivity-wifimanager-removedevice-f.md) | 移除网络配置。 |
| [removeGroup](arkts-connectivity-wifimanager-removegroup-f.md) | 移除群组。 |
| [scan](arkts-connectivity-wifimanager-scan-f.md) | 启动Wi-Fi扫描，使用前先开启Wi-Fi。 |
| [startDiscoverDevices](arkts-connectivity-wifimanager-startdiscoverdevices-f.md) | 开始发现设备。调用此方法后，可调用[stopDiscoverDevices](arkts-connectivity-wifimanager-stopdiscoverdevices-f.md)停止发现设备以释放资源。 |
| [startScan](arkts-connectivity-wifimanager-startscan-f.md) | 启动Wi-Fi扫描。 |
| [stopDiscoverDevices](arkts-connectivity-wifimanager-stopdiscoverdevices-f.md) | 停止发现设备。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addHotspotBlockList](arkts-connectivity-wifimanager-addhotspotblocklist-f-sys.md) | 将设备添加到热点的阻止连接设备列表中，列表中的设备将不能访问热点。 |
| [allowAutoConnect](arkts-connectivity-wifimanager-allowautoconnect-f-sys.md) | 设置是否允许通过networkId自动连接。如果isAllowed为true，则可以再次关联该网络，否则不可。 |
| [connectToDevice](arkts-connectivity-wifimanager-connecttodevice-f-sys.md) | 连接到指定网络（如果当前已经连接到热点，请先断开连接）。 |
| [deletePersistentGroup](arkts-connectivity-wifimanager-deletepersistentgroup-f-sys.md) | 删除指定网络ID的永久Wi-Fi组配置。该接口用于清除已保存的Wi-Fi网络配置信息，使其不再自动连接。 |
| [delHotspotBlockList](arkts-connectivity-wifimanager-delhotspotblocklist-f-sys.md) | 将设备从热点的阻止列表中删除。 |
| [disableHotspot](arkts-connectivity-wifimanager-disablehotspot-f-sys.md) | 关闭热点 ，异步接口，是否关闭成功需要注册并监听hotspotStateChange的回调。 |
| [disableNetwork](arkts-connectivity-wifimanager-disablenetwork-f-sys.md) | 关闭网络配置。 |
| [disableNetwork](arkts-connectivity-wifimanager-disablenetwork-f-sys.md) | 禁用网络连接，将已连接的网络断开，且在设置的时间范围内无法自动回连。 |
| [enableHiLinkHandshake](arkts-connectivity-wifimanager-enablehilinkhandshake-f-sys.md) | 设置是否使能hiLink。 |
| [enableHotspot](arkts-connectivity-wifimanager-enablehotspot-f-sys.md) | 开启热点，异步接口，是否打开成功需要注册并监听hotspotStateChange的回调。 |
| [enableSemiWifi](arkts-connectivity-wifimanager-enablesemiwifi-f-sys.md) | 使能Wi-Fi半关闭（STA关闭，P2P、HML等功能可用），异步接口，需要通过注册"wifiStateChange"事件的回调来监听是否使能成功。 |
| [factoryReset](arkts-connectivity-wifimanager-factoryreset-f-sys.md) | 重置所有已保存的设备配置。 |
| [get5GChannelList](arkts-connectivity-wifimanager-get5gchannellist-f-sys.md) | 获取当前设备支持的5G信道列表。 |
| [getDeviceConfig](arkts-connectivity-wifimanager-getdeviceconfig-f-sys.md) | 根据网络ID获取单条网络配置。 |
| [getDisconnectedReason](arkts-connectivity-wifimanager-getdisconnectedreason-f-sys.md) | 获取最近一次断连原因。 |
| [getHotspotBlockList](arkts-connectivity-wifimanager-gethotspotblocklist-f-sys.md) | 获取当前Wi-Fi热点的黑名单设备列表。该接口返回被热点拉黑的设备信息列表，仅在设备作为热点(AP)模式下有效。 |
| [getHotspotConfig](arkts-connectivity-wifimanager-gethotspotconfig-f-sys.md) | 获取Wi-Fi热点的配置信息，包括SSID、加密方式、密码、带宽、信道、最大连接STA数量等。 |
| [getP2pGroups](arkts-connectivity-wifimanager-getp2pgroups-f-sys.md) | 获取创建的所有P2P群组信息，使用Promise异步回调。 |
| [getP2pGroups](arkts-connectivity-wifimanager-getp2pgroups-f-sys.md) | 获取创建的所有P2P群组信息，使用callback异步回调。 |
| [getScanAlwaysAllowed](arkts-connectivity-wifimanager-getscanalwaysallowed-f-sys.md) | 获取是否始终允许扫描。 |
| [getStations](arkts-connectivity-wifimanager-getstations-f-sys.md) | 获取当前连接到本设备热点的所有设备信息列表。 |
| [getSupportedFeatures](arkts-connectivity-wifimanager-getsupportedfeatures-f-sys.md) | 查询设备支持的特性。 |
| [getWifiCapability](arkts-connectivity-wifimanager-getwificapability-f-sys.md) | 获取Wi-Fi支持的能力。 |
| [getWifiDetailState](arkts-connectivity-wifimanager-getwifidetailstate-f-sys.md) | 获取Wi-Fi开关详细状态。 |
| [isHotspotDualBandSupported](arkts-connectivity-wifimanager-ishotspotdualbandsupported-f-sys.md) | 检查当前设备的Wi-Fi热点功能是否支持双频段（同时支持2.4GHz和5GHz频段）。 |
| [isOpenSoftApAllowed](arkts-connectivity-wifimanager-isopensoftapallowed-f-sys.md) | 检查在某些情况下是否能够操作Wi-Fi热点。当飞行模式开启时，如果系统不支持SoftAP和STA共存，也不支持信号桥接，则无法操作热点开关。 |
| [isRandomMacDisabled](arkts-connectivity-wifimanager-israndommacdisabled-f-sys.md) | 随机MAC地址是否被禁用。 |
| [off](arkts-connectivity-wifimanager-off-f-sys.md#offstreamchange) | 取消注册Wi-Fi流变更事件。使用callback异步回调。 |
| [off](arkts-connectivity-wifimanager-off-f-sys.md#offdeviceconfigchange) | 取消注册Wi-Fi设备配置更改事件。使用callback异步回调。 |
| [off](arkts-connectivity-wifimanager-off-f-sys.md#offhotspotstajoin) | 取消注册Wi-Fi热点的STA加入事件。使用callback异步回调。 |
| [off](arkts-connectivity-wifimanager-off-f-sys.md#offhotspotstaleave) | 取消注册Wi-Fi热点STA离开事件。使用callback异步回调。 |
| [on](arkts-connectivity-wifimanager-on-f-sys.md#onstreamchange) | 注册Wi-Fi流变更事件，在业务退出时，要调用off(type: 'streamChange', callback?: Callback&lt;number&gt;)接口去掉之前的注册回调。使用callback异步回调。 |
| [on](arkts-connectivity-wifimanager-on-f-sys.md#ondeviceconfigchange) | 注册Wi-Fi设备配置更改事件，在业务退出时，要调用off(type: 'deviceConfigChange', callback?: Callback&lt;number&gt;)接口去掉之前的注册回调。使用callback异步回调。 |
| [on](arkts-connectivity-wifimanager-on-f-sys.md#onhotspotstajoin) | 注册Wi-Fi热点STA加入事件，在业务退出时，要调用off(type: 'hotspotStaJoin', callback?: Callback&lt;StationInfo&gt;)接口去掉之前的注册回调。使用callback异步回调。 |
| [on](arkts-connectivity-wifimanager-on-f-sys.md#onhotspotstaleave) | 注册Wi-Fi热点STA离开事件，在业务退出时，要调用off(type: 'hotspotStaLeave', callback?: Callback&lt;StationInfo&gt;)接口去掉之前的注册回调。使用callback异步回调。 |
| [reassociate](arkts-connectivity-wifimanager-reassociate-f-sys.md) | 重新关联网络。 |
| [reconnect](arkts-connectivity-wifimanager-reconnect-f-sys.md) | 重新连接网络。 |
| [removeAllNetwork](arkts-connectivity-wifimanager-removeallnetwork-f-sys.md) | 移除所有网络配置。 |
| [setDeviceName](arkts-connectivity-wifimanager-setdevicename-f-sys.md) | 设置设备名称。 |
| [setHotspotConfig](arkts-connectivity-wifimanager-sethotspotconfig-f-sys.md) | 设置Wi-Fi热点的配置信息，包括SSID、加密方式、密码、带宽、信道、最大连接STA数量等。 |
| [setScanAlwaysAllowed](arkts-connectivity-wifimanager-setscanalwaysallowed-f-sys.md) | 设置是否始终允许扫描。 |
| [setWifiCapability](arkts-connectivity-wifimanager-setwificapability-f-sys.md) | 设置Wi-Fi能力。 |
| [startPortalCertification](arkts-connectivity-wifimanager-startportalcertification-f-sys.md) | 启动Portal认证流程，用于处理需要Web页面认证的公共Wi-Fi网络（如酒店、机场、咖啡厅等场所的网络）。 |
| [startWifiDetection](arkts-connectivity-wifimanager-startwifidetection-f-sys.md) | 发起WiFi网络探测。 |
| [updateNetwork](arkts-connectivity-wifimanager-updatenetwork-f-sys.md) | 更新网络配置。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [ConnectSettings](arkts-connectivity-wifimanager-connectsettings-i.md) | 连接Wi-Fi设置信息。 |
| [IpInfo](arkts-connectivity-wifimanager-ipinfo-i.md) | IPV4信息。 |
| [Ipv6Info](arkts-connectivity-wifimanager-ipv6info-i.md) | Ipv6信息。 |
| [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i.md) | Wi-Fi配置信息。 |
| [WifiEapConfig](arkts-connectivity-wifimanager-wifieapconfig-i.md) | 可扩展身份验证协议配置信息。 |
| [WifiInfoElem](arkts-connectivity-wifimanager-wifiinfoelem-i.md) | Wi-Fi热点信息。 |
| [WifiLinkedInfo](arkts-connectivity-wifimanager-wifilinkedinfo-i.md) | Wi-Fi连接信息。 |
| [WifiP2PConfig](arkts-connectivity-wifimanager-wifip2pconfig-i.md) | 表示P2P配置信息。 |
| [WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md) | 表示P2P设备信息。 |
| [WifiP2pGroupInfo](arkts-connectivity-wifimanager-wifip2pgroupinfo-i.md) | 表示P2P群组相关信息。 |
| [WifiP2pLinkedInfo](arkts-connectivity-wifimanager-wifip2plinkedinfo-i.md) | 提供Wi-Fi连接的相关信息。 |
| [WifiScanInfo](arkts-connectivity-wifimanager-wifiscaninfo-i.md) | Wi-Fi热点信息。 |
| [WifiWapiConfig](arkts-connectivity-wifimanager-wifiwapiconfig-i.md) | WAPI(Wireless LAN Authentication and Privacy Infrastructure) 身份验证协议配置。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [HotspotConfig](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md) | 热点配置信息。 |
| [IpConfig](arkts-connectivity-wifimanager-ipconfig-i-sys.md) | IP配置信息。 |
| [Ipv6Config](arkts-connectivity-wifimanager-ipv6config-i-sys.md) | Wi-Fi IPv6配置信息。 |
| [StationInfo](arkts-connectivity-wifimanager-stationinfo-i-sys.md) | 接入的设备信息。包含连接到Wi-Fi网络的设备详细信息。 |
| [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i-sys.md) | Wi-Fi配置信息。 |
| [WifiLinkedInfo](arkts-connectivity-wifimanager-wifilinkedinfo-i-sys.md) | Wi-Fi连接信息。 |
| [WifiProxyConfig](arkts-connectivity-wifimanager-wifiproxyconfig-i-sys.md) | Wifi 代理配置。 |
| [WifiScanInfo](arkts-connectivity-wifimanager-wifiscaninfo-i-sys.md) | Wi-Fi热点信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ConnState](arkts-connectivity-wifimanager-connstate-e.md) | 表示Wi-Fi连接状态的枚举。 |
| [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md) | Wi-Fi设备地址（MAC/BSSID）类型。是标识Wi-Fi设备或接入点的唯一地址。 |
| [EapMethod](arkts-connectivity-wifimanager-eapmethod-e.md) | 表示EAP认证方式的枚举。 |
| [GroupOwnerBand](arkts-connectivity-wifimanager-groupownerband-e.md) | 表示群组带宽的枚举。 |
| [P2pConnectState](arkts-connectivity-wifimanager-p2pconnectstate-e.md) | 表示P2P连接状态的枚举。 |
| [P2pDeviceStatus](arkts-connectivity-wifimanager-p2pdevicestatus-e.md) | 表示设备状态的枚举。 |
| [Phase2Method](arkts-connectivity-wifimanager-phase2method-e.md) | 表示第二阶段认证方式的枚举。 |
| [WapiPskType](arkts-connectivity-wifimanager-wapipsktype-e.md) | WAPI认证方式的枚举。 |
| [WifiBandType](arkts-connectivity-wifimanager-wifibandtype-e.md) | 表示WIFI频段类型的枚举。 |
| [WifiCapability](arkts-connectivity-wifimanager-wificapability-e.md) | Wi-Fi功能。 |
| [WifiCategory](arkts-connectivity-wifimanager-wificategory-e.md) | 表示热点支持的最高Wi-Fi类别。可以用于识别和区分不同Wi-Fi技术标准的热点。 |
| [WifiChannelWidth](arkts-connectivity-wifimanager-wifichannelwidth-e.md) | 表示带宽类型的枚举。 |
| [WifiLinkType](arkts-connectivity-wifimanager-wifilinktype-e.md) | 枚举，Wi-Fi7连接类型。 |
| [WifiSecurityType](arkts-connectivity-wifimanager-wifisecuritytype-e.md) | 表示加密类型的枚举。 |
| [WifiStandard](arkts-connectivity-wifimanager-wifistandard-e.md) | 表示WIFI标准的枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DisconnectedReason](arkts-connectivity-wifimanager-disconnectedreason-e-sys.md) | 表示Wi-Fi断开原因的枚举，用于诊断网络连接问题和优化连接策略。 |
| [IpType](arkts-connectivity-wifimanager-iptype-e-sys.md) | 表示IP类型的枚举。 |
| [ProxyMethod](arkts-connectivity-wifimanager-proxymethod-e-sys.md) | 表示WiFi代理方法的枚举。 |
| [SuppState](arkts-connectivity-wifimanager-suppstate-e-sys.md) | 表示请求状态的枚举。 |
| [WifiDetailState](arkts-connectivity-wifimanager-wifidetailstate-e-sys.md) | 表示Wi-Fi开关状态的枚举。 |
<!--DelEnd-->
