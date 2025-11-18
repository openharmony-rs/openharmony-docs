| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API跨平台权限变更|类名：http；<br>API声明：type HttpProxy = connection.HttpProxy;<br>差异内容：NA|类名：http；<br>API声明：type HttpProxy = connection.HttpProxy;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequestOptions；<br>API声明：usingProxy?: boolean \| HttpProxy;<br>差异内容：NA|类名：HttpRequestOptions；<br>API声明：usingProxy?: boolean \| HttpProxy;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequestOptions；<br>API声明：caPath?: string;<br>差异内容：NA|类名：HttpRequestOptions；<br>API声明：caPath?: string;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequestOptions；<br>API声明：resumeFrom?: number;<br>差异内容：NA|类名：HttpRequestOptions；<br>API声明：resumeFrom?: number;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequestOptions；<br>API声明：resumeTo?: number;<br>差异内容：NA|类名：HttpRequestOptions；<br>API声明：resumeTo?: number;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequestOptions；<br>API声明：clientCert?: ClientCert;<br>差异内容：NA|类名：HttpRequestOptions；<br>API声明：clientCert?: ClientCert;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequestOptions；<br>API声明：dnsOverHttps?: string;<br>差异内容：NA|类名：HttpRequestOptions；<br>API声明：dnsOverHttps?: string;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequestOptions；<br>API声明：dnsServers?: Array\<string>;<br>差异内容：NA|类名：HttpRequestOptions；<br>API声明：dnsServers?: Array\<string>;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequestOptions；<br>API声明：maxLimit?: number;<br>差异内容：NA|类名：HttpRequestOptions；<br>API声明：maxLimit?: number;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequestOptions；<br>API声明：multiFormDataList?: Array\<MultiFormData>;<br>差异内容：NA|类名：HttpRequestOptions；<br>API声明：multiFormDataList?: Array\<MultiFormData>;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：http；<br>API声明：export interface MultiFormData<br>差异内容：NA|类名：http；<br>API声明：export interface MultiFormData<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：MultiFormData；<br>API声明：name: string;<br>差异内容：NA|类名：MultiFormData；<br>API声明：name: string;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：MultiFormData；<br>API声明：contentType: string;<br>差异内容：NA|类名：MultiFormData；<br>API声明：contentType: string;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：MultiFormData；<br>API声明：remoteFileName?: string;<br>差异内容：NA|类名：MultiFormData；<br>API声明：remoteFileName?: string;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：MultiFormData；<br>API声明：data?: string \| Object \| ArrayBuffer;<br>差异内容：NA|类名：MultiFormData；<br>API声明：data?: string \| Object \| ArrayBuffer;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：MultiFormData；<br>API声明：filePath?: string;<br>差异内容：NA|类名：MultiFormData；<br>API声明：filePath?: string;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：http；<br>API声明：export enum CertType<br>差异内容：NA|类名：http；<br>API声明：export enum CertType<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：CertType；<br>API声明：PEM = 'PEM'<br>差异内容：NA|类名：CertType；<br>API声明：PEM = 'PEM'<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：CertType；<br>API声明：DER = 'DER'<br>差异内容：NA|类名：CertType；<br>API声明：DER = 'DER'<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：CertType；<br>API声明：P12 = 'P12'<br>差异内容：NA|类名：CertType；<br>API声明：P12 = 'P12'<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：http；<br>API声明：export interface ClientCert<br>差异内容：NA|类名：http；<br>API声明：export interface ClientCert<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：ClientCert；<br>API声明：certPath: string;<br>差异内容：NA|类名：ClientCert；<br>API声明：certPath: string;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：ClientCert；<br>API声明：certType?: CertType;<br>差异内容：NA|类名：ClientCert；<br>API声明：certType?: CertType;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：ClientCert；<br>API声明：keyPath: string;<br>差异内容：NA|类名：ClientCert；<br>API声明：keyPath: string;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：ClientCert；<br>API声明：keyPassword?: string;<br>差异内容：NA|类名：ClientCert；<br>API声明：keyPassword?: string;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：on(type: 'dataReceiveProgress', callback: Callback\<DataReceiveProgressInfo>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：on(type: 'dataReceiveProgress', callback: Callback\<DataReceiveProgressInfo>): void;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：off(type: 'dataReceiveProgress', callback?: Callback\<DataReceiveProgressInfo>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：off(type: 'dataReceiveProgress', callback?: Callback\<DataReceiveProgressInfo>): void;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：on(type: 'dataSendProgress', callback: Callback\<DataSendProgressInfo>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：on(type: 'dataSendProgress', callback: Callback\<DataSendProgressInfo>): void;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：off(type: 'dataSendProgress', callback?: Callback\<DataSendProgressInfo>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：off(type: 'dataSendProgress', callback?: Callback\<DataSendProgressInfo>): void;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpProtocol；<br>API声明：HTTP3<br>差异内容：NA|类名：HttpProtocol；<br>API声明：HTTP3<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpResponse；<br>API声明：performanceTiming: PerformanceTiming;<br>差异内容：NA|类名：HttpResponse；<br>API声明：performanceTiming: PerformanceTiming;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：http；<br>API声明：export interface PerformanceTiming<br>差异内容：NA|类名：http；<br>API声明：export interface PerformanceTiming<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：PerformanceTiming；<br>API声明：dnsTiming: number;<br>差异内容：NA|类名：PerformanceTiming；<br>API声明：dnsTiming: number;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：PerformanceTiming；<br>API声明：tcpTiming: number;<br>差异内容：NA|类名：PerformanceTiming；<br>API声明：tcpTiming: number;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：PerformanceTiming；<br>API声明：tlsTiming: number;<br>差异内容：NA|类名：PerformanceTiming；<br>API声明：tlsTiming: number;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：PerformanceTiming；<br>API声明：firstSendTiming: number;<br>差异内容：NA|类名：PerformanceTiming；<br>API声明：firstSendTiming: number;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：PerformanceTiming；<br>API声明：firstReceiveTiming: number;<br>差异内容：NA|类名：PerformanceTiming；<br>API声明：firstReceiveTiming: number;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：PerformanceTiming；<br>API声明：totalFinishTiming: number;<br>差异内容：NA|类名：PerformanceTiming；<br>API声明：totalFinishTiming: number;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：PerformanceTiming；<br>API声明：redirectTiming: number;<br>差异内容：NA|类名：PerformanceTiming；<br>API声明：redirectTiming: number;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：PerformanceTiming；<br>API声明：responseHeaderTiming: number;<br>差异内容：NA|类名：PerformanceTiming；<br>API声明：responseHeaderTiming: number;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：PerformanceTiming；<br>API声明：responseBodyTiming: number;<br>差异内容：NA|类名：PerformanceTiming；<br>API声明：responseBodyTiming: number;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：PerformanceTiming；<br>API声明：totalTiming: number;<br>差异内容：NA|类名：PerformanceTiming；<br>API声明：totalTiming: number;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：http；<br>API声明：export interface DataReceiveProgressInfo<br>差异内容：NA|类名：http；<br>API声明：export interface DataReceiveProgressInfo<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：DataReceiveProgressInfo；<br>API声明：receiveSize: number;<br>差异内容：NA|类名：DataReceiveProgressInfo；<br>API声明：receiveSize: number;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：DataReceiveProgressInfo；<br>API声明：totalSize: number;<br>差异内容：NA|类名：DataReceiveProgressInfo；<br>API声明：totalSize: number;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：http；<br>API声明：export interface DataSendProgressInfo<br>差异内容：NA|类名：http；<br>API声明：export interface DataSendProgressInfo<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：DataSendProgressInfo；<br>API声明：sendSize: number;<br>差异内容：NA|类名：DataSendProgressInfo；<br>API声明：sendSize: number;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：DataSendProgressInfo；<br>API声明：totalSize: number;<br>差异内容：NA|类名：DataSendProgressInfo；<br>API声明：totalSize: number;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：socket；<br>API声明：function constructMulticastSocketInstance(): MulticastSocket;<br>差异内容：NA|类名：socket；<br>API声明：function constructMulticastSocketInstance(): MulticastSocket;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：socket；<br>API声明：function constructLocalSocketInstance(): LocalSocket;<br>差异内容：NA|类名：socket；<br>API声明：function constructLocalSocketInstance(): LocalSocket;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：socket；<br>API声明：function constructLocalSocketServerInstance(): LocalSocketServer;<br>差异内容：NA|类名：socket；<br>API声明：function constructLocalSocketServerInstance(): LocalSocketServer;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：socket；<br>API声明：export interface LocalSocketMessageInfo<br>差异内容：NA|类名：socket；<br>API声明：export interface LocalSocketMessageInfo<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketMessageInfo；<br>API声明：message: ArrayBuffer;<br>差异内容：NA|类名：LocalSocketMessageInfo；<br>API声明：message: ArrayBuffer;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketMessageInfo；<br>API声明：address: string;<br>差异内容：NA|类名：LocalSocketMessageInfo；<br>API声明：address: string;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketMessageInfo；<br>API声明：size: number;<br>差异内容：NA|类名：LocalSocketMessageInfo；<br>API声明：size: number;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：socket；<br>API声明：export interface LocalAddress<br>差异内容：NA|类名：socket；<br>API声明：export interface LocalAddress<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalAddress；<br>API声明：address: string;<br>差异内容：NA|类名：LocalAddress；<br>API声明：address: string;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：socket；<br>API声明：export interface LocalConnectOptions<br>差异内容：NA|类名：socket；<br>API声明：export interface LocalConnectOptions<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalConnectOptions；<br>API声明：address: LocalAddress;<br>差异内容：NA|类名：LocalConnectOptions；<br>API声明：address: LocalAddress;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalConnectOptions；<br>API声明：timeout?: number;<br>差异内容：NA|类名：LocalConnectOptions；<br>API声明：timeout?: number;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：socket；<br>API声明：export interface LocalSendOptions<br>差异内容：NA|类名：socket；<br>API声明：export interface LocalSendOptions<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSendOptions；<br>API声明：data: string \| ArrayBuffer;<br>差异内容：NA|类名：LocalSendOptions；<br>API声明：data: string \| ArrayBuffer;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSendOptions；<br>API声明：encoding?: string;<br>差异内容：NA|类名：LocalSendOptions；<br>API声明：encoding?: string;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：socket；<br>API声明：export interface MulticastSocket<br>差异内容：NA|类名：socket；<br>API声明：export interface MulticastSocket<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：MulticastSocket；<br>API声明：addMembership(multicastAddress: NetAddress, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：MulticastSocket；<br>API声明：addMembership(multicastAddress: NetAddress, callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：MulticastSocket；<br>API声明：addMembership(multicastAddress: NetAddress): Promise\<void>;<br>差异内容：NA|类名：MulticastSocket；<br>API声明：addMembership(multicastAddress: NetAddress): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：MulticastSocket；<br>API声明：dropMembership(multicastAddress: NetAddress, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：MulticastSocket；<br>API声明：dropMembership(multicastAddress: NetAddress, callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：MulticastSocket；<br>API声明：dropMembership(multicastAddress: NetAddress): Promise\<void>;<br>差异内容：NA|类名：MulticastSocket；<br>API声明：dropMembership(multicastAddress: NetAddress): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：MulticastSocket；<br>API声明：setMulticastTTL(ttl: number, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：MulticastSocket；<br>API声明：setMulticastTTL(ttl: number, callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：MulticastSocket；<br>API声明：setMulticastTTL(ttl: number): Promise\<void>;<br>差异内容：NA|类名：MulticastSocket；<br>API声明：setMulticastTTL(ttl: number): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：MulticastSocket；<br>API声明：getMulticastTTL(callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：MulticastSocket；<br>API声明：getMulticastTTL(callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：MulticastSocket；<br>API声明：getMulticastTTL(): Promise\<number>;<br>差异内容：NA|类名：MulticastSocket；<br>API声明：getMulticastTTL(): Promise\<number>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：MulticastSocket；<br>API声明：setLoopbackMode(flag: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：MulticastSocket；<br>API声明：setLoopbackMode(flag: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：MulticastSocket；<br>API声明：setLoopbackMode(flag: boolean): Promise\<void>;<br>差异内容：NA|类名：MulticastSocket；<br>API声明：setLoopbackMode(flag: boolean): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：MulticastSocket；<br>API声明：getLoopbackMode(callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|类名：MulticastSocket；<br>API声明：getLoopbackMode(callback: AsyncCallback\<boolean>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：MulticastSocket；<br>API声明：getLoopbackMode(): Promise\<boolean>;<br>差异内容：NA|类名：MulticastSocket；<br>API声明：getLoopbackMode(): Promise\<boolean>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：socket；<br>API声明：export interface LocalSocket<br>差异内容：NA|类名：socket；<br>API声明：export interface LocalSocket<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocket；<br>API声明：bind(address: LocalAddress): Promise\<void>;<br>差异内容：NA|类名：LocalSocket；<br>API声明：bind(address: LocalAddress): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocket；<br>API声明：connect(options: LocalConnectOptions): Promise\<void>;<br>差异内容：NA|类名：LocalSocket；<br>API声明：connect(options: LocalConnectOptions): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocket；<br>API声明：send(options: LocalSendOptions): Promise\<void>;<br>差异内容：NA|类名：LocalSocket；<br>API声明：send(options: LocalSendOptions): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocket；<br>API声明：close(): Promise\<void>;<br>差异内容：NA|类名：LocalSocket；<br>API声明：close(): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocket；<br>API声明：getState(): Promise\<SocketStateBase>;<br>差异内容：NA|类名：LocalSocket；<br>API声明：getState(): Promise\<SocketStateBase>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocket；<br>API声明：getSocketFd(): Promise\<number>;<br>差异内容：NA|类名：LocalSocket；<br>API声明：getSocketFd(): Promise\<number>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocket；<br>API声明：setExtraOptions(options: ExtraOptionsBase): Promise\<void>;<br>差异内容：NA|类名：LocalSocket；<br>API声明：setExtraOptions(options: ExtraOptionsBase): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocket；<br>API声明：getExtraOptions(): Promise\<ExtraOptionsBase>;<br>差异内容：NA|类名：LocalSocket；<br>API声明：getExtraOptions(): Promise\<ExtraOptionsBase>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocket；<br>API声明：on(type: 'message', callback: Callback\<LocalSocketMessageInfo>): void;<br>差异内容：NA|类名：LocalSocket；<br>API声明：on(type: 'message', callback: Callback\<LocalSocketMessageInfo>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocket；<br>API声明：off(type: 'message', callback?: Callback\<LocalSocketMessageInfo>): void;<br>差异内容：NA|类名：LocalSocket；<br>API声明：off(type: 'message', callback?: Callback\<LocalSocketMessageInfo>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocket；<br>API声明：on(type: 'connect', callback: Callback\<void>): void;<br>差异内容：NA|类名：LocalSocket；<br>API声明：on(type: 'connect', callback: Callback\<void>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocket；<br>API声明：off(type: 'connect', callback?: Callback\<void>): void;<br>差异内容：NA|类名：LocalSocket；<br>API声明：off(type: 'connect', callback?: Callback\<void>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocket；<br>API声明：on(type: 'close', callback: Callback\<void>): void;<br>差异内容：NA|类名：LocalSocket；<br>API声明：on(type: 'close', callback: Callback\<void>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocket；<br>API声明：off(type: 'close', callback?: Callback\<void>): void;<br>差异内容：NA|类名：LocalSocket；<br>API声明：off(type: 'close', callback?: Callback\<void>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocket；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：NA|类名：LocalSocket；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocket；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：NA|类名：LocalSocket；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：socket；<br>API声明：export interface LocalSocketConnection<br>差异内容：NA|类名：socket；<br>API声明：export interface LocalSocketConnection<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketConnection；<br>API声明：clientId: number;<br>差异内容：NA|类名：LocalSocketConnection；<br>API声明：clientId: number;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketConnection；<br>API声明：send(options: LocalSendOptions): Promise\<void>;<br>差异内容：NA|类名：LocalSocketConnection；<br>API声明：send(options: LocalSendOptions): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketConnection；<br>API声明：close(): Promise\<void>;<br>差异内容：NA|类名：LocalSocketConnection；<br>API声明：close(): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketConnection；<br>API声明：on(type: 'message', callback: Callback\<LocalSocketMessageInfo>): void;<br>差异内容：NA|类名：LocalSocketConnection；<br>API声明：on(type: 'message', callback: Callback\<LocalSocketMessageInfo>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketConnection；<br>API声明：off(type: 'message', callback?: Callback\<LocalSocketMessageInfo>): void;<br>差异内容：NA|类名：LocalSocketConnection；<br>API声明：off(type: 'message', callback?: Callback\<LocalSocketMessageInfo>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketConnection；<br>API声明：on(type: 'close', callback: Callback\<void>): void;<br>差异内容：NA|类名：LocalSocketConnection；<br>API声明：on(type: 'close', callback: Callback\<void>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketConnection；<br>API声明：off(type: 'close', callback?: Callback\<void>): void;<br>差异内容：NA|类名：LocalSocketConnection；<br>API声明：off(type: 'close', callback?: Callback\<void>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketConnection；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：NA|类名：LocalSocketConnection；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketConnection；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：NA|类名：LocalSocketConnection；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：socket；<br>API声明：export interface LocalSocketServer<br>差异内容：NA|类名：socket；<br>API声明：export interface LocalSocketServer<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketServer；<br>API声明：listen(address: LocalAddress): Promise\<void>;<br>差异内容：NA|类名：LocalSocketServer；<br>API声明：listen(address: LocalAddress): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketServer；<br>API声明：getState(): Promise\<SocketStateBase>;<br>差异内容：NA|类名：LocalSocketServer；<br>API声明：getState(): Promise\<SocketStateBase>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketServer；<br>API声明：setExtraOptions(options: ExtraOptionsBase): Promise\<void>;<br>差异内容：NA|类名：LocalSocketServer；<br>API声明：setExtraOptions(options: ExtraOptionsBase): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketServer；<br>API声明：getExtraOptions(): Promise\<ExtraOptionsBase>;<br>差异内容：NA|类名：LocalSocketServer；<br>API声明：getExtraOptions(): Promise\<ExtraOptionsBase>;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketServer；<br>API声明：on(type: 'connect', callback: Callback\<LocalSocketConnection>): void;<br>差异内容：NA|类名：LocalSocketServer；<br>API声明：on(type: 'connect', callback: Callback\<LocalSocketConnection>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketServer；<br>API声明：off(type: 'connect', callback?: Callback\<LocalSocketConnection>): void;<br>差异内容：NA|类名：LocalSocketServer；<br>API声明：off(type: 'connect', callback?: Callback\<LocalSocketConnection>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketServer；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：NA|类名：LocalSocketServer；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：LocalSocketServer；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：NA|类名：LocalSocketServer；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：TCPSocketConnection；<br>API声明：on(type: 'message', callback: Callback\<SocketMessageInfo>): void;<br>差异内容：NA|类名：TCPSocketConnection；<br>API声明：on(type: 'message', callback: Callback\<SocketMessageInfo>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：TCPSocketConnection；<br>API声明：off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;<br>差异内容：NA|类名：TCPSocketConnection；<br>API声明：off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：TLSSocketConnection；<br>API声明：on(type: 'message', callback: Callback\<SocketMessageInfo>): void;<br>差异内容：NA|类名：TLSSocketConnection；<br>API声明：on(type: 'message', callback: Callback\<SocketMessageInfo>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：TLSSocketConnection；<br>API声明：off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;<br>差异内容：NA|类名：TLSSocketConnection；<br>API声明：off(type: 'message', callback?: Callback\<SocketMessageInfo>): void;<br>差异内容：crossplatform|api/@ohos.net.socket.d.ts|
|API跨平台权限变更|类名：WebSocketRequestOptions；<br>API声明：caPath?: string;<br>差异内容：NA|类名：WebSocketRequestOptions；<br>API声明：caPath?: string;<br>差异内容：crossplatform|api/@ohos.net.webSocket.d.ts|
|API跨平台权限变更|类名：WebSocketRequestOptions；<br>API声明：clientCert?: ClientCert;<br>差异内容：NA|类名：WebSocketRequestOptions；<br>API声明：clientCert?: ClientCert;<br>差异内容：crossplatform|api/@ohos.net.webSocket.d.ts|
|API跨平台权限变更|类名：webSocket；<br>API声明：export interface ClientCert<br>差异内容：NA|类名：webSocket；<br>API声明：export interface ClientCert<br>差异内容：crossplatform|api/@ohos.net.webSocket.d.ts|
|API跨平台权限变更|类名：ClientCert；<br>API声明：certPath: string;<br>差异内容：NA|类名：ClientCert；<br>API声明：certPath: string;<br>差异内容：crossplatform|api/@ohos.net.webSocket.d.ts|
|API跨平台权限变更|类名：ClientCert；<br>API声明：keyPath: string;<br>差异内容：NA|类名：ClientCert；<br>API声明：keyPath: string;<br>差异内容：crossplatform|api/@ohos.net.webSocket.d.ts|
|API跨平台权限变更|类名：ClientCert；<br>API声明：keyPassword?: string;<br>差异内容：NA|类名：ClientCert；<br>API声明：keyPassword?: string;<br>差异内容：crossplatform|api/@ohos.net.webSocket.d.ts|
|API跨平台权限变更|类名：WebSocket；<br>API声明：on(type: 'dataEnd', callback: Callback\<void>): void;<br>差异内容：NA|类名：WebSocket；<br>API声明：on(type: 'dataEnd', callback: Callback\<void>): void;<br>差异内容：crossplatform|api/@ohos.net.webSocket.d.ts|
|API跨平台权限变更|类名：WebSocket；<br>API声明：off(type: 'dataEnd', callback?: Callback\<void>): void;<br>差异内容：NA|类名：WebSocket；<br>API声明：off(type: 'dataEnd', callback?: Callback\<void>): void;<br>差异内容：crossplatform|api/@ohos.net.webSocket.d.ts|
|新增错误码|类名：networkSecurity；<br>API声明：export function certVerification(cert: CertBlob, caCert?: CertBlob): Promise\<number>;<br>差异内容：NA|类名：networkSecurity；<br>API声明：export function certVerification(cert: CertBlob, caCert?: CertBlob): Promise\<number>;<br>差异内容：2305018,2305069|api/@ohos.net.networkSecurity.d.ts|
|新增错误码|类名：networkSecurity；<br>API声明：export function certVerificationSync(cert: CertBlob, caCert?: CertBlob): number;<br>差异内容：NA|类名：networkSecurity；<br>API声明：export function certVerificationSync(cert: CertBlob, caCert?: CertBlob): number;<br>差异内容：2305018,2305069|api/@ohos.net.networkSecurity.d.ts|
|新增错误码|类名：WebSocket；<br>API声明：connect(url: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|类名：WebSocket；<br>API声明：connect(url: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：2302001,2302002,2302003,2302999|api/@ohos.net.webSocket.d.ts|
|新增错误码|类名：WebSocket；<br>API声明：connect(url: string, options: WebSocketRequestOptions, callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|类名：WebSocket；<br>API声明：connect(url: string, options: WebSocketRequestOptions, callback: AsyncCallback\<boolean>): void;<br>差异内容：2302001,2302002,2302003,2302999|api/@ohos.net.webSocket.d.ts|
|新增错误码|类名：WebSocket；<br>API声明：connect(url: string, options?: WebSocketRequestOptions): Promise\<boolean>;<br>差异内容：NA|类名：WebSocket；<br>API声明：connect(url: string, options?: WebSocketRequestOptions): Promise\<boolean>;<br>差异内容：2302001,2302002,2302003,2302999|api/@ohos.net.webSocket.d.ts|
|删除错误码|类名：connection；<br>API声明：function getDefaultNet(): Promise\<NetHandle>;<br>差异内容：401|类名：connection；<br>API声明：function getDefaultNet(): Promise\<NetHandle>;<br>差异内容：NA|api/@ohos.net.connection.d.ts|
|删除错误码|类名：connection；<br>API声明：function getDefaultNetSync(): NetHandle;<br>差异内容：401|类名：connection；<br>API声明：function getDefaultNetSync(): NetHandle;<br>差异内容：NA|api/@ohos.net.connection.d.ts|
|删除错误码|类名：connection；<br>API声明：function getAllNets(): Promise\<Array\<NetHandle>>;<br>差异内容：401|类名：connection；<br>API声明：function getAllNets(): Promise\<Array\<NetHandle>>;<br>差异内容：NA|api/@ohos.net.connection.d.ts|
|删除错误码|类名：connection；<br>API声明：function getAllNetsSync(): Array\<NetHandle>;<br>差异内容：401|类名：connection；<br>API声明：function getAllNetsSync(): Array\<NetHandle>;<br>差异内容：NA|api/@ohos.net.connection.d.ts|
|删除错误码|类名：connection；<br>API声明：function isDefaultNetMetered(): Promise\<boolean>;<br>差异内容：401|类名：connection；<br>API声明：function isDefaultNetMetered(): Promise\<boolean>;<br>差异内容：NA|api/@ohos.net.connection.d.ts|
|删除错误码|类名：connection；<br>API声明：function isDefaultNetMeteredSync(): boolean;<br>差异内容：401|类名：connection；<br>API声明：function isDefaultNetMeteredSync(): boolean;<br>差异内容：NA|api/@ohos.net.connection.d.ts|
|删除错误码|类名：connection；<br>API声明：function hasDefaultNet(): Promise\<boolean>;<br>差异内容：401|类名：connection；<br>API声明：function hasDefaultNet(): Promise\<boolean>;<br>差异内容：NA|api/@ohos.net.connection.d.ts|
|删除错误码|类名：connection；<br>API声明：function hasDefaultNetSync(): boolean;<br>差异内容：401|类名：connection；<br>API声明：function hasDefaultNetSync(): boolean;<br>差异内容：NA|api/@ohos.net.connection.d.ts|
|删除错误码|类名：connection；<br>API声明：function getAppNet(): Promise\<NetHandle>;<br>差异内容：401|类名：connection；<br>API声明：function getAppNet(): Promise\<NetHandle>;<br>差异内容：NA|api/@ohos.net.connection.d.ts|
|删除错误码|类名：connection；<br>API声明：function getAppNetSync(): NetHandle;<br>差异内容：401|类名：connection；<br>API声明：function getAppNetSync(): NetHandle;<br>差异内容：NA|api/@ohos.net.connection.d.ts|
|删除错误码|类名：connection；<br>API声明：function clearCustomDnsRules(): Promise\<void>;<br>差异内容：401|类名：connection；<br>API声明：function clearCustomDnsRules(): Promise\<void>;<br>差异内容：NA|api/@ohos.net.connection.d.ts|
|删除错误码|类名：NetConnection；<br>API声明：unregister(callback: AsyncCallback\<void>): void;<br>差异内容：201|类名：NetConnection；<br>API声明：unregister(callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.net.connection.d.ts|
|函数变更|类名：TLSSocket；<br>API声明：send(data: string, callback: AsyncCallback\<void>): void;<br>差异内容：data: string|类名：TLSSocket；<br>API声明：send(data: string \| ArrayBuffer, callback: AsyncCallback\<void>): void;<br>差异内容：data: string \| ArrayBuffer|api/@ohos.net.socket.d.ts|
|函数变更|类名：TLSSocket；<br>API声明：send(data: string): Promise\<void>;<br>差异内容：data: string|类名：TLSSocket；<br>API声明：send(data: string \| ArrayBuffer): Promise\<void>;<br>差异内容：data: string \| ArrayBuffer|api/@ohos.net.socket.d.ts|
|函数变更|类名：TLSSocketConnection；<br>API声明：send(data: string, callback: AsyncCallback\<void>): void;<br>差异内容：data: string|类名：TLSSocketConnection；<br>API声明：send(data: string \| ArrayBuffer, callback: AsyncCallback\<void>): void;<br>差异内容：data: string \| ArrayBuffer|api/@ohos.net.socket.d.ts|
|函数变更|类名：TLSSocketConnection；<br>API声明：send(data: string): Promise\<void>;<br>差异内容：data: string|类名：TLSSocketConnection；<br>API声明：send(data: string \| ArrayBuffer): Promise\<void>;<br>差异内容：data: string \| ArrayBuffer|api/@ohos.net.socket.d.ts|
|属性变更|类名：TLSSecureOptions；<br>API声明：ca: string \| Array\<string>;<br>差异内容：ca: string \| Array\<string>;|类名：TLSSecureOptions；<br>API声明：ca?: string \| Array\<string>;<br>差异内容：ca?: string \| Array\<string>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：NetCap；<br>API声明：NET_CAPABILITY_PORTAL = 17<br>差异内容：NET_CAPABILITY_PORTAL = 17|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetCap；<br>API声明：NET_CAPABILITY_CHECKING_CONNECTIVITY = 31<br>差异内容：NET_CAPABILITY_CHECKING_CONNECTIVITY = 31|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetBearType；<br>API声明：BEARER_BLUETOOTH = 2<br>差异内容：BEARER_BLUETOOTH = 2|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：NetBearType；<br>API声明：BEARER_VPN = 4<br>差异内容：BEARER_VPN = 4|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：HttpProxy；<br>API声明：username?: string;<br>差异内容：username?: string;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：HttpProxy；<br>API声明：password?: string;<br>差异内容：password?: string;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：certificatePinning?: CertificatePinning \| CertificatePinning[];<br>差异内容：certificatePinning?: CertificatePinning \| CertificatePinning[];|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：interface CertificatePinning<br>差异内容：interface CertificatePinning|api/@ohos.net.http.d.ts|
|新增API|NA|类名：CertificatePinning；<br>API声明：publicKeyHash: string;<br>差异内容：publicKeyHash: string;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：CertificatePinning；<br>API声明：hashAlgorithm: 'SHA-256';<br>差异内容：hashAlgorithm: 'SHA-256';|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ResponseCode；<br>API声明：RANGE_NOT_SATISFIABLE<br>差异内容：RANGE_NOT_SATISFIABLE|api/@ohos.net.http.d.ts|
|新增API|NA|类名：socket；<br>API声明：function constructTLSSocketInstance(tcpSocket: TCPSocket): TLSSocket;<br>差异内容：function constructTLSSocketInstance(tcpSocket: TCPSocket): TLSSocket;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：UDPSocket；<br>API声明：getLocalAddress(): Promise\<NetAddress>;<br>差异内容：getLocalAddress(): Promise\<NetAddress>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocket；<br>API声明：getLocalAddress(): Promise\<string>;<br>差异内容：getLocalAddress(): Promise\<string>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketConnection；<br>API声明：getLocalAddress(): Promise\<string>;<br>差异内容：getLocalAddress(): Promise\<string>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketServer；<br>API声明：getLocalAddress(): Promise\<string>;<br>差异内容：getLocalAddress(): Promise\<string>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocket；<br>API声明：getLocalAddress(): Promise\<NetAddress>;<br>差异内容：getLocalAddress(): Promise\<NetAddress>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：getLocalAddress(): Promise\<NetAddress>;<br>差异内容：getLocalAddress(): Promise\<NetAddress>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSecureOptions；<br>API声明：isBidirectionalAuthentication?: boolean;<br>差异内容：isBidirectionalAuthentication?: boolean;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSConnectOptions；<br>API声明：skipRemoteValidation?: boolean;<br>差异内容：skipRemoteValidation?: boolean;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketConnection；<br>API声明：getLocalAddress(): Promise\<NetAddress>;<br>差异内容：getLocalAddress(): Promise\<NetAddress>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketServer；<br>API声明：getLocalAddress(): Promise\<NetAddress>;<br>差异内容：getLocalAddress(): Promise\<NetAddress>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketConnection；<br>API声明：getLocalAddress(): Promise\<NetAddress>;<br>差异内容：getLocalAddress(): Promise\<NetAddress>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketServer；<br>API声明：getLocalAddress(): Promise\<NetAddress>;<br>差异内容：getLocalAddress(): Promise\<NetAddress>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：webSocket；<br>API声明：type HttpProxy = connection.HttpProxy;<br>差异内容：type HttpProxy = connection.HttpProxy;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketRequestOptions；<br>API声明：proxy?: ProxyConfiguration;<br>差异内容：proxy?: ProxyConfiguration;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketRequestOptions；<br>API声明：protocol?: string;<br>差异内容：protocol?: string;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：webSocket；<br>API声明：export type ProxyConfiguration = 'system' \| 'no-proxy' \| HttpProxy;<br>差异内容：export type ProxyConfiguration = 'system' \| 'no-proxy' \| HttpProxy;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：webSocket；<br>API声明：export type ResponseHeaders = {<br>        [k: string]: string \| string[] \| undefined;<br>    };<br>差异内容：export type ResponseHeaders = {<br>        [k: string]: string \| string[] \| undefined;<br>    };|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：on(type: 'headerReceive', callback: Callback\<ResponseHeaders>): void;<br>差异内容：on(type: 'headerReceive', callback: Callback\<ResponseHeaders>): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocket；<br>API声明：off(type: 'headerReceive', callback?: Callback\<ResponseHeaders>): void;<br>差异内容：off(type: 'headerReceive', callback?: Callback\<ResponseHeaders>): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：statistics；<br>API声明：type NetBearType = connection.NetBearType;<br>差异内容：type NetBearType = connection.NetBearType;|api/@ohos.net.statistics.d.ts|
|新增kit|类名：global；<br>API声明：api\application\VpnExtensionContext.d.ts<br>差异内容：NA|类名：global；<br>API声明：api\application\VpnExtensionContext.d.ts<br>差异内容：NetworkKit|api/application/VpnExtensionContext.d.ts|
|API从不支持元服务到支持元服务|类名：connection；<br>API声明：export interface NetAddress<br>差异内容：NA|类名：connection；<br>API声明：export interface NetAddress<br>差异内容：atomicservice|api/@ohos.net.connection.d.ts|
|API从不支持元服务到支持元服务|类名：NetAddress；<br>API声明：address: string;<br>差异内容：NA|类名：NetAddress；<br>API声明：address: string;<br>差异内容：atomicservice|api/@ohos.net.connection.d.ts|
|API从不支持元服务到支持元服务|类名：NetAddress；<br>API声明：family?: number;<br>差异内容：NA|类名：NetAddress；<br>API声明：family?: number;<br>差异内容：atomicservice|api/@ohos.net.connection.d.ts|
|API从不支持元服务到支持元服务|类名：NetAddress；<br>API声明：port?: number;<br>差异内容：NA|类名：NetAddress；<br>API声明：port?: number;<br>差异内容：atomicservice|api/@ohos.net.connection.d.ts|
|API从不支持元服务到支持元服务|类名：mdns；<br>API声明：type NetAddress = connection.NetAddress;<br>差异内容：NA|类名：mdns；<br>API声明：type NetAddress = connection.NetAddress;<br>差异内容：atomicservice|api/@ohos.net.mdns.d.ts|
