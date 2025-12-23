| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|API model switching|Class name: global;<br>API declaration: export default class FenceExtensionAbility<br>DIfferences: NA|Class name: global;<br>API declaration: export default class FenceExtensionAbility<br>DIfferences: stagemodelonly|api/@ohos.app.ability.FenceExtensionAbility.d.ts|
|API model switching|Class name: FenceExtensionAbility;<br>API declaration: context: FenceExtensionContext;<br>DIfferences: NA|Class name: FenceExtensionAbility;<br>API declaration: context: FenceExtensionContext;<br>DIfferences: stagemodelonly|api/@ohos.app.ability.FenceExtensionAbility.d.ts|
|API model switching|Class name: FenceExtensionAbility;<br>API declaration: onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record\<string, string>): void;<br>DIfferences: NA|Class name: FenceExtensionAbility;<br>API declaration: onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record\<string, string>): void;<br>DIfferences: stagemodelonly|api/@ohos.app.ability.FenceExtensionAbility.d.ts|
|API model switching|Class name: FenceExtensionAbility;<br>API declaration: onDestroy(): void;<br>DIfferences: NA|Class name: FenceExtensionAbility;<br>API declaration: onDestroy(): void;<br>DIfferences: stagemodelonly|api/@ohos.app.ability.FenceExtensionAbility.d.ts|
|API model switching|Class name: global;<br>API declaration: export default class FenceExtensionContext<br>DIfferences: NA|Class name: global;<br>API declaration: export default class FenceExtensionContext<br>DIfferences: stagemodelonly|api/@ohos.app.ability.FenceExtensionContext.d.ts|
|Deleted error code|Class name: geoLocationManager;<br>API declaration: function on(type: 'locationChange', request: LocationRequest \| ContinuousLocationRequest, callback: Callback\<Location>): void;<br>DIfferences: 3301200|Class name: geoLocationManager;<br>API declaration: function on(type: 'locationChange', request: LocationRequest \| ContinuousLocationRequest, callback: Callback\<Location>): void;<br>DIfferences: NA|api/@ohos.geoLocationManager.d.ts|
|Deleted error code|Class name: geoLocationManager;<br>API declaration: function off(type: 'locationChange', callback?: Callback\<Location>): void;<br>DIfferences: 3301100,3301200|Class name: geoLocationManager;<br>API declaration: function off(type: 'locationChange', callback?: Callback\<Location>): void;<br>DIfferences: NA|api/@ohos.geoLocationManager.d.ts|
|Deleted error code|Class name: geoLocationManager;<br>API declaration: function on(type: 'cachedGnssLocationsChange', request: CachedGnssLocationsRequest, callback: Callback\<Array\<Location>>): void;<br>DIfferences: 3301200|Class name: geoLocationManager;<br>API declaration: function on(type: 'cachedGnssLocationsChange', request: CachedGnssLocationsRequest, callback: Callback\<Array\<Location>>): void;<br>DIfferences: NA|api/@ohos.geoLocationManager.d.ts|
|Deleted error code|Class name: geoLocationManager;<br>API declaration: function off(type: 'cachedGnssLocationsChange', callback?: Callback\<Array\<Location>>): void;<br>DIfferences: 3301200|Class name: geoLocationManager;<br>API declaration: function off(type: 'cachedGnssLocationsChange', callback?: Callback\<Array\<Location>>): void;<br>DIfferences: NA|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function on(type: 'bluetoothScanResultChange', callback: Callback\<BluetoothScanResult>): void;<br>DIfferences: function on(type: 'bluetoothScanResultChange', callback: Callback\<BluetoothScanResult>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function off(type: 'bluetoothScanResultChange', callback?: Callback\<BluetoothScanResult>): void;<br>DIfferences: function off(type: 'bluetoothScanResultChange', callback?: Callback\<BluetoothScanResult>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function getDistanceBetweenLocations(location1: Location, location2: Location): number;<br>DIfferences: function getDistanceBetweenLocations(location1: Location, location2: Location): number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function isPoiServiceSupported(): boolean;<br>DIfferences: function isPoiServiceSupported(): boolean;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function getPoiInfo(): Promise\<PoiInfo>;<br>DIfferences: function getPoiInfo(): Promise\<PoiInfo>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function addBeaconFence(fenceRequest: BeaconFenceRequest): Promise\<number>;<br>DIfferences: function addBeaconFence(fenceRequest: BeaconFenceRequest): Promise\<number>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function removeBeaconFence(beaconFence?: BeaconFence): Promise\<void>;<br>DIfferences: function removeBeaconFence(beaconFence?: BeaconFence): Promise\<void>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function isBeaconFenceSupported(): boolean;<br>DIfferences: function isBeaconFenceSupported(): boolean;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeofenceTransition;<br>API declaration: beaconFence?: BeaconFence;<br>DIfferences: beaconFence?: BeaconFence;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: ContinuousLocationRequest;<br>API declaration: needPoi?: boolean;<br>DIfferences: needPoi?: boolean;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: SingleLocationRequest;<br>API declaration: needPoi?: boolean;<br>DIfferences: needPoi?: boolean;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Location;<br>API declaration: poi?: PoiInfo;<br>DIfferences: poi?: PoiInfo;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export interface BluetoothScanResult<br>DIfferences: export interface BluetoothScanResult|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: BluetoothScanResult;<br>API declaration: deviceId: string;<br>DIfferences: deviceId: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: BluetoothScanResult;<br>API declaration: rssi: number;<br>DIfferences: rssi: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: BluetoothScanResult;<br>API declaration: data?: ArrayBuffer;<br>DIfferences: data?: ArrayBuffer;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: BluetoothScanResult;<br>API declaration: deviceName: string;<br>DIfferences: deviceName: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: BluetoothScanResult;<br>API declaration: connectable: boolean;<br>DIfferences: connectable: boolean;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export interface Poi<br>DIfferences: export interface Poi|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Poi;<br>API declaration: id: string;<br>DIfferences: id: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Poi;<br>API declaration: confidence: number;<br>DIfferences: confidence: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Poi;<br>API declaration: name: string;<br>DIfferences: name: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Poi;<br>API declaration: latitude: number;<br>DIfferences: latitude: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Poi;<br>API declaration: longitude: number;<br>DIfferences: longitude: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Poi;<br>API declaration: administrativeArea: string;<br>DIfferences: administrativeArea: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Poi;<br>API declaration: subAdministrativeArea: string;<br>DIfferences: subAdministrativeArea: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Poi;<br>API declaration: locality: string;<br>DIfferences: locality: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Poi;<br>API declaration: subLocality: string;<br>DIfferences: subLocality: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Poi;<br>API declaration: address: string;<br>DIfferences: address: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export interface PoiInfo<br>DIfferences: export interface PoiInfo|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: PoiInfo;<br>API declaration: poiArray: Array\<Poi>;<br>DIfferences: poiArray: Array\<Poi>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: PoiInfo;<br>API declaration: timestamp: number;<br>DIfferences: timestamp: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export interface BeaconManufactureData<br>DIfferences: export interface BeaconManufactureData|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: BeaconManufactureData;<br>API declaration: manufactureId: number;<br>DIfferences: manufactureId: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: BeaconManufactureData;<br>API declaration: manufactureData: ArrayBuffer;<br>DIfferences: manufactureData: ArrayBuffer;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: BeaconManufactureData;<br>API declaration: manufactureDataMask: ArrayBuffer;<br>DIfferences: manufactureDataMask: ArrayBuffer;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export interface BeaconFence<br>DIfferences: export interface BeaconFence|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: BeaconFence;<br>API declaration: identifier: string;<br>DIfferences: identifier: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: BeaconFence;<br>API declaration: beaconFenceInfoType: BeaconFenceInfoType;<br>DIfferences: beaconFenceInfoType: BeaconFenceInfoType;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: BeaconFence;<br>API declaration: manufactureData?: BeaconManufactureData;<br>DIfferences: manufactureData?: BeaconManufactureData;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export interface BeaconFenceRequest<br>DIfferences: export interface BeaconFenceRequest|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: BeaconFenceRequest;<br>API declaration: beacon: BeaconFence;<br>DIfferences: beacon: BeaconFence;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: BeaconFenceRequest;<br>API declaration: transitionCallback?: Callback\<GeofenceTransition>;<br>DIfferences: transitionCallback?: Callback\<GeofenceTransition>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: BeaconFenceRequest;<br>API declaration: fenceExtensionAbilityName?: string;<br>DIfferences: fenceExtensionAbilityName?: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export enum SportsType<br>DIfferences: export enum SportsType|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: SportsType;<br>API declaration: RUNNING = 1<br>DIfferences: RUNNING = 1|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: SportsType;<br>API declaration: WALKING<br>DIfferences: WALKING|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: SportsType;<br>API declaration: CYCLING<br>DIfferences: CYCLING|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export enum BeaconFenceInfoType<br>DIfferences: export enum BeaconFenceInfoType|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: BeaconFenceInfoType;<br>API declaration: BEACON_MANUFACTURE_DATA = 1<br>DIfferences: BEACON_MANUFACTURE_DATA = 1|api/@ohos.geoLocationManager.d.ts|
