| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: global;<br>API declaration: declare namespace call<br>Differences: declare namespace call|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function dial(phoneNumber: string, options: DialOptions, callback: AsyncCallback\<boolean>): void;<br>Differences: function dial(phoneNumber: string, options: DialOptions, callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function dial(phoneNumber: string, options?: DialOptions): Promise\<boolean>;<br>Differences: function dial(phoneNumber: string, options?: DialOptions): Promise\<boolean>;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function dial(phoneNumber: string, callback: AsyncCallback\<boolean>): void;<br>Differences: function dial(phoneNumber: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function makeCall(phoneNumber: string, callback: AsyncCallback\<void>): void;<br>Differences: function makeCall(phoneNumber: string, callback: AsyncCallback\<void>): void;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function makeCall(phoneNumber: string): Promise\<void>;<br>Differences: function makeCall(phoneNumber: string): Promise\<void>;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function hasCall(callback: AsyncCallback\<boolean>): void;<br>Differences: function hasCall(callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function hasCall(): Promise\<boolean>;<br>Differences: function hasCall(): Promise\<boolean>;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function hasCallSync(): boolean;<br>Differences: function hasCallSync(): boolean;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function getCallState(callback: AsyncCallback\<CallState>): void;<br>Differences: function getCallState(callback: AsyncCallback\<CallState>): void;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function getCallState(): Promise\<CallState>;<br>Differences: function getCallState(): Promise\<CallState>;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function getCallStateSync(): CallState;<br>Differences: function getCallStateSync(): CallState;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function hasVoiceCapability(): boolean;<br>Differences: function hasVoiceCapability(): boolean;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function isEmergencyPhoneNumber(phoneNumber: string, options: EmergencyNumberOptions, callback: AsyncCallback\<boolean>): void;<br>Differences: function isEmergencyPhoneNumber(phoneNumber: string, options: EmergencyNumberOptions, callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function isEmergencyPhoneNumber(phoneNumber: string, options?: EmergencyNumberOptions): Promise\<boolean>;<br>Differences: function isEmergencyPhoneNumber(phoneNumber: string, options?: EmergencyNumberOptions): Promise\<boolean>;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function isEmergencyPhoneNumber(phoneNumber: string, callback: AsyncCallback\<boolean>): void;<br>Differences: function isEmergencyPhoneNumber(phoneNumber: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function formatPhoneNumber(phoneNumber: string, options: NumberFormatOptions, callback: AsyncCallback\<string>): void;<br>Differences: function formatPhoneNumber(phoneNumber: string, options: NumberFormatOptions, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function formatPhoneNumber(phoneNumber: string, options?: NumberFormatOptions): Promise\<string>;<br>Differences: function formatPhoneNumber(phoneNumber: string, options?: NumberFormatOptions): Promise\<string>;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function formatPhoneNumber(phoneNumber: string, callback: AsyncCallback\<string>): void;<br>Differences: function formatPhoneNumber(phoneNumber: string, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function formatPhoneNumberToE164(phoneNumber: string, countryCode: string, callback: AsyncCallback\<string>): void;<br>Differences: function formatPhoneNumberToE164(phoneNumber: string, countryCode: string, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: function formatPhoneNumberToE164(phoneNumber: string, countryCode: string): Promise\<string>;<br>Differences: function formatPhoneNumberToE164(phoneNumber: string, countryCode: string): Promise\<string>;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: export enum CallState<br>Differences: export enum CallState|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: CallState;<br>API declaration: CALL_STATE_UNKNOWN = -1<br>Differences: CALL_STATE_UNKNOWN = -1|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: CallState;<br>API declaration: CALL_STATE_IDLE = 0<br>Differences: CALL_STATE_IDLE = 0|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: CallState;<br>API declaration: CALL_STATE_RINGING = 1<br>Differences: CALL_STATE_RINGING = 1|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: CallState;<br>API declaration: CALL_STATE_OFFHOOK = 2<br>Differences: CALL_STATE_OFFHOOK = 2|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: CallState;<br>API declaration: CALL_STATE_ANSWERED = 3<br>Differences: CALL_STATE_ANSWERED = 3|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: export interface DialOptions<br>Differences: export interface DialOptions|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: DialOptions;<br>API declaration: extras?: boolean;<br>Differences: extras?: boolean;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: export interface EmergencyNumberOptions<br>Differences: export interface EmergencyNumberOptions|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: EmergencyNumberOptions;<br>API declaration: slotId?: number;<br>Differences: slotId?: number;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: call;<br>API declaration: export interface NumberFormatOptions<br>Differences: export interface NumberFormatOptions|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: NumberFormatOptions;<br>API declaration: countryCode?: string;<br>Differences: countryCode?: string;|api/@ohos.telephony.call.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace data<br>Differences: declare namespace data|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: data;<br>API declaration: function getDefaultCellularDataSlotId(callback: AsyncCallback\<number>): void;<br>Differences: function getDefaultCellularDataSlotId(callback: AsyncCallback\<number>): void;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: data;<br>API declaration: function getDefaultCellularDataSlotId(): Promise\<number>;<br>Differences: function getDefaultCellularDataSlotId(): Promise\<number>;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: data;<br>API declaration: function getDefaultCellularDataSlotIdSync(): number;<br>Differences: function getDefaultCellularDataSlotIdSync(): number;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: data;<br>API declaration: function getCellularDataFlowType(callback: AsyncCallback\<DataFlowType>): void;<br>Differences: function getCellularDataFlowType(callback: AsyncCallback\<DataFlowType>): void;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: data;<br>API declaration: function getCellularDataFlowType(): Promise\<DataFlowType>;<br>Differences: function getCellularDataFlowType(): Promise\<DataFlowType>;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: data;<br>API declaration: function getCellularDataState(callback: AsyncCallback\<DataConnectState>): void;<br>Differences: function getCellularDataState(callback: AsyncCallback\<DataConnectState>): void;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: data;<br>API declaration: function getCellularDataState(): Promise\<DataConnectState>;<br>Differences: function getCellularDataState(): Promise\<DataConnectState>;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: data;<br>API declaration: function isCellularDataEnabled(callback: AsyncCallback\<boolean>): void;<br>Differences: function isCellularDataEnabled(callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: data;<br>API declaration: function isCellularDataEnabled(): Promise\<boolean>;<br>Differences: function isCellularDataEnabled(): Promise\<boolean>;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: data;<br>API declaration: function isCellularDataRoamingEnabled(slotId: number, callback: AsyncCallback\<boolean>): void;<br>Differences: function isCellularDataRoamingEnabled(slotId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: data;<br>API declaration: function isCellularDataRoamingEnabled(slotId: number): Promise\<boolean>;<br>Differences: function isCellularDataRoamingEnabled(slotId: number): Promise\<boolean>;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: data;<br>API declaration: function getDefaultCellularDataSimId(): number;<br>Differences: function getDefaultCellularDataSimId(): number;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: data;<br>API declaration: export enum DataFlowType<br>Differences: export enum DataFlowType|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: DataFlowType;<br>API declaration: DATA_FLOW_TYPE_NONE = 0<br>Differences: DATA_FLOW_TYPE_NONE = 0|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: DataFlowType;<br>API declaration: DATA_FLOW_TYPE_DOWN = 1<br>Differences: DATA_FLOW_TYPE_DOWN = 1|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: DataFlowType;<br>API declaration: DATA_FLOW_TYPE_UP = 2<br>Differences: DATA_FLOW_TYPE_UP = 2|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: DataFlowType;<br>API declaration: DATA_FLOW_TYPE_UP_DOWN = 3<br>Differences: DATA_FLOW_TYPE_UP_DOWN = 3|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: DataFlowType;<br>API declaration: DATA_FLOW_TYPE_DORMANT = 4<br>Differences: DATA_FLOW_TYPE_DORMANT = 4|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: data;<br>API declaration: export enum DataConnectState<br>Differences: export enum DataConnectState|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: DataConnectState;<br>API declaration: DATA_STATE_UNKNOWN = -1<br>Differences: DATA_STATE_UNKNOWN = -1|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: DataConnectState;<br>API declaration: DATA_STATE_DISCONNECTED = 0<br>Differences: DATA_STATE_DISCONNECTED = 0|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: DataConnectState;<br>API declaration: DATA_STATE_CONNECTING = 1<br>Differences: DATA_STATE_CONNECTING = 1|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: DataConnectState;<br>API declaration: DATA_STATE_CONNECTED = 2<br>Differences: DATA_STATE_CONNECTED = 2|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: DataConnectState;<br>API declaration: DATA_STATE_SUSPENDED = 3<br>Differences: DATA_STATE_SUSPENDED = 3|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace observer<br>Differences: declare namespace observer|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: type NetworkState = radio.NetworkState;<br>Differences: type NetworkState = radio.NetworkState;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: type SignalInformation = radio.SignalInformation;<br>Differences: type SignalInformation = radio.SignalInformation;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: type DataConnectState = data.DataConnectState;<br>Differences: type DataConnectState = data.DataConnectState;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: type RatType = radio.RadioTechnology;<br>Differences: type RatType = radio.RadioTechnology;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: type DataFlowType = data.DataFlowType;<br>Differences: type DataFlowType = data.DataFlowType;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: type CallState = call.CallState;<br>Differences: type CallState = call.CallState;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: type CardType = sim.CardType;<br>Differences: type CardType = sim.CardType;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: type SimState = sim.SimState;<br>Differences: type SimState = sim.SimState;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function on(type: 'networkStateChange', callback: Callback\<NetworkState>): void;<br>Differences: function on(type: 'networkStateChange', callback: Callback\<NetworkState>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function on(type: 'networkStateChange', options: ObserverOptions, callback: Callback\<NetworkState>): void;<br>Differences: function on(type: 'networkStateChange', options: ObserverOptions, callback: Callback\<NetworkState>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function off(type: 'networkStateChange', callback?: Callback\<NetworkState>): void;<br>Differences: function off(type: 'networkStateChange', callback?: Callback\<NetworkState>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function on(type: 'signalInfoChange', callback: Callback\<Array\<SignalInformation>>): void;<br>Differences: function on(type: 'signalInfoChange', callback: Callback\<Array\<SignalInformation>>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function on(type: 'signalInfoChange', options: ObserverOptions, callback: Callback\<Array\<SignalInformation>>): void;<br>Differences: function on(type: 'signalInfoChange', options: ObserverOptions, callback: Callback\<Array\<SignalInformation>>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function off(type: 'signalInfoChange', callback?: Callback\<Array\<SignalInformation>>): void;<br>Differences: function off(type: 'signalInfoChange', callback?: Callback\<Array\<SignalInformation>>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function on(type: 'cellularDataConnectionStateChange', callback: Callback\<DataConnectionStateInfo>): void;<br>Differences: function on(type: 'cellularDataConnectionStateChange', callback: Callback\<DataConnectionStateInfo>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function on(type: 'cellularDataConnectionStateChange', options: ObserverOptions, callback: Callback\<DataConnectionStateInfo>): void;<br>Differences: function on(type: 'cellularDataConnectionStateChange', options: ObserverOptions, callback: Callback\<DataConnectionStateInfo>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function off(type: 'cellularDataConnectionStateChange', callback?: Callback\<DataConnectionStateInfo>): void;<br>Differences: function off(type: 'cellularDataConnectionStateChange', callback?: Callback\<DataConnectionStateInfo>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function on(type: 'cellularDataFlowChange', callback: Callback\<DataFlowType>): void;<br>Differences: function on(type: 'cellularDataFlowChange', callback: Callback\<DataFlowType>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function on(type: 'cellularDataFlowChange', options: ObserverOptions, callback: Callback\<DataFlowType>): void;<br>Differences: function on(type: 'cellularDataFlowChange', options: ObserverOptions, callback: Callback\<DataFlowType>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function off(type: 'cellularDataFlowChange', callback?: Callback\<DataFlowType>): void;<br>Differences: function off(type: 'cellularDataFlowChange', callback?: Callback\<DataFlowType>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function on(type: 'callStateChange', callback: Callback\<CallStateInfo>): void;<br>Differences: function on(type: 'callStateChange', callback: Callback\<CallStateInfo>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function on(type: 'callStateChange', options: ObserverOptions, callback: Callback\<CallStateInfo>): void;<br>Differences: function on(type: 'callStateChange', options: ObserverOptions, callback: Callback\<CallStateInfo>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function off(type: 'callStateChange', callback?: Callback\<CallStateInfo>): void;<br>Differences: function off(type: 'callStateChange', callback?: Callback\<CallStateInfo>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function on(type: 'simStateChange', callback: Callback\<SimStateData>): void;<br>Differences: function on(type: 'simStateChange', callback: Callback\<SimStateData>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function on(type: 'simStateChange', options: ObserverOptions, callback: Callback\<SimStateData>): void;<br>Differences: function on(type: 'simStateChange', options: ObserverOptions, callback: Callback\<SimStateData>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function off(type: 'simStateChange', callback?: Callback\<SimStateData>): void;<br>Differences: function off(type: 'simStateChange', callback?: Callback\<SimStateData>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function on(type: 'iccAccountInfoChange', callback: Callback\<void>): void;<br>Differences: function on(type: 'iccAccountInfoChange', callback: Callback\<void>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: function off(type: 'iccAccountInfoChange', callback?: Callback\<void>): void;<br>Differences: function off(type: 'iccAccountInfoChange', callback?: Callback\<void>): void;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: export interface SimStateData<br>Differences: export interface SimStateData|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: SimStateData;<br>API declaration: type: CardType;<br>Differences: type: CardType;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: SimStateData;<br>API declaration: state: SimState;<br>Differences: state: SimState;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: SimStateData;<br>API declaration: reason: LockReason;<br>Differences: reason: LockReason;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: export interface CallStateInfo<br>Differences: export interface CallStateInfo|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: CallStateInfo;<br>API declaration: state: CallState;<br>Differences: state: CallState;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: CallStateInfo;<br>API declaration: number: string;<br>Differences: number: string;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: export interface DataConnectionStateInfo<br>Differences: export interface DataConnectionStateInfo|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: DataConnectionStateInfo;<br>API declaration: state: DataConnectState;<br>Differences: state: DataConnectState;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: DataConnectionStateInfo;<br>API declaration: network: RatType;<br>Differences: network: RatType;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: export interface ObserverOptions<br>Differences: export interface ObserverOptions|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: ObserverOptions;<br>API declaration: slotId: number;<br>Differences: slotId: number;|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: observer;<br>API declaration: export enum LockReason<br>Differences: export enum LockReason|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: LockReason;<br>API declaration: SIM_NONE<br>Differences: SIM_NONE|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: LockReason;<br>API declaration: SIM_PIN<br>Differences: SIM_PIN|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: LockReason;<br>API declaration: SIM_PUK<br>Differences: SIM_PUK|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: LockReason;<br>API declaration: SIM_PN_PIN<br>Differences: SIM_PN_PIN|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: LockReason;<br>API declaration: SIM_PN_PUK<br>Differences: SIM_PN_PUK|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: LockReason;<br>API declaration: SIM_PU_PIN<br>Differences: SIM_PU_PIN|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: LockReason;<br>API declaration: SIM_PU_PUK<br>Differences: SIM_PU_PUK|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: LockReason;<br>API declaration: SIM_PP_PIN<br>Differences: SIM_PP_PIN|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: LockReason;<br>API declaration: SIM_PP_PUK<br>Differences: SIM_PP_PUK|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: LockReason;<br>API declaration: SIM_PC_PIN<br>Differences: SIM_PC_PIN|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: LockReason;<br>API declaration: SIM_PC_PUK<br>Differences: SIM_PC_PUK|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: LockReason;<br>API declaration: SIM_SIM_PIN<br>Differences: SIM_SIM_PIN|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: LockReason;<br>API declaration: SIM_SIM_PUK<br>Differences: SIM_SIM_PUK|api/@ohos.telephony.observer.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace radio<br>Differences: declare namespace radio|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getRadioTech(slotId: number, callback: AsyncCallback\<NetworkRadioTech>): void;<br>Differences: function getRadioTech(slotId: number, callback: AsyncCallback\<NetworkRadioTech>): void;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getRadioTech(slotId: number): Promise\<NetworkRadioTech>;<br>Differences: function getRadioTech(slotId: number): Promise\<NetworkRadioTech>;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getNetworkState(slotId: number, callback: AsyncCallback\<NetworkState>): void;<br>Differences: function getNetworkState(slotId: number, callback: AsyncCallback\<NetworkState>): void;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getNetworkState(slotId?: number): Promise\<NetworkState>;<br>Differences: function getNetworkState(slotId?: number): Promise\<NetworkState>;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getNetworkState(callback: AsyncCallback\<NetworkState>): void;<br>Differences: function getNetworkState(callback: AsyncCallback\<NetworkState>): void;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getNetworkSelectionMode(slotId: number, callback: AsyncCallback\<NetworkSelectionMode>): void;<br>Differences: function getNetworkSelectionMode(slotId: number, callback: AsyncCallback\<NetworkSelectionMode>): void;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getNetworkSelectionMode(slotId: number): Promise\<NetworkSelectionMode>;<br>Differences: function getNetworkSelectionMode(slotId: number): Promise\<NetworkSelectionMode>;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getISOCountryCodeForNetwork(slotId: number, callback: AsyncCallback\<string>): void;<br>Differences: function getISOCountryCodeForNetwork(slotId: number, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getISOCountryCodeForNetwork(slotId: number): Promise\<string>;<br>Differences: function getISOCountryCodeForNetwork(slotId: number): Promise\<string>;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getISOCountryCodeForNetworkSync(slotId: number): string;<br>Differences: function getISOCountryCodeForNetworkSync(slotId: number): string;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getPrimarySlotId(callback: AsyncCallback\<number>): void;<br>Differences: function getPrimarySlotId(callback: AsyncCallback\<number>): void;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getPrimarySlotId(): Promise\<number>;<br>Differences: function getPrimarySlotId(): Promise\<number>;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getSignalInformation(slotId: number, callback: AsyncCallback\<Array\<SignalInformation>>): void;<br>Differences: function getSignalInformation(slotId: number, callback: AsyncCallback\<Array\<SignalInformation>>): void;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getSignalInformation(slotId: number): Promise\<Array\<SignalInformation>>;<br>Differences: function getSignalInformation(slotId: number): Promise\<Array\<SignalInformation>>;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getSignalInformationSync(slotId: number): Array\<SignalInformation>;<br>Differences: function getSignalInformationSync(slotId: number): Array\<SignalInformation>;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function isNrSupported(): boolean;<br>Differences: function isNrSupported(): boolean;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function isNrSupported(slotId: number): boolean;<br>Differences: function isNrSupported(slotId: number): boolean;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function isNRSupported(): boolean;<br>Differences: function isNRSupported(): boolean;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function isNRSupported(slotId: number): boolean;<br>Differences: function isNRSupported(slotId: number): boolean;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function isRadioOn(slotId: number, callback: AsyncCallback\<boolean>): void;<br>Differences: function isRadioOn(slotId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function isRadioOn(slotId?: number): Promise\<boolean>;<br>Differences: function isRadioOn(slotId?: number): Promise\<boolean>;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function isRadioOn(callback: AsyncCallback\<boolean>): void;<br>Differences: function isRadioOn(callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getOperatorName(slotId: number, callback: AsyncCallback\<string>): void;<br>Differences: function getOperatorName(slotId: number, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getOperatorName(slotId: number): Promise\<string>;<br>Differences: function getOperatorName(slotId: number): Promise\<string>;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getOperatorNameSync(slotId: number): string;<br>Differences: function getOperatorNameSync(slotId: number): string;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: export interface NetworkRadioTech<br>Differences: export interface NetworkRadioTech|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkRadioTech;<br>API declaration: psRadioTech: RadioTechnology;<br>Differences: psRadioTech: RadioTechnology;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkRadioTech;<br>API declaration: csRadioTech: RadioTechnology;<br>Differences: csRadioTech: RadioTechnology;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: export enum RadioTechnology<br>Differences: export enum RadioTechnology|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: RadioTechnology;<br>API declaration: RADIO_TECHNOLOGY_UNKNOWN = 0<br>Differences: RADIO_TECHNOLOGY_UNKNOWN = 0|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: RadioTechnology;<br>API declaration: RADIO_TECHNOLOGY_GSM = 1<br>Differences: RADIO_TECHNOLOGY_GSM = 1|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: RadioTechnology;<br>API declaration: RADIO_TECHNOLOGY_1XRTT = 2<br>Differences: RADIO_TECHNOLOGY_1XRTT = 2|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: RadioTechnology;<br>API declaration: RADIO_TECHNOLOGY_WCDMA = 3<br>Differences: RADIO_TECHNOLOGY_WCDMA = 3|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: RadioTechnology;<br>API declaration: RADIO_TECHNOLOGY_HSPA = 4<br>Differences: RADIO_TECHNOLOGY_HSPA = 4|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: RadioTechnology;<br>API declaration: RADIO_TECHNOLOGY_HSPAP = 5<br>Differences: RADIO_TECHNOLOGY_HSPAP = 5|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: RadioTechnology;<br>API declaration: RADIO_TECHNOLOGY_TD_SCDMA = 6<br>Differences: RADIO_TECHNOLOGY_TD_SCDMA = 6|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: RadioTechnology;<br>API declaration: RADIO_TECHNOLOGY_EVDO = 7<br>Differences: RADIO_TECHNOLOGY_EVDO = 7|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: RadioTechnology;<br>API declaration: RADIO_TECHNOLOGY_EHRPD = 8<br>Differences: RADIO_TECHNOLOGY_EHRPD = 8|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: RadioTechnology;<br>API declaration: RADIO_TECHNOLOGY_LTE = 9<br>Differences: RADIO_TECHNOLOGY_LTE = 9|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: RadioTechnology;<br>API declaration: RADIO_TECHNOLOGY_LTE_CA = 10<br>Differences: RADIO_TECHNOLOGY_LTE_CA = 10|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: RadioTechnology;<br>API declaration: RADIO_TECHNOLOGY_IWLAN = 11<br>Differences: RADIO_TECHNOLOGY_IWLAN = 11|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: RadioTechnology;<br>API declaration: RADIO_TECHNOLOGY_NR = 12<br>Differences: RADIO_TECHNOLOGY_NR = 12|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: export interface SignalInformation<br>Differences: export interface SignalInformation|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: SignalInformation;<br>API declaration: signalType: NetworkType;<br>Differences: signalType: NetworkType;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: SignalInformation;<br>API declaration: signalLevel: number;<br>Differences: signalLevel: number;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: SignalInformation;<br>API declaration: dBm: number;<br>Differences: dBm: number;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: export enum NetworkType<br>Differences: export enum NetworkType|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkType;<br>API declaration: NETWORK_TYPE_UNKNOWN<br>Differences: NETWORK_TYPE_UNKNOWN|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkType;<br>API declaration: NETWORK_TYPE_GSM<br>Differences: NETWORK_TYPE_GSM|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkType;<br>API declaration: NETWORK_TYPE_CDMA<br>Differences: NETWORK_TYPE_CDMA|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkType;<br>API declaration: NETWORK_TYPE_WCDMA<br>Differences: NETWORK_TYPE_WCDMA|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkType;<br>API declaration: NETWORK_TYPE_TDSCDMA<br>Differences: NETWORK_TYPE_TDSCDMA|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkType;<br>API declaration: NETWORK_TYPE_LTE<br>Differences: NETWORK_TYPE_LTE|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkType;<br>API declaration: NETWORK_TYPE_NR<br>Differences: NETWORK_TYPE_NR|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: export interface NetworkState<br>Differences: export interface NetworkState|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkState;<br>API declaration: longOperatorName: string;<br>Differences: longOperatorName: string;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkState;<br>API declaration: shortOperatorName: string;<br>Differences: shortOperatorName: string;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkState;<br>API declaration: plmnNumeric: string;<br>Differences: plmnNumeric: string;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkState;<br>API declaration: isRoaming: boolean;<br>Differences: isRoaming: boolean;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkState;<br>API declaration: regState: RegState;<br>Differences: regState: RegState;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkState;<br>API declaration: cfgTech: RadioTechnology;<br>Differences: cfgTech: RadioTechnology;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkState;<br>API declaration: nsaState: NsaState;<br>Differences: nsaState: NsaState;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkState;<br>API declaration: isCaActive: boolean;<br>Differences: isCaActive: boolean;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkState;<br>API declaration: isEmergency: boolean;<br>Differences: isEmergency: boolean;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: export enum RegState<br>Differences: export enum RegState|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: RegState;<br>API declaration: REG_STATE_NO_SERVICE = 0<br>Differences: REG_STATE_NO_SERVICE = 0|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: RegState;<br>API declaration: REG_STATE_IN_SERVICE = 1<br>Differences: REG_STATE_IN_SERVICE = 1|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: RegState;<br>API declaration: REG_STATE_EMERGENCY_CALL_ONLY = 2<br>Differences: REG_STATE_EMERGENCY_CALL_ONLY = 2|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: RegState;<br>API declaration: REG_STATE_POWER_OFF = 3<br>Differences: REG_STATE_POWER_OFF = 3|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: export enum NsaState<br>Differences: export enum NsaState|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NsaState;<br>API declaration: NSA_STATE_NOT_SUPPORT = 1<br>Differences: NSA_STATE_NOT_SUPPORT = 1|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NsaState;<br>API declaration: NSA_STATE_NO_DETECT = 2<br>Differences: NSA_STATE_NO_DETECT = 2|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NsaState;<br>API declaration: NSA_STATE_CONNECTED_DETECT = 3<br>Differences: NSA_STATE_CONNECTED_DETECT = 3|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NsaState;<br>API declaration: NSA_STATE_IDLE_DETECT = 4<br>Differences: NSA_STATE_IDLE_DETECT = 4|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NsaState;<br>API declaration: NSA_STATE_DUAL_CONNECTED = 5<br>Differences: NSA_STATE_DUAL_CONNECTED = 5|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NsaState;<br>API declaration: NSA_STATE_SA_ATTACHED = 6<br>Differences: NSA_STATE_SA_ATTACHED = 6|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: export interface CellInformation<br>Differences: export interface CellInformation|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: CellInformation;<br>API declaration: networkType: NetworkType;<br>Differences: networkType: NetworkType;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: CellInformation;<br>API declaration: signalInformation: SignalInformation;<br>Differences: signalInformation: SignalInformation;|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: radio;<br>API declaration: export enum NetworkSelectionMode<br>Differences: export enum NetworkSelectionMode|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkSelectionMode;<br>API declaration: NETWORK_SELECTION_UNKNOWN<br>Differences: NETWORK_SELECTION_UNKNOWN|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkSelectionMode;<br>API declaration: NETWORK_SELECTION_AUTOMATIC<br>Differences: NETWORK_SELECTION_AUTOMATIC|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: NetworkSelectionMode;<br>API declaration: NETWORK_SELECTION_MANUAL<br>Differences: NETWORK_SELECTION_MANUAL|api/@ohos.telephony.radio.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace sim<br>Differences: declare namespace sim|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function isSimActive(slotId: number, callback: AsyncCallback\<boolean>): void;<br>Differences: function isSimActive(slotId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function isSimActive(slotId: number): Promise\<boolean>;<br>Differences: function isSimActive(slotId: number): Promise\<boolean>;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function isSimActiveSync(slotId: number): boolean;<br>Differences: function isSimActiveSync(slotId: number): boolean;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getDefaultVoiceSlotId(callback: AsyncCallback\<number>): void;<br>Differences: function getDefaultVoiceSlotId(callback: AsyncCallback\<number>): void;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getDefaultVoiceSlotId(): Promise\<number>;<br>Differences: function getDefaultVoiceSlotId(): Promise\<number>;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function hasOperatorPrivileges(slotId: number, callback: AsyncCallback\<boolean>): void;<br>Differences: function hasOperatorPrivileges(slotId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function hasOperatorPrivileges(slotId: number): Promise\<boolean>;<br>Differences: function hasOperatorPrivileges(slotId: number): Promise\<boolean>;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getISOCountryCodeForSim(slotId: number, callback: AsyncCallback\<string>): void;<br>Differences: function getISOCountryCodeForSim(slotId: number, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getISOCountryCodeForSim(slotId: number): Promise\<string>;<br>Differences: function getISOCountryCodeForSim(slotId: number): Promise\<string>;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getISOCountryCodeForSimSync(slotId: number): string;<br>Differences: function getISOCountryCodeForSimSync(slotId: number): string;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getSimOperatorNumeric(slotId: number, callback: AsyncCallback\<string>): void;<br>Differences: function getSimOperatorNumeric(slotId: number, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getSimOperatorNumeric(slotId: number): Promise\<string>;<br>Differences: function getSimOperatorNumeric(slotId: number): Promise\<string>;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getSimOperatorNumericSync(slotId: number): string;<br>Differences: function getSimOperatorNumericSync(slotId: number): string;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getSimSpn(slotId: number, callback: AsyncCallback\<string>): void;<br>Differences: function getSimSpn(slotId: number, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getSimSpn(slotId: number): Promise\<string>;<br>Differences: function getSimSpn(slotId: number): Promise\<string>;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getSimSpnSync(slotId: number): string;<br>Differences: function getSimSpnSync(slotId: number): string;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getSimState(slotId: number, callback: AsyncCallback\<SimState>): void;<br>Differences: function getSimState(slotId: number, callback: AsyncCallback\<SimState>): void;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getSimState(slotId: number): Promise\<SimState>;<br>Differences: function getSimState(slotId: number): Promise\<SimState>;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getSimStateSync(slotId: number): SimState;<br>Differences: function getSimStateSync(slotId: number): SimState;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getCardType(slotId: number, callback: AsyncCallback\<CardType>): void;<br>Differences: function getCardType(slotId: number, callback: AsyncCallback\<CardType>): void;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getCardType(slotId: number): Promise\<CardType>;<br>Differences: function getCardType(slotId: number): Promise\<CardType>;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getCardTypeSync(slotId: number): CardType;<br>Differences: function getCardTypeSync(slotId: number): CardType;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getMaxSimCount(): number;<br>Differences: function getMaxSimCount(): number;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function hasSimCard(slotId: number, callback: AsyncCallback\<boolean>): void;<br>Differences: function hasSimCard(slotId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function hasSimCard(slotId: number): Promise\<boolean>;<br>Differences: function hasSimCard(slotId: number): Promise\<boolean>;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function hasSimCardSync(slotId: number): boolean;<br>Differences: function hasSimCardSync(slotId: number): boolean;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getSimAccountInfo(slotId: number, callback: AsyncCallback\<IccAccountInfo>): void;<br>Differences: function getSimAccountInfo(slotId: number, callback: AsyncCallback\<IccAccountInfo>): void;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getSimAccountInfo(slotId: number): Promise\<IccAccountInfo>;<br>Differences: function getSimAccountInfo(slotId: number): Promise\<IccAccountInfo>;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getActiveSimAccountInfoList(callback: AsyncCallback\<Array\<IccAccountInfo>>): void;<br>Differences: function getActiveSimAccountInfoList(callback: AsyncCallback\<Array\<IccAccountInfo>>): void;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getActiveSimAccountInfoList(): Promise\<Array\<IccAccountInfo>>;<br>Differences: function getActiveSimAccountInfoList(): Promise\<Array\<IccAccountInfo>>;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getOpKey(slotId: number, callback: AsyncCallback\<string>): void;<br>Differences: function getOpKey(slotId: number, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getOpKey(slotId: number): Promise\<string>;<br>Differences: function getOpKey(slotId: number): Promise\<string>;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getOpKeySync(slotId: number): string;<br>Differences: function getOpKeySync(slotId: number): string;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getOpName(slotId: number, callback: AsyncCallback\<string>): void;<br>Differences: function getOpName(slotId: number, callback: AsyncCallback\<string>): void;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getOpName(slotId: number): Promise\<string>;<br>Differences: function getOpName(slotId: number): Promise\<string>;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getOpNameSync(slotId: number): string;<br>Differences: function getOpNameSync(slotId: number): string;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getDefaultVoiceSimId(callback: AsyncCallback\<number>): void;<br>Differences: function getDefaultVoiceSimId(callback: AsyncCallback\<number>): void;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getDefaultVoiceSimId(): Promise\<number>;<br>Differences: function getDefaultVoiceSimId(): Promise\<number>;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: export interface IccAccountInfo<br>Differences: export interface IccAccountInfo|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: IccAccountInfo;<br>API declaration: simId: number;<br>Differences: simId: number;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: IccAccountInfo;<br>API declaration: slotIndex: number;<br>Differences: slotIndex: number;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: IccAccountInfo;<br>API declaration: isEsim: boolean;<br>Differences: isEsim: boolean;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: IccAccountInfo;<br>API declaration: isActive: boolean;<br>Differences: isActive: boolean;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: IccAccountInfo;<br>API declaration: iccId: string;<br>Differences: iccId: string;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: IccAccountInfo;<br>API declaration: showName: string;<br>Differences: showName: string;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: IccAccountInfo;<br>API declaration: showNumber: string;<br>Differences: showNumber: string;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: export enum CardType<br>Differences: export enum CardType|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: CardType;<br>API declaration: UNKNOWN_CARD = -1<br>Differences: UNKNOWN_CARD = -1|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: CardType;<br>API declaration: SINGLE_MODE_SIM_CARD = 10<br>Differences: SINGLE_MODE_SIM_CARD = 10|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: CardType;<br>API declaration: SINGLE_MODE_USIM_CARD = 20<br>Differences: SINGLE_MODE_USIM_CARD = 20|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: CardType;<br>API declaration: SINGLE_MODE_RUIM_CARD = 30<br>Differences: SINGLE_MODE_RUIM_CARD = 30|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: CardType;<br>API declaration: DUAL_MODE_CG_CARD = 40<br>Differences: DUAL_MODE_CG_CARD = 40|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: CardType;<br>API declaration: CT_NATIONAL_ROAMING_CARD = 41<br>Differences: CT_NATIONAL_ROAMING_CARD = 41|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: CardType;<br>API declaration: CU_DUAL_MODE_CARD = 42<br>Differences: CU_DUAL_MODE_CARD = 42|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: CardType;<br>API declaration: DUAL_MODE_TELECOM_LTE_CARD = 43<br>Differences: DUAL_MODE_TELECOM_LTE_CARD = 43|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: CardType;<br>API declaration: DUAL_MODE_UG_CARD = 50<br>Differences: DUAL_MODE_UG_CARD = 50|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: CardType;<br>API declaration: SINGLE_MODE_ISIM_CARD = 60<br>Differences: SINGLE_MODE_ISIM_CARD = 60|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: export enum SimState<br>Differences: export enum SimState|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: SimState;<br>API declaration: SIM_STATE_UNKNOWN<br>Differences: SIM_STATE_UNKNOWN|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: SimState;<br>API declaration: SIM_STATE_NOT_PRESENT<br>Differences: SIM_STATE_NOT_PRESENT|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: SimState;<br>API declaration: SIM_STATE_LOCKED<br>Differences: SIM_STATE_LOCKED|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: SimState;<br>API declaration: SIM_STATE_NOT_READY<br>Differences: SIM_STATE_NOT_READY|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: SimState;<br>API declaration: SIM_STATE_READY<br>Differences: SIM_STATE_READY|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: SimState;<br>API declaration: SIM_STATE_LOADED<br>Differences: SIM_STATE_LOADED|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace sms<br>Differences: declare namespace sms|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: sms;<br>API declaration: function createMessage(pdu: Array\<number>, specification: string, callback: AsyncCallback\<ShortMessage>): void;<br>Differences: function createMessage(pdu: Array\<number>, specification: string, callback: AsyncCallback\<ShortMessage>): void;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: sms;<br>API declaration: function createMessage(pdu: Array\<number>, specification: string): Promise\<ShortMessage>;<br>Differences: function createMessage(pdu: Array\<number>, specification: string): Promise\<ShortMessage>;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: sms;<br>API declaration: function sendMessage(options: SendMessageOptions): void;<br>Differences: function sendMessage(options: SendMessageOptions): void;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: sms;<br>API declaration: function sendShortMessage(options: SendMessageOptions, callback: AsyncCallback\<void>): void;<br>Differences: function sendShortMessage(options: SendMessageOptions, callback: AsyncCallback\<void>): void;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: sms;<br>API declaration: function sendShortMessage(options: SendMessageOptions): Promise\<void>;<br>Differences: function sendShortMessage(options: SendMessageOptions): Promise\<void>;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: sms;<br>API declaration: function getDefaultSmsSlotId(callback: AsyncCallback\<number>): void;<br>Differences: function getDefaultSmsSlotId(callback: AsyncCallback\<number>): void;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: sms;<br>API declaration: function getDefaultSmsSlotId(): Promise\<number>;<br>Differences: function getDefaultSmsSlotId(): Promise\<number>;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: sms;<br>API declaration: function hasSmsCapability(): boolean;<br>Differences: function hasSmsCapability(): boolean;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: sms;<br>API declaration: function getDefaultSmsSimId(callback: AsyncCallback\<number>): void;<br>Differences: function getDefaultSmsSimId(callback: AsyncCallback\<number>): void;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: sms;<br>API declaration: function getDefaultSmsSimId(): Promise\<number>;<br>Differences: function getDefaultSmsSimId(): Promise\<number>;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: sms;<br>API declaration: export interface ShortMessage<br>Differences: export interface ShortMessage|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ShortMessage;<br>API declaration: visibleMessageBody: string;<br>Differences: visibleMessageBody: string;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ShortMessage;<br>API declaration: visibleRawAddress: string;<br>Differences: visibleRawAddress: string;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ShortMessage;<br>API declaration: messageClass: ShortMessageClass;<br>Differences: messageClass: ShortMessageClass;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ShortMessage;<br>API declaration: protocolId: number;<br>Differences: protocolId: number;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ShortMessage;<br>API declaration: scAddress: string;<br>Differences: scAddress: string;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ShortMessage;<br>API declaration: scTimestamp: number;<br>Differences: scTimestamp: number;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ShortMessage;<br>API declaration: isReplaceMessage: boolean;<br>Differences: isReplaceMessage: boolean;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ShortMessage;<br>API declaration: hasReplyPath: boolean;<br>Differences: hasReplyPath: boolean;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ShortMessage;<br>API declaration: pdu: Array\<number>;<br>Differences: pdu: Array\<number>;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ShortMessage;<br>API declaration: status: number;<br>Differences: status: number;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ShortMessage;<br>API declaration: isSmsStatusReportMessage: boolean;<br>Differences: isSmsStatusReportMessage: boolean;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: sms;<br>API declaration: export enum ShortMessageClass<br>Differences: export enum ShortMessageClass|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ShortMessageClass;<br>API declaration: UNKNOWN<br>Differences: UNKNOWN|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ShortMessageClass;<br>API declaration: INSTANT_MESSAGE<br>Differences: INSTANT_MESSAGE|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ShortMessageClass;<br>API declaration: OPTIONAL_MESSAGE<br>Differences: OPTIONAL_MESSAGE|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ShortMessageClass;<br>API declaration: SIM_MESSAGE<br>Differences: SIM_MESSAGE|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ShortMessageClass;<br>API declaration: FORWARD_MESSAGE<br>Differences: FORWARD_MESSAGE|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: sms;<br>API declaration: export interface SendMessageOptions<br>Differences: export interface SendMessageOptions|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: SendMessageOptions;<br>API declaration: slotId: number;<br>Differences: slotId: number;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: SendMessageOptions;<br>API declaration: destinationHost: string;<br>Differences: destinationHost: string;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: SendMessageOptions;<br>API declaration: serviceCenter?: string;<br>Differences: serviceCenter?: string;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: SendMessageOptions;<br>API declaration: content: string \| Array\<number>;<br>Differences: content: string \| Array\<number>;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: SendMessageOptions;<br>API declaration: destinationPort?: number;<br>Differences: destinationPort?: number;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: SendMessageOptions;<br>API declaration: sendCallback?: AsyncCallback\<ISendShortMessageCallback>;<br>Differences: sendCallback?: AsyncCallback\<ISendShortMessageCallback>;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: SendMessageOptions;<br>API declaration: deliveryCallback?: AsyncCallback\<IDeliveryShortMessageCallback>;<br>Differences: deliveryCallback?: AsyncCallback\<IDeliveryShortMessageCallback>;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: sms;<br>API declaration: export interface ISendShortMessageCallback<br>Differences: export interface ISendShortMessageCallback|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ISendShortMessageCallback;<br>API declaration: result: SendSmsResult;<br>Differences: result: SendSmsResult;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ISendShortMessageCallback;<br>API declaration: url: string;<br>Differences: url: string;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: ISendShortMessageCallback;<br>API declaration: isLastPart: boolean;<br>Differences: isLastPart: boolean;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: sms;<br>API declaration: export interface IDeliveryShortMessageCallback<br>Differences: export interface IDeliveryShortMessageCallback|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: IDeliveryShortMessageCallback;<br>API declaration: pdu: Array\<number>;<br>Differences: pdu: Array\<number>;|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: sms;<br>API declaration: export enum SendSmsResult<br>Differences: export enum SendSmsResult|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: SendSmsResult;<br>API declaration: SEND_SMS_SUCCESS = 0<br>Differences: SEND_SMS_SUCCESS = 0|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: SendSmsResult;<br>API declaration: SEND_SMS_FAILURE_UNKNOWN = 1<br>Differences: SEND_SMS_FAILURE_UNKNOWN = 1|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: SendSmsResult;<br>API declaration: SEND_SMS_FAILURE_RADIO_OFF = 2<br>Differences: SEND_SMS_FAILURE_RADIO_OFF = 2|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: SendSmsResult;<br>API declaration: SEND_SMS_FAILURE_SERVICE_UNAVAILABLE = 3<br>Differences: SEND_SMS_FAILURE_SERVICE_UNAVAILABLE = 3|api/@ohos.telephony.sms.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace vcard<br>Differences: declare namespace vcard|api/@ohos.telephony.vcard.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.telephony.call.d.ts<br>Differences: TelephonyKit|api/@ohos.telephony.call.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.telephony.data.d.ts<br>Differences: TelephonyKit|api/@ohos.telephony.data.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.telephony.observer.d.ts<br>Differences: TelephonyKit|api/@ohos.telephony.observer.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.telephony.radio.d.ts<br>Differences: TelephonyKit|api/@ohos.telephony.radio.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.telephony.sim.d.ts<br>Differences: TelephonyKit|api/@ohos.telephony.sim.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.telephony.sms.d.ts<br>Differences: TelephonyKit|api/@ohos.telephony.sms.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.telephony.vcard.d.ts<br>Differences: TelephonyKit|api/@ohos.telephony.vcard.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.TelephonyKit.d.ts<br>Differences: TelephonyKit|kits/@kit.TelephonyKit.d.ts|
