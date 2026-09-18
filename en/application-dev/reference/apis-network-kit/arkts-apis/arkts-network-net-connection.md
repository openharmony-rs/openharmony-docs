# @ohos.net.connection(Network Connection Management)

The network connection management module provides basic network management capabilities. You can obtain the default active network, the list of all active networks, and network capability information.

> **NOTE:** 
> 
> Unless otherwise specified, the APIs of this module do not support concurrent calls.

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addCustomDnsRule](arkts-network-connection-addcustomdnsrule-f.md) | Adds custom DNS rules for the specified host of the current application. This API uses an asynchronous callback to return the result. |
| [addCustomDnsRule](arkts-network-connection-addcustomdnsrule-f.md) | Adds custom DNS rules for the specified host of the current application. This API uses a promise to return the result. |
| [clearCustomDnsRules](arkts-network-connection-clearcustomdnsrules-f.md) | Removes all custom DNS rules of the current application. This API uses an asynchronous callback to return the result. |
| [clearCustomDnsRules](arkts-network-connection-clearcustomdnsrules-f.md) | Removes all custom DNS rules of the current application. This API uses a promise to return the result. |
| [createNetConnection](arkts-network-connection-createnetconnection-f.md) | Creates a **NetConnection** object, which can be used to listen for the network status. [netSpecifier](arkts-network-connection-netspecifier-i.md) specifies the network to be listened for, and **timeout** indicates the timeout duration (ms). **netSpecifier** is a mandatory parameter for **timeout**. If neither of them is present, the default network is used. |
| [findProxyForUrl](arkts-network-connection-findproxyforurl-f.md) | Parses the specified URL proxy address based on the configured PAC script and returns the corresponding PAC proxy information. |
| [getAddressesByName](arkts-network-connection-getaddressesbyname-f.md) | Obtains all IP addresses of the default network by resolving the host name. This API uses an asynchronous callback to return the result. |
| [getAddressesByName](arkts-network-connection-getaddressesbyname-f.md) | Obtains all IP addresses of the default network by resolving the host name. This API uses a promise to return the result. |
| [getAddressesByNameWithOptions](arkts-network-connection-getaddressesbynamewithoptions-f.md) | Performs the DNS resolution using the current default network based on the specified IP address type. This API uses a promise to return the result. |
| [getAllNets](arkts-network-connection-getallnets-f.md) | Obtains the list of all connected networks. This API uses an asynchronous callback to return the result. |
| [getAllNets](arkts-network-connection-getallnets-f.md) | Obtains the list of all connected networks. This API uses a promise to return the result. |
| [getAllNetsSync](arkts-network-connection-getallnetssync-f.md) | Obtains the list of all connected networks. This API returns the result synchronously. |
| [getAppNet](arkts-network-connection-getappnet-f.md) | Obtains the network handle bound to an application. This API uses an asynchronous callback to return the result. |
| [getAppNet](arkts-network-connection-getappnet-f.md) | Obtains the network information bound to an application. This API uses a promise to return the result. |
| [getAppNetSync](arkts-network-connection-getappnetsync-f.md) | Obtains the network information bound to an application. This API returns the result synchronously. |
| [getConnectionProperties](arkts-network-connection-getconnectionproperties-f.md) | Obtains the connection information of the data network specified by **NetHandle**, including the NIC name, domain name, link information, route information, network address, and maximum transmission unit. This API uses an asynchronous callback to return the result. |
| [getConnectionProperties](arkts-network-connection-getconnectionproperties-f.md) | Obtains the connection information of the data network specified by **NetHandle**, including the NIC name, domain name, link information, route information, network address, and maximum transmission unit. This API uses a promise to return the result. |
| [getConnectionPropertiesSync](arkts-network-connection-getconnectionpropertiessync-f.md) | Obtains the connection information of the data network specified by **NetHandle**, including the NIC name, domain name, link information, route information, network address, and maximum transmission unit. This API returns the result synchronously. |
| [getConnectOwnerUid](arkts-network-connection-getconnectowneruid-f.md) | Queries the UID of the application that initiates a specified network connection. This API uses a promise to return the result. |
| [getConnectOwnerUidSync](arkts-network-connection-getconnectowneruidsync-f.md) | Queries the UID of the application that initiates a specified network connection. This API returns the result synchronously. |
| [getDefaultHttpProxy](arkts-network-connection-getdefaulthttpproxy-f.md) | Obtains the default HTTP proxy configuration of the network. This API uses an asynchronous callback to return the result. |
| [getDefaultHttpProxy](arkts-network-connection-getdefaulthttpproxy-f.md) | Obtains the default HTTP proxy configuration of the network. This API uses a promise to return the result. |
| [getDefaultNet](arkts-network-connection-getdefaultnet-f.md) | Obtains the network handle used by the system by default, including the network ID. This API uses an asynchronous callback to return the result. |
| [getDefaultNet](arkts-network-connection-getdefaultnet-f.md) | Obtains the network handle used by the system by default, including the network ID. This API uses a promise to return the result. |
| [getDefaultNetSync](arkts-network-connection-getdefaultnetsync-f.md) | Obtains the network handle used by the system by default, including the network ID. This API returns the result synchronously. |
| [getDnsAscii](arkts-network-connection-getdnsascii-f.md) | Converts the host name from Unicode to ASCII and controls the conversion behavior through the optional conversion process parameter (**conversionProcess**). |
| [getDnsUnicode](arkts-network-connection-getdnsunicode-f.md) | Converts host names from ASCII to Unicode using the Punycode encoding mode and uses the optional conversionProcess parameter to control the conversion behavior. |
| [getIpNeighTable](arkts-network-connection-getipneightable-f.md) | Obtains information about entries in the IP neighbor table of the local device, including IPv4 and IPv6 entries. Each entry contains an IP address, a MAC address, and a network adapter name. This API uses a promise to return the result. |
| [getNetCapabilities](arkts-network-connection-getnetcapabilities-f.md) | Obtains the network capability set of the data network specified by **NetHandle**, including the uplink and downlink bandwidth, specific network capabilities, and network type. This API uses an asynchronous callback to return the result. |
| [getNetCapabilities](arkts-network-connection-getnetcapabilities-f.md) | Obtains the network capability set of the data network specified by **NetHandle**, including the uplink and downlink bandwidth, specific network capabilities, and network type. This API uses a promise to return the result. |
| [getNetCapabilitiesSync](arkts-network-connection-getnetcapabilitiessync-f.md) | Obtains the network capability information of the data network specified by **NetHandle**, including the uplink and downlink bandwidth, specific network capabilities, and network type. This API returns the result synchronously. |
| [getNetExtAttribute](arkts-network-connection-getnetextattribute-f.md) | Obtains the extended attributes of the network specified by **netHandle** to determine its security level. This API uses a promise to return the result. |
| [getNetExtAttributeSync](arkts-network-connection-getnetextattributesync-f.md) | Obtains the extended attributes of the network specified by **netHandle** to determine its security level. This API returns the result synchronously. |
| [getPacFileUrl](arkts-network-connection-getpacfileurl-f.md) | Obtains the URL of the current PAC script. |
| [getPacUrl](arkts-network-connection-getpacurl-f.md) | Obtains the URL of the system-level PAC script. |
| [getSystemNetPortStates](arkts-network-connection-getsystemnetportstates-f.md) | Obtains information about all TCP and UDP ports currently listened by the system, and the PID and UID of the processes that listen for the ports. Both IPv4 and IPv6 addresses are supported. |
| [hasDefaultNet](arkts-network-connection-hasdefaultnet-f.md) | Checks whether there is an available network. This API uses an asynchronous callback to return the result. If there is an available network, [getDefaultNet](arkts-network-connection-getdefaultnet-f.md) can be used to obtain the default network handle. |
| [hasDefaultNet](arkts-network-connection-hasdefaultnet-f.md) | Checks whether there is an available network. This API uses a promise to return the result. If there is an available network, [getDefaultNet](arkts-network-connection-getdefaultnet-f.md) can be used to obtain the default network handle. |
| [hasDefaultNetSync](arkts-network-connection-hasdefaultnetsync-f.md) | Checks whether there is an available network. This API returns the result synchronously. |
| [isDefaultNetMetered](arkts-network-connection-isdefaultnetmetered-f.md) | Checks whether the data traffic over the current default network is metered. For example, data traffic over Wi-Fi is not metered, whereas that over cellular networks is. This API uses an asynchronous callback to return the result. |
| [isDefaultNetMetered](arkts-network-connection-isdefaultnetmetered-f.md) | Checks whether the data traffic over the current default network is metered. For example, data traffic over Wi-Fi is not metered, whereas that over cellular networks is. This API uses a promise to return the result. |
| [isDefaultNetMeteredSync](arkts-network-connection-isdefaultnetmeteredsync-f.md) | Checks whether the data traffic over the current network is metered. For example, data traffic over Wi-Fi is not metered, whereas that over cellular networks is. This API returns the result synchronously. |
| [queryProbeResult](arkts-network-connection-queryproberesult-f.md) | Queries network probe results. If an exception (for example, network disconnection) occurs and the request fails to be sent, the API immediately returns the result without performing subsequent probe. This API uses a promise to return the result. |
| [queryTraceRoute](arkts-network-connection-querytraceroute-f.md) | Queries the network route tracing information. This API uses a promise to return the result. |
| [refreshGlobalHttpProxy](arkts-network-connection-refreshglobalhttpproxy-f.md) | Notifies the system that global proxy re-authentication is required. Upon receiving the notification, the system will reprocess the global proxy's authentication status. |
| [removeCustomDnsRule](arkts-network-connection-removecustomdnsrule-f.md) | Removes the custom DNS rules of the specified host from the current application. This API uses an asynchronous callback to return the result. |
| [removeCustomDnsRule](arkts-network-connection-removecustomdnsrule-f.md) | Removes the custom DNS rules of the specified host from the current application. This API uses a promise to return the result. |
| [reportNetConnected](arkts-network-connection-reportnetconnected-f.md) | Reports the network availability to the network management module. This API uses an asynchronous callback to return the result. |
| [reportNetConnected](arkts-network-connection-reportnetconnected-f.md) | Reports that the network is available to the network management module. This API uses a promise to return the result. |
| [reportNetDisconnected](arkts-network-connection-reportnetdisconnected-f.md) | Reports the network unavailability to the network management module. This API uses an asynchronous callback to return the result. |
| [reportNetDisconnected](arkts-network-connection-reportnetdisconnected-f.md) | Reports the network unavailability to the network management module. This API uses a promise to return the result. |
| [setAppHttpProxy](arkts-network-connection-setapphttpproxy-f.md) | Sets the application-level HTTP proxy configuration. |
| [setAppNet](arkts-network-connection-setappnet-f.md) | Binds an application to the network specified by **netHandle**, so that the application can access the external network only through this network. This API uses an asynchronous callback to return the result. |
| [setAppNet](arkts-network-connection-setappnet-f.md) | Binds an application to the network specified by **netHandle**, so that the application can access the external network only through this network. This API uses a promise to return the result. This API uses a promise to return the result. |
| [setNetExtAttribute](arkts-network-connection-setnetextattribute-f.md) | Sets extended attributes of the network specified by **netHandle** to indicate its security level. This API uses a promise to return the result. |
| [setNetExtAttributeSync](arkts-network-connection-setnetextattributesync-f.md) | Sets extended attributes of the network specified by **netHandle** to indicate its security level. This API returns the result synchronously. |
| [setPacFileUrl](arkts-network-connection-setpacfileurl-f.md) | Sets the URL of the Proxy Auto-Configuration Script (PAC) and enables the PAC proxy capability, for example, http:/ /127.0.0.1:21998/PacProxyScript.pac. You can call [findProxyForUrl](arkts-network-connection-findproxyforurl-f.md) to parse the URL and obtain the proxy information. |
| [setPacUrl](arkts-network-connection-setpacurl-f.md) | Sets the URL of the system-level Proxy Auto Config (PAC) script. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addVlanIp](arkts-network-connection-addvlanip-f-sys.md) | Adds a specified IP address and subnet mask for the VLAN specified by **vlanId** on an Ethernet NIC. This API uses a promise to return the result. |
| [createVlanInterface](arkts-network-connection-createvlaninterface-f-sys.md) | Creates a virtual local area network (VLAN) with specified **vlanId** on a specified Ethernet NIC. This API uses a promise to return the result. |
| [deleteVlanIp](arkts-network-connection-deletevlanip-f-sys.md) | Deletes the configured IP address and subnet mask from the VLAN specified by **vlanId** on an Ethernet NIC. This API uses a promise to return the result. |
| [destroyVlanInterface](arkts-network-connection-destroyvlaninterface-f-sys.md) | Deletes a VLAN specified by **vlanId** from a specified Ethernet NIC. This API uses a promise to return the result. |
| [disableAirplaneMode](arkts-network-connection-disableairplanemode-f-sys.md) | Disables airplane mode. This API uses an asynchronous callback to return the result. |
| [disableAirplaneMode](arkts-network-connection-disableairplanemode-f-sys.md) | Disables airplane mode. This API uses a promise to return the result. |
| [enableAirplaneMode](arkts-network-connection-enableairplanemode-f-sys.md) | Enables the airplane mode. This API uses an asynchronous callback to return the result. |
| [enableAirplaneMode](arkts-network-connection-enableairplanemode-f-sys.md) | Enables airplane mode. This API uses a promise to return the result. |
| [factoryReset](arkts-network-connection-factoryreset-f-sys.md) | Resets the network settings to the factory defaults. This API uses a promise to return the result. |
| [getGlobalHttpProxy](arkts-network-connection-getglobalhttpproxy-f-sys.md) | Obtains the global network proxy configuration information. This API uses an asynchronous callback to return the result. |
| [getGlobalHttpProxy](arkts-network-connection-getglobalhttpproxy-f-sys.md) | Obtains the global network proxy configuration information. This API uses a promise to return the result. |
| [getProxyMode](arkts-network-connection-getproxymode-f-sys.md) | Obtains the current proxy mode. This API uses a promise to return the result. |
| [setGlobalHttpProxy](arkts-network-connection-setglobalhttpproxy-f-sys.md) | Sets the global network HTTP proxy configuration information. This API uses an asynchronous callback to return the result. |
| [setGlobalHttpProxy](arkts-network-connection-setglobalhttpproxy-f-sys.md) | Sets the global network HTTP proxy configuration information. This API uses a promise to return the result. |
| [setInterfaceUp](arkts-network-connection-setinterfaceup-f-sys.md) | Set a specific interface up. |
| [setProxyMode](arkts-network-connection-setproxymode-f-sys.md) | Sets the proxy mode. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [ConnectionProperties](arkts-network-connection-connectionproperties-i.md) | Defines the network connection properties. |
| [HttpProxy](arkts-network-connection-httpproxy-i.md) | Represents the HTTP proxy configuration. |
| [LinkAddress](arkts-network-connection-linkaddress-i.md) | Defines network link information. |
| [NetAddress](arkts-network-connection-netaddress-i.md) | Defines a network address. |
| [NetBlockStatusInfo](arkts-network-connection-netblockstatusinfo-i.md) | Obtains the network block status information. |
| [NetCapabilities](arkts-network-connection-netcapabilities-i.md) | Defines the network capability set. |
| [NetCapabilityInfo](arkts-network-connection-netcapabilityinfo-i.md) | Provides an instance that bears data network capabilities. |
| [NetConnection](arkts-network-connection-netconnection-i.md) | Represents the network connection object type. |
| [NetConnectionPropertyInfo](arkts-network-connection-netconnectionpropertyinfo-i.md) | Defines the network connection properties. |
| [NetHandle](arkts-network-connection-nethandle-i.md) | Represents the network handle. |
| [NetIpMacInfo](arkts-network-connection-netipmacinfo-i.md) | Defines information about entries in the IP neighbor table. |
| [NetPortStatesInfo](arkts-network-connection-netportstatesinfo-i.md) | Describes the information about the TCP and UDP ports that are currently listened for by the system. |
| [NetSpecifier](arkts-network-connection-netspecifier-i.md) | Provides an instance that bears data network capabilities. |
| [ProbeResultInfo](arkts-network-connection-proberesultinfo-i.md) | Defines the network probe result information. |
| [QueryOptions](arkts-network-connection-queryoptions-i.md) | Defines the type of the IP address to be queried. |
| [RouteInfo](arkts-network-connection-routeinfo-i.md) | Defines network route information. |
| [Socks5Proxy](arkts-network-connection-socks5proxy-i.md) | Socks5 Proxy Configuration Information. |
| [TcpNetPortStatesInfo](arkts-network-connection-tcpnetportstatesinfo-i.md) | Describes the TCP port state information. |
| [TraceRouteInfo](arkts-network-connection-tracerouteinfo-i.md) | Defines the route tracing information. |
| [TraceRouteOptions](arkts-network-connection-tracerouteoptions-i.md) | Defines options for route tracing. |
| [UdpNetPortStatesInfo](arkts-network-connection-udpnetportstatesinfo-i.md) | Describes the UDP port state information. |

