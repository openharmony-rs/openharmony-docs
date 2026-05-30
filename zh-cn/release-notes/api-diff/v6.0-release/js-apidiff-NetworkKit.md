| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API跨平台权限变更|类名：HttpRequest；<br>API声明：requestInStream(url: string, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：requestInStream(url: string, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：requestInStream(url: string, options?: HttpRequestOptions): Promise\<number>;<br>差异内容：NA|类名：HttpRequest；<br>API声明：requestInStream(url: string, options?: HttpRequestOptions): Promise\<number>;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：on(type: "dataReceive", callback: Callback\<ArrayBuffer>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：on(type: "dataReceive", callback: Callback\<ArrayBuffer>): void;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：off(type: "dataReceive", callback?: Callback\<ArrayBuffer>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：off(type: "dataReceive", callback?: Callback\<ArrayBuffer>): void;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：on(type: "dataEnd", callback: Callback\<void>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：on(type: "dataEnd", callback: Callback\<void>): void;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：off(type: "dataEnd", callback?: Callback\<void>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：off(type: "dataEnd", callback?: Callback\<void>): void;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|新增错误码|类名：HttpRequest；<br>API声明：request(url: string, callback: AsyncCallback\<HttpResponse>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：request(url: string, callback: AsyncCallback\<HttpResponse>): void;<br>差异内容：2300997,2300998|api/@ohos.net.http.d.ts|
|新增错误码|类名：HttpRequest；<br>API声明：request(url: string, options: HttpRequestOptions, callback: AsyncCallback\<HttpResponse>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：request(url: string, options: HttpRequestOptions, callback: AsyncCallback\<HttpResponse>): void;<br>差异内容：2300997,2300998|api/@ohos.net.http.d.ts|
|新增错误码|类名：HttpRequest；<br>API声明：request(url: string, options?: HttpRequestOptions): Promise\<HttpResponse>;<br>差异内容：NA|类名：HttpRequest；<br>API声明：request(url: string, options?: HttpRequestOptions): Promise\<HttpResponse>;<br>差异内容：2300997,2300998|api/@ohos.net.http.d.ts|
|新增错误码|类名：HttpRequest；<br>API声明：requestInStream(url: string, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：requestInStream(url: string, callback: AsyncCallback\<number>): void;<br>差异内容：2300997|api/@ohos.net.http.d.ts|
|新增错误码|类名：HttpRequest；<br>API声明：requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number>): void;<br>差异内容：2300997|api/@ohos.net.http.d.ts|
|新增错误码|类名：HttpRequest；<br>API声明：requestInStream(url: string, options?: HttpRequestOptions): Promise\<number>;<br>差异内容：NA|类名：HttpRequest；<br>API声明：requestInStream(url: string, options?: HttpRequestOptions): Promise\<number>;<br>差异内容：2300997|api/@ohos.net.http.d.ts|
|新增错误码|类名：UDPSocket；<br>API声明：send(options: UDPSendOptions, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：UDPSocket；<br>API声明：send(options: UDPSendOptions, callback: AsyncCallback\<void>): void;<br>差异内容：2301206,2301207,2301208,2301209,2301210,2301211,2301212,2301213|api/@ohos.net.socket.d.ts|
|新增错误码|类名：UDPSocket；<br>API声明：send(options: UDPSendOptions): Promise\<void>;<br>差异内容：NA|类名：UDPSocket；<br>API声明：send(options: UDPSendOptions): Promise\<void>;<br>差异内容：2301206,2301207,2301208,2301209,2301210,2301211,2301212,2301213|api/@ohos.net.socket.d.ts|
|新增错误码|类名：TCPSocket；<br>API声明：connect(options: TCPConnectOptions, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：TCPSocket；<br>API声明：connect(options: TCPConnectOptions, callback: AsyncCallback\<void>): void;<br>差异内容：2301206,2301207,2301208,2301209,2301210,2301211,2301212,2301213|api/@ohos.net.socket.d.ts|
|新增错误码|类名：TCPSocket；<br>API声明：connect(options: TCPConnectOptions): Promise\<void>;<br>差异内容：NA|类名：TCPSocket；<br>API声明：connect(options: TCPConnectOptions): Promise\<void>;<br>差异内容：2301206,2301207,2301208,2301209,2301210,2301211,2301212,2301213|api/@ohos.net.socket.d.ts|
|新增错误码|类名：TLSSocket；<br>API声明：connect(options: TLSConnectOptions, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：TLSSocket；<br>API声明：connect(options: TLSConnectOptions, callback: AsyncCallback\<void>): void;<br>差异内容：2301206,2301207,2301208,2301209,2301210,2301211,2301212,2301213|api/@ohos.net.socket.d.ts|
|新增错误码|类名：TLSSocket；<br>API声明：connect(options: TLSConnectOptions): Promise\<void>;<br>差异内容：NA|类名：TLSSocket；<br>API声明：connect(options: TLSConnectOptions): Promise\<void>;<br>差异内容：2301206,2301207,2301208,2301209,2301210,2301211,2301212,2301213|api/@ohos.net.socket.d.ts|
|新增错误码|类名：WebSocket；<br>API声明：connect(url: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|类名：WebSocket；<br>API声明：connect(url: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：2302998|api/@ohos.net.webSocket.d.ts|
|新增错误码|类名：WebSocket；<br>API声明：connect(url: string, options: WebSocketRequestOptions, callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|类名：WebSocket；<br>API声明：connect(url: string, options: WebSocketRequestOptions, callback: AsyncCallback\<boolean>): void;<br>差异内容：2302998|api/@ohos.net.webSocket.d.ts|
|新增错误码|类名：WebSocket；<br>API声明：connect(url: string, options?: WebSocketRequestOptions): Promise\<boolean>;<br>差异内容：NA|类名：WebSocket；<br>API声明：connect(url: string, options?: WebSocketRequestOptions): Promise\<boolean>;<br>差异内容：2302998|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：remoteValidation?: RemoteValidation;<br>差异内容：remoteValidation?: RemoteValidation;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：tlsOptions?: TlsOptions;<br>差异内容：tlsOptions?: TlsOptions;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：serverAuthentication?: ServerAuthentication;<br>差异内容：serverAuthentication?: ServerAuthentication;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export interface ServerAuthentication<br>差异内容：export interface ServerAuthentication|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ServerAuthentication；<br>API声明：credential: Credential;<br>差异内容：credential: Credential;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ServerAuthentication；<br>API声明：authenticationType?: AuthenticationType;<br>差异内容：authenticationType?: AuthenticationType;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type TlsOptions = 'system' \| TlsConfig;<br>差异内容：export type TlsOptions = 'system' \| TlsConfig;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type RemoteValidation = 'system' \| 'skip';<br>差异内容：export type RemoteValidation = 'system' \| 'skip';|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type AuthenticationType = 'basic' \| 'ntlm' \| 'digest';<br>差异内容：export type AuthenticationType = 'basic' \| 'ntlm' \| 'digest';|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export interface Credential<br>差异内容：export interface Credential|api/@ohos.net.http.d.ts|
|新增API|NA|类名：Credential；<br>API声明：username: string;<br>差异内容：username: string;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：Credential；<br>API声明：password: string;<br>差异内容：password: string;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export interface TlsConfig<br>差异内容：export interface TlsConfig|api/@ohos.net.http.d.ts|
|新增API|NA|类名：TlsConfig；<br>API声明：tlsVersionMin: TlsVersion;<br>差异内容：tlsVersionMin: TlsVersion;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：TlsConfig；<br>API声明：tlsVersionMax: TlsVersion;<br>差异内容：tlsVersionMax: TlsVersion;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：TlsConfig；<br>API声明：cipherSuites?: CipherSuite[];<br>差异内容：cipherSuites?: CipherSuite[];|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type TlsV13SpecificCipherSuite = 'TLS_AES_128_GCM_SHA256' \| 'TLS_AES_256_GCM_SHA384' \| 'TLS_CHACHA20_POLY1305_SHA256';<br>差异内容：export type TlsV13SpecificCipherSuite = 'TLS_AES_128_GCM_SHA256' \| 'TLS_AES_256_GCM_SHA384' \| 'TLS_CHACHA20_POLY1305_SHA256';|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type TlsV12SpecificCipherSuite = 'TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256' \| 'TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256' \| 'TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384' \| 'TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384' \| 'TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256' \| 'TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256' \| 'TLS_RSA_WITH_AES_128_GCM_SHA256' \| 'TLS_RSA_WITH_AES_256_GCM_SHA384';<br>差异内容：export type TlsV12SpecificCipherSuite = 'TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256' \| 'TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256' \| 'TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384' \| 'TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384' \| 'TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256' \| 'TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256' \| 'TLS_RSA_WITH_AES_128_GCM_SHA256' \| 'TLS_RSA_WITH_AES_256_GCM_SHA384';|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type TlsV10SpecificCipherSuite = 'TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA' \| 'TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA' \| 'TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA' \| 'TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA' \| 'TLS_RSA_WITH_AES_128_CBC_SHA' \| 'TLS_RSA_WITH_AES_256_CBC_SHA' \| 'TLS_RSA_WITH_3DES_EDE_CBC_SHA';<br>差异内容：export type TlsV10SpecificCipherSuite = 'TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA' \| 'TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA' \| 'TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA' \| 'TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA' \| 'TLS_RSA_WITH_AES_128_CBC_SHA' \| 'TLS_RSA_WITH_AES_256_CBC_SHA' \| 'TLS_RSA_WITH_3DES_EDE_CBC_SHA';|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type CipherSuite = TlsV13CipherSuite;<br>差异内容：export type CipherSuite = TlsV13CipherSuite;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type TlsV13CipherSuite = TlsV12CipherSuite \| TlsV13SpecificCipherSuite;<br>差异内容：export type TlsV13CipherSuite = TlsV12CipherSuite \| TlsV13SpecificCipherSuite;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type TlsV12CipherSuite = TlsV11CipherSuite \| TlsV12SpecificCipherSuite;<br>差异内容：export type TlsV12CipherSuite = TlsV11CipherSuite \| TlsV12SpecificCipherSuite;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type TlsV11CipherSuite = TlsV10CipherSuite;<br>差异内容：export type TlsV11CipherSuite = TlsV10CipherSuite;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type TlsV10CipherSuite = TlsV10SpecificCipherSuite;<br>差异内容：export type TlsV10CipherSuite = TlsV10SpecificCipherSuite;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export enum TlsVersion<br>差异内容：export enum TlsVersion|api/@ohos.net.http.d.ts|
|新增API|NA|类名：TlsVersion；<br>API声明：TLS_V_1_0 = 4<br>差异内容：TLS_V_1_0 = 4|api/@ohos.net.http.d.ts|
|新增API|NA|类名：TlsVersion；<br>API声明：TLS_V_1_1 = 5<br>差异内容：TLS_V_1_1 = 5|api/@ohos.net.http.d.ts|
|新增API|NA|类名：TlsVersion；<br>API声明：TLS_V_1_2 = 6<br>差异内容：TLS_V_1_2 = 6|api/@ohos.net.http.d.ts|
|新增API|NA|类名：TlsVersion；<br>API声明：TLS_V_1_3 = 7<br>差异内容：TLS_V_1_3 = 7|api/@ohos.net.http.d.ts|
|新增API|NA|类名：UDPSendOptions；<br>API声明：proxy?: ProxyOptions;<br>差异内容：proxy?: ProxyOptions;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export enum ProxyTypes<br>差异内容：export enum ProxyTypes|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：ProxyTypes；<br>API声明：NONE = 0<br>差异内容：NONE = 0|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：ProxyTypes；<br>API声明：SOCKS5 = 1<br>差异内容：SOCKS5 = 1|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface ProxyOptions<br>差异内容：export interface ProxyOptions|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：ProxyOptions；<br>API声明：type: ProxyTypes;<br>差异内容：type: ProxyTypes;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：ProxyOptions；<br>API声明：address: NetAddress;<br>差异内容：address: NetAddress;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：ProxyOptions；<br>API声明：username?: string;<br>差异内容：username?: string;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：ProxyOptions；<br>API声明：password?: string;<br>差异内容：password?: string;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPConnectOptions；<br>API声明：proxy?: ProxyOptions;<br>差异内容：proxy?: ProxyOptions;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：getSocketFd(): Promise\<number>;<br>差异内容：getSocketFd(): Promise\<number>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSConnectOptions；<br>API声明：proxy?: ProxyOptions;<br>差异内容：proxy?: ProxyOptions;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：networkSecurity；<br>API声明：export function isCleartextPermitted(): boolean;<br>差异内容：export function isCleartextPermitted(): boolean;|api/@ohos.net.networkSecurity.d.ts|
|新增API|NA|类名：networkSecurity；<br>API声明：export function isCleartextPermittedByHostName(hostName: string): boolean;<br>差异内容：export function isCleartextPermittedByHostName(hostName: string): boolean;|api/@ohos.net.networkSecurity.d.ts|
