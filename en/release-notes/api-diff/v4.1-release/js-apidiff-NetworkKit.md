| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: global;<br>API declaration: export default class VpnExtensionAbility<br>Differences: export default class VpnExtensionAbility|api/@ohos.app.ability.VpnExtensionAbility.d.ts|
|New API |NA|Class name: VpnExtensionAbility;<br>API declaration: context: VpnExtensionContext;<br>Differences: context: VpnExtensionContext;|api/@ohos.app.ability.VpnExtensionAbility.d.ts|
|New API |NA|Class name: VpnExtensionAbility;<br>API declaration: onCreate(want: Want): void;<br>Differences: onCreate(want: Want): void;|api/@ohos.app.ability.VpnExtensionAbility.d.ts|
|New API |NA|Class name: VpnExtensionAbility;<br>API declaration: onDestroy(): void;<br>Differences: onDestroy(): void;|api/@ohos.app.ability.VpnExtensionAbility.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace connection<br>Differences: declare namespace connection|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: type HttpRequest = http.HttpRequest;<br>Differences: type HttpRequest = http.HttpRequest;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: type TCPSocket = socket.TCPSocket;<br>Differences: type TCPSocket = socket.TCPSocket;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: type UDPSocket = socket.UDPSocket;<br>Differences: type UDPSocket = socket.UDPSocket;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function createNetConnection(netSpecifier?: NetSpecifier, timeout?: number): NetConnection;<br>Differences: function createNetConnection(netSpecifier?: NetSpecifier, timeout?: number): NetConnection;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getDefaultNet(callback: AsyncCallback\<NetHandle>): void;<br>Differences: function getDefaultNet(callback: AsyncCallback\<NetHandle>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getDefaultNet(): Promise\<NetHandle>;<br>Differences: function getDefaultNet(): Promise\<NetHandle>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getDefaultNetSync(): NetHandle;<br>Differences: function getDefaultNetSync(): NetHandle;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getAllNets(callback: AsyncCallback\<Array\<NetHandle>>): void;<br>Differences: function getAllNets(callback: AsyncCallback\<Array\<NetHandle>>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getAllNets(): Promise\<Array\<NetHandle>>;<br>Differences: function getAllNets(): Promise\<Array\<NetHandle>>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getAllNetsSync(): Array\<NetHandle>;<br>Differences: function getAllNetsSync(): Array\<NetHandle>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getConnectionProperties(netHandle: NetHandle, callback: AsyncCallback\<ConnectionProperties>): void;<br>Differences: function getConnectionProperties(netHandle: NetHandle, callback: AsyncCallback\<ConnectionProperties>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getConnectionProperties(netHandle: NetHandle): Promise\<ConnectionProperties>;<br>Differences: function getConnectionProperties(netHandle: NetHandle): Promise\<ConnectionProperties>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getConnectionPropertiesSync(netHandle: NetHandle): ConnectionProperties;<br>Differences: function getConnectionPropertiesSync(netHandle: NetHandle): ConnectionProperties;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getNetCapabilities(netHandle: NetHandle, callback: AsyncCallback\<NetCapabilities>): void;<br>Differences: function getNetCapabilities(netHandle: NetHandle, callback: AsyncCallback\<NetCapabilities>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getNetCapabilities(netHandle: NetHandle): Promise\<NetCapabilities>;<br>Differences: function getNetCapabilities(netHandle: NetHandle): Promise\<NetCapabilities>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getNetCapabilitiesSync(netHandle: NetHandle): NetCapabilities;<br>Differences: function getNetCapabilitiesSync(netHandle: NetHandle): NetCapabilities;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function isDefaultNetMetered(callback: AsyncCallback\<boolean>): void;<br>Differences: function isDefaultNetMetered(callback: AsyncCallback\<boolean>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function isDefaultNetMetered(): Promise\<boolean>;<br>Differences: function isDefaultNetMetered(): Promise\<boolean>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function isDefaultNetMeteredSync(): boolean;<br>Differences: function isDefaultNetMeteredSync(): boolean;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function hasDefaultNet(callback: AsyncCallback\<boolean>): void;<br>Differences: function hasDefaultNet(callback: AsyncCallback\<boolean>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function hasDefaultNet(): Promise\<boolean>;<br>Differences: function hasDefaultNet(): Promise\<boolean>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function hasDefaultNetSync(): boolean;<br>Differences: function hasDefaultNetSync(): boolean;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function reportNetConnected(netHandle: NetHandle, callback: AsyncCallback\<void>): void;<br>Differences: function reportNetConnected(netHandle: NetHandle, callback: AsyncCallback\<void>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function reportNetConnected(netHandle: NetHandle): Promise\<void>;<br>Differences: function reportNetConnected(netHandle: NetHandle): Promise\<void>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function reportNetDisconnected(netHandle: NetHandle, callback: AsyncCallback\<void>): void;<br>Differences: function reportNetDisconnected(netHandle: NetHandle, callback: AsyncCallback\<void>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function reportNetDisconnected(netHandle: NetHandle): Promise\<void>;<br>Differences: function reportNetDisconnected(netHandle: NetHandle): Promise\<void>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getAddressesByName(host: string, callback: AsyncCallback\<Array\<NetAddress>>): void;<br>Differences: function getAddressesByName(host: string, callback: AsyncCallback\<Array\<NetAddress>>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getAddressesByName(host: string): Promise\<Array\<NetAddress>>;<br>Differences: function getAddressesByName(host: string): Promise\<Array\<NetAddress>>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getAppNet(callback: AsyncCallback\<NetHandle>): void;<br>Differences: function getAppNet(callback: AsyncCallback\<NetHandle>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getAppNet(): Promise\<NetHandle>;<br>Differences: function getAppNet(): Promise\<NetHandle>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getAppNetSync(): NetHandle;<br>Differences: function getAppNetSync(): NetHandle;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function setAppNet(netHandle: NetHandle, callback: AsyncCallback\<void>): void;<br>Differences: function setAppNet(netHandle: NetHandle, callback: AsyncCallback\<void>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function setAppNet(netHandle: NetHandle): Promise\<void>;<br>Differences: function setAppNet(netHandle: NetHandle): Promise\<void>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getDefaultHttpProxy(callback: AsyncCallback\<HttpProxy>): void;<br>Differences: function getDefaultHttpProxy(callback: AsyncCallback\<HttpProxy>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function getDefaultHttpProxy(): Promise\<HttpProxy>;<br>Differences: function getDefaultHttpProxy(): Promise\<HttpProxy>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function setAppHttpProxy(httpProxy: HttpProxy): void;<br>Differences: function setAppHttpProxy(httpProxy: HttpProxy): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function addCustomDnsRule(host: string, ip: Array\<string>, callback: AsyncCallback\<void>): void;<br>Differences: function addCustomDnsRule(host: string, ip: Array\<string>, callback: AsyncCallback\<void>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function addCustomDnsRule(host: string, ip: Array\<string>): Promise\<void>;<br>Differences: function addCustomDnsRule(host: string, ip: Array\<string>): Promise\<void>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function removeCustomDnsRule(host: string, callback: AsyncCallback\<void>): void;<br>Differences: function removeCustomDnsRule(host: string, callback: AsyncCallback\<void>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function removeCustomDnsRule(host: string): Promise\<void>;<br>Differences: function removeCustomDnsRule(host: string): Promise\<void>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function clearCustomDnsRules(callback: AsyncCallback\<void>): void;<br>Differences: function clearCustomDnsRules(callback: AsyncCallback\<void>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: function clearCustomDnsRules(): Promise\<void>;<br>Differences: function clearCustomDnsRules(): Promise\<void>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: export interface NetConnection<br>Differences: export interface NetConnection|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetConnection;<br>API declaration: on(type: 'netAvailable', callback: Callback\<NetHandle>): void;<br>Differences: on(type: 'netAvailable', callback: Callback\<NetHandle>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetConnection;<br>API declaration: on(type: 'netBlockStatusChange', callback: Callback\<NetBlockStatusInfo>): void;<br>Differences: on(type: 'netBlockStatusChange', callback: Callback\<NetBlockStatusInfo>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetConnection;<br>API declaration: on(type: 'netCapabilitiesChange', callback: Callback\<NetCapabilityInfo>): void;<br>Differences: on(type: 'netCapabilitiesChange', callback: Callback\<NetCapabilityInfo>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetConnection;<br>API declaration: on(type: 'netConnectionPropertiesChange', callback: Callback\<NetConnectionPropertyInfo>): void;<br>Differences: on(type: 'netConnectionPropertiesChange', callback: Callback\<NetConnectionPropertyInfo>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetConnection;<br>API declaration: on(type: 'netLost', callback: Callback\<NetHandle>): void;<br>Differences: on(type: 'netLost', callback: Callback\<NetHandle>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetConnection;<br>API declaration: on(type: 'netUnavailable', callback: Callback\<void>): void;<br>Differences: on(type: 'netUnavailable', callback: Callback\<void>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetConnection;<br>API declaration: register(callback: AsyncCallback\<void>): void;<br>Differences: register(callback: AsyncCallback\<void>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetConnection;<br>API declaration: unregister(callback: AsyncCallback\<void>): void;<br>Differences: unregister(callback: AsyncCallback\<void>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: export interface NetSpecifier<br>Differences: export interface NetSpecifier|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetSpecifier;<br>API declaration: netCapabilities: NetCapabilities;<br>Differences: netCapabilities: NetCapabilities;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetSpecifier;<br>API declaration: bearerPrivateIdentifier?: string;<br>Differences: bearerPrivateIdentifier?: string;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: export interface NetCapabilityInfo<br>Differences: export interface NetCapabilityInfo|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetCapabilityInfo;<br>API declaration: netHandle: NetHandle;<br>Differences: netHandle: NetHandle;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetCapabilityInfo;<br>API declaration: netCap: NetCapabilities;<br>Differences: netCap: NetCapabilities;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: export interface NetHandle<br>Differences: export interface NetHandle|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetHandle;<br>API declaration: netId: number;<br>Differences: netId: number;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetHandle;<br>API declaration: bindSocket(socketParam: TCPSocket \| UDPSocket, callback: AsyncCallback\<void>): void;<br>Differences: bindSocket(socketParam: TCPSocket \| UDPSocket, callback: AsyncCallback\<void>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetHandle;<br>API declaration: bindSocket(socketParam: TCPSocket \| UDPSocket): Promise\<void>;<br>Differences: bindSocket(socketParam: TCPSocket \| UDPSocket): Promise\<void>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetHandle;<br>API declaration: getAddressesByName(host: string, callback: AsyncCallback\<Array\<NetAddress>>): void;<br>Differences: getAddressesByName(host: string, callback: AsyncCallback\<Array\<NetAddress>>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetHandle;<br>API declaration: getAddressesByName(host: string): Promise\<Array\<NetAddress>>;<br>Differences: getAddressesByName(host: string): Promise\<Array\<NetAddress>>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetHandle;<br>API declaration: getAddressByName(host: string, callback: AsyncCallback\<NetAddress>): void;<br>Differences: getAddressByName(host: string, callback: AsyncCallback\<NetAddress>): void;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetHandle;<br>API declaration: getAddressByName(host: string): Promise\<NetAddress>;<br>Differences: getAddressByName(host: string): Promise\<NetAddress>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: export interface NetCapabilities<br>Differences: export interface NetCapabilities|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetCapabilities;<br>API declaration: linkUpBandwidthKbps?: number;<br>Differences: linkUpBandwidthKbps?: number;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetCapabilities;<br>API declaration: linkDownBandwidthKbps?: number;<br>Differences: linkDownBandwidthKbps?: number;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetCapabilities;<br>API declaration: networkCap?: Array\<NetCap>;<br>Differences: networkCap?: Array\<NetCap>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetCapabilities;<br>API declaration: bearerTypes: Array\<NetBearType>;<br>Differences: bearerTypes: Array\<NetBearType>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: export interface NetConnectionPropertyInfo<br>Differences: export interface NetConnectionPropertyInfo|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetConnectionPropertyInfo;<br>API declaration: netHandle: NetHandle;<br>Differences: netHandle: NetHandle;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetConnectionPropertyInfo;<br>API declaration: connectionProperties: ConnectionProperties;<br>Differences: connectionProperties: ConnectionProperties;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: export interface NetBlockStatusInfo<br>Differences: export interface NetBlockStatusInfo|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetBlockStatusInfo;<br>API declaration: netHandle: NetHandle;<br>Differences: netHandle: NetHandle;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetBlockStatusInfo;<br>API declaration: blocked: boolean;<br>Differences: blocked: boolean;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: export enum NetCap<br>Differences: export enum NetCap|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetCap;<br>API declaration: NET_CAPABILITY_MMS = 0<br>Differences: NET_CAPABILITY_MMS = 0|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetCap;<br>API declaration: NET_CAPABILITY_NOT_METERED = 11<br>Differences: NET_CAPABILITY_NOT_METERED = 11|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetCap;<br>API declaration: NET_CAPABILITY_INTERNET = 12<br>Differences: NET_CAPABILITY_INTERNET = 12|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetCap;<br>API declaration: NET_CAPABILITY_NOT_VPN = 15<br>Differences: NET_CAPABILITY_NOT_VPN = 15|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetCap;<br>API declaration: NET_CAPABILITY_VALIDATED = 16<br>Differences: NET_CAPABILITY_VALIDATED = 16|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: export enum NetBearType<br>Differences: export enum NetBearType|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetBearType;<br>API declaration: BEARER_CELLULAR = 0<br>Differences: BEARER_CELLULAR = 0|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetBearType;<br>API declaration: BEARER_WIFI = 1<br>Differences: BEARER_WIFI = 1|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetBearType;<br>API declaration: BEARER_ETHERNET = 3<br>Differences: BEARER_ETHERNET = 3|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: export interface ConnectionProperties<br>Differences: export interface ConnectionProperties|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: ConnectionProperties;<br>API declaration: interfaceName: string;<br>Differences: interfaceName: string;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: ConnectionProperties;<br>API declaration: domains: string;<br>Differences: domains: string;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: ConnectionProperties;<br>API declaration: linkAddresses: Array\<LinkAddress>;<br>Differences: linkAddresses: Array\<LinkAddress>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: ConnectionProperties;<br>API declaration: dnses: Array\<NetAddress>;<br>Differences: dnses: Array\<NetAddress>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: ConnectionProperties;<br>API declaration: routes: Array\<RouteInfo>;<br>Differences: routes: Array\<RouteInfo>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: ConnectionProperties;<br>API declaration: mtu: number;<br>Differences: mtu: number;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: export interface RouteInfo<br>Differences: export interface RouteInfo|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: RouteInfo;<br>API declaration: interface: string;<br>Differences: interface: string;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: RouteInfo;<br>API declaration: destination: LinkAddress;<br>Differences: destination: LinkAddress;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: RouteInfo;<br>API declaration: gateway: NetAddress;<br>Differences: gateway: NetAddress;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: RouteInfo;<br>API declaration: hasGateway: boolean;<br>Differences: hasGateway: boolean;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: RouteInfo;<br>API declaration: isDefaultRoute: boolean;<br>Differences: isDefaultRoute: boolean;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: export interface LinkAddress<br>Differences: export interface LinkAddress|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: LinkAddress;<br>API declaration: address: NetAddress;<br>Differences: address: NetAddress;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: LinkAddress;<br>API declaration: prefixLength: number;<br>Differences: prefixLength: number;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: export interface NetAddress<br>Differences: export interface NetAddress|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetAddress;<br>API declaration: address: string;<br>Differences: address: string;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetAddress;<br>API declaration: family?: number;<br>Differences: family?: number;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: NetAddress;<br>API declaration: port?: number;<br>Differences: port?: number;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: connection;<br>API declaration: export interface HttpProxy<br>Differences: export interface HttpProxy|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: HttpProxy;<br>API declaration: host: string;<br>Differences: host: string;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: HttpProxy;<br>API declaration: port: number;<br>Differences: port: number;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: HttpProxy;<br>API declaration: exclusionList: Array\<string>;<br>Differences: exclusionList: Array\<string>;|api/@ohos.net.connection.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace ethernet<br>Differences: declare namespace ethernet|api/@ohos.net.ethernet.d.ts|
|New API |NA|Class name: ethernet;<br>API declaration: type HttpProxy = connection.HttpProxy;<br>Differences: type HttpProxy = connection.HttpProxy;|api/@ohos.net.ethernet.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace http<br>Differences: declare namespace http|api/@ohos.net.http.d.ts|
|New API |NA|Class name: http;<br>API declaration: type HttpProxy = connection.HttpProxy;<br>Differences: type HttpProxy = connection.HttpProxy;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: http;<br>API declaration: function createHttp(): HttpRequest;<br>Differences: function createHttp(): HttpRequest;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: http;<br>API declaration: export interface HttpRequestOptions<br>Differences: export interface HttpRequestOptions|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequestOptions;<br>API declaration: method?: RequestMethod;<br>Differences: method?: RequestMethod;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequestOptions;<br>API declaration: extraData?: string \| Object \| ArrayBuffer;<br>Differences: extraData?: string \| Object \| ArrayBuffer;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequestOptions;<br>API declaration: expectDataType?: HttpDataType;<br>Differences: expectDataType?: HttpDataType;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequestOptions;<br>API declaration: usingCache?: boolean;<br>Differences: usingCache?: boolean;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequestOptions;<br>API declaration: priority?: number;<br>Differences: priority?: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequestOptions;<br>API declaration: header?: Object;<br>Differences: header?: Object;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequestOptions;<br>API declaration: readTimeout?: number;<br>Differences: readTimeout?: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequestOptions;<br>API declaration: connectTimeout?: number;<br>Differences: connectTimeout?: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequestOptions;<br>API declaration: usingProtocol?: HttpProtocol;<br>Differences: usingProtocol?: HttpProtocol;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequestOptions;<br>API declaration: usingProxy?: boolean \| HttpProxy;<br>Differences: usingProxy?: boolean \| HttpProxy;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequestOptions;<br>API declaration: caPath?: string;<br>Differences: caPath?: string;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequestOptions;<br>API declaration: resumeFrom?: number;<br>Differences: resumeFrom?: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequestOptions;<br>API declaration: resumeTo?: number;<br>Differences: resumeTo?: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequestOptions;<br>API declaration: clientCert?: ClientCert;<br>Differences: clientCert?: ClientCert;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequestOptions;<br>API declaration: dnsOverHttps?: string;<br>Differences: dnsOverHttps?: string;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequestOptions;<br>API declaration: dnsServers?: Array\<string>;<br>Differences: dnsServers?: Array\<string>;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequestOptions;<br>API declaration: maxLimit?: number;<br>Differences: maxLimit?: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequestOptions;<br>API declaration: multiFormDataList?: Array\<MultiFormData>;<br>Differences: multiFormDataList?: Array\<MultiFormData>;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: http;<br>API declaration: export interface MultiFormData<br>Differences: export interface MultiFormData|api/@ohos.net.http.d.ts|
|New API |NA|Class name: MultiFormData;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: MultiFormData;<br>API declaration: contentType: string;<br>Differences: contentType: string;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: MultiFormData;<br>API declaration: remoteFileName?: string;<br>Differences: remoteFileName?: string;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: MultiFormData;<br>API declaration: data?: string \| Object \| ArrayBuffer;<br>Differences: data?: string \| Object \| ArrayBuffer;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: MultiFormData;<br>API declaration: filePath?: string;<br>Differences: filePath?: string;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: http;<br>API declaration: export enum CertType<br>Differences: export enum CertType|api/@ohos.net.http.d.ts|
|New API |NA|Class name: CertType;<br>API declaration: PEM = 'PEM'<br>Differences: PEM = 'PEM'|api/@ohos.net.http.d.ts|
|New API |NA|Class name: CertType;<br>API declaration: DER = 'DER'<br>Differences: DER = 'DER'|api/@ohos.net.http.d.ts|
|New API |NA|Class name: CertType;<br>API declaration: P12 = 'P12'<br>Differences: P12 = 'P12'|api/@ohos.net.http.d.ts|
|New API |NA|Class name: http;<br>API declaration: export interface ClientCert<br>Differences: export interface ClientCert|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ClientCert;<br>API declaration: certPath: string;<br>Differences: certPath: string;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ClientCert;<br>API declaration: certType?: CertType;<br>Differences: certType?: CertType;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ClientCert;<br>API declaration: keyPath: string;<br>Differences: keyPath: string;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ClientCert;<br>API declaration: keyPassword?: string;<br>Differences: keyPassword?: string;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: http;<br>API declaration: export interface HttpRequest<br>Differences: export interface HttpRequest|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: request(url: string, callback: AsyncCallback\<HttpResponse>): void;<br>Differences: request(url: string, callback: AsyncCallback\<HttpResponse>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: request(url: string, options: HttpRequestOptions, callback: AsyncCallback\<HttpResponse>): void;<br>Differences: request(url: string, options: HttpRequestOptions, callback: AsyncCallback\<HttpResponse>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: request(url: string, options?: HttpRequestOptions): Promise\<HttpResponse>;<br>Differences: request(url: string, options?: HttpRequestOptions): Promise\<HttpResponse>;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: requestInStream(url: string, callback: AsyncCallback\<number>): void;<br>Differences: requestInStream(url: string, callback: AsyncCallback\<number>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number>): void;<br>Differences: requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: requestInStream(url: string, options?: HttpRequestOptions): Promise\<number>;<br>Differences: requestInStream(url: string, options?: HttpRequestOptions): Promise\<number>;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: destroy(): void;<br>Differences: destroy(): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: on(type: "headerReceive", callback: AsyncCallback\<Object>): void;<br>Differences: on(type: "headerReceive", callback: AsyncCallback\<Object>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: off(type: "headerReceive", callback?: AsyncCallback\<Object>): void;<br>Differences: off(type: "headerReceive", callback?: AsyncCallback\<Object>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: on(type: "headersReceive", callback: Callback\<Object>): void;<br>Differences: on(type: "headersReceive", callback: Callback\<Object>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: off(type: "headersReceive", callback?: Callback\<Object>): void;<br>Differences: off(type: "headersReceive", callback?: Callback\<Object>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: once(type: "headersReceive", callback: Callback\<Object>): void;<br>Differences: once(type: "headersReceive", callback: Callback\<Object>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: on(type: "dataReceive", callback: Callback\<ArrayBuffer>): void;<br>Differences: on(type: "dataReceive", callback: Callback\<ArrayBuffer>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: off(type: "dataReceive", callback?: Callback\<ArrayBuffer>): void;<br>Differences: off(type: "dataReceive", callback?: Callback\<ArrayBuffer>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: on(type: "dataEnd", callback: Callback\<void>): void;<br>Differences: on(type: "dataEnd", callback: Callback\<void>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: off(type: "dataEnd", callback?: Callback\<void>): void;<br>Differences: off(type: "dataEnd", callback?: Callback\<void>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: on(type: 'dataReceiveProgress', callback: Callback\<DataReceiveProgressInfo>): void;<br>Differences: on(type: 'dataReceiveProgress', callback: Callback\<DataReceiveProgressInfo>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: off(type: 'dataReceiveProgress', callback?: Callback\<DataReceiveProgressInfo>): void;<br>Differences: off(type: 'dataReceiveProgress', callback?: Callback\<DataReceiveProgressInfo>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: on(type: 'dataSendProgress', callback: Callback\<DataSendProgressInfo>): void;<br>Differences: on(type: 'dataSendProgress', callback: Callback\<DataSendProgressInfo>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpRequest;<br>API declaration: off(type: 'dataSendProgress', callback?: Callback\<DataSendProgressInfo>): void;<br>Differences: off(type: 'dataSendProgress', callback?: Callback\<DataSendProgressInfo>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: http;<br>API declaration: export enum RequestMethod<br>Differences: export enum RequestMethod|api/@ohos.net.http.d.ts|
|New API |NA|Class name: RequestMethod;<br>API declaration: OPTIONS = "OPTIONS"<br>Differences: OPTIONS = "OPTIONS"|api/@ohos.net.http.d.ts|
|New API |NA|Class name: RequestMethod;<br>API declaration: GET = "GET"<br>Differences: GET = "GET"|api/@ohos.net.http.d.ts|
|New API |NA|Class name: RequestMethod;<br>API declaration: HEAD = "HEAD"<br>Differences: HEAD = "HEAD"|api/@ohos.net.http.d.ts|
|New API |NA|Class name: RequestMethod;<br>API declaration: POST = "POST"<br>Differences: POST = "POST"|api/@ohos.net.http.d.ts|
|New API |NA|Class name: RequestMethod;<br>API declaration: PUT = "PUT"<br>Differences: PUT = "PUT"|api/@ohos.net.http.d.ts|
|New API |NA|Class name: RequestMethod;<br>API declaration: DELETE = "DELETE"<br>Differences: DELETE = "DELETE"|api/@ohos.net.http.d.ts|
|New API |NA|Class name: RequestMethod;<br>API declaration: TRACE = "TRACE"<br>Differences: TRACE = "TRACE"|api/@ohos.net.http.d.ts|
|New API |NA|Class name: RequestMethod;<br>API declaration: CONNECT = "CONNECT"<br>Differences: CONNECT = "CONNECT"|api/@ohos.net.http.d.ts|
|New API |NA|Class name: http;<br>API declaration: export enum ResponseCode<br>Differences: export enum ResponseCode|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: OK = 200<br>Differences: OK = 200|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: CREATED<br>Differences: CREATED|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: ACCEPTED<br>Differences: ACCEPTED|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: NOT_AUTHORITATIVE<br>Differences: NOT_AUTHORITATIVE|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: NO_CONTENT<br>Differences: NO_CONTENT|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: RESET<br>Differences: RESET|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: PARTIAL<br>Differences: PARTIAL|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: MULT_CHOICE = 300<br>Differences: MULT_CHOICE = 300|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: MOVED_PERM<br>Differences: MOVED_PERM|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: MOVED_TEMP<br>Differences: MOVED_TEMP|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: SEE_OTHER<br>Differences: SEE_OTHER|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: NOT_MODIFIED<br>Differences: NOT_MODIFIED|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: USE_PROXY<br>Differences: USE_PROXY|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: BAD_REQUEST = 400<br>Differences: BAD_REQUEST = 400|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: UNAUTHORIZED<br>Differences: UNAUTHORIZED|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: PAYMENT_REQUIRED<br>Differences: PAYMENT_REQUIRED|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: FORBIDDEN<br>Differences: FORBIDDEN|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: NOT_FOUND<br>Differences: NOT_FOUND|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: BAD_METHOD<br>Differences: BAD_METHOD|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: NOT_ACCEPTABLE<br>Differences: NOT_ACCEPTABLE|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: PROXY_AUTH<br>Differences: PROXY_AUTH|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: CLIENT_TIMEOUT<br>Differences: CLIENT_TIMEOUT|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: CONFLICT<br>Differences: CONFLICT|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: GONE<br>Differences: GONE|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: LENGTH_REQUIRED<br>Differences: LENGTH_REQUIRED|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: PRECON_FAILED<br>Differences: PRECON_FAILED|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: ENTITY_TOO_LARGE<br>Differences: ENTITY_TOO_LARGE|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: REQ_TOO_LONG<br>Differences: REQ_TOO_LONG|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: UNSUPPORTED_TYPE<br>Differences: UNSUPPORTED_TYPE|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: INTERNAL_ERROR = 500<br>Differences: INTERNAL_ERROR = 500|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: NOT_IMPLEMENTED<br>Differences: NOT_IMPLEMENTED|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: BAD_GATEWAY<br>Differences: BAD_GATEWAY|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: UNAVAILABLE<br>Differences: UNAVAILABLE|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: GATEWAY_TIMEOUT<br>Differences: GATEWAY_TIMEOUT|api/@ohos.net.http.d.ts|
|New API |NA|Class name: ResponseCode;<br>API declaration: VERSION<br>Differences: VERSION|api/@ohos.net.http.d.ts|
|New API |NA|Class name: http;<br>API declaration: export enum HttpProtocol<br>Differences: export enum HttpProtocol|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpProtocol;<br>API declaration: HTTP1_1<br>Differences: HTTP1_1|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpProtocol;<br>API declaration: HTTP2<br>Differences: HTTP2|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpProtocol;<br>API declaration: HTTP3<br>Differences: HTTP3|api/@ohos.net.http.d.ts|
|New API |NA|Class name: http;<br>API declaration: export enum HttpDataType<br>Differences: export enum HttpDataType|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpDataType;<br>API declaration: STRING<br>Differences: STRING|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpDataType;<br>API declaration: OBJECT = 1<br>Differences: OBJECT = 1|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpDataType;<br>API declaration: ARRAY_BUFFER = 2<br>Differences: ARRAY_BUFFER = 2|api/@ohos.net.http.d.ts|
|New API |NA|Class name: http;<br>API declaration: export interface HttpResponse<br>Differences: export interface HttpResponse|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpResponse;<br>API declaration: result: string \| Object \| ArrayBuffer;<br>Differences: result: string \| Object \| ArrayBuffer;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpResponse;<br>API declaration: resultType: HttpDataType;<br>Differences: resultType: HttpDataType;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpResponse;<br>API declaration: responseCode: ResponseCode \| number;<br>Differences: responseCode: ResponseCode \| number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpResponse;<br>API declaration: header: Object;<br>Differences: header: Object;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpResponse;<br>API declaration: cookies: string;<br>Differences: cookies: string;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpResponse;<br>API declaration: performanceTiming: PerformanceTiming;<br>Differences: performanceTiming: PerformanceTiming;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: http;<br>API declaration: export interface PerformanceTiming<br>Differences: export interface PerformanceTiming|api/@ohos.net.http.d.ts|
|New API |NA|Class name: PerformanceTiming;<br>API declaration: dnsTiming: number;<br>Differences: dnsTiming: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: PerformanceTiming;<br>API declaration: tcpTiming: number;<br>Differences: tcpTiming: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: PerformanceTiming;<br>API declaration: tlsTiming: number;<br>Differences: tlsTiming: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: PerformanceTiming;<br>API declaration: firstSendTiming: number;<br>Differences: firstSendTiming: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: PerformanceTiming;<br>API declaration: firstReceiveTiming: number;<br>Differences: firstReceiveTiming: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: PerformanceTiming;<br>API declaration: totalFinishTiming: number;<br>Differences: totalFinishTiming: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: PerformanceTiming;<br>API declaration: redirectTiming: number;<br>Differences: redirectTiming: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: PerformanceTiming;<br>API declaration: responseHeaderTiming: number;<br>Differences: responseHeaderTiming: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: PerformanceTiming;<br>API declaration: responseBodyTiming: number;<br>Differences: responseBodyTiming: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: PerformanceTiming;<br>API declaration: totalTiming: number;<br>Differences: totalTiming: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: http;<br>API declaration: export interface DataReceiveProgressInfo<br>Differences: export interface DataReceiveProgressInfo|api/@ohos.net.http.d.ts|
|New API |NA|Class name: DataReceiveProgressInfo;<br>API declaration: receiveSize: number;<br>Differences: receiveSize: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: DataReceiveProgressInfo;<br>API declaration: totalSize: number;<br>Differences: totalSize: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: http;<br>API declaration: export interface DataSendProgressInfo<br>Differences: export interface DataSendProgressInfo|api/@ohos.net.http.d.ts|
|New API |NA|Class name: DataSendProgressInfo;<br>API declaration: sendSize: number;<br>Differences: sendSize: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: DataSendProgressInfo;<br>API declaration: totalSize: number;<br>Differences: totalSize: number;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: http;<br>API declaration: function createHttpResponseCache(cacheSize?: number): HttpResponseCache;<br>Differences: function createHttpResponseCache(cacheSize?: number): HttpResponseCache;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: http;<br>API declaration: export interface HttpResponseCache<br>Differences: export interface HttpResponseCache|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpResponseCache;<br>API declaration: flush(callback: AsyncCallback\<void>): void;<br>Differences: flush(callback: AsyncCallback\<void>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpResponseCache;<br>API declaration: flush(): Promise\<void>;<br>Differences: flush(): Promise\<void>;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpResponseCache;<br>API declaration: delete(callback: AsyncCallback\<void>): void;<br>Differences: delete(callback: AsyncCallback\<void>): void;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: HttpResponseCache;<br>API declaration: delete(): Promise\<void>;<br>Differences: delete(): Promise\<void>;|api/@ohos.net.http.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace mdns<br>Differences: declare namespace mdns|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: mdns;<br>API declaration: type NetAddress = connection.NetAddress;<br>Differences: type NetAddress = connection.NetAddress;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: mdns;<br>API declaration: function addLocalService(context: Context, serviceInfo: LocalServiceInfo, callback: AsyncCallback\<LocalServiceInfo>): void;<br>Differences: function addLocalService(context: Context, serviceInfo: LocalServiceInfo, callback: AsyncCallback\<LocalServiceInfo>): void;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: mdns;<br>API declaration: function addLocalService(context: Context, serviceInfo: LocalServiceInfo): Promise\<LocalServiceInfo>;<br>Differences: function addLocalService(context: Context, serviceInfo: LocalServiceInfo): Promise\<LocalServiceInfo>;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: mdns;<br>API declaration: function removeLocalService(context: Context, serviceInfo: LocalServiceInfo, callback: AsyncCallback\<LocalServiceInfo>): void;<br>Differences: function removeLocalService(context: Context, serviceInfo: LocalServiceInfo, callback: AsyncCallback\<LocalServiceInfo>): void;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: mdns;<br>API declaration: function removeLocalService(context: Context, serviceInfo: LocalServiceInfo): Promise\<LocalServiceInfo>;<br>Differences: function removeLocalService(context: Context, serviceInfo: LocalServiceInfo): Promise\<LocalServiceInfo>;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: mdns;<br>API declaration: function createDiscoveryService(context: Context, serviceType: string): DiscoveryService;<br>Differences: function createDiscoveryService(context: Context, serviceType: string): DiscoveryService;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: mdns;<br>API declaration: function resolveLocalService(context: Context, serviceInfo: LocalServiceInfo, callback: AsyncCallback\<LocalServiceInfo>): void;<br>Differences: function resolveLocalService(context: Context, serviceInfo: LocalServiceInfo, callback: AsyncCallback\<LocalServiceInfo>): void;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: mdns;<br>API declaration: function resolveLocalService(context: Context, serviceInfo: LocalServiceInfo): Promise\<LocalServiceInfo>;<br>Differences: function resolveLocalService(context: Context, serviceInfo: LocalServiceInfo): Promise\<LocalServiceInfo>;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: mdns;<br>API declaration: export interface DiscoveryService<br>Differences: export interface DiscoveryService|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: DiscoveryService;<br>API declaration: on(type: 'discoveryStart', callback: Callback\<DiscoveryEventInfo>): void;<br>Differences: on(type: 'discoveryStart', callback: Callback\<DiscoveryEventInfo>): void;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: DiscoveryService;<br>API declaration: off(type: 'discoveryStart', callback?: Callback\<DiscoveryEventInfo>): void;<br>Differences: off(type: 'discoveryStart', callback?: Callback\<DiscoveryEventInfo>): void;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: DiscoveryService;<br>API declaration: on(type: 'discoveryStop', callback: Callback\<DiscoveryEventInfo>): void;<br>Differences: on(type: 'discoveryStop', callback: Callback\<DiscoveryEventInfo>): void;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: DiscoveryService;<br>API declaration: off(type: 'discoveryStop', callback?: Callback\<DiscoveryEventInfo>): void;<br>Differences: off(type: 'discoveryStop', callback?: Callback\<DiscoveryEventInfo>): void;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: DiscoveryService;<br>API declaration: on(type: 'serviceFound', callback: Callback\<LocalServiceInfo>): void;<br>Differences: on(type: 'serviceFound', callback: Callback\<LocalServiceInfo>): void;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: DiscoveryService;<br>API declaration: off(type: 'serviceFound', callback?: Callback\<LocalServiceInfo>): void;<br>Differences: off(type: 'serviceFound', callback?: Callback\<LocalServiceInfo>): void;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: DiscoveryService;<br>API declaration: on(type: 'serviceLost', callback: Callback\<LocalServiceInfo>): void;<br>Differences: on(type: 'serviceLost', callback: Callback\<LocalServiceInfo>): void;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: DiscoveryService;<br>API declaration: off(type: 'serviceLost', callback?: Callback\<LocalServiceInfo>): void;<br>Differences: off(type: 'serviceLost', callback?: Callback\<LocalServiceInfo>): void;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: DiscoveryService;<br>API declaration: startSearchingMDNS(): void;<br>Differences: startSearchingMDNS(): void;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: DiscoveryService;<br>API declaration: stopSearchingMDNS(): void;<br>Differences: stopSearchingMDNS(): void;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: mdns;<br>API declaration: export interface LocalServiceInfo<br>Differences: export interface LocalServiceInfo|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: LocalServiceInfo;<br>API declaration: serviceType: string;<br>Differences: serviceType: string;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: LocalServiceInfo;<br>API declaration: serviceName: string;<br>Differences: serviceName: string;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: LocalServiceInfo;<br>API declaration: port?: number;<br>Differences: port?: number;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: LocalServiceInfo;<br>API declaration: host?: NetAddress;<br>Differences: host?: NetAddress;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: LocalServiceInfo;<br>API declaration: serviceAttribute?: Array\<ServiceAttribute>;<br>Differences: serviceAttribute?: Array\<ServiceAttribute>;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: mdns;<br>API declaration: export interface ServiceAttribute<br>Differences: export interface ServiceAttribute|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: ServiceAttribute;<br>API declaration: key: string;<br>Differences: key: string;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: ServiceAttribute;<br>API declaration: value: Array\<number>;<br>Differences: value: Array\<number>;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: mdns;<br>API declaration: export interface DiscoveryEventInfo<br>Differences: export interface DiscoveryEventInfo|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: DiscoveryEventInfo;<br>API declaration: serviceInfo: LocalServiceInfo;<br>Differences: serviceInfo: LocalServiceInfo;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: DiscoveryEventInfo;<br>API declaration: errorCode?: MdnsError;<br>Differences: errorCode?: MdnsError;|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: mdns;<br>API declaration: export enum MdnsError<br>Differences: export enum MdnsError|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: MdnsError;<br>API declaration: INTERNAL_ERROR = 0<br>Differences: INTERNAL_ERROR = 0|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: MdnsError;<br>API declaration: ALREADY_ACTIVE = 1<br>Differences: ALREADY_ACTIVE = 1|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: MdnsError;<br>API declaration: MAX_LIMIT = 2<br>Differences: MAX_LIMIT = 2|api/@ohos.net.mdns.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace networkSecurity<br>Differences: declare namespace networkSecurity|api/@ohos.net.networkSecurity.d.ts|
|New API |NA|Class name: networkSecurity;<br>API declaration: export enum CertType<br>Differences: export enum CertType|api/@ohos.net.networkSecurity.d.ts|
|New API |NA|Class name: CertType;<br>API declaration: CERT_TYPE_PEM = 0<br>Differences: CERT_TYPE_PEM = 0|api/@ohos.net.networkSecurity.d.ts|
|New API |NA|Class name: CertType;<br>API declaration: CERT_TYPE_DER = 1<br>Differences: CERT_TYPE_DER = 1|api/@ohos.net.networkSecurity.d.ts|
|New API |NA|Class name: networkSecurity;<br>API declaration: export interface CertBlob<br>Differences: export interface CertBlob|api/@ohos.net.networkSecurity.d.ts|
|New API |NA|Class name: CertBlob;<br>API declaration: type: CertType;<br>Differences: type: CertType;|api/@ohos.net.networkSecurity.d.ts|
|New API |NA|Class name: CertBlob;<br>API declaration: data: string \| ArrayBuffer;<br>Differences: data: string \| ArrayBuffer;|api/@ohos.net.networkSecurity.d.ts|
|New API |NA|Class name: networkSecurity;<br>API declaration: export function certVerification(cert: CertBlob, caCert?: CertBlob): Promise\<number>;<br>Differences: export function certVerification(cert: CertBlob, caCert?: CertBlob): Promise\<number>;|api/@ohos.net.networkSecurity.d.ts|
|New API |NA|Class name: networkSecurity;<br>API declaration: export function certVerificationSync(cert: CertBlob, caCert?: CertBlob): number;<br>Differences: export function certVerificationSync(cert: CertBlob, caCert?: CertBlob): number;|api/@ohos.net.networkSecurity.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace policy<br>Differences: declare namespace policy|api/@ohos.net.policy.d.ts|
|New API |NA|Class name: policy;<br>API declaration: type NetBearType = connection.NetBearType;<br>Differences: type NetBearType = connection.NetBearType;|api/@ohos.net.policy.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace sharing<br>Differences: declare namespace sharing|api/@ohos.net.sharing.d.ts|
|New API |NA|Class name: sharing;<br>API declaration: type NetHandle = connection.NetHandle;<br>Differences: type NetHandle = connection.NetHandle;|api/@ohos.net.sharing.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace socket<br>Differences: declare namespace socket|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export type X509CertRawData = cert.EncodingBlob;<br>Differences: export type X509CertRawData = cert.EncodingBlob;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: function constructUDPSocketInstance(): UDPSocket;<br>Differences: function constructUDPSocketInstance(): UDPSocket;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: function constructMulticastSocketInstance(): MulticastSocket;<br>Differences: function constructMulticastSocketInstance(): MulticastSocket;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: function constructTCPSocketInstance(): TCPSocket;<br>Differences: function constructTCPSocketInstance(): TCPSocket;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: function constructTLSSocketInstance(): TLSSocket;<br>Differences: function constructTLSSocketInstance(): TLSSocket;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: function constructTCPSocketServerInstance(): TCPSocketServer;<br>Differences: function constructTCPSocketServerInstance(): TCPSocketServer;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: function constructTLSSocketServerInstance(): TLSSocketServer;<br>Differences: function constructTLSSocketServerInstance(): TLSSocketServer;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: function constructLocalSocketInstance(): LocalSocket;<br>Differences: function constructLocalSocketInstance(): LocalSocket;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: function constructLocalSocketServerInstance(): LocalSocketServer;<br>Differences: function constructLocalSocketServerInstance(): LocalSocketServer;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface UDPSendOptions<br>Differences: export interface UDPSendOptions|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSendOptions;<br>API declaration: data: string \| ArrayBuffer;<br>Differences: data: string \| ArrayBuffer;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSendOptions;<br>API declaration: address: NetAddress;<br>Differences: address: NetAddress;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface ExtraOptionsBase<br>Differences: export interface ExtraOptionsBase|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: ExtraOptionsBase;<br>API declaration: receiveBufferSize?: number;<br>Differences: receiveBufferSize?: number;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: ExtraOptionsBase;<br>API declaration: sendBufferSize?: number;<br>Differences: sendBufferSize?: number;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: ExtraOptionsBase;<br>API declaration: reuseAddress?: boolean;<br>Differences: reuseAddress?: boolean;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: ExtraOptionsBase;<br>API declaration: socketTimeout?: number;<br>Differences: socketTimeout?: number;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface UDPExtraOptions<br>Differences: export interface UDPExtraOptions|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPExtraOptions;<br>API declaration: broadcast?: boolean;<br>Differences: broadcast?: boolean;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface SocketStateBase<br>Differences: export interface SocketStateBase|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: SocketStateBase;<br>API declaration: isBound: boolean;<br>Differences: isBound: boolean;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: SocketStateBase;<br>API declaration: isClose: boolean;<br>Differences: isClose: boolean;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: SocketStateBase;<br>API declaration: isConnected: boolean;<br>Differences: isConnected: boolean;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface SocketRemoteInfo<br>Differences: export interface SocketRemoteInfo|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: SocketRemoteInfo;<br>API declaration: address: string;<br>Differences: address: string;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: SocketRemoteInfo;<br>API declaration: family: 'IPv4' \| 'IPv6';<br>Differences: family: 'IPv4' \| 'IPv6';|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: SocketRemoteInfo;<br>API declaration: port: number;<br>Differences: port: number;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: SocketRemoteInfo;<br>API declaration: size: number;<br>Differences: size: number;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface LocalSocketMessageInfo<br>Differences: export interface LocalSocketMessageInfo|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketMessageInfo;<br>API declaration: message: ArrayBuffer;<br>Differences: message: ArrayBuffer;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketMessageInfo;<br>API declaration: address: string;<br>Differences: address: string;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketMessageInfo;<br>API declaration: size: number;<br>Differences: size: number;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface LocalAddress<br>Differences: export interface LocalAddress|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalAddress;<br>API declaration: address: string;<br>Differences: address: string;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface LocalConnectOptions<br>Differences: export interface LocalConnectOptions|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalConnectOptions;<br>API declaration: address: LocalAddress;<br>Differences: address: LocalAddress;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalConnectOptions;<br>API declaration: timeout?: number;<br>Differences: timeout?: number;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface LocalSendOptions<br>Differences: export interface LocalSendOptions|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSendOptions;<br>API declaration: data: string \| ArrayBuffer;<br>Differences: data: string \| ArrayBuffer;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSendOptions;<br>API declaration: encoding?: string;<br>Differences: encoding?: string;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface UDPSocket<br>Differences: export interface UDPSocket|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSocket;<br>API declaration: bind(address: NetAddress, callback: AsyncCallback\<void>): void;<br>Differences: bind(address: NetAddress, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSocket;<br>API declaration: bind(address: NetAddress): Promise\<void>;<br>Differences: bind(address: NetAddress): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSocket;<br>API declaration: send(options: UDPSendOptions, callback: AsyncCallback\<void>): void;<br>Differences: send(options: UDPSendOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSocket;<br>API declaration: send(options: UDPSendOptions): Promise\<void>;<br>Differences: send(options: UDPSendOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSocket;<br>API declaration: close(callback: AsyncCallback\<void>): void;<br>Differences: close(callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSocket;<br>API declaration: close(): Promise\<void>;<br>Differences: close(): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSocket;<br>API declaration: getState(callback: AsyncCallback\<SocketStateBase>): void;<br>Differences: getState(callback: AsyncCallback\<SocketStateBase>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSocket;<br>API declaration: getState(): Promise\<SocketStateBase>;<br>Differences: getState(): Promise\<SocketStateBase>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSocket;<br>API declaration: setExtraOptions(options: UDPExtraOptions, callback: AsyncCallback\<void>): void;<br>Differences: setExtraOptions(options: UDPExtraOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSocket;<br>API declaration: setExtraOptions(options: UDPExtraOptions): Promise\<void>;<br>Differences: setExtraOptions(options: UDPExtraOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSocket;<br>API declaration: on(type: 'message', callback: Callback\<SocketMessageInfo>): void;<br>Differences: on(type: 'message', callback: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSocket;<br>API declaration: off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;<br>Differences: off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSocket;<br>API declaration: on(type: 'listening' \| 'close', callback: Callback\<void>): void;<br>Differences: on(type: 'listening' \| 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSocket;<br>API declaration: on(type: 'listening' \| 'close', callback: Callback\<void>): void;<br>Differences: on(type: 'listening' \| 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSocket;<br>API declaration: off(type: 'listening' \| 'close', callback?: Callback\<void>): void;<br>Differences: off(type: 'listening' \| 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSocket;<br>API declaration: off(type: 'listening' \| 'close', callback?: Callback\<void>): void;<br>Differences: off(type: 'listening' \| 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSocket;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: UDPSocket;<br>API declaration: off(type: 'error', callback?: ErrorCallback): void;<br>Differences: off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface MulticastSocket<br>Differences: export interface MulticastSocket|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: MulticastSocket;<br>API declaration: addMembership(multicastAddress: NetAddress, callback: AsyncCallback\<void>): void;<br>Differences: addMembership(multicastAddress: NetAddress, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: MulticastSocket;<br>API declaration: addMembership(multicastAddress: NetAddress): Promise\<void>;<br>Differences: addMembership(multicastAddress: NetAddress): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: MulticastSocket;<br>API declaration: dropMembership(multicastAddress: NetAddress, callback: AsyncCallback\<void>): void;<br>Differences: dropMembership(multicastAddress: NetAddress, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: MulticastSocket;<br>API declaration: dropMembership(multicastAddress: NetAddress): Promise\<void>;<br>Differences: dropMembership(multicastAddress: NetAddress): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: MulticastSocket;<br>API declaration: setMulticastTTL(ttl: number, callback: AsyncCallback\<void>): void;<br>Differences: setMulticastTTL(ttl: number, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: MulticastSocket;<br>API declaration: setMulticastTTL(ttl: number): Promise\<void>;<br>Differences: setMulticastTTL(ttl: number): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: MulticastSocket;<br>API declaration: getMulticastTTL(callback: AsyncCallback\<number>): void;<br>Differences: getMulticastTTL(callback: AsyncCallback\<number>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: MulticastSocket;<br>API declaration: getMulticastTTL(): Promise\<number>;<br>Differences: getMulticastTTL(): Promise\<number>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: MulticastSocket;<br>API declaration: setLoopbackMode(flag: boolean, callback: AsyncCallback\<void>): void;<br>Differences: setLoopbackMode(flag: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: MulticastSocket;<br>API declaration: setLoopbackMode(flag: boolean): Promise\<void>;<br>Differences: setLoopbackMode(flag: boolean): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: MulticastSocket;<br>API declaration: getLoopbackMode(callback: AsyncCallback\<boolean>): void;<br>Differences: getLoopbackMode(callback: AsyncCallback\<boolean>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: MulticastSocket;<br>API declaration: getLoopbackMode(): Promise\<boolean>;<br>Differences: getLoopbackMode(): Promise\<boolean>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface LocalSocket<br>Differences: export interface LocalSocket|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocket;<br>API declaration: bind(address: LocalAddress): Promise\<void>;<br>Differences: bind(address: LocalAddress): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocket;<br>API declaration: connect(options: LocalConnectOptions): Promise\<void>;<br>Differences: connect(options: LocalConnectOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocket;<br>API declaration: send(options: LocalSendOptions): Promise\<void>;<br>Differences: send(options: LocalSendOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocket;<br>API declaration: close(): Promise\<void>;<br>Differences: close(): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocket;<br>API declaration: getState(): Promise\<SocketStateBase>;<br>Differences: getState(): Promise\<SocketStateBase>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocket;<br>API declaration: getSocketFd(): Promise\<number>;<br>Differences: getSocketFd(): Promise\<number>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocket;<br>API declaration: setExtraOptions(options: ExtraOptionsBase): Promise\<void>;<br>Differences: setExtraOptions(options: ExtraOptionsBase): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocket;<br>API declaration: getExtraOptions(): Promise\<ExtraOptionsBase>;<br>Differences: getExtraOptions(): Promise\<ExtraOptionsBase>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocket;<br>API declaration: on(type: 'message', callback: Callback\<LocalSocketMessageInfo>): void;<br>Differences: on(type: 'message', callback: Callback\<LocalSocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocket;<br>API declaration: off(type: 'message', callback?: Callback\<LocalSocketMessageInfo>): void;<br>Differences: off(type: 'message', callback?: Callback\<LocalSocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocket;<br>API declaration: on(type: 'connect', callback: Callback\<void>): void;<br>Differences: on(type: 'connect', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocket;<br>API declaration: off(type: 'connect', callback?: Callback\<void>): void;<br>Differences: off(type: 'connect', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocket;<br>API declaration: on(type: 'close', callback: Callback\<void>): void;<br>Differences: on(type: 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocket;<br>API declaration: off(type: 'close', callback?: Callback\<void>): void;<br>Differences: off(type: 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocket;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocket;<br>API declaration: off(type: 'error', callback?: ErrorCallback): void;<br>Differences: off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface LocalSocketConnection<br>Differences: export interface LocalSocketConnection|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketConnection;<br>API declaration: clientId: number;<br>Differences: clientId: number;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketConnection;<br>API declaration: send(options: LocalSendOptions): Promise\<void>;<br>Differences: send(options: LocalSendOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketConnection;<br>API declaration: close(): Promise\<void>;<br>Differences: close(): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketConnection;<br>API declaration: on(type: 'message', callback: Callback\<LocalSocketMessageInfo>): void;<br>Differences: on(type: 'message', callback: Callback\<LocalSocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketConnection;<br>API declaration: off(type: 'message', callback?: Callback\<LocalSocketMessageInfo>): void;<br>Differences: off(type: 'message', callback?: Callback\<LocalSocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketConnection;<br>API declaration: on(type: 'close', callback: Callback\<void>): void;<br>Differences: on(type: 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketConnection;<br>API declaration: off(type: 'close', callback?: Callback\<void>): void;<br>Differences: off(type: 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketConnection;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketConnection;<br>API declaration: off(type: 'error', callback?: ErrorCallback): void;<br>Differences: off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface LocalSocketServer<br>Differences: export interface LocalSocketServer|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketServer;<br>API declaration: listen(address: LocalAddress): Promise\<void>;<br>Differences: listen(address: LocalAddress): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketServer;<br>API declaration: getState(): Promise\<SocketStateBase>;<br>Differences: getState(): Promise\<SocketStateBase>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketServer;<br>API declaration: setExtraOptions(options: ExtraOptionsBase): Promise\<void>;<br>Differences: setExtraOptions(options: ExtraOptionsBase): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketServer;<br>API declaration: getExtraOptions(): Promise\<ExtraOptionsBase>;<br>Differences: getExtraOptions(): Promise\<ExtraOptionsBase>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketServer;<br>API declaration: on(type: 'connect', callback: Callback\<LocalSocketConnection>): void;<br>Differences: on(type: 'connect', callback: Callback\<LocalSocketConnection>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketServer;<br>API declaration: off(type: 'connect', callback?: Callback\<LocalSocketConnection>): void;<br>Differences: off(type: 'connect', callback?: Callback\<LocalSocketConnection>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketServer;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: LocalSocketServer;<br>API declaration: off(type: 'error', callback?: ErrorCallback): void;<br>Differences: off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface TCPConnectOptions<br>Differences: export interface TCPConnectOptions|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPConnectOptions;<br>API declaration: address: NetAddress;<br>Differences: address: NetAddress;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPConnectOptions;<br>API declaration: timeout?: number;<br>Differences: timeout?: number;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface TCPSendOptions<br>Differences: export interface TCPSendOptions|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSendOptions;<br>API declaration: data: string \| ArrayBuffer;<br>Differences: data: string \| ArrayBuffer;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSendOptions;<br>API declaration: encoding?: string;<br>Differences: encoding?: string;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface TCPExtraOptions<br>Differences: export interface TCPExtraOptions|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPExtraOptions;<br>API declaration: keepAlive?: boolean;<br>Differences: keepAlive?: boolean;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPExtraOptions;<br>API declaration: OOBInline?: boolean;<br>Differences: OOBInline?: boolean;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPExtraOptions;<br>API declaration: TCPNoDelay?: boolean;<br>Differences: TCPNoDelay?: boolean;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPExtraOptions;<br>API declaration: socketLinger?: {<br>            on: boolean;<br>            linger: number;<br>        };<br>Differences: socketLinger?: {<br>            on: boolean;<br>            linger: number;<br>        };|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface TCPSocket<br>Differences: export interface TCPSocket|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: bind(address: NetAddress, callback: AsyncCallback\<void>): void;<br>Differences: bind(address: NetAddress, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: bind(address: NetAddress): Promise\<void>;<br>Differences: bind(address: NetAddress): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: connect(options: TCPConnectOptions, callback: AsyncCallback\<void>): void;<br>Differences: connect(options: TCPConnectOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: connect(options: TCPConnectOptions): Promise\<void>;<br>Differences: connect(options: TCPConnectOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: send(options: TCPSendOptions, callback: AsyncCallback\<void>): void;<br>Differences: send(options: TCPSendOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: send(options: TCPSendOptions): Promise\<void>;<br>Differences: send(options: TCPSendOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: close(callback: AsyncCallback\<void>): void;<br>Differences: close(callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: close(): Promise\<void>;<br>Differences: close(): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: getRemoteAddress(callback: AsyncCallback\<NetAddress>): void;<br>Differences: getRemoteAddress(callback: AsyncCallback\<NetAddress>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: getRemoteAddress(): Promise\<NetAddress>;<br>Differences: getRemoteAddress(): Promise\<NetAddress>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: getState(callback: AsyncCallback\<SocketStateBase>): void;<br>Differences: getState(callback: AsyncCallback\<SocketStateBase>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: getState(): Promise\<SocketStateBase>;<br>Differences: getState(): Promise\<SocketStateBase>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: getSocketFd(callback: AsyncCallback\<number>): void;<br>Differences: getSocketFd(callback: AsyncCallback\<number>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: getSocketFd(): Promise\<number>;<br>Differences: getSocketFd(): Promise\<number>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback\<void>): void;<br>Differences: setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: setExtraOptions(options: TCPExtraOptions): Promise\<void>;<br>Differences: setExtraOptions(options: TCPExtraOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: on(type: 'message', callback: Callback\<SocketMessageInfo>): void;<br>Differences: on(type: 'message', callback: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;<br>Differences: off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: on(type: 'connect' \| 'close', callback: Callback\<void>): void;<br>Differences: on(type: 'connect' \| 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: on(type: 'connect' \| 'close', callback: Callback\<void>): void;<br>Differences: on(type: 'connect' \| 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: off(type: 'connect' \| 'close', callback?: Callback\<void>): void;<br>Differences: off(type: 'connect' \| 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: off(type: 'connect' \| 'close', callback?: Callback\<void>): void;<br>Differences: off(type: 'connect' \| 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocket;<br>API declaration: off(type: 'error', callback?: ErrorCallback): void;<br>Differences: off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface TLSSocket<br>Differences: export interface TLSSocket|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: bind(address: NetAddress, callback: AsyncCallback\<void>): void;<br>Differences: bind(address: NetAddress, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: bind(address: NetAddress): Promise\<void>;<br>Differences: bind(address: NetAddress): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: getRemoteAddress(callback: AsyncCallback\<NetAddress>): void;<br>Differences: getRemoteAddress(callback: AsyncCallback\<NetAddress>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: getRemoteAddress(): Promise\<NetAddress>;<br>Differences: getRemoteAddress(): Promise\<NetAddress>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: getState(callback: AsyncCallback\<SocketStateBase>): void;<br>Differences: getState(callback: AsyncCallback\<SocketStateBase>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: getState(): Promise\<SocketStateBase>;<br>Differences: getState(): Promise\<SocketStateBase>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback\<void>): void;<br>Differences: setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: setExtraOptions(options: TCPExtraOptions): Promise\<void>;<br>Differences: setExtraOptions(options: TCPExtraOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: on(type: 'message', callback: Callback\<SocketMessageInfo>): void;<br>Differences: on(type: 'message', callback: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;<br>Differences: off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: on(type: 'connect' \| 'close', callback: Callback\<void>): void;<br>Differences: on(type: 'connect' \| 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: on(type: 'connect' \| 'close', callback: Callback\<void>): void;<br>Differences: on(type: 'connect' \| 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: off(type: 'connect' \| 'close', callback?: Callback\<void>): void;<br>Differences: off(type: 'connect' \| 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: off(type: 'connect' \| 'close', callback?: Callback\<void>): void;<br>Differences: off(type: 'connect' \| 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: off(type: 'error', callback?: ErrorCallback): void;<br>Differences: off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: getCertificate(callback: AsyncCallback\<X509CertRawData>): void;<br>Differences: getCertificate(callback: AsyncCallback\<X509CertRawData>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: getCertificate(): Promise\<X509CertRawData>;<br>Differences: getCertificate(): Promise\<X509CertRawData>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: getRemoteCertificate(callback: AsyncCallback\<X509CertRawData>): void;<br>Differences: getRemoteCertificate(callback: AsyncCallback\<X509CertRawData>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: getRemoteCertificate(): Promise\<X509CertRawData>;<br>Differences: getRemoteCertificate(): Promise\<X509CertRawData>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: getProtocol(callback: AsyncCallback\<string>): void;<br>Differences: getProtocol(callback: AsyncCallback\<string>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: getProtocol(): Promise\<string>;<br>Differences: getProtocol(): Promise\<string>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: getCipherSuite(callback: AsyncCallback\<Array\<string>>): void;<br>Differences: getCipherSuite(callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: getCipherSuite(): Promise\<Array\<string>>;<br>Differences: getCipherSuite(): Promise\<Array\<string>>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: getSignatureAlgorithms(callback: AsyncCallback\<Array\<string>>): void;<br>Differences: getSignatureAlgorithms(callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: getSignatureAlgorithms(): Promise\<Array\<string>>;<br>Differences: getSignatureAlgorithms(): Promise\<Array\<string>>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: connect(options: TLSConnectOptions, callback: AsyncCallback\<void>): void;<br>Differences: connect(options: TLSConnectOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: connect(options: TLSConnectOptions): Promise\<void>;<br>Differences: connect(options: TLSConnectOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: send(data: string, callback: AsyncCallback\<void>): void;<br>Differences: send(data: string, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: send(data: string): Promise\<void>;<br>Differences: send(data: string): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: close(callback: AsyncCallback\<void>): void;<br>Differences: close(callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocket;<br>API declaration: close(): Promise\<void>;<br>Differences: close(): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface TLSSecureOptions<br>Differences: export interface TLSSecureOptions|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSecureOptions;<br>API declaration: ca: string \| Array\<string>;<br>Differences: ca: string \| Array\<string>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSecureOptions;<br>API declaration: cert?: string;<br>Differences: cert?: string;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSecureOptions;<br>API declaration: key?: string;<br>Differences: key?: string;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSecureOptions;<br>API declaration: password?: string;<br>Differences: password?: string;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSecureOptions;<br>API declaration: protocols?: Protocol \| Array\<Protocol>;<br>Differences: protocols?: Protocol \| Array\<Protocol>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSecureOptions;<br>API declaration: useRemoteCipherPrefer?: boolean;<br>Differences: useRemoteCipherPrefer?: boolean;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSecureOptions;<br>API declaration: signatureAlgorithms?: string;<br>Differences: signatureAlgorithms?: string;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSecureOptions;<br>API declaration: cipherSuite?: string;<br>Differences: cipherSuite?: string;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface TLSConnectOptions<br>Differences: export interface TLSConnectOptions|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSConnectOptions;<br>API declaration: address: NetAddress;<br>Differences: address: NetAddress;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSConnectOptions;<br>API declaration: secureOptions: TLSSecureOptions;<br>Differences: secureOptions: TLSSecureOptions;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSConnectOptions;<br>API declaration: ALPNProtocols?: Array\<string>;<br>Differences: ALPNProtocols?: Array\<string>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export enum Protocol<br>Differences: export enum Protocol|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: Protocol;<br>API declaration: TLSv12 = "TLSv1.2"<br>Differences: TLSv12 = "TLSv1.2"|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: Protocol;<br>API declaration: TLSv13 = "TLSv1.3"<br>Differences: TLSv13 = "TLSv1.3"|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface TCPSocketConnection<br>Differences: export interface TCPSocketConnection|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketConnection;<br>API declaration: clientId: number;<br>Differences: clientId: number;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketConnection;<br>API declaration: send(options: TCPSendOptions, callback: AsyncCallback\<void>): void;<br>Differences: send(options: TCPSendOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketConnection;<br>API declaration: send(options: TCPSendOptions): Promise\<void>;<br>Differences: send(options: TCPSendOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketConnection;<br>API declaration: close(callback: AsyncCallback\<void>): void;<br>Differences: close(callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketConnection;<br>API declaration: close(): Promise\<void>;<br>Differences: close(): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketConnection;<br>API declaration: getRemoteAddress(callback: AsyncCallback\<NetAddress>): void;<br>Differences: getRemoteAddress(callback: AsyncCallback\<NetAddress>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketConnection;<br>API declaration: getRemoteAddress(): Promise\<NetAddress>;<br>Differences: getRemoteAddress(): Promise\<NetAddress>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketConnection;<br>API declaration: on(type: 'message', callback: Callback\<SocketMessageInfo>): void;<br>Differences: on(type: 'message', callback: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketConnection;<br>API declaration: off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;<br>Differences: off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketConnection;<br>API declaration: on(type: 'close', callback: Callback\<void>): void;<br>Differences: on(type: 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketConnection;<br>API declaration: off(type: 'close', callback?: Callback\<void>): void;<br>Differences: off(type: 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketConnection;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketConnection;<br>API declaration: off(type: 'error', callback?: ErrorCallback): void;<br>Differences: off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface TCPSocketServer<br>Differences: export interface TCPSocketServer|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketServer;<br>API declaration: listen(address: NetAddress, callback: AsyncCallback\<void>): void;<br>Differences: listen(address: NetAddress, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketServer;<br>API declaration: listen(address: NetAddress): Promise\<void>;<br>Differences: listen(address: NetAddress): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketServer;<br>API declaration: getState(callback: AsyncCallback\<SocketStateBase>): void;<br>Differences: getState(callback: AsyncCallback\<SocketStateBase>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketServer;<br>API declaration: getState(): Promise\<SocketStateBase>;<br>Differences: getState(): Promise\<SocketStateBase>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketServer;<br>API declaration: setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback\<void>): void;<br>Differences: setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketServer;<br>API declaration: setExtraOptions(options: TCPExtraOptions): Promise\<void>;<br>Differences: setExtraOptions(options: TCPExtraOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketServer;<br>API declaration: on(type: 'connect', callback: Callback\<TCPSocketConnection>): void;<br>Differences: on(type: 'connect', callback: Callback\<TCPSocketConnection>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketServer;<br>API declaration: off(type: 'connect', callback?: Callback\<TCPSocketConnection>): void;<br>Differences: off(type: 'connect', callback?: Callback\<TCPSocketConnection>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketServer;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TCPSocketServer;<br>API declaration: off(type: 'error', callback?: ErrorCallback): void;<br>Differences: off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface TLSSocketConnection<br>Differences: export interface TLSSocketConnection|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: clientId: number;<br>Differences: clientId: number;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: send(data: string, callback: AsyncCallback\<void>): void;<br>Differences: send(data: string, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: send(data: string): Promise\<void>;<br>Differences: send(data: string): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: close(callback: AsyncCallback\<void>): void;<br>Differences: close(callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: close(): Promise\<void>;<br>Differences: close(): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: getRemoteAddress(callback: AsyncCallback\<NetAddress>): void;<br>Differences: getRemoteAddress(callback: AsyncCallback\<NetAddress>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: getRemoteAddress(): Promise\<NetAddress>;<br>Differences: getRemoteAddress(): Promise\<NetAddress>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: getRemoteCertificate(callback: AsyncCallback\<X509CertRawData>): void;<br>Differences: getRemoteCertificate(callback: AsyncCallback\<X509CertRawData>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: getRemoteCertificate(): Promise\<X509CertRawData>;<br>Differences: getRemoteCertificate(): Promise\<X509CertRawData>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: getCipherSuite(callback: AsyncCallback\<Array\<string>>): void;<br>Differences: getCipherSuite(callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: getCipherSuite(): Promise\<Array\<string>>;<br>Differences: getCipherSuite(): Promise\<Array\<string>>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: getSignatureAlgorithms(callback: AsyncCallback\<Array\<string>>): void;<br>Differences: getSignatureAlgorithms(callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: getSignatureAlgorithms(): Promise\<Array\<string>>;<br>Differences: getSignatureAlgorithms(): Promise\<Array\<string>>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: on(type: 'message', callback: Callback\<SocketMessageInfo>): void;<br>Differences: on(type: 'message', callback: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;<br>Differences: off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: on(type: 'close', callback: Callback\<void>): void;<br>Differences: on(type: 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: off(type: 'close', callback?: Callback\<void>): void;<br>Differences: off(type: 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketConnection;<br>API declaration: off(type: 'error', callback?: ErrorCallback): void;<br>Differences: off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface SocketMessageInfo<br>Differences: export interface SocketMessageInfo|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: SocketMessageInfo;<br>API declaration: message: ArrayBuffer;<br>Differences: message: ArrayBuffer;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: SocketMessageInfo;<br>API declaration: remoteInfo: SocketRemoteInfo;<br>Differences: remoteInfo: SocketRemoteInfo;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: socket;<br>API declaration: export interface TLSSocketServer<br>Differences: export interface TLSSocketServer|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketServer;<br>API declaration: listen(options: TLSConnectOptions, callback: AsyncCallback\<void>): void;<br>Differences: listen(options: TLSConnectOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketServer;<br>API declaration: listen(options: TLSConnectOptions): Promise\<void>;<br>Differences: listen(options: TLSConnectOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketServer;<br>API declaration: getState(callback: AsyncCallback\<SocketStateBase>): void;<br>Differences: getState(callback: AsyncCallback\<SocketStateBase>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketServer;<br>API declaration: getState(): Promise\<SocketStateBase>;<br>Differences: getState(): Promise\<SocketStateBase>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketServer;<br>API declaration: setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback\<void>): void;<br>Differences: setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketServer;<br>API declaration: setExtraOptions(options: TCPExtraOptions): Promise\<void>;<br>Differences: setExtraOptions(options: TCPExtraOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketServer;<br>API declaration: getCertificate(callback: AsyncCallback\<X509CertRawData>): void;<br>Differences: getCertificate(callback: AsyncCallback\<X509CertRawData>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketServer;<br>API declaration: getCertificate(): Promise\<X509CertRawData>;<br>Differences: getCertificate(): Promise\<X509CertRawData>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketServer;<br>API declaration: getProtocol(callback: AsyncCallback\<string>): void;<br>Differences: getProtocol(callback: AsyncCallback\<string>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketServer;<br>API declaration: getProtocol(): Promise\<string>;<br>Differences: getProtocol(): Promise\<string>;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketServer;<br>API declaration: on(type: 'connect', callback: Callback\<TLSSocketConnection>): void;<br>Differences: on(type: 'connect', callback: Callback\<TLSSocketConnection>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketServer;<br>API declaration: off(type: 'connect', callback?: Callback\<TLSSocketConnection>): void;<br>Differences: off(type: 'connect', callback?: Callback\<TLSSocketConnection>): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketServer;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: TLSSocketServer;<br>API declaration: off(type: 'error', callback?: ErrorCallback): void;<br>Differences: off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace statistics<br>Differences: declare namespace statistics|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getIfaceRxBytes(nic: string, callback: AsyncCallback\<number>): void;<br>Differences: function getIfaceRxBytes(nic: string, callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getIfaceRxBytes(nic: string): Promise\<number>;<br>Differences: function getIfaceRxBytes(nic: string): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getIfaceTxBytes(nic: string, callback: AsyncCallback\<number>): void;<br>Differences: function getIfaceTxBytes(nic: string, callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getIfaceTxBytes(nic: string): Promise\<number>;<br>Differences: function getIfaceTxBytes(nic: string): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getCellularRxBytes(callback: AsyncCallback\<number>): void;<br>Differences: function getCellularRxBytes(callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getCellularRxBytes(): Promise\<number>;<br>Differences: function getCellularRxBytes(): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getCellularTxBytes(callback: AsyncCallback\<number>): void;<br>Differences: function getCellularTxBytes(callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getCellularTxBytes(): Promise\<number>;<br>Differences: function getCellularTxBytes(): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getAllRxBytes(callback: AsyncCallback\<number>): void;<br>Differences: function getAllRxBytes(callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getAllRxBytes(): Promise\<number>;<br>Differences: function getAllRxBytes(): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getAllTxBytes(callback: AsyncCallback\<number>): void;<br>Differences: function getAllTxBytes(callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getAllTxBytes(): Promise\<number>;<br>Differences: function getAllTxBytes(): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getUidRxBytes(uid: number, callback: AsyncCallback\<number>): void;<br>Differences: function getUidRxBytes(uid: number, callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getUidRxBytes(uid: number): Promise\<number>;<br>Differences: function getUidRxBytes(uid: number): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getUidTxBytes(uid: number, callback: AsyncCallback\<number>): void;<br>Differences: function getUidTxBytes(uid: number, callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getUidTxBytes(uid: number): Promise\<number>;<br>Differences: function getUidTxBytes(uid: number): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getSockfdRxBytes(sockfd: number, callback: AsyncCallback\<number>): void;<br>Differences: function getSockfdRxBytes(sockfd: number, callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getSockfdRxBytes(sockfd: number): Promise\<number>;<br>Differences: function getSockfdRxBytes(sockfd: number): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getSockfdTxBytes(sockfd: number, callback: AsyncCallback\<number>): void;<br>Differences: function getSockfdTxBytes(sockfd: number, callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: statistics;<br>API declaration: function getSockfdTxBytes(sockfd: number): Promise\<number>;<br>Differences: function getSockfdTxBytes(sockfd: number): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace vpn<br>Differences: declare namespace vpn|api/@ohos.net.vpn.d.ts|
|New API |NA|Class name: vpn;<br>API declaration: export type LinkAddress = connection.LinkAddress;<br>Differences: export type LinkAddress = connection.LinkAddress;|api/@ohos.net.vpn.d.ts|
|New API |NA|Class name: vpn;<br>API declaration: export type RouteInfo = connection.RouteInfo;<br>Differences: export type RouteInfo = connection.RouteInfo;|api/@ohos.net.vpn.d.ts|
|New API |NA|Class name: vpn;<br>API declaration: export type AbilityContext = _AbilityContext;<br>Differences: export type AbilityContext = _AbilityContext;|api/@ohos.net.vpn.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace vpnExtension<br>Differences: declare namespace vpnExtension|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: vpnExtension;<br>API declaration: export type LinkAddress = connection.LinkAddress;<br>Differences: export type LinkAddress = connection.LinkAddress;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: vpnExtension;<br>API declaration: export type RouteInfo = connection.RouteInfo;<br>Differences: export type RouteInfo = connection.RouteInfo;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: vpnExtension;<br>API declaration: export type VpnExtensionContext = _VpnExtensionContext;<br>Differences: export type VpnExtensionContext = _VpnExtensionContext;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: vpnExtension;<br>API declaration: function startVpnExtensionAbility(want: Want): Promise\<void>;<br>Differences: function startVpnExtensionAbility(want: Want): Promise\<void>;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: vpnExtension;<br>API declaration: function stopVpnExtensionAbility(want: Want): Promise\<void>;<br>Differences: function stopVpnExtensionAbility(want: Want): Promise\<void>;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: vpnExtension;<br>API declaration: function createVpnConnection(context: VpnExtensionContext): VpnConnection;<br>Differences: function createVpnConnection(context: VpnExtensionContext): VpnConnection;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: vpnExtension;<br>API declaration: export interface VpnConnection<br>Differences: export interface VpnConnection|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: VpnConnection;<br>API declaration: create(config: VpnConfig): Promise\<number>;<br>Differences: create(config: VpnConfig): Promise\<number>;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: VpnConnection;<br>API declaration: protect(socketFd: number): Promise\<void>;<br>Differences: protect(socketFd: number): Promise\<void>;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: VpnConnection;<br>API declaration: destroy(): Promise\<void>;<br>Differences: destroy(): Promise\<void>;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: vpnExtension;<br>API declaration: export interface VpnConfig<br>Differences: export interface VpnConfig|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: VpnConfig;<br>API declaration: addresses: Array\<LinkAddress>;<br>Differences: addresses: Array\<LinkAddress>;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: VpnConfig;<br>API declaration: routes?: Array\<RouteInfo>;<br>Differences: routes?: Array\<RouteInfo>;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: VpnConfig;<br>API declaration: dnsAddresses?: Array\<string>;<br>Differences: dnsAddresses?: Array\<string>;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: VpnConfig;<br>API declaration: searchDomains?: Array\<string>;<br>Differences: searchDomains?: Array\<string>;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: VpnConfig;<br>API declaration: mtu?: number;<br>Differences: mtu?: number;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: VpnConfig;<br>API declaration: isIPv4Accepted?: boolean;<br>Differences: isIPv4Accepted?: boolean;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: VpnConfig;<br>API declaration: isIPv6Accepted?: boolean;<br>Differences: isIPv6Accepted?: boolean;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: VpnConfig;<br>API declaration: isInternal?: boolean;<br>Differences: isInternal?: boolean;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: VpnConfig;<br>API declaration: isBlocking?: boolean;<br>Differences: isBlocking?: boolean;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: VpnConfig;<br>API declaration: trustedApplications?: Array\<string>;<br>Differences: trustedApplications?: Array\<string>;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: VpnConfig;<br>API declaration: blockedApplications?: Array\<string>;<br>Differences: blockedApplications?: Array\<string>;|api/@ohos.net.vpnExtension.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace webSocket<br>Differences: declare namespace webSocket|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: webSocket;<br>API declaration: function createWebSocket(): WebSocket;<br>Differences: function createWebSocket(): WebSocket;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: webSocket;<br>API declaration: export interface WebSocketRequestOptions<br>Differences: export interface WebSocketRequestOptions|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocketRequestOptions;<br>API declaration: header?: Object;<br>Differences: header?: Object;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocketRequestOptions;<br>API declaration: caPath?: string;<br>Differences: caPath?: string;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocketRequestOptions;<br>API declaration: clientCert?: ClientCert;<br>Differences: clientCert?: ClientCert;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: webSocket;<br>API declaration: export interface ClientCert<br>Differences: export interface ClientCert|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: ClientCert;<br>API declaration: certPath: string;<br>Differences: certPath: string;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: ClientCert;<br>API declaration: keyPath: string;<br>Differences: keyPath: string;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: ClientCert;<br>API declaration: keyPassword?: string;<br>Differences: keyPassword?: string;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: webSocket;<br>API declaration: export interface WebSocketCloseOptions<br>Differences: export interface WebSocketCloseOptions|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocketCloseOptions;<br>API declaration: code?: number;<br>Differences: code?: number;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocketCloseOptions;<br>API declaration: reason?: string;<br>Differences: reason?: string;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: webSocket;<br>API declaration: export interface CloseResult<br>Differences: export interface CloseResult|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: CloseResult;<br>API declaration: code: number;<br>Differences: code: number;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: CloseResult;<br>API declaration: reason: string;<br>Differences: reason: string;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: webSocket;<br>API declaration: export interface WebSocket<br>Differences: export interface WebSocket|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocket;<br>API declaration: connect(url: string, callback: AsyncCallback\<boolean>): void;<br>Differences: connect(url: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocket;<br>API declaration: connect(url: string, options: WebSocketRequestOptions, callback: AsyncCallback\<boolean>): void;<br>Differences: connect(url: string, options: WebSocketRequestOptions, callback: AsyncCallback\<boolean>): void;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocket;<br>API declaration: connect(url: string, options?: WebSocketRequestOptions): Promise\<boolean>;<br>Differences: connect(url: string, options?: WebSocketRequestOptions): Promise\<boolean>;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocket;<br>API declaration: send(data: string \| ArrayBuffer, callback: AsyncCallback\<boolean>): void;<br>Differences: send(data: string \| ArrayBuffer, callback: AsyncCallback\<boolean>): void;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocket;<br>API declaration: send(data: string \| ArrayBuffer): Promise\<boolean>;<br>Differences: send(data: string \| ArrayBuffer): Promise\<boolean>;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocket;<br>API declaration: close(callback: AsyncCallback\<boolean>): void;<br>Differences: close(callback: AsyncCallback\<boolean>): void;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocket;<br>API declaration: close(options: WebSocketCloseOptions, callback: AsyncCallback\<boolean>): void;<br>Differences: close(options: WebSocketCloseOptions, callback: AsyncCallback\<boolean>): void;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocket;<br>API declaration: close(options?: WebSocketCloseOptions): Promise\<boolean>;<br>Differences: close(options?: WebSocketCloseOptions): Promise\<boolean>;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocket;<br>API declaration: on(type: 'open', callback: AsyncCallback\<Object>): void;<br>Differences: on(type: 'open', callback: AsyncCallback\<Object>): void;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocket;<br>API declaration: off(type: 'open', callback?: AsyncCallback\<Object>): void;<br>Differences: off(type: 'open', callback?: AsyncCallback\<Object>): void;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocket;<br>API declaration: on(type: 'message', callback: AsyncCallback\<string \| ArrayBuffer>): void;<br>Differences: on(type: 'message', callback: AsyncCallback\<string \| ArrayBuffer>): void;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocket;<br>API declaration: off(type: 'message', callback?: AsyncCallback\<string \| ArrayBuffer>): void;<br>Differences: off(type: 'message', callback?: AsyncCallback\<string \| ArrayBuffer>): void;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocket;<br>API declaration: on(type: 'close', callback: AsyncCallback\<CloseResult>): void;<br>Differences: on(type: 'close', callback: AsyncCallback\<CloseResult>): void;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocket;<br>API declaration: off(type: 'close', callback?: AsyncCallback\<CloseResult>): void;<br>Differences: off(type: 'close', callback?: AsyncCallback\<CloseResult>): void;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocket;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocket;<br>API declaration: off(type: 'error', callback?: ErrorCallback): void;<br>Differences: off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocket;<br>API declaration: on(type: 'dataEnd', callback: Callback\<void>): void;<br>Differences: on(type: 'dataEnd', callback: Callback\<void>): void;|api/@ohos.net.webSocket.d.ts|
|New API |NA|Class name: WebSocket;<br>API declaration: off(type: 'dataEnd', callback?: Callback\<void>): void;<br>Differences: off(type: 'dataEnd', callback?: Callback\<void>): void;|api/@ohos.net.webSocket.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.app.ability.VpnExtensionAbility.d.ts<br>Differences: NetworkKit|api/@ohos.app.ability.VpnExtensionAbility.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.net.connection.d.ts<br>Differences: NetworkKit|api/@ohos.net.connection.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.net.ethernet.d.ts<br>Differences: NetworkKit|api/@ohos.net.ethernet.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.net.http.d.ts<br>Differences: NetworkKit|api/@ohos.net.http.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.net.mdns.d.ts<br>Differences: NetworkKit|api/@ohos.net.mdns.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.net.networkSecurity.d.ts<br>Differences: NetworkKit|api/@ohos.net.networkSecurity.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.net.policy.d.ts<br>Differences: NetworkKit|api/@ohos.net.policy.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.net.sharing.d.ts<br>Differences: NetworkKit|api/@ohos.net.sharing.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.net.socket.d.ts<br>Differences: NetworkKit|api/@ohos.net.socket.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.net.statistics.d.ts<br>Differences: NetworkKit|api/@ohos.net.statistics.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.net.vpn.d.ts<br>Differences: NetworkKit|api/@ohos.net.vpn.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.net.vpnExtension.d.ts<br>Differences: NetworkKit|api/@ohos.net.vpnExtension.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.net.webSocket.d.ts<br>Differences: NetworkKit|api/@ohos.net.webSocket.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.NetworkKit.d.ts<br>Differences: NetworkKit|kits/@kit.NetworkKit.d.ts|
