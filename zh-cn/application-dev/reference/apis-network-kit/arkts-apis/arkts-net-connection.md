# @ohos.net.connection(网络连接管理)

网络连接管理提供管理网络一些基础能力，包括获取默认激活的网络、获取所有激活网络列表、获取网络能力信息等功能。

> **说明：**
> 
> 无特殊说明，接口默认不支持并发。

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addCustomDnsRule(网络连接管理)](arkts-network-connection-addcustomdnsrule-f.md) | 为当前应用程序添加自定义host和对应的IP地址的映射。使用callback异步回调。 |
| [addCustomDnsRule(网络连接管理)](arkts-network-connection-addcustomdnsrule-f.md) | 为当前应用程序添加自定义host和对应的IP地址的映射。使用Promise异步回调。 |
| [clearCustomDnsRules(网络连接管理)](arkts-network-connection-clearcustomdnsrules-f.md) | 删除当前应用程序的所有的自定义DNS规则。使用callback异步回调。 |
| [clearCustomDnsRules(网络连接管理)](arkts-network-connection-clearcustomdnsrules-f.md) | 删除当前应用程序的所有的自定义DNS规则。使用Promise异步回调。 |
| [createNetConnection(网络连接管理)](arkts-network-connection-createnetconnection-f.md) | 创建一个NetConnection对象，可用于监听网络状态。[netSpecifier](arkts-network-connection-netspecifier-i.md)表示需要监听网络的网络特征；timeout是超时时间（单位：毫秒)； netSpecifier是timeout的必要条件，两者都没有则表示关注默认网络。 |
| [findProxyForUrl(网络连接管理)](arkts-network-connection-findproxyforurl-f.md) | 通过设置的PAC脚本，解析指定的URL代理地址，返回对应的PAC代理信息。 |
| [getAddressesByName(网络连接管理)](arkts-network-connection-getaddressesbyname-f.md) | 使用当前默认网络解析主机名以获取所有IP地址。使用callback异步回调。 |
| [getAddressesByName(网络连接管理)](arkts-network-connection-getaddressesbyname-f.md) | 使用当前默认网络解析主机名以获取所有IP地址。使用Promise异步回调。 |
| [getAddressesByNameWithOptions(网络连接管理)](arkts-network-connection-getaddressesbynamewithoptions-f.md) | 使用当前默认网络基于指定IP类型进行DNS解析。使用Promise异步回调。 |
| [getAllNets(网络连接管理)](arkts-network-connection-getallnets-f.md) | 获取所有处于连接状态的网络列表，使用callback异步回调。 |
| [getAllNets(网络连接管理)](arkts-network-connection-getallnets-f.md) | 获取所有处于连接状态的网络列表。使用Promise异步回调。 |
| [getAllNetsSync(网络连接管理)](arkts-network-connection-getallnetssync-f.md) | 获取所有处于连接状态的网络列表。使用同步方式返回。 |
| [getAppNet(网络连接管理)](arkts-network-connection-getappnet-f.md) | 获取App绑定的网络句柄。使用callback异步回调。 |
| [getAppNet(网络连接管理)](arkts-network-connection-getappnet-f.md) | 获取App绑定的网络信息。使用Promise异步回调。 |
| [getAppNetSync(网络连接管理)](arkts-network-connection-getappnetsync-f.md) | 获取App绑定的网络信息。使用同步方式返回。 |
| [getConnectionProperties(网络连接管理)](arkts-network-connection-getconnectionproperties-f.md) | 获取netHandle对应的网络的连接信息，包含网卡名称、域名、链路信息、路由信息、网络地址及最大传输单元。使用callback异步回调。 |
| [getConnectionProperties(网络连接管理)](arkts-network-connection-getconnectionproperties-f.md) | 获取netHandle对应的网络的连接信息，包含网卡名称、域名、链路信息、路由信息、网络地址及最大传输单元。使用Promise异步回调。 |
| [getConnectionPropertiesSync(网络连接管理)](arkts-network-connection-getconnectionpropertiessync-f.md) | 获取netHandle对应的网络的连接信息，包含网卡名称、域名、链路信息、路由信息、网络地址及最大传输单元。使用同步方式返回。 |
| [getConnectOwnerUid(网络连接管理)](arkts-network-connection-getconnectowneruid-f.md) | 用于查询发起指定网络连接的应用UID。使用Promise异步回调。 |
| [getConnectOwnerUidSync(网络连接管理)](arkts-network-connection-getconnectowneruidsync-f.md) | 用于查询发起指定网络连接的应用UID。使用同步方式返回。 |
| [getDefaultHttpProxy(网络连接管理)](arkts-network-connection-getdefaulthttpproxy-f.md) | 获取网络的默认代理配置信息。使用callback异步回调。 |
| [getDefaultHttpProxy(网络连接管理)](arkts-network-connection-getdefaulthttpproxy-f.md) | 获取网络默认的代理配置信息。使用Promise异步回调。 |
| [getDefaultNet(网络连接管理)](arkts-network-connection-getdefaultnet-f.md) | 获取系统默认使用的网络句柄，包含网络ID。使用callback异步回调。 |
| [getDefaultNet(网络连接管理)](arkts-network-connection-getdefaultnet-f.md) | 获取系统默认使用的网络句柄，包含网络ID。使用Promise异步回调。 |
| [getDefaultNetSync(网络连接管理)](arkts-network-connection-getdefaultnetsync-f.md) | 获取系统默认使用的网络句柄，包含网络ID。使用同步方式返回。 |
| [getDnsAscii(网络连接管理)](arkts-network-connection-getdnsascii-f.md) | 将Unicode编码形式的主机名转换为ASCII编码形式，并可通过可选的转换流程参数（conversionProcess）控制转换行为。 |
| [getDnsUnicode(网络连接管理)](arkts-network-connection-getdnsunicode-f.md) | 使用Punycode编码方式，将ASCII编码形式的主机名转换为Unicode编码形式，并通过可选的conversionProcess参数控制转换行为。 |
| [getIpNeighTable(网络连接管理)](arkts-network-connection-getipneightable-f.md) | 获取本地设备IP邻居表条目信息，包括IPv4和IPv6，每个条目信息包括IP地址、MAC地址、网卡名。使用Promise异步回调。 |
| [getNetCapabilities(网络连接管理)](arkts-network-connection-getnetcapabilities-f.md) | 获取netHandle对应网络的能力集，包含上/下行带宽、网络具体能力、网络类型。使用callback异步回调。 |
| [getNetCapabilities(网络连接管理)](arkts-network-connection-getnetcapabilities-f.md) | 获取netHandle对应网络的能力集，包含上/下行带宽、网络具体能力、网络类型。使用Promise异步回调。 |
| [getNetCapabilitiesSync(网络连接管理)](arkts-network-connection-getnetcapabilitiessync-f.md) | 获取netHandle对应网络的能力信息，包含上/下行带宽、网络具体能力、网络类型。使用同步方式返回。 |
| [getNetExtAttribute(网络连接管理)](arkts-network-connection-getnetextattribute-f.md) | 获取netHandle对应网络的扩展属性，以确定网络的安全级别。使用Promise异步回调。 |
| [getNetExtAttributeSync(网络连接管理)](arkts-network-connection-getnetextattributesync-f.md) | 获取netHandle对应网络的扩展属性，以确定网络的安全级别。使用同步方式返回。 |
| [getPacFileUrl(网络连接管理)](arkts-network-connection-getpacfileurl-f.md) | 获取当前PAC脚本的URL地址。 |
| [getPacUrl(网络连接管理)](arkts-network-connection-getpacurl-f.md) | 获取系统级代理自动配置（PAC）脚本地址。 |
| [getSystemNetPortStates(网络连接管理)](arkts-network-connection-getsystemnetportstates-f.md) | 获取系统当前监听的所有TCP、UDP端口信息，以及监听端口进程的PID、UID，支持IPv4和IPv6。 |
| [hasDefaultNet(网络连接管理)](arkts-network-connection-hasdefaultnet-f.md) | 获取当前是否有可用网络，使用callback异步回调。如果有可用网络，可以使用[getDefaultNet](arkts-network-connection-getdefaultnet-f.md)获取默认网络句柄。 |
| [hasDefaultNet(网络连接管理)](arkts-network-connection-hasdefaultnet-f.md) | 获取当前是否有可用网络。使用Promise异步回调。如果有可用网络，可以使用[getDefaultNet](arkts-network-connection-getdefaultnet-f.md)获取默认网络句柄。 |
| [hasDefaultNetSync(网络连接管理)](arkts-network-connection-hasdefaultnetsync-f.md) | 获取当前是否有可用网络。使用同步方式返回。 |
| [isDefaultNetMetered(网络连接管理)](arkts-network-connection-isdefaultnetmetered-f.md) | 检查当前默认网络上的数据流量使用是否被计费（例如：WiFi网络不会被计费，蜂窝网络会被计费）。使用callback异步回调。 |
| [isDefaultNetMetered(网络连接管理)](arkts-network-connection-isdefaultnetmetered-f.md) | 检查当前默认网络上的数据流量使用是否被计费（例如：WiFi网络不会被计费，蜂窝网络会被计费）。使用Promise异步回调。 |
| [isDefaultNetMeteredSync(网络连接管理)](arkts-network-connection-isdefaultnetmeteredsync-f.md) | 检查当前网络上的数据流量使用是否被计费（例如：WiFi网络不会被计费，蜂窝网络会被计费）。使用同步方式返回。 |
| [queryProbeResult(网络连接管理)](arkts-network-connection-queryproberesult-f.md) | 查询网络探测结果。若出现异常（例如断网），导致发送请求失败，则接口会立即返回，不再进行后续探测。本接口使用Promise方式作为异步方法。 |
| [queryTraceRoute(网络连接管理)](arkts-network-connection-querytraceroute-f.md) | 查询网络路由跟踪信息，使用Promise方式作为异步方法。 |
| [refreshGlobalHttpProxy(网络连接管理)](arkts-network-connection-refreshglobalhttpproxy-f.md) | 通知系统需要重新验证全局代理。 收到通知后，系统将重新处理全局代理的认证状态。 |
| [removeCustomDnsRule(网络连接管理)](arkts-network-connection-removecustomdnsrule-f.md) | 删除当前应用程序中对应host的自定义DNS规则。使用callback异步回调。 |
| [removeCustomDnsRule(网络连接管理)](arkts-network-connection-removecustomdnsrule-f.md) | 删除当前应用程序中对应host的自定义DNS规则。使用Promise异步回调。 |
| [reportNetConnected(网络连接管理)](arkts-network-connection-reportnetconnected-f.md) | 向网络管理上报网络处于可用状态。使用callback方式异步回调。 |
| [reportNetConnected(网络连接管理)](arkts-network-connection-reportnetconnected-f.md) | 向网络管理报告网络处于可用状态。使用Promise异步回调。 |
| [reportNetDisconnected(网络连接管理)](arkts-network-connection-reportnetdisconnected-f.md) | 向网络管理上报网络处于不可用状态。使用callback异步回调。 |
| [reportNetDisconnected(网络连接管理)](arkts-network-connection-reportnetdisconnected-f.md) | 向网络管理上报网络处于不可用状态。使用Promise异步回调。 |
| [setAppHttpProxy(网络连接管理)](arkts-network-connection-setapphttpproxy-f.md) | 设置应用级Http代理配置信息。 |
| [setAppNet(网络连接管理)](arkts-network-connection-setappnet-f.md) | 将App绑定到特定的网络，绑定后App只能通过netHandle对应的网络访问网络。使用callback异步回调。 |
| [setAppNet(网络连接管理)](arkts-network-connection-setappnet-f.md) | 将App异步绑定到特定的网络，绑定后App只能通过netHandle对应的网络访问网络。使用Promise异步回调。 |
| [setNetExtAttribute(网络连接管理)](arkts-network-connection-setnetextattribute-f.md) | 为netHandle对应的网络设置扩展属性，标识网络的安全级别。使用Promise异步回调。 |
| [setNetExtAttributeSync(网络连接管理)](arkts-network-connection-setnetextattributesync-f.md) | 为netHandle对应的网络设置扩展属性，标识网络的安全级别。使用同步方式返回。 |
| [setPacFileUrl(网络连接管理)](arkts-network-connection-setpacfileurl-f.md) | 设置PAC脚本（Proxy Auto-Configuration Script，代理自动配置脚本）的URL地址，并启动PAC代理能力，比如：http://127.0.0.1:21998/PacProxyScript.pac 。可通 过调用[findProxyForUrl](arkts-network-connection-findproxyforurl-f.md)解析URL地址来获取代理信息。 |
| [setPacUrl(网络连接管理)](arkts-network-connection-setpacurl-f.md) | 设置系统级代理自动配置（Proxy Auto Config，PAC）脚本地址。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addVlanIp(网络连接管理)](arkts-network-connection-addvlanip-f-sys.md) | 为以太网网卡上对应vlanId的虚拟局域网配置指定的IP地址及子网掩码。使用Promise异步回调。 |
| [createVlanInterface(网络连接管理)](arkts-network-connection-createvlaninterface-f-sys.md) | 在指定的以太网网卡上，创建一个由vlanId指定的虚拟局域网。使用Promise异步回调。 |
| [deleteVlanIp(网络连接管理)](arkts-network-connection-deletevlanip-f-sys.md) | 从以太网网卡上对应vlanId的虚拟局域网中，删除已配置的IP地址及子网掩码。使用Promise异步回调。 |
| [destroyVlanInterface(网络连接管理)](arkts-network-connection-destroyvlaninterface-f-sys.md) | 删除指定以太网网卡上由vlanId指定的虚拟局域网。使用Promise异步回调。 |
| [disableAirplaneMode(网络连接管理)](arkts-network-connection-disableairplanemode-f-sys.md) | 关闭飞行模式，使用callback异步回调。 |
| [disableAirplaneMode(网络连接管理)](arkts-network-connection-disableairplanemode-f-sys.md) | 关闭飞行模式，使用Promise异步回调。 |
| [enableAirplaneMode(网络连接管理)](arkts-network-connection-enableairplanemode-f-sys.md) | 开启飞行模式，使用callback异步回调。 |
| [enableAirplaneMode(网络连接管理)](arkts-network-connection-enableairplanemode-f-sys.md) | 开启飞行模式，使用Promise异步回调。 |
| [factoryReset(网络连接管理)](arkts-network-connection-factoryreset-f-sys.md) | 出厂重置网络设置，使用Promise异步回调。 |
| [getGlobalHttpProxy(网络连接管理)](arkts-network-connection-getglobalhttpproxy-f-sys.md) | 获取网络的全局代理配置信息，使用callback异步回调。 |
| [getGlobalHttpProxy(网络连接管理)](arkts-network-connection-getglobalhttpproxy-f-sys.md) | 获取网络的全局代理配置信息，使用Promise异步回调。 |
| [getProxyMode(网络连接管理)](arkts-network-connection-getproxymode-f-sys.md) | 获取当前的代理模式。使用Promise异步回调。 |
| [setGlobalHttpProxy(网络连接管理)](arkts-network-connection-setglobalhttpproxy-f-sys.md) | 设置网络全局Http代理配置信息，使用callback异步回调。 |
| [setGlobalHttpProxy(网络连接管理)](arkts-network-connection-setglobalhttpproxy-f-sys.md) | 设置网络全局Http代理配置信息，使用Promise异步回调。 |
| [setInterfaceUp(网络连接管理)](arkts-network-connection-setinterfaceup-f-sys.md) | 将指定的网卡接口设置为启用状态，使其可以收发网络数据包，参与网络通信；启用后的网卡接口可以被路由子系统选择用于数据传输；系统可以检测到该网络的存在并尝试建立连接，使用Promise异步回调。 |
| [setProxyMode(网络连接管理)](arkts-network-connection-setproxymode-f-sys.md) | 设置代理模式。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [ConnectionProperties(网络连接管理)](arkts-network-connection-connectionproperties-i.md) | 网络连接信息。 |
| [HttpProxy(网络连接管理)](arkts-network-connection-httpproxy-i.md) | 网络代理配置信息 |
| [LinkAddress(网络连接管理)](arkts-network-connection-linkaddress-i.md) | 网络链路信息。 |
| [NetAddress(网络连接管理)](arkts-network-connection-netaddress-i.md) | 网络地址。 |
| [NetBlockStatusInfo(网络连接管理)](arkts-network-connection-netblockstatusinfo-i.md) | 获取网络状态信息。 |
| [NetCapabilities(网络连接管理)](arkts-network-connection-netcapabilities-i.md) | 网络的能力集。 |
| [NetCapabilityInfo(网络连接管理)](arkts-network-connection-netcapabilityinfo-i.md) | 提供承载数据网络能力的实例。 |
| [NetConnection(网络连接管理)](arkts-network-connection-netconnection-i.md) | 网络连接对象类型。 |
| [NetConnectionPropertyInfo(网络连接管理)](arkts-network-connection-netconnectionpropertyinfo-i.md) | 网络连接信息。 |
| [NetHandle(网络连接管理)](arkts-network-connection-nethandle-i.md) | 网络句柄。在调用NetHandle的方法之前，需要先获取NetHandle对象。例如可通过[getDefaultNet](arkts-network-connection-getdefaultnet-f.md)获取系统当前默认网络的网络句柄。 |
| [NetIpMacInfo(网络连接管理)](arkts-network-connection-netipmacinfo-i.md) | IP邻居表条目信息。 |
| [NetPortStatesInfo(网络连接管理)](arkts-network-connection-netportstatesinfo-i.md) | 系统当前监听的TCP、UDP端口信息。 |
| [NetSpecifier(网络连接管理)](arkts-network-connection-netspecifier-i.md) | 提供承载数据网络能力的实例。 |
| [ProbeResultInfo(网络连接管理)](arkts-network-connection-proberesultinfo-i.md) | 网络探测结果信息。 |
| [QueryOptions(网络连接管理)](arkts-network-connection-queryoptions-i.md) | 需要查询的IP类型。 |
| [RouteInfo(网络连接管理)](arkts-network-connection-routeinfo-i.md) | 网络路由信息。 |
| [Socks5Proxy(网络连接管理)](arkts-network-connection-socks5proxy-i.md) | SOCKS5代理配置信息。 |
| [TcpNetPortStatesInfo(网络连接管理)](arkts-network-connection-tcpnetportstatesinfo-i.md) | TCP端口状态信息。 |
| [TraceRouteInfo(网络连接管理)](arkts-network-connection-tracerouteinfo-i.md) | 路由跟踪信息。 |
| [TraceRouteOptions(网络连接管理)](arkts-network-connection-tracerouteoptions-i.md) | 路由跟踪的选项。 |
| [UdpNetPortStatesInfo(网络连接管理)](arkts-network-connection-udpnetportstatesinfo-i.md) | UDP端口状态信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ConversionProcess(网络连接管理)](arkts-network-connection-conversionprocess-e.md) | ASCII/Unicode转码转换流程参数的枚举。 |
| [FamilyType(网络连接管理)](arkts-network-connection-familytype-e.md) | 需要查询的具体IP地址类型。 |
| [NetBearType(网络连接管理)](arkts-network-connection-netbeartype-e.md) | 网络类型。 |
| [NetCap(网络连接管理)](arkts-network-connection-netcap-e.md) | 网络具体能力。 |
| [PacketsType(网络连接管理)](arkts-network-connection-packetstype-e.md) | 网络探测数据包类型。 |
| [ProtocolType(网络连接管理)](arkts-network-connection-protocoltype-e.md) | 网络协议类型的枚举。 |
| [Socks5DnsStrategy(网络连接管理)](arkts-network-connection-socks5dnsstrategy-e.md) | SOCKS5代理的DNS查询策略配置信息。 |
| [TcpState(网络连接管理)](arkts-network-connection-tcpstate-e.md) | TCP状态。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ProxyMode(网络连接管理)](arkts-network-connection-proxymode-e-sys.md) | 表示代理模式的枚举。使用Promise异步回调。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [HttpRequest(网络连接管理)](arkts-network-connection-httprequest-t.md) | 定义一个HTTP请求，可以通过[http.createHttp](arkts-network-http-createhttp-f.md)创建。 |
| [TCPSocket(网络连接管理)](arkts-network-connection-tcpsocket-t.md) | 定义一个TCPSocket对象，可以通过[socket.constructTCPSocketInstance](arkts-network-socket-constructtcpsocketinstance-f.md)创 建。 |
| [UDPSocket(网络连接管理)](arkts-network-connection-udpsocket-t.md) | 定义一个UDPSocket对象，可以通过[socket.constructUDPSocketInstance](arkts-network-socket-constructudpsocketinstance-f.md)创 建。 |
