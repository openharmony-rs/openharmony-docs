| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API模型切换|类名：global；<br>API声明：export default class FenceExtensionAbility<br>差异内容：stagemodelonly|类名：global；<br>API声明：export default class FenceExtensionAbility<br>差异内容：NA|api/@ohos.app.ability.FenceExtensionAbility.d.ts|
|API模型切换|类名：FenceExtensionAbility；<br>API声明：context: FenceExtensionContext;<br>差异内容：stagemodelonly|类名：FenceExtensionAbility；<br>API声明：context: FenceExtensionContext;<br>差异内容：NA|api/@ohos.app.ability.FenceExtensionAbility.d.ts|
|API模型切换|类名：FenceExtensionAbility；<br>API声明：onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record\<string, string>): void;<br>差异内容：stagemodelonly|类名：FenceExtensionAbility；<br>API声明：onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record\<string, string>): void;<br>差异内容：NA|api/@ohos.app.ability.FenceExtensionAbility.d.ts|
|API模型切换|类名：FenceExtensionAbility；<br>API声明：onDestroy(): void;<br>差异内容：stagemodelonly|类名：FenceExtensionAbility；<br>API声明：onDestroy(): void;<br>差异内容：NA|api/@ohos.app.ability.FenceExtensionAbility.d.ts|
|API模型切换|类名：global；<br>API声明：export default class FenceExtensionContext<br>差异内容：stagemodelonly|类名：global；<br>API声明：export default class FenceExtensionContext<br>差异内容：NA|api/@ohos.app.ability.FenceExtensionContext.d.ts|
|新增错误码|类名：geoLocationManager；<br>API声明：function on(type: 'locationChange', request: LocationRequest \| ContinuousLocationRequest, callback: Callback\<Location>): void;<br>差异内容：NA|类名：geoLocationManager；<br>API声明：function on(type: 'locationChange', request: LocationRequest \| ContinuousLocationRequest, callback: Callback\<Location>): void;<br>差异内容：3301200|api/@ohos.geoLocationManager.d.ts|
|新增错误码|类名：geoLocationManager；<br>API声明：function off(type: 'locationChange', callback?: Callback\<Location>): void;<br>差异内容：NA|类名：geoLocationManager；<br>API声明：function off(type: 'locationChange', callback?: Callback\<Location>): void;<br>差异内容：3301100,3301200|api/@ohos.geoLocationManager.d.ts|
|新增错误码|类名：geoLocationManager；<br>API声明：function on(type: 'cachedGnssLocationsChange', request: CachedGnssLocationsRequest, callback: Callback\<Array\<Location>>): void;<br>差异内容：NA|类名：geoLocationManager；<br>API声明：function on(type: 'cachedGnssLocationsChange', request: CachedGnssLocationsRequest, callback: Callback\<Array\<Location>>): void;<br>差异内容：3301200|api/@ohos.geoLocationManager.d.ts|
|新增错误码|类名：geoLocationManager；<br>API声明：function off(type: 'cachedGnssLocationsChange', callback?: Callback\<Array\<Location>>): void;<br>差异内容：NA|类名：geoLocationManager；<br>API声明：function off(type: 'cachedGnssLocationsChange', callback?: Callback\<Array\<Location>>): void;<br>差异内容：3301200|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：geoLocationManager；<br>API声明：function on(type: 'bluetoothScanResultChange', callback: Callback\<BluetoothScanResult>): void;<br>差异内容：function on(type: 'bluetoothScanResultChange', callback: Callback\<BluetoothScanResult>): void;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：geoLocationManager；<br>API声明：function off(type: 'bluetoothScanResultChange', callback?: Callback\<BluetoothScanResult>): void;<br>差异内容：function off(type: 'bluetoothScanResultChange', callback?: Callback\<BluetoothScanResult>): void;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：geoLocationManager；<br>API声明：function getDistanceBetweenLocations(location1: Location, location2: Location): number;<br>差异内容：function getDistanceBetweenLocations(location1: Location, location2: Location): number;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：geoLocationManager；<br>API声明：function isPoiServiceSupported(): boolean;<br>差异内容：function isPoiServiceSupported(): boolean;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：geoLocationManager；<br>API声明：function getPoiInfo(): Promise\<PoiInfo>;<br>差异内容：function getPoiInfo(): Promise\<PoiInfo>;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：geoLocationManager；<br>API声明：function addBeaconFence(fenceRequest: BeaconFenceRequest): Promise\<number>;<br>差异内容：function addBeaconFence(fenceRequest: BeaconFenceRequest): Promise\<number>;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：geoLocationManager；<br>API声明：function removeBeaconFence(beaconFence?: BeaconFence): Promise\<void>;<br>差异内容：function removeBeaconFence(beaconFence?: BeaconFence): Promise\<void>;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：geoLocationManager；<br>API声明：function isBeaconFenceSupported(): boolean;<br>差异内容：function isBeaconFenceSupported(): boolean;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：GeofenceTransition；<br>API声明：beaconFence?: BeaconFence;<br>差异内容：beaconFence?: BeaconFence;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：ContinuousLocationRequest；<br>API声明：needPoi?: boolean;<br>差异内容：needPoi?: boolean;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：SingleLocationRequest；<br>API声明：needPoi?: boolean;<br>差异内容：needPoi?: boolean;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：Location；<br>API声明：poi?: PoiInfo;<br>差异内容：poi?: PoiInfo;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：geoLocationManager；<br>API声明：export interface BluetoothScanResult<br>差异内容：export interface BluetoothScanResult|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：BluetoothScanResult；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：BluetoothScanResult；<br>API声明：rssi: number;<br>差异内容：rssi: number;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：BluetoothScanResult；<br>API声明：data?: ArrayBuffer;<br>差异内容：data?: ArrayBuffer;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：BluetoothScanResult；<br>API声明：deviceName: string;<br>差异内容：deviceName: string;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：BluetoothScanResult；<br>API声明：connectable: boolean;<br>差异内容：connectable: boolean;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：geoLocationManager；<br>API声明：export interface Poi<br>差异内容：export interface Poi|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：Poi；<br>API声明：id: string;<br>差异内容：id: string;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：Poi；<br>API声明：confidence: number;<br>差异内容：confidence: number;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：Poi；<br>API声明：name: string;<br>差异内容：name: string;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：Poi；<br>API声明：latitude: number;<br>差异内容：latitude: number;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：Poi；<br>API声明：longitude: number;<br>差异内容：longitude: number;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：Poi；<br>API声明：administrativeArea: string;<br>差异内容：administrativeArea: string;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：Poi；<br>API声明：subAdministrativeArea: string;<br>差异内容：subAdministrativeArea: string;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：Poi；<br>API声明：locality: string;<br>差异内容：locality: string;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：Poi；<br>API声明：subLocality: string;<br>差异内容：subLocality: string;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：Poi；<br>API声明：address: string;<br>差异内容：address: string;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：geoLocationManager；<br>API声明：export interface PoiInfo<br>差异内容：export interface PoiInfo|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：PoiInfo；<br>API声明：poiArray: Array\<Poi>;<br>差异内容：poiArray: Array\<Poi>;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：PoiInfo；<br>API声明：timestamp: number;<br>差异内容：timestamp: number;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：geoLocationManager；<br>API声明：export interface BeaconManufactureData<br>差异内容：export interface BeaconManufactureData|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：BeaconManufactureData；<br>API声明：manufactureId: number;<br>差异内容：manufactureId: number;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：BeaconManufactureData；<br>API声明：manufactureData: ArrayBuffer;<br>差异内容：manufactureData: ArrayBuffer;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：BeaconManufactureData；<br>API声明：manufactureDataMask: ArrayBuffer;<br>差异内容：manufactureDataMask: ArrayBuffer;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：geoLocationManager；<br>API声明：export interface BeaconFence<br>差异内容：export interface BeaconFence|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：BeaconFence；<br>API声明：identifier: string;<br>差异内容：identifier: string;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：BeaconFence；<br>API声明：beaconFenceInfoType: BeaconFenceInfoType;<br>差异内容：beaconFenceInfoType: BeaconFenceInfoType;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：BeaconFence；<br>API声明：manufactureData?: BeaconManufactureData;<br>差异内容：manufactureData?: BeaconManufactureData;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：geoLocationManager；<br>API声明：export interface BeaconFenceRequest<br>差异内容：export interface BeaconFenceRequest|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：BeaconFenceRequest；<br>API声明：beacon: BeaconFence;<br>差异内容：beacon: BeaconFence;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：BeaconFenceRequest；<br>API声明：transitionCallback?: Callback\<GeofenceTransition>;<br>差异内容：transitionCallback?: Callback\<GeofenceTransition>;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：BeaconFenceRequest；<br>API声明：fenceExtensionAbilityName?: string;<br>差异内容：fenceExtensionAbilityName?: string;|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：geoLocationManager；<br>API声明：export enum SportsType<br>差异内容：export enum SportsType|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：SportsType；<br>API声明：RUNNING = 1<br>差异内容：RUNNING = 1|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：SportsType；<br>API声明：WALKING<br>差异内容：WALKING|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：SportsType；<br>API声明：CYCLING<br>差异内容：CYCLING|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：geoLocationManager；<br>API声明：export enum BeaconFenceInfoType<br>差异内容：export enum BeaconFenceInfoType|NA|api/@ohos.geoLocationManager.d.ts|
|删除API|类名：BeaconFenceInfoType；<br>API声明：BEACON_MANUFACTURE_DATA = 1<br>差异内容：BEACON_MANUFACTURE_DATA = 1|NA|api/@ohos.geoLocationManager.d.ts|
