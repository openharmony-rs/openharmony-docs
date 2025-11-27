| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增错误码|类名：ble；<br>API声明：function startAdvertising(setting: AdvertiseSetting, advData: AdvertiseData, advResponse?: AdvertiseData): void;<br>差异内容：NA|类名：ble；<br>API声明：function startAdvertising(setting: AdvertiseSetting, advData: AdvertiseData, advResponse?: AdvertiseData): void;<br>差异内容：2900010,2902054|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：ble；<br>API声明：function startAdvertising(advertisingParams: AdvertisingParams, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：ble；<br>API声明：function startAdvertising(advertisingParams: AdvertisingParams, callback: AsyncCallback\<number>): void;<br>差异内容：2900010,2902054|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：ble；<br>API声明：function startAdvertising(advertisingParams: AdvertisingParams): Promise\<number>;<br>差异内容：NA|类名：ble；<br>API声明：function startAdvertising(advertisingParams: AdvertisingParams): Promise\<number>;<br>差异内容：2900010,2902054|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：ble；<br>API声明：function stopAdvertising(advertisingId: number, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：ble；<br>API声明：function stopAdvertising(advertisingId: number, callback: AsyncCallback\<void>): void;<br>差异内容：2902055|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：ble；<br>API声明：function stopAdvertising(advertisingId: number): Promise\<void>;<br>差异内容：NA|类名：ble；<br>API声明：function stopAdvertising(advertisingId: number): Promise\<void>;<br>差异内容：2902055|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：ble；<br>API声明：function enableAdvertising(advertisingEnableParams: AdvertisingEnableParams, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：ble；<br>API声明：function enableAdvertising(advertisingEnableParams: AdvertisingEnableParams, callback: AsyncCallback\<void>): void;<br>差异内容：2902055|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：ble；<br>API声明：function enableAdvertising(advertisingEnableParams: AdvertisingEnableParams): Promise\<void>;<br>差异内容：NA|类名：ble；<br>API声明：function enableAdvertising(advertisingEnableParams: AdvertisingEnableParams): Promise\<void>;<br>差异内容：2902055|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：ble；<br>API声明：function disableAdvertising(advertisingDisableParams: AdvertisingDisableParams, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：ble；<br>API声明：function disableAdvertising(advertisingDisableParams: AdvertisingDisableParams, callback: AsyncCallback\<void>): void;<br>差异内容：2902055|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：ble；<br>API声明：function disableAdvertising(advertisingDisableParams: AdvertisingDisableParams): Promise\<void>;<br>差异内容：NA|类名：ble；<br>API声明：function disableAdvertising(advertisingDisableParams: AdvertisingDisableParams): Promise\<void>;<br>差异内容：2902055|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：GattClientDevice；<br>API声明：readCharacteristicValue(characteristic: BLECharacteristic, callback: AsyncCallback\<BLECharacteristic>): void;<br>差异内容：NA|类名：GattClientDevice；<br>API声明：readCharacteristicValue(characteristic: BLECharacteristic, callback: AsyncCallback\<BLECharacteristic>): void;<br>差异内容：2900011,2901003,2901004,2901005,2901006,2901007|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：GattClientDevice；<br>API声明：readCharacteristicValue(characteristic: BLECharacteristic): Promise\<BLECharacteristic>;<br>差异内容：NA|类名：GattClientDevice；<br>API声明：readCharacteristicValue(characteristic: BLECharacteristic): Promise\<BLECharacteristic>;<br>差异内容：2900011,2901003,2901004,2901005,2901006,2901007|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：GattClientDevice；<br>API声明：readDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback\<BLEDescriptor>): void;<br>差异内容：NA|类名：GattClientDevice；<br>API声明：readDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback\<BLEDescriptor>): void;<br>差异内容：2900011,2901003,2901004,2901005,2901006,2901007|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：GattClientDevice；<br>API声明：readDescriptorValue(descriptor: BLEDescriptor): Promise\<BLEDescriptor>;<br>差异内容：NA|类名：GattClientDevice；<br>API声明：readDescriptorValue(descriptor: BLEDescriptor): Promise\<BLEDescriptor>;<br>差异内容：2900011,2901003,2901004,2901005,2901006,2901007|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：GattClientDevice；<br>API声明：writeCharacteristicValue(characteristic: BLECharacteristic, writeType: GattWriteType, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：GattClientDevice；<br>API声明：writeCharacteristicValue(characteristic: BLECharacteristic, writeType: GattWriteType, callback: AsyncCallback\<void>): void;<br>差异内容：2900011,2901003,2901004,2901005,2901006,2901007|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：GattClientDevice；<br>API声明：writeCharacteristicValue(characteristic: BLECharacteristic, writeType: GattWriteType): Promise\<void>;<br>差异内容：NA|类名：GattClientDevice；<br>API声明：writeCharacteristicValue(characteristic: BLECharacteristic, writeType: GattWriteType): Promise\<void>;<br>差异内容：2900011,2901003,2901004,2901005,2901006,2901007|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：GattClientDevice；<br>API声明：writeDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：GattClientDevice；<br>API声明：writeDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback\<void>): void;<br>差异内容：2900011,2901003,2901004,2901005,2901006,2901007|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：GattClientDevice；<br>API声明：writeDescriptorValue(descriptor: BLEDescriptor): Promise\<void>;<br>差异内容：NA|类名：GattClientDevice；<br>API声明：writeDescriptorValue(descriptor: BLEDescriptor): Promise\<void>;<br>差异内容：2900011,2901003,2901004,2901005,2901006,2901007|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：GattClientDevice；<br>API声明：getRssiValue(callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：GattClientDevice；<br>API声明：getRssiValue(callback: AsyncCallback\<number>): void;<br>差异内容：2900011,2901003|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：GattClientDevice；<br>API声明：getRssiValue(): Promise\<number>;<br>差异内容：NA|类名：GattClientDevice；<br>API声明：getRssiValue(): Promise\<number>;<br>差异内容：2900011,2901003|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：GattClientDevice；<br>API声明：setCharacteristicChangeNotification(characteristic: BLECharacteristic, enable: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：GattClientDevice；<br>API声明：setCharacteristicChangeNotification(characteristic: BLECharacteristic, enable: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：2900011,2901003|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：GattClientDevice；<br>API声明：setCharacteristicChangeNotification(characteristic: BLECharacteristic, enable: boolean): Promise\<void>;<br>差异内容：NA|类名：GattClientDevice；<br>API声明：setCharacteristicChangeNotification(characteristic: BLECharacteristic, enable: boolean): Promise\<void>;<br>差异内容：2900011,2901003|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：GattClientDevice；<br>API声明：setCharacteristicChangeIndication(characteristic: BLECharacteristic, enable: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：GattClientDevice；<br>API声明：setCharacteristicChangeIndication(characteristic: BLECharacteristic, enable: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：2900011,2901003|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：GattClientDevice；<br>API声明：setCharacteristicChangeIndication(characteristic: BLECharacteristic, enable: boolean): Promise\<void>;<br>差异内容：NA|类名：GattClientDevice；<br>API声明：setCharacteristicChangeIndication(characteristic: BLECharacteristic, enable: boolean): Promise\<void>;<br>差异内容：2900011,2901003|api/@ohos.bluetooth.ble.d.ts|
|新增错误码|类名：HceService；<br>API声明：on(type: 'hceCmd', callback: AsyncCallback\<number[]>): void;<br>差异内容：NA|类名：HceService；<br>API声明：on(type: 'hceCmd', callback: AsyncCallback\<number[]>): void;<br>差异内容：201,401,801|api/@ohos.nfc.cardEmulation.d.ts|
|删除错误码|类名：access；<br>API声明：function on(type: 'stateChange', callback: Callback\<BluetoothState>): void;<br>差异内容：201|类名：access；<br>API声明：function on(type: 'stateChange', callback: Callback\<BluetoothState>): void;<br>差异内容：NA|api/@ohos.bluetooth.access.d.ts|
|删除错误码|类名：access；<br>API声明：function off(type: 'stateChange', callback?: Callback\<BluetoothState>): void;<br>差异内容：201|类名：access；<br>API声明：function off(type: 'stateChange', callback?: Callback\<BluetoothState>): void;<br>差异内容：NA|api/@ohos.bluetooth.access.d.ts|
|删除错误码|类名：connection；<br>API声明：function getRemoteDeviceClass(deviceId: string): DeviceClass;<br>差异内容：201|类名：connection；<br>API声明：function getRemoteDeviceClass(deviceId: string): DeviceClass;<br>差异内容：NA|api/@ohos.bluetooth.connection.d.ts|
|删除错误码|类名：wifiManager；<br>API声明：function on(type: 'hotspotStateChange', callback: Callback\<number>): void;<br>差异内容：202|类名：wifiManager；<br>API声明：function on(type: 'hotspotStateChange', callback: Callback\<number>): void;<br>差异内容：NA|api/@ohos.wifiManager.d.ts|
|删除错误码|类名：wifiManager；<br>API声明：function off(type: 'hotspotStateChange', callback?: Callback\<number>): void;<br>差异内容：202|类名：wifiManager；<br>API声明：function off(type: 'hotspotStateChange', callback?: Callback\<number>): void;<br>差异内容：NA|api/@ohos.wifiManager.d.ts|
|权限变更|类名：access；<br>API声明：function on(type: 'stateChange', callback: Callback\<BluetoothState>): void;<br>差异内容：ohos.permission.ACCESS_BLUETOOTH|类名：access；<br>API声明：function on(type: 'stateChange', callback: Callback\<BluetoothState>): void;<br>差异内容：NA|api/@ohos.bluetooth.access.d.ts|
|权限变更|类名：access；<br>API声明：function off(type: 'stateChange', callback?: Callback\<BluetoothState>): void;<br>差异内容：ohos.permission.ACCESS_BLUETOOTH|类名：access；<br>API声明：function off(type: 'stateChange', callback?: Callback\<BluetoothState>): void;<br>差异内容：NA|api/@ohos.bluetooth.access.d.ts|
|权限变更|类名：connection；<br>API声明：function getRemoteDeviceClass(deviceId: string): DeviceClass;<br>差异内容：ohos.permission.ACCESS_BLUETOOTH|类名：connection；<br>API声明：function getRemoteDeviceClass(deviceId: string): DeviceClass;<br>差异内容：NA|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace opp<br>差异内容：declare namespace opp|api/@ohos.bluetooth.opp.d.ts|
|新增API|NA|类名：opp；<br>API声明：interface OppServerProfile<br>差异内容：interface OppServerProfile|api/@ohos.bluetooth.opp.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface BarcodeTag<br>差异内容：export interface BarcodeTag|api/tag/nfctech.d.ts|
|新增API|NA|类名：BarcodeTag；<br>API声明：getBarcode(): Promise\<ArrayBuffer>;<br>差异内容：getBarcode(): Promise\<ArrayBuffer>;|api/tag/nfctech.d.ts|
|新增API|NA|类名：access；<br>API声明：function enableBluetoothAsync(): Promise\<void>;<br>差异内容：function enableBluetoothAsync(): Promise\<void>;|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：access；<br>API声明：function disableBluetoothAsync(): Promise\<void>;<br>差异内容：function disableBluetoothAsync(): Promise\<void>;|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：access；<br>API声明：function addPersistentDeviceId(deviceId: string): Promise\<void>;<br>差异内容：function addPersistentDeviceId(deviceId: string): Promise\<void>;|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：access；<br>API声明：function deletePersistentDeviceId(deviceId: string): Promise\<void>;<br>差异内容：function deletePersistentDeviceId(deviceId: string): Promise\<void>;|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：access；<br>API声明：function getPersistentDeviceIds(): string[];<br>差异内容：function getPersistentDeviceIds(): string[];|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：access；<br>API声明：function isValidRandomDeviceId(deviceId: string): boolean;<br>差异内容：function isValidRandomDeviceId(deviceId: string): boolean;|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：ble；<br>API声明：function createBleScanner(): BleScanner;<br>差异内容：function createBleScanner(): BleScanner;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface BleScanner<br>差异内容：interface BleScanner|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BleScanner；<br>API声明：startScan(filters: Array\<ScanFilter>, options?: ScanOptions): Promise\<void>;<br>差异内容：startScan(filters: Array\<ScanFilter>, options?: ScanOptions): Promise\<void>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BleScanner；<br>API声明：stopScan(): Promise\<void>;<br>差异内容：stopScan(): Promise\<void>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BleScanner；<br>API声明：on(type: 'BLEDeviceFind', callback: Callback\<ScanReport>): void;<br>差异内容：on(type: 'BLEDeviceFind', callback: Callback\<ScanReport>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BleScanner；<br>API声明：off(type: 'BLEDeviceFind', callback?: Callback\<ScanReport>): void;<br>差异内容：off(type: 'BLEDeviceFind', callback?: Callback\<ScanReport>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BLECharacteristic；<br>API声明：characteristicValueHandle?: number;<br>差异内容：characteristicValueHandle?: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BLECharacteristic；<br>API声明：permissions?: GattPermissions;<br>差异内容：permissions?: GattPermissions;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BLEDescriptor；<br>API声明：descriptorHandle?: number;<br>差异内容：descriptorHandle?: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BLEDescriptor；<br>API声明：permissions?: GattPermissions;<br>差异内容：permissions?: GattPermissions;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BLEConnectionChangeState；<br>API声明：reason?: GattDisconnectReason;<br>差异内容：reason?: GattDisconnectReason;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface ScanReport<br>差异内容：interface ScanReport|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanReport；<br>API声明：reportType: ScanReportType;<br>差异内容：reportType: ScanReportType;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanReport；<br>API声明：scanResult: Array\<ScanResult>;<br>差异内容：scanResult: Array\<ScanResult>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertiseData；<br>API声明：includeTxPower?: boolean;<br>差异内容：includeTxPower?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanOptions；<br>API声明：reportMode?: ScanReportMode;<br>差异内容：reportMode?: ScanReportMode;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattProperties；<br>API声明：broadcast?: boolean;<br>差异内容：broadcast?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattProperties；<br>API声明：authenticatedSignedWrite?: boolean;<br>差异内容：authenticatedSignedWrite?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattProperties；<br>API声明：extendedProperties?: boolean;<br>差异内容：extendedProperties?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：enum ScanReportMode<br>差异内容：enum ScanReportMode|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanReportMode；<br>API声明：NORMAL = 1<br>差异内容：NORMAL = 1|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanReportMode；<br>API声明：BATCH = 2<br>差异内容：BATCH = 2|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanReportMode；<br>API声明：FENCE_SENSITIVITY_LOW = 10<br>差异内容：FENCE_SENSITIVITY_LOW = 10|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanReportMode；<br>API声明：FENCE_SENSITIVITY_HIGH = 11<br>差异内容：FENCE_SENSITIVITY_HIGH = 11|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：enum ScanReportType<br>差异内容：enum ScanReportType|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanReportType；<br>API声明：ON_FOUND = 1<br>差异内容：ON_FOUND = 1|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanReportType；<br>API声明：ON_LOST = 2<br>差异内容：ON_LOST = 2|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanReportType；<br>API声明：ON_BATCH = 3<br>差异内容：ON_BATCH = 3|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：enum GattDisconnectReason<br>差异内容：enum GattDisconnectReason|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattDisconnectReason；<br>API声明：CONN_TIMEOUT = 1<br>差异内容：CONN_TIMEOUT = 1|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattDisconnectReason；<br>API声明：CONN_TERMINATE_PEER_USER = 2<br>差异内容：CONN_TERMINATE_PEER_USER = 2|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattDisconnectReason；<br>API声明：CONN_TERMINATE_LOCAL_HOST = 3<br>差异内容：CONN_TERMINATE_LOCAL_HOST = 3|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattDisconnectReason；<br>API声明：CONN_UNKNOWN = 4<br>差异内容：CONN_UNKNOWN = 4|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface GattPermissions<br>差异内容：interface GattPermissions|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattPermissions；<br>API声明：read?: boolean;<br>差异内容：read?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattPermissions；<br>API声明：readEncrypted?: boolean;<br>差异内容：readEncrypted?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattPermissions；<br>API声明：readEncryptedMitm?: boolean;<br>差异内容：readEncryptedMitm?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattPermissions；<br>API声明：write?: boolean;<br>差异内容：write?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattPermissions；<br>API声明：writeEncrypted?: boolean;<br>差异内容：writeEncrypted?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattPermissions；<br>API声明：writeEncryptedMitm?: boolean;<br>差异内容：writeEncryptedMitm?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattPermissions；<br>API声明：writeSigned?: boolean;<br>差异内容：writeSigned?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattPermissions；<br>API声明：writeSignedMitm?: boolean;<br>差异内容：writeSignedMitm?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getRemoteDeviceName(deviceId: string, alias?: boolean): string;<br>差异内容：function getRemoteDeviceName(deviceId: string, alias?: boolean): string;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getRemoteDeviceTransport(deviceId: string): BluetoothTransport;<br>差异内容：function getRemoteDeviceTransport(deviceId: string): BluetoothTransport;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function connectAllowedProfiles(deviceId: string, callback: AsyncCallback\<void>): void;<br>差异内容：function connectAllowedProfiles(deviceId: string, callback: AsyncCallback\<void>): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function connectAllowedProfiles(deviceId: string): Promise\<void>;<br>差异内容：function connectAllowedProfiles(deviceId: string): Promise\<void>;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getLastConnectionTime(deviceId: string): Promise\<number>;<br>差异内容：function getLastConnectionTime(deviceId: string): Promise\<number>;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function on(type: 'discoveryResult', callback: Callback\<Array\<DiscoveryResult>>): void;<br>差异内容：function on(type: 'discoveryResult', callback: Callback\<Array\<DiscoveryResult>>): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function off(type: 'discoveryResult', callback?: Callback\<Array\<DiscoveryResult>>): void;<br>差异内容：function off(type: 'discoveryResult', callback?: Callback\<Array\<DiscoveryResult>>): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：BluetoothTransport；<br>API声明：TRANSPORT_DUAL = 2<br>差异内容：TRANSPORT_DUAL = 2|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：BluetoothTransport；<br>API声明：TRANSPORT_UNKNOWN = 3<br>差异内容：TRANSPORT_UNKNOWN = 3|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：interface DiscoveryResult<br>差异内容：interface DiscoveryResult|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：DiscoveryResult；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：DiscoveryResult；<br>API声明：rssi: number;<br>差异内容：rssi: number;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：DiscoveryResult；<br>API声明：deviceName: string;<br>差异内容：deviceName: string;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：DiscoveryResult；<br>API声明：deviceClass: DeviceClass;<br>差异内容：deviceClass: DeviceClass;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：HceService；<br>API声明：off(type: 'hceCmd', callback?: AsyncCallback\<number[]>): void;<br>差异内容：off(type: 'hceCmd', callback?: AsyncCallback\<number[]>): void;|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function enableWifi(): void;<br>差异内容：function enableWifi(): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function disableWifi(): void;<br>差异内容：function disableWifi(): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function addDeviceConfig(config: WifiDeviceConfig): Promise\<number>;<br>差异内容：function addDeviceConfig(config: WifiDeviceConfig): Promise\<number>;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function addDeviceConfig(config: WifiDeviceConfig, callback: AsyncCallback\<number>): void;<br>差异内容：function addDeviceConfig(config: WifiDeviceConfig, callback: AsyncCallback\<number>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function connectToCandidateConfigWithUserAction(networkId: number): Promise\<void>;<br>差异内容：function connectToCandidateConfigWithUserAction(networkId: number): Promise\<void>;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function connectToNetwork(networkId: number): void;<br>差异内容：function connectToNetwork(networkId: number): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function disconnect(): void;<br>差异内容：function disconnect(): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getMultiLinkedInfo(): Array\<WifiLinkedInfo>;<br>差异内容：function getMultiLinkedInfo(): Array\<WifiLinkedInfo>;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getLinkedInfoSync(): WifiLinkedInfo;<br>差异内容：function getLinkedInfoSync(): WifiLinkedInfo;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getDeviceMacAddress(): string[];<br>差异内容：function getDeviceMacAddress(): string[];|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getDeviceConfigs(): Array\<WifiDeviceConfig>;<br>差异内容：function getDeviceConfigs(): Array\<WifiDeviceConfig>;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function removeDevice(id: number): void;<br>差异内容：function removeDevice(id: number): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function isHotspotActive(): boolean;<br>差异内容：function isHotspotActive(): boolean;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiCategory；<br>API声明：WIFI7 = 4<br>差异内容：WIFI7 = 4|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiCategory；<br>API声明：WIFI7_PLUS = 5<br>差异内容：WIFI7_PLUS = 5|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：enum WifiLinkType<br>差异内容：enum WifiLinkType|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkType；<br>API声明：DEFAULT_LINK = 0<br>差异内容：DEFAULT_LINK = 0|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkType；<br>API声明：WIFI7_SINGLE_LINK = 1<br>差异内容：WIFI7_SINGLE_LINK = 1|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkType；<br>API声明：WIFI7_MLSR = 2<br>差异内容：WIFI7_MLSR = 2|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkType；<br>API声明：WIFI7_EMLSR = 3<br>差异内容：WIFI7_EMLSR = 3|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkType；<br>API声明：WIFI7_STR = 4<br>差异内容：WIFI7_STR = 4|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：wifiLinkType?: WifiLinkType;<br>差异内容：wifiLinkType?: WifiLinkType;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：CodecInfo；<br>API声明：codecBitRate?: CodecBitRate;<br>差异内容：codecBitRate?: CodecBitRate;|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecInfo；<br>API声明：codecFrameLength?: CodecFrameLength;<br>差异内容：codecFrameLength?: CodecFrameLength;|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：a2dp；<br>API声明：interface CodecInfoList<br>差异内容：interface CodecInfoList|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecInfoList；<br>API声明：codecType: CodecType;<br>差异内容：codecType: CodecType;|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecInfoList；<br>API声明：codecBitsPerSampleArray: CodecBitsPerSample[];<br>差异内容：codecBitsPerSampleArray: CodecBitsPerSample[];|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecInfoList；<br>API声明：codecChannelModeArray: CodecChannelMode[];<br>差异内容：codecChannelModeArray: CodecChannelMode[];|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecInfoList；<br>API声明：codecSampleRateArray: CodecSampleRate[];<br>差异内容：codecSampleRateArray: CodecSampleRate[];|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecInfoList；<br>API声明：codecBitRateArray: CodecBitRate[];<br>差异内容：codecBitRateArray: CodecBitRate[];|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecInfoList；<br>API声明：codecFrameLengthArray: CodecFrameLength[];<br>差异内容：codecFrameLengthArray: CodecFrameLength[];|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：a2dp；<br>API声明：enum CodecBitRate<br>差异内容：enum CodecBitRate|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecBitRate；<br>API声明：CODEC_BIT_RATE_96000 = 0<br>差异内容：CODEC_BIT_RATE_96000 = 0|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecBitRate；<br>API声明：CODEC_BIT_RATE_128000 = 1<br>差异内容：CODEC_BIT_RATE_128000 = 1|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecBitRate；<br>API声明：CODEC_BIT_RATE_192000 = 2<br>差异内容：CODEC_BIT_RATE_192000 = 2|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecBitRate；<br>API声明：CODEC_BIT_RATE_256000 = 3<br>差异内容：CODEC_BIT_RATE_256000 = 3|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecBitRate；<br>API声明：CODEC_BIT_RATE_320000 = 4<br>差异内容：CODEC_BIT_RATE_320000 = 4|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecBitRate；<br>API声明：CODEC_BIT_RATE_480000 = 5<br>差异内容：CODEC_BIT_RATE_480000 = 5|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecBitRate；<br>API声明：CODEC_BIT_RATE_640000 = 6<br>差异内容：CODEC_BIT_RATE_640000 = 6|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecBitRate；<br>API声明：CODEC_BIT_RATE_960000 = 7<br>差异内容：CODEC_BIT_RATE_960000 = 7|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecBitRate；<br>API声明：CODEC_BIT_RATE_ABR = 8<br>差异内容：CODEC_BIT_RATE_ABR = 8|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：a2dp；<br>API声明：enum CodecFrameLength<br>差异内容：enum CodecFrameLength|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecFrameLength；<br>API声明：CODEC_FRAME_LENGTH_5MS = 0<br>差异内容：CODEC_FRAME_LENGTH_5MS = 0|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecFrameLength；<br>API声明：CODEC_FRAME_LENGTH_10MS = 1<br>差异内容：CODEC_FRAME_LENGTH_10MS = 1|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：socket；<br>API声明：function getL2capPsm(serverSocket: number): number;<br>差异内容：function getL2capPsm(serverSocket: number): number;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function getDeviceId(clientSocket: number): string;<br>差异内容：function getDeviceId(clientSocket: number): string;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function sppWriteAsync(clientSocket: number, data: ArrayBuffer): Promise\<void>;<br>差异内容：function sppWriteAsync(clientSocket: number, data: ArrayBuffer): Promise\<void>;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function sppReadAsync(clientSocket: number): Promise\<ArrayBuffer>;<br>差异内容：function sppReadAsync(clientSocket: number): Promise\<ArrayBuffer>;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：SppOptions；<br>API声明：psm?: number;<br>差异内容：psm?: number;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：SppType；<br>API声明：SPP_L2CAP = 1<br>差异内容：SPP_L2CAP = 1|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：SppType；<br>API声明：SPP_L2CAP_BLE = 2<br>差异内容：SPP_L2CAP_BLE = 2|api/@ohos.bluetooth.socket.d.ts|
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
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bluetooth.opp.d.ts<br>差异内容：ConnectivityKit|api/@ohos.bluetooth.opp.d.ts|
|新增导出符号|类名：global；<br>API声明：export interface BarcodeTag<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export interface BarcodeTag|api/tag/nfctech.d.ts|