### Enums

| Name | Description |
| --- | --- |
| [ConversionProcess](arkts-network-connection-conversionprocess-e.md) | Enumerates the parameters of the ASCII/Unicode transcoding process. |
| [FamilyType](arkts-network-connection-familytype-e.md) | Indicates the type of the IP address to be queried. |
| [NetBearType](arkts-network-connection-netbeartype-e.md) | Enumerates network types. |
| [NetCap](arkts-network-connection-netcap-e.md) | Defines the network capability. |
| [PacketsType](arkts-network-connection-packetstype-e.md) | Defines the type of network probe data packets. |
| [ProtocolType](arkts-network-connection-protocoltype-e.md) | Enumerates network protocol types. |
| [Socks5DnsStrategy](arkts-network-connection-socks5dnsstrategy-e.md) | Socks5 DNS strategy |
| [TcpState](arkts-network-connection-tcpstate-e.md) | Enumerates TCP states. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ProxyMode](arkts-network-connection-proxymode-e-sys.md) | Enumerates the proxy modes. This API uses a promise to return the result. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [HttpRequest](arkts-network-connection-httprequest-t.md) | Defines an HTTP request, which can be created using [http.createHttp](arkts-network-http-createhttp-f.md). |
| [TCPSocket](arkts-network-connection-tcpsocket-t.md) | Defines a TCPSocket object, which can be created using [socket.constructTCPSocketInstance](arkts-network-socket-constructtcpsocketinstance-f.md). |
| [UDPSocket](arkts-network-connection-udpsocket-t.md) | Defines a **UDPSocket** object, which can be created using [socket.constructUDPSocketInstance](arkts-network-socket-constructudpsocketinstance-f.md). |
