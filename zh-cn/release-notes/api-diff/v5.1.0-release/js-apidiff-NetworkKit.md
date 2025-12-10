| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API跨平台权限变更|类名：HttpRequest；<br>API声明：requestInStream(url: string, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|类名：HttpRequest；<br>API声明：requestInStream(url: string, callback: AsyncCallback\<number>): void;<br>差异内容：NA|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|类名：HttpRequest；<br>API声明：requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number>): void;<br>差异内容：NA|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：requestInStream(url: string, options?: HttpRequestOptions): Promise\<number>;<br>差异内容：crossplatform|类名：HttpRequest；<br>API声明：requestInStream(url: string, options?: HttpRequestOptions): Promise\<number>;<br>差异内容：NA|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：on(type: "dataReceive", callback: Callback\<ArrayBuffer>): void;<br>差异内容：crossplatform|类名：HttpRequest；<br>API声明：on(type: "dataReceive", callback: Callback\<ArrayBuffer>): void;<br>差异内容：NA|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：off(type: "dataReceive", callback?: Callback\<ArrayBuffer>): void;<br>差异内容：crossplatform|类名：HttpRequest；<br>API声明：off(type: "dataReceive", callback?: Callback\<ArrayBuffer>): void;<br>差异内容：NA|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：on(type: "dataEnd", callback: Callback\<void>): void;<br>差异内容：crossplatform|类名：HttpRequest；<br>API声明：on(type: "dataEnd", callback: Callback\<void>): void;<br>差异内容：NA|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：off(type: "dataEnd", callback?: Callback\<void>): void;<br>差异内容：crossplatform|类名：HttpRequest；<br>API声明：off(type: "dataEnd", callback?: Callback\<void>): void;<br>差异内容：NA|api/@ohos.net.http.d.ts|
|删除错误码|类名：HttpRequest；<br>API声明：request(url: string, callback: AsyncCallback\<HttpResponse>): void;<br>差异内容：2300997,2300998|类名：HttpRequest；<br>API声明：request(url: string, callback: AsyncCallback\<HttpResponse>): void;<br>差异内容：NA|api/@ohos.net.http.d.ts|
|删除错误码|类名：HttpRequest；<br>API声明：request(url: string, options: HttpRequestOptions, callback: AsyncCallback\<HttpResponse>): void;<br>差异内容：2300997,2300998|类名：HttpRequest；<br>API声明：request(url: string, options: HttpRequestOptions, callback: AsyncCallback\<HttpResponse>): void;<br>差异内容：NA|api/@ohos.net.http.d.ts|
|删除错误码|类名：HttpRequest；<br>API声明：request(url: string, options?: HttpRequestOptions): Promise\<HttpResponse>;<br>差异内容：2300997,2300998|类名：HttpRequest；<br>API声明：request(url: string, options?: HttpRequestOptions): Promise\<HttpResponse>;<br>差异内容：NA|api/@ohos.net.http.d.ts|
|删除错误码|类名：HttpRequest；<br>API声明：requestInStream(url: string, callback: AsyncCallback\<number>): void;<br>差异内容：2300997|类名：HttpRequest；<br>API声明：requestInStream(url: string, callback: AsyncCallback\<number>): void;<br>差异内容：NA|api/@ohos.net.http.d.ts|
|删除错误码|类名：HttpRequest；<br>API声明：requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number>): void;<br>差异内容：2300997|类名：HttpRequest；<br>API声明：requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number>): void;<br>差异内容：NA|api/@ohos.net.http.d.ts|
|删除错误码|类名：HttpRequest；<br>API声明：requestInStream(url: string, options?: HttpRequestOptions): Promise\<number>;<br>差异内容：2300997|类名：HttpRequest；<br>API声明：requestInStream(url: string, options?: HttpRequestOptions): Promise\<number>;<br>差异内容：NA|api/@ohos.net.http.d.ts|
|删除错误码|类名：UDPSocket；<br>API声明：send(options: UDPSendOptions, callback: AsyncCallback\<void>): void;<br>差异内容：2301206,2301207,2301208,2301209,2301210,2301211,2301212,2301213|类名：UDPSocket；<br>API声明：send(options: UDPSendOptions, callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.net.socket.d.ts|
|删除错误码|类名：UDPSocket；<br>API声明：send(options: UDPSendOptions): Promise\<void>;<br>差异内容：2301206,2301207,2301208,2301209,2301210,2301211,2301212,2301213|类名：UDPSocket；<br>API声明：send(options: UDPSendOptions): Promise\<void>;<br>差异内容：NA|api/@ohos.net.socket.d.ts|
|删除错误码|类名：TCPSocket；<br>API声明：connect(options: TCPConnectOptions, callback: AsyncCallback\<void>): void;<br>差异内容：2301206,2301207,2301208,2301209,2301210,2301211,2301212,2301213|类名：TCPSocket；<br>API声明：connect(options: TCPConnectOptions, callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.net.socket.d.ts|
|删除错误码|类名：TCPSocket；<br>API声明：connect(options: TCPConnectOptions): Promise\<void>;<br>差异内容：2301206,2301207,2301208,2301209,2301210,2301211,2301212,2301213|类名：TCPSocket；<br>API声明：connect(options: TCPConnectOptions): Promise\<void>;<br>差异内容：NA|api/@ohos.net.socket.d.ts|
|删除错误码|类名：TLSSocket；<br>API声明：connect(options: TLSConnectOptions, callback: AsyncCallback\<void>): void;<br>差异内容：2301206,2301207,2301208,2301209,2301210,2301211,2301212,2301213|类名：TLSSocket；<br>API声明：connect(options: TLSConnectOptions, callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.net.socket.d.ts|
|删除错误码|类名：TLSSocket；<br>API声明：connect(options: TLSConnectOptions): Promise\<void>;<br>差异内容：2301206,2301207,2301208,2301209,2301210,2301211,2301212,2301213|类名：TLSSocket；<br>API声明：connect(options: TLSConnectOptions): Promise\<void>;<br>差异内容：NA|api/@ohos.net.socket.d.ts|
|删除错误码|类名：WebSocket；<br>API声明：connect(url: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：2302998|类名：WebSocket；<br>API声明：connect(url: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|api/@ohos.net.webSocket.d.ts|
|删除错误码|类名：WebSocket；<br>API声明：connect(url: string, options: WebSocketRequestOptions, callback: AsyncCallback\<boolean>): void;<br>差异内容：2302998|类名：WebSocket；<br>API声明：connect(url: string, options: WebSocketRequestOptions, callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|api/@ohos.net.webSocket.d.ts|
|删除错误码|类名：WebSocket；<br>API声明：connect(url: string, options?: WebSocketRequestOptions): Promise\<boolean>;<br>差异内容：2302998|类名：WebSocket；<br>API声明：connect(url: string, options?: WebSocketRequestOptions): Promise\<boolean>;<br>差异内容：NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：global；<br>API声明：declare namespace eap<br>差异内容：declare namespace eap|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：eap；<br>API声明：function regCustomEapHandler(netType: number, eapCode: number, eapType: number, callback: Callback\<EapData>): void;<br>差异内容：function regCustomEapHandler(netType: number, eapCode: number, eapType: number, callback: Callback\<EapData>): void;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：eap；<br>API声明：function unregCustomEapHandler(netType: number, eapCode: number, eapType: number, callback: Callback\<EapData>): void;<br>差异内容：function unregCustomEapHandler(netType: number, eapCode: number, eapType: number, callback: Callback\<EapData>): void;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：eap；<br>API声明：function replyCustomEapData(result: CustomResult, data: EapData): void;<br>差异内容：function replyCustomEapData(result: CustomResult, data: EapData): void;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：eap；<br>API声明：function startEthEap(netId: number, profile: EthEapProfile): void;<br>差异内容：function startEthEap(netId: number, profile: EthEapProfile): void;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：eap；<br>API声明：function logOffEthEap(netId: number): void;<br>差异内容：function logOffEthEap(netId: number): void;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：eap；<br>API声明：interface EapData<br>差异内容：interface EapData|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EapData；<br>API声明：msgId: number;<br>差异内容：msgId: number;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EapData；<br>API声明：eapBuffer: Uint8Array;<br>差异内容：eapBuffer: Uint8Array;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EapData；<br>API声明：bufferLen: number;<br>差异内容：bufferLen: number;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：eap；<br>API声明：enum CustomResult<br>差异内容：enum CustomResult|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：CustomResult；<br>API声明：RESULT_FAIL<br>差异内容：RESULT_FAIL|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：CustomResult；<br>API声明：RESULT_NEXT<br>差异内容：RESULT_NEXT|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：CustomResult；<br>API声明：RESULT_FINISH<br>差异内容：RESULT_FINISH|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：eap；<br>API声明：enum EapMethod<br>差异内容：enum EapMethod|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EapMethod；<br>API声明：EAP_NONE<br>差异内容：EAP_NONE|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EapMethod；<br>API声明：EAP_PEAP<br>差异内容：EAP_PEAP|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EapMethod；<br>API声明：EAP_TLS<br>差异内容：EAP_TLS|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EapMethod；<br>API声明：EAP_TTLS<br>差异内容：EAP_TTLS|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EapMethod；<br>API声明：EAP_PWD<br>差异内容：EAP_PWD|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EapMethod；<br>API声明：EAP_SIM<br>差异内容：EAP_SIM|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EapMethod；<br>API声明：EAP_AKA<br>差异内容：EAP_AKA|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EapMethod；<br>API声明：EAP_AKA_PRIME<br>差异内容：EAP_AKA_PRIME|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EapMethod；<br>API声明：EAP_UNAUTH_TLS<br>差异内容：EAP_UNAUTH_TLS|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：eap；<br>API声明：enum Phase2Method<br>差异内容：enum Phase2Method|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：Phase2Method；<br>API声明：PHASE2_NONE<br>差异内容：PHASE2_NONE|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：Phase2Method；<br>API声明：PHASE2_PAP<br>差异内容：PHASE2_PAP|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：Phase2Method；<br>API声明：PHASE2_MSCHAP<br>差异内容：PHASE2_MSCHAP|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：Phase2Method；<br>API声明：PHASE2_MSCHAPV2<br>差异内容：PHASE2_MSCHAPV2|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：Phase2Method；<br>API声明：PHASE2_GTC<br>差异内容：PHASE2_GTC|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：Phase2Method；<br>API声明：PHASE2_SIM<br>差异内容：PHASE2_SIM|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：Phase2Method；<br>API声明：PHASE2_AKA<br>差异内容：PHASE2_AKA|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：Phase2Method；<br>API声明：PHASE2_AKA_PRIME<br>差异内容：PHASE2_AKA_PRIME|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：eap；<br>API声明：interface EthEapProfile<br>差异内容：interface EthEapProfile|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EthEapProfile；<br>API声明：eapMethod: EapMethod;<br>差异内容：eapMethod: EapMethod;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EthEapProfile；<br>API声明：phase2Method: Phase2Method;<br>差异内容：phase2Method: Phase2Method;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EthEapProfile；<br>API声明：identity: string;<br>差异内容：identity: string;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EthEapProfile；<br>API声明：anonymousIdentity: string;<br>差异内容：anonymousIdentity: string;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EthEapProfile；<br>API声明：password: string;<br>差异内容：password: string;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EthEapProfile；<br>API声明：caCertAliases: string;<br>差异内容：caCertAliases: string;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EthEapProfile；<br>API声明：caPath: string;<br>差异内容：caPath: string;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EthEapProfile；<br>API声明：clientCertAliases: string;<br>差异内容：clientCertAliases: string;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EthEapProfile；<br>API声明：certEntry: Uint8Array;<br>差异内容：certEntry: Uint8Array;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EthEapProfile；<br>API声明：certPassword: string;<br>差异内容：certPassword: string;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EthEapProfile；<br>API声明：altSubjectMatch: string;<br>差异内容：altSubjectMatch: string;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EthEapProfile；<br>API声明：domainSuffixMatch: string;<br>差异内容：domainSuffixMatch: string;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EthEapProfile；<br>API声明：realm: string;<br>差异内容：realm: string;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EthEapProfile；<br>API声明：plmn: string;<br>差异内容：plmn: string;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：EthEapProfile；<br>API声明：eapSubId: number;<br>差异内容：eapSubId: number;|NA|api/@ohos.net.eap.d.ts|
|删除API|类名：connection；<br>API声明：function setNetExtAttribute(netHandle: NetHandle, netExtAttribute: string): Promise\<void>;<br>差异内容：function setNetExtAttribute(netHandle: NetHandle, netExtAttribute: string): Promise\<void>;|NA|api/@ohos.net.connection.d.ts|
|删除API|类名：connection；<br>API声明：function setNetExtAttributeSync(netHandle: NetHandle, netExtAttribute: string): void;<br>差异内容：function setNetExtAttributeSync(netHandle: NetHandle, netExtAttribute: string): void;|NA|api/@ohos.net.connection.d.ts|
|删除API|类名：connection；<br>API声明：function getNetExtAttribute(netHandle: NetHandle): Promise\<string>;<br>差异内容：function getNetExtAttribute(netHandle: NetHandle): Promise\<string>;|NA|api/@ohos.net.connection.d.ts|
|删除API|类名：connection；<br>API声明：function getNetExtAttributeSync(netHandle: NetHandle): string;<br>差异内容：function getNetExtAttributeSync(netHandle: NetHandle): string;|NA|api/@ohos.net.connection.d.ts|
|删除API|类名：connection；<br>API声明：function setPacFileUrl(pacFileUrl: string): void;<br>差异内容：function setPacFileUrl(pacFileUrl: string): void;|NA|api/@ohos.net.connection.d.ts|
|删除API|类名：connection；<br>API声明：function getPacFileUrl(): string;<br>差异内容：function getPacFileUrl(): string;|NA|api/@ohos.net.connection.d.ts|
|删除API|类名：connection；<br>API声明：function findProxyForUrl(url: string): string;<br>差异内容：function findProxyForUrl(url: string): string;|NA|api/@ohos.net.connection.d.ts|
|删除API|类名：RouteInfo；<br>API声明：isExcludedRoute?: boolean;<br>差异内容：isExcludedRoute?: boolean;|NA|api/@ohos.net.connection.d.ts|
|删除API|类名：HttpRequestOptions；<br>API声明：caData?: string;<br>差异内容：caData?: string;|NA|api/@ohos.net.http.d.ts|
|删除API|类名：HttpRequestOptions；<br>API声明：sslType?: SslType;<br>差异内容：sslType?: SslType;|NA|api/@ohos.net.http.d.ts|
|删除API|类名：HttpRequestOptions；<br>API声明：clientEncCert?: ClientCert;<br>差异内容：clientEncCert?: ClientCert;|NA|api/@ohos.net.http.d.ts|
|删除API|类名：HttpRequestOptions；<br>API声明：remoteValidation?: RemoteValidation;<br>差异内容：remoteValidation?: RemoteValidation;|NA|api/@ohos.net.http.d.ts|
|删除API|类名：HttpRequestOptions；<br>API声明：tlsOptions?: TlsOptions;<br>差异内容：tlsOptions?: TlsOptions;|NA|api/@ohos.net.http.d.ts|
|删除API|类名：HttpRequestOptions；<br>API声明：serverAuthentication?: ServerAuthentication;<br>差异内容：serverAuthentication?: ServerAuthentication;|NA|api/@ohos.net.http.d.ts|
|删除API|类名：http；<br>API声明：export interface ServerAuthentication<br>差异内容：export interface ServerAuthentication|NA|api/@ohos.net.http.d.ts|
|删除API|类名：ServerAuthentication；<br>API声明：credential: Credential;<br>差异内容：credential: Credential;|NA|api/@ohos.net.http.d.ts|
|删除API|类名：ServerAuthentication；<br>API声明：authenticationType?: AuthenticationType;<br>差异内容：authenticationType?: AuthenticationType;|NA|api/@ohos.net.http.d.ts|
|删除API|类名：http；<br>API声明：export type TlsOptions = 'system' \| TlsConfig;<br>差异内容：export type TlsOptions = 'system' \| TlsConfig;|NA|api/@ohos.net.http.d.ts|
|删除API|类名：http；<br>API声明：export type RemoteValidation = 'system' \| 'skip';<br>差异内容：export type RemoteValidation = 'system' \| 'skip';|NA|api/@ohos.net.http.d.ts|
|删除API|类名：http；<br>API声明：export type AuthenticationType = 'basic' \| 'ntlm' \| 'digest';<br>差异内容：export type AuthenticationType = 'basic' \| 'ntlm' \| 'digest';|NA|api/@ohos.net.http.d.ts|
|删除API|类名：http；<br>API声明：export type SslType = 'TLS' \| 'TLCP';<br>差异内容：export type SslType = 'TLS' \| 'TLCP';|NA|api/@ohos.net.http.d.ts|
|删除API|类名：http；<br>API声明：export interface Credential<br>差异内容：export interface Credential|NA|api/@ohos.net.http.d.ts|
|删除API|类名：Credential；<br>API声明：username: string;<br>差异内容：username: string;|NA|api/@ohos.net.http.d.ts|
|删除API|类名：Credential；<br>API声明：password: string;<br>差异内容：password: string;|NA|api/@ohos.net.http.d.ts|
|删除API|类名：http；<br>API声明：export interface TlsConfig<br>差异内容：export interface TlsConfig|NA|api/@ohos.net.http.d.ts|
|删除API|类名：TlsConfig；<br>API声明：tlsVersionMin: TlsVersion;<br>差异内容：tlsVersionMin: TlsVersion;|NA|api/@ohos.net.http.d.ts|
|删除API|类名：TlsConfig；<br>API声明：tlsVersionMax: TlsVersion;<br>差异内容：tlsVersionMax: TlsVersion;|NA|api/@ohos.net.http.d.ts|
|删除API|类名：TlsConfig；<br>API声明：cipherSuites?: CipherSuite[];<br>差异内容：cipherSuites?: CipherSuite[];|NA|api/@ohos.net.http.d.ts|
|删除API|类名：http；<br>API声明：export type TlsV13SpecificCipherSuite = 'TLS_AES_128_GCM_SHA256' \| 'TLS_AES_256_GCM_SHA384' \| 'TLS_CHACHA20_POLY1305_SHA256';<br>差异内容：export type TlsV13SpecificCipherSuite = 'TLS_AES_128_GCM_SHA256' \| 'TLS_AES_256_GCM_SHA384' \| 'TLS_CHACHA20_POLY1305_SHA256';|NA|api/@ohos.net.http.d.ts|
|删除API|类名：http；<br>API声明：export type TlsV12SpecificCipherSuite = 'TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256' \| 'TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256' \| 'TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384' \| 'TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384' \| 'TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256' \| 'TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256' \| 'TLS_RSA_WITH_AES_128_GCM_SHA256' \| 'TLS_RSA_WITH_AES_256_GCM_SHA384';<br>差异内容：export type TlsV12SpecificCipherSuite = 'TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256' \| 'TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256' \| 'TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384' \| 'TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384' \| 'TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256' \| 'TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256' \| 'TLS_RSA_WITH_AES_128_GCM_SHA256' \| 'TLS_RSA_WITH_AES_256_GCM_SHA384';|NA|api/@ohos.net.http.d.ts|
|删除API|类名：http；<br>API声明：export type TlsV10SpecificCipherSuite = 'TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA' \| 'TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA' \| 'TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA' \| 'TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA' \| 'TLS_RSA_WITH_AES_128_CBC_SHA' \| 'TLS_RSA_WITH_AES_256_CBC_SHA' \| 'TLS_RSA_WITH_3DES_EDE_CBC_SHA';<br>差异内容：export type TlsV10SpecificCipherSuite = 'TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA' \| 'TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA' \| 'TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA' \| 'TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA' \| 'TLS_RSA_WITH_AES_128_CBC_SHA' \| 'TLS_RSA_WITH_AES_256_CBC_SHA' \| 'TLS_RSA_WITH_3DES_EDE_CBC_SHA';|NA|api/@ohos.net.http.d.ts|
|删除API|类名：http；<br>API声明：export type CipherSuite = TlsV13CipherSuite;<br>差异内容：export type CipherSuite = TlsV13CipherSuite;|NA|api/@ohos.net.http.d.ts|
|删除API|类名：http；<br>API声明：export type TlsV13CipherSuite = TlsV12CipherSuite \| TlsV13SpecificCipherSuite;<br>差异内容：export type TlsV13CipherSuite = TlsV12CipherSuite \| TlsV13SpecificCipherSuite;|NA|api/@ohos.net.http.d.ts|
|删除API|类名：http；<br>API声明：export type TlsV12CipherSuite = TlsV11CipherSuite \| TlsV12SpecificCipherSuite;<br>差异内容：export type TlsV12CipherSuite = TlsV11CipherSuite \| TlsV12SpecificCipherSuite;|NA|api/@ohos.net.http.d.ts|
|删除API|类名：http；<br>API声明：export type TlsV11CipherSuite = TlsV10CipherSuite;<br>差异内容：export type TlsV11CipherSuite = TlsV10CipherSuite;|NA|api/@ohos.net.http.d.ts|
|删除API|类名：http；<br>API声明：export type TlsV10CipherSuite = TlsV10SpecificCipherSuite;<br>差异内容：export type TlsV10CipherSuite = TlsV10SpecificCipherSuite;|NA|api/@ohos.net.http.d.ts|
|删除API|类名：http；<br>API声明：export enum TlsVersion<br>差异内容：export enum TlsVersion|NA|api/@ohos.net.http.d.ts|
|删除API|类名：TlsVersion；<br>API声明：TLS_V_1_0 = 4<br>差异内容：TLS_V_1_0 = 4|NA|api/@ohos.net.http.d.ts|
|删除API|类名：TlsVersion；<br>API声明：TLS_V_1_1 = 5<br>差异内容：TLS_V_1_1 = 5|NA|api/@ohos.net.http.d.ts|
|删除API|类名：TlsVersion；<br>API声明：TLS_V_1_2 = 6<br>差异内容：TLS_V_1_2 = 6|NA|api/@ohos.net.http.d.ts|
|删除API|类名：TlsVersion；<br>API声明：TLS_V_1_3 = 7<br>差异内容：TLS_V_1_3 = 7|NA|api/@ohos.net.http.d.ts|
|删除API|类名：networkSecurity；<br>API声明：export function isCleartextPermitted(): boolean;<br>差异内容：export function isCleartextPermitted(): boolean;|NA|api/@ohos.net.networkSecurity.d.ts|
|删除API|类名：networkSecurity；<br>API声明：export function isCleartextPermittedByHostName(hostName: string): boolean;<br>差异内容：export function isCleartextPermittedByHostName(hostName: string): boolean;|NA|api/@ohos.net.networkSecurity.d.ts|
|删除API|类名：UDPSendOptions；<br>API声明：proxy?: ProxyOptions;<br>差异内容：proxy?: ProxyOptions;|NA|api/@ohos.net.socket.d.ts|
|删除API|类名：socket；<br>API声明：export enum ProxyTypes<br>差异内容：export enum ProxyTypes|NA|api/@ohos.net.socket.d.ts|
|删除API|类名：ProxyTypes；<br>API声明：NONE = 0<br>差异内容：NONE = 0|NA|api/@ohos.net.socket.d.ts|
|删除API|类名：ProxyTypes；<br>API声明：SOCKS5 = 1<br>差异内容：SOCKS5 = 1|NA|api/@ohos.net.socket.d.ts|
|删除API|类名：socket；<br>API声明：export interface ProxyOptions<br>差异内容：export interface ProxyOptions|NA|api/@ohos.net.socket.d.ts|
|删除API|类名：ProxyOptions；<br>API声明：type: ProxyTypes;<br>差异内容：type: ProxyTypes;|NA|api/@ohos.net.socket.d.ts|
|删除API|类名：ProxyOptions；<br>API声明：address: NetAddress;<br>差异内容：address: NetAddress;|NA|api/@ohos.net.socket.d.ts|
|删除API|类名：ProxyOptions；<br>API声明：username?: string;<br>差异内容：username?: string;|NA|api/@ohos.net.socket.d.ts|
|删除API|类名：ProxyOptions；<br>API声明：password?: string;<br>差异内容：password?: string;|NA|api/@ohos.net.socket.d.ts|
|删除API|类名：LocalSocketServer；<br>API声明：close(): Promise\<void>;<br>差异内容：close(): Promise\<void>;|NA|api/@ohos.net.socket.d.ts|
|删除API|类名：TCPConnectOptions；<br>API声明：proxy?: ProxyOptions;<br>差异内容：proxy?: ProxyOptions;|NA|api/@ohos.net.socket.d.ts|
|删除API|类名：TLSSocket；<br>API声明：getSocketFd(): Promise\<number>;<br>差异内容：getSocketFd(): Promise\<number>;|NA|api/@ohos.net.socket.d.ts|
|删除API|类名：TLSConnectOptions；<br>API声明：proxy?: ProxyOptions;<br>差异内容：proxy?: ProxyOptions;|NA|api/@ohos.net.socket.d.ts|
|删除API|类名：TCPSocketServer；<br>API声明：close(): Promise\<void>;<br>差异内容：close(): Promise\<void>;|NA|api/@ohos.net.socket.d.ts|
|删除API|类名：TLSSocketServer；<br>API声明：close(): Promise\<void>;<br>差异内容：close(): Promise\<void>;|NA|api/@ohos.net.socket.d.ts|
|删除API|类名：VpnConnection；<br>API声明：generateVpnId(): Promise\<string>;<br>差异内容：generateVpnId(): Promise\<string>;|NA|api/@ohos.net.vpnExtension.d.ts|
|删除API|类名：VpnConnection；<br>API声明：destroy(vpnId: string): Promise\<void>;<br>差异内容：destroy(vpnId: string): Promise\<void>;|NA|api/@ohos.net.vpnExtension.d.ts|
|删除API|类名：VpnConfig；<br>API声明：vpnId?: string;<br>差异内容：vpnId?: string;|NA|api/@ohos.net.vpnExtension.d.ts|
|删除API|类名：WebSocketRequestOptions；<br>API声明：skipServerCertVerification?: boolean;<br>差异内容：skipServerCertVerification?: boolean;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：webSocket；<br>API声明：function createWebSocketServer(): WebSocketServer;<br>差异内容：function createWebSocketServer(): WebSocketServer;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：webSocket；<br>API声明：export interface WebSocketServerConfig<br>差异内容：export interface WebSocketServerConfig|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServerConfig；<br>API声明：serverIP?: string;<br>差异内容：serverIP?: string;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServerConfig；<br>API声明：serverPort: number;<br>差异内容：serverPort: number;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServerConfig；<br>API声明：serverCert?: ServerCert;<br>差异内容：serverCert?: ServerCert;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServerConfig；<br>API声明：maxConcurrentClientsNumber: number;<br>差异内容：maxConcurrentClientsNumber: number;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServerConfig；<br>API声明：protocol?: string;<br>差异内容：protocol?: string;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServerConfig；<br>API声明：maxConnectionsForOneClient: number;<br>差异内容：maxConnectionsForOneClient: number;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：webSocket；<br>API声明：export interface ServerCert<br>差异内容：export interface ServerCert|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：ServerCert；<br>API声明：certPath: string;<br>差异内容：certPath: string;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：ServerCert；<br>API声明：keyPath: string;<br>差异内容：keyPath: string;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：webSocket；<br>API声明：export interface WebSocketConnection<br>差异内容：export interface WebSocketConnection|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketConnection；<br>API声明：clientIP: string;<br>差异内容：clientIP: string;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketConnection；<br>API声明：clientPort: number;<br>差异内容：clientPort: number;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：webSocket；<br>API声明：export interface WebSocketMessage<br>差异内容：export interface WebSocketMessage|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketMessage；<br>API声明：data: string \| ArrayBuffer;<br>差异内容：data: string \| ArrayBuffer;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketMessage；<br>API声明：clientConnection: WebSocketConnection;<br>差异内容：clientConnection: WebSocketConnection;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：webSocket；<br>API声明：export type ClientConnectionCloseCallback = (clientConnection: WebSocketConnection, closeReason: CloseResult) => void;<br>差异内容：export type ClientConnectionCloseCallback = (clientConnection: WebSocketConnection, closeReason: CloseResult) => void;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：webSocket；<br>API声明：export interface WebSocketServer<br>差异内容：export interface WebSocketServer|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServer；<br>API声明：start(config: WebSocketServerConfig): Promise\<boolean>;<br>差异内容：start(config: WebSocketServerConfig): Promise\<boolean>;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServer；<br>API声明：listAllConnections(): WebSocketConnection[];<br>差异内容：listAllConnections(): WebSocketConnection[];|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServer；<br>API声明：close(connection: WebSocketConnection, options?: webSocket.WebSocketCloseOptions): Promise\<boolean>;<br>差异内容：close(connection: WebSocketConnection, options?: webSocket.WebSocketCloseOptions): Promise\<boolean>;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServer；<br>API声明：send(data: string \| ArrayBuffer, connection: WebSocketConnection): Promise\<boolean>;<br>差异内容：send(data: string \| ArrayBuffer, connection: WebSocketConnection): Promise\<boolean>;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServer；<br>API声明：stop(): Promise\<boolean>;<br>差异内容：stop(): Promise\<boolean>;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServer；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServer；<br>API声明：on(type: 'connect', callback: Callback\<WebSocketConnection>): void;<br>差异内容：on(type: 'connect', callback: Callback\<WebSocketConnection>): void;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServer；<br>API声明：on(type: 'messageReceive', callback: Callback\<WebSocketMessage>): void;<br>差异内容：on(type: 'messageReceive', callback: Callback\<WebSocketMessage>): void;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServer；<br>API声明：on(type: 'close', callback: ClientConnectionCloseCallback): void;<br>差异内容：on(type: 'close', callback: ClientConnectionCloseCallback): void;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServer；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServer；<br>API声明：off(type: 'connect', callback?: Callback\<WebSocketConnection>): void;<br>差异内容：off(type: 'connect', callback?: Callback\<WebSocketConnection>): void;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServer；<br>API声明：off(type: 'close', callback?: ClientConnectionCloseCallback): void;<br>差异内容：off(type: 'close', callback?: ClientConnectionCloseCallback): void;|NA|api/@ohos.net.webSocket.d.ts|
|删除API|类名：WebSocketServer；<br>API声明：off(type: 'messageReceive', callback?: Callback\<WebSocketMessage>): void;<br>差异内容：off(type: 'messageReceive', callback?: Callback\<WebSocketMessage>): void;|NA|api/@ohos.net.webSocket.d.ts|
|删除kit|类名：global；<br>API声明：api\@ohos.net.eap.d.ts<br>差异内容：NetworkKit|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.net.eap.d.ts|
|API从支持元服务到不支持元服务|类名：NetBearType；<br>API声明：BEARER_BLUETOOTH = 2<br>差异内容：atomicservice|类名：NetBearType；<br>API声明：BEARER_BLUETOOTH = 2<br>差异内容：NA|api/@ohos.net.connection.d.ts|
