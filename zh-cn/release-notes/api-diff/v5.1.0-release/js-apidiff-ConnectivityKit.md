| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增错误码|类名：access；<br>API声明：function on(type: 'stateChange', callback: Callback\<BluetoothState>): void;<br>差异内容：NA|类名：access；<br>API声明：function on(type: 'stateChange', callback: Callback\<BluetoothState>): void;<br>差异内容：201|api/@ohos.bluetooth.access.d.ts|
|新增错误码|类名：access；<br>API声明：function off(type: 'stateChange', callback?: Callback\<BluetoothState>): void;<br>差异内容：NA|类名：access；<br>API声明：function off(type: 'stateChange', callback?: Callback\<BluetoothState>): void;<br>差异内容：201|api/@ohos.bluetooth.access.d.ts|
|新增错误码|类名：connection；<br>API声明：function getRemoteDeviceClass(deviceId: string): DeviceClass;<br>差异内容：NA|类名：connection；<br>API声明：function getRemoteDeviceClass(deviceId: string): DeviceClass;<br>差异内容：201|api/@ohos.bluetooth.connection.d.ts|
|新增错误码|类名：wifiManager；<br>API声明：function on(type: 'hotspotStateChange', callback: Callback\<number>): void;<br>差异内容：NA|类名：wifiManager；<br>API声明：function on(type: 'hotspotStateChange', callback: Callback\<number>): void;<br>差异内容：202|api/@ohos.wifiManager.d.ts|
|新增错误码|类名：wifiManager；<br>API声明：function off(type: 'hotspotStateChange', callback?: Callback\<number>): void;<br>差异内容：NA|类名：wifiManager；<br>API声明：function off(type: 'hotspotStateChange', callback?: Callback\<number>): void;<br>差异内容：202|api/@ohos.wifiManager.d.ts|
|删除错误码|类名：ble；<br>API声明：function startAdvertising(setting: AdvertiseSetting, advData: AdvertiseData, advResponse?: AdvertiseData): void;<br>差异内容：2900010,2902054|类名：ble；<br>API声明：function startAdvertising(setting: AdvertiseSetting, advData: AdvertiseData, advResponse?: AdvertiseData): void;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：ble；<br>API声明：function startAdvertising(advertisingParams: AdvertisingParams, callback: AsyncCallback\<number>): void;<br>差异内容：2900010,2902054|类名：ble；<br>API声明：function startAdvertising(advertisingParams: AdvertisingParams, callback: AsyncCallback\<number>): void;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：ble；<br>API声明：function startAdvertising(advertisingParams: AdvertisingParams): Promise\<number>;<br>差异内容：2900010,2902054|类名：ble；<br>API声明：function startAdvertising(advertisingParams: AdvertisingParams): Promise\<number>;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：ble；<br>API声明：function stopAdvertising(advertisingId: number, callback: AsyncCallback\<void>): void;<br>差异内容：2902055|类名：ble；<br>API声明：function stopAdvertising(advertisingId: number, callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：ble；<br>API声明：function stopAdvertising(advertisingId: number): Promise\<void>;<br>差异内容：2902055|类名：ble；<br>API声明：function stopAdvertising(advertisingId: number): Promise\<void>;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：ble；<br>API声明：function enableAdvertising(advertisingEnableParams: AdvertisingEnableParams, callback: AsyncCallback\<void>): void;<br>差异内容：2902055|类名：ble；<br>API声明：function enableAdvertising(advertisingEnableParams: AdvertisingEnableParams, callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：ble；<br>API声明：function enableAdvertising(advertisingEnableParams: AdvertisingEnableParams): Promise\<void>;<br>差异内容：2902055|类名：ble；<br>API声明：function enableAdvertising(advertisingEnableParams: AdvertisingEnableParams): Promise\<void>;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：ble；<br>API声明：function disableAdvertising(advertisingDisableParams: AdvertisingDisableParams, callback: AsyncCallback\<void>): void;<br>差异内容：2902055|类名：ble；<br>API声明：function disableAdvertising(advertisingDisableParams: AdvertisingDisableParams, callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：ble；<br>API声明：function disableAdvertising(advertisingDisableParams: AdvertisingDisableParams): Promise\<void>;<br>差异内容：2902055|类名：ble；<br>API声明：function disableAdvertising(advertisingDisableParams: AdvertisingDisableParams): Promise\<void>;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：GattClientDevice；<br>API声明：readCharacteristicValue(characteristic: BLECharacteristic, callback: AsyncCallback\<BLECharacteristic>): void;<br>差异内容：2900011,2901003,2901004,2901005,2901006,2901007|类名：GattClientDevice；<br>API声明：readCharacteristicValue(characteristic: BLECharacteristic, callback: AsyncCallback\<BLECharacteristic>): void;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：GattClientDevice；<br>API声明：readCharacteristicValue(characteristic: BLECharacteristic): Promise\<BLECharacteristic>;<br>差异内容：2900011,2901003,2901004,2901005,2901006,2901007|类名：GattClientDevice；<br>API声明：readCharacteristicValue(characteristic: BLECharacteristic): Promise\<BLECharacteristic>;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：GattClientDevice；<br>API声明：readDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback\<BLEDescriptor>): void;<br>差异内容：2900011,2901003,2901004,2901005,2901006,2901007|类名：GattClientDevice；<br>API声明：readDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback\<BLEDescriptor>): void;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：GattClientDevice；<br>API声明：readDescriptorValue(descriptor: BLEDescriptor): Promise\<BLEDescriptor>;<br>差异内容：2900011,2901003,2901004,2901005,2901006,2901007|类名：GattClientDevice；<br>API声明：readDescriptorValue(descriptor: BLEDescriptor): Promise\<BLEDescriptor>;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：GattClientDevice；<br>API声明：writeCharacteristicValue(characteristic: BLECharacteristic, writeType: GattWriteType, callback: AsyncCallback\<void>): void;<br>差异内容：2900011,2901003,2901004,2901005,2901006,2901007|类名：GattClientDevice；<br>API声明：writeCharacteristicValue(characteristic: BLECharacteristic, writeType: GattWriteType, callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：GattClientDevice；<br>API声明：writeCharacteristicValue(characteristic: BLECharacteristic, writeType: GattWriteType): Promise\<void>;<br>差异内容：2900011,2901003,2901004,2901005,2901006,2901007|类名：GattClientDevice；<br>API声明：writeCharacteristicValue(characteristic: BLECharacteristic, writeType: GattWriteType): Promise\<void>;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：GattClientDevice；<br>API声明：writeDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback\<void>): void;<br>差异内容：2900011,2901003,2901004,2901005,2901006,2901007|类名：GattClientDevice；<br>API声明：writeDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：GattClientDevice；<br>API声明：writeDescriptorValue(descriptor: BLEDescriptor): Promise\<void>;<br>差异内容：2900011,2901003,2901004,2901005,2901006,2901007|类名：GattClientDevice；<br>API声明：writeDescriptorValue(descriptor: BLEDescriptor): Promise\<void>;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：GattClientDevice；<br>API声明：getRssiValue(callback: AsyncCallback\<number>): void;<br>差异内容：2900011,2901003|类名：GattClientDevice；<br>API声明：getRssiValue(callback: AsyncCallback\<number>): void;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：GattClientDevice；<br>API声明：getRssiValue(): Promise\<number>;<br>差异内容：2900011,2901003|类名：GattClientDevice；<br>API声明：getRssiValue(): Promise\<number>;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：GattClientDevice；<br>API声明：setCharacteristicChangeNotification(characteristic: BLECharacteristic, enable: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：2900011,2901003|类名：GattClientDevice；<br>API声明：setCharacteristicChangeNotification(characteristic: BLECharacteristic, enable: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：GattClientDevice；<br>API声明：setCharacteristicChangeNotification(characteristic: BLECharacteristic, enable: boolean): Promise\<void>;<br>差异内容：2900011,2901003|类名：GattClientDevice；<br>API声明：setCharacteristicChangeNotification(characteristic: BLECharacteristic, enable: boolean): Promise\<void>;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：GattClientDevice；<br>API声明：setCharacteristicChangeIndication(characteristic: BLECharacteristic, enable: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：2900011,2901003|类名：GattClientDevice；<br>API声明：setCharacteristicChangeIndication(characteristic: BLECharacteristic, enable: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：GattClientDevice；<br>API声明：setCharacteristicChangeIndication(characteristic: BLECharacteristic, enable: boolean): Promise\<void>;<br>差异内容：2900011,2901003|类名：GattClientDevice；<br>API声明：setCharacteristicChangeIndication(characteristic: BLECharacteristic, enable: boolean): Promise\<void>;<br>差异内容：NA|api/@ohos.bluetooth.ble.d.ts|
|删除错误码|类名：HceService；<br>API声明：on(type: 'hceCmd', callback: AsyncCallback\<number[]>): void;<br>差异内容：201,401,801|类名：HceService；<br>API声明：on(type: 'hceCmd', callback: AsyncCallback\<number[]>): void;<br>差异内容：NA|api/@ohos.nfc.cardEmulation.d.ts|
|权限变更|类名：access；<br>API声明：function on(type: 'stateChange', callback: Callback\<BluetoothState>): void;<br>差异内容：NA|类名：access；<br>API声明：function on(type: 'stateChange', callback: Callback\<BluetoothState>): void;<br>差异内容：ohos.permission.ACCESS_BLUETOOTH|api/@ohos.bluetooth.access.d.ts|
|权限变更|类名：access；<br>API声明：function off(type: 'stateChange', callback?: Callback\<BluetoothState>): void;<br>差异内容：NA|类名：access；<br>API声明：function off(type: 'stateChange', callback?: Callback\<BluetoothState>): void;<br>差异内容：ohos.permission.ACCESS_BLUETOOTH|api/@ohos.bluetooth.access.d.ts|
|权限变更|类名：connection；<br>API声明：function getRemoteDeviceClass(deviceId: string): DeviceClass;<br>差异内容：NA|类名：connection；<br>API声明：function getRemoteDeviceClass(deviceId: string): DeviceClass;<br>差异内容：ohos.permission.ACCESS_BLUETOOTH|api/@ohos.bluetooth.connection.d.ts|
|删除API|类名：global；<br>API声明：declare namespace opp<br>差异内容：declare namespace opp|NA|api/@ohos.bluetooth.opp.d.ts|
|删除API|类名：opp；<br>API声明：interface OppServerProfile<br>差异内容：interface OppServerProfile|NA|api/@ohos.bluetooth.opp.d.ts|
|删除API|类名：global；<br>API声明：export interface BarcodeTag<br>差异内容：export interface BarcodeTag|NA|api/tag/nfctech.d.ts|
|删除API|类名：BarcodeTag；<br>API声明：getBarcode(): Promise\<ArrayBuffer>;<br>差异内容：getBarcode(): Promise\<ArrayBuffer>;|NA|api/tag/nfctech.d.ts|
|删除API|类名：CodecInfo；<br>API声明：codecBitRate?: CodecBitRate;<br>差异内容：codecBitRate?: CodecBitRate;|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：CodecInfo；<br>API声明：codecFrameLength?: CodecFrameLength;<br>差异内容：codecFrameLength?: CodecFrameLength;|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：a2dp；<br>API声明：interface CodecInfoList<br>差异内容：interface CodecInfoList|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：CodecInfoList；<br>API声明：codecType: CodecType;<br>差异内容：codecType: CodecType;|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：CodecInfoList；<br>API声明：codecBitsPerSampleArray: CodecBitsPerSample[];<br>差异内容：codecBitsPerSampleArray: CodecBitsPerSample[];|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：CodecInfoList；<br>API声明：codecChannelModeArray: CodecChannelMode[];<br>差异内容：codecChannelModeArray: CodecChannelMode[];|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：CodecInfoList；<br>API声明：codecSampleRateArray: CodecSampleRate[];<br>差异内容：codecSampleRateArray: CodecSampleRate[];|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：CodecInfoList；<br>API声明：codecBitRateArray: CodecBitRate[];<br>差异内容：codecBitRateArray: CodecBitRate[];|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：CodecInfoList；<br>API声明：codecFrameLengthArray: CodecFrameLength[];<br>差异内容：codecFrameLengthArray: CodecFrameLength[];|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：a2dp；<br>API声明：enum CodecBitRate<br>差异内容：enum CodecBitRate|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：CodecBitRate；<br>API声明：CODEC_BIT_RATE_96000 = 0<br>差异内容：CODEC_BIT_RATE_96000 = 0|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：CodecBitRate；<br>API声明：CODEC_BIT_RATE_128000 = 1<br>差异内容：CODEC_BIT_RATE_128000 = 1|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：CodecBitRate；<br>API声明：CODEC_BIT_RATE_192000 = 2<br>差异内容：CODEC_BIT_RATE_192000 = 2|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：CodecBitRate；<br>API声明：CODEC_BIT_RATE_256000 = 3<br>差异内容：CODEC_BIT_RATE_256000 = 3|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：CodecBitRate；<br>API声明：CODEC_BIT_RATE_320000 = 4<br>差异内容：CODEC_BIT_RATE_320000 = 4|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：CodecBitRate；<br>API声明：CODEC_BIT_RATE_480000 = 5<br>差异内容：CODEC_BIT_RATE_480000 = 5|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：CodecBitRate；<br>API声明：CODEC_BIT_RATE_640000 = 6<br>差异内容：CODEC_BIT_RATE_640000 = 6|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：CodecBitRate；<br>API声明：CODEC_BIT_RATE_960000 = 7<br>差异内容：CODEC_BIT_RATE_960000 = 7|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：CodecBitRate；<br>API声明：CODEC_BIT_RATE_ABR = 8<br>差异内容：CODEC_BIT_RATE_ABR = 8|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：a2dp；<br>API声明：enum CodecFrameLength<br>差异内容：enum CodecFrameLength|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：CodecFrameLength；<br>API声明：CODEC_FRAME_LENGTH_5MS = 0<br>差异内容：CODEC_FRAME_LENGTH_5MS = 0|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：CodecFrameLength；<br>API声明：CODEC_FRAME_LENGTH_10MS = 1<br>差异内容：CODEC_FRAME_LENGTH_10MS = 1|NA|api/@ohos.bluetooth.a2dp.d.ts|
|删除API|类名：access；<br>API声明：function enableBluetoothAsync(): Promise\<void>;<br>差异内容：function enableBluetoothAsync(): Promise\<void>;|NA|api/@ohos.bluetooth.access.d.ts|
|删除API|类名：access；<br>API声明：function disableBluetoothAsync(): Promise\<void>;<br>差异内容：function disableBluetoothAsync(): Promise\<void>;|NA|api/@ohos.bluetooth.access.d.ts|
|删除API|类名：access；<br>API声明：function addPersistentDeviceId(deviceId: string): Promise\<void>;<br>差异内容：function addPersistentDeviceId(deviceId: string): Promise\<void>;|NA|api/@ohos.bluetooth.access.d.ts|
|删除API|类名：access；<br>API声明：function deletePersistentDeviceId(deviceId: string): Promise\<void>;<br>差异内容：function deletePersistentDeviceId(deviceId: string): Promise\<void>;|NA|api/@ohos.bluetooth.access.d.ts|
|删除API|类名：access；<br>API声明：function getPersistentDeviceIds(): string[];<br>差异内容：function getPersistentDeviceIds(): string[];|NA|api/@ohos.bluetooth.access.d.ts|
|删除API|类名：access；<br>API声明：function isValidRandomDeviceId(deviceId: string): boolean;<br>差异内容：function isValidRandomDeviceId(deviceId: string): boolean;|NA|api/@ohos.bluetooth.access.d.ts|
|删除API|类名：BLECharacteristic；<br>API声明：characteristicValueHandle?: number;<br>差异内容：characteristicValueHandle?: number;|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：BLECharacteristic；<br>API声明：permissions?: GattPermissions;<br>差异内容：permissions?: GattPermissions;|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：BLEDescriptor；<br>API声明：descriptorHandle?: number;<br>差异内容：descriptorHandle?: number;|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：BLEDescriptor；<br>API声明：permissions?: GattPermissions;<br>差异内容：permissions?: GattPermissions;|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：BLEConnectionChangeState；<br>API声明：reason?: GattDisconnectReason;<br>差异内容：reason?: GattDisconnectReason;|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：AdvertiseData；<br>API声明：includeTxPower?: boolean;<br>差异内容：includeTxPower?: boolean;|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：GattProperties；<br>API声明：broadcast?: boolean;<br>差异内容：broadcast?: boolean;|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：GattProperties；<br>API声明：authenticatedSignedWrite?: boolean;<br>差异内容：authenticatedSignedWrite?: boolean;|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：GattProperties；<br>API声明：extendedProperties?: boolean;<br>差异内容：extendedProperties?: boolean;|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：ScanReportMode；<br>API声明：BATCH = 2<br>差异内容：BATCH = 2|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：ScanReportMode；<br>API声明：FENCE_SENSITIVITY_LOW = 10<br>差异内容：FENCE_SENSITIVITY_LOW = 10|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：ScanReportMode；<br>API声明：FENCE_SENSITIVITY_HIGH = 11<br>差异内容：FENCE_SENSITIVITY_HIGH = 11|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：ScanReportType；<br>API声明：ON_BATCH = 3<br>差异内容：ON_BATCH = 3|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：ble；<br>API声明：enum GattDisconnectReason<br>差异内容：enum GattDisconnectReason|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：GattDisconnectReason；<br>API声明：CONN_TIMEOUT = 1<br>差异内容：CONN_TIMEOUT = 1|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：GattDisconnectReason；<br>API声明：CONN_TERMINATE_PEER_USER = 2<br>差异内容：CONN_TERMINATE_PEER_USER = 2|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：GattDisconnectReason；<br>API声明：CONN_TERMINATE_LOCAL_HOST = 3<br>差异内容：CONN_TERMINATE_LOCAL_HOST = 3|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：GattDisconnectReason；<br>API声明：CONN_UNKNOWN = 4<br>差异内容：CONN_UNKNOWN = 4|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：ble；<br>API声明：interface GattPermissions<br>差异内容：interface GattPermissions|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：GattPermissions；<br>API声明：read?: boolean;<br>差异内容：read?: boolean;|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：GattPermissions；<br>API声明：readEncrypted?: boolean;<br>差异内容：readEncrypted?: boolean;|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：GattPermissions；<br>API声明：readEncryptedMitm?: boolean;<br>差异内容：readEncryptedMitm?: boolean;|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：GattPermissions；<br>API声明：write?: boolean;<br>差异内容：write?: boolean;|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：GattPermissions；<br>API声明：writeEncrypted?: boolean;<br>差异内容：writeEncrypted?: boolean;|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：GattPermissions；<br>API声明：writeEncryptedMitm?: boolean;<br>差异内容：writeEncryptedMitm?: boolean;|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：GattPermissions；<br>API声明：writeSigned?: boolean;<br>差异内容：writeSigned?: boolean;|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：GattPermissions；<br>API声明：writeSignedMitm?: boolean;<br>差异内容：writeSignedMitm?: boolean;|NA|api/@ohos.bluetooth.ble.d.ts|
|删除API|类名：connection；<br>API声明：function getRemoteDeviceName(deviceId: string, alias?: boolean): string;<br>差异内容：function getRemoteDeviceName(deviceId: string, alias?: boolean): string;|NA|api/@ohos.bluetooth.connection.d.ts|
|删除API|类名：connection；<br>API声明：function getRemoteDeviceTransport(deviceId: string): BluetoothTransport;<br>差异内容：function getRemoteDeviceTransport(deviceId: string): BluetoothTransport;|NA|api/@ohos.bluetooth.connection.d.ts|
|删除API|类名：connection；<br>API声明：function connectAllowedProfiles(deviceId: string, callback: AsyncCallback\<void>): void;<br>差异内容：function connectAllowedProfiles(deviceId: string, callback: AsyncCallback\<void>): void;|NA|api/@ohos.bluetooth.connection.d.ts|
|删除API|类名：connection；<br>API声明：function connectAllowedProfiles(deviceId: string): Promise\<void>;<br>差异内容：function connectAllowedProfiles(deviceId: string): Promise\<void>;|NA|api/@ohos.bluetooth.connection.d.ts|
|删除API|类名：connection；<br>API声明：function on(type: 'discoveryResult', callback: Callback\<Array\<DiscoveryResult>>): void;<br>差异内容：function on(type: 'discoveryResult', callback: Callback\<Array\<DiscoveryResult>>): void;|NA|api/@ohos.bluetooth.connection.d.ts|
|删除API|类名：connection；<br>API声明：function off(type: 'discoveryResult', callback?: Callback\<Array\<DiscoveryResult>>): void;<br>差异内容：function off(type: 'discoveryResult', callback?: Callback\<Array\<DiscoveryResult>>): void;|NA|api/@ohos.bluetooth.connection.d.ts|
|删除API|类名：BluetoothTransport；<br>API声明：TRANSPORT_DUAL = 2<br>差异内容：TRANSPORT_DUAL = 2|NA|api/@ohos.bluetooth.connection.d.ts|
|删除API|类名：BluetoothTransport；<br>API声明：TRANSPORT_UNKNOWN = 3<br>差异内容：TRANSPORT_UNKNOWN = 3|NA|api/@ohos.bluetooth.connection.d.ts|
|删除API|类名：connection；<br>API声明：interface DiscoveryResult<br>差异内容：interface DiscoveryResult|NA|api/@ohos.bluetooth.connection.d.ts|
|删除API|类名：DiscoveryResult；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|NA|api/@ohos.bluetooth.connection.d.ts|
|删除API|类名：DiscoveryResult；<br>API声明：rssi: number;<br>差异内容：rssi: number;|NA|api/@ohos.bluetooth.connection.d.ts|
|删除API|类名：DiscoveryResult；<br>API声明：deviceName: string;<br>差异内容：deviceName: string;|NA|api/@ohos.bluetooth.connection.d.ts|
|删除API|类名：DiscoveryResult；<br>API声明：deviceClass: DeviceClass;<br>差异内容：deviceClass: DeviceClass;|NA|api/@ohos.bluetooth.connection.d.ts|
|删除API|类名：socket；<br>API声明：function getL2capPsm(serverSocket: number): number;<br>差异内容：function getL2capPsm(serverSocket: number): number;|NA|api/@ohos.bluetooth.socket.d.ts|
|删除API|类名：socket；<br>API声明：function getDeviceId(clientSocket: number): string;<br>差异内容：function getDeviceId(clientSocket: number): string;|NA|api/@ohos.bluetooth.socket.d.ts|
|删除API|类名：socket；<br>API声明：function sppWriteAsync(clientSocket: number, data: ArrayBuffer): Promise\<void>;<br>差异内容：function sppWriteAsync(clientSocket: number, data: ArrayBuffer): Promise\<void>;|NA|api/@ohos.bluetooth.socket.d.ts|
|删除API|类名：socket；<br>API声明：function sppReadAsync(clientSocket: number): Promise\<ArrayBuffer>;<br>差异内容：function sppReadAsync(clientSocket: number): Promise\<ArrayBuffer>;|NA|api/@ohos.bluetooth.socket.d.ts|
|删除API|类名：SppOptions；<br>API声明：psm?: number;<br>差异内容：psm?: number;|NA|api/@ohos.bluetooth.socket.d.ts|
|删除API|类名：SppType；<br>API声明：SPP_L2CAP = 1<br>差异内容：SPP_L2CAP = 1|NA|api/@ohos.bluetooth.socket.d.ts|
|删除API|类名：SppType；<br>API声明：SPP_L2CAP_BLE = 2<br>差异内容：SPP_L2CAP_BLE = 2|NA|api/@ohos.bluetooth.socket.d.ts|
|删除API|类名：HceService；<br>API声明：off(type: 'hceCmd', callback?: AsyncCallback\<number[]>): void;<br>差异内容：off(type: 'hceCmd', callback?: AsyncCallback\<number[]>): void;|NA|api/@ohos.nfc.cardEmulation.d.ts|
|删除API|类名：tag；<br>API声明：const NFC_BARCODE = 10;<br>差异内容：const NFC_BARCODE = 10;|NA|api/@ohos.nfc.tag.d.ts|
|删除API|类名：tag；<br>API声明：function getBarcodeTag(tagInfo: TagInfo): BarcodeTag;<br>差异内容：function getBarcodeTag(tagInfo: TagInfo): BarcodeTag;|NA|api/@ohos.nfc.tag.d.ts|
|删除API|类名：ndef；<br>API声明：function makeApplicationRecord(bundleName: string): NdefRecord;<br>差异内容：function makeApplicationRecord(bundleName: string): NdefRecord;|NA|api/@ohos.nfc.tag.d.ts|
|删除API|类名：tag；<br>API声明：export type BarcodeTag = _BarcodeTag;<br>差异内容：export type BarcodeTag = _BarcodeTag;|NA|api/@ohos.nfc.tag.d.ts|
|删除API|类名：omapi；<br>API声明：function on(type: 'stateChanged', callback: Callback\<ServiceState>): void;<br>差异内容：function on(type: 'stateChanged', callback: Callback\<ServiceState>): void;|NA|api/@ohos.secureElement.d.ts|
|删除API|类名：omapi；<br>API声明：function off(type: 'stateChanged', callback?: Callback\<ServiceState>): void;<br>差异内容：function off(type: 'stateChanged', callback?: Callback\<ServiceState>): void;|NA|api/@ohos.secureElement.d.ts|
|删除API|类名：wifiManager；<br>API声明：function disableWifi(): void;<br>差异内容：function disableWifi(): void;|NA|api/@ohos.wifiManager.d.ts|
|删除API|类名：wifiManager；<br>API声明：function connectToCandidateConfigWithUserAction(networkId: number): Promise\<void>;<br>差异内容：function connectToCandidateConfigWithUserAction(networkId: number): Promise\<void>;|NA|api/@ohos.wifiManager.d.ts|
|删除API|类名：wifiManager；<br>API声明：function getMultiLinkedInfo(): Array\<WifiLinkedInfo>;<br>差异内容：function getMultiLinkedInfo(): Array\<WifiLinkedInfo>;|NA|api/@ohos.wifiManager.d.ts|
|删除API|类名：wifiManager；<br>API声明：function getLinkedInfoSync(): WifiLinkedInfo;<br>差异内容：function getLinkedInfoSync(): WifiLinkedInfo;|NA|api/@ohos.wifiManager.d.ts|
|删除API|类名：wifiManager；<br>API声明：enum WifiLinkType<br>差异内容：enum WifiLinkType|NA|api/@ohos.wifiManager.d.ts|
|删除API|类名：WifiLinkType；<br>API声明：DEFAULT_LINK = 0<br>差异内容：DEFAULT_LINK = 0|NA|api/@ohos.wifiManager.d.ts|
|删除API|类名：WifiLinkType；<br>API声明：WIFI7_SINGLE_LINK = 1<br>差异内容：WIFI7_SINGLE_LINK = 1|NA|api/@ohos.wifiManager.d.ts|
|删除API|类名：WifiLinkType；<br>API声明：WIFI7_MLSR = 2<br>差异内容：WIFI7_MLSR = 2|NA|api/@ohos.wifiManager.d.ts|
|删除API|类名：WifiLinkType；<br>API声明：WIFI7_EMLSR = 3<br>差异内容：WIFI7_EMLSR = 3|NA|api/@ohos.wifiManager.d.ts|
|删除API|类名：WifiLinkType；<br>API声明：WIFI7_STR = 4<br>差异内容：WIFI7_STR = 4|NA|api/@ohos.wifiManager.d.ts|
|删除API|类名：WifiLinkedInfo；<br>API声明：wifiLinkType?: WifiLinkType;<br>差异内容：wifiLinkType?: WifiLinkType;|NA|api/@ohos.wifiManager.d.ts|
|起始版本有变化|类名：connection；<br>API声明：type ProfileUuids = constant.ProfileUuids;<br>差异内容：12|类名：connection；<br>API声明：type ProfileUuids = constant.ProfileUuids;<br>差异内容：10|api/@ohos.bluetooth.connection.d.ts|
|起始版本有变化|类名：connection；<br>API声明：function getRemoteProfileUuids(deviceId: string, callback: AsyncCallback\<Array\<ProfileUuids>>): void;<br>差异内容：12|类名：connection；<br>API声明：function getRemoteProfileUuids(deviceId: string, callback: AsyncCallback\<Array\<ProfileUuids>>): void;<br>差异内容：10|api/@ohos.bluetooth.connection.d.ts|
|起始版本有变化|类名：connection；<br>API声明：function getRemoteProfileUuids(deviceId: string): Promise\<Array\<ProfileUuids>>;<br>差异内容：12|类名：connection；<br>API声明：function getRemoteProfileUuids(deviceId: string): Promise\<Array\<ProfileUuids>>;<br>差异内容：10|api/@ohos.bluetooth.connection.d.ts|
|起始版本有变化|类名：constant；<br>API声明：export enum ProfileUuids<br>差异内容：12|类名：constant；<br>API声明：export enum ProfileUuids<br>差异内容：10|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HFP_AG = '0000111F-0000-1000-8000-00805F9B34FB'<br>差异内容：12|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HFP_AG = '0000111F-0000-1000-8000-00805F9B34FB'<br>差异内容：10|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HFP_HF = '0000111E-0000-1000-8000-00805F9B34FB'<br>差异内容：12|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HFP_HF = '0000111E-0000-1000-8000-00805F9B34FB'<br>差异内容：10|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HSP_AG = '00001112-0000-1000-8000-00805F9B34FB'<br>差异内容：12|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HSP_AG = '00001112-0000-1000-8000-00805F9B34FB'<br>差异内容：10|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HSP_HS = '00001108-0000-1000-8000-00805F9B34FB'<br>差异内容：12|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HSP_HS = '00001108-0000-1000-8000-00805F9B34FB'<br>差异内容：10|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_A2DP_SRC = '0000110A-0000-1000-8000-00805F9B34FB'<br>差异内容：12|类名：ProfileUuids；<br>API声明：PROFILE_UUID_A2DP_SRC = '0000110A-0000-1000-8000-00805F9B34FB'<br>差异内容：10|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_A2DP_SINK = '0000110B-0000-1000-8000-00805F9B34FB'<br>差异内容：12|类名：ProfileUuids；<br>API声明：PROFILE_UUID_A2DP_SINK = '0000110B-0000-1000-8000-00805F9B34FB'<br>差异内容：10|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_AVRCP_CT = '0000110E-0000-1000-8000-00805F9B34FB'<br>差异内容：12|类名：ProfileUuids；<br>API声明：PROFILE_UUID_AVRCP_CT = '0000110E-0000-1000-8000-00805F9B34FB'<br>差异内容：10|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_AVRCP_TG = '0000110C-0000-1000-8000-00805F9B34FB'<br>差异内容：12|类名：ProfileUuids；<br>API声明：PROFILE_UUID_AVRCP_TG = '0000110C-0000-1000-8000-00805F9B34FB'<br>差异内容：10|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HID = '00001124-0000-1000-8000-00805F9B34FB'<br>差异内容：12|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HID = '00001124-0000-1000-8000-00805F9B34FB'<br>差异内容：10|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HOGP = '00001812-0000-1000-8000-00805F9B34FB'<br>差异内容：12|类名：ProfileUuids；<br>API声明：PROFILE_UUID_HOGP = '00001812-0000-1000-8000-00805F9B34FB'<br>差异内容：10|api/@ohos.bluetooth.constant.d.ts|
|起始版本有变化|类名：wifiManager；<br>API声明：function isHotspotActive(): boolean;<br>差异内容：15|类名：wifiManager；<br>API声明：function isHotspotActive(): boolean;<br>差异内容：9|api/@ohos.wifiManager.d.ts|
|删除kit|类名：global；<br>API声明：api\@ohos.bluetooth.opp.d.ts<br>差异内容：ConnectivityKit|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.bluetooth.opp.d.ts|
|删除导出符号|类名：global；<br>API声明：export interface BarcodeTag<br>差异内容：export interface BarcodeTag|类名：global；<br>API声明：<br>差异内容：NA|api/tag/nfctech.d.ts|
