| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace call<br>差异内容：declare namespace call|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function dial(phoneNumber: string, options: DialOptions, callback: AsyncCallback\<boolean>): void;<br>差异内容：function dial(phoneNumber: string, options: DialOptions, callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function dial(phoneNumber: string, options?: DialOptions): Promise\<boolean>;<br>差异内容：function dial(phoneNumber: string, options?: DialOptions): Promise\<boolean>;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function dial(phoneNumber: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：function dial(phoneNumber: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function makeCall(phoneNumber: string, callback: AsyncCallback\<void>): void;<br>差异内容：function makeCall(phoneNumber: string, callback: AsyncCallback\<void>): void;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function makeCall(phoneNumber: string): Promise\<void>;<br>差异内容：function makeCall(phoneNumber: string): Promise\<void>;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function hasCall(callback: AsyncCallback\<boolean>): void;<br>差异内容：function hasCall(callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function hasCall(): Promise\<boolean>;<br>差异内容：function hasCall(): Promise\<boolean>;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function hasCallSync(): boolean;<br>差异内容：function hasCallSync(): boolean;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function getCallState(callback: AsyncCallback\<CallState>): void;<br>差异内容：function getCallState(callback: AsyncCallback\<CallState>): void;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function getCallState(): Promise\<CallState>;<br>差异内容：function getCallState(): Promise\<CallState>;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function getCallStateSync(): CallState;<br>差异内容：function getCallStateSync(): CallState;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function hasVoiceCapability(): boolean;<br>差异内容：function hasVoiceCapability(): boolean;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function isEmergencyPhoneNumber(phoneNumber: string, options: EmergencyNumberOptions, callback: AsyncCallback\<boolean>): void;<br>差异内容：function isEmergencyPhoneNumber(phoneNumber: string, options: EmergencyNumberOptions, callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function isEmergencyPhoneNumber(phoneNumber: string, options?: EmergencyNumberOptions): Promise\<boolean>;<br>差异内容：function isEmergencyPhoneNumber(phoneNumber: string, options?: EmergencyNumberOptions): Promise\<boolean>;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function isEmergencyPhoneNumber(phoneNumber: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：function isEmergencyPhoneNumber(phoneNumber: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function formatPhoneNumber(phoneNumber: string, options: NumberFormatOptions, callback: AsyncCallback\<string>): void;<br>差异内容：function formatPhoneNumber(phoneNumber: string, options: NumberFormatOptions, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function formatPhoneNumber(phoneNumber: string, options?: NumberFormatOptions): Promise\<string>;<br>差异内容：function formatPhoneNumber(phoneNumber: string, options?: NumberFormatOptions): Promise\<string>;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function formatPhoneNumber(phoneNumber: string, callback: AsyncCallback\<string>): void;<br>差异内容：function formatPhoneNumber(phoneNumber: string, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function formatPhoneNumberToE164(phoneNumber: string, countryCode: string, callback: AsyncCallback\<string>): void;<br>差异内容：function formatPhoneNumberToE164(phoneNumber: string, countryCode: string, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：function formatPhoneNumberToE164(phoneNumber: string, countryCode: string): Promise\<string>;<br>差异内容：function formatPhoneNumberToE164(phoneNumber: string, countryCode: string): Promise\<string>;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：export enum CallState<br>差异内容：export enum CallState|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：CallState；<br>API声明：CALL_STATE_UNKNOWN = -1<br>差异内容：CALL_STATE_UNKNOWN = -1|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：CallState；<br>API声明：CALL_STATE_IDLE = 0<br>差异内容：CALL_STATE_IDLE = 0|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：CallState；<br>API声明：CALL_STATE_RINGING = 1<br>差异内容：CALL_STATE_RINGING = 1|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：CallState；<br>API声明：CALL_STATE_OFFHOOK = 2<br>差异内容：CALL_STATE_OFFHOOK = 2|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：CallState；<br>API声明：CALL_STATE_ANSWERED = 3<br>差异内容：CALL_STATE_ANSWERED = 3|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：export interface DialOptions<br>差异内容：export interface DialOptions|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：DialOptions；<br>API声明：extras?: boolean;<br>差异内容：extras?: boolean;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：export interface EmergencyNumberOptions<br>差异内容：export interface EmergencyNumberOptions|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：EmergencyNumberOptions；<br>API声明：slotId?: number;<br>差异内容：slotId?: number;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：call；<br>API声明：export interface NumberFormatOptions<br>差异内容：export interface NumberFormatOptions|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：NumberFormatOptions；<br>API声明：countryCode?: string;<br>差异内容：countryCode?: string;|api/@ohos.telephony.call.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace data<br>差异内容：declare namespace data|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：data；<br>API声明：function getDefaultCellularDataSlotId(callback: AsyncCallback\<number>): void;<br>差异内容：function getDefaultCellularDataSlotId(callback: AsyncCallback\<number>): void;|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：data；<br>API声明：function getDefaultCellularDataSlotId(): Promise\<number>;<br>差异内容：function getDefaultCellularDataSlotId(): Promise\<number>;|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：data；<br>API声明：function getDefaultCellularDataSlotIdSync(): number;<br>差异内容：function getDefaultCellularDataSlotIdSync(): number;|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：data；<br>API声明：function getCellularDataFlowType(callback: AsyncCallback\<DataFlowType>): void;<br>差异内容：function getCellularDataFlowType(callback: AsyncCallback\<DataFlowType>): void;|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：data；<br>API声明：function getCellularDataFlowType(): Promise\<DataFlowType>;<br>差异内容：function getCellularDataFlowType(): Promise\<DataFlowType>;|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：data；<br>API声明：function getCellularDataState(callback: AsyncCallback\<DataConnectState>): void;<br>差异内容：function getCellularDataState(callback: AsyncCallback\<DataConnectState>): void;|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：data；<br>API声明：function getCellularDataState(): Promise\<DataConnectState>;<br>差异内容：function getCellularDataState(): Promise\<DataConnectState>;|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：data；<br>API声明：function isCellularDataEnabled(callback: AsyncCallback\<boolean>): void;<br>差异内容：function isCellularDataEnabled(callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：data；<br>API声明：function isCellularDataEnabled(): Promise\<boolean>;<br>差异内容：function isCellularDataEnabled(): Promise\<boolean>;|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：data；<br>API声明：function isCellularDataRoamingEnabled(slotId: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：function isCellularDataRoamingEnabled(slotId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：data；<br>API声明：function isCellularDataRoamingEnabled(slotId: number): Promise\<boolean>;<br>差异内容：function isCellularDataRoamingEnabled(slotId: number): Promise\<boolean>;|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：data；<br>API声明：function getDefaultCellularDataSimId(): number;<br>差异内容：function getDefaultCellularDataSimId(): number;|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：data；<br>API声明：export enum DataFlowType<br>差异内容：export enum DataFlowType|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：DataFlowType；<br>API声明：DATA_FLOW_TYPE_NONE = 0<br>差异内容：DATA_FLOW_TYPE_NONE = 0|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：DataFlowType；<br>API声明：DATA_FLOW_TYPE_DOWN = 1<br>差异内容：DATA_FLOW_TYPE_DOWN = 1|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：DataFlowType；<br>API声明：DATA_FLOW_TYPE_UP = 2<br>差异内容：DATA_FLOW_TYPE_UP = 2|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：DataFlowType；<br>API声明：DATA_FLOW_TYPE_UP_DOWN = 3<br>差异内容：DATA_FLOW_TYPE_UP_DOWN = 3|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：DataFlowType；<br>API声明：DATA_FLOW_TYPE_DORMANT = 4<br>差异内容：DATA_FLOW_TYPE_DORMANT = 4|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：data；<br>API声明：export enum DataConnectState<br>差异内容：export enum DataConnectState|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：DataConnectState；<br>API声明：DATA_STATE_UNKNOWN = -1<br>差异内容：DATA_STATE_UNKNOWN = -1|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：DataConnectState；<br>API声明：DATA_STATE_DISCONNECTED = 0<br>差异内容：DATA_STATE_DISCONNECTED = 0|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：DataConnectState；<br>API声明：DATA_STATE_CONNECTING = 1<br>差异内容：DATA_STATE_CONNECTING = 1|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：DataConnectState；<br>API声明：DATA_STATE_CONNECTED = 2<br>差异内容：DATA_STATE_CONNECTED = 2|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：DataConnectState；<br>API声明：DATA_STATE_SUSPENDED = 3<br>差异内容：DATA_STATE_SUSPENDED = 3|api/@ohos.telephony.data.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace observer<br>差异内容：declare namespace observer|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：type NetworkState = radio.NetworkState;<br>差异内容：type NetworkState = radio.NetworkState;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：type SignalInformation = radio.SignalInformation;<br>差异内容：type SignalInformation = radio.SignalInformation;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：type DataConnectState = data.DataConnectState;<br>差异内容：type DataConnectState = data.DataConnectState;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：type RatType = radio.RadioTechnology;<br>差异内容：type RatType = radio.RadioTechnology;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：type DataFlowType = data.DataFlowType;<br>差异内容：type DataFlowType = data.DataFlowType;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：type CallState = call.CallState;<br>差异内容：type CallState = call.CallState;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：type CardType = sim.CardType;<br>差异内容：type CardType = sim.CardType;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：type SimState = sim.SimState;<br>差异内容：type SimState = sim.SimState;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function on(type: 'networkStateChange', callback: Callback\<NetworkState>): void;<br>差异内容：function on(type: 'networkStateChange', callback: Callback\<NetworkState>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function on(type: 'networkStateChange', options: ObserverOptions, callback: Callback\<NetworkState>): void;<br>差异内容：function on(type: 'networkStateChange', options: ObserverOptions, callback: Callback\<NetworkState>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function off(type: 'networkStateChange', callback?: Callback\<NetworkState>): void;<br>差异内容：function off(type: 'networkStateChange', callback?: Callback\<NetworkState>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function on(type: 'signalInfoChange', callback: Callback\<Array\<SignalInformation>>): void;<br>差异内容：function on(type: 'signalInfoChange', callback: Callback\<Array\<SignalInformation>>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function on(type: 'signalInfoChange', options: ObserverOptions, callback: Callback\<Array\<SignalInformation>>): void;<br>差异内容：function on(type: 'signalInfoChange', options: ObserverOptions, callback: Callback\<Array\<SignalInformation>>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function off(type: 'signalInfoChange', callback?: Callback\<Array\<SignalInformation>>): void;<br>差异内容：function off(type: 'signalInfoChange', callback?: Callback\<Array\<SignalInformation>>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function on(type: 'cellularDataConnectionStateChange', callback: Callback\<DataConnectionStateInfo>): void;<br>差异内容：function on(type: 'cellularDataConnectionStateChange', callback: Callback\<DataConnectionStateInfo>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function on(type: 'cellularDataConnectionStateChange', options: ObserverOptions, callback: Callback\<DataConnectionStateInfo>): void;<br>差异内容：function on(type: 'cellularDataConnectionStateChange', options: ObserverOptions, callback: Callback\<DataConnectionStateInfo>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function off(type: 'cellularDataConnectionStateChange', callback?: Callback\<DataConnectionStateInfo>): void;<br>差异内容：function off(type: 'cellularDataConnectionStateChange', callback?: Callback\<DataConnectionStateInfo>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function on(type: 'cellularDataFlowChange', callback: Callback\<DataFlowType>): void;<br>差异内容：function on(type: 'cellularDataFlowChange', callback: Callback\<DataFlowType>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function on(type: 'cellularDataFlowChange', options: ObserverOptions, callback: Callback\<DataFlowType>): void;<br>差异内容：function on(type: 'cellularDataFlowChange', options: ObserverOptions, callback: Callback\<DataFlowType>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function off(type: 'cellularDataFlowChange', callback?: Callback\<DataFlowType>): void;<br>差异内容：function off(type: 'cellularDataFlowChange', callback?: Callback\<DataFlowType>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function on(type: 'callStateChange', callback: Callback\<CallStateInfo>): void;<br>差异内容：function on(type: 'callStateChange', callback: Callback\<CallStateInfo>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function on(type: 'callStateChange', options: ObserverOptions, callback: Callback\<CallStateInfo>): void;<br>差异内容：function on(type: 'callStateChange', options: ObserverOptions, callback: Callback\<CallStateInfo>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function off(type: 'callStateChange', callback?: Callback\<CallStateInfo>): void;<br>差异内容：function off(type: 'callStateChange', callback?: Callback\<CallStateInfo>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function on(type: 'simStateChange', callback: Callback\<SimStateData>): void;<br>差异内容：function on(type: 'simStateChange', callback: Callback\<SimStateData>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function on(type: 'simStateChange', options: ObserverOptions, callback: Callback\<SimStateData>): void;<br>差异内容：function on(type: 'simStateChange', options: ObserverOptions, callback: Callback\<SimStateData>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function off(type: 'simStateChange', callback?: Callback\<SimStateData>): void;<br>差异内容：function off(type: 'simStateChange', callback?: Callback\<SimStateData>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function on(type: 'iccAccountInfoChange', callback: Callback\<void>): void;<br>差异内容：function on(type: 'iccAccountInfoChange', callback: Callback\<void>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：function off(type: 'iccAccountInfoChange', callback?: Callback\<void>): void;<br>差异内容：function off(type: 'iccAccountInfoChange', callback?: Callback\<void>): void;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：export interface SimStateData<br>差异内容：export interface SimStateData|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：SimStateData；<br>API声明：type: CardType;<br>差异内容：type: CardType;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：SimStateData；<br>API声明：state: SimState;<br>差异内容：state: SimState;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：SimStateData；<br>API声明：reason: LockReason;<br>差异内容：reason: LockReason;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：export interface CallStateInfo<br>差异内容：export interface CallStateInfo|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：CallStateInfo；<br>API声明：state: CallState;<br>差异内容：state: CallState;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：CallStateInfo；<br>API声明：number: string;<br>差异内容：number: string;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：export interface DataConnectionStateInfo<br>差异内容：export interface DataConnectionStateInfo|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：DataConnectionStateInfo；<br>API声明：state: DataConnectState;<br>差异内容：state: DataConnectState;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：DataConnectionStateInfo；<br>API声明：network: RatType;<br>差异内容：network: RatType;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：export interface ObserverOptions<br>差异内容：export interface ObserverOptions|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：ObserverOptions；<br>API声明：slotId: number;<br>差异内容：slotId: number;|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：observer；<br>API声明：export enum LockReason<br>差异内容：export enum LockReason|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：LockReason；<br>API声明：SIM_NONE<br>差异内容：SIM_NONE|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：LockReason；<br>API声明：SIM_PIN<br>差异内容：SIM_PIN|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：LockReason；<br>API声明：SIM_PUK<br>差异内容：SIM_PUK|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：LockReason；<br>API声明：SIM_PN_PIN<br>差异内容：SIM_PN_PIN|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：LockReason；<br>API声明：SIM_PN_PUK<br>差异内容：SIM_PN_PUK|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：LockReason；<br>API声明：SIM_PU_PIN<br>差异内容：SIM_PU_PIN|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：LockReason；<br>API声明：SIM_PU_PUK<br>差异内容：SIM_PU_PUK|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：LockReason；<br>API声明：SIM_PP_PIN<br>差异内容：SIM_PP_PIN|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：LockReason；<br>API声明：SIM_PP_PUK<br>差异内容：SIM_PP_PUK|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：LockReason；<br>API声明：SIM_PC_PIN<br>差异内容：SIM_PC_PIN|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：LockReason；<br>API声明：SIM_PC_PUK<br>差异内容：SIM_PC_PUK|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：LockReason；<br>API声明：SIM_SIM_PIN<br>差异内容：SIM_SIM_PIN|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：LockReason；<br>API声明：SIM_SIM_PUK<br>差异内容：SIM_SIM_PUK|api/@ohos.telephony.observer.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace radio<br>差异内容：declare namespace radio|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function getRadioTech(slotId: number, callback: AsyncCallback\<NetworkRadioTech>): void;<br>差异内容：function getRadioTech(slotId: number, callback: AsyncCallback\<NetworkRadioTech>): void;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function getRadioTech(slotId: number): Promise\<NetworkRadioTech>;<br>差异内容：function getRadioTech(slotId: number): Promise\<NetworkRadioTech>;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function getNetworkState(slotId: number, callback: AsyncCallback\<NetworkState>): void;<br>差异内容：function getNetworkState(slotId: number, callback: AsyncCallback\<NetworkState>): void;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function getNetworkState(slotId?: number): Promise\<NetworkState>;<br>差异内容：function getNetworkState(slotId?: number): Promise\<NetworkState>;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function getNetworkState(callback: AsyncCallback\<NetworkState>): void;<br>差异内容：function getNetworkState(callback: AsyncCallback\<NetworkState>): void;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function getNetworkSelectionMode(slotId: number, callback: AsyncCallback\<NetworkSelectionMode>): void;<br>差异内容：function getNetworkSelectionMode(slotId: number, callback: AsyncCallback\<NetworkSelectionMode>): void;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function getNetworkSelectionMode(slotId: number): Promise\<NetworkSelectionMode>;<br>差异内容：function getNetworkSelectionMode(slotId: number): Promise\<NetworkSelectionMode>;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function getISOCountryCodeForNetwork(slotId: number, callback: AsyncCallback\<string>): void;<br>差异内容：function getISOCountryCodeForNetwork(slotId: number, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function getISOCountryCodeForNetwork(slotId: number): Promise\<string>;<br>差异内容：function getISOCountryCodeForNetwork(slotId: number): Promise\<string>;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function getISOCountryCodeForNetworkSync(slotId: number): string;<br>差异内容：function getISOCountryCodeForNetworkSync(slotId: number): string;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function getPrimarySlotId(callback: AsyncCallback\<number>): void;<br>差异内容：function getPrimarySlotId(callback: AsyncCallback\<number>): void;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function getPrimarySlotId(): Promise\<number>;<br>差异内容：function getPrimarySlotId(): Promise\<number>;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function getSignalInformation(slotId: number, callback: AsyncCallback\<Array\<SignalInformation>>): void;<br>差异内容：function getSignalInformation(slotId: number, callback: AsyncCallback\<Array\<SignalInformation>>): void;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function getSignalInformation(slotId: number): Promise\<Array\<SignalInformation>>;<br>差异内容：function getSignalInformation(slotId: number): Promise\<Array\<SignalInformation>>;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function getSignalInformationSync(slotId: number): Array\<SignalInformation>;<br>差异内容：function getSignalInformationSync(slotId: number): Array\<SignalInformation>;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function isNrSupported(): boolean;<br>差异内容：function isNrSupported(): boolean;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function isNrSupported(slotId: number): boolean;<br>差异内容：function isNrSupported(slotId: number): boolean;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function isNRSupported(): boolean;<br>差异内容：function isNRSupported(): boolean;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function isNRSupported(slotId: number): boolean;<br>差异内容：function isNRSupported(slotId: number): boolean;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function isRadioOn(slotId: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：function isRadioOn(slotId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function isRadioOn(slotId?: number): Promise\<boolean>;<br>差异内容：function isRadioOn(slotId?: number): Promise\<boolean>;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function isRadioOn(callback: AsyncCallback\<boolean>): void;<br>差异内容：function isRadioOn(callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function getOperatorName(slotId: number, callback: AsyncCallback\<string>): void;<br>差异内容：function getOperatorName(slotId: number, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function getOperatorName(slotId: number): Promise\<string>;<br>差异内容：function getOperatorName(slotId: number): Promise\<string>;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：function getOperatorNameSync(slotId: number): string;<br>差异内容：function getOperatorNameSync(slotId: number): string;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：export interface NetworkRadioTech<br>差异内容：export interface NetworkRadioTech|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkRadioTech；<br>API声明：psRadioTech: RadioTechnology;<br>差异内容：psRadioTech: RadioTechnology;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkRadioTech；<br>API声明：csRadioTech: RadioTechnology;<br>差异内容：csRadioTech: RadioTechnology;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：export enum RadioTechnology<br>差异内容：export enum RadioTechnology|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：RadioTechnology；<br>API声明：RADIO_TECHNOLOGY_UNKNOWN = 0<br>差异内容：RADIO_TECHNOLOGY_UNKNOWN = 0|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：RadioTechnology；<br>API声明：RADIO_TECHNOLOGY_GSM = 1<br>差异内容：RADIO_TECHNOLOGY_GSM = 1|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：RadioTechnology；<br>API声明：RADIO_TECHNOLOGY_1XRTT = 2<br>差异内容：RADIO_TECHNOLOGY_1XRTT = 2|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：RadioTechnology；<br>API声明：RADIO_TECHNOLOGY_WCDMA = 3<br>差异内容：RADIO_TECHNOLOGY_WCDMA = 3|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：RadioTechnology；<br>API声明：RADIO_TECHNOLOGY_HSPA = 4<br>差异内容：RADIO_TECHNOLOGY_HSPA = 4|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：RadioTechnology；<br>API声明：RADIO_TECHNOLOGY_HSPAP = 5<br>差异内容：RADIO_TECHNOLOGY_HSPAP = 5|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：RadioTechnology；<br>API声明：RADIO_TECHNOLOGY_TD_SCDMA = 6<br>差异内容：RADIO_TECHNOLOGY_TD_SCDMA = 6|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：RadioTechnology；<br>API声明：RADIO_TECHNOLOGY_EVDO = 7<br>差异内容：RADIO_TECHNOLOGY_EVDO = 7|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：RadioTechnology；<br>API声明：RADIO_TECHNOLOGY_EHRPD = 8<br>差异内容：RADIO_TECHNOLOGY_EHRPD = 8|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：RadioTechnology；<br>API声明：RADIO_TECHNOLOGY_LTE = 9<br>差异内容：RADIO_TECHNOLOGY_LTE = 9|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：RadioTechnology；<br>API声明：RADIO_TECHNOLOGY_LTE_CA = 10<br>差异内容：RADIO_TECHNOLOGY_LTE_CA = 10|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：RadioTechnology；<br>API声明：RADIO_TECHNOLOGY_IWLAN = 11<br>差异内容：RADIO_TECHNOLOGY_IWLAN = 11|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：RadioTechnology；<br>API声明：RADIO_TECHNOLOGY_NR = 12<br>差异内容：RADIO_TECHNOLOGY_NR = 12|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：export interface SignalInformation<br>差异内容：export interface SignalInformation|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：SignalInformation；<br>API声明：signalType: NetworkType;<br>差异内容：signalType: NetworkType;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：SignalInformation；<br>API声明：signalLevel: number;<br>差异内容：signalLevel: number;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：SignalInformation；<br>API声明：dBm: number;<br>差异内容：dBm: number;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：export enum NetworkType<br>差异内容：export enum NetworkType|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkType；<br>API声明：NETWORK_TYPE_UNKNOWN<br>差异内容：NETWORK_TYPE_UNKNOWN|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkType；<br>API声明：NETWORK_TYPE_GSM<br>差异内容：NETWORK_TYPE_GSM|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkType；<br>API声明：NETWORK_TYPE_CDMA<br>差异内容：NETWORK_TYPE_CDMA|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkType；<br>API声明：NETWORK_TYPE_WCDMA<br>差异内容：NETWORK_TYPE_WCDMA|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkType；<br>API声明：NETWORK_TYPE_TDSCDMA<br>差异内容：NETWORK_TYPE_TDSCDMA|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkType；<br>API声明：NETWORK_TYPE_LTE<br>差异内容：NETWORK_TYPE_LTE|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkType；<br>API声明：NETWORK_TYPE_NR<br>差异内容：NETWORK_TYPE_NR|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：export interface NetworkState<br>差异内容：export interface NetworkState|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkState；<br>API声明：longOperatorName: string;<br>差异内容：longOperatorName: string;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkState；<br>API声明：shortOperatorName: string;<br>差异内容：shortOperatorName: string;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkState；<br>API声明：plmnNumeric: string;<br>差异内容：plmnNumeric: string;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkState；<br>API声明：isRoaming: boolean;<br>差异内容：isRoaming: boolean;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkState；<br>API声明：regState: RegState;<br>差异内容：regState: RegState;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkState；<br>API声明：cfgTech: RadioTechnology;<br>差异内容：cfgTech: RadioTechnology;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkState；<br>API声明：nsaState: NsaState;<br>差异内容：nsaState: NsaState;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkState；<br>API声明：isCaActive: boolean;<br>差异内容：isCaActive: boolean;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkState；<br>API声明：isEmergency: boolean;<br>差异内容：isEmergency: boolean;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：export enum RegState<br>差异内容：export enum RegState|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：RegState；<br>API声明：REG_STATE_NO_SERVICE = 0<br>差异内容：REG_STATE_NO_SERVICE = 0|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：RegState；<br>API声明：REG_STATE_IN_SERVICE = 1<br>差异内容：REG_STATE_IN_SERVICE = 1|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：RegState；<br>API声明：REG_STATE_EMERGENCY_CALL_ONLY = 2<br>差异内容：REG_STATE_EMERGENCY_CALL_ONLY = 2|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：RegState；<br>API声明：REG_STATE_POWER_OFF = 3<br>差异内容：REG_STATE_POWER_OFF = 3|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：export enum NsaState<br>差异内容：export enum NsaState|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NsaState；<br>API声明：NSA_STATE_NOT_SUPPORT = 1<br>差异内容：NSA_STATE_NOT_SUPPORT = 1|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NsaState；<br>API声明：NSA_STATE_NO_DETECT = 2<br>差异内容：NSA_STATE_NO_DETECT = 2|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NsaState；<br>API声明：NSA_STATE_CONNECTED_DETECT = 3<br>差异内容：NSA_STATE_CONNECTED_DETECT = 3|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NsaState；<br>API声明：NSA_STATE_IDLE_DETECT = 4<br>差异内容：NSA_STATE_IDLE_DETECT = 4|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NsaState；<br>API声明：NSA_STATE_DUAL_CONNECTED = 5<br>差异内容：NSA_STATE_DUAL_CONNECTED = 5|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NsaState；<br>API声明：NSA_STATE_SA_ATTACHED = 6<br>差异内容：NSA_STATE_SA_ATTACHED = 6|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：export interface CellInformation<br>差异内容：export interface CellInformation|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：CellInformation；<br>API声明：networkType: NetworkType;<br>差异内容：networkType: NetworkType;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：CellInformation；<br>API声明：signalInformation: SignalInformation;<br>差异内容：signalInformation: SignalInformation;|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：radio；<br>API声明：export enum NetworkSelectionMode<br>差异内容：export enum NetworkSelectionMode|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkSelectionMode；<br>API声明：NETWORK_SELECTION_UNKNOWN<br>差异内容：NETWORK_SELECTION_UNKNOWN|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkSelectionMode；<br>API声明：NETWORK_SELECTION_AUTOMATIC<br>差异内容：NETWORK_SELECTION_AUTOMATIC|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：NetworkSelectionMode；<br>API声明：NETWORK_SELECTION_MANUAL<br>差异内容：NETWORK_SELECTION_MANUAL|api/@ohos.telephony.radio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace sim<br>差异内容：declare namespace sim|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function isSimActive(slotId: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：function isSimActive(slotId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function isSimActive(slotId: number): Promise\<boolean>;<br>差异内容：function isSimActive(slotId: number): Promise\<boolean>;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function isSimActiveSync(slotId: number): boolean;<br>差异内容：function isSimActiveSync(slotId: number): boolean;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getDefaultVoiceSlotId(callback: AsyncCallback\<number>): void;<br>差异内容：function getDefaultVoiceSlotId(callback: AsyncCallback\<number>): void;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getDefaultVoiceSlotId(): Promise\<number>;<br>差异内容：function getDefaultVoiceSlotId(): Promise\<number>;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function hasOperatorPrivileges(slotId: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：function hasOperatorPrivileges(slotId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function hasOperatorPrivileges(slotId: number): Promise\<boolean>;<br>差异内容：function hasOperatorPrivileges(slotId: number): Promise\<boolean>;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getISOCountryCodeForSim(slotId: number, callback: AsyncCallback\<string>): void;<br>差异内容：function getISOCountryCodeForSim(slotId: number, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getISOCountryCodeForSim(slotId: number): Promise\<string>;<br>差异内容：function getISOCountryCodeForSim(slotId: number): Promise\<string>;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getISOCountryCodeForSimSync(slotId: number): string;<br>差异内容：function getISOCountryCodeForSimSync(slotId: number): string;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getSimOperatorNumeric(slotId: number, callback: AsyncCallback\<string>): void;<br>差异内容：function getSimOperatorNumeric(slotId: number, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getSimOperatorNumeric(slotId: number): Promise\<string>;<br>差异内容：function getSimOperatorNumeric(slotId: number): Promise\<string>;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getSimOperatorNumericSync(slotId: number): string;<br>差异内容：function getSimOperatorNumericSync(slotId: number): string;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getSimSpn(slotId: number, callback: AsyncCallback\<string>): void;<br>差异内容：function getSimSpn(slotId: number, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getSimSpn(slotId: number): Promise\<string>;<br>差异内容：function getSimSpn(slotId: number): Promise\<string>;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getSimSpnSync(slotId: number): string;<br>差异内容：function getSimSpnSync(slotId: number): string;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getSimState(slotId: number, callback: AsyncCallback\<SimState>): void;<br>差异内容：function getSimState(slotId: number, callback: AsyncCallback\<SimState>): void;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getSimState(slotId: number): Promise\<SimState>;<br>差异内容：function getSimState(slotId: number): Promise\<SimState>;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getSimStateSync(slotId: number): SimState;<br>差异内容：function getSimStateSync(slotId: number): SimState;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getCardType(slotId: number, callback: AsyncCallback\<CardType>): void;<br>差异内容：function getCardType(slotId: number, callback: AsyncCallback\<CardType>): void;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getCardType(slotId: number): Promise\<CardType>;<br>差异内容：function getCardType(slotId: number): Promise\<CardType>;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getCardTypeSync(slotId: number): CardType;<br>差异内容：function getCardTypeSync(slotId: number): CardType;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getMaxSimCount(): number;<br>差异内容：function getMaxSimCount(): number;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function hasSimCard(slotId: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：function hasSimCard(slotId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function hasSimCard(slotId: number): Promise\<boolean>;<br>差异内容：function hasSimCard(slotId: number): Promise\<boolean>;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function hasSimCardSync(slotId: number): boolean;<br>差异内容：function hasSimCardSync(slotId: number): boolean;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getSimAccountInfo(slotId: number, callback: AsyncCallback\<IccAccountInfo>): void;<br>差异内容：function getSimAccountInfo(slotId: number, callback: AsyncCallback\<IccAccountInfo>): void;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getSimAccountInfo(slotId: number): Promise\<IccAccountInfo>;<br>差异内容：function getSimAccountInfo(slotId: number): Promise\<IccAccountInfo>;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getActiveSimAccountInfoList(callback: AsyncCallback\<Array\<IccAccountInfo>>): void;<br>差异内容：function getActiveSimAccountInfoList(callback: AsyncCallback\<Array\<IccAccountInfo>>): void;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getActiveSimAccountInfoList(): Promise\<Array\<IccAccountInfo>>;<br>差异内容：function getActiveSimAccountInfoList(): Promise\<Array\<IccAccountInfo>>;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getOpKey(slotId: number, callback: AsyncCallback\<string>): void;<br>差异内容：function getOpKey(slotId: number, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getOpKey(slotId: number): Promise\<string>;<br>差异内容：function getOpKey(slotId: number): Promise\<string>;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getOpKeySync(slotId: number): string;<br>差异内容：function getOpKeySync(slotId: number): string;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getOpName(slotId: number, callback: AsyncCallback\<string>): void;<br>差异内容：function getOpName(slotId: number, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getOpName(slotId: number): Promise\<string>;<br>差异内容：function getOpName(slotId: number): Promise\<string>;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getOpNameSync(slotId: number): string;<br>差异内容：function getOpNameSync(slotId: number): string;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getDefaultVoiceSimId(callback: AsyncCallback\<number>): void;<br>差异内容：function getDefaultVoiceSimId(callback: AsyncCallback\<number>): void;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：function getDefaultVoiceSimId(): Promise\<number>;<br>差异内容：function getDefaultVoiceSimId(): Promise\<number>;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：export interface IccAccountInfo<br>差异内容：export interface IccAccountInfo|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：IccAccountInfo；<br>API声明：simId: number;<br>差异内容：simId: number;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：IccAccountInfo；<br>API声明：slotIndex: number;<br>差异内容：slotIndex: number;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：IccAccountInfo；<br>API声明：isEsim: boolean;<br>差异内容：isEsim: boolean;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：IccAccountInfo；<br>API声明：isActive: boolean;<br>差异内容：isActive: boolean;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：IccAccountInfo；<br>API声明：iccId: string;<br>差异内容：iccId: string;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：IccAccountInfo；<br>API声明：showName: string;<br>差异内容：showName: string;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：IccAccountInfo；<br>API声明：showNumber: string;<br>差异内容：showNumber: string;|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：export enum CardType<br>差异内容：export enum CardType|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：CardType；<br>API声明：UNKNOWN_CARD = -1<br>差异内容：UNKNOWN_CARD = -1|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：CardType；<br>API声明：SINGLE_MODE_SIM_CARD = 10<br>差异内容：SINGLE_MODE_SIM_CARD = 10|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：CardType；<br>API声明：SINGLE_MODE_USIM_CARD = 20<br>差异内容：SINGLE_MODE_USIM_CARD = 20|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：CardType；<br>API声明：SINGLE_MODE_RUIM_CARD = 30<br>差异内容：SINGLE_MODE_RUIM_CARD = 30|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：CardType；<br>API声明：DUAL_MODE_CG_CARD = 40<br>差异内容：DUAL_MODE_CG_CARD = 40|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：CardType；<br>API声明：CT_NATIONAL_ROAMING_CARD = 41<br>差异内容：CT_NATIONAL_ROAMING_CARD = 41|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：CardType；<br>API声明：CU_DUAL_MODE_CARD = 42<br>差异内容：CU_DUAL_MODE_CARD = 42|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：CardType；<br>API声明：DUAL_MODE_TELECOM_LTE_CARD = 43<br>差异内容：DUAL_MODE_TELECOM_LTE_CARD = 43|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：CardType；<br>API声明：DUAL_MODE_UG_CARD = 50<br>差异内容：DUAL_MODE_UG_CARD = 50|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：CardType；<br>API声明：SINGLE_MODE_ISIM_CARD = 60<br>差异内容：SINGLE_MODE_ISIM_CARD = 60|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：sim；<br>API声明：export enum SimState<br>差异内容：export enum SimState|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：SimState；<br>API声明：SIM_STATE_UNKNOWN<br>差异内容：SIM_STATE_UNKNOWN|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：SimState；<br>API声明：SIM_STATE_NOT_PRESENT<br>差异内容：SIM_STATE_NOT_PRESENT|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：SimState；<br>API声明：SIM_STATE_LOCKED<br>差异内容：SIM_STATE_LOCKED|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：SimState；<br>API声明：SIM_STATE_NOT_READY<br>差异内容：SIM_STATE_NOT_READY|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：SimState；<br>API声明：SIM_STATE_READY<br>差异内容：SIM_STATE_READY|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：SimState；<br>API声明：SIM_STATE_LOADED<br>差异内容：SIM_STATE_LOADED|api/@ohos.telephony.sim.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace sms<br>差异内容：declare namespace sms|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：sms；<br>API声明：function createMessage(pdu: Array\<number>, specification: string, callback: AsyncCallback\<ShortMessage>): void;<br>差异内容：function createMessage(pdu: Array\<number>, specification: string, callback: AsyncCallback\<ShortMessage>): void;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：sms；<br>API声明：function createMessage(pdu: Array\<number>, specification: string): Promise\<ShortMessage>;<br>差异内容：function createMessage(pdu: Array\<number>, specification: string): Promise\<ShortMessage>;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：sms；<br>API声明：function sendMessage(options: SendMessageOptions): void;<br>差异内容：function sendMessage(options: SendMessageOptions): void;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：sms；<br>API声明：function sendShortMessage(options: SendMessageOptions, callback: AsyncCallback\<void>): void;<br>差异内容：function sendShortMessage(options: SendMessageOptions, callback: AsyncCallback\<void>): void;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：sms；<br>API声明：function sendShortMessage(options: SendMessageOptions): Promise\<void>;<br>差异内容：function sendShortMessage(options: SendMessageOptions): Promise\<void>;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：sms；<br>API声明：function getDefaultSmsSlotId(callback: AsyncCallback\<number>): void;<br>差异内容：function getDefaultSmsSlotId(callback: AsyncCallback\<number>): void;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：sms；<br>API声明：function getDefaultSmsSlotId(): Promise\<number>;<br>差异内容：function getDefaultSmsSlotId(): Promise\<number>;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：sms；<br>API声明：function hasSmsCapability(): boolean;<br>差异内容：function hasSmsCapability(): boolean;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：sms；<br>API声明：function getDefaultSmsSimId(callback: AsyncCallback\<number>): void;<br>差异内容：function getDefaultSmsSimId(callback: AsyncCallback\<number>): void;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：sms；<br>API声明：function getDefaultSmsSimId(): Promise\<number>;<br>差异内容：function getDefaultSmsSimId(): Promise\<number>;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：sms；<br>API声明：export interface ShortMessage<br>差异内容：export interface ShortMessage|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ShortMessage；<br>API声明：visibleMessageBody: string;<br>差异内容：visibleMessageBody: string;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ShortMessage；<br>API声明：visibleRawAddress: string;<br>差异内容：visibleRawAddress: string;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ShortMessage；<br>API声明：messageClass: ShortMessageClass;<br>差异内容：messageClass: ShortMessageClass;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ShortMessage；<br>API声明：protocolId: number;<br>差异内容：protocolId: number;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ShortMessage；<br>API声明：scAddress: string;<br>差异内容：scAddress: string;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ShortMessage；<br>API声明：scTimestamp: number;<br>差异内容：scTimestamp: number;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ShortMessage；<br>API声明：isReplaceMessage: boolean;<br>差异内容：isReplaceMessage: boolean;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ShortMessage；<br>API声明：hasReplyPath: boolean;<br>差异内容：hasReplyPath: boolean;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ShortMessage；<br>API声明：pdu: Array\<number>;<br>差异内容：pdu: Array\<number>;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ShortMessage；<br>API声明：status: number;<br>差异内容：status: number;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ShortMessage；<br>API声明：isSmsStatusReportMessage: boolean;<br>差异内容：isSmsStatusReportMessage: boolean;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：sms；<br>API声明：export enum ShortMessageClass<br>差异内容：export enum ShortMessageClass|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ShortMessageClass；<br>API声明：UNKNOWN<br>差异内容：UNKNOWN|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ShortMessageClass；<br>API声明：INSTANT_MESSAGE<br>差异内容：INSTANT_MESSAGE|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ShortMessageClass；<br>API声明：OPTIONAL_MESSAGE<br>差异内容：OPTIONAL_MESSAGE|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ShortMessageClass；<br>API声明：SIM_MESSAGE<br>差异内容：SIM_MESSAGE|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ShortMessageClass；<br>API声明：FORWARD_MESSAGE<br>差异内容：FORWARD_MESSAGE|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：sms；<br>API声明：export interface SendMessageOptions<br>差异内容：export interface SendMessageOptions|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：SendMessageOptions；<br>API声明：slotId: number;<br>差异内容：slotId: number;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：SendMessageOptions；<br>API声明：destinationHost: string;<br>差异内容：destinationHost: string;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：SendMessageOptions；<br>API声明：serviceCenter?: string;<br>差异内容：serviceCenter?: string;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：SendMessageOptions；<br>API声明：content: string \| Array\<number>;<br>差异内容：content: string \| Array\<number>;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：SendMessageOptions；<br>API声明：destinationPort?: number;<br>差异内容：destinationPort?: number;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：SendMessageOptions；<br>API声明：sendCallback?: AsyncCallback\<ISendShortMessageCallback>;<br>差异内容：sendCallback?: AsyncCallback\<ISendShortMessageCallback>;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：SendMessageOptions；<br>API声明：deliveryCallback?: AsyncCallback\<IDeliveryShortMessageCallback>;<br>差异内容：deliveryCallback?: AsyncCallback\<IDeliveryShortMessageCallback>;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：sms；<br>API声明：export interface ISendShortMessageCallback<br>差异内容：export interface ISendShortMessageCallback|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ISendShortMessageCallback；<br>API声明：result: SendSmsResult;<br>差异内容：result: SendSmsResult;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ISendShortMessageCallback；<br>API声明：url: string;<br>差异内容：url: string;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：ISendShortMessageCallback；<br>API声明：isLastPart: boolean;<br>差异内容：isLastPart: boolean;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：sms；<br>API声明：export interface IDeliveryShortMessageCallback<br>差异内容：export interface IDeliveryShortMessageCallback|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：IDeliveryShortMessageCallback；<br>API声明：pdu: Array\<number>;<br>差异内容：pdu: Array\<number>;|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：sms；<br>API声明：export enum SendSmsResult<br>差异内容：export enum SendSmsResult|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：SendSmsResult；<br>API声明：SEND_SMS_SUCCESS = 0<br>差异内容：SEND_SMS_SUCCESS = 0|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：SendSmsResult；<br>API声明：SEND_SMS_FAILURE_UNKNOWN = 1<br>差异内容：SEND_SMS_FAILURE_UNKNOWN = 1|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：SendSmsResult；<br>API声明：SEND_SMS_FAILURE_RADIO_OFF = 2<br>差异内容：SEND_SMS_FAILURE_RADIO_OFF = 2|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：SendSmsResult；<br>API声明：SEND_SMS_FAILURE_SERVICE_UNAVAILABLE = 3<br>差异内容：SEND_SMS_FAILURE_SERVICE_UNAVAILABLE = 3|api/@ohos.telephony.sms.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace vcard<br>差异内容：declare namespace vcard|api/@ohos.telephony.vcard.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.telephony.call.d.ts<br>差异内容：TelephonyKit|api/@ohos.telephony.call.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.telephony.data.d.ts<br>差异内容：TelephonyKit|api/@ohos.telephony.data.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.telephony.observer.d.ts<br>差异内容：TelephonyKit|api/@ohos.telephony.observer.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.telephony.radio.d.ts<br>差异内容：TelephonyKit|api/@ohos.telephony.radio.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.telephony.sim.d.ts<br>差异内容：TelephonyKit|api/@ohos.telephony.sim.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.telephony.sms.d.ts<br>差异内容：TelephonyKit|api/@ohos.telephony.sms.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.telephony.vcard.d.ts<br>差异内容：TelephonyKit|api/@ohos.telephony.vcard.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.TelephonyKit.d.ts<br>差异内容：TelephonyKit|kits/@kit.TelephonyKit.d.ts|
