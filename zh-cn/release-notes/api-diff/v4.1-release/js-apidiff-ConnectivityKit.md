| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace a2dp<br>差异内容：declare namespace a2dp|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：a2dp；<br>API声明：type BaseProfile = baseProfile.BaseProfile;<br>差异内容：type BaseProfile = baseProfile.BaseProfile;|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：a2dp；<br>API声明：function createA2dpSrcProfile(): A2dpSourceProfile;<br>差异内容：function createA2dpSrcProfile(): A2dpSourceProfile;|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：a2dp；<br>API声明：interface A2dpSourceProfile<br>差异内容：interface A2dpSourceProfile|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：A2dpSourceProfile；<br>API声明：getPlayingState(deviceId: string): PlayingState;<br>差异内容：getPlayingState(deviceId: string): PlayingState;|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：a2dp；<br>API声明：interface CodecInfo<br>差异内容：interface CodecInfo|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecInfo；<br>API声明：codecType: CodecType;<br>差异内容：codecType: CodecType;|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecInfo；<br>API声明：codecBitsPerSample: CodecBitsPerSample;<br>差异内容：codecBitsPerSample: CodecBitsPerSample;|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecInfo；<br>API声明：codecChannelMode: CodecChannelMode;<br>差异内容：codecChannelMode: CodecChannelMode;|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecInfo；<br>API声明：codecSampleRate: CodecSampleRate;<br>差异内容：codecSampleRate: CodecSampleRate;|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：a2dp；<br>API声明：enum PlayingState<br>差异内容：enum PlayingState|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：PlayingState；<br>API声明：STATE_NOT_PLAYING<br>差异内容：STATE_NOT_PLAYING|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：PlayingState；<br>API声明：STATE_PLAYING<br>差异内容：STATE_PLAYING|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：a2dp；<br>API声明：enum CodecType<br>差异内容：enum CodecType|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecType；<br>API声明：CODEC_TYPE_INVALID = -1<br>差异内容：CODEC_TYPE_INVALID = -1|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecType；<br>API声明：CODEC_TYPE_SBC = 0<br>差异内容：CODEC_TYPE_SBC = 0|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecType；<br>API声明：CODEC_TYPE_AAC = 1<br>差异内容：CODEC_TYPE_AAC = 1|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecType；<br>API声明：CODEC_TYPE_L2HC = 2<br>差异内容：CODEC_TYPE_L2HC = 2|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：a2dp；<br>API声明：enum CodecChannelMode<br>差异内容：enum CodecChannelMode|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecChannelMode；<br>API声明：CODEC_CHANNEL_MODE_NONE = 0<br>差异内容：CODEC_CHANNEL_MODE_NONE = 0|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecChannelMode；<br>API声明：CODEC_CHANNEL_MODE_MONO = 1<br>差异内容：CODEC_CHANNEL_MODE_MONO = 1|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecChannelMode；<br>API声明：CODEC_CHANNEL_MODE_STEREO = 2<br>差异内容：CODEC_CHANNEL_MODE_STEREO = 2|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：a2dp；<br>API声明：enum CodecBitsPerSample<br>差异内容：enum CodecBitsPerSample|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecBitsPerSample；<br>API声明：CODEC_BITS_PER_SAMPLE_NONE = 0<br>差异内容：CODEC_BITS_PER_SAMPLE_NONE = 0|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecBitsPerSample；<br>API声明：CODEC_BITS_PER_SAMPLE_16 = 1<br>差异内容：CODEC_BITS_PER_SAMPLE_16 = 1|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecBitsPerSample；<br>API声明：CODEC_BITS_PER_SAMPLE_24 = 2<br>差异内容：CODEC_BITS_PER_SAMPLE_24 = 2|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecBitsPerSample；<br>API声明：CODEC_BITS_PER_SAMPLE_32 = 3<br>差异内容：CODEC_BITS_PER_SAMPLE_32 = 3|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：a2dp；<br>API声明：enum CodecSampleRate<br>差异内容：enum CodecSampleRate|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecSampleRate；<br>API声明：CODEC_SAMPLE_RATE_NONE = 0<br>差异内容：CODEC_SAMPLE_RATE_NONE = 0|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecSampleRate；<br>API声明：CODEC_SAMPLE_RATE_44100 = 1<br>差异内容：CODEC_SAMPLE_RATE_44100 = 1|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecSampleRate；<br>API声明：CODEC_SAMPLE_RATE_48000 = 2<br>差异内容：CODEC_SAMPLE_RATE_48000 = 2|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecSampleRate；<br>API声明：CODEC_SAMPLE_RATE_88200 = 3<br>差异内容：CODEC_SAMPLE_RATE_88200 = 3|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecSampleRate；<br>API声明：CODEC_SAMPLE_RATE_96000 = 4<br>差异内容：CODEC_SAMPLE_RATE_96000 = 4|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecSampleRate；<br>API声明：CODEC_SAMPLE_RATE_176400 = 5<br>差异内容：CODEC_SAMPLE_RATE_176400 = 5|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：CodecSampleRate；<br>API声明：CODEC_SAMPLE_RATE_192000 = 6<br>差异内容：CODEC_SAMPLE_RATE_192000 = 6|api/@ohos.bluetooth.a2dp.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace access<br>差异内容：declare namespace access|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：access；<br>API声明：function enableBluetooth(): void;<br>差异内容：function enableBluetooth(): void;|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：access；<br>API声明：function disableBluetooth(): void;<br>差异内容：function disableBluetooth(): void;|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：access；<br>API声明：function getState(): BluetoothState;<br>差异内容：function getState(): BluetoothState;|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：access；<br>API声明：function on(type: 'stateChange', callback: Callback\<BluetoothState>): void;<br>差异内容：function on(type: 'stateChange', callback: Callback\<BluetoothState>): void;|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：access；<br>API声明：function off(type: 'stateChange', callback?: Callback\<BluetoothState>): void;<br>差异内容：function off(type: 'stateChange', callback?: Callback\<BluetoothState>): void;|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：access；<br>API声明：export enum BluetoothState<br>差异内容：export enum BluetoothState|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_OFF = 0<br>差异内容：STATE_OFF = 0|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_TURNING_ON = 1<br>差异内容：STATE_TURNING_ON = 1|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_ON = 2<br>差异内容：STATE_ON = 2|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_TURNING_OFF = 3<br>差异内容：STATE_TURNING_OFF = 3|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_BLE_TURNING_ON = 4<br>差异内容：STATE_BLE_TURNING_ON = 4|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_BLE_ON = 5<br>差异内容：STATE_BLE_ON = 5|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_BLE_TURNING_OFF = 6<br>差异内容：STATE_BLE_TURNING_OFF = 6|api/@ohos.bluetooth.access.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace baseProfile<br>差异内容：declare namespace baseProfile|api/@ohos.bluetooth.baseProfile.d.ts|
|新增API|NA|类名：baseProfile；<br>API声明：type ProfileConnectionState = constant.ProfileConnectionState;<br>差异内容：type ProfileConnectionState = constant.ProfileConnectionState;|api/@ohos.bluetooth.baseProfile.d.ts|
|新增API|NA|类名：baseProfile；<br>API声明：export interface StateChangeParam<br>差异内容：export interface StateChangeParam|api/@ohos.bluetooth.baseProfile.d.ts|
|新增API|NA|类名：StateChangeParam；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.baseProfile.d.ts|
|新增API|NA|类名：StateChangeParam；<br>API声明：state: ProfileConnectionState;<br>差异内容：state: ProfileConnectionState;|api/@ohos.bluetooth.baseProfile.d.ts|
|新增API|NA|类名：baseProfile；<br>API声明：export interface BaseProfile<br>差异内容：export interface BaseProfile|api/@ohos.bluetooth.baseProfile.d.ts|
|新增API|NA|类名：BaseProfile；<br>API声明：getConnectedDevices(): Array\<string>;<br>差异内容：getConnectedDevices(): Array\<string>;|api/@ohos.bluetooth.baseProfile.d.ts|
|新增API|NA|类名：BaseProfile；<br>API声明：getConnectionState(deviceId: string): ProfileConnectionState;<br>差异内容：getConnectionState(deviceId: string): ProfileConnectionState;|api/@ohos.bluetooth.baseProfile.d.ts|
|新增API|NA|类名：BaseProfile；<br>API声明：on(type: 'connectionStateChange', callback: Callback\<StateChangeParam>): void;<br>差异内容：on(type: 'connectionStateChange', callback: Callback\<StateChangeParam>): void;|api/@ohos.bluetooth.baseProfile.d.ts|
|新增API|NA|类名：BaseProfile；<br>API声明：off(type: 'connectionStateChange', callback?: Callback\<StateChangeParam>): void;<br>差异内容：off(type: 'connectionStateChange', callback?: Callback\<StateChangeParam>): void;|api/@ohos.bluetooth.baseProfile.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace ble<br>差异内容：declare namespace ble|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：type ProfileConnectionState = constant.ProfileConnectionState;<br>差异内容：type ProfileConnectionState = constant.ProfileConnectionState;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function createGattServer(): GattServer;<br>差异内容：function createGattServer(): GattServer;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function createGattClientDevice(deviceId: string): GattClientDevice;<br>差异内容：function createGattClientDevice(deviceId: string): GattClientDevice;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function getConnectedBLEDevices(): Array\<string>;<br>差异内容：function getConnectedBLEDevices(): Array\<string>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function startBLEScan(filters: Array\<ScanFilter>, options?: ScanOptions): void;<br>差异内容：function startBLEScan(filters: Array\<ScanFilter>, options?: ScanOptions): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function stopBLEScan(): void;<br>差异内容：function stopBLEScan(): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function startAdvertising(setting: AdvertiseSetting, advData: AdvertiseData, advResponse?: AdvertiseData): void;<br>差异内容：function startAdvertising(setting: AdvertiseSetting, advData: AdvertiseData, advResponse?: AdvertiseData): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function startAdvertising(advertisingParams: AdvertisingParams, callback: AsyncCallback\<number>): void;<br>差异内容：function startAdvertising(advertisingParams: AdvertisingParams, callback: AsyncCallback\<number>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function startAdvertising(advertisingParams: AdvertisingParams): Promise\<number>;<br>差异内容：function startAdvertising(advertisingParams: AdvertisingParams): Promise\<number>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function stopAdvertising(): void;<br>差异内容：function stopAdvertising(): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function stopAdvertising(advertisingId: number, callback: AsyncCallback\<void>): void;<br>差异内容：function stopAdvertising(advertisingId: number, callback: AsyncCallback\<void>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function stopAdvertising(advertisingId: number): Promise\<void>;<br>差异内容：function stopAdvertising(advertisingId: number): Promise\<void>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function enableAdvertising(advertisingEnableParams: AdvertisingEnableParams, callback: AsyncCallback\<void>): void;<br>差异内容：function enableAdvertising(advertisingEnableParams: AdvertisingEnableParams, callback: AsyncCallback\<void>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function enableAdvertising(advertisingEnableParams: AdvertisingEnableParams): Promise\<void>;<br>差异内容：function enableAdvertising(advertisingEnableParams: AdvertisingEnableParams): Promise\<void>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function disableAdvertising(advertisingDisableParams: AdvertisingDisableParams, callback: AsyncCallback\<void>): void;<br>差异内容：function disableAdvertising(advertisingDisableParams: AdvertisingDisableParams, callback: AsyncCallback\<void>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function disableAdvertising(advertisingDisableParams: AdvertisingDisableParams): Promise\<void>;<br>差异内容：function disableAdvertising(advertisingDisableParams: AdvertisingDisableParams): Promise\<void>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function on(type: 'advertisingStateChange', callback: Callback\<AdvertisingStateChangeInfo>): void;<br>差异内容：function on(type: 'advertisingStateChange', callback: Callback\<AdvertisingStateChangeInfo>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function off(type: 'advertisingStateChange', callback?: Callback\<AdvertisingStateChangeInfo>): void;<br>差异内容：function off(type: 'advertisingStateChange', callback?: Callback\<AdvertisingStateChangeInfo>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function on(type: 'BLEDeviceFind', callback: Callback\<Array\<ScanResult>>): void;<br>差异内容：function on(type: 'BLEDeviceFind', callback: Callback\<Array\<ScanResult>>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：function off(type: 'BLEDeviceFind', callback?: Callback\<Array\<ScanResult>>): void;<br>差异内容：function off(type: 'BLEDeviceFind', callback?: Callback\<Array\<ScanResult>>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface GattServer<br>差异内容：interface GattServer|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：addService(service: GattService): void;<br>差异内容：addService(service: GattService): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：removeService(serviceUuid: string): void;<br>差异内容：removeService(serviceUuid: string): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：close(): void;<br>差异内容：close(): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：notifyCharacteristicChanged(deviceId: string, notifyCharacteristic: NotifyCharacteristic, callback: AsyncCallback\<void>): void;<br>差异内容：notifyCharacteristicChanged(deviceId: string, notifyCharacteristic: NotifyCharacteristic, callback: AsyncCallback\<void>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：notifyCharacteristicChanged(deviceId: string, notifyCharacteristic: NotifyCharacteristic): Promise\<void>;<br>差异内容：notifyCharacteristicChanged(deviceId: string, notifyCharacteristic: NotifyCharacteristic): Promise\<void>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：sendResponse(serverResponse: ServerResponse): void;<br>差异内容：sendResponse(serverResponse: ServerResponse): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：on(type: 'characteristicRead', callback: Callback\<CharacteristicReadRequest>): void;<br>差异内容：on(type: 'characteristicRead', callback: Callback\<CharacteristicReadRequest>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：off(type: 'characteristicRead', callback?: Callback\<CharacteristicReadRequest>): void;<br>差异内容：off(type: 'characteristicRead', callback?: Callback\<CharacteristicReadRequest>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：on(type: 'characteristicWrite', callback: Callback\<CharacteristicWriteRequest>): void;<br>差异内容：on(type: 'characteristicWrite', callback: Callback\<CharacteristicWriteRequest>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：off(type: 'characteristicWrite', callback?: Callback\<CharacteristicWriteRequest>): void;<br>差异内容：off(type: 'characteristicWrite', callback?: Callback\<CharacteristicWriteRequest>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：on(type: 'descriptorRead', callback: Callback\<DescriptorReadRequest>): void;<br>差异内容：on(type: 'descriptorRead', callback: Callback\<DescriptorReadRequest>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：off(type: 'descriptorRead', callback?: Callback\<DescriptorReadRequest>): void;<br>差异内容：off(type: 'descriptorRead', callback?: Callback\<DescriptorReadRequest>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：on(type: 'descriptorWrite', callback: Callback\<DescriptorWriteRequest>): void;<br>差异内容：on(type: 'descriptorWrite', callback: Callback\<DescriptorWriteRequest>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：off(type: 'descriptorWrite', callback?: Callback\<DescriptorWriteRequest>): void;<br>差异内容：off(type: 'descriptorWrite', callback?: Callback\<DescriptorWriteRequest>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：on(type: 'connectionStateChange', callback: Callback\<BLEConnectionChangeState>): void;<br>差异内容：on(type: 'connectionStateChange', callback: Callback\<BLEConnectionChangeState>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：off(type: 'connectionStateChange', callback?: Callback\<BLEConnectionChangeState>): void;<br>差异内容：off(type: 'connectionStateChange', callback?: Callback\<BLEConnectionChangeState>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：on(type: 'BLEMtuChange', callback: Callback\<number>): void;<br>差异内容：on(type: 'BLEMtuChange', callback: Callback\<number>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：off(type: 'BLEMtuChange', callback?: Callback\<number>): void;<br>差异内容：off(type: 'BLEMtuChange', callback?: Callback\<number>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface GattClientDevice<br>差异内容：interface GattClientDevice|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：connect(): void;<br>差异内容：connect(): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：disconnect(): void;<br>差异内容：disconnect(): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：close(): void;<br>差异内容：close(): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：getDeviceName(callback: AsyncCallback\<string>): void;<br>差异内容：getDeviceName(callback: AsyncCallback\<string>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：getDeviceName(): Promise\<string>;<br>差异内容：getDeviceName(): Promise\<string>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：getServices(callback: AsyncCallback\<Array\<GattService>>): void;<br>差异内容：getServices(callback: AsyncCallback\<Array\<GattService>>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：getServices(): Promise\<Array\<GattService>>;<br>差异内容：getServices(): Promise\<Array\<GattService>>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：readCharacteristicValue(characteristic: BLECharacteristic, callback: AsyncCallback\<BLECharacteristic>): void;<br>差异内容：readCharacteristicValue(characteristic: BLECharacteristic, callback: AsyncCallback\<BLECharacteristic>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：readCharacteristicValue(characteristic: BLECharacteristic): Promise\<BLECharacteristic>;<br>差异内容：readCharacteristicValue(characteristic: BLECharacteristic): Promise\<BLECharacteristic>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：readDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback\<BLEDescriptor>): void;<br>差异内容：readDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback\<BLEDescriptor>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：readDescriptorValue(descriptor: BLEDescriptor): Promise\<BLEDescriptor>;<br>差异内容：readDescriptorValue(descriptor: BLEDescriptor): Promise\<BLEDescriptor>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：writeCharacteristicValue(characteristic: BLECharacteristic, writeType: GattWriteType, callback: AsyncCallback\<void>): void;<br>差异内容：writeCharacteristicValue(characteristic: BLECharacteristic, writeType: GattWriteType, callback: AsyncCallback\<void>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：writeCharacteristicValue(characteristic: BLECharacteristic, writeType: GattWriteType): Promise\<void>;<br>差异内容：writeCharacteristicValue(characteristic: BLECharacteristic, writeType: GattWriteType): Promise\<void>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：writeDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback\<void>): void;<br>差异内容：writeDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback\<void>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：writeDescriptorValue(descriptor: BLEDescriptor): Promise\<void>;<br>差异内容：writeDescriptorValue(descriptor: BLEDescriptor): Promise\<void>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：getRssiValue(callback: AsyncCallback\<number>): void;<br>差异内容：getRssiValue(callback: AsyncCallback\<number>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：getRssiValue(): Promise\<number>;<br>差异内容：getRssiValue(): Promise\<number>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：setBLEMtuSize(mtu: number): void;<br>差异内容：setBLEMtuSize(mtu: number): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：setCharacteristicChangeNotification(characteristic: BLECharacteristic, enable: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：setCharacteristicChangeNotification(characteristic: BLECharacteristic, enable: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：setCharacteristicChangeNotification(characteristic: BLECharacteristic, enable: boolean): Promise\<void>;<br>差异内容：setCharacteristicChangeNotification(characteristic: BLECharacteristic, enable: boolean): Promise\<void>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：setCharacteristicChangeIndication(characteristic: BLECharacteristic, enable: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：setCharacteristicChangeIndication(characteristic: BLECharacteristic, enable: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：setCharacteristicChangeIndication(characteristic: BLECharacteristic, enable: boolean): Promise\<void>;<br>差异内容：setCharacteristicChangeIndication(characteristic: BLECharacteristic, enable: boolean): Promise\<void>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：on(type: 'BLECharacteristicChange', callback: Callback\<BLECharacteristic>): void;<br>差异内容：on(type: 'BLECharacteristicChange', callback: Callback\<BLECharacteristic>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：off(type: 'BLECharacteristicChange', callback?: Callback\<BLECharacteristic>): void;<br>差异内容：off(type: 'BLECharacteristicChange', callback?: Callback\<BLECharacteristic>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：on(type: 'BLEConnectionStateChange', callback: Callback\<BLEConnectionChangeState>): void;<br>差异内容：on(type: 'BLEConnectionStateChange', callback: Callback\<BLEConnectionChangeState>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：off(type: 'BLEConnectionStateChange', callback?: Callback\<BLEConnectionChangeState>): void;<br>差异内容：off(type: 'BLEConnectionStateChange', callback?: Callback\<BLEConnectionChangeState>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：on(type: 'BLEMtuChange', callback: Callback\<number>): void;<br>差异内容：on(type: 'BLEMtuChange', callback: Callback\<number>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：off(type: 'BLEMtuChange', callback?: Callback\<number>): void;<br>差异内容：off(type: 'BLEMtuChange', callback?: Callback\<number>): void;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface GattService<br>差异内容：interface GattService|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattService；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattService；<br>API声明：isPrimary: boolean;<br>差异内容：isPrimary: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattService；<br>API声明：characteristics: Array\<BLECharacteristic>;<br>差异内容：characteristics: Array\<BLECharacteristic>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattService；<br>API声明：includeServices?: Array\<GattService>;<br>差异内容：includeServices?: Array\<GattService>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface BLECharacteristic<br>差异内容：interface BLECharacteristic|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BLECharacteristic；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BLECharacteristic；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BLECharacteristic；<br>API声明：characteristicValue: ArrayBuffer;<br>差异内容：characteristicValue: ArrayBuffer;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BLECharacteristic；<br>API声明：descriptors: Array\<BLEDescriptor>;<br>差异内容：descriptors: Array\<BLEDescriptor>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BLECharacteristic；<br>API声明：properties?: GattProperties;<br>差异内容：properties?: GattProperties;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface BLEDescriptor<br>差异内容：interface BLEDescriptor|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BLEDescriptor；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BLEDescriptor；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BLEDescriptor；<br>API声明：descriptorUuid: string;<br>差异内容：descriptorUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BLEDescriptor；<br>API声明：descriptorValue: ArrayBuffer;<br>差异内容：descriptorValue: ArrayBuffer;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface NotifyCharacteristic<br>差异内容：interface NotifyCharacteristic|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：NotifyCharacteristic；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：NotifyCharacteristic；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：NotifyCharacteristic；<br>API声明：characteristicValue: ArrayBuffer;<br>差异内容：characteristicValue: ArrayBuffer;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：NotifyCharacteristic；<br>API声明：confirm: boolean;<br>差异内容：confirm: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface CharacteristicReadRequest<br>差异内容：interface CharacteristicReadRequest|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：CharacteristicReadRequest；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：CharacteristicReadRequest；<br>API声明：transId: number;<br>差异内容：transId: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：CharacteristicReadRequest；<br>API声明：offset: number;<br>差异内容：offset: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：CharacteristicReadRequest；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：CharacteristicReadRequest；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface CharacteristicWriteRequest<br>差异内容：interface CharacteristicWriteRequest|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：CharacteristicWriteRequest；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：CharacteristicWriteRequest；<br>API声明：transId: number;<br>差异内容：transId: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：CharacteristicWriteRequest；<br>API声明：offset: number;<br>差异内容：offset: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：CharacteristicWriteRequest；<br>API声明：isPrepared: boolean;<br>差异内容：isPrepared: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：CharacteristicWriteRequest；<br>API声明：needRsp: boolean;<br>差异内容：needRsp: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：CharacteristicWriteRequest；<br>API声明：value: ArrayBuffer;<br>差异内容：value: ArrayBuffer;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：CharacteristicWriteRequest；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：CharacteristicWriteRequest；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface DescriptorReadRequest<br>差异内容：interface DescriptorReadRequest|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：DescriptorReadRequest；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：DescriptorReadRequest；<br>API声明：transId: number;<br>差异内容：transId: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：DescriptorReadRequest；<br>API声明：offset: number;<br>差异内容：offset: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：DescriptorReadRequest；<br>API声明：descriptorUuid: string;<br>差异内容：descriptorUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：DescriptorReadRequest；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：DescriptorReadRequest；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface DescriptorWriteRequest<br>差异内容：interface DescriptorWriteRequest|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：DescriptorWriteRequest；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：DescriptorWriteRequest；<br>API声明：transId: number;<br>差异内容：transId: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：DescriptorWriteRequest；<br>API声明：offset: number;<br>差异内容：offset: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：DescriptorWriteRequest；<br>API声明：isPrepared: boolean;<br>差异内容：isPrepared: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：DescriptorWriteRequest；<br>API声明：needRsp: boolean;<br>差异内容：needRsp: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：DescriptorWriteRequest；<br>API声明：value: ArrayBuffer;<br>差异内容：value: ArrayBuffer;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：DescriptorWriteRequest；<br>API声明：descriptorUuid: string;<br>差异内容：descriptorUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：DescriptorWriteRequest；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：DescriptorWriteRequest；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface ServerResponse<br>差异内容：interface ServerResponse|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ServerResponse；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ServerResponse；<br>API声明：transId: number;<br>差异内容：transId: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ServerResponse；<br>API声明：status: number;<br>差异内容：status: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ServerResponse；<br>API声明：offset: number;<br>差异内容：offset: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ServerResponse；<br>API声明：value: ArrayBuffer;<br>差异内容：value: ArrayBuffer;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface BLEConnectionChangeState<br>差异内容：interface BLEConnectionChangeState|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BLEConnectionChangeState；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：BLEConnectionChangeState；<br>API声明：state: ProfileConnectionState;<br>差异内容：state: ProfileConnectionState;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface ScanResult<br>差异内容：interface ScanResult|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanResult；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanResult；<br>API声明：rssi: number;<br>差异内容：rssi: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanResult；<br>API声明：data: ArrayBuffer;<br>差异内容：data: ArrayBuffer;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanResult；<br>API声明：deviceName: string;<br>差异内容：deviceName: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanResult；<br>API声明：connectable: boolean;<br>差异内容：connectable: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface AdvertiseSetting<br>差异内容：interface AdvertiseSetting|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertiseSetting；<br>API声明：interval?: number;<br>差异内容：interval?: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertiseSetting；<br>API声明：txPower?: number;<br>差异内容：txPower?: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertiseSetting；<br>API声明：connectable?: boolean;<br>差异内容：connectable?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface AdvertiseData<br>差异内容：interface AdvertiseData|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertiseData；<br>API声明：serviceUuids: Array\<string>;<br>差异内容：serviceUuids: Array\<string>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertiseData；<br>API声明：manufactureData: Array\<ManufactureData>;<br>差异内容：manufactureData: Array\<ManufactureData>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertiseData；<br>API声明：serviceData: Array\<ServiceData>;<br>差异内容：serviceData: Array\<ServiceData>;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertiseData；<br>API声明：includeDeviceName?: boolean;<br>差异内容：includeDeviceName?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface AdvertisingParams<br>差异内容：interface AdvertisingParams|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertisingParams；<br>API声明：advertisingSettings: AdvertiseSetting;<br>差异内容：advertisingSettings: AdvertiseSetting;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertisingParams；<br>API声明：advertisingData: AdvertiseData;<br>差异内容：advertisingData: AdvertiseData;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertisingParams；<br>API声明：advertisingResponse?: AdvertiseData;<br>差异内容：advertisingResponse?: AdvertiseData;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertisingParams；<br>API声明：duration?: number;<br>差异内容：duration?: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface AdvertisingEnableParams<br>差异内容：interface AdvertisingEnableParams|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertisingEnableParams；<br>API声明：advertisingId: number;<br>差异内容：advertisingId: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertisingEnableParams；<br>API声明：duration?: number;<br>差异内容：duration?: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface AdvertisingDisableParams<br>差异内容：interface AdvertisingDisableParams|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertisingDisableParams；<br>API声明：advertisingId: number;<br>差异内容：advertisingId: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface AdvertisingStateChangeInfo<br>差异内容：interface AdvertisingStateChangeInfo|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertisingStateChangeInfo；<br>API声明：advertisingId: number;<br>差异内容：advertisingId: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertisingStateChangeInfo；<br>API声明：state: AdvertisingState;<br>差异内容：state: AdvertisingState;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface ManufactureData<br>差异内容：interface ManufactureData|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ManufactureData；<br>API声明：manufactureId: number;<br>差异内容：manufactureId: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ManufactureData；<br>API声明：manufactureValue: ArrayBuffer;<br>差异内容：manufactureValue: ArrayBuffer;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface ServiceData<br>差异内容：interface ServiceData|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ServiceData；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ServiceData；<br>API声明：serviceValue: ArrayBuffer;<br>差异内容：serviceValue: ArrayBuffer;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface ScanFilter<br>差异内容：interface ScanFilter|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：deviceId?: string;<br>差异内容：deviceId?: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：name?: string;<br>差异内容：name?: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：serviceUuid?: string;<br>差异内容：serviceUuid?: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：serviceUuidMask?: string;<br>差异内容：serviceUuidMask?: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：serviceSolicitationUuid?: string;<br>差异内容：serviceSolicitationUuid?: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：serviceSolicitationUuidMask?: string;<br>差异内容：serviceSolicitationUuidMask?: string;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：serviceData?: ArrayBuffer;<br>差异内容：serviceData?: ArrayBuffer;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：serviceDataMask?: ArrayBuffer;<br>差异内容：serviceDataMask?: ArrayBuffer;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：manufactureId?: number;<br>差异内容：manufactureId?: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：manufactureData?: ArrayBuffer;<br>差异内容：manufactureData?: ArrayBuffer;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：manufactureDataMask?: ArrayBuffer;<br>差异内容：manufactureDataMask?: ArrayBuffer;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface ScanOptions<br>差异内容：interface ScanOptions|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanOptions；<br>API声明：interval?: number;<br>差异内容：interval?: number;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanOptions；<br>API声明：dutyMode?: ScanDuty;<br>差异内容：dutyMode?: ScanDuty;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanOptions；<br>API声明：matchMode?: MatchMode;<br>差异内容：matchMode?: MatchMode;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：interface GattProperties<br>差异内容：interface GattProperties|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattProperties；<br>API声明：write?: boolean;<br>差异内容：write?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattProperties；<br>API声明：writeNoResponse?: boolean;<br>差异内容：writeNoResponse?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattProperties；<br>API声明：read?: boolean;<br>差异内容：read?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattProperties；<br>API声明：notify?: boolean;<br>差异内容：notify?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattProperties；<br>API声明：indicate?: boolean;<br>差异内容：indicate?: boolean;|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：enum GattWriteType<br>差异内容：enum GattWriteType|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattWriteType；<br>API声明：WRITE = 1<br>差异内容：WRITE = 1|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：GattWriteType；<br>API声明：WRITE_NO_RESPONSE = 2<br>差异内容：WRITE_NO_RESPONSE = 2|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：enum ScanDuty<br>差异内容：enum ScanDuty|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanDuty；<br>API声明：SCAN_MODE_LOW_POWER = 0<br>差异内容：SCAN_MODE_LOW_POWER = 0|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanDuty；<br>API声明：SCAN_MODE_BALANCED = 1<br>差异内容：SCAN_MODE_BALANCED = 1|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ScanDuty；<br>API声明：SCAN_MODE_LOW_LATENCY = 2<br>差异内容：SCAN_MODE_LOW_LATENCY = 2|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：enum MatchMode<br>差异内容：enum MatchMode|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：MatchMode；<br>API声明：MATCH_MODE_AGGRESSIVE = 1<br>差异内容：MATCH_MODE_AGGRESSIVE = 1|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：MatchMode；<br>API声明：MATCH_MODE_STICKY = 2<br>差异内容：MATCH_MODE_STICKY = 2|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：ble；<br>API声明：enum AdvertisingState<br>差异内容：enum AdvertisingState|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertisingState；<br>API声明：STARTED = 1<br>差异内容：STARTED = 1|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertisingState；<br>API声明：ENABLED = 2<br>差异内容：ENABLED = 2|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertisingState；<br>API声明：DISABLED = 3<br>差异内容：DISABLED = 3|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：AdvertisingState；<br>API声明：STOPPED = 4<br>差异内容：STOPPED = 4|api/@ohos.bluetooth.ble.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace connection<br>差异内容：declare namespace connection|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：type ProfileConnectionState = constant.ProfileConnectionState;<br>差异内容：type ProfileConnectionState = constant.ProfileConnectionState;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：type ProfileId = constant.ProfileId;<br>差异内容：type ProfileId = constant.ProfileId;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：type MajorClass = constant.MajorClass;<br>差异内容：type MajorClass = constant.MajorClass;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：type MajorMinorClass = constant.MajorMinorClass;<br>差异内容：type MajorMinorClass = constant.MajorMinorClass;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getProfileConnectionState(profileId?: ProfileId): ProfileConnectionState;<br>差异内容：function getProfileConnectionState(profileId?: ProfileId): ProfileConnectionState;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function pairDevice(deviceId: string, callback: AsyncCallback\<void>): void;<br>差异内容：function pairDevice(deviceId: string, callback: AsyncCallback\<void>): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function pairDevice(deviceId: string): Promise\<void>;<br>差异内容：function pairDevice(deviceId: string): Promise\<void>;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getRemoteDeviceName(deviceId: string): string;<br>差异内容：function getRemoteDeviceName(deviceId: string): string;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getRemoteDeviceClass(deviceId: string): DeviceClass;<br>差异内容：function getRemoteDeviceClass(deviceId: string): DeviceClass;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getLocalName(): string;<br>差异内容：function getLocalName(): string;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getPairedDevices(): Array\<string>;<br>差异内容：function getPairedDevices(): Array\<string>;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getPairState(deviceId: string): BondState;<br>差异内容：function getPairState(deviceId: string): BondState;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function setDevicePairingConfirmation(deviceId: string, accept: boolean): void;<br>差异内容：function setDevicePairingConfirmation(deviceId: string, accept: boolean): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function setDevicePinCode(deviceId: string, code: string, callback: AsyncCallback\<void>): void;<br>差异内容：function setDevicePinCode(deviceId: string, code: string, callback: AsyncCallback\<void>): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function setDevicePinCode(deviceId: string, code: string): Promise\<void>;<br>差异内容：function setDevicePinCode(deviceId: string, code: string): Promise\<void>;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function setLocalName(name: string): void;<br>差异内容：function setLocalName(name: string): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function setBluetoothScanMode(mode: ScanMode, duration: number): void;<br>差异内容：function setBluetoothScanMode(mode: ScanMode, duration: number): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getBluetoothScanMode(): ScanMode;<br>差异内容：function getBluetoothScanMode(): ScanMode;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function startBluetoothDiscovery(): void;<br>差异内容：function startBluetoothDiscovery(): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function stopBluetoothDiscovery(): void;<br>差异内容：function stopBluetoothDiscovery(): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function isBluetoothDiscovering(): boolean;<br>差异内容：function isBluetoothDiscovering(): boolean;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function on(type: 'bluetoothDeviceFind', callback: Callback\<Array\<string>>): void;<br>差异内容：function on(type: 'bluetoothDeviceFind', callback: Callback\<Array\<string>>): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function off(type: 'bluetoothDeviceFind', callback?: Callback\<Array\<string>>): void;<br>差异内容：function off(type: 'bluetoothDeviceFind', callback?: Callback\<Array\<string>>): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function on(type: 'bondStateChange', callback: Callback\<BondStateParam>): void;<br>差异内容：function on(type: 'bondStateChange', callback: Callback\<BondStateParam>): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function off(type: 'bondStateChange', callback?: Callback\<BondStateParam>): void;<br>差异内容：function off(type: 'bondStateChange', callback?: Callback\<BondStateParam>): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function on(type: 'pinRequired', callback: Callback\<PinRequiredParam>): void;<br>差异内容：function on(type: 'pinRequired', callback: Callback\<PinRequiredParam>): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function off(type: 'pinRequired', callback?: Callback\<PinRequiredParam>): void;<br>差异内容：function off(type: 'pinRequired', callback?: Callback\<PinRequiredParam>): void;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：interface BondStateParam<br>差异内容：interface BondStateParam|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：BondStateParam；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：BondStateParam；<br>API声明：state: BondState;<br>差异内容：state: BondState;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：interface PinRequiredParam<br>差异内容：interface PinRequiredParam|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：PinRequiredParam；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：PinRequiredParam；<br>API声明：pinCode: string;<br>差异内容：pinCode: string;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：interface DeviceClass<br>差异内容：interface DeviceClass|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：DeviceClass；<br>API声明：majorClass: MajorClass;<br>差异内容：majorClass: MajorClass;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：DeviceClass；<br>API声明：majorMinorClass: MajorMinorClass;<br>差异内容：majorMinorClass: MajorMinorClass;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：DeviceClass；<br>API声明：classOfDevice: number;<br>差异内容：classOfDevice: number;|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：enum BluetoothTransport<br>差异内容：enum BluetoothTransport|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：BluetoothTransport；<br>API声明：TRANSPORT_BR_EDR = 0<br>差异内容：TRANSPORT_BR_EDR = 0|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：BluetoothTransport；<br>API声明：TRANSPORT_LE = 1<br>差异内容：TRANSPORT_LE = 1|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：enum ScanMode<br>差异内容：enum ScanMode|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：ScanMode；<br>API声明：SCAN_MODE_NONE = 0<br>差异内容：SCAN_MODE_NONE = 0|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：ScanMode；<br>API声明：SCAN_MODE_CONNECTABLE = 1<br>差异内容：SCAN_MODE_CONNECTABLE = 1|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：ScanMode；<br>API声明：SCAN_MODE_GENERAL_DISCOVERABLE = 2<br>差异内容：SCAN_MODE_GENERAL_DISCOVERABLE = 2|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：ScanMode；<br>API声明：SCAN_MODE_LIMITED_DISCOVERABLE = 3<br>差异内容：SCAN_MODE_LIMITED_DISCOVERABLE = 3|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：ScanMode；<br>API声明：SCAN_MODE_CONNECTABLE_GENERAL_DISCOVERABLE = 4<br>差异内容：SCAN_MODE_CONNECTABLE_GENERAL_DISCOVERABLE = 4|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：ScanMode；<br>API声明：SCAN_MODE_CONNECTABLE_LIMITED_DISCOVERABLE = 5<br>差异内容：SCAN_MODE_CONNECTABLE_LIMITED_DISCOVERABLE = 5|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：enum BondState<br>差异内容：enum BondState|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：BondState；<br>API声明：BOND_STATE_INVALID = 0<br>差异内容：BOND_STATE_INVALID = 0|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：BondState；<br>API声明：BOND_STATE_BONDING = 1<br>差异内容：BOND_STATE_BONDING = 1|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：BondState；<br>API声明：BOND_STATE_BONDED = 2<br>差异内容：BOND_STATE_BONDED = 2|api/@ohos.bluetooth.connection.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace constant<br>差异内容：declare namespace constant|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：constant；<br>API声明：export enum ProfileId<br>差异内容：export enum ProfileId|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：ProfileId；<br>API声明：PROFILE_A2DP_SOURCE = 1<br>差异内容：PROFILE_A2DP_SOURCE = 1|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：ProfileId；<br>API声明：PROFILE_HANDSFREE_AUDIO_GATEWAY = 4<br>差异内容：PROFILE_HANDSFREE_AUDIO_GATEWAY = 4|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：ProfileId；<br>API声明：PROFILE_HID_HOST = 6<br>差异内容：PROFILE_HID_HOST = 6|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：ProfileId；<br>API声明：PROFILE_PAN_NETWORK = 7<br>差异内容：PROFILE_PAN_NETWORK = 7|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：constant；<br>API声明：export enum ProfileConnectionState<br>差异内容：export enum ProfileConnectionState|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：ProfileConnectionState；<br>API声明：STATE_DISCONNECTED = 0<br>差异内容：STATE_DISCONNECTED = 0|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：ProfileConnectionState；<br>API声明：STATE_CONNECTING = 1<br>差异内容：STATE_CONNECTING = 1|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：ProfileConnectionState；<br>API声明：STATE_CONNECTED = 2<br>差异内容：STATE_CONNECTED = 2|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：ProfileConnectionState；<br>API声明：STATE_DISCONNECTING = 3<br>差异内容：STATE_DISCONNECTING = 3|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：constant；<br>API声明：export enum MajorClass<br>差异内容：export enum MajorClass|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_MISC = 0x0000<br>差异内容：MAJOR_MISC = 0x0000|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_COMPUTER = 0x0100<br>差异内容：MAJOR_COMPUTER = 0x0100|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_PHONE = 0x0200<br>差异内容：MAJOR_PHONE = 0x0200|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_NETWORKING = 0x0300<br>差异内容：MAJOR_NETWORKING = 0x0300|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_AUDIO_VIDEO = 0x0400<br>差异内容：MAJOR_AUDIO_VIDEO = 0x0400|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_PERIPHERAL = 0x0500<br>差异内容：MAJOR_PERIPHERAL = 0x0500|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_IMAGING = 0x0600<br>差异内容：MAJOR_IMAGING = 0x0600|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_WEARABLE = 0x0700<br>差异内容：MAJOR_WEARABLE = 0x0700|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_TOY = 0x0800<br>差异内容：MAJOR_TOY = 0x0800|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_HEALTH = 0x0900<br>差异内容：MAJOR_HEALTH = 0x0900|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_UNCATEGORIZED = 0x1F00<br>差异内容：MAJOR_UNCATEGORIZED = 0x1F00|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：constant；<br>API声明：export enum MajorMinorClass<br>差异内容：export enum MajorMinorClass|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_UNCATEGORIZED = 0x0100<br>差异内容：COMPUTER_UNCATEGORIZED = 0x0100|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_DESKTOP = 0x0104<br>差异内容：COMPUTER_DESKTOP = 0x0104|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_SERVER = 0x0108<br>差异内容：COMPUTER_SERVER = 0x0108|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_LAPTOP = 0x010C<br>差异内容：COMPUTER_LAPTOP = 0x010C|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_HANDHELD_PC_PDA = 0x0110<br>差异内容：COMPUTER_HANDHELD_PC_PDA = 0x0110|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_PALM_SIZE_PC_PDA = 0x0114<br>差异内容：COMPUTER_PALM_SIZE_PC_PDA = 0x0114|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_WEARABLE = 0x0118<br>差异内容：COMPUTER_WEARABLE = 0x0118|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_TABLET = 0x011C<br>差异内容：COMPUTER_TABLET = 0x011C|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PHONE_UNCATEGORIZED = 0x0200<br>差异内容：PHONE_UNCATEGORIZED = 0x0200|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PHONE_CELLULAR = 0x0204<br>差异内容：PHONE_CELLULAR = 0x0204|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PHONE_CORDLESS = 0x0208<br>差异内容：PHONE_CORDLESS = 0x0208|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PHONE_SMART = 0x020C<br>差异内容：PHONE_SMART = 0x020C|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PHONE_MODEM_OR_GATEWAY = 0x0210<br>差异内容：PHONE_MODEM_OR_GATEWAY = 0x0210|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PHONE_ISDN = 0x0214<br>差异内容：PHONE_ISDN = 0x0214|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_FULLY_AVAILABLE = 0x0300<br>差异内容：NETWORK_FULLY_AVAILABLE = 0x0300|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_1_TO_17_UTILIZED = 0x0320<br>差异内容：NETWORK_1_TO_17_UTILIZED = 0x0320|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_17_TO_33_UTILIZED = 0x0340<br>差异内容：NETWORK_17_TO_33_UTILIZED = 0x0340|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_33_TO_50_UTILIZED = 0x0360<br>差异内容：NETWORK_33_TO_50_UTILIZED = 0x0360|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_60_TO_67_UTILIZED = 0x0380<br>差异内容：NETWORK_60_TO_67_UTILIZED = 0x0380|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_67_TO_83_UTILIZED = 0x03A0<br>差异内容：NETWORK_67_TO_83_UTILIZED = 0x03A0|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_83_TO_99_UTILIZED = 0x03C0<br>差异内容：NETWORK_83_TO_99_UTILIZED = 0x03C0|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_NO_SERVICE = 0x03E0<br>差异内容：NETWORK_NO_SERVICE = 0x03E0|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_UNCATEGORIZED = 0x0400<br>差异内容：AUDIO_VIDEO_UNCATEGORIZED = 0x0400|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_WEARABLE_HEADSET = 0x0404<br>差异内容：AUDIO_VIDEO_WEARABLE_HEADSET = 0x0404|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_HANDSFREE = 0x0408<br>差异内容：AUDIO_VIDEO_HANDSFREE = 0x0408|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_MICROPHONE = 0x0410<br>差异内容：AUDIO_VIDEO_MICROPHONE = 0x0410|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_LOUDSPEAKER = 0x0414<br>差异内容：AUDIO_VIDEO_LOUDSPEAKER = 0x0414|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_HEADPHONES = 0x0418<br>差异内容：AUDIO_VIDEO_HEADPHONES = 0x0418|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_PORTABLE_AUDIO = 0x041C<br>差异内容：AUDIO_VIDEO_PORTABLE_AUDIO = 0x041C|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_CAR_AUDIO = 0x0420<br>差异内容：AUDIO_VIDEO_CAR_AUDIO = 0x0420|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_SET_TOP_BOX = 0x0424<br>差异内容：AUDIO_VIDEO_SET_TOP_BOX = 0x0424|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_HIFI_AUDIO = 0x0428<br>差异内容：AUDIO_VIDEO_HIFI_AUDIO = 0x0428|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_VCR = 0x042C<br>差异内容：AUDIO_VIDEO_VCR = 0x042C|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_VIDEO_CAMERA = 0x0430<br>差异内容：AUDIO_VIDEO_VIDEO_CAMERA = 0x0430|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_CAMCORDER = 0x0434<br>差异内容：AUDIO_VIDEO_CAMCORDER = 0x0434|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_VIDEO_MONITOR = 0x0438<br>差异内容：AUDIO_VIDEO_VIDEO_MONITOR = 0x0438|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_VIDEO_DISPLAY_AND_LOUDSPEAKER = 0x043C<br>差异内容：AUDIO_VIDEO_VIDEO_DISPLAY_AND_LOUDSPEAKER = 0x043C|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_VIDEO_CONFERENCING = 0x0440<br>差异内容：AUDIO_VIDEO_VIDEO_CONFERENCING = 0x0440|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_VIDEO_GAMING_TOY = 0x0448<br>差异内容：AUDIO_VIDEO_VIDEO_GAMING_TOY = 0x0448|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_NON_KEYBOARD_NON_POINTING = 0x0500<br>差异内容：PERIPHERAL_NON_KEYBOARD_NON_POINTING = 0x0500|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_KEYBOARD = 0x0540<br>差异内容：PERIPHERAL_KEYBOARD = 0x0540|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_POINTING_DEVICE = 0x0580<br>差异内容：PERIPHERAL_POINTING_DEVICE = 0x0580|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_KEYBOARD_POINTING = 0x05C0<br>差异内容：PERIPHERAL_KEYBOARD_POINTING = 0x05C0|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_UNCATEGORIZED = 0x0500<br>差异内容：PERIPHERAL_UNCATEGORIZED = 0x0500|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_JOYSTICK = 0x0504<br>差异内容：PERIPHERAL_JOYSTICK = 0x0504|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_GAMEPAD = 0x0508<br>差异内容：PERIPHERAL_GAMEPAD = 0x0508|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_REMOTE_CONTROL = 0x05C0<br>差异内容：PERIPHERAL_REMOTE_CONTROL = 0x05C0|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_SENSING_DEVICE = 0x0510<br>差异内容：PERIPHERAL_SENSING_DEVICE = 0x0510|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_DIGITIZER_TABLET = 0x0514<br>差异内容：PERIPHERAL_DIGITIZER_TABLET = 0x0514|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_CARD_READER = 0x0518<br>差异内容：PERIPHERAL_CARD_READER = 0x0518|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_DIGITAL_PEN = 0x051C<br>差异内容：PERIPHERAL_DIGITAL_PEN = 0x051C|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_SCANNER_RFID = 0x0520<br>差异内容：PERIPHERAL_SCANNER_RFID = 0x0520|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_GESTURAL_INPUT = 0x0522<br>差异内容：PERIPHERAL_GESTURAL_INPUT = 0x0522|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：IMAGING_UNCATEGORIZED = 0x0600<br>差异内容：IMAGING_UNCATEGORIZED = 0x0600|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：IMAGING_DISPLAY = 0x0610<br>差异内容：IMAGING_DISPLAY = 0x0610|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：IMAGING_CAMERA = 0x0620<br>差异内容：IMAGING_CAMERA = 0x0620|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：IMAGING_SCANNER = 0x0640<br>差异内容：IMAGING_SCANNER = 0x0640|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：IMAGING_PRINTER = 0x0680<br>差异内容：IMAGING_PRINTER = 0x0680|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：WEARABLE_UNCATEGORIZED = 0x0700<br>差异内容：WEARABLE_UNCATEGORIZED = 0x0700|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：WEARABLE_WRIST_WATCH = 0x0704<br>差异内容：WEARABLE_WRIST_WATCH = 0x0704|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：WEARABLE_PAGER = 0x0708<br>差异内容：WEARABLE_PAGER = 0x0708|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：WEARABLE_JACKET = 0x070C<br>差异内容：WEARABLE_JACKET = 0x070C|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：WEARABLE_HELMET = 0x0710<br>差异内容：WEARABLE_HELMET = 0x0710|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：WEARABLE_GLASSES = 0x0714<br>差异内容：WEARABLE_GLASSES = 0x0714|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：TOY_UNCATEGORIZED = 0x0800<br>差异内容：TOY_UNCATEGORIZED = 0x0800|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：TOY_ROBOT = 0x0804<br>差异内容：TOY_ROBOT = 0x0804|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：TOY_VEHICLE = 0x0808<br>差异内容：TOY_VEHICLE = 0x0808|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：TOY_DOLL_ACTION_FIGURE = 0x080C<br>差异内容：TOY_DOLL_ACTION_FIGURE = 0x080C|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：TOY_CONTROLLER = 0x0810<br>差异内容：TOY_CONTROLLER = 0x0810|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：TOY_GAME = 0x0814<br>差异内容：TOY_GAME = 0x0814|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_UNCATEGORIZED = 0x0900<br>差异内容：HEALTH_UNCATEGORIZED = 0x0900|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_BLOOD_PRESSURE = 0x0904<br>差异内容：HEALTH_BLOOD_PRESSURE = 0x0904|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_THERMOMETER = 0x0908<br>差异内容：HEALTH_THERMOMETER = 0x0908|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_WEIGHING = 0x090C<br>差异内容：HEALTH_WEIGHING = 0x090C|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_GLUCOSE = 0x0910<br>差异内容：HEALTH_GLUCOSE = 0x0910|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_PULSE_OXIMETER = 0x0914<br>差异内容：HEALTH_PULSE_OXIMETER = 0x0914|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_PULSE_RATE = 0x0918<br>差异内容：HEALTH_PULSE_RATE = 0x0918|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_DATA_DISPLAY = 0x091C<br>差异内容：HEALTH_DATA_DISPLAY = 0x091C|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_STEP_COUNTER = 0x0920<br>差异内容：HEALTH_STEP_COUNTER = 0x0920|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_BODY_COMPOSITION_ANALYZER = 0x0924<br>差异内容：HEALTH_BODY_COMPOSITION_ANALYZER = 0x0924|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_PEAK_FLOW_MONITOR = 0x0928<br>差异内容：HEALTH_PEAK_FLOW_MONITOR = 0x0928|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_MEDICATION_MONITOR = 0x092C<br>差异内容：HEALTH_MEDICATION_MONITOR = 0x092C|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_KNEE_PROSTHESIS = 0x0930<br>差异内容：HEALTH_KNEE_PROSTHESIS = 0x0930|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_ANKLE_PROSTHESIS = 0x0934<br>差异内容：HEALTH_ANKLE_PROSTHESIS = 0x0934|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_GENERIC_HEALTH_MANAGER = 0x0938<br>差异内容：HEALTH_GENERIC_HEALTH_MANAGER = 0x0938|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_PERSONAL_MOBILITY_DEVICE = 0x093C<br>差异内容：HEALTH_PERSONAL_MOBILITY_DEVICE = 0x093C|api/@ohos.bluetooth.constant.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace bluetooth<br>差异内容：declare namespace bluetooth|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function getState(): BluetoothState;<br>差异内容：function getState(): BluetoothState;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function getBtConnectionState(): ProfileConnectionState;<br>差异内容：function getBtConnectionState(): ProfileConnectionState;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function pairDevice(deviceId: string): boolean;<br>差异内容：function pairDevice(deviceId: string): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function getRemoteDeviceName(deviceId: string): string;<br>差异内容：function getRemoteDeviceName(deviceId: string): string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function getRemoteDeviceClass(deviceId: string): DeviceClass;<br>差异内容：function getRemoteDeviceClass(deviceId: string): DeviceClass;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function enableBluetooth(): boolean;<br>差异内容：function enableBluetooth(): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function disableBluetooth(): boolean;<br>差异内容：function disableBluetooth(): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function getLocalName(): string;<br>差异内容：function getLocalName(): string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function getPairedDevices(): Array\<string>;<br>差异内容：function getPairedDevices(): Array\<string>;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function getProfileConnState(profileId: ProfileId): ProfileConnectionState;<br>差异内容：function getProfileConnState(profileId: ProfileId): ProfileConnectionState;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function setDevicePairingConfirmation(device: string, accept: boolean): boolean;<br>差异内容：function setDevicePairingConfirmation(device: string, accept: boolean): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function setLocalName(name: string): boolean;<br>差异内容：function setLocalName(name: string): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function setBluetoothScanMode(mode: ScanMode, duration: number): boolean;<br>差异内容：function setBluetoothScanMode(mode: ScanMode, duration: number): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function getBluetoothScanMode(): ScanMode;<br>差异内容：function getBluetoothScanMode(): ScanMode;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function startBluetoothDiscovery(): boolean;<br>差异内容：function startBluetoothDiscovery(): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function stopBluetoothDiscovery(): boolean;<br>差异内容：function stopBluetoothDiscovery(): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function on(type: 'bluetoothDeviceFind', callback: Callback\<Array\<string>>): void;<br>差异内容：function on(type: 'bluetoothDeviceFind', callback: Callback\<Array\<string>>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function off(type: 'bluetoothDeviceFind', callback?: Callback\<Array\<string>>): void;<br>差异内容：function off(type: 'bluetoothDeviceFind', callback?: Callback\<Array\<string>>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function on(type: 'bondStateChange', callback: Callback\<BondStateParam>): void;<br>差异内容：function on(type: 'bondStateChange', callback: Callback\<BondStateParam>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function off(type: 'bondStateChange', callback?: Callback\<BondStateParam>): void;<br>差异内容：function off(type: 'bondStateChange', callback?: Callback\<BondStateParam>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function on(type: 'pinRequired', callback: Callback\<PinRequiredParam>): void;<br>差异内容：function on(type: 'pinRequired', callback: Callback\<PinRequiredParam>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function off(type: 'pinRequired', callback?: Callback\<PinRequiredParam>): void;<br>差异内容：function off(type: 'pinRequired', callback?: Callback\<PinRequiredParam>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function on(type: 'stateChange', callback: Callback\<BluetoothState>): void;<br>差异内容：function on(type: 'stateChange', callback: Callback\<BluetoothState>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function off(type: 'stateChange', callback?: Callback\<BluetoothState>): void;<br>差异内容：function off(type: 'stateChange', callback?: Callback\<BluetoothState>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function sppListen(name: string, option: SppOption, callback: AsyncCallback\<number>): void;<br>差异内容：function sppListen(name: string, option: SppOption, callback: AsyncCallback\<number>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function sppAccept(serverSocket: number, callback: AsyncCallback\<number>): void;<br>差异内容：function sppAccept(serverSocket: number, callback: AsyncCallback\<number>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function sppConnect(device: string, option: SppOption, callback: AsyncCallback\<number>): void;<br>差异内容：function sppConnect(device: string, option: SppOption, callback: AsyncCallback\<number>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function sppCloseServerSocket(socket: number): void;<br>差异内容：function sppCloseServerSocket(socket: number): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function sppCloseClientSocket(socket: number): void;<br>差异内容：function sppCloseClientSocket(socket: number): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function sppWrite(clientSocket: number, data: ArrayBuffer): boolean;<br>差异内容：function sppWrite(clientSocket: number, data: ArrayBuffer): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function on(type: 'sppRead', clientSocket: number, callback: Callback\<ArrayBuffer>): void;<br>差异内容：function on(type: 'sppRead', clientSocket: number, callback: Callback\<ArrayBuffer>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function off(type: 'sppRead', clientSocket: number, callback?: Callback\<ArrayBuffer>): void;<br>差异内容：function off(type: 'sppRead', clientSocket: number, callback?: Callback\<ArrayBuffer>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：function getProfile(profileId: ProfileId): A2dpSourceProfile \| HandsFreeAudioGatewayProfile;<br>差异内容：function getProfile(profileId: ProfileId): A2dpSourceProfile \| HandsFreeAudioGatewayProfile;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface BaseProfile<br>差异内容：interface BaseProfile|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BaseProfile；<br>API声明：getConnectionDevices(): Array\<string>;<br>差异内容：getConnectionDevices(): Array\<string>;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BaseProfile；<br>API声明：getDeviceState(device: string): ProfileConnectionState;<br>差异内容：getDeviceState(device: string): ProfileConnectionState;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface A2dpSourceProfile<br>差异内容：interface A2dpSourceProfile|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：A2dpSourceProfile；<br>API声明：connect(device: string): boolean;<br>差异内容：connect(device: string): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：A2dpSourceProfile；<br>API声明：disconnect(device: string): boolean;<br>差异内容：disconnect(device: string): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：A2dpSourceProfile；<br>API声明：on(type: 'connectionStateChange', callback: Callback\<StateChangeParam>): void;<br>差异内容：on(type: 'connectionStateChange', callback: Callback\<StateChangeParam>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：A2dpSourceProfile；<br>API声明：off(type: 'connectionStateChange', callback?: Callback\<StateChangeParam>): void;<br>差异内容：off(type: 'connectionStateChange', callback?: Callback\<StateChangeParam>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：A2dpSourceProfile；<br>API声明：getPlayingState(device: string): PlayingState;<br>差异内容：getPlayingState(device: string): PlayingState;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface HandsFreeAudioGatewayProfile<br>差异内容：interface HandsFreeAudioGatewayProfile|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：HandsFreeAudioGatewayProfile；<br>API声明：connect(device: string): boolean;<br>差异内容：connect(device: string): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：HandsFreeAudioGatewayProfile；<br>API声明：disconnect(device: string): boolean;<br>差异内容：disconnect(device: string): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：HandsFreeAudioGatewayProfile；<br>API声明：on(type: 'connectionStateChange', callback: Callback\<StateChangeParam>): void;<br>差异内容：on(type: 'connectionStateChange', callback: Callback\<StateChangeParam>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：HandsFreeAudioGatewayProfile；<br>API声明：off(type: 'connectionStateChange', callback?: Callback\<StateChangeParam>): void;<br>差异内容：off(type: 'connectionStateChange', callback?: Callback\<StateChangeParam>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：namespace BLE<br>差异内容：namespace BLE|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BLE；<br>API声明：function createGattServer(): GattServer;<br>差异内容：function createGattServer(): GattServer;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BLE；<br>API声明：function createGattClientDevice(deviceId: string): GattClientDevice;<br>差异内容：function createGattClientDevice(deviceId: string): GattClientDevice;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BLE；<br>API声明：function getConnectedBLEDevices(): Array\<string>;<br>差异内容：function getConnectedBLEDevices(): Array\<string>;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BLE；<br>API声明：function startBLEScan(filters: Array\<ScanFilter>, options?: ScanOptions): void;<br>差异内容：function startBLEScan(filters: Array\<ScanFilter>, options?: ScanOptions): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BLE；<br>API声明：function stopBLEScan(): void;<br>差异内容：function stopBLEScan(): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BLE；<br>API声明：function on(type: 'BLEDeviceFind', callback: Callback\<Array\<ScanResult>>): void;<br>差异内容：function on(type: 'BLEDeviceFind', callback: Callback\<Array\<ScanResult>>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BLE；<br>API声明：function off(type: 'BLEDeviceFind', callback?: Callback\<Array\<ScanResult>>): void;<br>差异内容：function off(type: 'BLEDeviceFind', callback?: Callback\<Array\<ScanResult>>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface GattServer<br>差异内容：interface GattServer|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：startAdvertising(setting: AdvertiseSetting, advData: AdvertiseData, advResponse?: AdvertiseData): void;<br>差异内容：startAdvertising(setting: AdvertiseSetting, advData: AdvertiseData, advResponse?: AdvertiseData): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：stopAdvertising(): void;<br>差异内容：stopAdvertising(): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：addService(service: GattService): boolean;<br>差异内容：addService(service: GattService): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：removeService(serviceUuid: string): boolean;<br>差异内容：removeService(serviceUuid: string): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：close(): void;<br>差异内容：close(): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：notifyCharacteristicChanged(deviceId: string, notifyCharacteristic: NotifyCharacteristic): boolean;<br>差异内容：notifyCharacteristicChanged(deviceId: string, notifyCharacteristic: NotifyCharacteristic): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：sendResponse(serverResponse: ServerResponse): boolean;<br>差异内容：sendResponse(serverResponse: ServerResponse): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：on(type: 'characteristicRead', callback: Callback\<CharacteristicReadReq>): void;<br>差异内容：on(type: 'characteristicRead', callback: Callback\<CharacteristicReadReq>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：off(type: 'characteristicRead', callback?: Callback\<CharacteristicReadReq>): void;<br>差异内容：off(type: 'characteristicRead', callback?: Callback\<CharacteristicReadReq>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：on(type: 'characteristicWrite', callback: Callback\<CharacteristicWriteReq>): void;<br>差异内容：on(type: 'characteristicWrite', callback: Callback\<CharacteristicWriteReq>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：off(type: 'characteristicWrite', callback?: Callback\<CharacteristicWriteReq>): void;<br>差异内容：off(type: 'characteristicWrite', callback?: Callback\<CharacteristicWriteReq>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：on(type: 'descriptorRead', callback: Callback\<DescriptorReadReq>): void;<br>差异内容：on(type: 'descriptorRead', callback: Callback\<DescriptorReadReq>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：off(type: 'descriptorRead', callback?: Callback\<DescriptorReadReq>): void;<br>差异内容：off(type: 'descriptorRead', callback?: Callback\<DescriptorReadReq>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：on(type: 'descriptorWrite', callback: Callback\<DescriptorWriteReq>): void;<br>差异内容：on(type: 'descriptorWrite', callback: Callback\<DescriptorWriteReq>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：off(type: 'descriptorWrite', callback?: Callback\<DescriptorWriteReq>): void;<br>差异内容：off(type: 'descriptorWrite', callback?: Callback\<DescriptorWriteReq>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：on(type: 'connectStateChange', callback: Callback\<BLEConnectChangedState>): void;<br>差异内容：on(type: 'connectStateChange', callback: Callback\<BLEConnectChangedState>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：off(type: 'connectStateChange', callback?: Callback\<BLEConnectChangedState>): void;<br>差异内容：off(type: 'connectStateChange', callback?: Callback\<BLEConnectChangedState>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface GattClientDevice<br>差异内容：interface GattClientDevice|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：connect(): boolean;<br>差异内容：connect(): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：disconnect(): boolean;<br>差异内容：disconnect(): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：close(): boolean;<br>差异内容：close(): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：getDeviceName(callback: AsyncCallback\<string>): void;<br>差异内容：getDeviceName(callback: AsyncCallback\<string>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：getDeviceName(): Promise\<string>;<br>差异内容：getDeviceName(): Promise\<string>;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：getServices(callback: AsyncCallback\<Array\<GattService>>): void;<br>差异内容：getServices(callback: AsyncCallback\<Array\<GattService>>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：getServices(): Promise\<Array\<GattService>>;<br>差异内容：getServices(): Promise\<Array\<GattService>>;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：readCharacteristicValue(characteristic: BLECharacteristic, callback: AsyncCallback\<BLECharacteristic>): void;<br>差异内容：readCharacteristicValue(characteristic: BLECharacteristic, callback: AsyncCallback\<BLECharacteristic>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：readCharacteristicValue(characteristic: BLECharacteristic): Promise\<BLECharacteristic>;<br>差异内容：readCharacteristicValue(characteristic: BLECharacteristic): Promise\<BLECharacteristic>;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：readDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback\<BLEDescriptor>): void;<br>差异内容：readDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback\<BLEDescriptor>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：readDescriptorValue(descriptor: BLEDescriptor): Promise\<BLEDescriptor>;<br>差异内容：readDescriptorValue(descriptor: BLEDescriptor): Promise\<BLEDescriptor>;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：writeCharacteristicValue(characteristic: BLECharacteristic): boolean;<br>差异内容：writeCharacteristicValue(characteristic: BLECharacteristic): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：writeDescriptorValue(descriptor: BLEDescriptor): boolean;<br>差异内容：writeDescriptorValue(descriptor: BLEDescriptor): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：getRssiValue(callback: AsyncCallback\<number>): void;<br>差异内容：getRssiValue(callback: AsyncCallback\<number>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：getRssiValue(): Promise\<number>;<br>差异内容：getRssiValue(): Promise\<number>;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：setBLEMtuSize(mtu: number): boolean;<br>差异内容：setBLEMtuSize(mtu: number): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：setNotifyCharacteristicChanged(characteristic: BLECharacteristic, enable: boolean): boolean;<br>差异内容：setNotifyCharacteristicChanged(characteristic: BLECharacteristic, enable: boolean): boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：on(type: 'BLECharacteristicChange', callback: Callback\<BLECharacteristic>): void;<br>差异内容：on(type: 'BLECharacteristicChange', callback: Callback\<BLECharacteristic>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：off(type: 'BLECharacteristicChange', callback?: Callback\<BLECharacteristic>): void;<br>差异内容：off(type: 'BLECharacteristicChange', callback?: Callback\<BLECharacteristic>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：on(type: 'BLEConnectionStateChange', callback: Callback\<BLEConnectChangedState>): void;<br>差异内容：on(type: 'BLEConnectionStateChange', callback: Callback\<BLEConnectChangedState>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：off(type: 'BLEConnectionStateChange', callback?: Callback\<BLEConnectChangedState>): void;<br>差异内容：off(type: 'BLEConnectionStateChange', callback?: Callback\<BLEConnectChangedState>): void;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface GattService<br>差异内容：interface GattService|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattService；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattService；<br>API声明：isPrimary: boolean;<br>差异内容：isPrimary: boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattService；<br>API声明：characteristics: Array\<BLECharacteristic>;<br>差异内容：characteristics: Array\<BLECharacteristic>;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：GattService；<br>API声明：includeServices?: Array\<GattService>;<br>差异内容：includeServices?: Array\<GattService>;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface BLECharacteristic<br>差异内容：interface BLECharacteristic|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BLECharacteristic；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BLECharacteristic；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BLECharacteristic；<br>API声明：characteristicValue: ArrayBuffer;<br>差异内容：characteristicValue: ArrayBuffer;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BLECharacteristic；<br>API声明：descriptors: Array\<BLEDescriptor>;<br>差异内容：descriptors: Array\<BLEDescriptor>;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface BLEDescriptor<br>差异内容：interface BLEDescriptor|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BLEDescriptor；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BLEDescriptor；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BLEDescriptor；<br>API声明：descriptorUuid: string;<br>差异内容：descriptorUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BLEDescriptor；<br>API声明：descriptorValue: ArrayBuffer;<br>差异内容：descriptorValue: ArrayBuffer;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface NotifyCharacteristic<br>差异内容：interface NotifyCharacteristic|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：NotifyCharacteristic；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：NotifyCharacteristic；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：NotifyCharacteristic；<br>API声明：characteristicValue: ArrayBuffer;<br>差异内容：characteristicValue: ArrayBuffer;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：NotifyCharacteristic；<br>API声明：confirm: boolean;<br>差异内容：confirm: boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface CharacteristicReadReq<br>差异内容：interface CharacteristicReadReq|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：CharacteristicReadReq；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：CharacteristicReadReq；<br>API声明：transId: number;<br>差异内容：transId: number;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：CharacteristicReadReq；<br>API声明：offset: number;<br>差异内容：offset: number;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：CharacteristicReadReq；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：CharacteristicReadReq；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface CharacteristicWriteReq<br>差异内容：interface CharacteristicWriteReq|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：CharacteristicWriteReq；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：CharacteristicWriteReq；<br>API声明：transId: number;<br>差异内容：transId: number;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：CharacteristicWriteReq；<br>API声明：offset: number;<br>差异内容：offset: number;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：CharacteristicWriteReq；<br>API声明：isPrep: boolean;<br>差异内容：isPrep: boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：CharacteristicWriteReq；<br>API声明：needRsp: boolean;<br>差异内容：needRsp: boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：CharacteristicWriteReq；<br>API声明：value: ArrayBuffer;<br>差异内容：value: ArrayBuffer;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：CharacteristicWriteReq；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：CharacteristicWriteReq；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface DescriptorReadReq<br>差异内容：interface DescriptorReadReq|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：DescriptorReadReq；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：DescriptorReadReq；<br>API声明：transId: number;<br>差异内容：transId: number;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：DescriptorReadReq；<br>API声明：offset: number;<br>差异内容：offset: number;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：DescriptorReadReq；<br>API声明：descriptorUuid: string;<br>差异内容：descriptorUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：DescriptorReadReq；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：DescriptorReadReq；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface DescriptorWriteReq<br>差异内容：interface DescriptorWriteReq|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：DescriptorWriteReq；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：DescriptorWriteReq；<br>API声明：transId: number;<br>差异内容：transId: number;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：DescriptorWriteReq；<br>API声明：offset: number;<br>差异内容：offset: number;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：DescriptorWriteReq；<br>API声明：isPrep: boolean;<br>差异内容：isPrep: boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：DescriptorWriteReq；<br>API声明：needRsp: boolean;<br>差异内容：needRsp: boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：DescriptorWriteReq；<br>API声明：value: ArrayBuffer;<br>差异内容：value: ArrayBuffer;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：DescriptorWriteReq；<br>API声明：descriptorUuid: string;<br>差异内容：descriptorUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：DescriptorWriteReq；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：DescriptorWriteReq；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface ServerResponse<br>差异内容：interface ServerResponse|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ServerResponse；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ServerResponse；<br>API声明：transId: number;<br>差异内容：transId: number;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ServerResponse；<br>API声明：status: number;<br>差异内容：status: number;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ServerResponse；<br>API声明：offset: number;<br>差异内容：offset: number;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ServerResponse；<br>API声明：value: ArrayBuffer;<br>差异内容：value: ArrayBuffer;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface BLEConnectChangedState<br>差异内容：interface BLEConnectChangedState|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BLEConnectChangedState；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BLEConnectChangedState；<br>API声明：state: ProfileConnectionState;<br>差异内容：state: ProfileConnectionState;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface ScanResult<br>差异内容：interface ScanResult|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ScanResult；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ScanResult；<br>API声明：rssi: number;<br>差异内容：rssi: number;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ScanResult；<br>API声明：data: ArrayBuffer;<br>差异内容：data: ArrayBuffer;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface AdvertiseSetting<br>差异内容：interface AdvertiseSetting|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：AdvertiseSetting；<br>API声明：interval?: number;<br>差异内容：interval?: number;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：AdvertiseSetting；<br>API声明：txPower?: number;<br>差异内容：txPower?: number;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：AdvertiseSetting；<br>API声明：connectable?: boolean;<br>差异内容：connectable?: boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface AdvertiseData<br>差异内容：interface AdvertiseData|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：AdvertiseData；<br>API声明：serviceUuids: Array\<string>;<br>差异内容：serviceUuids: Array\<string>;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：AdvertiseData；<br>API声明：manufactureData: Array\<ManufactureData>;<br>差异内容：manufactureData: Array\<ManufactureData>;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：AdvertiseData；<br>API声明：serviceData: Array\<ServiceData>;<br>差异内容：serviceData: Array\<ServiceData>;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface ManufactureData<br>差异内容：interface ManufactureData|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ManufactureData；<br>API声明：manufactureId: number;<br>差异内容：manufactureId: number;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ManufactureData；<br>API声明：manufactureValue: ArrayBuffer;<br>差异内容：manufactureValue: ArrayBuffer;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface ServiceData<br>差异内容：interface ServiceData|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ServiceData；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ServiceData；<br>API声明：serviceValue: ArrayBuffer;<br>差异内容：serviceValue: ArrayBuffer;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface ScanFilter<br>差异内容：interface ScanFilter|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：deviceId?: string;<br>差异内容：deviceId?: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：name?: string;<br>差异内容：name?: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：serviceUuid?: string;<br>差异内容：serviceUuid?: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface ScanOptions<br>差异内容：interface ScanOptions|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ScanOptions；<br>API声明：interval?: number;<br>差异内容：interval?: number;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ScanOptions；<br>API声明：dutyMode?: ScanDuty;<br>差异内容：dutyMode?: ScanDuty;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ScanOptions；<br>API声明：matchMode?: MatchMode;<br>差异内容：matchMode?: MatchMode;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface SppOption<br>差异内容：interface SppOption|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：SppOption；<br>API声明：uuid: string;<br>差异内容：uuid: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：SppOption；<br>API声明：secure: boolean;<br>差异内容：secure: boolean;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：SppOption；<br>API声明：type: SppType;<br>差异内容：type: SppType;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface PinRequiredParam<br>差异内容：interface PinRequiredParam|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：PinRequiredParam；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：PinRequiredParam；<br>API声明：pinCode: string;<br>差异内容：pinCode: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface DeviceClass<br>差异内容：interface DeviceClass|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：DeviceClass；<br>API声明：majorClass: MajorClass;<br>差异内容：majorClass: MajorClass;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：DeviceClass；<br>API声明：majorMinorClass: MajorMinorClass;<br>差异内容：majorMinorClass: MajorMinorClass;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：DeviceClass；<br>API声明：classOfDevice: number;<br>差异内容：classOfDevice: number;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface BondStateParam<br>差异内容：interface BondStateParam|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BondStateParam；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BondStateParam；<br>API声明：state: BondState;<br>差异内容：state: BondState;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：enum ScanDuty<br>差异内容：enum ScanDuty|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ScanDuty；<br>API声明：SCAN_MODE_LOW_POWER = 0<br>差异内容：SCAN_MODE_LOW_POWER = 0|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ScanDuty；<br>API声明：SCAN_MODE_BALANCED = 1<br>差异内容：SCAN_MODE_BALANCED = 1|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ScanDuty；<br>API声明：SCAN_MODE_LOW_LATENCY = 2<br>差异内容：SCAN_MODE_LOW_LATENCY = 2|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：enum MatchMode<br>差异内容：enum MatchMode|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MatchMode；<br>API声明：MATCH_MODE_AGGRESSIVE = 1<br>差异内容：MATCH_MODE_AGGRESSIVE = 1|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MatchMode；<br>API声明：MATCH_MODE_STICKY = 2<br>差异内容：MATCH_MODE_STICKY = 2|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：enum ProfileConnectionState<br>差异内容：enum ProfileConnectionState|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ProfileConnectionState；<br>API声明：STATE_DISCONNECTED = 0<br>差异内容：STATE_DISCONNECTED = 0|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ProfileConnectionState；<br>API声明：STATE_CONNECTING = 1<br>差异内容：STATE_CONNECTING = 1|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ProfileConnectionState；<br>API声明：STATE_CONNECTED = 2<br>差异内容：STATE_CONNECTED = 2|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ProfileConnectionState；<br>API声明：STATE_DISCONNECTING = 3<br>差异内容：STATE_DISCONNECTING = 3|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：enum BluetoothState<br>差异内容：enum BluetoothState|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_OFF = 0<br>差异内容：STATE_OFF = 0|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_TURNING_ON = 1<br>差异内容：STATE_TURNING_ON = 1|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_ON = 2<br>差异内容：STATE_ON = 2|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_TURNING_OFF = 3<br>差异内容：STATE_TURNING_OFF = 3|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_BLE_TURNING_ON = 4<br>差异内容：STATE_BLE_TURNING_ON = 4|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_BLE_ON = 5<br>差异内容：STATE_BLE_ON = 5|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_BLE_TURNING_OFF = 6<br>差异内容：STATE_BLE_TURNING_OFF = 6|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：enum SppType<br>差异内容：enum SppType|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：SppType；<br>API声明：SPP_RFCOMM<br>差异内容：SPP_RFCOMM|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：enum ScanMode<br>差异内容：enum ScanMode|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ScanMode；<br>API声明：SCAN_MODE_NONE = 0<br>差异内容：SCAN_MODE_NONE = 0|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ScanMode；<br>API声明：SCAN_MODE_CONNECTABLE = 1<br>差异内容：SCAN_MODE_CONNECTABLE = 1|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ScanMode；<br>API声明：SCAN_MODE_GENERAL_DISCOVERABLE = 2<br>差异内容：SCAN_MODE_GENERAL_DISCOVERABLE = 2|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ScanMode；<br>API声明：SCAN_MODE_LIMITED_DISCOVERABLE = 3<br>差异内容：SCAN_MODE_LIMITED_DISCOVERABLE = 3|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ScanMode；<br>API声明：SCAN_MODE_CONNECTABLE_GENERAL_DISCOVERABLE = 4<br>差异内容：SCAN_MODE_CONNECTABLE_GENERAL_DISCOVERABLE = 4|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ScanMode；<br>API声明：SCAN_MODE_CONNECTABLE_LIMITED_DISCOVERABLE = 5<br>差异内容：SCAN_MODE_CONNECTABLE_LIMITED_DISCOVERABLE = 5|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：enum BondState<br>差异内容：enum BondState|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BondState；<br>API声明：BOND_STATE_INVALID = 0<br>差异内容：BOND_STATE_INVALID = 0|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BondState；<br>API声明：BOND_STATE_BONDING = 1<br>差异内容：BOND_STATE_BONDING = 1|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：BondState；<br>API声明：BOND_STATE_BONDED = 2<br>差异内容：BOND_STATE_BONDED = 2|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：enum MajorClass<br>差异内容：enum MajorClass|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_MISC = 0x0000<br>差异内容：MAJOR_MISC = 0x0000|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_COMPUTER = 0x0100<br>差异内容：MAJOR_COMPUTER = 0x0100|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_PHONE = 0x0200<br>差异内容：MAJOR_PHONE = 0x0200|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_NETWORKING = 0x0300<br>差异内容：MAJOR_NETWORKING = 0x0300|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_AUDIO_VIDEO = 0x0400<br>差异内容：MAJOR_AUDIO_VIDEO = 0x0400|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_PERIPHERAL = 0x0500<br>差异内容：MAJOR_PERIPHERAL = 0x0500|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_IMAGING = 0x0600<br>差异内容：MAJOR_IMAGING = 0x0600|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_WEARABLE = 0x0700<br>差异内容：MAJOR_WEARABLE = 0x0700|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_TOY = 0x0800<br>差异内容：MAJOR_TOY = 0x0800|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_HEALTH = 0x0900<br>差异内容：MAJOR_HEALTH = 0x0900|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_UNCATEGORIZED = 0x1F00<br>差异内容：MAJOR_UNCATEGORIZED = 0x1F00|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：enum MajorMinorClass<br>差异内容：enum MajorMinorClass|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_UNCATEGORIZED = 0x0100<br>差异内容：COMPUTER_UNCATEGORIZED = 0x0100|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_DESKTOP = 0x0104<br>差异内容：COMPUTER_DESKTOP = 0x0104|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_SERVER = 0x0108<br>差异内容：COMPUTER_SERVER = 0x0108|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_LAPTOP = 0x010C<br>差异内容：COMPUTER_LAPTOP = 0x010C|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_HANDHELD_PC_PDA = 0x0110<br>差异内容：COMPUTER_HANDHELD_PC_PDA = 0x0110|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_PALM_SIZE_PC_PDA = 0x0114<br>差异内容：COMPUTER_PALM_SIZE_PC_PDA = 0x0114|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_WEARABLE = 0x0118<br>差异内容：COMPUTER_WEARABLE = 0x0118|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_TABLET = 0x011C<br>差异内容：COMPUTER_TABLET = 0x011C|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PHONE_UNCATEGORIZED = 0x0200<br>差异内容：PHONE_UNCATEGORIZED = 0x0200|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PHONE_CELLULAR = 0x0204<br>差异内容：PHONE_CELLULAR = 0x0204|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PHONE_CORDLESS = 0x0208<br>差异内容：PHONE_CORDLESS = 0x0208|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PHONE_SMART = 0x020C<br>差异内容：PHONE_SMART = 0x020C|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PHONE_MODEM_OR_GATEWAY = 0x0210<br>差异内容：PHONE_MODEM_OR_GATEWAY = 0x0210|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PHONE_ISDN = 0x0214<br>差异内容：PHONE_ISDN = 0x0214|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_FULLY_AVAILABLE = 0x0300<br>差异内容：NETWORK_FULLY_AVAILABLE = 0x0300|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_1_TO_17_UTILIZED = 0x0320<br>差异内容：NETWORK_1_TO_17_UTILIZED = 0x0320|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_17_TO_33_UTILIZED = 0x0340<br>差异内容：NETWORK_17_TO_33_UTILIZED = 0x0340|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_33_TO_50_UTILIZED = 0x0360<br>差异内容：NETWORK_33_TO_50_UTILIZED = 0x0360|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_60_TO_67_UTILIZED = 0x0380<br>差异内容：NETWORK_60_TO_67_UTILIZED = 0x0380|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_67_TO_83_UTILIZED = 0x03A0<br>差异内容：NETWORK_67_TO_83_UTILIZED = 0x03A0|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_83_TO_99_UTILIZED = 0x03C0<br>差异内容：NETWORK_83_TO_99_UTILIZED = 0x03C0|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_NO_SERVICE = 0x03E0<br>差异内容：NETWORK_NO_SERVICE = 0x03E0|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_UNCATEGORIZED = 0x0400<br>差异内容：AUDIO_VIDEO_UNCATEGORIZED = 0x0400|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_WEARABLE_HEADSET = 0x0404<br>差异内容：AUDIO_VIDEO_WEARABLE_HEADSET = 0x0404|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_HANDSFREE = 0x0408<br>差异内容：AUDIO_VIDEO_HANDSFREE = 0x0408|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_MICROPHONE = 0x0410<br>差异内容：AUDIO_VIDEO_MICROPHONE = 0x0410|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_LOUDSPEAKER = 0x0414<br>差异内容：AUDIO_VIDEO_LOUDSPEAKER = 0x0414|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_HEADPHONES = 0x0418<br>差异内容：AUDIO_VIDEO_HEADPHONES = 0x0418|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_PORTABLE_AUDIO = 0x041C<br>差异内容：AUDIO_VIDEO_PORTABLE_AUDIO = 0x041C|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_CAR_AUDIO = 0x0420<br>差异内容：AUDIO_VIDEO_CAR_AUDIO = 0x0420|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_SET_TOP_BOX = 0x0424<br>差异内容：AUDIO_VIDEO_SET_TOP_BOX = 0x0424|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_HIFI_AUDIO = 0x0428<br>差异内容：AUDIO_VIDEO_HIFI_AUDIO = 0x0428|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_VCR = 0x042C<br>差异内容：AUDIO_VIDEO_VCR = 0x042C|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_VIDEO_CAMERA = 0x0430<br>差异内容：AUDIO_VIDEO_VIDEO_CAMERA = 0x0430|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_CAMCORDER = 0x0434<br>差异内容：AUDIO_VIDEO_CAMCORDER = 0x0434|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_VIDEO_MONITOR = 0x0438<br>差异内容：AUDIO_VIDEO_VIDEO_MONITOR = 0x0438|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_VIDEO_DISPLAY_AND_LOUDSPEAKER = 0x043C<br>差异内容：AUDIO_VIDEO_VIDEO_DISPLAY_AND_LOUDSPEAKER = 0x043C|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_VIDEO_CONFERENCING = 0x0440<br>差异内容：AUDIO_VIDEO_VIDEO_CONFERENCING = 0x0440|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_VIDEO_GAMING_TOY = 0x0448<br>差异内容：AUDIO_VIDEO_VIDEO_GAMING_TOY = 0x0448|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_NON_KEYBOARD_NON_POINTING = 0x0500<br>差异内容：PERIPHERAL_NON_KEYBOARD_NON_POINTING = 0x0500|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_KEYBOARD = 0x0540<br>差异内容：PERIPHERAL_KEYBOARD = 0x0540|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_POINTING_DEVICE = 0x0580<br>差异内容：PERIPHERAL_POINTING_DEVICE = 0x0580|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_KEYBOARD_POINTING = 0x05C0<br>差异内容：PERIPHERAL_KEYBOARD_POINTING = 0x05C0|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_UNCATEGORIZED = 0x0500<br>差异内容：PERIPHERAL_UNCATEGORIZED = 0x0500|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_JOYSTICK = 0x0504<br>差异内容：PERIPHERAL_JOYSTICK = 0x0504|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_GAMEPAD = 0x0508<br>差异内容：PERIPHERAL_GAMEPAD = 0x0508|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_REMOTE_CONTROL = 0x05C0<br>差异内容：PERIPHERAL_REMOTE_CONTROL = 0x05C0|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_SENSING_DEVICE = 0x0510<br>差异内容：PERIPHERAL_SENSING_DEVICE = 0x0510|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_DIGITIZER_TABLET = 0x0514<br>差异内容：PERIPHERAL_DIGITIZER_TABLET = 0x0514|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_CARD_READER = 0x0518<br>差异内容：PERIPHERAL_CARD_READER = 0x0518|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_DIGITAL_PEN = 0x051C<br>差异内容：PERIPHERAL_DIGITAL_PEN = 0x051C|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_SCANNER_RFID = 0x0520<br>差异内容：PERIPHERAL_SCANNER_RFID = 0x0520|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_GESTURAL_INPUT = 0x0522<br>差异内容：PERIPHERAL_GESTURAL_INPUT = 0x0522|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：IMAGING_UNCATEGORIZED = 0x0600<br>差异内容：IMAGING_UNCATEGORIZED = 0x0600|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：IMAGING_DISPLAY = 0x0610<br>差异内容：IMAGING_DISPLAY = 0x0610|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：IMAGING_CAMERA = 0x0620<br>差异内容：IMAGING_CAMERA = 0x0620|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：IMAGING_SCANNER = 0x0640<br>差异内容：IMAGING_SCANNER = 0x0640|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：IMAGING_PRINTER = 0x0680<br>差异内容：IMAGING_PRINTER = 0x0680|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：WEARABLE_UNCATEGORIZED = 0x0700<br>差异内容：WEARABLE_UNCATEGORIZED = 0x0700|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：WEARABLE_WRIST_WATCH = 0x0704<br>差异内容：WEARABLE_WRIST_WATCH = 0x0704|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：WEARABLE_PAGER = 0x0708<br>差异内容：WEARABLE_PAGER = 0x0708|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：WEARABLE_JACKET = 0x070C<br>差异内容：WEARABLE_JACKET = 0x070C|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：WEARABLE_HELMET = 0x0710<br>差异内容：WEARABLE_HELMET = 0x0710|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：WEARABLE_GLASSES = 0x0714<br>差异内容：WEARABLE_GLASSES = 0x0714|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：TOY_UNCATEGORIZED = 0x0800<br>差异内容：TOY_UNCATEGORIZED = 0x0800|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：TOY_ROBOT = 0x0804<br>差异内容：TOY_ROBOT = 0x0804|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：TOY_VEHICLE = 0x0808<br>差异内容：TOY_VEHICLE = 0x0808|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：TOY_DOLL_ACTION_FIGURE = 0x080C<br>差异内容：TOY_DOLL_ACTION_FIGURE = 0x080C|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：TOY_CONTROLLER = 0x0810<br>差异内容：TOY_CONTROLLER = 0x0810|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：TOY_GAME = 0x0814<br>差异内容：TOY_GAME = 0x0814|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_UNCATEGORIZED = 0x0900<br>差异内容：HEALTH_UNCATEGORIZED = 0x0900|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_BLOOD_PRESSURE = 0x0904<br>差异内容：HEALTH_BLOOD_PRESSURE = 0x0904|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_THERMOMETER = 0x0908<br>差异内容：HEALTH_THERMOMETER = 0x0908|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_WEIGHING = 0x090C<br>差异内容：HEALTH_WEIGHING = 0x090C|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_GLUCOSE = 0x0910<br>差异内容：HEALTH_GLUCOSE = 0x0910|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_PULSE_OXIMETER = 0x0914<br>差异内容：HEALTH_PULSE_OXIMETER = 0x0914|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_PULSE_RATE = 0x0918<br>差异内容：HEALTH_PULSE_RATE = 0x0918|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_DATA_DISPLAY = 0x091C<br>差异内容：HEALTH_DATA_DISPLAY = 0x091C|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_STEP_COUNTER = 0x0920<br>差异内容：HEALTH_STEP_COUNTER = 0x0920|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_BODY_COMPOSITION_ANALYZER = 0x0924<br>差异内容：HEALTH_BODY_COMPOSITION_ANALYZER = 0x0924|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_PEAK_FLOW_MOITOR = 0x0928<br>差异内容：HEALTH_PEAK_FLOW_MOITOR = 0x0928|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_MEDICATION_MONITOR = 0x092C<br>差异内容：HEALTH_MEDICATION_MONITOR = 0x092C|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_KNEE_PROSTHESIS = 0x0930<br>差异内容：HEALTH_KNEE_PROSTHESIS = 0x0930|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_ANKLE_PROSTHESIS = 0x0934<br>差异内容：HEALTH_ANKLE_PROSTHESIS = 0x0934|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_GENERIC_HEALTH_MANAGER = 0x0938<br>差异内容：HEALTH_GENERIC_HEALTH_MANAGER = 0x0938|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_PERSONAL_MOBILITY_DEVICE = 0x093C<br>差异内容：HEALTH_PERSONAL_MOBILITY_DEVICE = 0x093C|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：interface StateChangeParam<br>差异内容：interface StateChangeParam|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：StateChangeParam；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：StateChangeParam；<br>API声明：state: ProfileConnectionState;<br>差异内容：state: ProfileConnectionState;|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：enum PlayingState<br>差异内容：enum PlayingState|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：PlayingState；<br>API声明：STATE_NOT_PLAYING<br>差异内容：STATE_NOT_PLAYING|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：PlayingState；<br>API声明：STATE_PLAYING<br>差异内容：STATE_PLAYING|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：bluetooth；<br>API声明：enum ProfileId<br>差异内容：enum ProfileId|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ProfileId；<br>API声明：PROFILE_A2DP_SOURCE = 1<br>差异内容：PROFILE_A2DP_SOURCE = 1|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：ProfileId；<br>API声明：PROFILE_HANDS_FREE_AUDIO_GATEWAY = 4<br>差异内容：PROFILE_HANDS_FREE_AUDIO_GATEWAY = 4|api/@ohos.bluetooth.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace hfp<br>差异内容：declare namespace hfp|api/@ohos.bluetooth.hfp.d.ts|
|新增API|NA|类名：hfp；<br>API声明：type BaseProfile = baseProfile.BaseProfile;<br>差异内容：type BaseProfile = baseProfile.BaseProfile;|api/@ohos.bluetooth.hfp.d.ts|
|新增API|NA|类名：hfp；<br>API声明：function createHfpAgProfile(): HandsFreeAudioGatewayProfile;<br>差异内容：function createHfpAgProfile(): HandsFreeAudioGatewayProfile;|api/@ohos.bluetooth.hfp.d.ts|
|新增API|NA|类名：hfp；<br>API声明：interface HandsFreeAudioGatewayProfile<br>差异内容：interface HandsFreeAudioGatewayProfile|api/@ohos.bluetooth.hfp.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace hid<br>差异内容：declare namespace hid|api/@ohos.bluetooth.hid.d.ts|
|新增API|NA|类名：hid；<br>API声明：type BaseProfile = baseProfile.BaseProfile;<br>差异内容：type BaseProfile = baseProfile.BaseProfile;|api/@ohos.bluetooth.hid.d.ts|
|新增API|NA|类名：hid；<br>API声明：function createHidHostProfile(): HidHostProfile;<br>差异内容：function createHidHostProfile(): HidHostProfile;|api/@ohos.bluetooth.hid.d.ts|
|新增API|NA|类名：hid；<br>API声明：interface HidHostProfile<br>差异内容：interface HidHostProfile|api/@ohos.bluetooth.hid.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace map<br>差异内容：declare namespace map|api/@ohos.bluetooth.map.d.ts|
|新增API|NA|类名：map；<br>API声明：type BaseProfile = baseProfile.BaseProfile;<br>差异内容：type BaseProfile = baseProfile.BaseProfile;|api/@ohos.bluetooth.map.d.ts|
|新增API|NA|类名：map；<br>API声明：function createMapMseProfile(): MapMseProfile;<br>差异内容：function createMapMseProfile(): MapMseProfile;|api/@ohos.bluetooth.map.d.ts|
|新增API|NA|类名：map；<br>API声明：interface MapMseProfile<br>差异内容：interface MapMseProfile|api/@ohos.bluetooth.map.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace pan<br>差异内容：declare namespace pan|api/@ohos.bluetooth.pan.d.ts|
|新增API|NA|类名：pan；<br>API声明：type BaseProfile = baseProfile.BaseProfile;<br>差异内容：type BaseProfile = baseProfile.BaseProfile;|api/@ohos.bluetooth.pan.d.ts|
|新增API|NA|类名：pan；<br>API声明：function createPanProfile(): PanProfile;<br>差异内容：function createPanProfile(): PanProfile;|api/@ohos.bluetooth.pan.d.ts|
|新增API|NA|类名：pan；<br>API声明：interface PanProfile<br>差异内容：interface PanProfile|api/@ohos.bluetooth.pan.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace pbap<br>差异内容：declare namespace pbap|api/@ohos.bluetooth.pbap.d.ts|
|新增API|NA|类名：pbap；<br>API声明：type BaseProfile = baseProfile.BaseProfile;<br>差异内容：type BaseProfile = baseProfile.BaseProfile;|api/@ohos.bluetooth.pbap.d.ts|
|新增API|NA|类名：pbap；<br>API声明：function createPbapServerProfile(): PbapServerProfile;<br>差异内容：function createPbapServerProfile(): PbapServerProfile;|api/@ohos.bluetooth.pbap.d.ts|
|新增API|NA|类名：pbap；<br>API声明：interface PbapServerProfile<br>差异内容：interface PbapServerProfile|api/@ohos.bluetooth.pbap.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace socket<br>差异内容：declare namespace socket|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function sppListen(name: string, options: SppOptions, callback: AsyncCallback\<number>): void;<br>差异内容：function sppListen(name: string, options: SppOptions, callback: AsyncCallback\<number>): void;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function sppAccept(serverSocket: number, callback: AsyncCallback\<number>): void;<br>差异内容：function sppAccept(serverSocket: number, callback: AsyncCallback\<number>): void;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function sppConnect(deviceId: string, options: SppOptions, callback: AsyncCallback\<number>): void;<br>差异内容：function sppConnect(deviceId: string, options: SppOptions, callback: AsyncCallback\<number>): void;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function sppCloseServerSocket(socket: number): void;<br>差异内容：function sppCloseServerSocket(socket: number): void;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function sppCloseClientSocket(socket: number): void;<br>差异内容：function sppCloseClientSocket(socket: number): void;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function sppWrite(clientSocket: number, data: ArrayBuffer): void;<br>差异内容：function sppWrite(clientSocket: number, data: ArrayBuffer): void;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function on(type: 'sppRead', clientSocket: number, callback: Callback\<ArrayBuffer>): void;<br>差异内容：function on(type: 'sppRead', clientSocket: number, callback: Callback\<ArrayBuffer>): void;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：function off(type: 'sppRead', clientSocket: number, callback?: Callback\<ArrayBuffer>): void;<br>差异内容：function off(type: 'sppRead', clientSocket: number, callback?: Callback\<ArrayBuffer>): void;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：interface SppOptions<br>差异内容：interface SppOptions|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：SppOptions；<br>API声明：uuid: string;<br>差异内容：uuid: string;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：SppOptions；<br>API声明：secure: boolean;<br>差异内容：secure: boolean;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：SppOptions；<br>API声明：type: SppType;<br>差异内容：type: SppType;|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：enum SppType<br>差异内容：enum SppType|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：SppType；<br>API声明：SPP_RFCOMM<br>差异内容：SPP_RFCOMM|api/@ohos.bluetooth.socket.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace wearDetection<br>差异内容：declare namespace wearDetection|api/@ohos.bluetooth.wearDetection.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace bluetoothManager<br>差异内容：declare namespace bluetoothManager|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function getState(): BluetoothState;<br>差异内容：function getState(): BluetoothState;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function getBtConnectionState(): ProfileConnectionState;<br>差异内容：function getBtConnectionState(): ProfileConnectionState;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function pairDevice(deviceId: string): void;<br>差异内容：function pairDevice(deviceId: string): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function getRemoteDeviceName(deviceId: string): string;<br>差异内容：function getRemoteDeviceName(deviceId: string): string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function getRemoteDeviceClass(deviceId: string): DeviceClass;<br>差异内容：function getRemoteDeviceClass(deviceId: string): DeviceClass;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function enableBluetooth(): void;<br>差异内容：function enableBluetooth(): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function disableBluetooth(): void;<br>差异内容：function disableBluetooth(): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function getLocalName(): string;<br>差异内容：function getLocalName(): string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function getPairedDevices(): Array\<string>;<br>差异内容：function getPairedDevices(): Array\<string>;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function getProfileConnectionState(profileId: ProfileId): ProfileConnectionState;<br>差异内容：function getProfileConnectionState(profileId: ProfileId): ProfileConnectionState;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function setDevicePairingConfirmation(device: string, accept: boolean): void;<br>差异内容：function setDevicePairingConfirmation(device: string, accept: boolean): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function setLocalName(name: string): void;<br>差异内容：function setLocalName(name: string): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function setBluetoothScanMode(mode: ScanMode, duration: number): void;<br>差异内容：function setBluetoothScanMode(mode: ScanMode, duration: number): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function getBluetoothScanMode(): ScanMode;<br>差异内容：function getBluetoothScanMode(): ScanMode;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function startBluetoothDiscovery(): void;<br>差异内容：function startBluetoothDiscovery(): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function stopBluetoothDiscovery(): void;<br>差异内容：function stopBluetoothDiscovery(): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function on(type: 'bluetoothDeviceFind', callback: Callback\<Array\<string>>): void;<br>差异内容：function on(type: 'bluetoothDeviceFind', callback: Callback\<Array\<string>>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function off(type: 'bluetoothDeviceFind', callback?: Callback\<Array\<string>>): void;<br>差异内容：function off(type: 'bluetoothDeviceFind', callback?: Callback\<Array\<string>>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function on(type: 'bondStateChange', callback: Callback\<BondStateParam>): void;<br>差异内容：function on(type: 'bondStateChange', callback: Callback\<BondStateParam>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function off(type: 'bondStateChange', callback?: Callback\<BondStateParam>): void;<br>差异内容：function off(type: 'bondStateChange', callback?: Callback\<BondStateParam>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function on(type: 'pinRequired', callback: Callback\<PinRequiredParam>): void;<br>差异内容：function on(type: 'pinRequired', callback: Callback\<PinRequiredParam>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function off(type: 'pinRequired', callback?: Callback\<PinRequiredParam>): void;<br>差异内容：function off(type: 'pinRequired', callback?: Callback\<PinRequiredParam>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function on(type: 'stateChange', callback: Callback\<BluetoothState>): void;<br>差异内容：function on(type: 'stateChange', callback: Callback\<BluetoothState>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function off(type: 'stateChange', callback?: Callback\<BluetoothState>): void;<br>差异内容：function off(type: 'stateChange', callback?: Callback\<BluetoothState>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function sppListen(name: string, option: SppOption, callback: AsyncCallback\<number>): void;<br>差异内容：function sppListen(name: string, option: SppOption, callback: AsyncCallback\<number>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function sppAccept(serverSocket: number, callback: AsyncCallback\<number>): void;<br>差异内容：function sppAccept(serverSocket: number, callback: AsyncCallback\<number>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function sppConnect(device: string, option: SppOption, callback: AsyncCallback\<number>): void;<br>差异内容：function sppConnect(device: string, option: SppOption, callback: AsyncCallback\<number>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function sppCloseServerSocket(socket: number): void;<br>差异内容：function sppCloseServerSocket(socket: number): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function sppCloseClientSocket(socket: number): void;<br>差异内容：function sppCloseClientSocket(socket: number): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function sppWrite(clientSocket: number, data: ArrayBuffer): void;<br>差异内容：function sppWrite(clientSocket: number, data: ArrayBuffer): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function on(type: 'sppRead', clientSocket: number, callback: Callback\<ArrayBuffer>): void;<br>差异内容：function on(type: 'sppRead', clientSocket: number, callback: Callback\<ArrayBuffer>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function off(type: 'sppRead', clientSocket: number, callback?: Callback\<ArrayBuffer>): void;<br>差异内容：function off(type: 'sppRead', clientSocket: number, callback?: Callback\<ArrayBuffer>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function getProfileInstance(profileId: ProfileId): A2dpSourceProfile \| HandsFreeAudioGatewayProfile \| HidHostProfile \| PanProfile;<br>差异内容：function getProfileInstance(profileId: ProfileId): A2dpSourceProfile \| HandsFreeAudioGatewayProfile \| HidHostProfile \| PanProfile;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface BaseProfile<br>差异内容：interface BaseProfile|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BaseProfile；<br>API声明：getConnectionDevices(): Array\<string>;<br>差异内容：getConnectionDevices(): Array\<string>;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BaseProfile；<br>API声明：getDeviceState(device: string): ProfileConnectionState;<br>差异内容：getDeviceState(device: string): ProfileConnectionState;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface A2dpSourceProfile<br>差异内容：interface A2dpSourceProfile|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：A2dpSourceProfile；<br>API声明：connect(device: string): void;<br>差异内容：connect(device: string): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：A2dpSourceProfile；<br>API声明：disconnect(device: string): void;<br>差异内容：disconnect(device: string): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：A2dpSourceProfile；<br>API声明：on(type: 'connectionStateChange', callback: Callback\<StateChangeParam>): void;<br>差异内容：on(type: 'connectionStateChange', callback: Callback\<StateChangeParam>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：A2dpSourceProfile；<br>API声明：off(type: 'connectionStateChange', callback?: Callback\<StateChangeParam>): void;<br>差异内容：off(type: 'connectionStateChange', callback?: Callback\<StateChangeParam>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：A2dpSourceProfile；<br>API声明：getPlayingState(device: string): PlayingState;<br>差异内容：getPlayingState(device: string): PlayingState;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface HandsFreeAudioGatewayProfile<br>差异内容：interface HandsFreeAudioGatewayProfile|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：HandsFreeAudioGatewayProfile；<br>API声明：connect(device: string): void;<br>差异内容：connect(device: string): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：HandsFreeAudioGatewayProfile；<br>API声明：disconnect(device: string): void;<br>差异内容：disconnect(device: string): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：HandsFreeAudioGatewayProfile；<br>API声明：on(type: 'connectionStateChange', callback: Callback\<StateChangeParam>): void;<br>差异内容：on(type: 'connectionStateChange', callback: Callback\<StateChangeParam>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：HandsFreeAudioGatewayProfile；<br>API声明：off(type: 'connectionStateChange', callback?: Callback\<StateChangeParam>): void;<br>差异内容：off(type: 'connectionStateChange', callback?: Callback\<StateChangeParam>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface HidHostProfile<br>差异内容：interface HidHostProfile|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：HidHostProfile；<br>API声明：on(type: 'connectionStateChange', callback: Callback\<StateChangeParam>): void;<br>差异内容：on(type: 'connectionStateChange', callback: Callback\<StateChangeParam>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：HidHostProfile；<br>API声明：off(type: 'connectionStateChange', callback?: Callback\<StateChangeParam>): void;<br>差异内容：off(type: 'connectionStateChange', callback?: Callback\<StateChangeParam>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface PanProfile<br>差异内容：interface PanProfile|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：PanProfile；<br>API声明：on(type: 'connectionStateChange', callback: Callback\<StateChangeParam>): void;<br>差异内容：on(type: 'connectionStateChange', callback: Callback\<StateChangeParam>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：PanProfile；<br>API声明：off(type: 'connectionStateChange', callback?: Callback\<StateChangeParam>): void;<br>差异内容：off(type: 'connectionStateChange', callback?: Callback\<StateChangeParam>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：namespace BLE<br>差异内容：namespace BLE|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BLE；<br>API声明：function createGattServer(): GattServer;<br>差异内容：function createGattServer(): GattServer;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BLE；<br>API声明：function createGattClientDevice(deviceId: string): GattClientDevice;<br>差异内容：function createGattClientDevice(deviceId: string): GattClientDevice;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BLE；<br>API声明：function getConnectedBLEDevices(): Array\<string>;<br>差异内容：function getConnectedBLEDevices(): Array\<string>;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BLE；<br>API声明：function startBLEScan(filters: Array\<ScanFilter>, options?: ScanOptions): void;<br>差异内容：function startBLEScan(filters: Array\<ScanFilter>, options?: ScanOptions): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BLE；<br>API声明：function stopBLEScan(): void;<br>差异内容：function stopBLEScan(): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BLE；<br>API声明：function on(type: 'BLEDeviceFind', callback: Callback\<Array\<ScanResult>>): void;<br>差异内容：function on(type: 'BLEDeviceFind', callback: Callback\<Array\<ScanResult>>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BLE；<br>API声明：function off(type: 'BLEDeviceFind', callback?: Callback\<Array\<ScanResult>>): void;<br>差异内容：function off(type: 'BLEDeviceFind', callback?: Callback\<Array\<ScanResult>>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface GattServer<br>差异内容：interface GattServer|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：startAdvertising(setting: AdvertiseSetting, advData: AdvertiseData, advResponse?: AdvertiseData): void;<br>差异内容：startAdvertising(setting: AdvertiseSetting, advData: AdvertiseData, advResponse?: AdvertiseData): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：stopAdvertising(): void;<br>差异内容：stopAdvertising(): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：addService(service: GattService): void;<br>差异内容：addService(service: GattService): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：removeService(serviceUuid: string): void;<br>差异内容：removeService(serviceUuid: string): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：close(): void;<br>差异内容：close(): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：notifyCharacteristicChanged(deviceId: string, notifyCharacteristic: NotifyCharacteristic): void;<br>差异内容：notifyCharacteristicChanged(deviceId: string, notifyCharacteristic: NotifyCharacteristic): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：sendResponse(serverResponse: ServerResponse): void;<br>差异内容：sendResponse(serverResponse: ServerResponse): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：on(type: 'characteristicRead', callback: Callback\<CharacteristicReadRequest>): void;<br>差异内容：on(type: 'characteristicRead', callback: Callback\<CharacteristicReadRequest>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：off(type: 'characteristicRead', callback?: Callback\<CharacteristicReadRequest>): void;<br>差异内容：off(type: 'characteristicRead', callback?: Callback\<CharacteristicReadRequest>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：on(type: 'characteristicWrite', callback: Callback\<CharacteristicWriteRequest>): void;<br>差异内容：on(type: 'characteristicWrite', callback: Callback\<CharacteristicWriteRequest>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：off(type: 'characteristicWrite', callback?: Callback\<CharacteristicWriteRequest>): void;<br>差异内容：off(type: 'characteristicWrite', callback?: Callback\<CharacteristicWriteRequest>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：on(type: 'descriptorRead', callback: Callback\<DescriptorReadRequest>): void;<br>差异内容：on(type: 'descriptorRead', callback: Callback\<DescriptorReadRequest>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：off(type: 'descriptorRead', callback?: Callback\<DescriptorReadRequest>): void;<br>差异内容：off(type: 'descriptorRead', callback?: Callback\<DescriptorReadRequest>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：on(type: 'descriptorWrite', callback: Callback\<DescriptorWriteRequest>): void;<br>差异内容：on(type: 'descriptorWrite', callback: Callback\<DescriptorWriteRequest>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：off(type: 'descriptorWrite', callback?: Callback\<DescriptorWriteRequest>): void;<br>差异内容：off(type: 'descriptorWrite', callback?: Callback\<DescriptorWriteRequest>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：on(type: 'connectStateChange', callback: Callback\<BLEConnectChangedState>): void;<br>差异内容：on(type: 'connectStateChange', callback: Callback\<BLEConnectChangedState>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattServer；<br>API声明：off(type: 'connectStateChange', callback?: Callback\<BLEConnectChangedState>): void;<br>差异内容：off(type: 'connectStateChange', callback?: Callback\<BLEConnectChangedState>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface GattClientDevice<br>差异内容：interface GattClientDevice|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：connect(): void;<br>差异内容：connect(): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：disconnect(): void;<br>差异内容：disconnect(): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：close(): void;<br>差异内容：close(): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：getDeviceName(callback: AsyncCallback\<string>): void;<br>差异内容：getDeviceName(callback: AsyncCallback\<string>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：getDeviceName(): Promise\<string>;<br>差异内容：getDeviceName(): Promise\<string>;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：getServices(callback: AsyncCallback\<Array\<GattService>>): void;<br>差异内容：getServices(callback: AsyncCallback\<Array\<GattService>>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：getServices(): Promise\<Array\<GattService>>;<br>差异内容：getServices(): Promise\<Array\<GattService>>;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：readCharacteristicValue(characteristic: BLECharacteristic, callback: AsyncCallback\<BLECharacteristic>): void;<br>差异内容：readCharacteristicValue(characteristic: BLECharacteristic, callback: AsyncCallback\<BLECharacteristic>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：readCharacteristicValue(characteristic: BLECharacteristic): Promise\<BLECharacteristic>;<br>差异内容：readCharacteristicValue(characteristic: BLECharacteristic): Promise\<BLECharacteristic>;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：readDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback\<BLEDescriptor>): void;<br>差异内容：readDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback\<BLEDescriptor>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：readDescriptorValue(descriptor: BLEDescriptor): Promise\<BLEDescriptor>;<br>差异内容：readDescriptorValue(descriptor: BLEDescriptor): Promise\<BLEDescriptor>;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：writeCharacteristicValue(characteristic: BLECharacteristic): void;<br>差异内容：writeCharacteristicValue(characteristic: BLECharacteristic): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：writeDescriptorValue(descriptor: BLEDescriptor): void;<br>差异内容：writeDescriptorValue(descriptor: BLEDescriptor): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：getRssiValue(callback: AsyncCallback\<number>): void;<br>差异内容：getRssiValue(callback: AsyncCallback\<number>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：getRssiValue(): Promise\<number>;<br>差异内容：getRssiValue(): Promise\<number>;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：setBLEMtuSize(mtu: number): void;<br>差异内容：setBLEMtuSize(mtu: number): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：setNotifyCharacteristicChanged(characteristic: BLECharacteristic, enable: boolean): void;<br>差异内容：setNotifyCharacteristicChanged(characteristic: BLECharacteristic, enable: boolean): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：on(type: 'BLECharacteristicChange', callback: Callback\<BLECharacteristic>): void;<br>差异内容：on(type: 'BLECharacteristicChange', callback: Callback\<BLECharacteristic>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：off(type: 'BLECharacteristicChange', callback?: Callback\<BLECharacteristic>): void;<br>差异内容：off(type: 'BLECharacteristicChange', callback?: Callback\<BLECharacteristic>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：on(type: 'BLEConnectionStateChange', callback: Callback\<BLEConnectChangedState>): void;<br>差异内容：on(type: 'BLEConnectionStateChange', callback: Callback\<BLEConnectChangedState>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattClientDevice；<br>API声明：off(type: 'BLEConnectionStateChange', callback?: Callback\<BLEConnectChangedState>): void;<br>差异内容：off(type: 'BLEConnectionStateChange', callback?: Callback\<BLEConnectChangedState>): void;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface GattService<br>差异内容：interface GattService|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattService；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattService；<br>API声明：isPrimary: boolean;<br>差异内容：isPrimary: boolean;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattService；<br>API声明：characteristics: Array\<BLECharacteristic>;<br>差异内容：characteristics: Array\<BLECharacteristic>;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：GattService；<br>API声明：includeServices?: Array\<GattService>;<br>差异内容：includeServices?: Array\<GattService>;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface BLECharacteristic<br>差异内容：interface BLECharacteristic|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BLECharacteristic；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BLECharacteristic；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BLECharacteristic；<br>API声明：characteristicValue: ArrayBuffer;<br>差异内容：characteristicValue: ArrayBuffer;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BLECharacteristic；<br>API声明：descriptors: Array\<BLEDescriptor>;<br>差异内容：descriptors: Array\<BLEDescriptor>;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface BLEDescriptor<br>差异内容：interface BLEDescriptor|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BLEDescriptor；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BLEDescriptor；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BLEDescriptor；<br>API声明：descriptorUuid: string;<br>差异内容：descriptorUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BLEDescriptor；<br>API声明：descriptorValue: ArrayBuffer;<br>差异内容：descriptorValue: ArrayBuffer;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface NotifyCharacteristic<br>差异内容：interface NotifyCharacteristic|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：NotifyCharacteristic；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：NotifyCharacteristic；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：NotifyCharacteristic；<br>API声明：characteristicValue: ArrayBuffer;<br>差异内容：characteristicValue: ArrayBuffer;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：NotifyCharacteristic；<br>API声明：confirm: boolean;<br>差异内容：confirm: boolean;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface CharacteristicReadRequest<br>差异内容：interface CharacteristicReadRequest|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：CharacteristicReadRequest；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：CharacteristicReadRequest；<br>API声明：transId: number;<br>差异内容：transId: number;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：CharacteristicReadRequest；<br>API声明：offset: number;<br>差异内容：offset: number;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：CharacteristicReadRequest；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：CharacteristicReadRequest；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface CharacteristicWriteRequest<br>差异内容：interface CharacteristicWriteRequest|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：CharacteristicWriteRequest；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：CharacteristicWriteRequest；<br>API声明：transId: number;<br>差异内容：transId: number;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：CharacteristicWriteRequest；<br>API声明：offset: number;<br>差异内容：offset: number;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：CharacteristicWriteRequest；<br>API声明：isPrep: boolean;<br>差异内容：isPrep: boolean;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：CharacteristicWriteRequest；<br>API声明：needRsp: boolean;<br>差异内容：needRsp: boolean;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：CharacteristicWriteRequest；<br>API声明：value: ArrayBuffer;<br>差异内容：value: ArrayBuffer;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：CharacteristicWriteRequest；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：CharacteristicWriteRequest；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface DescriptorReadRequest<br>差异内容：interface DescriptorReadRequest|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：DescriptorReadRequest；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：DescriptorReadRequest；<br>API声明：transId: number;<br>差异内容：transId: number;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：DescriptorReadRequest；<br>API声明：offset: number;<br>差异内容：offset: number;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：DescriptorReadRequest；<br>API声明：descriptorUuid: string;<br>差异内容：descriptorUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：DescriptorReadRequest；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：DescriptorReadRequest；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface DescriptorWriteRequest<br>差异内容：interface DescriptorWriteRequest|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：DescriptorWriteRequest；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：DescriptorWriteRequest；<br>API声明：transId: number;<br>差异内容：transId: number;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：DescriptorWriteRequest；<br>API声明：offset: number;<br>差异内容：offset: number;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：DescriptorWriteRequest；<br>API声明：isPrep: boolean;<br>差异内容：isPrep: boolean;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：DescriptorWriteRequest；<br>API声明：needRsp: boolean;<br>差异内容：needRsp: boolean;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：DescriptorWriteRequest；<br>API声明：value: ArrayBuffer;<br>差异内容：value: ArrayBuffer;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：DescriptorWriteRequest；<br>API声明：descriptorUuid: string;<br>差异内容：descriptorUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：DescriptorWriteRequest；<br>API声明：characteristicUuid: string;<br>差异内容：characteristicUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：DescriptorWriteRequest；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface ServerResponse<br>差异内容：interface ServerResponse|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ServerResponse；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ServerResponse；<br>API声明：transId: number;<br>差异内容：transId: number;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ServerResponse；<br>API声明：status: number;<br>差异内容：status: number;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ServerResponse；<br>API声明：offset: number;<br>差异内容：offset: number;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ServerResponse；<br>API声明：value: ArrayBuffer;<br>差异内容：value: ArrayBuffer;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface BLEConnectChangedState<br>差异内容：interface BLEConnectChangedState|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BLEConnectChangedState；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BLEConnectChangedState；<br>API声明：state: ProfileConnectionState;<br>差异内容：state: ProfileConnectionState;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface ScanResult<br>差异内容：interface ScanResult|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanResult；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanResult；<br>API声明：rssi: number;<br>差异内容：rssi: number;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanResult；<br>API声明：data: ArrayBuffer;<br>差异内容：data: ArrayBuffer;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface AdvertiseSetting<br>差异内容：interface AdvertiseSetting|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：AdvertiseSetting；<br>API声明：interval?: number;<br>差异内容：interval?: number;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：AdvertiseSetting；<br>API声明：txPower?: number;<br>差异内容：txPower?: number;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：AdvertiseSetting；<br>API声明：connectable?: boolean;<br>差异内容：connectable?: boolean;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface AdvertiseData<br>差异内容：interface AdvertiseData|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：AdvertiseData；<br>API声明：serviceUuids: Array\<string>;<br>差异内容：serviceUuids: Array\<string>;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：AdvertiseData；<br>API声明：manufactureData: Array\<ManufactureData>;<br>差异内容：manufactureData: Array\<ManufactureData>;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：AdvertiseData；<br>API声明：serviceData: Array\<ServiceData>;<br>差异内容：serviceData: Array\<ServiceData>;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface ManufactureData<br>差异内容：interface ManufactureData|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ManufactureData；<br>API声明：manufactureId: number;<br>差异内容：manufactureId: number;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ManufactureData；<br>API声明：manufactureValue: ArrayBuffer;<br>差异内容：manufactureValue: ArrayBuffer;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface ServiceData<br>差异内容：interface ServiceData|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ServiceData；<br>API声明：serviceUuid: string;<br>差异内容：serviceUuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ServiceData；<br>API声明：serviceValue: ArrayBuffer;<br>差异内容：serviceValue: ArrayBuffer;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface ScanFilter<br>差异内容：interface ScanFilter|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：deviceId?: string;<br>差异内容：deviceId?: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：name?: string;<br>差异内容：name?: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：serviceUuid?: string;<br>差异内容：serviceUuid?: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：serviceUuidMask?: string;<br>差异内容：serviceUuidMask?: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：serviceSolicitationUuid?: string;<br>差异内容：serviceSolicitationUuid?: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：serviceSolicitationUuidMask?: string;<br>差异内容：serviceSolicitationUuidMask?: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：serviceData?: ArrayBuffer;<br>差异内容：serviceData?: ArrayBuffer;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：serviceDataMask?: ArrayBuffer;<br>差异内容：serviceDataMask?: ArrayBuffer;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：manufactureId?: number;<br>差异内容：manufactureId?: number;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：manufactureData?: ArrayBuffer;<br>差异内容：manufactureData?: ArrayBuffer;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanFilter；<br>API声明：manufactureDataMask?: ArrayBuffer;<br>差异内容：manufactureDataMask?: ArrayBuffer;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface ScanOptions<br>差异内容：interface ScanOptions|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanOptions；<br>API声明：interval?: number;<br>差异内容：interval?: number;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanOptions；<br>API声明：dutyMode?: ScanDuty;<br>差异内容：dutyMode?: ScanDuty;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanOptions；<br>API声明：matchMode?: MatchMode;<br>差异内容：matchMode?: MatchMode;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface SppOption<br>差异内容：interface SppOption|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：SppOption；<br>API声明：uuid: string;<br>差异内容：uuid: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：SppOption；<br>API声明：secure: boolean;<br>差异内容：secure: boolean;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：SppOption；<br>API声明：type: SppType;<br>差异内容：type: SppType;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface PinRequiredParam<br>差异内容：interface PinRequiredParam|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：PinRequiredParam；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：PinRequiredParam；<br>API声明：pinCode: string;<br>差异内容：pinCode: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface DeviceClass<br>差异内容：interface DeviceClass|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：DeviceClass；<br>API声明：majorClass: MajorClass;<br>差异内容：majorClass: MajorClass;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：DeviceClass；<br>API声明：majorMinorClass: MajorMinorClass;<br>差异内容：majorMinorClass: MajorMinorClass;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：DeviceClass；<br>API声明：classOfDevice: number;<br>差异内容：classOfDevice: number;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface BondStateParam<br>差异内容：interface BondStateParam|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BondStateParam；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BondStateParam；<br>API声明：state: BondState;<br>差异内容：state: BondState;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：interface StateChangeParam<br>差异内容：interface StateChangeParam|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：StateChangeParam；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：StateChangeParam；<br>API声明：state: ProfileConnectionState;<br>差异内容：state: ProfileConnectionState;|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：enum ScanDuty<br>差异内容：enum ScanDuty|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanDuty；<br>API声明：SCAN_MODE_LOW_POWER = 0<br>差异内容：SCAN_MODE_LOW_POWER = 0|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanDuty；<br>API声明：SCAN_MODE_BALANCED = 1<br>差异内容：SCAN_MODE_BALANCED = 1|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanDuty；<br>API声明：SCAN_MODE_LOW_LATENCY = 2<br>差异内容：SCAN_MODE_LOW_LATENCY = 2|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：enum MatchMode<br>差异内容：enum MatchMode|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MatchMode；<br>API声明：MATCH_MODE_AGGRESSIVE = 1<br>差异内容：MATCH_MODE_AGGRESSIVE = 1|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MatchMode；<br>API声明：MATCH_MODE_STICKY = 2<br>差异内容：MATCH_MODE_STICKY = 2|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：enum ProfileConnectionState<br>差异内容：enum ProfileConnectionState|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ProfileConnectionState；<br>API声明：STATE_DISCONNECTED = 0<br>差异内容：STATE_DISCONNECTED = 0|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ProfileConnectionState；<br>API声明：STATE_CONNECTING = 1<br>差异内容：STATE_CONNECTING = 1|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ProfileConnectionState；<br>API声明：STATE_CONNECTED = 2<br>差异内容：STATE_CONNECTED = 2|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ProfileConnectionState；<br>API声明：STATE_DISCONNECTING = 3<br>差异内容：STATE_DISCONNECTING = 3|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：enum BluetoothState<br>差异内容：enum BluetoothState|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_OFF = 0<br>差异内容：STATE_OFF = 0|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_TURNING_ON = 1<br>差异内容：STATE_TURNING_ON = 1|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_ON = 2<br>差异内容：STATE_ON = 2|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_TURNING_OFF = 3<br>差异内容：STATE_TURNING_OFF = 3|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_BLE_TURNING_ON = 4<br>差异内容：STATE_BLE_TURNING_ON = 4|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_BLE_ON = 5<br>差异内容：STATE_BLE_ON = 5|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BluetoothState；<br>API声明：STATE_BLE_TURNING_OFF = 6<br>差异内容：STATE_BLE_TURNING_OFF = 6|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：enum SppType<br>差异内容：enum SppType|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：SppType；<br>API声明：SPP_RFCOMM<br>差异内容：SPP_RFCOMM|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：enum ScanMode<br>差异内容：enum ScanMode|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanMode；<br>API声明：SCAN_MODE_NONE = 0<br>差异内容：SCAN_MODE_NONE = 0|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanMode；<br>API声明：SCAN_MODE_CONNECTABLE = 1<br>差异内容：SCAN_MODE_CONNECTABLE = 1|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanMode；<br>API声明：SCAN_MODE_GENERAL_DISCOVERABLE = 2<br>差异内容：SCAN_MODE_GENERAL_DISCOVERABLE = 2|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanMode；<br>API声明：SCAN_MODE_LIMITED_DISCOVERABLE = 3<br>差异内容：SCAN_MODE_LIMITED_DISCOVERABLE = 3|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanMode；<br>API声明：SCAN_MODE_CONNECTABLE_GENERAL_DISCOVERABLE = 4<br>差异内容：SCAN_MODE_CONNECTABLE_GENERAL_DISCOVERABLE = 4|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ScanMode；<br>API声明：SCAN_MODE_CONNECTABLE_LIMITED_DISCOVERABLE = 5<br>差异内容：SCAN_MODE_CONNECTABLE_LIMITED_DISCOVERABLE = 5|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：enum BondState<br>差异内容：enum BondState|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BondState；<br>API声明：BOND_STATE_INVALID = 0<br>差异内容：BOND_STATE_INVALID = 0|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BondState；<br>API声明：BOND_STATE_BONDING = 1<br>差异内容：BOND_STATE_BONDING = 1|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：BondState；<br>API声明：BOND_STATE_BONDED = 2<br>差异内容：BOND_STATE_BONDED = 2|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：enum MajorClass<br>差异内容：enum MajorClass|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_MISC = 0x0000<br>差异内容：MAJOR_MISC = 0x0000|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_COMPUTER = 0x0100<br>差异内容：MAJOR_COMPUTER = 0x0100|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_PHONE = 0x0200<br>差异内容：MAJOR_PHONE = 0x0200|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_NETWORKING = 0x0300<br>差异内容：MAJOR_NETWORKING = 0x0300|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_AUDIO_VIDEO = 0x0400<br>差异内容：MAJOR_AUDIO_VIDEO = 0x0400|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_PERIPHERAL = 0x0500<br>差异内容：MAJOR_PERIPHERAL = 0x0500|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_IMAGING = 0x0600<br>差异内容：MAJOR_IMAGING = 0x0600|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_WEARABLE = 0x0700<br>差异内容：MAJOR_WEARABLE = 0x0700|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_TOY = 0x0800<br>差异内容：MAJOR_TOY = 0x0800|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_HEALTH = 0x0900<br>差异内容：MAJOR_HEALTH = 0x0900|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorClass；<br>API声明：MAJOR_UNCATEGORIZED = 0x1F00<br>差异内容：MAJOR_UNCATEGORIZED = 0x1F00|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：enum MajorMinorClass<br>差异内容：enum MajorMinorClass|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_UNCATEGORIZED = 0x0100<br>差异内容：COMPUTER_UNCATEGORIZED = 0x0100|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_DESKTOP = 0x0104<br>差异内容：COMPUTER_DESKTOP = 0x0104|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_SERVER = 0x0108<br>差异内容：COMPUTER_SERVER = 0x0108|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_LAPTOP = 0x010C<br>差异内容：COMPUTER_LAPTOP = 0x010C|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_HANDHELD_PC_PDA = 0x0110<br>差异内容：COMPUTER_HANDHELD_PC_PDA = 0x0110|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_PALM_SIZE_PC_PDA = 0x0114<br>差异内容：COMPUTER_PALM_SIZE_PC_PDA = 0x0114|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_WEARABLE = 0x0118<br>差异内容：COMPUTER_WEARABLE = 0x0118|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：COMPUTER_TABLET = 0x011C<br>差异内容：COMPUTER_TABLET = 0x011C|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PHONE_UNCATEGORIZED = 0x0200<br>差异内容：PHONE_UNCATEGORIZED = 0x0200|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PHONE_CELLULAR = 0x0204<br>差异内容：PHONE_CELLULAR = 0x0204|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PHONE_CORDLESS = 0x0208<br>差异内容：PHONE_CORDLESS = 0x0208|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PHONE_SMART = 0x020C<br>差异内容：PHONE_SMART = 0x020C|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PHONE_MODEM_OR_GATEWAY = 0x0210<br>差异内容：PHONE_MODEM_OR_GATEWAY = 0x0210|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PHONE_ISDN = 0x0214<br>差异内容：PHONE_ISDN = 0x0214|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_FULLY_AVAILABLE = 0x0300<br>差异内容：NETWORK_FULLY_AVAILABLE = 0x0300|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_1_TO_17_UTILIZED = 0x0320<br>差异内容：NETWORK_1_TO_17_UTILIZED = 0x0320|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_17_TO_33_UTILIZED = 0x0340<br>差异内容：NETWORK_17_TO_33_UTILIZED = 0x0340|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_33_TO_50_UTILIZED = 0x0360<br>差异内容：NETWORK_33_TO_50_UTILIZED = 0x0360|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_60_TO_67_UTILIZED = 0x0380<br>差异内容：NETWORK_60_TO_67_UTILIZED = 0x0380|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_67_TO_83_UTILIZED = 0x03A0<br>差异内容：NETWORK_67_TO_83_UTILIZED = 0x03A0|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_83_TO_99_UTILIZED = 0x03C0<br>差异内容：NETWORK_83_TO_99_UTILIZED = 0x03C0|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：NETWORK_NO_SERVICE = 0x03E0<br>差异内容：NETWORK_NO_SERVICE = 0x03E0|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_UNCATEGORIZED = 0x0400<br>差异内容：AUDIO_VIDEO_UNCATEGORIZED = 0x0400|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_WEARABLE_HEADSET = 0x0404<br>差异内容：AUDIO_VIDEO_WEARABLE_HEADSET = 0x0404|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_HANDSFREE = 0x0408<br>差异内容：AUDIO_VIDEO_HANDSFREE = 0x0408|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_MICROPHONE = 0x0410<br>差异内容：AUDIO_VIDEO_MICROPHONE = 0x0410|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_LOUDSPEAKER = 0x0414<br>差异内容：AUDIO_VIDEO_LOUDSPEAKER = 0x0414|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_HEADPHONES = 0x0418<br>差异内容：AUDIO_VIDEO_HEADPHONES = 0x0418|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_PORTABLE_AUDIO = 0x041C<br>差异内容：AUDIO_VIDEO_PORTABLE_AUDIO = 0x041C|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_CAR_AUDIO = 0x0420<br>差异内容：AUDIO_VIDEO_CAR_AUDIO = 0x0420|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_SET_TOP_BOX = 0x0424<br>差异内容：AUDIO_VIDEO_SET_TOP_BOX = 0x0424|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_HIFI_AUDIO = 0x0428<br>差异内容：AUDIO_VIDEO_HIFI_AUDIO = 0x0428|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_VCR = 0x042C<br>差异内容：AUDIO_VIDEO_VCR = 0x042C|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_VIDEO_CAMERA = 0x0430<br>差异内容：AUDIO_VIDEO_VIDEO_CAMERA = 0x0430|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_CAMCORDER = 0x0434<br>差异内容：AUDIO_VIDEO_CAMCORDER = 0x0434|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_VIDEO_MONITOR = 0x0438<br>差异内容：AUDIO_VIDEO_VIDEO_MONITOR = 0x0438|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_VIDEO_DISPLAY_AND_LOUDSPEAKER = 0x043C<br>差异内容：AUDIO_VIDEO_VIDEO_DISPLAY_AND_LOUDSPEAKER = 0x043C|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_VIDEO_CONFERENCING = 0x0440<br>差异内容：AUDIO_VIDEO_VIDEO_CONFERENCING = 0x0440|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：AUDIO_VIDEO_VIDEO_GAMING_TOY = 0x0448<br>差异内容：AUDIO_VIDEO_VIDEO_GAMING_TOY = 0x0448|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_NON_KEYBOARD_NON_POINTING = 0x0500<br>差异内容：PERIPHERAL_NON_KEYBOARD_NON_POINTING = 0x0500|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_KEYBOARD = 0x0540<br>差异内容：PERIPHERAL_KEYBOARD = 0x0540|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_POINTING_DEVICE = 0x0580<br>差异内容：PERIPHERAL_POINTING_DEVICE = 0x0580|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_KEYBOARD_POINTING = 0x05C0<br>差异内容：PERIPHERAL_KEYBOARD_POINTING = 0x05C0|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_UNCATEGORIZED = 0x0500<br>差异内容：PERIPHERAL_UNCATEGORIZED = 0x0500|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_JOYSTICK = 0x0504<br>差异内容：PERIPHERAL_JOYSTICK = 0x0504|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_GAMEPAD = 0x0508<br>差异内容：PERIPHERAL_GAMEPAD = 0x0508|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_REMOTE_CONTROL = 0x05C0<br>差异内容：PERIPHERAL_REMOTE_CONTROL = 0x05C0|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_SENSING_DEVICE = 0x0510<br>差异内容：PERIPHERAL_SENSING_DEVICE = 0x0510|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_DIGITIZER_TABLET = 0x0514<br>差异内容：PERIPHERAL_DIGITIZER_TABLET = 0x0514|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_CARD_READER = 0x0518<br>差异内容：PERIPHERAL_CARD_READER = 0x0518|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_DIGITAL_PEN = 0x051C<br>差异内容：PERIPHERAL_DIGITAL_PEN = 0x051C|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_SCANNER_RFID = 0x0520<br>差异内容：PERIPHERAL_SCANNER_RFID = 0x0520|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：PERIPHERAL_GESTURAL_INPUT = 0x0522<br>差异内容：PERIPHERAL_GESTURAL_INPUT = 0x0522|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：IMAGING_UNCATEGORIZED = 0x0600<br>差异内容：IMAGING_UNCATEGORIZED = 0x0600|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：IMAGING_DISPLAY = 0x0610<br>差异内容：IMAGING_DISPLAY = 0x0610|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：IMAGING_CAMERA = 0x0620<br>差异内容：IMAGING_CAMERA = 0x0620|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：IMAGING_SCANNER = 0x0640<br>差异内容：IMAGING_SCANNER = 0x0640|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：IMAGING_PRINTER = 0x0680<br>差异内容：IMAGING_PRINTER = 0x0680|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：WEARABLE_UNCATEGORIZED = 0x0700<br>差异内容：WEARABLE_UNCATEGORIZED = 0x0700|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：WEARABLE_WRIST_WATCH = 0x0704<br>差异内容：WEARABLE_WRIST_WATCH = 0x0704|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：WEARABLE_PAGER = 0x0708<br>差异内容：WEARABLE_PAGER = 0x0708|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：WEARABLE_JACKET = 0x070C<br>差异内容：WEARABLE_JACKET = 0x070C|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：WEARABLE_HELMET = 0x0710<br>差异内容：WEARABLE_HELMET = 0x0710|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：WEARABLE_GLASSES = 0x0714<br>差异内容：WEARABLE_GLASSES = 0x0714|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：TOY_UNCATEGORIZED = 0x0800<br>差异内容：TOY_UNCATEGORIZED = 0x0800|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：TOY_ROBOT = 0x0804<br>差异内容：TOY_ROBOT = 0x0804|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：TOY_VEHICLE = 0x0808<br>差异内容：TOY_VEHICLE = 0x0808|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：TOY_DOLL_ACTION_FIGURE = 0x080C<br>差异内容：TOY_DOLL_ACTION_FIGURE = 0x080C|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：TOY_CONTROLLER = 0x0810<br>差异内容：TOY_CONTROLLER = 0x0810|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：TOY_GAME = 0x0814<br>差异内容：TOY_GAME = 0x0814|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_UNCATEGORIZED = 0x0900<br>差异内容：HEALTH_UNCATEGORIZED = 0x0900|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_BLOOD_PRESSURE = 0x0904<br>差异内容：HEALTH_BLOOD_PRESSURE = 0x0904|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_THERMOMETER = 0x0908<br>差异内容：HEALTH_THERMOMETER = 0x0908|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_WEIGHING = 0x090C<br>差异内容：HEALTH_WEIGHING = 0x090C|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_GLUCOSE = 0x0910<br>差异内容：HEALTH_GLUCOSE = 0x0910|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_PULSE_OXIMETER = 0x0914<br>差异内容：HEALTH_PULSE_OXIMETER = 0x0914|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_PULSE_RATE = 0x0918<br>差异内容：HEALTH_PULSE_RATE = 0x0918|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_DATA_DISPLAY = 0x091C<br>差异内容：HEALTH_DATA_DISPLAY = 0x091C|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_STEP_COUNTER = 0x0920<br>差异内容：HEALTH_STEP_COUNTER = 0x0920|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_BODY_COMPOSITION_ANALYZER = 0x0924<br>差异内容：HEALTH_BODY_COMPOSITION_ANALYZER = 0x0924|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_PEAK_FLOW_MONITOR = 0x0928<br>差异内容：HEALTH_PEAK_FLOW_MONITOR = 0x0928|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_MEDICATION_MONITOR = 0x092C<br>差异内容：HEALTH_MEDICATION_MONITOR = 0x092C|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_KNEE_PROSTHESIS = 0x0930<br>差异内容：HEALTH_KNEE_PROSTHESIS = 0x0930|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_ANKLE_PROSTHESIS = 0x0934<br>差异内容：HEALTH_ANKLE_PROSTHESIS = 0x0934|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_GENERIC_HEALTH_MANAGER = 0x0938<br>差异内容：HEALTH_GENERIC_HEALTH_MANAGER = 0x0938|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：MajorMinorClass；<br>API声明：HEALTH_PERSONAL_MOBILITY_DEVICE = 0x093C<br>差异内容：HEALTH_PERSONAL_MOBILITY_DEVICE = 0x093C|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：enum PlayingState<br>差异内容：enum PlayingState|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：PlayingState；<br>API声明：STATE_NOT_PLAYING<br>差异内容：STATE_NOT_PLAYING|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：PlayingState；<br>API声明：STATE_PLAYING<br>差异内容：STATE_PLAYING|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：enum ProfileId<br>差异内容：enum ProfileId|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ProfileId；<br>API声明：PROFILE_A2DP_SOURCE = 1<br>差异内容：PROFILE_A2DP_SOURCE = 1|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ProfileId；<br>API声明：PROFILE_HANDS_FREE_AUDIO_GATEWAY = 4<br>差异内容：PROFILE_HANDS_FREE_AUDIO_GATEWAY = 4|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ProfileId；<br>API声明：PROFILE_HID_HOST = 6<br>差异内容：PROFILE_HID_HOST = 6|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：ProfileId；<br>API声明：PROFILE_PAN_NETWORK = 7<br>差异内容：PROFILE_PAN_NETWORK = 7|api/@ohos.bluetoothManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace connectedTag<br>差异内容：declare namespace connectedTag|api/@ohos.connectedTag.d.ts|
|新增API|NA|类名：connectedTag；<br>API声明：function init(): boolean;<br>差异内容：function init(): boolean;|api/@ohos.connectedTag.d.ts|
|新增API|NA|类名：connectedTag；<br>API声明：function initialize(): void;<br>差异内容：function initialize(): void;|api/@ohos.connectedTag.d.ts|
|新增API|NA|类名：connectedTag；<br>API声明：function uninit(): boolean;<br>差异内容：function uninit(): boolean;|api/@ohos.connectedTag.d.ts|
|新增API|NA|类名：connectedTag；<br>API声明：function uninitialize(): void;<br>差异内容：function uninitialize(): void;|api/@ohos.connectedTag.d.ts|
|新增API|NA|类名：connectedTag；<br>API声明：function readNdefTag(): Promise\<string>;<br>差异内容：function readNdefTag(): Promise\<string>;|api/@ohos.connectedTag.d.ts|
|新增API|NA|类名：connectedTag；<br>API声明：function readNdefTag(callback: AsyncCallback\<string>): void;<br>差异内容：function readNdefTag(callback: AsyncCallback\<string>): void;|api/@ohos.connectedTag.d.ts|
|新增API|NA|类名：connectedTag；<br>API声明：function read(): Promise\<number[]>;<br>差异内容：function read(): Promise\<number[]>;|api/@ohos.connectedTag.d.ts|
|新增API|NA|类名：connectedTag；<br>API声明：function read(callback: AsyncCallback\<number[]>): void;<br>差异内容：function read(callback: AsyncCallback\<number[]>): void;|api/@ohos.connectedTag.d.ts|
|新增API|NA|类名：connectedTag；<br>API声明：function writeNdefTag(data: string): Promise\<void>;<br>差异内容：function writeNdefTag(data: string): Promise\<void>;|api/@ohos.connectedTag.d.ts|
|新增API|NA|类名：connectedTag；<br>API声明：function writeNdefTag(data: string, callback: AsyncCallback\<void>): void;<br>差异内容：function writeNdefTag(data: string, callback: AsyncCallback\<void>): void;|api/@ohos.connectedTag.d.ts|
|新增API|NA|类名：connectedTag；<br>API声明：function write(data: number[]): Promise\<void>;<br>差异内容：function write(data: number[]): Promise\<void>;|api/@ohos.connectedTag.d.ts|
|新增API|NA|类名：connectedTag；<br>API声明：function write(data: number[], callback: AsyncCallback\<void>): void;<br>差异内容：function write(data: number[], callback: AsyncCallback\<void>): void;|api/@ohos.connectedTag.d.ts|
|新增API|NA|类名：connectedTag；<br>API声明：function on(type: 'notify', callback: Callback\<number>): void;<br>差异内容：function on(type: 'notify', callback: Callback\<number>): void;|api/@ohos.connectedTag.d.ts|
|新增API|NA|类名：connectedTag；<br>API声明：function off(type: 'notify', callback?: Callback\<number>): void;<br>差异内容：function off(type: 'notify', callback?: Callback\<number>): void;|api/@ohos.connectedTag.d.ts|
|新增API|NA|类名：connectedTag；<br>API声明：enum NfcRfType<br>差异内容：enum NfcRfType|api/@ohos.connectedTag.d.ts|
|新增API|NA|类名：NfcRfType；<br>API声明：NFC_RF_LEAVE = 0<br>差异内容：NFC_RF_LEAVE = 0|api/@ohos.connectedTag.d.ts|
|新增API|NA|类名：NfcRfType；<br>API声明：NFC_RF_ENTER = 1<br>差异内容：NFC_RF_ENTER = 1|api/@ohos.connectedTag.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace cardEmulation<br>差异内容：declare namespace cardEmulation|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：cardEmulation；<br>API声明：enum FeatureType<br>差异内容：enum FeatureType|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：FeatureType；<br>API声明：HCE = 0<br>差异内容：HCE = 0|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：FeatureType；<br>API声明：UICC = 1<br>差异内容：UICC = 1|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：FeatureType；<br>API声明：ESE = 2<br>差异内容：ESE = 2|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：cardEmulation；<br>API声明：enum CardType<br>差异内容：enum CardType|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：CardType；<br>API声明：PAYMENT = 'payment'<br>差异内容：PAYMENT = 'payment'|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：CardType；<br>API声明：OTHER = 'other'<br>差异内容：OTHER = 'other'|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：cardEmulation；<br>API声明：function isSupported(feature: number): boolean;<br>差异内容：function isSupported(feature: number): boolean;|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：cardEmulation；<br>API声明：function hasHceCapability(): boolean;<br>差异内容：function hasHceCapability(): boolean;|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：cardEmulation；<br>API声明：function isDefaultService(elementName: ElementName, type: CardType): boolean;<br>差异内容：function isDefaultService(elementName: ElementName, type: CardType): boolean;|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：cardEmulation；<br>API声明：export class HceService<br>差异内容：export class HceService|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：HceService；<br>API声明：startHCE(aidList: string[]): boolean;<br>差异内容：startHCE(aidList: string[]): boolean;|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：HceService；<br>API声明：start(elementName: ElementName, aidList: string[]): void;<br>差异内容：start(elementName: ElementName, aidList: string[]): void;|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：HceService；<br>API声明：stopHCE(): boolean;<br>差异内容：stopHCE(): boolean;|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：HceService；<br>API声明：stop(elementName: ElementName): void;<br>差异内容：stop(elementName: ElementName): void;|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：HceService；<br>API声明：on(type: 'hceCmd', callback: AsyncCallback\<number[]>): void;<br>差异内容：on(type: 'hceCmd', callback: AsyncCallback\<number[]>): void;|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：HceService；<br>API声明：sendResponse(responseApdu: number[]): void;<br>差异内容：sendResponse(responseApdu: number[]): void;|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：HceService；<br>API声明：transmit(response: number[]): Promise\<void>;<br>差异内容：transmit(response: number[]): Promise\<void>;|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：HceService；<br>API声明：transmit(response: number[], callback: AsyncCallback\<void>): void;<br>差异内容：transmit(response: number[], callback: AsyncCallback\<void>): void;|api/@ohos.nfc.cardEmulation.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace nfcController<br>差异内容：declare namespace nfcController|api/@ohos.nfc.controller.d.ts|
|新增API|NA|类名：nfcController；<br>API声明：enum NfcState<br>差异内容：enum NfcState|api/@ohos.nfc.controller.d.ts|
|新增API|NA|类名：NfcState；<br>API声明：STATE_OFF = 1<br>差异内容：STATE_OFF = 1|api/@ohos.nfc.controller.d.ts|
|新增API|NA|类名：NfcState；<br>API声明：STATE_TURNING_ON = 2<br>差异内容：STATE_TURNING_ON = 2|api/@ohos.nfc.controller.d.ts|
|新增API|NA|类名：NfcState；<br>API声明：STATE_ON = 3<br>差异内容：STATE_ON = 3|api/@ohos.nfc.controller.d.ts|
|新增API|NA|类名：NfcState；<br>API声明：STATE_TURNING_OFF = 4<br>差异内容：STATE_TURNING_OFF = 4|api/@ohos.nfc.controller.d.ts|
|新增API|NA|类名：nfcController；<br>API声明：function isNfcAvailable(): boolean;<br>差异内容：function isNfcAvailable(): boolean;|api/@ohos.nfc.controller.d.ts|
|新增API|NA|类名：nfcController；<br>API声明：function on(type: 'nfcStateChange', callback: Callback\<NfcState>): void;<br>差异内容：function on(type: 'nfcStateChange', callback: Callback\<NfcState>): void;|api/@ohos.nfc.controller.d.ts|
|新增API|NA|类名：nfcController；<br>API声明：function off(type: 'nfcStateChange', callback?: Callback\<NfcState>): void;<br>差异内容：function off(type: 'nfcStateChange', callback?: Callback\<NfcState>): void;|api/@ohos.nfc.controller.d.ts|
|新增API|NA|类名：nfcController；<br>API声明：function openNfc(): boolean;<br>差异内容：function openNfc(): boolean;|api/@ohos.nfc.controller.d.ts|
|新增API|NA|类名：nfcController；<br>API声明：function enableNfc(): void;<br>差异内容：function enableNfc(): void;|api/@ohos.nfc.controller.d.ts|
|新增API|NA|类名：nfcController；<br>API声明：function closeNfc(): boolean;<br>差异内容：function closeNfc(): boolean;|api/@ohos.nfc.controller.d.ts|
|新增API|NA|类名：nfcController；<br>API声明：function disableNfc(): void;<br>差异内容：function disableNfc(): void;|api/@ohos.nfc.controller.d.ts|
|新增API|NA|类名：nfcController；<br>API声明：function isNfcOpen(): boolean;<br>差异内容：function isNfcOpen(): boolean;|api/@ohos.nfc.controller.d.ts|
|新增API|NA|类名：nfcController；<br>API声明：function getNfcState(): NfcState;<br>差异内容：function getNfcState(): NfcState;|api/@ohos.nfc.controller.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace tag<br>差异内容：declare namespace tag|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：const NFC_A = 1;<br>差异内容：const NFC_A = 1;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：const NFC_B = 2;<br>差异内容：const NFC_B = 2;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：const ISO_DEP = 3;<br>差异内容：const ISO_DEP = 3;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：const NFC_F = 4;<br>差异内容：const NFC_F = 4;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：const NFC_V = 5;<br>差异内容：const NFC_V = 5;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：const NDEF = 6;<br>差异内容：const NDEF = 6;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：const NDEF_FORMATABLE = 7;<br>差异内容：const NDEF_FORMATABLE = 7;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：const MIFARE_CLASSIC = 8;<br>差异内容：const MIFARE_CLASSIC = 8;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：const MIFARE_ULTRALIGHT = 9;<br>差异内容：const MIFARE_ULTRALIGHT = 9;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：enum TnfType<br>差异内容：enum TnfType|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：TnfType；<br>API声明：TNF_EMPTY = 0x0<br>差异内容：TNF_EMPTY = 0x0|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：TnfType；<br>API声明：TNF_WELL_KNOWN = 0x1<br>差异内容：TNF_WELL_KNOWN = 0x1|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：TnfType；<br>API声明：TNF_MEDIA = 0x2<br>差异内容：TNF_MEDIA = 0x2|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：TnfType；<br>API声明：TNF_ABSOLUTE_URI = 0x3<br>差异内容：TNF_ABSOLUTE_URI = 0x3|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：TnfType；<br>API声明：TNF_EXT_APP = 0x4<br>差异内容：TNF_EXT_APP = 0x4|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：TnfType；<br>API声明：TNF_UNKNOWN = 0x5<br>差异内容：TNF_UNKNOWN = 0x5|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：TnfType；<br>API声明：TNF_UNCHANGED = 0x6<br>差异内容：TNF_UNCHANGED = 0x6|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：enum NfcForumType<br>差异内容：enum NfcForumType|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：NfcForumType；<br>API声明：NFC_FORUM_TYPE_1 = 1<br>差异内容：NFC_FORUM_TYPE_1 = 1|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：NfcForumType；<br>API声明：NFC_FORUM_TYPE_2 = 2<br>差异内容：NFC_FORUM_TYPE_2 = 2|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：NfcForumType；<br>API声明：NFC_FORUM_TYPE_3 = 3<br>差异内容：NFC_FORUM_TYPE_3 = 3|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：NfcForumType；<br>API声明：NFC_FORUM_TYPE_4 = 4<br>差异内容：NFC_FORUM_TYPE_4 = 4|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：NfcForumType；<br>API声明：MIFARE_CLASSIC = 101<br>差异内容：MIFARE_CLASSIC = 101|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：const RTD_TEXT: number[];<br>差异内容：const RTD_TEXT: number[];|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：const RTD_URI: number[];<br>差异内容：const RTD_URI: number[];|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：enum MifareClassicType<br>差异内容：enum MifareClassicType|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：MifareClassicType；<br>API声明：TYPE_UNKNOWN = 0<br>差异内容：TYPE_UNKNOWN = 0|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：MifareClassicType；<br>API声明：TYPE_CLASSIC = 1<br>差异内容：TYPE_CLASSIC = 1|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：MifareClassicType；<br>API声明：TYPE_PLUS = 2<br>差异内容：TYPE_PLUS = 2|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：MifareClassicType；<br>API声明：TYPE_PRO = 3<br>差异内容：TYPE_PRO = 3|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：enum MifareClassicSize<br>差异内容：enum MifareClassicSize|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：MifareClassicSize；<br>API声明：MC_SIZE_MINI = 320<br>差异内容：MC_SIZE_MINI = 320|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：MifareClassicSize；<br>API声明：MC_SIZE_1K = 1024<br>差异内容：MC_SIZE_1K = 1024|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：MifareClassicSize；<br>API声明：MC_SIZE_2K = 2048<br>差异内容：MC_SIZE_2K = 2048|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：MifareClassicSize；<br>API声明：MC_SIZE_4K = 4096<br>差异内容：MC_SIZE_4K = 4096|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：enum MifareUltralightType<br>差异内容：enum MifareUltralightType|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：MifareUltralightType；<br>API声明：TYPE_UNKNOWN = 0<br>差异内容：TYPE_UNKNOWN = 0|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：MifareUltralightType；<br>API声明：TYPE_ULTRALIGHT = 1<br>差异内容：TYPE_ULTRALIGHT = 1|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：MifareUltralightType；<br>API声明：TYPE_ULTRALIGHT_C = 2<br>差异内容：TYPE_ULTRALIGHT_C = 2|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function getNfcATag(tagInfo: TagInfo): NfcATag;<br>差异内容：function getNfcATag(tagInfo: TagInfo): NfcATag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function getNfcA(tagInfo: TagInfo): NfcATag;<br>差异内容：function getNfcA(tagInfo: TagInfo): NfcATag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function getNfcBTag(tagInfo: TagInfo): NfcBTag;<br>差异内容：function getNfcBTag(tagInfo: TagInfo): NfcBTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function getNfcB(tagInfo: TagInfo): NfcBTag;<br>差异内容：function getNfcB(tagInfo: TagInfo): NfcBTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function getNfcFTag(tagInfo: TagInfo): NfcFTag;<br>差异内容：function getNfcFTag(tagInfo: TagInfo): NfcFTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function getNfcF(tagInfo: TagInfo): NfcFTag;<br>差异内容：function getNfcF(tagInfo: TagInfo): NfcFTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function getNfcVTag(tagInfo: TagInfo): NfcVTag;<br>差异内容：function getNfcVTag(tagInfo: TagInfo): NfcVTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function getNfcV(tagInfo: TagInfo): NfcVTag;<br>差异内容：function getNfcV(tagInfo: TagInfo): NfcVTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function getIsoDep(tagInfo: TagInfo): IsoDepTag;<br>差异内容：function getIsoDep(tagInfo: TagInfo): IsoDepTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function getNdef(tagInfo: TagInfo): NdefTag;<br>差异内容：function getNdef(tagInfo: TagInfo): NdefTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function getMifareClassic(tagInfo: TagInfo): MifareClassicTag;<br>差异内容：function getMifareClassic(tagInfo: TagInfo): MifareClassicTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function getMifareUltralight(tagInfo: TagInfo): MifareUltralightTag;<br>差异内容：function getMifareUltralight(tagInfo: TagInfo): MifareUltralightTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function getNdefFormatable(tagInfo: TagInfo): NdefFormatableTag;<br>差异内容：function getNdefFormatable(tagInfo: TagInfo): NdefFormatableTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function getTagInfo(want: Want): TagInfo;<br>差异内容：function getTagInfo(want: Want): TagInfo;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function registerForegroundDispatch(elementName: ElementName, discTech: number[], callback: AsyncCallback\<TagInfo>): void;<br>差异内容：function registerForegroundDispatch(elementName: ElementName, discTech: number[], callback: AsyncCallback\<TagInfo>): void;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function unregisterForegroundDispatch(elementName: ElementName): void;<br>差异内容：function unregisterForegroundDispatch(elementName: ElementName): void;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function on(type: 'readerMode', elementName: ElementName, discTech: number[], callback: AsyncCallback\<TagInfo>): void;<br>差异内容：function on(type: 'readerMode', elementName: ElementName, discTech: number[], callback: AsyncCallback\<TagInfo>): void;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：function off(type: 'readerMode', elementName: ElementName, callback?: AsyncCallback\<TagInfo>): void;<br>差异内容：function off(type: 'readerMode', elementName: ElementName, callback?: AsyncCallback\<TagInfo>): void;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：export interface TagInfo<br>差异内容：export interface TagInfo|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：TagInfo；<br>API声明：uid: number[];<br>差异内容：uid: number[];|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：TagInfo；<br>API声明：technology: number[];<br>差异内容：technology: number[];|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：TagInfo；<br>API声明：supportedProfiles: number[];<br>差异内容：supportedProfiles: number[];|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：export interface NdefRecord<br>差异内容：export interface NdefRecord|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：NdefRecord；<br>API声明：tnf: number;<br>差异内容：tnf: number;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：NdefRecord；<br>API声明：rtdType: number[];<br>差异内容：rtdType: number[];|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：NdefRecord；<br>API声明：id: number[];<br>差异内容：id: number[];|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：NdefRecord；<br>API声明：payload: number[];<br>差异内容：payload: number[];|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：namespace ndef<br>差异内容：namespace ndef|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：ndef；<br>API声明：function makeUriRecord(uri: string): NdefRecord;<br>差异内容：function makeUriRecord(uri: string): NdefRecord;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：ndef；<br>API声明：function makeTextRecord(text: string, locale: string): NdefRecord;<br>差异内容：function makeTextRecord(text: string, locale: string): NdefRecord;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：ndef；<br>API声明：function makeMimeRecord(mimeType: string, mimeData: number[]): NdefRecord;<br>差异内容：function makeMimeRecord(mimeType: string, mimeData: number[]): NdefRecord;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：ndef；<br>API声明：function makeExternalRecord(domainName: string, type: string, externalData: number[]): NdefRecord;<br>差异内容：function makeExternalRecord(domainName: string, type: string, externalData: number[]): NdefRecord;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：ndef；<br>API声明：function createNdefMessage(data: number[]): NdefMessage;<br>差异内容：function createNdefMessage(data: number[]): NdefMessage;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：ndef；<br>API声明：function createNdefMessage(ndefRecords: NdefRecord[]): NdefMessage;<br>差异内容：function createNdefMessage(ndefRecords: NdefRecord[]): NdefMessage;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：ndef；<br>API声明：function messageToBytes(ndefMessage: NdefMessage): number[];<br>差异内容：function messageToBytes(ndefMessage: NdefMessage): number[];|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：export type NfcATag = _NfcATag;<br>差异内容：export type NfcATag = _NfcATag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：export type NfcBTag = _NfcBTag;<br>差异内容：export type NfcBTag = _NfcBTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：export type NfcFTag = _NfcFTag;<br>差异内容：export type NfcFTag = _NfcFTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：export type NfcVTag = _NfcVTag;<br>差异内容：export type NfcVTag = _NfcVTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：export type IsoDepTag = _IsoDepTag;<br>差异内容：export type IsoDepTag = _IsoDepTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：export type NdefTag = _NdefTag;<br>差异内容：export type NdefTag = _NdefTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：export type MifareClassicTag = _MifareClassicTag;<br>差异内容：export type MifareClassicTag = _MifareClassicTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：export type MifareUltralightTag = _MifareUltralightTag;<br>差异内容：export type MifareUltralightTag = _MifareUltralightTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：export type NdefFormatableTag = _NdefFormatableTag;<br>差异内容：export type NdefFormatableTag = _NdefFormatableTag;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：export type NdefMessage = _NdefMessage;<br>差异内容：export type NdefMessage = _NdefMessage;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：tag；<br>API声明：export type TagSession = _TagSession;<br>差异内容：export type TagSession = _TagSession;|api/@ohos.nfc.tag.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace omapi<br>差异内容：declare namespace omapi|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：omapi；<br>API声明：function newSEService(type: 'serviceState', callback: Callback\<ServiceState>): SEService;<br>差异内容：function newSEService(type: 'serviceState', callback: Callback\<ServiceState>): SEService;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：omapi；<br>API声明：export interface SEService<br>差异内容：export interface SEService|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：SEService；<br>API声明：getReaders(): Reader[];<br>差异内容：getReaders(): Reader[];|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：SEService；<br>API声明：isConnected(): boolean;<br>差异内容：isConnected(): boolean;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：SEService；<br>API声明：shutdown(): void;<br>差异内容：shutdown(): void;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：SEService；<br>API声明：getVersion(): string;<br>差异内容：getVersion(): string;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：omapi；<br>API声明：export interface Reader<br>差异内容：export interface Reader|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Reader；<br>API声明：getName(): string;<br>差异内容：getName(): string;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Reader；<br>API声明：isSecureElementPresent(): boolean;<br>差异内容：isSecureElementPresent(): boolean;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Reader；<br>API声明：openSession(): Session;<br>差异内容：openSession(): Session;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Reader；<br>API声明：closeSessions(): void;<br>差异内容：closeSessions(): void;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：omapi；<br>API声明：export interface Session<br>差异内容：export interface Session|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Session；<br>API声明：getReader(): Reader;<br>差异内容：getReader(): Reader;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Session；<br>API声明：getATR(): number[];<br>差异内容：getATR(): number[];|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Session；<br>API声明：close(): void;<br>差异内容：close(): void;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Session；<br>API声明：isClosed(): boolean;<br>差异内容：isClosed(): boolean;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Session；<br>API声明：closeChannels(): void;<br>差异内容：closeChannels(): void;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Session；<br>API声明：openBasicChannel(aid: number[]): Promise\<Channel>;<br>差异内容：openBasicChannel(aid: number[]): Promise\<Channel>;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Session；<br>API声明：openBasicChannel(aid: number[], callback: AsyncCallback\<Channel>): void;<br>差异内容：openBasicChannel(aid: number[], callback: AsyncCallback\<Channel>): void;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Session；<br>API声明：openBasicChannel(aid: number[], p2: number): Promise\<Channel>;<br>差异内容：openBasicChannel(aid: number[], p2: number): Promise\<Channel>;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Session；<br>API声明：openBasicChannel(aid: number[], p2: number, callback: AsyncCallback\<Channel>): void;<br>差异内容：openBasicChannel(aid: number[], p2: number, callback: AsyncCallback\<Channel>): void;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Session；<br>API声明：openLogicalChannel(aid: number[]): Promise\<Channel>;<br>差异内容：openLogicalChannel(aid: number[]): Promise\<Channel>;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Session；<br>API声明：openLogicalChannel(aid: number[], callback: AsyncCallback\<Channel>): void;<br>差异内容：openLogicalChannel(aid: number[], callback: AsyncCallback\<Channel>): void;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Session；<br>API声明：openLogicalChannel(aid: number[], p2: number): Promise\<Channel>;<br>差异内容：openLogicalChannel(aid: number[], p2: number): Promise\<Channel>;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Session；<br>API声明：openLogicalChannel(aid: number[], p2: number, callback: AsyncCallback\<Channel>): void;<br>差异内容：openLogicalChannel(aid: number[], p2: number, callback: AsyncCallback\<Channel>): void;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：omapi；<br>API声明：export interface Channel<br>差异内容：export interface Channel|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Channel；<br>API声明：getSession(): Session;<br>差异内容：getSession(): Session;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Channel；<br>API声明：close(): void;<br>差异内容：close(): void;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Channel；<br>API声明：isBasicChannel(): boolean;<br>差异内容：isBasicChannel(): boolean;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Channel；<br>API声明：isClosed(): boolean;<br>差异内容：isClosed(): boolean;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Channel；<br>API声明：getSelectResponse(): number[];<br>差异内容：getSelectResponse(): number[];|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Channel；<br>API声明：transmit(command: number[]): Promise\<number[]>;<br>差异内容：transmit(command: number[]): Promise\<number[]>;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：Channel；<br>API声明：transmit(command: number[], callback: AsyncCallback\<number[]>): void;<br>差异内容：transmit(command: number[], callback: AsyncCallback\<number[]>): void;|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：omapi；<br>API声明：enum ServiceState<br>差异内容：enum ServiceState|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：ServiceState；<br>API声明：DISCONNECTED = 0<br>差异内容：DISCONNECTED = 0|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：ServiceState；<br>API声明：CONNECTED = 1<br>差异内容：CONNECTED = 1|api/@ohos.secureElement.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace wifi<br>差异内容：declare namespace wifi|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function isWifiActive(): boolean;<br>差异内容：function isWifiActive(): boolean;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function scan(): boolean;<br>差异内容：function scan(): boolean;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function getScanInfos(): Promise\<Array\<WifiScanInfo>>;<br>差异内容：function getScanInfos(): Promise\<Array\<WifiScanInfo>>;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function getScanInfos(callback: AsyncCallback\<Array\<WifiScanInfo>>): void;<br>差异内容：function getScanInfos(callback: AsyncCallback\<Array\<WifiScanInfo>>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function addUntrustedConfig(config: WifiDeviceConfig): Promise\<boolean>;<br>差异内容：function addUntrustedConfig(config: WifiDeviceConfig): Promise\<boolean>;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function addUntrustedConfig(config: WifiDeviceConfig, callback: AsyncCallback\<boolean>): void;<br>差异内容：function addUntrustedConfig(config: WifiDeviceConfig, callback: AsyncCallback\<boolean>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function removeUntrustedConfig(config: WifiDeviceConfig): Promise\<boolean>;<br>差异内容：function removeUntrustedConfig(config: WifiDeviceConfig): Promise\<boolean>;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function removeUntrustedConfig(config: WifiDeviceConfig, callback: AsyncCallback\<boolean>): void;<br>差异内容：function removeUntrustedConfig(config: WifiDeviceConfig, callback: AsyncCallback\<boolean>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function getSignalLevel(rssi: number, band: number): number;<br>差异内容：function getSignalLevel(rssi: number, band: number): number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function getLinkedInfo(): Promise\<WifiLinkedInfo>;<br>差异内容：function getLinkedInfo(): Promise\<WifiLinkedInfo>;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function getLinkedInfo(callback: AsyncCallback\<WifiLinkedInfo>): void;<br>差异内容：function getLinkedInfo(callback: AsyncCallback\<WifiLinkedInfo>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function isConnected(): boolean;<br>差异内容：function isConnected(): boolean;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function isFeatureSupported(featureId: number): boolean;<br>差异内容：function isFeatureSupported(featureId: number): boolean;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function getIpInfo(): IpInfo;<br>差异内容：function getIpInfo(): IpInfo;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function getCountryCode(): string;<br>差异内容：function getCountryCode(): string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function getP2pLinkedInfo(): Promise\<WifiP2pLinkedInfo>;<br>差异内容：function getP2pLinkedInfo(): Promise\<WifiP2pLinkedInfo>;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function getP2pLinkedInfo(callback: AsyncCallback\<WifiP2pLinkedInfo>): void;<br>差异内容：function getP2pLinkedInfo(callback: AsyncCallback\<WifiP2pLinkedInfo>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function getCurrentGroup(): Promise\<WifiP2pGroupInfo>;<br>差异内容：function getCurrentGroup(): Promise\<WifiP2pGroupInfo>;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function getCurrentGroup(callback: AsyncCallback\<WifiP2pGroupInfo>): void;<br>差异内容：function getCurrentGroup(callback: AsyncCallback\<WifiP2pGroupInfo>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function getP2pPeerDevices(): Promise\<WifiP2pDevice[]>;<br>差异内容：function getP2pPeerDevices(): Promise\<WifiP2pDevice[]>;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function getP2pPeerDevices(callback: AsyncCallback\<WifiP2pDevice[]>): void;<br>差异内容：function getP2pPeerDevices(callback: AsyncCallback\<WifiP2pDevice[]>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function createGroup(config: WifiP2PConfig): boolean;<br>差异内容：function createGroup(config: WifiP2PConfig): boolean;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function removeGroup(): boolean;<br>差异内容：function removeGroup(): boolean;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function p2pConnect(config: WifiP2PConfig): boolean;<br>差异内容：function p2pConnect(config: WifiP2PConfig): boolean;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function p2pCancelConnect(): boolean;<br>差异内容：function p2pCancelConnect(): boolean;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function startDiscoverDevices(): boolean;<br>差异内容：function startDiscoverDevices(): boolean;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function stopDiscoverDevices(): boolean;<br>差异内容：function stopDiscoverDevices(): boolean;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function on(type: 'wifiStateChange', callback: Callback\<number>): void;<br>差异内容：function on(type: 'wifiStateChange', callback: Callback\<number>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function off(type: 'wifiStateChange', callback?: Callback\<number>): void;<br>差异内容：function off(type: 'wifiStateChange', callback?: Callback\<number>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function on(type: 'wifiConnectionChange', callback: Callback\<number>): void;<br>差异内容：function on(type: 'wifiConnectionChange', callback: Callback\<number>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function off(type: 'wifiConnectionChange', callback?: Callback\<number>): void;<br>差异内容：function off(type: 'wifiConnectionChange', callback?: Callback\<number>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function on(type: 'wifiScanStateChange', callback: Callback\<number>): void;<br>差异内容：function on(type: 'wifiScanStateChange', callback: Callback\<number>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function off(type: 'wifiScanStateChange', callback?: Callback\<number>): void;<br>差异内容：function off(type: 'wifiScanStateChange', callback?: Callback\<number>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function on(type: 'wifiRssiChange', callback: Callback\<number>): void;<br>差异内容：function on(type: 'wifiRssiChange', callback: Callback\<number>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function off(type: 'wifiRssiChange', callback?: Callback\<number>): void;<br>差异内容：function off(type: 'wifiRssiChange', callback?: Callback\<number>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function on(type: 'hotspotStateChange', callback: Callback\<number>): void;<br>差异内容：function on(type: 'hotspotStateChange', callback: Callback\<number>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function off(type: 'hotspotStateChange', callback?: Callback\<number>): void;<br>差异内容：function off(type: 'hotspotStateChange', callback?: Callback\<number>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function on(type: 'p2pStateChange', callback: Callback\<number>): void;<br>差异内容：function on(type: 'p2pStateChange', callback: Callback\<number>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function off(type: 'p2pStateChange', callback?: Callback\<number>): void;<br>差异内容：function off(type: 'p2pStateChange', callback?: Callback\<number>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function on(type: 'p2pConnectionChange', callback: Callback\<WifiP2pLinkedInfo>): void;<br>差异内容：function on(type: 'p2pConnectionChange', callback: Callback\<WifiP2pLinkedInfo>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function off(type: 'p2pConnectionChange', callback?: Callback\<WifiP2pLinkedInfo>): void;<br>差异内容：function off(type: 'p2pConnectionChange', callback?: Callback\<WifiP2pLinkedInfo>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function on(type: 'p2pDeviceChange', callback: Callback\<WifiP2pDevice>): void;<br>差异内容：function on(type: 'p2pDeviceChange', callback: Callback\<WifiP2pDevice>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function off(type: 'p2pDeviceChange', callback?: Callback\<WifiP2pDevice>): void;<br>差异内容：function off(type: 'p2pDeviceChange', callback?: Callback\<WifiP2pDevice>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function on(type: 'p2pPeerDeviceChange', callback: Callback\<WifiP2pDevice[]>): void;<br>差异内容：function on(type: 'p2pPeerDeviceChange', callback: Callback\<WifiP2pDevice[]>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function off(type: 'p2pPeerDeviceChange', callback?: Callback\<WifiP2pDevice[]>): void;<br>差异内容：function off(type: 'p2pPeerDeviceChange', callback?: Callback\<WifiP2pDevice[]>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function on(type: 'p2pPersistentGroupChange', callback: Callback\<void>): void;<br>差异内容：function on(type: 'p2pPersistentGroupChange', callback: Callback\<void>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function off(type: 'p2pPersistentGroupChange', callback?: Callback\<void>): void;<br>差异内容：function off(type: 'p2pPersistentGroupChange', callback?: Callback\<void>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function on(type: 'p2pDiscoveryChange', callback: Callback\<number>): void;<br>差异内容：function on(type: 'p2pDiscoveryChange', callback: Callback\<number>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：function off(type: 'p2pDiscoveryChange', callback?: Callback\<number>): void;<br>差异内容：function off(type: 'p2pDiscoveryChange', callback?: Callback\<number>): void;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：interface WifiDeviceConfig<br>差异内容：interface WifiDeviceConfig|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiDeviceConfig；<br>API声明：ssid: string;<br>差异内容：ssid: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiDeviceConfig；<br>API声明：bssid: string;<br>差异内容：bssid: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiDeviceConfig；<br>API声明：preSharedKey: string;<br>差异内容：preSharedKey: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiDeviceConfig；<br>API声明：isHiddenSsid: boolean;<br>差异内容：isHiddenSsid: boolean;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiDeviceConfig；<br>API声明：securityType: WifiSecurityType;<br>差异内容：securityType: WifiSecurityType;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：interface WifiScanInfo<br>差异内容：interface WifiScanInfo|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：ssid: string;<br>差异内容：ssid: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：bssid: string;<br>差异内容：bssid: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：capabilities: string;<br>差异内容：capabilities: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：securityType: WifiSecurityType;<br>差异内容：securityType: WifiSecurityType;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：rssi: number;<br>差异内容：rssi: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：band: number;<br>差异内容：band: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：frequency: number;<br>差异内容：frequency: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：channelWidth: number;<br>差异内容：channelWidth: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：timestamp: number;<br>差异内容：timestamp: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：enum WifiSecurityType<br>差异内容：enum WifiSecurityType|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_INVALID = 0<br>差异内容：WIFI_SEC_TYPE_INVALID = 0|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_OPEN = 1<br>差异内容：WIFI_SEC_TYPE_OPEN = 1|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_WEP = 2<br>差异内容：WIFI_SEC_TYPE_WEP = 2|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_PSK = 3<br>差异内容：WIFI_SEC_TYPE_PSK = 3|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_SAE = 4<br>差异内容：WIFI_SEC_TYPE_SAE = 4|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：interface WifiLinkedInfo<br>差异内容：interface WifiLinkedInfo|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：ssid: string;<br>差异内容：ssid: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：bssid: string;<br>差异内容：bssid: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：rssi: number;<br>差异内容：rssi: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：band: number;<br>差异内容：band: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：linkSpeed: number;<br>差异内容：linkSpeed: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：frequency: number;<br>差异内容：frequency: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：isHidden: boolean;<br>差异内容：isHidden: boolean;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：isRestricted: boolean;<br>差异内容：isRestricted: boolean;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：macAddress: string;<br>差异内容：macAddress: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：ipAddress: number;<br>差异内容：ipAddress: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：connState: ConnState;<br>差异内容：connState: ConnState;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：interface IpInfo<br>差异内容：interface IpInfo|api/@ohos.wifi.d.ts|
|新增API|NA|类名：IpInfo；<br>API声明：ipAddress: number;<br>差异内容：ipAddress: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：IpInfo；<br>API声明：gateway: number;<br>差异内容：gateway: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：IpInfo；<br>API声明：netmask: number;<br>差异内容：netmask: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：IpInfo；<br>API声明：primaryDns: number;<br>差异内容：primaryDns: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：IpInfo；<br>API声明：secondDns: number;<br>差异内容：secondDns: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：IpInfo；<br>API声明：serverIp: number;<br>差异内容：serverIp: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：IpInfo；<br>API声明：leaseDuration: number;<br>差异内容：leaseDuration: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：export enum ConnState<br>差异内容：export enum ConnState|api/@ohos.wifi.d.ts|
|新增API|NA|类名：ConnState；<br>API声明：SCANNING<br>差异内容：SCANNING|api/@ohos.wifi.d.ts|
|新增API|NA|类名：ConnState；<br>API声明：CONNECTING<br>差异内容：CONNECTING|api/@ohos.wifi.d.ts|
|新增API|NA|类名：ConnState；<br>API声明：AUTHENTICATING<br>差异内容：AUTHENTICATING|api/@ohos.wifi.d.ts|
|新增API|NA|类名：ConnState；<br>API声明：OBTAINING_IPADDR<br>差异内容：OBTAINING_IPADDR|api/@ohos.wifi.d.ts|
|新增API|NA|类名：ConnState；<br>API声明：CONNECTED<br>差异内容：CONNECTED|api/@ohos.wifi.d.ts|
|新增API|NA|类名：ConnState；<br>API声明：DISCONNECTING<br>差异内容：DISCONNECTING|api/@ohos.wifi.d.ts|
|新增API|NA|类名：ConnState；<br>API声明：DISCONNECTED<br>差异内容：DISCONNECTED|api/@ohos.wifi.d.ts|
|新增API|NA|类名：ConnState；<br>API声明：UNKNOWN<br>差异内容：UNKNOWN|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：interface WifiP2pDevice<br>差异内容：interface WifiP2pDevice|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2pDevice；<br>API声明：deviceName: string;<br>差异内容：deviceName: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2pDevice；<br>API声明：deviceAddress: string;<br>差异内容：deviceAddress: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2pDevice；<br>API声明：primaryDeviceType: string;<br>差异内容：primaryDeviceType: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2pDevice；<br>API声明：deviceStatus: P2pDeviceStatus;<br>差异内容：deviceStatus: P2pDeviceStatus;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2pDevice；<br>API声明：groupCapabilitys: number;<br>差异内容：groupCapabilitys: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：interface WifiP2PConfig<br>差异内容：interface WifiP2PConfig|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2PConfig；<br>API声明：deviceAddress: string;<br>差异内容：deviceAddress: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2PConfig；<br>API声明：netId: number;<br>差异内容：netId: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2PConfig；<br>API声明：passphrase: string;<br>差异内容：passphrase: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2PConfig；<br>API声明：groupName: string;<br>差异内容：groupName: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2PConfig；<br>API声明：goBand: GroupOwnerBand;<br>差异内容：goBand: GroupOwnerBand;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：interface WifiP2pGroupInfo<br>差异内容：interface WifiP2pGroupInfo|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2pGroupInfo；<br>API声明：isP2pGo: boolean;<br>差异内容：isP2pGo: boolean;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2pGroupInfo；<br>API声明：ownerInfo: WifiP2pDevice;<br>差异内容：ownerInfo: WifiP2pDevice;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2pGroupInfo；<br>API声明：passphrase: string;<br>差异内容：passphrase: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2pGroupInfo；<br>API声明：interface: string;<br>差异内容：interface: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2pGroupInfo；<br>API声明：groupName: string;<br>差异内容：groupName: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2pGroupInfo；<br>API声明：networkId: number;<br>差异内容：networkId: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2pGroupInfo；<br>API声明：frequency: number;<br>差异内容：frequency: number;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2pGroupInfo；<br>API声明：clientDevices: WifiP2pDevice[];<br>差异内容：clientDevices: WifiP2pDevice[];|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2pGroupInfo；<br>API声明：goIpAddress: string;<br>差异内容：goIpAddress: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：enum P2pConnectState<br>差异内容：enum P2pConnectState|api/@ohos.wifi.d.ts|
|新增API|NA|类名：P2pConnectState；<br>API声明：DISCONNECTED = 0<br>差异内容：DISCONNECTED = 0|api/@ohos.wifi.d.ts|
|新增API|NA|类名：P2pConnectState；<br>API声明：CONNECTED = 1<br>差异内容：CONNECTED = 1|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：interface WifiP2pLinkedInfo<br>差异内容：interface WifiP2pLinkedInfo|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2pLinkedInfo；<br>API声明：connectState: P2pConnectState;<br>差异内容：connectState: P2pConnectState;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2pLinkedInfo；<br>API声明：isGroupOwner: boolean;<br>差异内容：isGroupOwner: boolean;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：WifiP2pLinkedInfo；<br>API声明：groupOwnerAddr: string;<br>差异内容：groupOwnerAddr: string;|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：enum P2pDeviceStatus<br>差异内容：enum P2pDeviceStatus|api/@ohos.wifi.d.ts|
|新增API|NA|类名：P2pDeviceStatus；<br>API声明：CONNECTED = 0<br>差异内容：CONNECTED = 0|api/@ohos.wifi.d.ts|
|新增API|NA|类名：P2pDeviceStatus；<br>API声明：INVITED = 1<br>差异内容：INVITED = 1|api/@ohos.wifi.d.ts|
|新增API|NA|类名：P2pDeviceStatus；<br>API声明：FAILED = 2<br>差异内容：FAILED = 2|api/@ohos.wifi.d.ts|
|新增API|NA|类名：P2pDeviceStatus；<br>API声明：AVAILABLE = 3<br>差异内容：AVAILABLE = 3|api/@ohos.wifi.d.ts|
|新增API|NA|类名：P2pDeviceStatus；<br>API声明：UNAVAILABLE = 4<br>差异内容：UNAVAILABLE = 4|api/@ohos.wifi.d.ts|
|新增API|NA|类名：wifi；<br>API声明：enum GroupOwnerBand<br>差异内容：enum GroupOwnerBand|api/@ohos.wifi.d.ts|
|新增API|NA|类名：GroupOwnerBand；<br>API声明：GO_BAND_AUTO = 0<br>差异内容：GO_BAND_AUTO = 0|api/@ohos.wifi.d.ts|
|新增API|NA|类名：GroupOwnerBand；<br>API声明：GO_BAND_2GHZ = 1<br>差异内容：GO_BAND_2GHZ = 1|api/@ohos.wifi.d.ts|
|新增API|NA|类名：GroupOwnerBand；<br>API声明：GO_BAND_5GHZ = 2<br>差异内容：GO_BAND_5GHZ = 2|api/@ohos.wifi.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace wifiext<br>差异内容：declare namespace wifiext|api/@ohos.wifiext.d.ts|
|新增API|NA|类名：wifiext；<br>API声明：function enableHotspot(): boolean;<br>差异内容：function enableHotspot(): boolean;|api/@ohos.wifiext.d.ts|
|新增API|NA|类名：wifiext；<br>API声明：function disableHotspot(): boolean;<br>差异内容：function disableHotspot(): boolean;|api/@ohos.wifiext.d.ts|
|新增API|NA|类名：wifiext；<br>API声明：function getSupportedPowerModel(): Promise\<Array\<PowerModel>>;<br>差异内容：function getSupportedPowerModel(): Promise\<Array\<PowerModel>>;|api/@ohos.wifiext.d.ts|
|新增API|NA|类名：wifiext；<br>API声明：function getSupportedPowerModel(callback: AsyncCallback\<Array\<PowerModel>>): void;<br>差异内容：function getSupportedPowerModel(callback: AsyncCallback\<Array\<PowerModel>>): void;|api/@ohos.wifiext.d.ts|
|新增API|NA|类名：wifiext；<br>API声明：function getPowerModel(): Promise\<PowerModel>;<br>差异内容：function getPowerModel(): Promise\<PowerModel>;|api/@ohos.wifiext.d.ts|
|新增API|NA|类名：wifiext；<br>API声明：function getPowerModel(callback: AsyncCallback\<PowerModel>): void;<br>差异内容：function getPowerModel(callback: AsyncCallback\<PowerModel>): void;|api/@ohos.wifiext.d.ts|
|新增API|NA|类名：wifiext；<br>API声明：function setPowerModel(model: PowerModel): boolean;<br>差异内容：function setPowerModel(model: PowerModel): boolean;|api/@ohos.wifiext.d.ts|
|新增API|NA|类名：wifiext；<br>API声明：export enum PowerModel<br>差异内容：export enum PowerModel|api/@ohos.wifiext.d.ts|
|新增API|NA|类名：PowerModel；<br>API声明：SLEEPING = 0<br>差异内容：SLEEPING = 0|api/@ohos.wifiext.d.ts|
|新增API|NA|类名：PowerModel；<br>API声明：GENERAL = 1<br>差异内容：GENERAL = 1|api/@ohos.wifiext.d.ts|
|新增API|NA|类名：PowerModel；<br>API声明：THROUGH_WALL = 2<br>差异内容：THROUGH_WALL = 2|api/@ohos.wifiext.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace wifiManager<br>差异内容：declare namespace wifiManager|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function isWifiActive(): boolean;<br>差异内容：function isWifiActive(): boolean;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function scan(): void;<br>差异内容：function scan(): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getScanResults(): Promise\<Array\<WifiScanInfo>>;<br>差异内容：function getScanResults(): Promise\<Array\<WifiScanInfo>>;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getScanResults(callback: AsyncCallback\<Array\<WifiScanInfo>>): void;<br>差异内容：function getScanResults(callback: AsyncCallback\<Array\<WifiScanInfo>>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getScanResultsSync(): Array\<WifiScanInfo>;<br>差异内容：function getScanResultsSync(): Array\<WifiScanInfo>;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getScanInfoList(): Array\<WifiScanInfo>;<br>差异内容：function getScanInfoList(): Array\<WifiScanInfo>;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function addCandidateConfig(config: WifiDeviceConfig): Promise\<number>;<br>差异内容：function addCandidateConfig(config: WifiDeviceConfig): Promise\<number>;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function addCandidateConfig(config: WifiDeviceConfig, callback: AsyncCallback\<number>): void;<br>差异内容：function addCandidateConfig(config: WifiDeviceConfig, callback: AsyncCallback\<number>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function removeCandidateConfig(networkId: number): Promise\<void>;<br>差异内容：function removeCandidateConfig(networkId: number): Promise\<void>;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function removeCandidateConfig(networkId: number, callback: AsyncCallback\<void>): void;<br>差异内容：function removeCandidateConfig(networkId: number, callback: AsyncCallback\<void>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getCandidateConfigs(): Array\<WifiDeviceConfig>;<br>差异内容：function getCandidateConfigs(): Array\<WifiDeviceConfig>;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function connectToCandidateConfig(networkId: number): void;<br>差异内容：function connectToCandidateConfig(networkId: number): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getSignalLevel(rssi: number, band: number): number;<br>差异内容：function getSignalLevel(rssi: number, band: number): number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getLinkedInfo(): Promise\<WifiLinkedInfo>;<br>差异内容：function getLinkedInfo(): Promise\<WifiLinkedInfo>;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getLinkedInfo(callback: AsyncCallback\<WifiLinkedInfo>): void;<br>差异内容：function getLinkedInfo(callback: AsyncCallback\<WifiLinkedInfo>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function isConnected(): boolean;<br>差异内容：function isConnected(): boolean;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function isFeatureSupported(featureId: number): boolean;<br>差异内容：function isFeatureSupported(featureId: number): boolean;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getIpInfo(): IpInfo;<br>差异内容：function getIpInfo(): IpInfo;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getIpv6Info(): Ipv6Info;<br>差异内容：function getIpv6Info(): Ipv6Info;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getCountryCode(): string;<br>差异内容：function getCountryCode(): string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function isBandTypeSupported(bandType: WifiBandType): boolean;<br>差异内容：function isBandTypeSupported(bandType: WifiBandType): boolean;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function isMeteredHotspot(): boolean;<br>差异内容：function isMeteredHotspot(): boolean;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getP2pLinkedInfo(): Promise\<WifiP2pLinkedInfo>;<br>差异内容：function getP2pLinkedInfo(): Promise\<WifiP2pLinkedInfo>;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getP2pLinkedInfo(callback: AsyncCallback\<WifiP2pLinkedInfo>): void;<br>差异内容：function getP2pLinkedInfo(callback: AsyncCallback\<WifiP2pLinkedInfo>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getCurrentGroup(): Promise\<WifiP2pGroupInfo>;<br>差异内容：function getCurrentGroup(): Promise\<WifiP2pGroupInfo>;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getCurrentGroup(callback: AsyncCallback\<WifiP2pGroupInfo>): void;<br>差异内容：function getCurrentGroup(callback: AsyncCallback\<WifiP2pGroupInfo>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getP2pPeerDevices(): Promise\<WifiP2pDevice[]>;<br>差异内容：function getP2pPeerDevices(): Promise\<WifiP2pDevice[]>;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getP2pPeerDevices(callback: AsyncCallback\<WifiP2pDevice[]>): void;<br>差异内容：function getP2pPeerDevices(callback: AsyncCallback\<WifiP2pDevice[]>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getP2pLocalDevice(): Promise\<WifiP2pDevice>;<br>差异内容：function getP2pLocalDevice(): Promise\<WifiP2pDevice>;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getP2pLocalDevice(callback: AsyncCallback\<WifiP2pDevice>): void;<br>差异内容：function getP2pLocalDevice(callback: AsyncCallback\<WifiP2pDevice>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function createGroup(config: WifiP2PConfig): void;<br>差异内容：function createGroup(config: WifiP2PConfig): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function removeGroup(): void;<br>差异内容：function removeGroup(): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function p2pConnect(config: WifiP2PConfig): void;<br>差异内容：function p2pConnect(config: WifiP2PConfig): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function p2pCancelConnect(): void;<br>差异内容：function p2pCancelConnect(): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function startDiscoverDevices(): void;<br>差异内容：function startDiscoverDevices(): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function stopDiscoverDevices(): void;<br>差异内容：function stopDiscoverDevices(): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function on(type: 'wifiStateChange', callback: Callback\<number>): void;<br>差异内容：function on(type: 'wifiStateChange', callback: Callback\<number>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function off(type: 'wifiStateChange', callback?: Callback\<number>): void;<br>差异内容：function off(type: 'wifiStateChange', callback?: Callback\<number>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function on(type: 'wifiConnectionChange', callback: Callback\<number>): void;<br>差异内容：function on(type: 'wifiConnectionChange', callback: Callback\<number>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function off(type: 'wifiConnectionChange', callback?: Callback\<number>): void;<br>差异内容：function off(type: 'wifiConnectionChange', callback?: Callback\<number>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function on(type: 'wifiScanStateChange', callback: Callback\<number>): void;<br>差异内容：function on(type: 'wifiScanStateChange', callback: Callback\<number>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function off(type: 'wifiScanStateChange', callback?: Callback\<number>): void;<br>差异内容：function off(type: 'wifiScanStateChange', callback?: Callback\<number>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function on(type: 'wifiRssiChange', callback: Callback\<number>): void;<br>差异内容：function on(type: 'wifiRssiChange', callback: Callback\<number>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function off(type: 'wifiRssiChange', callback?: Callback\<number>): void;<br>差异内容：function off(type: 'wifiRssiChange', callback?: Callback\<number>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function on(type: 'hotspotStateChange', callback: Callback\<number>): void;<br>差异内容：function on(type: 'hotspotStateChange', callback: Callback\<number>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function off(type: 'hotspotStateChange', callback?: Callback\<number>): void;<br>差异内容：function off(type: 'hotspotStateChange', callback?: Callback\<number>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function on(type: 'p2pStateChange', callback: Callback\<number>): void;<br>差异内容：function on(type: 'p2pStateChange', callback: Callback\<number>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function off(type: 'p2pStateChange', callback?: Callback\<number>): void;<br>差异内容：function off(type: 'p2pStateChange', callback?: Callback\<number>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function on(type: 'p2pConnectionChange', callback: Callback\<WifiP2pLinkedInfo>): void;<br>差异内容：function on(type: 'p2pConnectionChange', callback: Callback\<WifiP2pLinkedInfo>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function off(type: 'p2pConnectionChange', callback?: Callback\<WifiP2pLinkedInfo>): void;<br>差异内容：function off(type: 'p2pConnectionChange', callback?: Callback\<WifiP2pLinkedInfo>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function on(type: 'p2pDeviceChange', callback: Callback\<WifiP2pDevice>): void;<br>差异内容：function on(type: 'p2pDeviceChange', callback: Callback\<WifiP2pDevice>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function off(type: 'p2pDeviceChange', callback?: Callback\<WifiP2pDevice>): void;<br>差异内容：function off(type: 'p2pDeviceChange', callback?: Callback\<WifiP2pDevice>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function on(type: 'p2pPeerDeviceChange', callback: Callback\<WifiP2pDevice[]>): void;<br>差异内容：function on(type: 'p2pPeerDeviceChange', callback: Callback\<WifiP2pDevice[]>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function off(type: 'p2pPeerDeviceChange', callback?: Callback\<WifiP2pDevice[]>): void;<br>差异内容：function off(type: 'p2pPeerDeviceChange', callback?: Callback\<WifiP2pDevice[]>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function on(type: 'p2pPersistentGroupChange', callback: Callback\<void>): void;<br>差异内容：function on(type: 'p2pPersistentGroupChange', callback: Callback\<void>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function off(type: 'p2pPersistentGroupChange', callback?: Callback\<void>): void;<br>差异内容：function off(type: 'p2pPersistentGroupChange', callback?: Callback\<void>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function on(type: 'p2pDiscoveryChange', callback: Callback\<number>): void;<br>差异内容：function on(type: 'p2pDiscoveryChange', callback: Callback\<number>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function off(type: 'p2pDiscoveryChange', callback?: Callback\<number>): void;<br>差异内容：function off(type: 'p2pDiscoveryChange', callback?: Callback\<number>): void;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：enum DeviceAddressType<br>差异内容：enum DeviceAddressType|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：DeviceAddressType；<br>API声明：RANDOM_DEVICE_ADDRESS<br>差异内容：RANDOM_DEVICE_ADDRESS|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：DeviceAddressType；<br>API声明：REAL_DEVICE_ADDRESS<br>差异内容：REAL_DEVICE_ADDRESS|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：enum EapMethod<br>差异内容：enum EapMethod|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_NONE<br>差异内容：EAP_NONE|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_PEAP<br>差异内容：EAP_PEAP|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_TLS<br>差异内容：EAP_TLS|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_TTLS<br>差异内容：EAP_TTLS|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_PWD<br>差异内容：EAP_PWD|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_SIM<br>差异内容：EAP_SIM|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_AKA<br>差异内容：EAP_AKA|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_AKA_PRIME<br>差异内容：EAP_AKA_PRIME|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_UNAUTH_TLS<br>差异内容：EAP_UNAUTH_TLS|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：enum Phase2Method<br>差异内容：enum Phase2Method|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_NONE<br>差异内容：PHASE2_NONE|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_PAP<br>差异内容：PHASE2_PAP|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_MSCHAP<br>差异内容：PHASE2_MSCHAP|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_MSCHAPV2<br>差异内容：PHASE2_MSCHAPV2|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_GTC<br>差异内容：PHASE2_GTC|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_SIM<br>差异内容：PHASE2_SIM|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_AKA<br>差异内容：PHASE2_AKA|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_AKA_PRIME<br>差异内容：PHASE2_AKA_PRIME|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：interface WifiEapConfig<br>差异内容：interface WifiEapConfig|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiEapConfig；<br>API声明：eapMethod: EapMethod;<br>差异内容：eapMethod: EapMethod;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiEapConfig；<br>API声明：phase2Method: Phase2Method;<br>差异内容：phase2Method: Phase2Method;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiEapConfig；<br>API声明：identity: string;<br>差异内容：identity: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiEapConfig；<br>API声明：anonymousIdentity: string;<br>差异内容：anonymousIdentity: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiEapConfig；<br>API声明：password: string;<br>差异内容：password: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiEapConfig；<br>API声明：caCertAlias: string;<br>差异内容：caCertAlias: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiEapConfig；<br>API声明：caPath: string;<br>差异内容：caPath: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiEapConfig；<br>API声明：clientCertAlias: string;<br>差异内容：clientCertAlias: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiEapConfig；<br>API声明：certEntry: Uint8Array;<br>差异内容：certEntry: Uint8Array;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiEapConfig；<br>API声明：certPassword: string;<br>差异内容：certPassword: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiEapConfig；<br>API声明：altSubjectMatch: string;<br>差异内容：altSubjectMatch: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiEapConfig；<br>API声明：domainSuffixMatch: string;<br>差异内容：domainSuffixMatch: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiEapConfig；<br>API声明：realm: string;<br>差异内容：realm: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiEapConfig；<br>API声明：plmn: string;<br>差异内容：plmn: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiEapConfig；<br>API声明：eapSubId: number;<br>差异内容：eapSubId: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：interface WifiDeviceConfig<br>差异内容：interface WifiDeviceConfig|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiDeviceConfig；<br>API声明：ssid: string;<br>差异内容：ssid: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiDeviceConfig；<br>API声明：bssid?: string;<br>差异内容：bssid?: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiDeviceConfig；<br>API声明：bssidType?: DeviceAddressType;<br>差异内容：bssidType?: DeviceAddressType;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiDeviceConfig；<br>API声明：preSharedKey: string;<br>差异内容：preSharedKey: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiDeviceConfig；<br>API声明：isHiddenSsid?: boolean;<br>差异内容：isHiddenSsid?: boolean;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiDeviceConfig；<br>API声明：securityType: WifiSecurityType;<br>差异内容：securityType: WifiSecurityType;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiDeviceConfig；<br>API声明：eapConfig?: WifiEapConfig;<br>差异内容：eapConfig?: WifiEapConfig;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：interface WifiInfoElem<br>差异内容：interface WifiInfoElem|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiInfoElem；<br>API声明：eid: number;<br>差异内容：eid: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiInfoElem；<br>API声明：content: Uint8Array;<br>差异内容：content: Uint8Array;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：enum WifiChannelWidth<br>差异内容：enum WifiChannelWidth|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiChannelWidth；<br>API声明：WIDTH_20MHZ = 0<br>差异内容：WIDTH_20MHZ = 0|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiChannelWidth；<br>API声明：WIDTH_40MHZ = 1<br>差异内容：WIDTH_40MHZ = 1|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiChannelWidth；<br>API声明：WIDTH_80MHZ = 2<br>差异内容：WIDTH_80MHZ = 2|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiChannelWidth；<br>API声明：WIDTH_160MHZ = 3<br>差异内容：WIDTH_160MHZ = 3|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiChannelWidth；<br>API声明：WIDTH_80MHZ_PLUS = 4<br>差异内容：WIDTH_80MHZ_PLUS = 4|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiChannelWidth；<br>API声明：WIDTH_INVALID<br>差异内容：WIDTH_INVALID|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：interface WifiScanInfo<br>差异内容：interface WifiScanInfo|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：ssid: string;<br>差异内容：ssid: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：bssid: string;<br>差异内容：bssid: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：bssidType: DeviceAddressType;<br>差异内容：bssidType: DeviceAddressType;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：capabilities: string;<br>差异内容：capabilities: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：securityType: WifiSecurityType;<br>差异内容：securityType: WifiSecurityType;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：rssi: number;<br>差异内容：rssi: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：band: number;<br>差异内容：band: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：frequency: number;<br>差异内容：frequency: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：channelWidth: number;<br>差异内容：channelWidth: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：centerFrequency0: number;<br>差异内容：centerFrequency0: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：centerFrequency1: number;<br>差异内容：centerFrequency1: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：infoElems: Array\<WifiInfoElem>;<br>差异内容：infoElems: Array\<WifiInfoElem>;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiScanInfo；<br>API声明：timestamp: number;<br>差异内容：timestamp: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：enum WifiSecurityType<br>差异内容：enum WifiSecurityType|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_INVALID = 0<br>差异内容：WIFI_SEC_TYPE_INVALID = 0|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_OPEN = 1<br>差异内容：WIFI_SEC_TYPE_OPEN = 1|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_WEP = 2<br>差异内容：WIFI_SEC_TYPE_WEP = 2|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_PSK = 3<br>差异内容：WIFI_SEC_TYPE_PSK = 3|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_SAE = 4<br>差异内容：WIFI_SEC_TYPE_SAE = 4|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_EAP = 5<br>差异内容：WIFI_SEC_TYPE_EAP = 5|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_EAP_SUITE_B = 6<br>差异内容：WIFI_SEC_TYPE_EAP_SUITE_B = 6|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_OWE = 7<br>差异内容：WIFI_SEC_TYPE_OWE = 7|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_WAPI_CERT = 8<br>差异内容：WIFI_SEC_TYPE_WAPI_CERT = 8|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_WAPI_PSK = 9<br>差异内容：WIFI_SEC_TYPE_WAPI_PSK = 9|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：enum WifiBandType<br>差异内容：enum WifiBandType|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiBandType；<br>API声明：WIFI_BAND_NONE<br>差异内容：WIFI_BAND_NONE|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiBandType；<br>API声明：WIFI_BAND_2G<br>差异内容：WIFI_BAND_2G|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiBandType；<br>API声明：WIFI_BAND_5G<br>差异内容：WIFI_BAND_5G|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiBandType；<br>API声明：WIFI_BAND_6G<br>差异内容：WIFI_BAND_6G|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiBandType；<br>API声明：WIFI_BAND_60G<br>差异内容：WIFI_BAND_60G|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：enum WifiStandard<br>差异内容：enum WifiStandard|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiStandard；<br>API声明：WIFI_STANDARD_UNDEFINED<br>差异内容：WIFI_STANDARD_UNDEFINED|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiStandard；<br>API声明：WIFI_STANDARD_11A<br>差异内容：WIFI_STANDARD_11A|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiStandard；<br>API声明：WIFI_STANDARD_11B<br>差异内容：WIFI_STANDARD_11B|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiStandard；<br>API声明：WIFI_STANDARD_11G<br>差异内容：WIFI_STANDARD_11G|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiStandard；<br>API声明：WIFI_STANDARD_11N<br>差异内容：WIFI_STANDARD_11N|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiStandard；<br>API声明：WIFI_STANDARD_11AC<br>差异内容：WIFI_STANDARD_11AC|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiStandard；<br>API声明：WIFI_STANDARD_11AX<br>差异内容：WIFI_STANDARD_11AX|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiStandard；<br>API声明：WIFI_STANDARD_11AD<br>差异内容：WIFI_STANDARD_11AD|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：interface WifiLinkedInfo<br>差异内容：interface WifiLinkedInfo|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：ssid: string;<br>差异内容：ssid: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：bssid: string;<br>差异内容：bssid: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：rssi: number;<br>差异内容：rssi: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：band: number;<br>差异内容：band: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：linkSpeed: number;<br>差异内容：linkSpeed: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：rxLinkSpeed: number;<br>差异内容：rxLinkSpeed: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：maxSupportedTxLinkSpeed: number;<br>差异内容：maxSupportedTxLinkSpeed: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：maxSupportedRxLinkSpeed: number;<br>差异内容：maxSupportedRxLinkSpeed: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：frequency: number;<br>差异内容：frequency: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：isHidden: boolean;<br>差异内容：isHidden: boolean;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：isRestricted: boolean;<br>差异内容：isRestricted: boolean;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：macType: number;<br>差异内容：macType: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：macAddress: string;<br>差异内容：macAddress: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：ipAddress: number;<br>差异内容：ipAddress: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：connState: ConnState;<br>差异内容：connState: ConnState;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：channelWidth: WifiChannelWidth;<br>差异内容：channelWidth: WifiChannelWidth;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiLinkedInfo；<br>API声明：wifiStandard: WifiStandard;<br>差异内容：wifiStandard: WifiStandard;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：interface IpInfo<br>差异内容：interface IpInfo|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：IpInfo；<br>API声明：ipAddress: number;<br>差异内容：ipAddress: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：IpInfo；<br>API声明：gateway: number;<br>差异内容：gateway: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：IpInfo；<br>API声明：netmask: number;<br>差异内容：netmask: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：IpInfo；<br>API声明：primaryDns: number;<br>差异内容：primaryDns: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：IpInfo；<br>API声明：secondDns: number;<br>差异内容：secondDns: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：IpInfo；<br>API声明：serverIp: number;<br>差异内容：serverIp: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：IpInfo；<br>API声明：leaseDuration: number;<br>差异内容：leaseDuration: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：interface Ipv6Info<br>差异内容：interface Ipv6Info|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：Ipv6Info；<br>API声明：linkIpv6Address: string;<br>差异内容：linkIpv6Address: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：Ipv6Info；<br>API声明：globalIpv6Address: string;<br>差异内容：globalIpv6Address: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：Ipv6Info；<br>API声明：randomGlobalIpv6Address: string;<br>差异内容：randomGlobalIpv6Address: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：Ipv6Info；<br>API声明：gateway: string;<br>差异内容：gateway: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：Ipv6Info；<br>API声明：netmask: string;<br>差异内容：netmask: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：Ipv6Info；<br>API声明：primaryDNS: string;<br>差异内容：primaryDNS: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：Ipv6Info；<br>API声明：secondDNS: string;<br>差异内容：secondDNS: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：export enum ConnState<br>差异内容：export enum ConnState|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：ConnState；<br>API声明：SCANNING<br>差异内容：SCANNING|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：ConnState；<br>API声明：CONNECTING<br>差异内容：CONNECTING|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：ConnState；<br>API声明：AUTHENTICATING<br>差异内容：AUTHENTICATING|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：ConnState；<br>API声明：OBTAINING_IPADDR<br>差异内容：OBTAINING_IPADDR|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：ConnState；<br>API声明：CONNECTED<br>差异内容：CONNECTED|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：ConnState；<br>API声明：DISCONNECTING<br>差异内容：DISCONNECTING|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：ConnState；<br>API声明：DISCONNECTED<br>差异内容：DISCONNECTED|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：ConnState；<br>API声明：UNKNOWN<br>差异内容：UNKNOWN|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：interface WifiP2pDevice<br>差异内容：interface WifiP2pDevice|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2pDevice；<br>API声明：deviceName: string;<br>差异内容：deviceName: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2pDevice；<br>API声明：deviceAddress: string;<br>差异内容：deviceAddress: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2pDevice；<br>API声明：deviceAddressType?: DeviceAddressType;<br>差异内容：deviceAddressType?: DeviceAddressType;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2pDevice；<br>API声明：primaryDeviceType: string;<br>差异内容：primaryDeviceType: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2pDevice；<br>API声明：deviceStatus: P2pDeviceStatus;<br>差异内容：deviceStatus: P2pDeviceStatus;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2pDevice；<br>API声明：groupCapabilities: number;<br>差异内容：groupCapabilities: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：interface WifiP2PConfig<br>差异内容：interface WifiP2PConfig|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2PConfig；<br>API声明：deviceAddress: string;<br>差异内容：deviceAddress: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2PConfig；<br>API声明：deviceAddressType?: DeviceAddressType;<br>差异内容：deviceAddressType?: DeviceAddressType;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2PConfig；<br>API声明：netId: number;<br>差异内容：netId: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2PConfig；<br>API声明：passphrase: string;<br>差异内容：passphrase: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2PConfig；<br>API声明：groupName: string;<br>差异内容：groupName: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2PConfig；<br>API声明：goBand: GroupOwnerBand;<br>差异内容：goBand: GroupOwnerBand;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：interface WifiP2pGroupInfo<br>差异内容：interface WifiP2pGroupInfo|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2pGroupInfo；<br>API声明：isP2pGo: boolean;<br>差异内容：isP2pGo: boolean;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2pGroupInfo；<br>API声明：ownerInfo: WifiP2pDevice;<br>差异内容：ownerInfo: WifiP2pDevice;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2pGroupInfo；<br>API声明：passphrase: string;<br>差异内容：passphrase: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2pGroupInfo；<br>API声明：interface: string;<br>差异内容：interface: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2pGroupInfo；<br>API声明：groupName: string;<br>差异内容：groupName: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2pGroupInfo；<br>API声明：networkId: number;<br>差异内容：networkId: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2pGroupInfo；<br>API声明：frequency: number;<br>差异内容：frequency: number;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2pGroupInfo；<br>API声明：clientDevices: WifiP2pDevice[];<br>差异内容：clientDevices: WifiP2pDevice[];|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2pGroupInfo；<br>API声明：goIpAddress: string;<br>差异内容：goIpAddress: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：enum P2pConnectState<br>差异内容：enum P2pConnectState|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：P2pConnectState；<br>API声明：DISCONNECTED = 0<br>差异内容：DISCONNECTED = 0|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：P2pConnectState；<br>API声明：CONNECTED = 1<br>差异内容：CONNECTED = 1|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：interface WifiP2pLinkedInfo<br>差异内容：interface WifiP2pLinkedInfo|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2pLinkedInfo；<br>API声明：connectState: P2pConnectState;<br>差异内容：connectState: P2pConnectState;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2pLinkedInfo；<br>API声明：isGroupOwner: boolean;<br>差异内容：isGroupOwner: boolean;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：WifiP2pLinkedInfo；<br>API声明：groupOwnerAddr: string;<br>差异内容：groupOwnerAddr: string;|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：enum P2pDeviceStatus<br>差异内容：enum P2pDeviceStatus|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：P2pDeviceStatus；<br>API声明：CONNECTED = 0<br>差异内容：CONNECTED = 0|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：P2pDeviceStatus；<br>API声明：INVITED = 1<br>差异内容：INVITED = 1|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：P2pDeviceStatus；<br>API声明：FAILED = 2<br>差异内容：FAILED = 2|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：P2pDeviceStatus；<br>API声明：AVAILABLE = 3<br>差异内容：AVAILABLE = 3|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：P2pDeviceStatus；<br>API声明：UNAVAILABLE = 4<br>差异内容：UNAVAILABLE = 4|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：enum GroupOwnerBand<br>差异内容：enum GroupOwnerBand|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：GroupOwnerBand；<br>API声明：GO_BAND_AUTO = 0<br>差异内容：GO_BAND_AUTO = 0|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：GroupOwnerBand；<br>API声明：GO_BAND_2GHZ = 1<br>差异内容：GO_BAND_2GHZ = 1|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：GroupOwnerBand；<br>API声明：GO_BAND_5GHZ = 2<br>差异内容：GO_BAND_5GHZ = 2|api/@ohos.wifiManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace wifiManagerExt<br>差异内容：declare namespace wifiManagerExt|api/@ohos.wifiManagerExt.d.ts|
|新增API|NA|类名：wifiManagerExt；<br>API声明：function enableHotspot(): void;<br>差异内容：function enableHotspot(): void;|api/@ohos.wifiManagerExt.d.ts|
|新增API|NA|类名：wifiManagerExt；<br>API声明：function disableHotspot(): void;<br>差异内容：function disableHotspot(): void;|api/@ohos.wifiManagerExt.d.ts|
|新增API|NA|类名：wifiManagerExt；<br>API声明：function getSupportedPowerMode(): Promise\<Array\<PowerMode>>;<br>差异内容：function getSupportedPowerMode(): Promise\<Array\<PowerMode>>;|api/@ohos.wifiManagerExt.d.ts|
|新增API|NA|类名：wifiManagerExt；<br>API声明：function getSupportedPowerMode(callback: AsyncCallback\<Array\<PowerMode>>): void;<br>差异内容：function getSupportedPowerMode(callback: AsyncCallback\<Array\<PowerMode>>): void;|api/@ohos.wifiManagerExt.d.ts|
|新增API|NA|类名：wifiManagerExt；<br>API声明：function getPowerMode(): Promise\<PowerMode>;<br>差异内容：function getPowerMode(): Promise\<PowerMode>;|api/@ohos.wifiManagerExt.d.ts|
|新增API|NA|类名：wifiManagerExt；<br>API声明：function getPowerMode(callback: AsyncCallback\<PowerMode>): void;<br>差异内容：function getPowerMode(callback: AsyncCallback\<PowerMode>): void;|api/@ohos.wifiManagerExt.d.ts|
|新增API|NA|类名：wifiManagerExt；<br>API声明：function setPowerMode(mode: PowerMode): void;<br>差异内容：function setPowerMode(mode: PowerMode): void;|api/@ohos.wifiManagerExt.d.ts|
|新增API|NA|类名：wifiManagerExt；<br>API声明：export enum PowerMode<br>差异内容：export enum PowerMode|api/@ohos.wifiManagerExt.d.ts|
|新增API|NA|类名：PowerMode；<br>API声明：SLEEPING = 0<br>差异内容：SLEEPING = 0|api/@ohos.wifiManagerExt.d.ts|
|新增API|NA|类名：PowerMode；<br>API声明：GENERAL = 1<br>差异内容：GENERAL = 1|api/@ohos.wifiManagerExt.d.ts|
|新增API|NA|类名：PowerMode；<br>API声明：THROUGH_WALL = 2<br>差异内容：THROUGH_WALL = 2|api/@ohos.wifiManagerExt.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface StartBLEScanOptions<br>差异内容：export interface StartBLEScanOptions|api/@system.bluetooth.d.ts|
|新增API|NA|类名：StartBLEScanOptions；<br>API声明：interval: number;<br>差异内容：interval: number;|api/@system.bluetooth.d.ts|
|新增API|NA|类名：StartBLEScanOptions；<br>API声明：success: () => void;<br>差异内容：success: () => void;|api/@system.bluetooth.d.ts|
|新增API|NA|类名：StartBLEScanOptions；<br>API声明：fail: (data: string, code: number) => void;<br>差异内容：fail: (data: string, code: number) => void;|api/@system.bluetooth.d.ts|
|新增API|NA|类名：StartBLEScanOptions；<br>API声明：complete: () => void;<br>差异内容：complete: () => void;|api/@system.bluetooth.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface StopBLEScanOptions<br>差异内容：export interface StopBLEScanOptions|api/@system.bluetooth.d.ts|
|新增API|NA|类名：StopBLEScanOptions；<br>API声明：success: () => void;<br>差异内容：success: () => void;|api/@system.bluetooth.d.ts|
|新增API|NA|类名：StopBLEScanOptions；<br>API声明：fail: (data: string, code: number) => void;<br>差异内容：fail: (data: string, code: number) => void;|api/@system.bluetooth.d.ts|
|新增API|NA|类名：StopBLEScanOptions；<br>API声明：complete: () => void;<br>差异内容：complete: () => void;|api/@system.bluetooth.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface BluetoothDevice<br>差异内容：export interface BluetoothDevice|api/@system.bluetooth.d.ts|
|新增API|NA|类名：BluetoothDevice；<br>API声明：addrType: 'public' \| 'random';<br>差异内容：addrType: 'public' \| 'random';|api/@system.bluetooth.d.ts|
|新增API|NA|类名：BluetoothDevice；<br>API声明：addr: string;<br>差异内容：addr: string;|api/@system.bluetooth.d.ts|
|新增API|NA|类名：BluetoothDevice；<br>API声明：rssi: number;<br>差异内容：rssi: number;|api/@system.bluetooth.d.ts|
|新增API|NA|类名：BluetoothDevice；<br>API声明：txpower: string;<br>差异内容：txpower: string;|api/@system.bluetooth.d.ts|
|新增API|NA|类名：BluetoothDevice；<br>API声明：data: string;<br>差异内容：data: string;|api/@system.bluetooth.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface BLEFoundResponse<br>差异内容：export interface BLEFoundResponse|api/@system.bluetooth.d.ts|
|新增API|NA|类名：BLEFoundResponse；<br>API声明：devices: Array\<BluetoothDevice>;<br>差异内容：devices: Array\<BluetoothDevice>;|api/@system.bluetooth.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SubscribeBLEFoundOptions<br>差异内容：export interface SubscribeBLEFoundOptions|api/@system.bluetooth.d.ts|
|新增API|NA|类名：SubscribeBLEFoundOptions；<br>API声明：success: (data: BLEFoundResponse) => void;<br>差异内容：success: (data: BLEFoundResponse) => void;|api/@system.bluetooth.d.ts|
|新增API|NA|类名：SubscribeBLEFoundOptions；<br>API声明：fail: (data: string, code: number) => void;<br>差异内容：fail: (data: string, code: number) => void;|api/@system.bluetooth.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class Bluetooth<br>差异内容：export default class Bluetooth|api/@system.bluetooth.d.ts|
|新增API|NA|类名：Bluetooth；<br>API声明：static startBLEScan(options: StartBLEScanOptions): void;<br>差异内容：static startBLEScan(options: StartBLEScanOptions): void;|api/@system.bluetooth.d.ts|
|新增API|NA|类名：Bluetooth；<br>API声明：static stopBLEScan(options: StopBLEScanOptions): void;<br>差异内容：static stopBLEScan(options: StopBLEScanOptions): void;|api/@system.bluetooth.d.ts|
|新增API|NA|类名：Bluetooth；<br>API声明：static subscribeBLEFound(options: SubscribeBLEFoundOptions): void;<br>差异内容：static subscribeBLEFound(options: SubscribeBLEFoundOptions): void;|api/@system.bluetooth.d.ts|
|新增API|NA|类名：Bluetooth；<br>API声明：static unsubscribeBLEFound(): void;<br>差异内容：static unsubscribeBLEFound(): void;|api/@system.bluetooth.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bluetooth.a2dp.d.ts<br>差异内容：ConnectivityKit|api/@ohos.bluetooth.a2dp.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bluetooth.access.d.ts<br>差异内容：ConnectivityKit|api/@ohos.bluetooth.access.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bluetooth.baseProfile.d.ts<br>差异内容：ConnectivityKit|api/@ohos.bluetooth.baseProfile.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bluetooth.ble.d.ts<br>差异内容：ConnectivityKit|api/@ohos.bluetooth.ble.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bluetooth.connection.d.ts<br>差异内容：ConnectivityKit|api/@ohos.bluetooth.connection.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bluetooth.constant.d.ts<br>差异内容：ConnectivityKit|api/@ohos.bluetooth.constant.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bluetooth.d.ts<br>差异内容：ConnectivityKit|api/@ohos.bluetooth.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bluetooth.hfp.d.ts<br>差异内容：ConnectivityKit|api/@ohos.bluetooth.hfp.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bluetooth.hid.d.ts<br>差异内容：ConnectivityKit|api/@ohos.bluetooth.hid.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bluetooth.map.d.ts<br>差异内容：ConnectivityKit|api/@ohos.bluetooth.map.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bluetooth.pan.d.ts<br>差异内容：ConnectivityKit|api/@ohos.bluetooth.pan.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bluetooth.pbap.d.ts<br>差异内容：ConnectivityKit|api/@ohos.bluetooth.pbap.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bluetooth.socket.d.ts<br>差异内容：ConnectivityKit|api/@ohos.bluetooth.socket.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bluetooth.wearDetection.d.ts<br>差异内容：ConnectivityKit|api/@ohos.bluetooth.wearDetection.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bluetoothManager.d.ts<br>差异内容：ConnectivityKit|api/@ohos.bluetoothManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.connectedTag.d.ts<br>差异内容：ConnectivityKit|api/@ohos.connectedTag.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.nfc.cardEmulation.d.ts<br>差异内容：ConnectivityKit|api/@ohos.nfc.cardEmulation.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.nfc.controller.d.ts<br>差异内容：ConnectivityKit|api/@ohos.nfc.controller.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.nfc.tag.d.ts<br>差异内容：ConnectivityKit|api/@ohos.nfc.tag.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.secureElement.d.ts<br>差异内容：ConnectivityKit|api/@ohos.secureElement.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.wifi.d.ts<br>差异内容：ConnectivityKit|api/@ohos.wifi.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.wifiext.d.ts<br>差异内容：ConnectivityKit|api/@ohos.wifiext.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.wifiManager.d.ts<br>差异内容：ConnectivityKit|api/@ohos.wifiManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.wifiManagerExt.d.ts<br>差异内容：ConnectivityKit|api/@ohos.wifiManagerExt.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@system.bluetooth.d.ts<br>差异内容：ConnectivityKit|api/@system.bluetooth.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.ConnectivityKit.d.ts<br>差异内容：ConnectivityKit|kits/@kit.ConnectivityKit.d.ts|
