| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|删除错误码|类名：distributedDeviceManager；<br>API声明：function releaseDeviceManager(deviceManager: DeviceManager): void;<br>差异内容：201|类名：distributedDeviceManager；<br>API声明：function releaseDeviceManager(deviceManager: DeviceManager): void;<br>差异内容：NA|api/@ohos.distributedDeviceManager.d.ts|
|删除错误码|类名：DeviceManager；<br>API声明：getAvailableDeviceListSync(): Array\<DeviceBasicInfo>;<br>差异内容：401|类名：DeviceManager；<br>API声明：getAvailableDeviceListSync(): Array\<DeviceBasicInfo>;<br>差异内容：NA|api/@ohos.distributedDeviceManager.d.ts|
|删除错误码|类名：DeviceManager；<br>API声明：stopDiscovering(): void;<br>差异内容：11600104,401|类名：DeviceManager；<br>API声明：stopDiscovering(): void;<br>差异内容：NA|api/@ohos.distributedDeviceManager.d.ts|
|权限变更|类名：distributedDeviceManager；<br>API声明：function releaseDeviceManager(deviceManager: DeviceManager): void;<br>差异内容：ohos.permission.DISTRIBUTED_DATASYNC|类名：distributedDeviceManager；<br>API声明：function releaseDeviceManager(deviceManager: DeviceManager): void;<br>差异内容：NA|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace abilityConnectionManager<br>差异内容：declare namespace abilityConnectionManager|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：interface PeerInfo<br>差异内容：interface PeerInfo|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：PeerInfo；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：PeerInfo；<br>API声明：bundleName: string;<br>差异内容：bundleName: string;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：PeerInfo；<br>API声明：moduleName: string;<br>差异内容：moduleName: string;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：PeerInfo；<br>API声明：abilityName: string;<br>差异内容：abilityName: string;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：PeerInfo；<br>API声明：serviceName?: string;<br>差异内容：serviceName?: string;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：interface ConnectOptions<br>差异内容：interface ConnectOptions|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：ConnectOptions；<br>API声明：needSendData?: boolean;<br>差异内容：needSendData?: boolean;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：ConnectOptions；<br>API声明：startOptions?: StartOptionParams;<br>差异内容：startOptions?: StartOptionParams;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：ConnectOptions；<br>API声明：parameters?: Record\<string, string>;<br>差异内容：parameters?: Record\<string, string>;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：interface ConnectResult<br>差异内容：interface ConnectResult|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：ConnectResult；<br>API声明：isConnected: boolean;<br>差异内容：isConnected: boolean;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：ConnectResult；<br>API声明：errorCode?: ConnectErrorCode;<br>差异内容：errorCode?: ConnectErrorCode;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：ConnectResult；<br>API声明：reason?: string;<br>差异内容：reason?: string;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：export enum ConnectErrorCode<br>差异内容：export enum ConnectErrorCode|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：ConnectErrorCode；<br>API声明：CONNECTED_SESSION_EXISTS = 0<br>差异内容：CONNECTED_SESSION_EXISTS = 0|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：ConnectErrorCode；<br>API声明：PEER_APP_REJECTED = 1<br>差异内容：PEER_APP_REJECTED = 1|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：ConnectErrorCode；<br>API声明：LOCAL_WIFI_NOT_OPEN = 2<br>差异内容：LOCAL_WIFI_NOT_OPEN = 2|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：ConnectErrorCode；<br>API声明：PEER_WIFI_NOT_OPEN = 3<br>差异内容：PEER_WIFI_NOT_OPEN = 3|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：ConnectErrorCode；<br>API声明：PEER_ABILITY_NO_ONCOLLABORATE = 4<br>差异内容：PEER_ABILITY_NO_ONCOLLABORATE = 4|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：ConnectErrorCode；<br>API声明：SYSTEM_INTERNAL_ERROR = 5<br>差异内容：SYSTEM_INTERNAL_ERROR = 5|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：export enum StartOptionParams<br>差异内容：export enum StartOptionParams|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：StartOptionParams；<br>API声明：START_IN_FOREGROUND = 0<br>差异内容：START_IN_FOREGROUND = 0|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：interface EventCallbackInfo<br>差异内容：interface EventCallbackInfo|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：EventCallbackInfo；<br>API声明：sessionId: number;<br>差异内容：sessionId: number;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：EventCallbackInfo；<br>API声明：reason?: DisconnectReason;<br>差异内容：reason?: DisconnectReason;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：EventCallbackInfo；<br>API声明：msg?: string;<br>差异内容：msg?: string;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：EventCallbackInfo；<br>API声明：data?: ArrayBuffer;<br>差异内容：data?: ArrayBuffer;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：interface CollaborateEventInfo<br>差异内容：interface CollaborateEventInfo|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：CollaborateEventInfo；<br>API声明：eventType: CollaborateEventType;<br>差异内容：eventType: CollaborateEventType;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：CollaborateEventInfo；<br>API声明：eventMsg?: string;<br>差异内容：eventMsg?: string;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：enum CollaborateEventType<br>差异内容：enum CollaborateEventType|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：CollaborateEventType；<br>API声明：SEND_FAILURE = 0<br>差异内容：SEND_FAILURE = 0|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：CollaborateEventType；<br>API声明：COLOR_SPACE_CONVERSION_FAILURE = 1<br>差异内容：COLOR_SPACE_CONVERSION_FAILURE = 1|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：enum DisconnectReason<br>差异内容：enum DisconnectReason|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：DisconnectReason；<br>API声明：PEER_APP_CLOSE_COLLABORATION = 0<br>差异内容：PEER_APP_CLOSE_COLLABORATION = 0|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：DisconnectReason；<br>API声明：PEER_APP_EXIT = 1<br>差异内容：PEER_APP_EXIT = 1|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：DisconnectReason；<br>API声明：NETWORK_DISCONNECTED = 2<br>差异内容：NETWORK_DISCONNECTED = 2|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：function on(type: 'connect', sessionId: number, callback: Callback\<EventCallbackInfo>): void;<br>差异内容：function on(type: 'connect', sessionId: number, callback: Callback\<EventCallbackInfo>): void;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：function off(type: 'connect', sessionId: number, callback?: Callback\<EventCallbackInfo>): void;<br>差异内容：function off(type: 'connect', sessionId: number, callback?: Callback\<EventCallbackInfo>): void;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：function on(type: 'disconnect', sessionId: number, callback: Callback\<EventCallbackInfo>): void;<br>差异内容：function on(type: 'disconnect', sessionId: number, callback: Callback\<EventCallbackInfo>): void;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：function off(type: 'disconnect', sessionId: number, callback?: Callback\<EventCallbackInfo>): void;<br>差异内容：function off(type: 'disconnect', sessionId: number, callback?: Callback\<EventCallbackInfo>): void;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：function on(type: 'receiveMessage', sessionId: number, callback: Callback\<EventCallbackInfo>): void;<br>差异内容：function on(type: 'receiveMessage', sessionId: number, callback: Callback\<EventCallbackInfo>): void;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：function off(type: 'receiveMessage', sessionId: number, callback?: Callback\<EventCallbackInfo>): void;<br>差异内容：function off(type: 'receiveMessage', sessionId: number, callback?: Callback\<EventCallbackInfo>): void;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：function on(type: 'receiveData', sessionId: number, callback: Callback\<EventCallbackInfo>): void;<br>差异内容：function on(type: 'receiveData', sessionId: number, callback: Callback\<EventCallbackInfo>): void;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：function off(type: 'receiveData', sessionId: number, callback?: Callback\<EventCallbackInfo>): void;<br>差异内容：function off(type: 'receiveData', sessionId: number, callback?: Callback\<EventCallbackInfo>): void;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：function createAbilityConnectionSession(serviceName: string, context: Context, peerInfo: PeerInfo, connectOptions: ConnectOptions): number;<br>差异内容：function createAbilityConnectionSession(serviceName: string, context: Context, peerInfo: PeerInfo, connectOptions: ConnectOptions): number;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：function destroyAbilityConnectionSession(sessionId: number): void;<br>差异内容：function destroyAbilityConnectionSession(sessionId: number): void;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：function getPeerInfoById(sessionId: number): PeerInfo \| undefined;<br>差异内容：function getPeerInfoById(sessionId: number): PeerInfo \| undefined;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：function connect(sessionId: number): Promise\<ConnectResult>;<br>差异内容：function connect(sessionId: number): Promise\<ConnectResult>;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：function disconnect(sessionId: number): void;<br>差异内容：function disconnect(sessionId: number): void;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：function acceptConnect(sessionId: number, token: string): Promise\<void>;<br>差异内容：function acceptConnect(sessionId: number, token: string): Promise\<void>;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：function reject(token: string, reason: string): void;<br>差异内容：function reject(token: string, reason: string): void;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：function sendMessage(sessionId: number, msg: string): Promise\<void>;<br>差异内容：function sendMessage(sessionId: number, msg: string): Promise\<void>;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：function sendData(sessionId: number, data: ArrayBuffer): Promise\<void>;<br>差异内容：function sendData(sessionId: number, data: ArrayBuffer): Promise\<void>;|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：export enum CollaborationKeys<br>差异内容：export enum CollaborationKeys|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：CollaborationKeys；<br>API声明：PEER_INFO = 'ohos.collaboration.key.peerInfo'<br>差异内容：PEER_INFO = 'ohos.collaboration.key.peerInfo'|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：CollaborationKeys；<br>API声明：CONNECT_OPTIONS = 'ohos.collaboration.key.connectOptions'<br>差异内容：CONNECT_OPTIONS = 'ohos.collaboration.key.connectOptions'|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：CollaborationKeys；<br>API声明：COLLABORATE_TYPE = 'ohos.collaboration.key.abilityCollaborateType'<br>差异内容：COLLABORATE_TYPE = 'ohos.collaboration.key.abilityCollaborateType'|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：abilityConnectionManager；<br>API声明：export enum CollaborationValues<br>差异内容：export enum CollaborationValues|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：CollaborationValues；<br>API声明：ABILITY_COLLABORATION_TYPE_DEFAULT = 'ohos.collaboration.value.abilityCollab'<br>差异内容：ABILITY_COLLABORATION_TYPE_DEFAULT = 'ohos.collaboration.value.abilityCollab'|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增API|NA|类名：CollaborationValues；<br>API声明：ABILITY_COLLABORATION_TYPE_CONNECT_PROXY = 'ohos.collaboration.value.connectProxy'<br>差异内容：ABILITY_COLLABORATION_TYPE_CONNECT_PROXY = 'ohos.collaboration.value.connectProxy'|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.distributedsched.abilityConnectionManager.d.ts<br>差异内容：DistributedServiceKit|api/@ohos.distributedsched.abilityConnectionManager.d.ts|
