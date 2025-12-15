| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增错误码|类名：distributedDeviceManager；<br>API声明：function releaseDeviceManager(deviceManager: DeviceManager): void;<br>差异内容：NA|类名：distributedDeviceManager；<br>API声明：function releaseDeviceManager(deviceManager: DeviceManager): void;<br>差异内容：201|api/@ohos.distributedDeviceManager.d.ts|
|新增错误码|类名：DeviceManager；<br>API声明：getAvailableDeviceListSync(): Array\<DeviceBasicInfo>;<br>差异内容：NA|类名：DeviceManager；<br>API声明：getAvailableDeviceListSync(): Array\<DeviceBasicInfo>;<br>差异内容：401|api/@ohos.distributedDeviceManager.d.ts|
|新增错误码|类名：DeviceManager；<br>API声明：stopDiscovering(): void;<br>差异内容：NA|类名：DeviceManager；<br>API声明：stopDiscovering(): void;<br>差异内容：11600104,401|api/@ohos.distributedDeviceManager.d.ts|
|权限变更|类名：distributedDeviceManager；<br>API声明：function releaseDeviceManager(deviceManager: DeviceManager): void;<br>差异内容：NA|类名：distributedDeviceManager；<br>API声明：function releaseDeviceManager(deviceManager: DeviceManager): void;<br>差异内容：ohos.permission.DISTRIBUTED_DATASYNC|api/@ohos.distributedDeviceManager.d.ts|
|删除API|类名：global；<br>API声明：export default class DistributedExtensionAbility<br>差异内容：export default class DistributedExtensionAbility|NA|api/@ohos.application.DistributedExtensionAbility.d.ts|
|删除API|类名：DistributedExtensionAbility；<br>API声明：context: DistributedExtensionContext;<br>差异内容：context: DistributedExtensionContext;|NA|api/@ohos.application.DistributedExtensionAbility.d.ts|
|删除API|类名：DistributedExtensionAbility；<br>API声明：onCreate(want: Want): void;<br>差异内容：onCreate(want: Want): void;|NA|api/@ohos.application.DistributedExtensionAbility.d.ts|
|删除API|类名：DistributedExtensionAbility；<br>API声明：onDestroy(): void;<br>差异内容：onDestroy(): void;|NA|api/@ohos.application.DistributedExtensionAbility.d.ts|
|删除API|类名：DistributedExtensionAbility；<br>API声明：onCollaborate(wantParam: Record\<string, Object>): AbilityConstant.CollaborateResult;<br>差异内容：onCollaborate(wantParam: Record\<string, Object>): AbilityConstant.CollaborateResult;|NA|api/@ohos.application.DistributedExtensionAbility.d.ts|
|删除API|类名：global；<br>API声明：export default class DistributedExtensionContext<br>差异内容：export default class DistributedExtensionContext|NA|api/@ohos.application.DistributedExtensionContext.d.ts|
|删除API|类名：global；<br>API声明：declare namespace abilityConnectionManager<br>差异内容：declare namespace abilityConnectionManager|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：interface PeerInfo<br>差异内容：interface PeerInfo|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：PeerInfo；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：PeerInfo；<br>API声明：bundleName: string;<br>差异内容：bundleName: string;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：PeerInfo；<br>API声明：moduleName: string;<br>差异内容：moduleName: string;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：PeerInfo；<br>API声明：abilityName: string;<br>差异内容：abilityName: string;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：PeerInfo；<br>API声明：serviceName?: string;<br>差异内容：serviceName?: string;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：interface ConnectOptions<br>差异内容：interface ConnectOptions|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：ConnectOptions；<br>API声明：needSendData?: boolean;<br>差异内容：needSendData?: boolean;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：ConnectOptions；<br>API声明：startOptions?: StartOptionParams;<br>差异内容：startOptions?: StartOptionParams;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：ConnectOptions；<br>API声明：parameters?: Record\<string, string>;<br>差异内容：parameters?: Record\<string, string>;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：interface ConnectResult<br>差异内容：interface ConnectResult|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：ConnectResult；<br>API声明：isConnected: boolean;<br>差异内容：isConnected: boolean;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：ConnectResult；<br>API声明：errorCode?: ConnectErrorCode;<br>差异内容：errorCode?: ConnectErrorCode;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：ConnectResult；<br>API声明：reason?: string;<br>差异内容：reason?: string;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：export enum ConnectErrorCode<br>差异内容：export enum ConnectErrorCode|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：ConnectErrorCode；<br>API声明：CONNECTED_SESSION_EXISTS = 0<br>差异内容：CONNECTED_SESSION_EXISTS = 0|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：ConnectErrorCode；<br>API声明：PEER_APP_REJECTED = 1<br>差异内容：PEER_APP_REJECTED = 1|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：ConnectErrorCode；<br>API声明：LOCAL_WIFI_NOT_OPEN = 2<br>差异内容：LOCAL_WIFI_NOT_OPEN = 2|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：ConnectErrorCode；<br>API声明：PEER_WIFI_NOT_OPEN = 3<br>差异内容：PEER_WIFI_NOT_OPEN = 3|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：ConnectErrorCode；<br>API声明：PEER_ABILITY_NO_ONCOLLABORATE = 4<br>差异内容：PEER_ABILITY_NO_ONCOLLABORATE = 4|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：ConnectErrorCode；<br>API声明：SYSTEM_INTERNAL_ERROR = 5<br>差异内容：SYSTEM_INTERNAL_ERROR = 5|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：export enum StartOptionParams<br>差异内容：export enum StartOptionParams|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：StartOptionParams；<br>API声明：START_IN_FOREGROUND = 0<br>差异内容：START_IN_FOREGROUND = 0|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：interface EventCallbackInfo<br>差异内容：interface EventCallbackInfo|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：EventCallbackInfo；<br>API声明：sessionId: number;<br>差异内容：sessionId: number;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：EventCallbackInfo；<br>API声明：reason?: DisconnectReason;<br>差异内容：reason?: DisconnectReason;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：EventCallbackInfo；<br>API声明：msg?: string;<br>差异内容：msg?: string;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：EventCallbackInfo；<br>API声明：data?: ArrayBuffer;<br>差异内容：data?: ArrayBuffer;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：interface CollaborateEventInfo<br>差异内容：interface CollaborateEventInfo|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：CollaborateEventInfo；<br>API声明：eventType: CollaborateEventType;<br>差异内容：eventType: CollaborateEventType;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：CollaborateEventInfo；<br>API声明：eventMsg?: string;<br>差异内容：eventMsg?: string;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：enum CollaborateEventType<br>差异内容：enum CollaborateEventType|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：CollaborateEventType；<br>API声明：SEND_FAILURE = 0<br>差异内容：SEND_FAILURE = 0|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：CollaborateEventType；<br>API声明：COLOR_SPACE_CONVERSION_FAILURE = 1<br>差异内容：COLOR_SPACE_CONVERSION_FAILURE = 1|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：enum DisconnectReason<br>差异内容：enum DisconnectReason|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：DisconnectReason；<br>API声明：PEER_APP_CLOSE_COLLABORATION = 0<br>差异内容：PEER_APP_CLOSE_COLLABORATION = 0|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：DisconnectReason；<br>API声明：PEER_APP_EXIT = 1<br>差异内容：PEER_APP_EXIT = 1|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：DisconnectReason；<br>API声明：NETWORK_DISCONNECTED = 2<br>差异内容：NETWORK_DISCONNECTED = 2|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：function on(type: 'connect', sessionId: number, callback: Callback\<EventCallbackInfo>): void;<br>差异内容：function on(type: 'connect', sessionId: number, callback: Callback\<EventCallbackInfo>): void;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：function off(type: 'connect', sessionId: number, callback?: Callback\<EventCallbackInfo>): void;<br>差异内容：function off(type: 'connect', sessionId: number, callback?: Callback\<EventCallbackInfo>): void;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：function on(type: 'disconnect', sessionId: number, callback: Callback\<EventCallbackInfo>): void;<br>差异内容：function on(type: 'disconnect', sessionId: number, callback: Callback\<EventCallbackInfo>): void;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：function off(type: 'disconnect', sessionId: number, callback?: Callback\<EventCallbackInfo>): void;<br>差异内容：function off(type: 'disconnect', sessionId: number, callback?: Callback\<EventCallbackInfo>): void;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：function on(type: 'receiveMessage', sessionId: number, callback: Callback\<EventCallbackInfo>): void;<br>差异内容：function on(type: 'receiveMessage', sessionId: number, callback: Callback\<EventCallbackInfo>): void;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：function off(type: 'receiveMessage', sessionId: number, callback?: Callback\<EventCallbackInfo>): void;<br>差异内容：function off(type: 'receiveMessage', sessionId: number, callback?: Callback\<EventCallbackInfo>): void;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：function on(type: 'receiveData', sessionId: number, callback: Callback\<EventCallbackInfo>): void;<br>差异内容：function on(type: 'receiveData', sessionId: number, callback: Callback\<EventCallbackInfo>): void;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：function off(type: 'receiveData', sessionId: number, callback?: Callback\<EventCallbackInfo>): void;<br>差异内容：function off(type: 'receiveData', sessionId: number, callback?: Callback\<EventCallbackInfo>): void;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：function createAbilityConnectionSession(serviceName: string, context: Context, peerInfo: PeerInfo, connectOptions: ConnectOptions): number;<br>差异内容：function createAbilityConnectionSession(serviceName: string, context: Context, peerInfo: PeerInfo, connectOptions: ConnectOptions): number;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：function destroyAbilityConnectionSession(sessionId: number): void;<br>差异内容：function destroyAbilityConnectionSession(sessionId: number): void;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：function getPeerInfoById(sessionId: number): PeerInfo \| undefined;<br>差异内容：function getPeerInfoById(sessionId: number): PeerInfo \| undefined;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：function connect(sessionId: number): Promise\<ConnectResult>;<br>差异内容：function connect(sessionId: number): Promise\<ConnectResult>;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：function disconnect(sessionId: number): void;<br>差异内容：function disconnect(sessionId: number): void;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：function acceptConnect(sessionId: number, token: string): Promise\<void>;<br>差异内容：function acceptConnect(sessionId: number, token: string): Promise\<void>;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：function reject(token: string, reason: string): void;<br>差异内容：function reject(token: string, reason: string): void;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：function sendMessage(sessionId: number, msg: string): Promise\<void>;<br>差异内容：function sendMessage(sessionId: number, msg: string): Promise\<void>;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：function sendData(sessionId: number, data: ArrayBuffer): Promise\<void>;<br>差异内容：function sendData(sessionId: number, data: ArrayBuffer): Promise\<void>;|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：export enum CollaborationKeys<br>差异内容：export enum CollaborationKeys|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：CollaborationKeys；<br>API声明：PEER_INFO = 'ohos.collaboration.key.peerInfo'<br>差异内容：PEER_INFO = 'ohos.collaboration.key.peerInfo'|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：CollaborationKeys；<br>API声明：CONNECT_OPTIONS = 'ohos.collaboration.key.connectOptions'<br>差异内容：CONNECT_OPTIONS = 'ohos.collaboration.key.connectOptions'|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：CollaborationKeys；<br>API声明：COLLABORATE_TYPE = 'ohos.collaboration.key.abilityCollaborateType'<br>差异内容：COLLABORATE_TYPE = 'ohos.collaboration.key.abilityCollaborateType'|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：abilityConnectionManager；<br>API声明：export enum CollaborationValues<br>差异内容：export enum CollaborationValues|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：CollaborationValues；<br>API声明：ABILITY_COLLABORATION_TYPE_DEFAULT = 'ohos.collaboration.value.abilityCollab'<br>差异内容：ABILITY_COLLABORATION_TYPE_DEFAULT = 'ohos.collaboration.value.abilityCollab'|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：CollaborationValues；<br>API声明：ABILITY_COLLABORATION_TYPE_CONNECT_PROXY = 'ohos.collaboration.value.connectProxy'<br>差异内容：ABILITY_COLLABORATION_TYPE_CONNECT_PROXY = 'ohos.collaboration.value.connectProxy'|NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除API|类名：global；<br>API声明：declare namespace linkEnhance<br>差异内容：declare namespace linkEnhance|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：linkEnhance；<br>API声明：interface ConnectResult<br>差异内容：interface ConnectResult|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：ConnectResult；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：ConnectResult；<br>API声明：success: boolean;<br>差异内容：success: boolean;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：ConnectResult；<br>API声明：reason: number;<br>差异内容：reason: number;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：linkEnhance；<br>API声明：interface Server<br>差异内容：interface Server|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：Server；<br>API声明：start(): void;<br>差异内容：start(): void;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：Server；<br>API声明：stop(): void;<br>差异内容：stop(): void;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：Server；<br>API声明：close(): void;<br>差异内容：close(): void;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：Server；<br>API声明：on(type: 'connectionAccepted', callback: Callback\<Connection>): void;<br>差异内容：on(type: 'connectionAccepted', callback: Callback\<Connection>): void;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：Server；<br>API声明：off(type: 'connectionAccepted', callback?: Callback\<Connection>): void;<br>差异内容：off(type: 'connectionAccepted', callback?: Callback\<Connection>): void;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：Server；<br>API声明：on(type: 'serverStopped', callback: Callback\<number>): void;<br>差异内容：on(type: 'serverStopped', callback: Callback\<number>): void;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：Server；<br>API声明：off(type: 'serverStopped', callback?: Callback\<number>): void;<br>差异内容：off(type: 'serverStopped', callback?: Callback\<number>): void;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：linkEnhance；<br>API声明：function createServer(name: string): Server;<br>差异内容：function createServer(name: string): Server;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：linkEnhance；<br>API声明：interface Connection<br>差异内容：interface Connection|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：Connection；<br>API声明：connect(): void;<br>差异内容：connect(): void;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：Connection；<br>API声明：disconnect(): void;<br>差异内容：disconnect(): void;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：Connection；<br>API声明：close(): void;<br>差异内容：close(): void;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：Connection；<br>API声明：getPeerDeviceId(): string;<br>差异内容：getPeerDeviceId(): string;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：Connection；<br>API声明：sendData(data: ArrayBuffer): void;<br>差异内容：sendData(data: ArrayBuffer): void;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：Connection；<br>API声明：on(type: 'connectResult', callback: Callback\<ConnectResult>): void;<br>差异内容：on(type: 'connectResult', callback: Callback\<ConnectResult>): void;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：Connection；<br>API声明：off(type: 'connectResult', callback?: Callback\<ConnectResult>): void;<br>差异内容：off(type: 'connectResult', callback?: Callback\<ConnectResult>): void;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：Connection；<br>API声明：on(type: 'disconnected', callback: Callback\<number>): void;<br>差异内容：on(type: 'disconnected', callback: Callback\<number>): void;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：Connection；<br>API声明：off(type: 'disconnected', callback?: Callback\<number>): void;<br>差异内容：off(type: 'disconnected', callback?: Callback\<number>): void;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：Connection；<br>API声明：on(type: 'dataReceived', callback: Callback\<ArrayBuffer>): void;<br>差异内容：on(type: 'dataReceived', callback: Callback\<ArrayBuffer>): void;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：Connection；<br>API声明：off(type: 'dataReceived', callback?: Callback\<ArrayBuffer>): void;<br>差异内容：off(type: 'dataReceived', callback?: Callback\<ArrayBuffer>): void;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：linkEnhance；<br>API声明：function createConnection(deviceId: string, name: string): Connection;<br>差异内容：function createConnection(deviceId: string, name: string): Connection;|NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除API|类名：global；<br>API声明：declare namespace proxyChannelManager<br>差异内容：declare namespace proxyChannelManager|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：proxyChannelManager；<br>API声明：function openProxyChannel(channelInfo: ChannelInfo): Promise\<number>;<br>差异内容：function openProxyChannel(channelInfo: ChannelInfo): Promise\<number>;|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：proxyChannelManager；<br>API声明：function closeProxyChannel(channelId: number): void;<br>差异内容：function closeProxyChannel(channelId: number): void;|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：proxyChannelManager；<br>API声明：function sendData(channelId: number, data: ArrayBuffer): Promise\<void>;<br>差异内容：function sendData(channelId: number, data: ArrayBuffer): Promise\<void>;|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：proxyChannelManager；<br>API声明：function on(type: 'receiveData', channelId: number, callback: Callback\<DataInfo>): void;<br>差异内容：function on(type: 'receiveData', channelId: number, callback: Callback\<DataInfo>): void;|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：proxyChannelManager；<br>API声明：function off(type: 'receiveData', channelId: number, callback?: Callback\<DataInfo>): void;<br>差异内容：function off(type: 'receiveData', channelId: number, callback?: Callback\<DataInfo>): void;|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：proxyChannelManager；<br>API声明：function on(type: 'channelStateChange', channelId: number, callback: Callback\<ChannelStateInfo>): void;<br>差异内容：function on(type: 'channelStateChange', channelId: number, callback: Callback\<ChannelStateInfo>): void;|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：proxyChannelManager；<br>API声明：function off(type: 'channelStateChange', channelId: number, callback?: Callback\<ChannelStateInfo>): void;<br>差异内容：function off(type: 'channelStateChange', channelId: number, callback?: Callback\<ChannelStateInfo>): void;|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：proxyChannelManager；<br>API声明：interface DataInfo<br>差异内容：interface DataInfo|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：DataInfo；<br>API声明：channelId: number;<br>差异内容：channelId: number;|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：DataInfo；<br>API声明：data: ArrayBuffer;<br>差异内容：data: ArrayBuffer;|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：proxyChannelManager；<br>API声明：enum LinkType<br>差异内容：enum LinkType|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：LinkType；<br>API声明：LINK_BR = 0<br>差异内容：LINK_BR = 0|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：proxyChannelManager；<br>API声明：interface ChannelInfo<br>差异内容：interface ChannelInfo|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：ChannelInfo；<br>API声明：linkType: LinkType;<br>差异内容：linkType: LinkType;|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：ChannelInfo；<br>API声明：peerDevAddr: string;<br>差异内容：peerDevAddr: string;|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：ChannelInfo；<br>API声明：peerUuid: string;<br>差异内容：peerUuid: string;|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：proxyChannelManager；<br>API声明：enum ChannelState<br>差异内容：enum ChannelState|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：ChannelState；<br>API声明：CHANNEL_WAIT_RESUME = 0<br>差异内容：CHANNEL_WAIT_RESUME = 0|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：ChannelState；<br>API声明：CHANNEL_RESUME = 1<br>差异内容：CHANNEL_RESUME = 1|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：ChannelState；<br>API声明：CHANNEL_EXCEPTION_SOFTWARE_FAILED = 2<br>差异内容：CHANNEL_EXCEPTION_SOFTWARE_FAILED = 2|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：ChannelState；<br>API声明：CHANNEL_BR_NO_PAIRED = 3<br>差异内容：CHANNEL_BR_NO_PAIRED = 3|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：proxyChannelManager；<br>API声明：interface ChannelStateInfo<br>差异内容：interface ChannelStateInfo|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：ChannelStateInfo；<br>API声明：channelId: number;<br>差异内容：channelId: number;|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除API|类名：ChannelStateInfo；<br>API声明：state: ChannelState;<br>差异内容：state: ChannelState;|NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除kit|类名：global；<br>API声明：api\@ohos.application.DistributedExtensionAbility.d.ts<br>差异内容：DistributedServiceKit|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.application.DistributedExtensionAbility.d.ts|
|删除kit|类名：global；<br>API声明：api\@ohos.application.DistributedExtensionContext.d.ts<br>差异内容：DistributedServiceKit|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.application.DistributedExtensionContext.d.ts|
|删除kit|类名：global；<br>API声明：api\@ohos.distributedsched.abilityConnectionManager.d.ts<br>差异内容：DistributedServiceKit|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|删除kit|类名：global；<br>API声明：api\@ohos.distributedsched.linkEnhance.d.ts<br>差异内容：DistributedServiceKit|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.distributedsched.linkEnhance.d.ts|
|删除kit|类名：global；<br>API声明：api\@ohos.distributedsched.proxyChannelManager.d.ts<br>差异内容：DistributedServiceKit|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.distributedsched.proxyChannelManager.d.ts|
|删除导出符号|类名：global；<br>API声明：export default class DistributedExtensionAbility<br>差异内容：export default class DistributedExtensionAbility|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.application.DistributedExtensionAbility.d.ts|
|删除导出符号|类名：global；<br>API声明：export default class DistributedExtensionContext<br>差异内容：export default class DistributedExtensionContext|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.application.DistributedExtensionContext.d.ts|
