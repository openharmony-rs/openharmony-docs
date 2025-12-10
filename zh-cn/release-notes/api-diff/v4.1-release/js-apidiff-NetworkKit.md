| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：export default class VpnExtensionAbility<br>差异内容：export default class VpnExtensionAbility|api/@ohos.app.ability.VpnExtensionAbility.d.ts|
|新增API|NA|类名：VpnExtensionAbility；<br>API声明：context: VpnExtensionContext;<br>差异内容：context: VpnExtensionContext;|api/@ohos.app.ability.VpnExtensionAbility.d.ts|
|新增API|NA|类名：VpnExtensionAbility；<br>API声明：onCreate(want: Want): void;<br>差异内容：onCreate(want: Want): void;|api/@ohos.app.ability.VpnExtensionAbility.d.ts|
|新增API|NA|类名：VpnExtensionAbility；<br>API声明：onDestroy(): void;<br>差异内容：onDestroy(): void;|api/@ohos.app.ability.VpnExtensionAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace connection<br>差异内容：declare namespace connection|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：type HttpRequest = http.HttpRequest;<br>差异内容：type HttpRequest = http.HttpRequest;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：type TCPSocket = socket.TCPSocket;<br>差异内容：type TCPSocket = socket.TCPSocket;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：type UDPSocket = socket.UDPSocket;<br>差异内容：type UDPSocket = socket.UDPSocket;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function createNetConnection(netSpecifier?: NetSpecifier, timeout?: number): NetConnection;<br>差异内容：function createNetConnection(netSpecifier?: NetSpecifier, timeout?: number): NetConnection;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getDefaultNet(callback: AsyncCallback\<NetHandle>): void;<br>差异内容：function getDefaultNet(callback: AsyncCallback\<NetHandle>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getDefaultNet(): Promise\<NetHandle>;<br>差异内容：function getDefaultNet(): Promise\<NetHandle>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getDefaultNetSync(): NetHandle;<br>差异内容：function getDefaultNetSync(): NetHandle;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getAllNets(callback: AsyncCallback\<Array\<NetHandle>>): void;<br>差异内容：function getAllNets(callback: AsyncCallback\<Array\<NetHandle>>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getAllNets(): Promise\<Array\<NetHandle>>;<br>差异内容：function getAllNets(): Promise\<Array\<NetHandle>>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getAllNetsSync(): Array\<NetHandle>;<br>差异内容：function getAllNetsSync(): Array\<NetHandle>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getConnectionProperties(netHandle: NetHandle, callback: AsyncCallback\<ConnectionProperties>): void;<br>差异内容：function getConnectionProperties(netHandle: NetHandle, callback: AsyncCallback\<ConnectionProperties>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getConnectionProperties(netHandle: NetHandle): Promise\<ConnectionProperties>;<br>差异内容：function getConnectionProperties(netHandle: NetHandle): Promise\<ConnectionProperties>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getConnectionPropertiesSync(netHandle: NetHandle): ConnectionProperties;<br>差异内容：function getConnectionPropertiesSync(netHandle: NetHandle): ConnectionProperties;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getNetCapabilities(netHandle: NetHandle, callback: AsyncCallback\<NetCapabilities>): void;<br>差异内容：function getNetCapabilities(netHandle: NetHandle, callback: AsyncCallback\<NetCapabilities>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getNetCapabilities(netHandle: NetHandle): Promise\<NetCapabilities>;<br>差异内容：function getNetCapabilities(netHandle: NetHandle): Promise\<NetCapabilities>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getNetCapabilitiesSync(netHandle: NetHandle): NetCapabilities;<br>差异内容：function getNetCapabilitiesSync(netHandle: NetHandle): NetCapabilities;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function isDefaultNetMetered(callback: AsyncCallback\<boolean>): void;<br>差异内容：function isDefaultNetMetered(callback: AsyncCallback\<boolean>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function isDefaultNetMetered(): Promise\<boolean>;<br>差异内容：function isDefaultNetMetered(): Promise\<boolean>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function isDefaultNetMeteredSync(): boolean;<br>差异内容：function isDefaultNetMeteredSync(): boolean;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function hasDefaultNet(callback: AsyncCallback\<boolean>): void;<br>差异内容：function hasDefaultNet(callback: AsyncCallback\<boolean>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function hasDefaultNet(): Promise\<boolean>;<br>差异内容：function hasDefaultNet(): Promise\<boolean>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function hasDefaultNetSync(): boolean;<br>差异内容：function hasDefaultNetSync(): boolean;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function reportNetConnected(netHandle: NetHandle, callback: AsyncCallback\<void>): void;<br>差异内容：function reportNetConnected(netHandle: NetHandle, callback: AsyncCallback\<void>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function reportNetConnected(netHandle: NetHandle): Promise\<void>;<br>差异内容：function reportNetConnected(netHandle: NetHandle): Promise\<void>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function reportNetDisconnected(netHandle: NetHandle, callback: AsyncCallback\<void>): void;<br>差异内容：function reportNetDisconnected(netHandle: NetHandle, callback: AsyncCallback\<void>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function reportNetDisconnected(netHandle: NetHandle): Promise\<void>;<br>差异内容：function reportNetDisconnected(netHandle: NetHandle): Promise\<void>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getAddressesByName(host: string, callback: AsyncCallback\<Array\<NetAddress>>): void;<br>差异内容：function getAddressesByName(host: string, callback: AsyncCallback\<Array\<NetAddress>>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getAddressesByName(host: string): Promise\<Array\<NetAddress>>;<br>差异内容：function getAddressesByName(host: string): Promise\<Array\<NetAddress>>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getAppNet(callback: AsyncCallback\<NetHandle>): void;<br>差异内容：function getAppNet(callback: AsyncCallback\<NetHandle>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getAppNet(): Promise\<NetHandle>;<br>差异内容：function getAppNet(): Promise\<NetHandle>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getAppNetSync(): NetHandle;<br>差异内容：function getAppNetSync(): NetHandle;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function setAppNet(netHandle: NetHandle, callback: AsyncCallback\<void>): void;<br>差异内容：function setAppNet(netHandle: NetHandle, callback: AsyncCallback\<void>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function setAppNet(netHandle: NetHandle): Promise\<void>;<br>差异内容：function setAppNet(netHandle: NetHandle): Promise\<void>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getDefaultHttpProxy(callback: AsyncCallback\<HttpProxy>): void;<br>差异内容：function getDefaultHttpProxy(callback: AsyncCallback\<HttpProxy>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getDefaultHttpProxy(): Promise\<HttpProxy>;<br>差异内容：function getDefaultHttpProxy(): Promise\<HttpProxy>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function setAppHttpProxy(httpProxy: HttpProxy): void;<br>差异内容：function setAppHttpProxy(httpProxy: HttpProxy): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function addCustomDnsRule(host: string, ip: Array\<string>, callback: AsyncCallback\<void>): void;<br>差异内容：function addCustomDnsRule(host: string, ip: Array\<string>, callback: AsyncCallback\<void>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function addCustomDnsRule(host: string, ip: Array\<string>): Promise\<void>;<br>差异内容：function addCustomDnsRule(host: string, ip: Array\<string>): Promise\<void>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function removeCustomDnsRule(host: string, callback: AsyncCallback\<void>): void;<br>差异内容：function removeCustomDnsRule(host: string, callback: AsyncCallback\<void>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function removeCustomDnsRule(host: string): Promise\<void>;<br>差异内容：function removeCustomDnsRule(host: string): Promise\<void>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function clearCustomDnsRules(callback: AsyncCallback\<void>): void;<br>差异内容：function clearCustomDnsRules(callback: AsyncCallback\<void>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function clearCustomDnsRules(): Promise\<void>;<br>差异内容：function clearCustomDnsRules(): Promise\<void>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：export interface NetConnection<br>差异内容：export interface NetConnection|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetConnection；<br>API声明：on(type: 'netAvailable', callback: Callback\<NetHandle>): void;<br>差异内容：on(type: 'netAvailable', callback: Callback\<NetHandle>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetConnection；<br>API声明：on(type: 'netBlockStatusChange', callback: Callback\<NetBlockStatusInfo>): void;<br>差异内容：on(type: 'netBlockStatusChange', callback: Callback\<NetBlockStatusInfo>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetConnection；<br>API声明：on(type: 'netCapabilitiesChange', callback: Callback\<NetCapabilityInfo>): void;<br>差异内容：on(type: 'netCapabilitiesChange', callback: Callback\<NetCapabilityInfo>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetConnection；<br>API声明：on(type: 'netConnectionPropertiesChange', callback: Callback\<NetConnectionPropertyInfo>): void;<br>差异内容：on(type: 'netConnectionPropertiesChange', callback: Callback\<NetConnectionPropertyInfo>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetConnection；<br>API声明：on(type: 'netLost', callback: Callback\<NetHandle>): void;<br>差异内容：on(type: 'netLost', callback: Callback\<NetHandle>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetConnection；<br>API声明：on(type: 'netUnavailable', callback: Callback\<void>): void;<br>差异内容：on(type: 'netUnavailable', callback: Callback\<void>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetConnection；<br>API声明：register(callback: AsyncCallback\<void>): void;<br>差异内容：register(callback: AsyncCallback\<void>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetConnection；<br>API声明：unregister(callback: AsyncCallback\<void>): void;<br>差异内容：unregister(callback: AsyncCallback\<void>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：export interface NetSpecifier<br>差异内容：export interface NetSpecifier|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetSpecifier；<br>API声明：netCapabilities: NetCapabilities;<br>差异内容：netCapabilities: NetCapabilities;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetSpecifier；<br>API声明：bearerPrivateIdentifier?: string;<br>差异内容：bearerPrivateIdentifier?: string;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：export interface NetCapabilityInfo<br>差异内容：export interface NetCapabilityInfo|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetCapabilityInfo；<br>API声明：netHandle: NetHandle;<br>差异内容：netHandle: NetHandle;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetCapabilityInfo；<br>API声明：netCap: NetCapabilities;<br>差异内容：netCap: NetCapabilities;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：export interface NetHandle<br>差异内容：export interface NetHandle|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetHandle；<br>API声明：netId: number;<br>差异内容：netId: number;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetHandle；<br>API声明：bindSocket(socketParam: TCPSocket \| UDPSocket, callback: AsyncCallback\<void>): void;<br>差异内容：bindSocket(socketParam: TCPSocket \| UDPSocket, callback: AsyncCallback\<void>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetHandle；<br>API声明：bindSocket(socketParam: TCPSocket \| UDPSocket): Promise\<void>;<br>差异内容：bindSocket(socketParam: TCPSocket \| UDPSocket): Promise\<void>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetHandle；<br>API声明：getAddressesByName(host: string, callback: AsyncCallback\<Array\<NetAddress>>): void;<br>差异内容：getAddressesByName(host: string, callback: AsyncCallback\<Array\<NetAddress>>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetHandle；<br>API声明：getAddressesByName(host: string): Promise\<Array\<NetAddress>>;<br>差异内容：getAddressesByName(host: string): Promise\<Array\<NetAddress>>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetHandle；<br>API声明：getAddressByName(host: string, callback: AsyncCallback\<NetAddress>): void;<br>差异内容：getAddressByName(host: string, callback: AsyncCallback\<NetAddress>): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetHandle；<br>API声明：getAddressByName(host: string): Promise\<NetAddress>;<br>差异内容：getAddressByName(host: string): Promise\<NetAddress>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：export interface NetCapabilities<br>差异内容：export interface NetCapabilities|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetCapabilities；<br>API声明：linkUpBandwidthKbps?: number;<br>差异内容：linkUpBandwidthKbps?: number;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetCapabilities；<br>API声明：linkDownBandwidthKbps?: number;<br>差异内容：linkDownBandwidthKbps?: number;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetCapabilities；<br>API声明：networkCap?: Array\<NetCap>;<br>差异内容：networkCap?: Array\<NetCap>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetCapabilities；<br>API声明：bearerTypes: Array\<NetBearType>;<br>差异内容：bearerTypes: Array\<NetBearType>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：export interface NetConnectionPropertyInfo<br>差异内容：export interface NetConnectionPropertyInfo|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetConnectionPropertyInfo；<br>API声明：netHandle: NetHandle;<br>差异内容：netHandle: NetHandle;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetConnectionPropertyInfo；<br>API声明：connectionProperties: ConnectionProperties;<br>差异内容：connectionProperties: ConnectionProperties;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：export interface NetBlockStatusInfo<br>差异内容：export interface NetBlockStatusInfo|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetBlockStatusInfo；<br>API声明：netHandle: NetHandle;<br>差异内容：netHandle: NetHandle;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetBlockStatusInfo；<br>API声明：blocked: boolean;<br>差异内容：blocked: boolean;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：export enum NetCap<br>差异内容：export enum NetCap|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetCap；<br>API声明：NET_CAPABILITY_MMS = 0<br>差异内容：NET_CAPABILITY_MMS = 0|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetCap；<br>API声明：NET_CAPABILITY_NOT_METERED = 11<br>差异内容：NET_CAPABILITY_NOT_METERED = 11|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetCap；<br>API声明：NET_CAPABILITY_INTERNET = 12<br>差异内容：NET_CAPABILITY_INTERNET = 12|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetCap；<br>API声明：NET_CAPABILITY_NOT_VPN = 15<br>差异内容：NET_CAPABILITY_NOT_VPN = 15|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetCap；<br>API声明：NET_CAPABILITY_VALIDATED = 16<br>差异内容：NET_CAPABILITY_VALIDATED = 16|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：export enum NetBearType<br>差异内容：export enum NetBearType|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetBearType；<br>API声明：BEARER_CELLULAR = 0<br>差异内容：BEARER_CELLULAR = 0|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetBearType；<br>API声明：BEARER_WIFI = 1<br>差异内容：BEARER_WIFI = 1|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetBearType；<br>API声明：BEARER_ETHERNET = 3<br>差异内容：BEARER_ETHERNET = 3|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：export interface ConnectionProperties<br>差异内容：export interface ConnectionProperties|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：ConnectionProperties；<br>API声明：interfaceName: string;<br>差异内容：interfaceName: string;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：ConnectionProperties；<br>API声明：domains: string;<br>差异内容：domains: string;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：ConnectionProperties；<br>API声明：linkAddresses: Array\<LinkAddress>;<br>差异内容：linkAddresses: Array\<LinkAddress>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：ConnectionProperties；<br>API声明：dnses: Array\<NetAddress>;<br>差异内容：dnses: Array\<NetAddress>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：ConnectionProperties；<br>API声明：routes: Array\<RouteInfo>;<br>差异内容：routes: Array\<RouteInfo>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：ConnectionProperties；<br>API声明：mtu: number;<br>差异内容：mtu: number;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：export interface RouteInfo<br>差异内容：export interface RouteInfo|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：RouteInfo；<br>API声明：interface: string;<br>差异内容：interface: string;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：RouteInfo；<br>API声明：destination: LinkAddress;<br>差异内容：destination: LinkAddress;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：RouteInfo；<br>API声明：gateway: NetAddress;<br>差异内容：gateway: NetAddress;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：RouteInfo；<br>API声明：hasGateway: boolean;<br>差异内容：hasGateway: boolean;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：RouteInfo；<br>API声明：isDefaultRoute: boolean;<br>差异内容：isDefaultRoute: boolean;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：export interface LinkAddress<br>差异内容：export interface LinkAddress|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：LinkAddress；<br>API声明：address: NetAddress;<br>差异内容：address: NetAddress;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：LinkAddress；<br>API声明：prefixLength: number;<br>差异内容：prefixLength: number;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：export interface NetAddress<br>差异内容：export interface NetAddress|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetAddress；<br>API声明：address: string;<br>差异内容：address: string;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetAddress；<br>API声明：family?: number;<br>差异内容：family?: number;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetAddress；<br>API声明：port?: number;<br>差异内容：port?: number;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：export interface HttpProxy<br>差异内容：export interface HttpProxy|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：HttpProxy；<br>API声明：host: string;<br>差异内容：host: string;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：HttpProxy；<br>API声明：port: number;<br>差异内容：port: number;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：HttpProxy；<br>API声明：exclusionList: Array\<string>;<br>差异内容：exclusionList: Array\<string>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace ethernet<br>差异内容：declare namespace ethernet|api/@ohos.net.ethernet.d.ts|
|新增API|NA|类名：ethernet；<br>API声明：type HttpProxy = connection.HttpProxy;<br>差异内容：type HttpProxy = connection.HttpProxy;|api/@ohos.net.ethernet.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace http<br>差异内容：declare namespace http|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：type HttpProxy = connection.HttpProxy;<br>差异内容：type HttpProxy = connection.HttpProxy;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：function createHttp(): HttpRequest;<br>差异内容：function createHttp(): HttpRequest;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export interface HttpRequestOptions<br>差异内容：export interface HttpRequestOptions|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：method?: RequestMethod;<br>差异内容：method?: RequestMethod;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：extraData?: string \| Object \| ArrayBuffer;<br>差异内容：extraData?: string \| Object \| ArrayBuffer;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：expectDataType?: HttpDataType;<br>差异内容：expectDataType?: HttpDataType;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：usingCache?: boolean;<br>差异内容：usingCache?: boolean;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：priority?: number;<br>差异内容：priority?: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：header?: Object;<br>差异内容：header?: Object;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：readTimeout?: number;<br>差异内容：readTimeout?: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：connectTimeout?: number;<br>差异内容：connectTimeout?: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：usingProtocol?: HttpProtocol;<br>差异内容：usingProtocol?: HttpProtocol;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：usingProxy?: boolean \| HttpProxy;<br>差异内容：usingProxy?: boolean \| HttpProxy;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：caPath?: string;<br>差异内容：caPath?: string;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：resumeFrom?: number;<br>差异内容：resumeFrom?: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：resumeTo?: number;<br>差异内容：resumeTo?: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：clientCert?: ClientCert;<br>差异内容：clientCert?: ClientCert;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：dnsOverHttps?: string;<br>差异内容：dnsOverHttps?: string;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：dnsServers?: Array\<string>;<br>差异内容：dnsServers?: Array\<string>;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：maxLimit?: number;<br>差异内容：maxLimit?: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：multiFormDataList?: Array\<MultiFormData>;<br>差异内容：multiFormDataList?: Array\<MultiFormData>;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export interface MultiFormData<br>差异内容：export interface MultiFormData|api/@ohos.net.http.d.ts|
|新增API|NA|类名：MultiFormData；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：MultiFormData；<br>API声明：contentType: string;<br>差异内容：contentType: string;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：MultiFormData；<br>API声明：remoteFileName?: string;<br>差异内容：remoteFileName?: string;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：MultiFormData；<br>API声明：data?: string \| Object \| ArrayBuffer;<br>差异内容：data?: string \| Object \| ArrayBuffer;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：MultiFormData；<br>API声明：filePath?: string;<br>差异内容：filePath?: string;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export enum CertType<br>差异内容：export enum CertType|api/@ohos.net.http.d.ts|
|新增API|NA|类名：CertType；<br>API声明：PEM = 'PEM'<br>差异内容：PEM = 'PEM'|api/@ohos.net.http.d.ts|
|新增API|NA|类名：CertType；<br>API声明：DER = 'DER'<br>差异内容：DER = 'DER'|api/@ohos.net.http.d.ts|
|新增API|NA|类名：CertType；<br>API声明：P12 = 'P12'<br>差异内容：P12 = 'P12'|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export interface ClientCert<br>差异内容：export interface ClientCert|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ClientCert；<br>API声明：certPath: string;<br>差异内容：certPath: string;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ClientCert；<br>API声明：certType?: CertType;<br>差异内容：certType?: CertType;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ClientCert；<br>API声明：keyPath: string;<br>差异内容：keyPath: string;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ClientCert；<br>API声明：keyPassword?: string;<br>差异内容：keyPassword?: string;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export interface HttpRequest<br>差异内容：export interface HttpRequest|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：request(url: string, callback: AsyncCallback\<HttpResponse>): void;<br>差异内容：request(url: string, callback: AsyncCallback\<HttpResponse>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：request(url: string, options: HttpRequestOptions, callback: AsyncCallback\<HttpResponse>): void;<br>差异内容：request(url: string, options: HttpRequestOptions, callback: AsyncCallback\<HttpResponse>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：request(url: string, options?: HttpRequestOptions): Promise\<HttpResponse>;<br>差异内容：request(url: string, options?: HttpRequestOptions): Promise\<HttpResponse>;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：requestInStream(url: string, callback: AsyncCallback\<number>): void;<br>差异内容：requestInStream(url: string, callback: AsyncCallback\<number>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number>): void;<br>差异内容：requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：requestInStream(url: string, options?: HttpRequestOptions): Promise\<number>;<br>差异内容：requestInStream(url: string, options?: HttpRequestOptions): Promise\<number>;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：destroy(): void;<br>差异内容：destroy(): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：on(type: "headerReceive", callback: AsyncCallback\<Object>): void;<br>差异内容：on(type: "headerReceive", callback: AsyncCallback\<Object>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：off(type: "headerReceive", callback?: AsyncCallback\<Object>): void;<br>差异内容：off(type: "headerReceive", callback?: AsyncCallback\<Object>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：on(type: "headersReceive", callback: Callback\<Object>): void;<br>差异内容：on(type: "headersReceive", callback: Callback\<Object>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：off(type: "headersReceive", callback?: Callback\<Object>): void;<br>差异内容：off(type: "headersReceive", callback?: Callback\<Object>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：once(type: "headersReceive", callback: Callback\<Object>): void;<br>差异内容：once(type: "headersReceive", callback: Callback\<Object>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：on(type: "dataReceive", callback: Callback\<ArrayBuffer>): void;<br>差异内容：on(type: "dataReceive", callback: Callback\<ArrayBuffer>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：off(type: "dataReceive", callback?: Callback\<ArrayBuffer>): void;<br>差异内容：off(type: "dataReceive", callback?: Callback\<ArrayBuffer>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：on(type: "dataEnd", callback: Callback\<void>): void;<br>差异内容：on(type: "dataEnd", callback: Callback\<void>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：off(type: "dataEnd", callback?: Callback\<void>): void;<br>差异内容：off(type: "dataEnd", callback?: Callback\<void>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：on(type: 'dataReceiveProgress', callback: Callback\<DataReceiveProgressInfo>): void;<br>差异内容：on(type: 'dataReceiveProgress', callback: Callback\<DataReceiveProgressInfo>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：off(type: 'dataReceiveProgress', callback?: Callback\<DataReceiveProgressInfo>): void;<br>差异内容：off(type: 'dataReceiveProgress', callback?: Callback\<DataReceiveProgressInfo>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：on(type: 'dataSendProgress', callback: Callback\<DataSendProgressInfo>): void;<br>差异内容：on(type: 'dataSendProgress', callback: Callback\<DataSendProgressInfo>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequest；<br>API声明：off(type: 'dataSendProgress', callback?: Callback\<DataSendProgressInfo>): void;<br>差异内容：off(type: 'dataSendProgress', callback?: Callback\<DataSendProgressInfo>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export enum RequestMethod<br>差异内容：export enum RequestMethod|api/@ohos.net.http.d.ts|
|新增API|NA|类名：RequestMethod；<br>API声明：OPTIONS = "OPTIONS"<br>差异内容：OPTIONS = "OPTIONS"|api/@ohos.net.http.d.ts|
|新增API|NA|类名：RequestMethod；<br>API声明：GET = "GET"<br>差异内容：GET = "GET"|api/@ohos.net.http.d.ts|
|新增API|NA|类名：RequestMethod；<br>API声明：HEAD = "HEAD"<br>差异内容：HEAD = "HEAD"|api/@ohos.net.http.d.ts|
|新增API|NA|类名：RequestMethod；<br>API声明：POST = "POST"<br>差异内容：POST = "POST"|api/@ohos.net.http.d.ts|
|新增API|NA|类名：RequestMethod；<br>API声明：PUT = "PUT"<br>差异内容：PUT = "PUT"|api/@ohos.net.http.d.ts|
|新增API|NA|类名：RequestMethod；<br>API声明：DELETE = "DELETE"<br>差异内容：DELETE = "DELETE"|api/@ohos.net.http.d.ts|
|新增API|NA|类名：RequestMethod；<br>API声明：TRACE = "TRACE"<br>差异内容：TRACE = "TRACE"|api/@ohos.net.http.d.ts|
|新增API|NA|类名：RequestMethod；<br>API声明：CONNECT = "CONNECT"<br>差异内容：CONNECT = "CONNECT"|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export enum ResponseCode<br>差异内容：export enum ResponseCode|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：OK = 200<br>差异内容：OK = 200|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：CREATED<br>差异内容：CREATED|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：ACCEPTED<br>差异内容：ACCEPTED|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：NOT_AUTHORITATIVE<br>差异内容：NOT_AUTHORITATIVE|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：NO_CONTENT<br>差异内容：NO_CONTENT|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：RESET<br>差异内容：RESET|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：PARTIAL<br>差异内容：PARTIAL|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：MULT_CHOICE = 300<br>差异内容：MULT_CHOICE = 300|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：MOVED_PERM<br>差异内容：MOVED_PERM|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：MOVED_TEMP<br>差异内容：MOVED_TEMP|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：SEE_OTHER<br>差异内容：SEE_OTHER|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：NOT_MODIFIED<br>差异内容：NOT_MODIFIED|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：USE_PROXY<br>差异内容：USE_PROXY|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：BAD_REQUEST = 400<br>差异内容：BAD_REQUEST = 400|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：UNAUTHORIZED<br>差异内容：UNAUTHORIZED|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：PAYMENT_REQUIRED<br>差异内容：PAYMENT_REQUIRED|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：FORBIDDEN<br>差异内容：FORBIDDEN|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：NOT_FOUND<br>差异内容：NOT_FOUND|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：BAD_METHOD<br>差异内容：BAD_METHOD|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：NOT_ACCEPTABLE<br>差异内容：NOT_ACCEPTABLE|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：PROXY_AUTH<br>差异内容：PROXY_AUTH|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：CLIENT_TIMEOUT<br>差异内容：CLIENT_TIMEOUT|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：CONFLICT<br>差异内容：CONFLICT|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：GONE<br>差异内容：GONE|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：LENGTH_REQUIRED<br>差异内容：LENGTH_REQUIRED|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：PRECON_FAILED<br>差异内容：PRECON_FAILED|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：ENTITY_TOO_LARGE<br>差异内容：ENTITY_TOO_LARGE|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：REQ_TOO_LONG<br>差异内容：REQ_TOO_LONG|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：UNSUPPORTED_TYPE<br>差异内容：UNSUPPORTED_TYPE|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：INTERNAL_ERROR = 500<br>差异内容：INTERNAL_ERROR = 500|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：NOT_IMPLEMENTED<br>差异内容：NOT_IMPLEMENTED|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：BAD_GATEWAY<br>差异内容：BAD_GATEWAY|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：UNAVAILABLE<br>差异内容：UNAVAILABLE|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：GATEWAY_TIMEOUT<br>差异内容：GATEWAY_TIMEOUT|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：VERSION<br>差异内容：VERSION|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export enum HttpProtocol<br>差异内容：export enum HttpProtocol|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpProtocol；<br>API声明：HTTP1_1<br>差异内容：HTTP1_1|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpProtocol；<br>API声明：HTTP2<br>差异内容：HTTP2|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpProtocol；<br>API声明：HTTP3<br>差异内容：HTTP3|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export enum HttpDataType<br>差异内容：export enum HttpDataType|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpDataType；<br>API声明：STRING<br>差异内容：STRING|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpDataType；<br>API声明：OBJECT = 1<br>差异内容：OBJECT = 1|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpDataType；<br>API声明：ARRAY_BUFFER = 2<br>差异内容：ARRAY_BUFFER = 2|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export interface HttpResponse<br>差异内容：export interface HttpResponse|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpResponse；<br>API声明：result: string \| Object \| ArrayBuffer;<br>差异内容：result: string \| Object \| ArrayBuffer;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpResponse；<br>API声明：resultType: HttpDataType;<br>差异内容：resultType: HttpDataType;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpResponse；<br>API声明：responseCode: ResponseCode \| number;<br>差异内容：responseCode: ResponseCode \| number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpResponse；<br>API声明：header: Object;<br>差异内容：header: Object;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpResponse；<br>API声明：cookies: string;<br>差异内容：cookies: string;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpResponse；<br>API声明：performanceTiming: PerformanceTiming;<br>差异内容：performanceTiming: PerformanceTiming;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export interface PerformanceTiming<br>差异内容：export interface PerformanceTiming|api/@ohos.net.http.d.ts|
|新增API|NA|类名：PerformanceTiming；<br>API声明：dnsTiming: number;<br>差异内容：dnsTiming: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：PerformanceTiming；<br>API声明：tcpTiming: number;<br>差异内容：tcpTiming: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：PerformanceTiming；<br>API声明：tlsTiming: number;<br>差异内容：tlsTiming: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：PerformanceTiming；<br>API声明：firstSendTiming: number;<br>差异内容：firstSendTiming: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：PerformanceTiming；<br>API声明：firstReceiveTiming: number;<br>差异内容：firstReceiveTiming: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：PerformanceTiming；<br>API声明：totalFinishTiming: number;<br>差异内容：totalFinishTiming: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：PerformanceTiming；<br>API声明：redirectTiming: number;<br>差异内容：redirectTiming: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：PerformanceTiming；<br>API声明：responseHeaderTiming: number;<br>差异内容：responseHeaderTiming: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：PerformanceTiming；<br>API声明：responseBodyTiming: number;<br>差异内容：responseBodyTiming: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：PerformanceTiming；<br>API声明：totalTiming: number;<br>差异内容：totalTiming: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export interface DataReceiveProgressInfo<br>差异内容：export interface DataReceiveProgressInfo|api/@ohos.net.http.d.ts|
|新增API|NA|类名：DataReceiveProgressInfo；<br>API声明：receiveSize: number;<br>差异内容：receiveSize: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：DataReceiveProgressInfo；<br>API声明：totalSize: number;<br>差异内容：totalSize: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export interface DataSendProgressInfo<br>差异内容：export interface DataSendProgressInfo|api/@ohos.net.http.d.ts|
|新增API|NA|类名：DataSendProgressInfo；<br>API声明：sendSize: number;<br>差异内容：sendSize: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：DataSendProgressInfo；<br>API声明：totalSize: number;<br>差异内容：totalSize: number;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：function createHttpResponseCache(cacheSize?: number): HttpResponseCache;<br>差异内容：function createHttpResponseCache(cacheSize?: number): HttpResponseCache;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export interface HttpResponseCache<br>差异内容：export interface HttpResponseCache|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpResponseCache；<br>API声明：flush(callback: AsyncCallback\<void>): void;<br>差异内容：flush(callback: AsyncCallback\<void>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpResponseCache；<br>API声明：flush(): Promise\<void>;<br>差异内容：flush(): Promise\<void>;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpResponseCache；<br>API声明：delete(callback: AsyncCallback\<void>): void;<br>差异内容：delete(callback: AsyncCallback\<void>): void;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpResponseCache；<br>API声明：delete(): Promise\<void>;<br>差异内容：delete(): Promise\<void>;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace mdns<br>差异内容：declare namespace mdns|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：mdns；<br>API声明：type NetAddress = connection.NetAddress;<br>差异内容：type NetAddress = connection.NetAddress;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：mdns；<br>API声明：function addLocalService(context: Context, serviceInfo: LocalServiceInfo, callback: AsyncCallback\<LocalServiceInfo>): void;<br>差异内容：function addLocalService(context: Context, serviceInfo: LocalServiceInfo, callback: AsyncCallback\<LocalServiceInfo>): void;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：mdns；<br>API声明：function addLocalService(context: Context, serviceInfo: LocalServiceInfo): Promise\<LocalServiceInfo>;<br>差异内容：function addLocalService(context: Context, serviceInfo: LocalServiceInfo): Promise\<LocalServiceInfo>;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：mdns；<br>API声明：function removeLocalService(context: Context, serviceInfo: LocalServiceInfo, callback: AsyncCallback\<LocalServiceInfo>): void;<br>差异内容：function removeLocalService(context: Context, serviceInfo: LocalServiceInfo, callback: AsyncCallback\<LocalServiceInfo>): void;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：mdns；<br>API声明：function removeLocalService(context: Context, serviceInfo: LocalServiceInfo): Promise\<LocalServiceInfo>;<br>差异内容：function removeLocalService(context: Context, serviceInfo: LocalServiceInfo): Promise\<LocalServiceInfo>;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：mdns；<br>API声明：function createDiscoveryService(context: Context, serviceType: string): DiscoveryService;<br>差异内容：function createDiscoveryService(context: Context, serviceType: string): DiscoveryService;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：mdns；<br>API声明：function resolveLocalService(context: Context, serviceInfo: LocalServiceInfo, callback: AsyncCallback\<LocalServiceInfo>): void;<br>差异内容：function resolveLocalService(context: Context, serviceInfo: LocalServiceInfo, callback: AsyncCallback\<LocalServiceInfo>): void;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：mdns；<br>API声明：function resolveLocalService(context: Context, serviceInfo: LocalServiceInfo): Promise\<LocalServiceInfo>;<br>差异内容：function resolveLocalService(context: Context, serviceInfo: LocalServiceInfo): Promise\<LocalServiceInfo>;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：mdns；<br>API声明：export interface DiscoveryService<br>差异内容：export interface DiscoveryService|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：DiscoveryService；<br>API声明：on(type: 'discoveryStart', callback: Callback\<DiscoveryEventInfo>): void;<br>差异内容：on(type: 'discoveryStart', callback: Callback\<DiscoveryEventInfo>): void;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：DiscoveryService；<br>API声明：off(type: 'discoveryStart', callback?: Callback\<DiscoveryEventInfo>): void;<br>差异内容：off(type: 'discoveryStart', callback?: Callback\<DiscoveryEventInfo>): void;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：DiscoveryService；<br>API声明：on(type: 'discoveryStop', callback: Callback\<DiscoveryEventInfo>): void;<br>差异内容：on(type: 'discoveryStop', callback: Callback\<DiscoveryEventInfo>): void;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：DiscoveryService；<br>API声明：off(type: 'discoveryStop', callback?: Callback\<DiscoveryEventInfo>): void;<br>差异内容：off(type: 'discoveryStop', callback?: Callback\<DiscoveryEventInfo>): void;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：DiscoveryService；<br>API声明：on(type: 'serviceFound', callback: Callback\<LocalServiceInfo>): void;<br>差异内容：on(type: 'serviceFound', callback: Callback\<LocalServiceInfo>): void;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：DiscoveryService；<br>API声明：off(type: 'serviceFound', callback?: Callback\<LocalServiceInfo>): void;<br>差异内容：off(type: 'serviceFound', callback?: Callback\<LocalServiceInfo>): void;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：DiscoveryService；<br>API声明：on(type: 'serviceLost', callback: Callback\<LocalServiceInfo>): void;<br>差异内容：on(type: 'serviceLost', callback: Callback\<LocalServiceInfo>): void;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：DiscoveryService；<br>API声明：off(type: 'serviceLost', callback?: Callback\<LocalServiceInfo>): void;<br>差异内容：off(type: 'serviceLost', callback?: Callback\<LocalServiceInfo>): void;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：DiscoveryService；<br>API声明：startSearchingMDNS(): void;<br>差异内容：startSearchingMDNS(): void;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：DiscoveryService；<br>API声明：stopSearchingMDNS(): void;<br>差异内容：stopSearchingMDNS(): void;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：mdns；<br>API声明：export interface LocalServiceInfo<br>差异内容：export interface LocalServiceInfo|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：LocalServiceInfo；<br>API声明：serviceType: string;<br>差异内容：serviceType: string;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：LocalServiceInfo；<br>API声明：serviceName: string;<br>差异内容：serviceName: string;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：LocalServiceInfo；<br>API声明：port?: number;<br>差异内容：port?: number;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：LocalServiceInfo；<br>API声明：host?: NetAddress;<br>差异内容：host?: NetAddress;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：LocalServiceInfo；<br>API声明：serviceAttribute?: Array\<ServiceAttribute>;<br>差异内容：serviceAttribute?: Array\<ServiceAttribute>;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：mdns；<br>API声明：export interface ServiceAttribute<br>差异内容：export interface ServiceAttribute|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：ServiceAttribute；<br>API声明：key: string;<br>差异内容：key: string;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：ServiceAttribute；<br>API声明：value: Array\<number>;<br>差异内容：value: Array\<number>;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：mdns；<br>API声明：export interface DiscoveryEventInfo<br>差异内容：export interface DiscoveryEventInfo|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：DiscoveryEventInfo；<br>API声明：serviceInfo: LocalServiceInfo;<br>差异内容：serviceInfo: LocalServiceInfo;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：DiscoveryEventInfo；<br>API声明：errorCode?: MdnsError;<br>差异内容：errorCode?: MdnsError;|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：mdns；<br>API声明：export enum MdnsError<br>差异内容：export enum MdnsError|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：MdnsError；<br>API声明：INTERNAL_ERROR = 0<br>差异内容：INTERNAL_ERROR = 0|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：MdnsError；<br>API声明：ALREADY_ACTIVE = 1<br>差异内容：ALREADY_ACTIVE = 1|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：MdnsError；<br>API声明：MAX_LIMIT = 2<br>差异内容：MAX_LIMIT = 2|api/@ohos.net.mdns.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace networkSecurity<br>差异内容：declare namespace networkSecurity|api/@ohos.net.networkSecurity.d.ts|
|新增API|NA|类名：networkSecurity；<br>API声明：export enum CertType<br>差异内容：export enum CertType|api/@ohos.net.networkSecurity.d.ts|
|新增API|NA|类名：CertType；<br>API声明：CERT_TYPE_PEM = 0<br>差异内容：CERT_TYPE_PEM = 0|api/@ohos.net.networkSecurity.d.ts|
|新增API|NA|类名：CertType；<br>API声明：CERT_TYPE_DER = 1<br>差异内容：CERT_TYPE_DER = 1|api/@ohos.net.networkSecurity.d.ts|
|新增API|NA|类名：networkSecurity；<br>API声明：export interface CertBlob<br>差异内容：export interface CertBlob|api/@ohos.net.networkSecurity.d.ts|
|新增API|NA|类名：CertBlob；<br>API声明：type: CertType;<br>差异内容：type: CertType;|api/@ohos.net.networkSecurity.d.ts|
|新增API|NA|类名：CertBlob；<br>API声明：data: string \| ArrayBuffer;<br>差异内容：data: string \| ArrayBuffer;|api/@ohos.net.networkSecurity.d.ts|
|新增API|NA|类名：networkSecurity；<br>API声明：export function certVerification(cert: CertBlob, caCert?: CertBlob): Promise\<number>;<br>差异内容：export function certVerification(cert: CertBlob, caCert?: CertBlob): Promise\<number>;|api/@ohos.net.networkSecurity.d.ts|
|新增API|NA|类名：networkSecurity；<br>API声明：export function certVerificationSync(cert: CertBlob, caCert?: CertBlob): number;<br>差异内容：export function certVerificationSync(cert: CertBlob, caCert?: CertBlob): number;|api/@ohos.net.networkSecurity.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace policy<br>差异内容：declare namespace policy|api/@ohos.net.policy.d.ts|
|新增API|NA|类名：policy；<br>API声明：type NetBearType = connection.NetBearType;<br>差异内容：type NetBearType = connection.NetBearType;|api/@ohos.net.policy.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace sharing<br>差异内容：declare namespace sharing|api/@ohos.net.sharing.d.ts|
|新增API|NA|类名：sharing；<br>API声明：type NetHandle = connection.NetHandle;<br>差异内容：type NetHandle = connection.NetHandle;|api/@ohos.net.sharing.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace socket<br>差异内容：declare namespace socket|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export type X509CertRawData = cert.EncodingBlob;<br>差异内容：export type X509CertRawData = cert.EncodingBlob;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function constructUDPSocketInstance(): UDPSocket;<br>差异内容：function constructUDPSocketInstance(): UDPSocket;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function constructMulticastSocketInstance(): MulticastSocket;<br>差异内容：function constructMulticastSocketInstance(): MulticastSocket;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function constructTCPSocketInstance(): TCPSocket;<br>差异内容：function constructTCPSocketInstance(): TCPSocket;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function constructTLSSocketInstance(): TLSSocket;<br>差异内容：function constructTLSSocketInstance(): TLSSocket;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function constructTCPSocketServerInstance(): TCPSocketServer;<br>差异内容：function constructTCPSocketServerInstance(): TCPSocketServer;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function constructTLSSocketServerInstance(): TLSSocketServer;<br>差异内容：function constructTLSSocketServerInstance(): TLSSocketServer;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function constructLocalSocketInstance(): LocalSocket;<br>差异内容：function constructLocalSocketInstance(): LocalSocket;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function constructLocalSocketServerInstance(): LocalSocketServer;<br>差异内容：function constructLocalSocketServerInstance(): LocalSocketServer;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface UDPSendOptions<br>差异内容：export interface UDPSendOptions|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSendOptions；<br>API声明：data: string \| ArrayBuffer;<br>差异内容：data: string \| ArrayBuffer;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSendOptions；<br>API声明：address: NetAddress;<br>差异内容：address: NetAddress;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface ExtraOptionsBase<br>差异内容：export interface ExtraOptionsBase|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：ExtraOptionsBase；<br>API声明：receiveBufferSize?: number;<br>差异内容：receiveBufferSize?: number;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：ExtraOptionsBase；<br>API声明：sendBufferSize?: number;<br>差异内容：sendBufferSize?: number;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：ExtraOptionsBase；<br>API声明：reuseAddress?: boolean;<br>差异内容：reuseAddress?: boolean;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：ExtraOptionsBase；<br>API声明：socketTimeout?: number;<br>差异内容：socketTimeout?: number;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface UDPExtraOptions<br>差异内容：export interface UDPExtraOptions|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPExtraOptions；<br>API声明：broadcast?: boolean;<br>差异内容：broadcast?: boolean;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface SocketStateBase<br>差异内容：export interface SocketStateBase|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：SocketStateBase；<br>API声明：isBound: boolean;<br>差异内容：isBound: boolean;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：SocketStateBase；<br>API声明：isClose: boolean;<br>差异内容：isClose: boolean;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：SocketStateBase；<br>API声明：isConnected: boolean;<br>差异内容：isConnected: boolean;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface SocketRemoteInfo<br>差异内容：export interface SocketRemoteInfo|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：SocketRemoteInfo；<br>API声明：address: string;<br>差异内容：address: string;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：SocketRemoteInfo；<br>API声明：family: 'IPv4' \| 'IPv6';<br>差异内容：family: 'IPv4' \| 'IPv6';|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：SocketRemoteInfo；<br>API声明：port: number;<br>差异内容：port: number;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：SocketRemoteInfo；<br>API声明：size: number;<br>差异内容：size: number;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface LocalSocketMessageInfo<br>差异内容：export interface LocalSocketMessageInfo|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketMessageInfo；<br>API声明：message: ArrayBuffer;<br>差异内容：message: ArrayBuffer;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketMessageInfo；<br>API声明：address: string;<br>差异内容：address: string;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketMessageInfo；<br>API声明：size: number;<br>差异内容：size: number;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface LocalAddress<br>差异内容：export interface LocalAddress|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalAddress；<br>API声明：address: string;<br>差异内容：address: string;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface LocalConnectOptions<br>差异内容：export interface LocalConnectOptions|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalConnectOptions；<br>API声明：address: LocalAddress;<br>差异内容：address: LocalAddress;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalConnectOptions；<br>API声明：timeout?: number;<br>差异内容：timeout?: number;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface LocalSendOptions<br>差异内容：export interface LocalSendOptions|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSendOptions；<br>API声明：data: string \| ArrayBuffer;<br>差异内容：data: string \| ArrayBuffer;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSendOptions；<br>API声明：encoding?: string;<br>差异内容：encoding?: string;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface UDPSocket<br>差异内容：export interface UDPSocket|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：bind(address: NetAddress, callback: AsyncCallback\<void>): void;<br>差异内容：bind(address: NetAddress, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：bind(address: NetAddress): Promise\<void>;<br>差异内容：bind(address: NetAddress): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：send(options: UDPSendOptions, callback: AsyncCallback\<void>): void;<br>差异内容：send(options: UDPSendOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：send(options: UDPSendOptions): Promise\<void>;<br>差异内容：send(options: UDPSendOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：close(callback: AsyncCallback\<void>): void;<br>差异内容：close(callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：close(): Promise\<void>;<br>差异内容：close(): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：getState(callback: AsyncCallback\<SocketStateBase>): void;<br>差异内容：getState(callback: AsyncCallback\<SocketStateBase>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：getState(): Promise\<SocketStateBase>;<br>差异内容：getState(): Promise\<SocketStateBase>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：setExtraOptions(options: UDPExtraOptions, callback: AsyncCallback\<void>): void;<br>差异内容：setExtraOptions(options: UDPExtraOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：setExtraOptions(options: UDPExtraOptions): Promise\<void>;<br>差异内容：setExtraOptions(options: UDPExtraOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：on(type: 'message', callback: Callback\<SocketMessageInfo>): void;<br>差异内容：on(type: 'message', callback: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;<br>差异内容：off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：on(type: 'listening' \| 'close', callback: Callback\<void>): void;<br>差异内容：on(type: 'listening' \| 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：on(type: 'listening' \| 'close', callback: Callback\<void>): void;<br>差异内容：on(type: 'listening' \| 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：off(type: 'listening' \| 'close', callback?: Callback\<void>): void;<br>差异内容：off(type: 'listening' \| 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：off(type: 'listening' \| 'close', callback?: Callback\<void>): void;<br>差异内容：off(type: 'listening' \| 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface MulticastSocket<br>差异内容：export interface MulticastSocket|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：MulticastSocket；<br>API声明：addMembership(multicastAddress: NetAddress, callback: AsyncCallback\<void>): void;<br>差异内容：addMembership(multicastAddress: NetAddress, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：MulticastSocket；<br>API声明：addMembership(multicastAddress: NetAddress): Promise\<void>;<br>差异内容：addMembership(multicastAddress: NetAddress): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：MulticastSocket；<br>API声明：dropMembership(multicastAddress: NetAddress, callback: AsyncCallback\<void>): void;<br>差异内容：dropMembership(multicastAddress: NetAddress, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：MulticastSocket；<br>API声明：dropMembership(multicastAddress: NetAddress): Promise\<void>;<br>差异内容：dropMembership(multicastAddress: NetAddress): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：MulticastSocket；<br>API声明：setMulticastTTL(ttl: number, callback: AsyncCallback\<void>): void;<br>差异内容：setMulticastTTL(ttl: number, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：MulticastSocket；<br>API声明：setMulticastTTL(ttl: number): Promise\<void>;<br>差异内容：setMulticastTTL(ttl: number): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：MulticastSocket；<br>API声明：getMulticastTTL(callback: AsyncCallback\<number>): void;<br>差异内容：getMulticastTTL(callback: AsyncCallback\<number>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：MulticastSocket；<br>API声明：getMulticastTTL(): Promise\<number>;<br>差异内容：getMulticastTTL(): Promise\<number>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：MulticastSocket；<br>API声明：setLoopbackMode(flag: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：setLoopbackMode(flag: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：MulticastSocket；<br>API声明：setLoopbackMode(flag: boolean): Promise\<void>;<br>差异内容：setLoopbackMode(flag: boolean): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：MulticastSocket；<br>API声明：getLoopbackMode(callback: AsyncCallback\<boolean>): void;<br>差异内容：getLoopbackMode(callback: AsyncCallback\<boolean>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：MulticastSocket；<br>API声明：getLoopbackMode(): Promise\<boolean>;<br>差异内容：getLoopbackMode(): Promise\<boolean>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface LocalSocket<br>差异内容：export interface LocalSocket|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocket；<br>API声明：bind(address: LocalAddress): Promise\<void>;<br>差异内容：bind(address: LocalAddress): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocket；<br>API声明：connect(options: LocalConnectOptions): Promise\<void>;<br>差异内容：connect(options: LocalConnectOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocket；<br>API声明：send(options: LocalSendOptions): Promise\<void>;<br>差异内容：send(options: LocalSendOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocket；<br>API声明：close(): Promise\<void>;<br>差异内容：close(): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocket；<br>API声明：getState(): Promise\<SocketStateBase>;<br>差异内容：getState(): Promise\<SocketStateBase>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocket；<br>API声明：getSocketFd(): Promise\<number>;<br>差异内容：getSocketFd(): Promise\<number>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocket；<br>API声明：setExtraOptions(options: ExtraOptionsBase): Promise\<void>;<br>差异内容：setExtraOptions(options: ExtraOptionsBase): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocket；<br>API声明：getExtraOptions(): Promise\<ExtraOptionsBase>;<br>差异内容：getExtraOptions(): Promise\<ExtraOptionsBase>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocket；<br>API声明：on(type: 'message', callback: Callback\<LocalSocketMessageInfo>): void;<br>差异内容：on(type: 'message', callback: Callback\<LocalSocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocket；<br>API声明：off(type: 'message', callback?: Callback\<LocalSocketMessageInfo>): void;<br>差异内容：off(type: 'message', callback?: Callback\<LocalSocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocket；<br>API声明：on(type: 'connect', callback: Callback\<void>): void;<br>差异内容：on(type: 'connect', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocket；<br>API声明：off(type: 'connect', callback?: Callback\<void>): void;<br>差异内容：off(type: 'connect', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocket；<br>API声明：on(type: 'close', callback: Callback\<void>): void;<br>差异内容：on(type: 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocket；<br>API声明：off(type: 'close', callback?: Callback\<void>): void;<br>差异内容：off(type: 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocket；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocket；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface LocalSocketConnection<br>差异内容：export interface LocalSocketConnection|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketConnection；<br>API声明：clientId: number;<br>差异内容：clientId: number;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketConnection；<br>API声明：send(options: LocalSendOptions): Promise\<void>;<br>差异内容：send(options: LocalSendOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketConnection；<br>API声明：close(): Promise\<void>;<br>差异内容：close(): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketConnection；<br>API声明：on(type: 'message', callback: Callback\<LocalSocketMessageInfo>): void;<br>差异内容：on(type: 'message', callback: Callback\<LocalSocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketConnection；<br>API声明：off(type: 'message', callback?: Callback\<LocalSocketMessageInfo>): void;<br>差异内容：off(type: 'message', callback?: Callback\<LocalSocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketConnection；<br>API声明：on(type: 'close', callback: Callback\<void>): void;<br>差异内容：on(type: 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketConnection；<br>API声明：off(type: 'close', callback?: Callback\<void>): void;<br>差异内容：off(type: 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketConnection；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketConnection；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface LocalSocketServer<br>差异内容：export interface LocalSocketServer|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketServer；<br>API声明：listen(address: LocalAddress): Promise\<void>;<br>差异内容：listen(address: LocalAddress): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketServer；<br>API声明：getState(): Promise\<SocketStateBase>;<br>差异内容：getState(): Promise\<SocketStateBase>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketServer；<br>API声明：setExtraOptions(options: ExtraOptionsBase): Promise\<void>;<br>差异内容：setExtraOptions(options: ExtraOptionsBase): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketServer；<br>API声明：getExtraOptions(): Promise\<ExtraOptionsBase>;<br>差异内容：getExtraOptions(): Promise\<ExtraOptionsBase>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketServer；<br>API声明：on(type: 'connect', callback: Callback\<LocalSocketConnection>): void;<br>差异内容：on(type: 'connect', callback: Callback\<LocalSocketConnection>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketServer；<br>API声明：off(type: 'connect', callback?: Callback\<LocalSocketConnection>): void;<br>差异内容：off(type: 'connect', callback?: Callback\<LocalSocketConnection>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketServer；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketServer；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface TCPConnectOptions<br>差异内容：export interface TCPConnectOptions|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPConnectOptions；<br>API声明：address: NetAddress;<br>差异内容：address: NetAddress;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPConnectOptions；<br>API声明：timeout?: number;<br>差异内容：timeout?: number;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface TCPSendOptions<br>差异内容：export interface TCPSendOptions|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSendOptions；<br>API声明：data: string \| ArrayBuffer;<br>差异内容：data: string \| ArrayBuffer;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSendOptions；<br>API声明：encoding?: string;<br>差异内容：encoding?: string;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface TCPExtraOptions<br>差异内容：export interface TCPExtraOptions|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPExtraOptions；<br>API声明：keepAlive?: boolean;<br>差异内容：keepAlive?: boolean;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPExtraOptions；<br>API声明：OOBInline?: boolean;<br>差异内容：OOBInline?: boolean;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPExtraOptions；<br>API声明：TCPNoDelay?: boolean;<br>差异内容：TCPNoDelay?: boolean;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPExtraOptions；<br>API声明：socketLinger?: {<br>            on: boolean;<br>            linger: number;<br>        };<br>差异内容：socketLinger?: {<br>            on: boolean;<br>            linger: number;<br>        };|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface TCPSocket<br>差异内容：export interface TCPSocket|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：bind(address: NetAddress, callback: AsyncCallback\<void>): void;<br>差异内容：bind(address: NetAddress, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：bind(address: NetAddress): Promise\<void>;<br>差异内容：bind(address: NetAddress): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：connect(options: TCPConnectOptions, callback: AsyncCallback\<void>): void;<br>差异内容：connect(options: TCPConnectOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：connect(options: TCPConnectOptions): Promise\<void>;<br>差异内容：connect(options: TCPConnectOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：send(options: TCPSendOptions, callback: AsyncCallback\<void>): void;<br>差异内容：send(options: TCPSendOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：send(options: TCPSendOptions): Promise\<void>;<br>差异内容：send(options: TCPSendOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：close(callback: AsyncCallback\<void>): void;<br>差异内容：close(callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：close(): Promise\<void>;<br>差异内容：close(): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：getRemoteAddress(callback: AsyncCallback\<NetAddress>): void;<br>差异内容：getRemoteAddress(callback: AsyncCallback\<NetAddress>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：getRemoteAddress(): Promise\<NetAddress>;<br>差异内容：getRemoteAddress(): Promise\<NetAddress>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：getState(callback: AsyncCallback\<SocketStateBase>): void;<br>差异内容：getState(callback: AsyncCallback\<SocketStateBase>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：getState(): Promise\<SocketStateBase>;<br>差异内容：getState(): Promise\<SocketStateBase>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：getSocketFd(callback: AsyncCallback\<number>): void;<br>差异内容：getSocketFd(callback: AsyncCallback\<number>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：getSocketFd(): Promise\<number>;<br>差异内容：getSocketFd(): Promise\<number>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback\<void>): void;<br>差异内容：setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：setExtraOptions(options: TCPExtraOptions): Promise\<void>;<br>差异内容：setExtraOptions(options: TCPExtraOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：on(type: 'message', callback: Callback\<SocketMessageInfo>): void;<br>差异内容：on(type: 'message', callback: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;<br>差异内容：off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：on(type: 'connect' \| 'close', callback: Callback\<void>): void;<br>差异内容：on(type: 'connect' \| 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：on(type: 'connect' \| 'close', callback: Callback\<void>): void;<br>差异内容：on(type: 'connect' \| 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：off(type: 'connect' \| 'close', callback?: Callback\<void>): void;<br>差异内容：off(type: 'connect' \| 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：off(type: 'connect' \| 'close', callback?: Callback\<void>): void;<br>差异内容：off(type: 'connect' \| 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface TLSSocket<br>差异内容：export interface TLSSocket|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：bind(address: NetAddress, callback: AsyncCallback\<void>): void;<br>差异内容：bind(address: NetAddress, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：bind(address: NetAddress): Promise\<void>;<br>差异内容：bind(address: NetAddress): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：getRemoteAddress(callback: AsyncCallback\<NetAddress>): void;<br>差异内容：getRemoteAddress(callback: AsyncCallback\<NetAddress>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：getRemoteAddress(): Promise\<NetAddress>;<br>差异内容：getRemoteAddress(): Promise\<NetAddress>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：getState(callback: AsyncCallback\<SocketStateBase>): void;<br>差异内容：getState(callback: AsyncCallback\<SocketStateBase>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：getState(): Promise\<SocketStateBase>;<br>差异内容：getState(): Promise\<SocketStateBase>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback\<void>): void;<br>差异内容：setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：setExtraOptions(options: TCPExtraOptions): Promise\<void>;<br>差异内容：setExtraOptions(options: TCPExtraOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：on(type: 'message', callback: Callback\<SocketMessageInfo>): void;<br>差异内容：on(type: 'message', callback: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;<br>差异内容：off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：on(type: 'connect' \| 'close', callback: Callback\<void>): void;<br>差异内容：on(type: 'connect' \| 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：on(type: 'connect' \| 'close', callback: Callback\<void>): void;<br>差异内容：on(type: 'connect' \| 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：off(type: 'connect' \| 'close', callback?: Callback\<void>): void;<br>差异内容：off(type: 'connect' \| 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：off(type: 'connect' \| 'close', callback?: Callback\<void>): void;<br>差异内容：off(type: 'connect' \| 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：getCertificate(callback: AsyncCallback\<X509CertRawData>): void;<br>差异内容：getCertificate(callback: AsyncCallback\<X509CertRawData>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：getCertificate(): Promise\<X509CertRawData>;<br>差异内容：getCertificate(): Promise\<X509CertRawData>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：getRemoteCertificate(callback: AsyncCallback\<X509CertRawData>): void;<br>差异内容：getRemoteCertificate(callback: AsyncCallback\<X509CertRawData>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：getRemoteCertificate(): Promise\<X509CertRawData>;<br>差异内容：getRemoteCertificate(): Promise\<X509CertRawData>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：getProtocol(callback: AsyncCallback\<string>): void;<br>差异内容：getProtocol(callback: AsyncCallback\<string>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：getProtocol(): Promise\<string>;<br>差异内容：getProtocol(): Promise\<string>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：getCipherSuite(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：getCipherSuite(callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：getCipherSuite(): Promise\<Array\<string>>;<br>差异内容：getCipherSuite(): Promise\<Array\<string>>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：getSignatureAlgorithms(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：getSignatureAlgorithms(callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：getSignatureAlgorithms(): Promise\<Array\<string>>;<br>差异内容：getSignatureAlgorithms(): Promise\<Array\<string>>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：connect(options: TLSConnectOptions, callback: AsyncCallback\<void>): void;<br>差异内容：connect(options: TLSConnectOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：connect(options: TLSConnectOptions): Promise\<void>;<br>差异内容：connect(options: TLSConnectOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：send(data: string, callback: AsyncCallback\<void>): void;<br>差异内容：send(data: string, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：send(data: string): Promise\<void>;<br>差异内容：send(data: string): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：close(callback: AsyncCallback\<void>): void;<br>差异内容：close(callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：close(): Promise\<void>;<br>差异内容：close(): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface TLSSecureOptions<br>差异内容：export interface TLSSecureOptions|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSecureOptions；<br>API声明：ca: string \| Array\<string>;<br>差异内容：ca: string \| Array\<string>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSecureOptions；<br>API声明：cert?: string;<br>差异内容：cert?: string;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSecureOptions；<br>API声明：key?: string;<br>差异内容：key?: string;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSecureOptions；<br>API声明：password?: string;<br>差异内容：password?: string;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSecureOptions；<br>API声明：protocols?: Protocol \| Array\<Protocol>;<br>差异内容：protocols?: Protocol \| Array\<Protocol>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSecureOptions；<br>API声明：useRemoteCipherPrefer?: boolean;<br>差异内容：useRemoteCipherPrefer?: boolean;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSecureOptions；<br>API声明：signatureAlgorithms?: string;<br>差异内容：signatureAlgorithms?: string;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSecureOptions；<br>API声明：cipherSuite?: string;<br>差异内容：cipherSuite?: string;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface TLSConnectOptions<br>差异内容：export interface TLSConnectOptions|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSConnectOptions；<br>API声明：address: NetAddress;<br>差异内容：address: NetAddress;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSConnectOptions；<br>API声明：secureOptions: TLSSecureOptions;<br>差异内容：secureOptions: TLSSecureOptions;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSConnectOptions；<br>API声明：ALPNProtocols?: Array\<string>;<br>差异内容：ALPNProtocols?: Array\<string>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export enum Protocol<br>差异内容：export enum Protocol|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：Protocol；<br>API声明：TLSv12 = "TLSv1.2"<br>差异内容：TLSv12 = "TLSv1.2"|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：Protocol；<br>API声明：TLSv13 = "TLSv1.3"<br>差异内容：TLSv13 = "TLSv1.3"|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface TCPSocketConnection<br>差异内容：export interface TCPSocketConnection|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketConnection；<br>API声明：clientId: number;<br>差异内容：clientId: number;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketConnection；<br>API声明：send(options: TCPSendOptions, callback: AsyncCallback\<void>): void;<br>差异内容：send(options: TCPSendOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketConnection；<br>API声明：send(options: TCPSendOptions): Promise\<void>;<br>差异内容：send(options: TCPSendOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketConnection；<br>API声明：close(callback: AsyncCallback\<void>): void;<br>差异内容：close(callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketConnection；<br>API声明：close(): Promise\<void>;<br>差异内容：close(): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketConnection；<br>API声明：getRemoteAddress(callback: AsyncCallback\<NetAddress>): void;<br>差异内容：getRemoteAddress(callback: AsyncCallback\<NetAddress>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketConnection；<br>API声明：getRemoteAddress(): Promise\<NetAddress>;<br>差异内容：getRemoteAddress(): Promise\<NetAddress>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketConnection；<br>API声明：on(type: 'message', callback: Callback\<SocketMessageInfo>): void;<br>差异内容：on(type: 'message', callback: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketConnection；<br>API声明：off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;<br>差异内容：off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketConnection；<br>API声明：on(type: 'close', callback: Callback\<void>): void;<br>差异内容：on(type: 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketConnection；<br>API声明：off(type: 'close', callback?: Callback\<void>): void;<br>差异内容：off(type: 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketConnection；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketConnection；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface TCPSocketServer<br>差异内容：export interface TCPSocketServer|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketServer；<br>API声明：listen(address: NetAddress, callback: AsyncCallback\<void>): void;<br>差异内容：listen(address: NetAddress, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketServer；<br>API声明：listen(address: NetAddress): Promise\<void>;<br>差异内容：listen(address: NetAddress): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketServer；<br>API声明：getState(callback: AsyncCallback\<SocketStateBase>): void;<br>差异内容：getState(callback: AsyncCallback\<SocketStateBase>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketServer；<br>API声明：getState(): Promise\<SocketStateBase>;<br>差异内容：getState(): Promise\<SocketStateBase>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketServer；<br>API声明：setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback\<void>): void;<br>差异内容：setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketServer；<br>API声明：setExtraOptions(options: TCPExtraOptions): Promise\<void>;<br>差异内容：setExtraOptions(options: TCPExtraOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketServer；<br>API声明：on(type: 'connect', callback: Callback\<TCPSocketConnection>): void;<br>差异内容：on(type: 'connect', callback: Callback\<TCPSocketConnection>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketServer；<br>API声明：off(type: 'connect', callback?: Callback\<TCPSocketConnection>): void;<br>差异内容：off(type: 'connect', callback?: Callback\<TCPSocketConnection>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketServer；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketServer；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface TLSSocketConnection<br>差异内容：export interface TLSSocketConnection|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：clientId: number;<br>差异内容：clientId: number;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：send(data: string, callback: AsyncCallback\<void>): void;<br>差异内容：send(data: string, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：send(data: string): Promise\<void>;<br>差异内容：send(data: string): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：close(callback: AsyncCallback\<void>): void;<br>差异内容：close(callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：close(): Promise\<void>;<br>差异内容：close(): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：getRemoteAddress(callback: AsyncCallback\<NetAddress>): void;<br>差异内容：getRemoteAddress(callback: AsyncCallback\<NetAddress>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：getRemoteAddress(): Promise\<NetAddress>;<br>差异内容：getRemoteAddress(): Promise\<NetAddress>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：getRemoteCertificate(callback: AsyncCallback\<X509CertRawData>): void;<br>差异内容：getRemoteCertificate(callback: AsyncCallback\<X509CertRawData>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：getRemoteCertificate(): Promise\<X509CertRawData>;<br>差异内容：getRemoteCertificate(): Promise\<X509CertRawData>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：getCipherSuite(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：getCipherSuite(callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：getCipherSuite(): Promise\<Array\<string>>;<br>差异内容：getCipherSuite(): Promise\<Array\<string>>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：getSignatureAlgorithms(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：getSignatureAlgorithms(callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：getSignatureAlgorithms(): Promise\<Array\<string>>;<br>差异内容：getSignatureAlgorithms(): Promise\<Array\<string>>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：on(type: 'message', callback: Callback\<SocketMessageInfo>): void;<br>差异内容：on(type: 'message', callback: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;<br>差异内容：off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：on(type: 'close', callback: Callback\<void>): void;<br>差异内容：on(type: 'close', callback: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：off(type: 'close', callback?: Callback\<void>): void;<br>差异内容：off(type: 'close', callback?: Callback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface SocketMessageInfo<br>差异内容：export interface SocketMessageInfo|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：SocketMessageInfo；<br>API声明：message: ArrayBuffer;<br>差异内容：message: ArrayBuffer;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：SocketMessageInfo；<br>API声明：remoteInfo: SocketRemoteInfo;<br>差异内容：remoteInfo: SocketRemoteInfo;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface TLSSocketServer<br>差异内容：export interface TLSSocketServer|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketServer；<br>API声明：listen(options: TLSConnectOptions, callback: AsyncCallback\<void>): void;<br>差异内容：listen(options: TLSConnectOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketServer；<br>API声明：listen(options: TLSConnectOptions): Promise\<void>;<br>差异内容：listen(options: TLSConnectOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketServer；<br>API声明：getState(callback: AsyncCallback\<SocketStateBase>): void;<br>差异内容：getState(callback: AsyncCallback\<SocketStateBase>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketServer；<br>API声明：getState(): Promise\<SocketStateBase>;<br>差异内容：getState(): Promise\<SocketStateBase>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketServer；<br>API声明：setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback\<void>): void;<br>差异内容：setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback\<void>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketServer；<br>API声明：setExtraOptions(options: TCPExtraOptions): Promise\<void>;<br>差异内容：setExtraOptions(options: TCPExtraOptions): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketServer；<br>API声明：getCertificate(callback: AsyncCallback\<X509CertRawData>): void;<br>差异内容：getCertificate(callback: AsyncCallback\<X509CertRawData>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketServer；<br>API声明：getCertificate(): Promise\<X509CertRawData>;<br>差异内容：getCertificate(): Promise\<X509CertRawData>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketServer；<br>API声明：getProtocol(callback: AsyncCallback\<string>): void;<br>差异内容：getProtocol(callback: AsyncCallback\<string>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketServer；<br>API声明：getProtocol(): Promise\<string>;<br>差异内容：getProtocol(): Promise\<string>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketServer；<br>API声明：on(type: 'connect', callback: Callback\<TLSSocketConnection>): void;<br>差异内容：on(type: 'connect', callback: Callback\<TLSSocketConnection>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketServer；<br>API声明：off(type: 'connect', callback?: Callback\<TLSSocketConnection>): void;<br>差异内容：off(type: 'connect', callback?: Callback\<TLSSocketConnection>): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketServer；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketServer；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace statistics<br>差异内容：declare namespace statistics|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getIfaceRxBytes(nic: string, callback: AsyncCallback\<number>): void;<br>差异内容：function getIfaceRxBytes(nic: string, callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getIfaceRxBytes(nic: string): Promise\<number>;<br>差异内容：function getIfaceRxBytes(nic: string): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getIfaceTxBytes(nic: string, callback: AsyncCallback\<number>): void;<br>差异内容：function getIfaceTxBytes(nic: string, callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getIfaceTxBytes(nic: string): Promise\<number>;<br>差异内容：function getIfaceTxBytes(nic: string): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getCellularRxBytes(callback: AsyncCallback\<number>): void;<br>差异内容：function getCellularRxBytes(callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getCellularRxBytes(): Promise\<number>;<br>差异内容：function getCellularRxBytes(): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getCellularTxBytes(callback: AsyncCallback\<number>): void;<br>差异内容：function getCellularTxBytes(callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getCellularTxBytes(): Promise\<number>;<br>差异内容：function getCellularTxBytes(): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getAllRxBytes(callback: AsyncCallback\<number>): void;<br>差异内容：function getAllRxBytes(callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getAllRxBytes(): Promise\<number>;<br>差异内容：function getAllRxBytes(): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getAllTxBytes(callback: AsyncCallback\<number>): void;<br>差异内容：function getAllTxBytes(callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getAllTxBytes(): Promise\<number>;<br>差异内容：function getAllTxBytes(): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getUidRxBytes(uid: number, callback: AsyncCallback\<number>): void;<br>差异内容：function getUidRxBytes(uid: number, callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getUidRxBytes(uid: number): Promise\<number>;<br>差异内容：function getUidRxBytes(uid: number): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getUidTxBytes(uid: number, callback: AsyncCallback\<number>): void;<br>差异内容：function getUidTxBytes(uid: number, callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getUidTxBytes(uid: number): Promise\<number>;<br>差异内容：function getUidTxBytes(uid: number): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getSockfdRxBytes(sockfd: number, callback: AsyncCallback\<number>): void;<br>差异内容：function getSockfdRxBytes(sockfd: number, callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getSockfdRxBytes(sockfd: number): Promise\<number>;<br>差异内容：function getSockfdRxBytes(sockfd: number): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getSockfdTxBytes(sockfd: number, callback: AsyncCallback\<number>): void;<br>差异内容：function getSockfdTxBytes(sockfd: number, callback: AsyncCallback\<number>): void;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：statistics；<br>API声明：function getSockfdTxBytes(sockfd: number): Promise\<number>;<br>差异内容：function getSockfdTxBytes(sockfd: number): Promise\<number>;|api/@ohos.net.statistics.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace vpn<br>差异内容：declare namespace vpn|api/@ohos.net.vpn.d.ts|
|新增API|NA|类名：vpn；<br>API声明：export type LinkAddress = connection.LinkAddress;<br>差异内容：export type LinkAddress = connection.LinkAddress;|api/@ohos.net.vpn.d.ts|
|新增API|NA|类名：vpn；<br>API声明：export type RouteInfo = connection.RouteInfo;<br>差异内容：export type RouteInfo = connection.RouteInfo;|api/@ohos.net.vpn.d.ts|
|新增API|NA|类名：vpn；<br>API声明：export type AbilityContext = _AbilityContext;<br>差异内容：export type AbilityContext = _AbilityContext;|api/@ohos.net.vpn.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace vpnExtension<br>差异内容：declare namespace vpnExtension|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：vpnExtension；<br>API声明：export type LinkAddress = connection.LinkAddress;<br>差异内容：export type LinkAddress = connection.LinkAddress;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：vpnExtension；<br>API声明：export type RouteInfo = connection.RouteInfo;<br>差异内容：export type RouteInfo = connection.RouteInfo;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：vpnExtension；<br>API声明：export type VpnExtensionContext = _VpnExtensionContext;<br>差异内容：export type VpnExtensionContext = _VpnExtensionContext;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：vpnExtension；<br>API声明：function startVpnExtensionAbility(want: Want): Promise\<void>;<br>差异内容：function startVpnExtensionAbility(want: Want): Promise\<void>;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：vpnExtension；<br>API声明：function stopVpnExtensionAbility(want: Want): Promise\<void>;<br>差异内容：function stopVpnExtensionAbility(want: Want): Promise\<void>;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：vpnExtension；<br>API声明：function createVpnConnection(context: VpnExtensionContext): VpnConnection;<br>差异内容：function createVpnConnection(context: VpnExtensionContext): VpnConnection;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：vpnExtension；<br>API声明：export interface VpnConnection<br>差异内容：export interface VpnConnection|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：VpnConnection；<br>API声明：create(config: VpnConfig): Promise\<number>;<br>差异内容：create(config: VpnConfig): Promise\<number>;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：VpnConnection；<br>API声明：protect(socketFd: number): Promise\<void>;<br>差异内容：protect(socketFd: number): Promise\<void>;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：VpnConnection；<br>API声明：destroy(): Promise\<void>;<br>差异内容：destroy(): Promise\<void>;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：vpnExtension；<br>API声明：export interface VpnConfig<br>差异内容：export interface VpnConfig|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：VpnConfig；<br>API声明：addresses: Array\<LinkAddress>;<br>差异内容：addresses: Array\<LinkAddress>;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：VpnConfig；<br>API声明：routes?: Array\<RouteInfo>;<br>差异内容：routes?: Array\<RouteInfo>;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：VpnConfig；<br>API声明：dnsAddresses?: Array\<string>;<br>差异内容：dnsAddresses?: Array\<string>;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：VpnConfig；<br>API声明：searchDomains?: Array\<string>;<br>差异内容：searchDomains?: Array\<string>;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：VpnConfig；<br>API声明：mtu?: number;<br>差异内容：mtu?: number;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：VpnConfig；<br>API声明：isIPv4Accepted?: boolean;<br>差异内容：isIPv4Accepted?: boolean;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：VpnConfig；<br>API声明：isIPv6Accepted?: boolean;<br>差异内容：isIPv6Accepted?: boolean;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：VpnConfig；<br>API声明：isInternal?: boolean;<br>差异内容：isInternal?: boolean;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：VpnConfig；<br>API声明：isBlocking?: boolean;<br>差异内容：isBlocking?: boolean;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：VpnConfig；<br>API声明：trustedApplications?: Array\<string>;<br>差异内容：trustedApplications?: Array\<string>;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：VpnConfig；<br>API声明：blockedApplications?: Array\<string>;<br>差异内容：blockedApplications?: Array\<string>;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace webSocket<br>差异内容：declare namespace webSocket|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：webSocket；<br>API声明：function createWebSocket(): WebSocket;<br>差异内容：function createWebSocket(): WebSocket;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：webSocket；<br>API声明：export interface WebSocketRequestOptions<br>差异内容：export interface WebSocketRequestOptions|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketRequestOptions；<br>API声明：header?: Object;<br>差异内容：header?: Object;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketRequestOptions；<br>API声明：caPath?: string;<br>差异内容：caPath?: string;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketRequestOptions；<br>API声明：clientCert?: ClientCert;<br>差异内容：clientCert?: ClientCert;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：webSocket；<br>API声明：export interface ClientCert<br>差异内容：export interface ClientCert|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：ClientCert；<br>API声明：certPath: string;<br>差异内容：certPath: string;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：ClientCert；<br>API声明：keyPath: string;<br>差异内容：keyPath: string;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：ClientCert；<br>API声明：keyPassword?: string;<br>差异内容：keyPassword?: string;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：webSocket；<br>API声明：export interface WebSocketCloseOptions<br>差异内容：export interface WebSocketCloseOptions|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketCloseOptions；<br>API声明：code?: number;<br>差异内容：code?: number;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketCloseOptions；<br>API声明：reason?: string;<br>差异内容：reason?: string;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：webSocket；<br>API声明：export interface CloseResult<br>差异内容：export interface CloseResult|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：CloseResult；<br>API声明：code: number;<br>差异内容：code: number;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：CloseResult；<br>API声明：reason: string;<br>差异内容：reason: string;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：webSocket；<br>API声明：export interface WebSocket<br>差异内容：export interface WebSocket|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：connect(url: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：connect(url: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：connect(url: string, options: WebSocketRequestOptions, callback: AsyncCallback\<boolean>): void;<br>差异内容：connect(url: string, options: WebSocketRequestOptions, callback: AsyncCallback\<boolean>): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：connect(url: string, options?: WebSocketRequestOptions): Promise\<boolean>;<br>差异内容：connect(url: string, options?: WebSocketRequestOptions): Promise\<boolean>;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：send(data: string \| ArrayBuffer, callback: AsyncCallback\<boolean>): void;<br>差异内容：send(data: string \| ArrayBuffer, callback: AsyncCallback\<boolean>): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：send(data: string \| ArrayBuffer): Promise\<boolean>;<br>差异内容：send(data: string \| ArrayBuffer): Promise\<boolean>;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：close(callback: AsyncCallback\<boolean>): void;<br>差异内容：close(callback: AsyncCallback\<boolean>): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：close(options: WebSocketCloseOptions, callback: AsyncCallback\<boolean>): void;<br>差异内容：close(options: WebSocketCloseOptions, callback: AsyncCallback\<boolean>): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：close(options?: WebSocketCloseOptions): Promise\<boolean>;<br>差异内容：close(options?: WebSocketCloseOptions): Promise\<boolean>;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：on(type: 'open', callback: AsyncCallback\<Object>): void;<br>差异内容：on(type: 'open', callback: AsyncCallback\<Object>): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：off(type: 'open', callback?: AsyncCallback\<Object>): void;<br>差异内容：off(type: 'open', callback?: AsyncCallback\<Object>): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：on(type: 'message', callback: AsyncCallback\<string \| ArrayBuffer>): void;<br>差异内容：on(type: 'message', callback: AsyncCallback\<string \| ArrayBuffer>): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：off(type: 'message', callback?: AsyncCallback\<string \| ArrayBuffer>): void;<br>差异内容：off(type: 'message', callback?: AsyncCallback\<string \| ArrayBuffer>): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：on(type: 'close', callback: AsyncCallback\<CloseResult>): void;<br>差异内容：on(type: 'close', callback: AsyncCallback\<CloseResult>): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：off(type: 'close', callback?: AsyncCallback\<CloseResult>): void;<br>差异内容：off(type: 'close', callback?: AsyncCallback\<CloseResult>): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：on(type: 'dataEnd', callback: Callback\<void>): void;<br>差异内容：on(type: 'dataEnd', callback: Callback\<void>): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：off(type: 'dataEnd', callback?: Callback\<void>): void;<br>差异内容：off(type: 'dataEnd', callback?: Callback\<void>): void;|api/@ohos.net.webSocket.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.VpnExtensionAbility.d.ts<br>差异内容：NetworkKit|api/@ohos.app.ability.VpnExtensionAbility.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.net.connection.d.ts<br>差异内容：NetworkKit|api/@ohos.net.connection.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.net.ethernet.d.ts<br>差异内容：NetworkKit|api/@ohos.net.ethernet.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.net.http.d.ts<br>差异内容：NetworkKit|api/@ohos.net.http.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.net.mdns.d.ts<br>差异内容：NetworkKit|api/@ohos.net.mdns.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.net.networkSecurity.d.ts<br>差异内容：NetworkKit|api/@ohos.net.networkSecurity.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.net.policy.d.ts<br>差异内容：NetworkKit|api/@ohos.net.policy.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.net.sharing.d.ts<br>差异内容：NetworkKit|api/@ohos.net.sharing.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.net.socket.d.ts<br>差异内容：NetworkKit|api/@ohos.net.socket.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.net.statistics.d.ts<br>差异内容：NetworkKit|api/@ohos.net.statistics.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.net.vpn.d.ts<br>差异内容：NetworkKit|api/@ohos.net.vpn.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.net.vpnExtension.d.ts<br>差异内容：NetworkKit|api/@ohos.net.vpnExtension.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.net.webSocket.d.ts<br>差异内容：NetworkKit|api/@ohos.net.webSocket.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.NetworkKit.d.ts<br>差异内容：NetworkKit|kits/@kit.NetworkKit.d.ts|
