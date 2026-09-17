# @ohos.wifi(WLAN)

该模块主要提供Wi-Fi基础功能（如Wi-Fi扫描、连接管理、连接信息查询、信号强度获取等）、P2P（peer-to-peer）功能（如设备发现、群组创建与管理、P2P连接等）和Wi-Fi消息通知服务，适用于应用通过Wi-Fi接入网络或与其他设备进行点对点数据传输和互联互通的场景。

> **说明：** 
> 
> 从API version 9开始，该接口不再维护，推荐使用[@ohos.wifiManager (WLAN)](arkts-connectivity-wifimanager.md)等相关接口。

**起始版本：** 6

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addUntrustedConfig](arkts-connectivity-wifi-adduntrustedconfig-f.md) | 添加不可信网络配置，使用Promise异步回调。 |
| [addUntrustedConfig](arkts-connectivity-wifi-adduntrustedconfig-f.md) | 添加不可信网络配置，使用callback异步回调。 |
| [createGroup](arkts-connectivity-wifi-creategroup-f.md) | 创建群组。 |
| [getCountryCode](arkts-connectivity-wifi-getcountrycode-f.md) | 获取国家码信息。 |
| [getCurrentGroup](arkts-connectivity-wifi-getcurrentgroup-f.md) | 获取P2P当前组信息。使用Promise异步回调。 |
| [getCurrentGroup](arkts-connectivity-wifi-getcurrentgroup-f.md) | 获取P2P当前组信息。使用callback异步回调。 |
| [getIpInfo](arkts-connectivity-wifi-getipinfo-f.md) | 获取IP信息。 |
| [getLinkedInfo](arkts-connectivity-wifi-getlinkedinfo-f.md) | 获取Wi-Fi连接信息。使用Promise异步回调。 |
| [getLinkedInfo](arkts-connectivity-wifi-getlinkedinfo-f.md) | 获取Wi-Fi连接信息。使用callback异步回调。 |
| [getP2pLinkedInfo](arkts-connectivity-wifi-getp2plinkedinfo-f.md) | 获取P2P连接信息。使用Promise异步回调。 |
| [getP2pLinkedInfo](arkts-connectivity-wifi-getp2plinkedinfo-f.md) | 获取P2P连接信息。使用callback异步回调。 |
| [getP2pPeerDevices](arkts-connectivity-wifi-getp2ppeerdevices-f.md) | 获取P2P对端设备列表信息。使用Promise异步回调。 |
| [getP2pPeerDevices](arkts-connectivity-wifi-getp2ppeerdevices-f.md) | 获取P2P对端设备列表信息。使用callback异步回调。 |
| [getScanInfos](arkts-connectivity-wifi-getscaninfos-f.md) | 获取扫描结果，使用Promise异步回调。 |
| [getScanInfos](arkts-connectivity-wifi-getscaninfos-f.md) | 获取扫描结果，使用callback异步回调。 |
| [getSignalLevel](arkts-connectivity-wifi-getsignallevel-f.md) | 查询Wi-Fi信号强度。 |
| [isConnected](arkts-connectivity-wifi-isconnected-f.md) | 查询Wi-Fi是否已连接。 |
| [isFeatureSupported](arkts-connectivity-wifi-isfeaturesupported-f.md) | 判断设备是否支持指定featureId对应的Wi-Fi特性。 |
| [isWifiActive](arkts-connectivity-wifi-iswifiactive-f.md) | 查询Wi-Fi是否已使能。 |
| [off](arkts-connectivity-wifi-off-f.md#offwifistatechange) | 取消注册Wi-Fi状态改变事件。 |
| [off](arkts-connectivity-wifi-off-f.md#offwificonnectionchange) | 取消注册Wi-Fi连接状态改变事件。 |
| [off](arkts-connectivity-wifi-off-f.md#offwifiscanstatechange) | 取消注册扫描状态改变事件。 |
| [off](arkts-connectivity-wifi-off-f.md#offwifirssichange) | 取消注册RSSI状态改变事件。 |
| [off](arkts-connectivity-wifi-off-f.md#offhotspotstatechange) | 取消注册热点状态改变事件。 |
| [off](arkts-connectivity-wifi-off-f.md#offp2pstatechange) | 取消注册P2P开关状态改变事件。 |
| [off](arkts-connectivity-wifi-off-f.md#offp2pconnectionchange) | 取消注册P2P连接状态改变事件。 |
| [off](arkts-connectivity-wifi-off-f.md#offp2pdevicechange) | 取消注册P2P设备状态改变事件。 |
| [off](arkts-connectivity-wifi-off-f.md#offp2ppeerdevicechange) | 取消注册P2P对端设备状态改变事件。 |
| [off](arkts-connectivity-wifi-off-f.md#offp2ppersistentgroupchange) | 取消注册P2P永久组状态改变事件。 |
| [off](arkts-connectivity-wifi-off-f.md#offp2pdiscoverychange) | 取消注册发现设备状态改变事件。 |
| [on](arkts-connectivity-wifi-on-f.md#onwifistatechange) | 注册Wi-Fi状态改变事件。 |
| [on](arkts-connectivity-wifi-on-f.md#onwificonnectionchange) | 注册Wi-Fi连接状态改变事件。 |
| [on](arkts-connectivity-wifi-on-f.md#onwifiscanstatechange) | 注册扫描状态改变事件。 |
| [on](arkts-connectivity-wifi-on-f.md#onwifirssichange) | 注册RSSI状态改变事件。 |
| [on](arkts-connectivity-wifi-on-f.md#onhotspotstatechange) | 注册热点状态改变事件。 |
| [on](arkts-connectivity-wifi-on-f.md#onp2pstatechange) | 注册P2P开关状态改变事件。 |
| [on](arkts-connectivity-wifi-on-f.md#onp2pconnectionchange) | 注册P2P连接状态改变事件。 |
| [on](arkts-connectivity-wifi-on-f.md#onp2pdevicechange) | 注册P2P设备状态改变事件。 |
| [on](arkts-connectivity-wifi-on-f.md#onp2ppeerdevicechange) | 注册P2P对端设备状态改变事件。 |
| [on](arkts-connectivity-wifi-on-f.md#onp2ppersistentgroupchange) | 注册P2P永久组状态改变事件。 |
| [on](arkts-connectivity-wifi-on-f.md#onp2pdiscoverychange) | 注册发现设备状态改变事件。 |
| [p2pCancelConnect](arkts-connectivity-wifi-p2pcancelconnect-f.md) | 取消P2P连接。 |
| [p2pConnect](arkts-connectivity-wifi-p2pconnect-f.md) | 执行P2P连接。 |
| [removeGroup](arkts-connectivity-wifi-removegroup-f.md) | 移除群组。 |
| [removeUntrustedConfig](arkts-connectivity-wifi-removeuntrustedconfig-f.md) | 移除不可信网络配置，使用Promise异步回调。 |
| [removeUntrustedConfig](arkts-connectivity-wifi-removeuntrustedconfig-f.md) | 移除不可信网络配置，使用callback异步回调。 |
| [scan](arkts-connectivity-wifi-scan-f.md) | 启动Wi-Fi扫描。 |
| [startDiscoverDevices](arkts-connectivity-wifi-startdiscoverdevices-f.md) | 开始发现设备。 |
| [stopDiscoverDevices](arkts-connectivity-wifi-stopdiscoverdevices-f.md) | 停止发现设备。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addDeviceConfig](arkts-connectivity-wifi-adddeviceconfig-f-sys.md) | 添加网络配置。使用Promise异步回调。 |
| [addDeviceConfig](arkts-connectivity-wifi-adddeviceconfig-f-sys.md) | 添加网络配置。使用callback异步回调。 |
| [connectToDevice](arkts-connectivity-wifi-connecttodevice-f-sys.md) | 连接到指定网络。 |
| [connectToNetwork](arkts-connectivity-wifi-connecttonetwork-f-sys.md) | 应用使用该接口连接到热点。 |
| [deletePersistentGroup](arkts-connectivity-wifi-deletepersistentgroup-f-sys.md) | 删除永久组。 |
| [disableHotspot](arkts-connectivity-wifi-disablehotspot-f-sys.md) | 关闭热点。 |
| [disableNetwork](arkts-connectivity-wifi-disablenetwork-f-sys.md) | 关闭网络配置。 |
| [disableWifi](arkts-connectivity-wifi-disablewifi-f-sys.md) | 禁用Wi-Fi。 |
| [disconnect](arkts-connectivity-wifi-disconnect-f-sys.md) | 断开连接的网络。 |
| [enableHotspot](arkts-connectivity-wifi-enablehotspot-f-sys.md) | 开启热点。 |
| [enableWifi](arkts-connectivity-wifi-enablewifi-f-sys.md) | 启动Wi-Fi。 |
| [getDeviceConfigs](arkts-connectivity-wifi-getdeviceconfigs-f-sys.md) | 获取网络配置。 |
| [getDeviceMacAddress](arkts-connectivity-wifi-getdevicemacaddress-f-sys.md) | 获取设备的MAC地址。 |
| [getHotspotConfig](arkts-connectivity-wifi-gethotspotconfig-f-sys.md) | 获取热点配置信息。 |
| [getStations](arkts-connectivity-wifi-getstations-f-sys.md) | 获取连接的设备。 |
| [getSupportedFeatures](arkts-connectivity-wifi-getsupportedfeatures-f-sys.md) | 查询设备支持的特性。 |
| [isHotspotActive](arkts-connectivity-wifi-ishotspotactive-f-sys.md) | 热点是否已激活。 |
| [isHotspotDualBandSupported](arkts-connectivity-wifi-ishotspotdualbandsupported-f-sys.md) | 热点是否支持双频。 |
| [off](arkts-connectivity-wifi-off-f-sys.md#offstreamchange) | 取消注册Wi-Fi流更改事件。使用callback异步回调。 |
| [off](arkts-connectivity-wifi-off-f-sys.md#offhotspotstajoin) | 取消注册Wi-Fi热点sta加入事件。使用callback异步回调。 |
| [off](arkts-connectivity-wifi-off-f-sys.md#offhotspotstaleave) | 取消注册Wi-Fi热点sta离开事件。使用callback异步回调。 |
| [on](arkts-connectivity-wifi-on-f-sys.md#onstreamchange) | 注册Wi-Fi流更改事件。使用callback异步回调。 |
| [on](arkts-connectivity-wifi-on-f-sys.md#onhotspotstajoin) | 注册Wi-Fi热点sta加入事件。使用callback异步回调。 |
| [on](arkts-connectivity-wifi-on-f-sys.md#onhotspotstaleave) | 注册Wi-Fi热点sta离开事件。使用callback异步回调。 |
| [reassociate](arkts-connectivity-wifi-reassociate-f-sys.md) | 重新关联网络。 |
| [reconnect](arkts-connectivity-wifi-reconnect-f-sys.md) | 重新连接网络。 |
| [removeAllNetwork](arkts-connectivity-wifi-removeallnetwork-f-sys.md) | 移除所有网络配置。 |
| [removeDevice](arkts-connectivity-wifi-removedevice-f-sys.md) | 移除指定的网络配置。 |
| [setDeviceName](arkts-connectivity-wifi-setdevicename-f-sys.md) | 设置设备名称。 |
| [setHotspotConfig](arkts-connectivity-wifi-sethotspotconfig-f-sys.md) | 设置热点配置信息。 |
| [updateNetwork](arkts-connectivity-wifi-updatenetwork-f-sys.md) | 更新网络配置。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [IpInfo](arkts-connectivity-wifi-ipinfo-i.md) | IP信息。 |
| [WifiDeviceConfig](arkts-connectivity-wifi-wifideviceconfig-i.md) | Wi-Fi配置信息。 |
| [WifiLinkedInfo](arkts-connectivity-wifi-wifilinkedinfo-i.md) | 提供Wi-Fi连接的相关信息。 |
| [WifiP2PConfig](arkts-connectivity-wifi-wifip2pconfig-i.md) | 表示P2P配置信息。 |
| [WifiP2pDevice](arkts-connectivity-wifi-wifip2pdevice-i.md) | 表示P2P设备信息。 |
| [WifiP2pGroupInfo](arkts-connectivity-wifi-wifip2pgroupinfo-i.md) | 表示P2P群组相关信息。 |
| [WifiP2pLinkedInfo](arkts-connectivity-wifi-wifip2plinkedinfo-i.md) | 提供P2P连接的相关信息。 |
| [WifiScanInfo](arkts-connectivity-wifi-wifiscaninfo-i.md) | Wi-Fi热点信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [HotspotConfig](arkts-connectivity-wifi-hotspotconfig-i-sys.md) | 热点配置信息。 |
| [IpConfig](arkts-connectivity-wifi-ipconfig-i-sys.md) | IPv4配置信息。 |
| [StationInfo](arkts-connectivity-wifi-stationinfo-i-sys.md) | 接入的设备信息。 |
| [WifiDeviceConfig](arkts-connectivity-wifi-wifideviceconfig-i-sys.md) | Wi-Fi配置信息。 |
| [WifiLinkedInfo](arkts-connectivity-wifi-wifilinkedinfo-i-sys.md) | 提供Wi-Fi连接的相关信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ConnState](arkts-connectivity-wifi-connstate-e.md) | 表示Wi-Fi连接状态的枚举。 |
| [GroupOwnerBand](arkts-connectivity-wifi-groupownerband-e.md) | 表示群组带宽的枚举。 |
| [P2pConnectState](arkts-connectivity-wifi-p2pconnectstate-e.md) | 表示P2P连接状态的枚举。 |
| [P2pDeviceStatus](arkts-connectivity-wifi-p2pdevicestatus-e.md) | 表示设备状态的枚举。 |
| [WifiSecurityType](arkts-connectivity-wifi-wifisecuritytype-e.md) | 表示加密类型的枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [IpType](arkts-connectivity-wifi-iptype-e-sys.md) | 表示IP类型的枚举。 |
| [SuppState](arkts-connectivity-wifi-suppstate-e-sys.md) | 表示请求状态的枚举。 |
<!--DelEnd-->
