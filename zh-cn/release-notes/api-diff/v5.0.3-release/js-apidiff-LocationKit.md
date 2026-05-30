| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API模型切换|类名：global；<br>API声明：export default class FenceExtensionAbility<br>差异内容：NA|类名：global；<br>API声明：export default class FenceExtensionAbility<br>差异内容：stagemodelonly|api/@ohos.app.ability.FenceExtensionAbility.d.ts|
|API模型切换|类名：FenceExtensionAbility；<br>API声明：context: FenceExtensionContext;<br>差异内容：NA|类名：FenceExtensionAbility；<br>API声明：context: FenceExtensionContext;<br>差异内容：stagemodelonly|api/@ohos.app.ability.FenceExtensionAbility.d.ts|
|API模型切换|类名：FenceExtensionAbility；<br>API声明：onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record\<string, string>): void;<br>差异内容：NA|类名：FenceExtensionAbility；<br>API声明：onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record\<string, string>): void;<br>差异内容：stagemodelonly|api/@ohos.app.ability.FenceExtensionAbility.d.ts|
|API模型切换|类名：FenceExtensionAbility；<br>API声明：onDestroy(): void;<br>差异内容：NA|类名：FenceExtensionAbility；<br>API声明：onDestroy(): void;<br>差异内容：stagemodelonly|api/@ohos.app.ability.FenceExtensionAbility.d.ts|
|API模型切换|类名：global；<br>API声明：export default class FenceExtensionContext<br>差异内容：NA|类名：global；<br>API声明：export default class FenceExtensionContext<br>差异内容：stagemodelonly|api/@ohos.app.ability.FenceExtensionContext.d.ts|
|删除错误码|类名：geoLocationManager；<br>API声明：function on(type: 'locationChange', request: LocationRequest \| ContinuousLocationRequest, callback: Callback\<Location>): void;<br>差异内容：3301200|类名：geoLocationManager；<br>API声明：function on(type: 'locationChange', request: LocationRequest \| ContinuousLocationRequest, callback: Callback\<Location>): void;<br>差异内容：NA|api/@ohos.geoLocationManager.d.ts|
|删除错误码|类名：geoLocationManager；<br>API声明：function off(type: 'locationChange', callback?: Callback\<Location>): void;<br>差异内容：3301100,3301200|类名：geoLocationManager；<br>API声明：function off(type: 'locationChange', callback?: Callback\<Location>): void;<br>差异内容：NA|api/@ohos.geoLocationManager.d.ts|
|删除错误码|类名：geoLocationManager；<br>API声明：function on(type: 'cachedGnssLocationsChange', request: CachedGnssLocationsRequest, callback: Callback\<Array\<Location>>): void;<br>差异内容：3301200|类名：geoLocationManager；<br>API声明：function on(type: 'cachedGnssLocationsChange', request: CachedGnssLocationsRequest, callback: Callback\<Array\<Location>>): void;<br>差异内容：NA|api/@ohos.geoLocationManager.d.ts|
|删除错误码|类名：geoLocationManager；<br>API声明：function off(type: 'cachedGnssLocationsChange', callback?: Callback\<Array\<Location>>): void;<br>差异内容：3301200|类名：geoLocationManager；<br>API声明：function off(type: 'cachedGnssLocationsChange', callback?: Callback\<Array\<Location>>): void;<br>差异内容：NA|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function on(type: 'bluetoothScanResultChange', callback: Callback\<BluetoothScanResult>): void;<br>差异内容：function on(type: 'bluetoothScanResultChange', callback: Callback\<BluetoothScanResult>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function off(type: 'bluetoothScanResultChange', callback?: Callback\<BluetoothScanResult>): void;<br>差异内容：function off(type: 'bluetoothScanResultChange', callback?: Callback\<BluetoothScanResult>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function getDistanceBetweenLocations(location1: Location, location2: Location): number;<br>差异内容：function getDistanceBetweenLocations(location1: Location, location2: Location): number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function isPoiServiceSupported(): boolean;<br>差异内容：function isPoiServiceSupported(): boolean;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function getPoiInfo(): Promise\<PoiInfo>;<br>差异内容：function getPoiInfo(): Promise\<PoiInfo>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function addBeaconFence(fenceRequest: BeaconFenceRequest): Promise\<number>;<br>差异内容：function addBeaconFence(fenceRequest: BeaconFenceRequest): Promise\<number>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function removeBeaconFence(beaconFence?: BeaconFence): Promise\<void>;<br>差异内容：function removeBeaconFence(beaconFence?: BeaconFence): Promise\<void>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function isBeaconFenceSupported(): boolean;<br>差异内容：function isBeaconFenceSupported(): boolean;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeofenceTransition；<br>API声明：beaconFence?: BeaconFence;<br>差异内容：beaconFence?: BeaconFence;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：ContinuousLocationRequest；<br>API声明：needPoi?: boolean;<br>差异内容：needPoi?: boolean;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SingleLocationRequest；<br>API声明：needPoi?: boolean;<br>差异内容：needPoi?: boolean;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：poi?: PoiInfo;<br>差异内容：poi?: PoiInfo;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface BluetoothScanResult<br>差异内容：export interface BluetoothScanResult|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BluetoothScanResult；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BluetoothScanResult；<br>API声明：rssi: number;<br>差异内容：rssi: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BluetoothScanResult；<br>API声明：data?: ArrayBuffer;<br>差异内容：data?: ArrayBuffer;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BluetoothScanResult；<br>API声明：deviceName: string;<br>差异内容：deviceName: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BluetoothScanResult；<br>API声明：connectable: boolean;<br>差异内容：connectable: boolean;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface Poi<br>差异内容：export interface Poi|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Poi；<br>API声明：id: string;<br>差异内容：id: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Poi；<br>API声明：confidence: number;<br>差异内容：confidence: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Poi；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Poi；<br>API声明：latitude: number;<br>差异内容：latitude: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Poi；<br>API声明：longitude: number;<br>差异内容：longitude: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Poi；<br>API声明：administrativeArea: string;<br>差异内容：administrativeArea: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Poi；<br>API声明：subAdministrativeArea: string;<br>差异内容：subAdministrativeArea: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Poi；<br>API声明：locality: string;<br>差异内容：locality: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Poi；<br>API声明：subLocality: string;<br>差异内容：subLocality: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Poi；<br>API声明：address: string;<br>差异内容：address: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface PoiInfo<br>差异内容：export interface PoiInfo|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：PoiInfo；<br>API声明：poiArray: Array\<Poi>;<br>差异内容：poiArray: Array\<Poi>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：PoiInfo；<br>API声明：timestamp: number;<br>差异内容：timestamp: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface BeaconManufactureData<br>差异内容：export interface BeaconManufactureData|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BeaconManufactureData；<br>API声明：manufactureId: number;<br>差异内容：manufactureId: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BeaconManufactureData；<br>API声明：manufactureData: ArrayBuffer;<br>差异内容：manufactureData: ArrayBuffer;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BeaconManufactureData；<br>API声明：manufactureDataMask: ArrayBuffer;<br>差异内容：manufactureDataMask: ArrayBuffer;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface BeaconFence<br>差异内容：export interface BeaconFence|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BeaconFence；<br>API声明：identifier: string;<br>差异内容：identifier: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BeaconFence；<br>API声明：beaconFenceInfoType: BeaconFenceInfoType;<br>差异内容：beaconFenceInfoType: BeaconFenceInfoType;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BeaconFence；<br>API声明：manufactureData?: BeaconManufactureData;<br>差异内容：manufactureData?: BeaconManufactureData;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface BeaconFenceRequest<br>差异内容：export interface BeaconFenceRequest|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BeaconFenceRequest；<br>API声明：beacon: BeaconFence;<br>差异内容：beacon: BeaconFence;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BeaconFenceRequest；<br>API声明：transitionCallback?: Callback\<GeofenceTransition>;<br>差异内容：transitionCallback?: Callback\<GeofenceTransition>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BeaconFenceRequest；<br>API声明：fenceExtensionAbilityName?: string;<br>差异内容：fenceExtensionAbilityName?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export enum SportsType<br>差异内容：export enum SportsType|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SportsType；<br>API声明：RUNNING = 1<br>差异内容：RUNNING = 1|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SportsType；<br>API声明：WALKING<br>差异内容：WALKING|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SportsType；<br>API声明：CYCLING<br>差异内容：CYCLING|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export enum BeaconFenceInfoType<br>差异内容：export enum BeaconFenceInfoType|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BeaconFenceInfoType；<br>API声明：BEACON_MANUFACTURE_DATA = 1<br>差异内容：BEACON_MANUFACTURE_DATA = 1|api/@ohos.geoLocationManager.d.ts|
