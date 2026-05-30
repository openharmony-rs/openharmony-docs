| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增错误码|类名：HceService；<br>API声明：on(type: 'hceCmd', callback: AsyncCallback\<number[]>): void;<br>差异内容：NA|类名：HceService；<br>API声明：on(type: 'hceCmd', callback: AsyncCallback\<number[]>): void;<br>差异内容：201,401,801|api/@ohos.nfc.cardEmulation.d.ts|
|删除错误码|类名：access；<br>API声明：function on(type: 'stateChange', callback: Callback\<BluetoothState>): void;<br>差异内容：201|类名：access；<br>API声明：function on(type: 'stateChange', callback: Callback\<BluetoothState>): void;<br>差异内容：NA|api/@ohos.bluetooth.access.d.ts|
|删除错误码|类名：access；<br>API声明：function off(type: 'stateChange', callback?: Callback\<BluetoothState>): void;<br>差异内容：201|类名：access；<br>API声明：function off(type: 'stateChange', callback?: Callback\<BluetoothState>): void;<br>差异内容：NA|api/@ohos.bluetooth.access.d.ts|
|删除错误码|类名：connection；<br>API声明：function getRemoteDeviceClass(deviceId: string): DeviceClass;<br>差异内容：201|类名：connection；<br>API声明：function getRemoteDeviceClass(deviceId: string): DeviceClass;<br>差异内容：NA|api/@ohos.bluetooth.connection.d.ts|
|权限变更|类名：access；<br>API声明：function on(type: 'stateChange', callback: Callback\<BluetoothState>): void;<br>差异内容：ohos.permission.ACCESS_BLUETOOTH|类名：access；<br>API声明：function on(type: 'stateChange', callback: Callback\<BluetoothState>): void;<br>差异内容：NA|api/@ohos.bluetooth.access.d.ts|
|权限变更|类名：access；<br>API声明：function off(type: 'stateChange', callback?: Callback\<BluetoothState>): void;<br>差异内容：ohos.permission.ACCESS_BLUETOOTH|类名：access；<br>API声明：function off(type: 'stateChange', callback?: Callback\<BluetoothState>): void;<br>差异内容：NA|api/@ohos.bluetooth.access.d.ts|
|权限变更|类名：connection；<br>API声明：function getRemoteDeviceClass(deviceId: string): DeviceClass;<br>差异内容：ohos.permission.ACCESS_BLUETOOTH|类名：connection；<br>API声明：function getRemoteDeviceClass(deviceId: string): DeviceClass;<br>差异内容：NA|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace opp<br>差异内容：declare namespace opp|api/@ohos.bluetooth.opp.d.ts|
|新增API|NA|类名：opp；<br>API声明：interface OppServerProfile<br>差异内容：interface OppServerProfile|api/@ohos.bluetooth.opp.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface BarcodeTag<br>差异内容：export interface BarcodeTag|api/tag/nfctech.d.ts|
|新增API|NA|类名：BarcodeTag；<br>API声明：getBarcode(): Promise\<ArrayBuffer>;<br>差异内容：getBarcode(): Promise\<ArrayBuffer>;|api/tag/nfctech.d.ts|
|新增API|NA|类名：access；<br>API声明：function addPersistentDeviceId(deviceId: string): Promise\<void>;<br>差异内容：function addPersistentDeviceId(deviceId: string): Promise\<void>;|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：access；<br>API声明：function deletePersistentDeviceId(deviceId: string): Promise\<void>;<br>差异内容：function deletePersistentDeviceId(deviceId: string): Promise\<void>;|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：access；<br>API声明：function getPersistentDeviceIds(): string[];<br>差异内容：function getPersistentDeviceIds(): string[];|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：access；<br>API声明：function isValidRandomDeviceId(deviceId: string): boolean;<br>差异内容：function isValidRandomDeviceId(deviceId: string): boolean;|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getRemoteDeviceName(deviceId: string, alias?: boolean): string;<br>差异内容：function getRemoteDeviceName(deviceId: string, alias?: boolean): string;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function connectAllowedProfiles(deviceId: string, callback: AsyncCallback\<void>): void;<br>差异内容：function connectAllowedProfiles(deviceId: string, callback: AsyncCallback\<void>): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function connectAllowedProfiles(deviceId: string): Promise\<void>;<br>差异内容：function connectAllowedProfiles(deviceId: string): Promise\<void>;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function on(type: 'discoveryResult', callback: Callback\<Array\<DiscoveryResult>>): void;<br>差异内容：function on(type: 'discoveryResult', callback: Callback\<Array\<DiscoveryResult>>): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function off(type: 'discoveryResult', callback?: Callback\<Array\<DiscoveryResult>>): void;<br>差异内容：function off(type: 'discoveryResult', callback?: Callback\<Array\<DiscoveryResult>>): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：interface DiscoveryResult<br>差异内容：interface DiscoveryResult|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：DiscoveryResult；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：DiscoveryResult；<br>API声明：rssi: number;<br>差异内容：rssi: number;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：DiscoveryResult；<br>API声明：deviceName: string;<br>差异内容：deviceName: string;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：DiscoveryResult；<br>API声明：deviceClass: DeviceClass;<br>差异内容：deviceClass: DeviceClass;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：HceService；<br>API声明：off(type: 'hceCmd', callback?: AsyncCallback\<number[]>): void;<br>差异内容：off(type: 'hceCmd', callback?: AsyncCallback\<number[]>): void;|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getMultiLinkedInfo(): Array\<WifiLinkedInfo>;<br>差异内容：function getMultiLinkedInfo(): Array\<WifiLinkedInfo>;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getLinkedInfoSync(): WifiLinkedInfo;<br>差异内容：function getLinkedInfoSync(): WifiLinkedInfo;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：enum WifiLinkType<br>差异内容：enum WifiLinkType|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkType；<br>API声明：DEFAULT_LINK = 0<br>差异内容：DEFAULT_LINK = 0|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkType；<br>API声明：WIFI7_SINGLE_LINK = 1<br>差异内容：WIFI7_SINGLE_LINK = 1|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkType；<br>API声明：WIFI7_MLSR = 2<br>差异内容：WIFI7_MLSR = 2|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkType；<br>API声明：WIFI7_EMLSR = 3<br>差异内容：WIFI7_EMLSR = 3|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkType；<br>API声明：WIFI7_STR = 4<br>差异内容：WIFI7_STR = 4|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：wifiLinkType?: WifiLinkType;<br>差异内容：wifiLinkType?: WifiLinkType;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：BLECharacteristic；<br>API声明：characteristicValueHandle?: number;<br>差异内容：characteristicValueHandle?: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BLEDescriptor；<br>API声明：descriptorHandle?: number;<br>差异内容：descriptorHandle?: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertiseData；<br>API声明：includeTxPower?: boolean;<br>差异内容：includeTxPower?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanReportMode；<br>API声明：FENCE_SENSITIVITY_LOW = 10<br>差异内容：FENCE_SENSITIVITY_LOW = 10|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanReportMode；<br>API声明：FENCE_SENSITIVITY_HIGH = 11<br>差异内容：FENCE_SENSITIVITY_HIGH = 11|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：socket；<br>API声明：function getDeviceId(clientSocket: number): string;<br>差异内容：function getDeviceId(clientSocket: number): string;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function sppWriteAsync(clientSocket: number, data: ArrayBuffer): Promise\<void>;<br>差异内容：function sppWriteAsync(clientSocket: number, data: ArrayBuffer): Promise\<void>;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function sppReadAsync(clientSocket: number): Promise\<ArrayBuffer>;<br>差异内容：function sppReadAsync(clientSocket: number): Promise\<ArrayBuffer>;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：tag；<br>API声明：const NFC_BARCODE = 10;<br>差异内容：const NFC_BARCODE = 10;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function getBarcodeTag(tagInfo: TagInfo): BarcodeTag;<br>差异内容：function getBarcodeTag(tagInfo: TagInfo): BarcodeTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：ndef；<br>API声明：function makeApplicationRecord(bundleName: string): NdefRecord;<br>差异内容：function makeApplicationRecord(bundleName: string): NdefRecord;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：export type BarcodeTag = _BarcodeTag;<br>差异内容：export type BarcodeTag = _BarcodeTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：omapi；<br>API声明：function on(type: 'stateChanged', callback: Callback\<ServiceState>): void;<br>差异内容：function on(type: 'stateChanged', callback: Callback\<ServiceState>): void;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：omapi；<br>API声明：function off(type: 'stateChanged', callback?: Callback\<ServiceState>): void;<br>差异内容：function off(type: 'stateChanged', callback?: Callback\<ServiceState>): void;|api/@ohos.secureElement.d.ts|
|起始版本有变化|类名：connection；<br>API声明：type ProfileUuids = constant.ProfileUuids;<br>差异内容：10|类名：connection；<br>API声明：type ProfileUuids = constant.ProfileUuids;<br>差异内容：12|api/@ohos.bluetooth.connection.d.ts|
|起始版本有变化|类名：connection；<br>API声明：function getRemoteProfileUuids(deviceId: string, callback: AsyncCallback\<Array\<ProfileUuids>>): void;<br>差异内容：10|类名：connection；<br>API声明：function getRemoteProfileUuids(deviceId: string, callback: AsyncCallback\<Array\<ProfileUuids>>): void;<br>差异内容：12|api/@ohos.bluetooth.connection.d.ts|
|起始版本有变化|类名：connection；<br>API声明：function getRemoteProfileUuids(deviceId: string): Promise\<Array\<ProfileUuids>>;<br>差异内容：10|类名：connection；<br>API声明：function getRemoteProfileUuids(deviceId: string): Promise\<Array\<ProfileUuids>>;<br>差异内容：12|api/@ohos.bluetooth.connection.d.ts|
|起始版本有变化|类名：constant；<br>API声明：export enum ProfileUuids<br>差异内容：10|类名：constant；<br>API声明：export enum ProfileUuids<br>差异内容：12|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HFP_AG = '0000111F-0000-1000-8000-00805F9B34FB'<br>差异内容：10|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HFP_AG = '0000111F-0000-1000-8000-00805F9B34FB'<br>差异内容：12|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HFP_HF = '0000111E-0000-1000-8000-00805F9B34FB'<br>差异内容：10|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HFP_HF = '0000111E-0000-1000-8000-00805F9B34FB'<br>差异内容：12|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HSP_AG = '00001112-0000-1000-8000-00805F9B34FB'<br>差异内容：10|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HSP_AG = '00001112-0000-1000-8000-00805F9B34FB'<br>差异内容：12|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HSP_HS = '00001108-0000-1000-8000-00805F9B34FB'<br>差异内容：10|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HSP_HS = '00001108-0000-1000-8000-00805F9B34FB'<br>差异内容：12|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_A2DP_SRC = '0000110A-0000-1000-8000-00805F9B34FB'<br>差异内容：10|类名：ProfileUuids；<br>API声明：PROFILE_UUID_A2DP_SRC = '0000110A-0000-1000-8000-00805F9B34FB'<br>差异内容：12|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_A2DP_SINK = '0000110B-0000-1000-8000-00805F9B34FB'<br>差异内容：10|类名：ProfileUuids；<br>API声明：PROFILE_UUID_A2DP_SINK = '0000110B-0000-1000-8000-00805F9B34FB'<br>差异内容：12|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_AVRCP_CT = '0000110E-0000-1000-8000-00805F9B34FB'<br>差异内容：10|类名：ProfileUuids；<br>API声明：PROFILE_UUID_AVRCP_CT = '0000110E-0000-1000-8000-00805F9B34FB'<br>差异内容：12|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_AVRCP_TG = '0000110C-0000-1000-8000-00805F9B34FB'<br>差异内容：10|类名：ProfileUuids；<br>API声明：PROFILE_UUID_AVRCP_TG = '0000110C-0000-1000-8000-00805F9B34FB'<br>差异内容：12|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HID = '00001124-0000-1000-8000-00805F9B34FB'<br>差异内容：10|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HID = '00001124-0000-1000-8000-00805F9B34FB'<br>差异内容：12|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HOGP = '00001812-0000-1000-8000-00805F9B34FB'<br>差异内容：10|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HOGP = '00001812-0000-1000-8000-00805F9B34FB'<br>差异内容：12|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：wifiManager；<br>API声明：function isHotspotActive(): boolean;<br>差异内容：9|类名：wifiManager；<br>API声明：function isHotspotActive(): boolean;<br>差异内容：15|api/@ohos.wifiManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bluetooth.opp.d.ts<br>差异内容：ConnectivityKit|api/@ohos.bluetooth.opp.d.ts|
|新增导出符号|类名：global；<br>API声明：export interface BarcodeTag<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export interface BarcodeTag|api/tag/nfctech.d.ts|
