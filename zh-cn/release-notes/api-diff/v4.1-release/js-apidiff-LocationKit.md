| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace geolocation<br>差异内容：declare namespace geolocation|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function on(type: 'locationChange', request: LocationRequest, callback: Callback\<Location>): void;<br>差异内容：function on(type: 'locationChange', request: LocationRequest, callback: Callback\<Location>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function off(type: 'locationChange', callback?: Callback\<Location>): void;<br>差异内容：function off(type: 'locationChange', callback?: Callback\<Location>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function on(type: 'locationServiceState', callback: Callback\<boolean>): void;<br>差异内容：function on(type: 'locationServiceState', callback: Callback\<boolean>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function off(type: 'locationServiceState', callback?: Callback\<boolean>): void;<br>差异内容：function off(type: 'locationServiceState', callback?: Callback\<boolean>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function on(type: 'cachedGnssLocationsReporting', request: CachedGnssLocationsRequest, callback: Callback\<Array\<Location>>): void;<br>差异内容：function on(type: 'cachedGnssLocationsReporting', request: CachedGnssLocationsRequest, callback: Callback\<Array\<Location>>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function off(type: 'cachedGnssLocationsReporting', callback?: Callback\<Array\<Location>>): void;<br>差异内容：function off(type: 'cachedGnssLocationsReporting', callback?: Callback\<Array\<Location>>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function on(type: 'gnssStatusChange', callback: Callback\<SatelliteStatusInfo>): void;<br>差异内容：function on(type: 'gnssStatusChange', callback: Callback\<SatelliteStatusInfo>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function off(type: 'gnssStatusChange', callback?: Callback\<SatelliteStatusInfo>): void;<br>差异内容：function off(type: 'gnssStatusChange', callback?: Callback\<SatelliteStatusInfo>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function on(type: 'nmeaMessageChange', callback: Callback\<string>): void;<br>差异内容：function on(type: 'nmeaMessageChange', callback: Callback\<string>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function off(type: 'nmeaMessageChange', callback?: Callback\<string>): void;<br>差异内容：function off(type: 'nmeaMessageChange', callback?: Callback\<string>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function on(type: 'fenceStatusChange', request: GeofenceRequest, want: WantAgent): void;<br>差异内容：function on(type: 'fenceStatusChange', request: GeofenceRequest, want: WantAgent): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function off(type: 'fenceStatusChange', request: GeofenceRequest, want: WantAgent): void;<br>差异内容：function off(type: 'fenceStatusChange', request: GeofenceRequest, want: WantAgent): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function getCurrentLocation(request: CurrentLocationRequest, callback: AsyncCallback\<Location>): void;<br>差异内容：function getCurrentLocation(request: CurrentLocationRequest, callback: AsyncCallback\<Location>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function getCurrentLocation(callback: AsyncCallback\<Location>): void;<br>差异内容：function getCurrentLocation(callback: AsyncCallback\<Location>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function getCurrentLocation(request?: CurrentLocationRequest): Promise\<Location>;<br>差异内容：function getCurrentLocation(request?: CurrentLocationRequest): Promise\<Location>;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function getLastLocation(callback: AsyncCallback\<Location>): void;<br>差异内容：function getLastLocation(callback: AsyncCallback\<Location>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function getLastLocation(): Promise\<Location>;<br>差异内容：function getLastLocation(): Promise\<Location>;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function isLocationEnabled(callback: AsyncCallback\<boolean>): void;<br>差异内容：function isLocationEnabled(callback: AsyncCallback\<boolean>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function isLocationEnabled(): Promise\<boolean>;<br>差异内容：function isLocationEnabled(): Promise\<boolean>;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function requestEnableLocation(callback: AsyncCallback\<boolean>): void;<br>差异内容：function requestEnableLocation(callback: AsyncCallback\<boolean>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function requestEnableLocation(): Promise\<boolean>;<br>差异内容：function requestEnableLocation(): Promise\<boolean>;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function getAddressesFromLocation(request: ReverseGeoCodeRequest, callback: AsyncCallback\<Array\<GeoAddress>>): void;<br>差异内容：function getAddressesFromLocation(request: ReverseGeoCodeRequest, callback: AsyncCallback\<Array\<GeoAddress>>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function getAddressesFromLocation(request: ReverseGeoCodeRequest): Promise\<Array\<GeoAddress>>;<br>差异内容：function getAddressesFromLocation(request: ReverseGeoCodeRequest): Promise\<Array\<GeoAddress>>;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function getAddressesFromLocationName(request: GeoCodeRequest, callback: AsyncCallback\<Array\<GeoAddress>>): void;<br>差异内容：function getAddressesFromLocationName(request: GeoCodeRequest, callback: AsyncCallback\<Array\<GeoAddress>>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function getAddressesFromLocationName(request: GeoCodeRequest): Promise\<Array\<GeoAddress>>;<br>差异内容：function getAddressesFromLocationName(request: GeoCodeRequest): Promise\<Array\<GeoAddress>>;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function isGeoServiceAvailable(callback: AsyncCallback\<boolean>): void;<br>差异内容：function isGeoServiceAvailable(callback: AsyncCallback\<boolean>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function isGeoServiceAvailable(): Promise\<boolean>;<br>差异内容：function isGeoServiceAvailable(): Promise\<boolean>;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function getCachedGnssLocationsSize(callback: AsyncCallback\<number>): void;<br>差异内容：function getCachedGnssLocationsSize(callback: AsyncCallback\<number>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function getCachedGnssLocationsSize(): Promise\<number>;<br>差异内容：function getCachedGnssLocationsSize(): Promise\<number>;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function flushCachedGnssLocations(callback: AsyncCallback\<boolean>): void;<br>差异内容：function flushCachedGnssLocations(callback: AsyncCallback\<boolean>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function flushCachedGnssLocations(): Promise\<boolean>;<br>差异内容：function flushCachedGnssLocations(): Promise\<boolean>;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function sendCommand(command: LocationCommand, callback: AsyncCallback\<boolean>): void;<br>差异内容：function sendCommand(command: LocationCommand, callback: AsyncCallback\<boolean>): void;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：function sendCommand(command: LocationCommand): Promise\<boolean>;<br>差异内容：function sendCommand(command: LocationCommand): Promise\<boolean>;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：export interface SatelliteStatusInfo<br>差异内容：export interface SatelliteStatusInfo|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：SatelliteStatusInfo；<br>API声明：satellitesNumber: number;<br>差异内容：satellitesNumber: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：SatelliteStatusInfo；<br>API声明：satelliteIds: Array\<number>;<br>差异内容：satelliteIds: Array\<number>;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：SatelliteStatusInfo；<br>API声明：carrierToNoiseDensitys: Array\<number>;<br>差异内容：carrierToNoiseDensitys: Array\<number>;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：SatelliteStatusInfo；<br>API声明：altitudes: Array\<number>;<br>差异内容：altitudes: Array\<number>;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：SatelliteStatusInfo；<br>API声明：azimuths: Array\<number>;<br>差异内容：azimuths: Array\<number>;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：SatelliteStatusInfo；<br>API声明：carrierFrequencies: Array\<number>;<br>差异内容：carrierFrequencies: Array\<number>;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：export interface CachedGnssLocationsRequest<br>差异内容：export interface CachedGnssLocationsRequest|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：CachedGnssLocationsRequest；<br>API声明：reportingPeriodSec: number;<br>差异内容：reportingPeriodSec: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：CachedGnssLocationsRequest；<br>API声明：wakeUpCacheQueueFull: boolean;<br>差异内容：wakeUpCacheQueueFull: boolean;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：export interface GeofenceRequest<br>差异内容：export interface GeofenceRequest|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeofenceRequest；<br>API声明：priority: LocationRequestPriority;<br>差异内容：priority: LocationRequestPriority;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeofenceRequest；<br>API声明：scenario: LocationRequestScenario;<br>差异内容：scenario: LocationRequestScenario;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeofenceRequest；<br>API声明：geofence: Geofence;<br>差异内容：geofence: Geofence;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：export interface Geofence<br>差异内容：export interface Geofence|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：Geofence；<br>API声明：latitude: number;<br>差异内容：latitude: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：Geofence；<br>API声明：longitude: number;<br>差异内容：longitude: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：Geofence；<br>API声明：radius: number;<br>差异内容：radius: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：Geofence；<br>API声明：expiration: number;<br>差异内容：expiration: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：export interface ReverseGeoCodeRequest<br>差异内容：export interface ReverseGeoCodeRequest|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：ReverseGeoCodeRequest；<br>API声明：locale?: string;<br>差异内容：locale?: string;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：ReverseGeoCodeRequest；<br>API声明：latitude: number;<br>差异内容：latitude: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：ReverseGeoCodeRequest；<br>API声明：longitude: number;<br>差异内容：longitude: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：ReverseGeoCodeRequest；<br>API声明：maxItems?: number;<br>差异内容：maxItems?: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：export interface GeoCodeRequest<br>差异内容：export interface GeoCodeRequest|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoCodeRequest；<br>API声明：locale?: string;<br>差异内容：locale?: string;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoCodeRequest；<br>API声明：description: string;<br>差异内容：description: string;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoCodeRequest；<br>API声明：maxItems?: number;<br>差异内容：maxItems?: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoCodeRequest；<br>API声明：minLatitude?: number;<br>差异内容：minLatitude?: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoCodeRequest；<br>API声明：minLongitude?: number;<br>差异内容：minLongitude?: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoCodeRequest；<br>API声明：maxLatitude?: number;<br>差异内容：maxLatitude?: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoCodeRequest；<br>API声明：maxLongitude?: number;<br>差异内容：maxLongitude?: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：export interface GeoAddress<br>差异内容：export interface GeoAddress|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：latitude?: number;<br>差异内容：latitude?: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：longitude?: number;<br>差异内容：longitude?: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：locale?: string;<br>差异内容：locale?: string;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：placeName?: string;<br>差异内容：placeName?: string;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：countryCode?: string;<br>差异内容：countryCode?: string;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：countryName?: string;<br>差异内容：countryName?: string;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：administrativeArea?: string;<br>差异内容：administrativeArea?: string;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：subAdministrativeArea?: string;<br>差异内容：subAdministrativeArea?: string;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：locality?: string;<br>差异内容：locality?: string;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：subLocality?: string;<br>差异内容：subLocality?: string;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：roadName?: string;<br>差异内容：roadName?: string;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：subRoadName?: string;<br>差异内容：subRoadName?: string;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：premises?: string;<br>差异内容：premises?: string;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：postalCode?: string;<br>差异内容：postalCode?: string;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：phoneNumber?: string;<br>差异内容：phoneNumber?: string;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：addressUrl?: string;<br>差异内容：addressUrl?: string;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：descriptions?: Array\<string>;<br>差异内容：descriptions?: Array\<string>;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：descriptionsSize?: number;<br>差异内容：descriptionsSize?: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：export interface LocationRequest<br>差异内容：export interface LocationRequest|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationRequest；<br>API声明：priority?: LocationRequestPriority;<br>差异内容：priority?: LocationRequestPriority;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationRequest；<br>API声明：scenario?: LocationRequestScenario;<br>差异内容：scenario?: LocationRequestScenario;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationRequest；<br>API声明：timeInterval?: number;<br>差异内容：timeInterval?: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationRequest；<br>API声明：distanceInterval?: number;<br>差异内容：distanceInterval?: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationRequest；<br>API声明：maxAccuracy?: number;<br>差异内容：maxAccuracy?: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：export interface CurrentLocationRequest<br>差异内容：export interface CurrentLocationRequest|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：CurrentLocationRequest；<br>API声明：priority?: LocationRequestPriority;<br>差异内容：priority?: LocationRequestPriority;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：CurrentLocationRequest；<br>API声明：scenario?: LocationRequestScenario;<br>差异内容：scenario?: LocationRequestScenario;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：CurrentLocationRequest；<br>API声明：maxAccuracy?: number;<br>差异内容：maxAccuracy?: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：CurrentLocationRequest；<br>API声明：timeoutMs?: number;<br>差异内容：timeoutMs?: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：export interface Location<br>差异内容：export interface Location|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：Location；<br>API声明：latitude: number;<br>差异内容：latitude: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：Location；<br>API声明：longitude: number;<br>差异内容：longitude: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：Location；<br>API声明：altitude: number;<br>差异内容：altitude: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：Location；<br>API声明：accuracy: number;<br>差异内容：accuracy: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：Location；<br>API声明：speed: number;<br>差异内容：speed: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：Location；<br>API声明：timeStamp: number;<br>差异内容：timeStamp: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：Location；<br>API声明：direction: number;<br>差异内容：direction: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：Location；<br>API声明：timeSinceBoot: number;<br>差异内容：timeSinceBoot: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：Location；<br>API声明：additions?: Array\<string>;<br>差异内容：additions?: Array\<string>;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：Location；<br>API声明：additionSize?: number;<br>差异内容：additionSize?: number;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：export enum LocationRequestPriority<br>差异内容：export enum LocationRequestPriority|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationRequestPriority；<br>API声明：UNSET = 0x200<br>差异内容：UNSET = 0x200|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationRequestPriority；<br>API声明：ACCURACY<br>差异内容：ACCURACY|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationRequestPriority；<br>API声明：LOW_POWER<br>差异内容：LOW_POWER|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationRequestPriority；<br>API声明：FIRST_FIX<br>差异内容：FIRST_FIX|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：export enum LocationRequestScenario<br>差异内容：export enum LocationRequestScenario|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationRequestScenario；<br>API声明：UNSET = 0x300<br>差异内容：UNSET = 0x300|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationRequestScenario；<br>API声明：NAVIGATION<br>差异内容：NAVIGATION|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationRequestScenario；<br>API声明：TRAJECTORY_TRACKING<br>差异内容：TRAJECTORY_TRACKING|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationRequestScenario；<br>API声明：CAR_HAILING<br>差异内容：CAR_HAILING|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationRequestScenario；<br>API声明：DAILY_LIFE_SERVICE<br>差异内容：DAILY_LIFE_SERVICE|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationRequestScenario；<br>API声明：NO_POWER<br>差异内容：NO_POWER|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：export enum GeoLocationErrorCode<br>差异内容：export enum GeoLocationErrorCode|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoLocationErrorCode；<br>API声明：INPUT_PARAMS_ERROR<br>差异内容：INPUT_PARAMS_ERROR|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoLocationErrorCode；<br>API声明：REVERSE_GEOCODE_ERROR<br>差异内容：REVERSE_GEOCODE_ERROR|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoLocationErrorCode；<br>API声明：GEOCODE_ERROR<br>差异内容：GEOCODE_ERROR|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoLocationErrorCode；<br>API声明：LOCATOR_ERROR<br>差异内容：LOCATOR_ERROR|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoLocationErrorCode；<br>API声明：LOCATION_SWITCH_ERROR<br>差异内容：LOCATION_SWITCH_ERROR|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoLocationErrorCode；<br>API声明：LAST_KNOWN_LOCATION_ERROR<br>差异内容：LAST_KNOWN_LOCATION_ERROR|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：GeoLocationErrorCode；<br>API声明：LOCATION_REQUEST_TIMEOUT_ERROR<br>差异内容：LOCATION_REQUEST_TIMEOUT_ERROR|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：export enum LocationPrivacyType<br>差异内容：export enum LocationPrivacyType|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationPrivacyType；<br>API声明：OTHERS = 0<br>差异内容：OTHERS = 0|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationPrivacyType；<br>API声明：STARTUP<br>差异内容：STARTUP|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationPrivacyType；<br>API声明：CORE_LOCATION<br>差异内容：CORE_LOCATION|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：geolocation；<br>API声明：export interface LocationCommand<br>差异内容：export interface LocationCommand|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationCommand；<br>API声明：scenario: LocationRequestScenario;<br>差异内容：scenario: LocationRequestScenario;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：LocationCommand；<br>API声明：command: string;<br>差异内容：command: string;|api/@ohos.geolocation.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace geoLocationManager<br>差异内容：declare namespace geoLocationManager|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function on(type: 'locationChange', request: LocationRequest, callback: Callback\<Location>): void;<br>差异内容：function on(type: 'locationChange', request: LocationRequest, callback: Callback\<Location>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function off(type: 'locationChange', callback?: Callback\<Location>): void;<br>差异内容：function off(type: 'locationChange', callback?: Callback\<Location>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function on(type: 'locationEnabledChange', callback: Callback\<boolean>): void;<br>差异内容：function on(type: 'locationEnabledChange', callback: Callback\<boolean>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function off(type: 'locationEnabledChange', callback?: Callback\<boolean>): void;<br>差异内容：function off(type: 'locationEnabledChange', callback?: Callback\<boolean>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function on(type: 'cachedGnssLocationsChange', request: CachedGnssLocationsRequest, callback: Callback\<Array\<Location>>): void;<br>差异内容：function on(type: 'cachedGnssLocationsChange', request: CachedGnssLocationsRequest, callback: Callback\<Array\<Location>>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function off(type: 'cachedGnssLocationsChange', callback?: Callback\<Array\<Location>>): void;<br>差异内容：function off(type: 'cachedGnssLocationsChange', callback?: Callback\<Array\<Location>>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function on(type: 'satelliteStatusChange', callback: Callback\<SatelliteStatusInfo>): void;<br>差异内容：function on(type: 'satelliteStatusChange', callback: Callback\<SatelliteStatusInfo>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function off(type: 'satelliteStatusChange', callback?: Callback\<SatelliteStatusInfo>): void;<br>差异内容：function off(type: 'satelliteStatusChange', callback?: Callback\<SatelliteStatusInfo>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function on(type: 'nmeaMessage', callback: Callback\<string>): void;<br>差异内容：function on(type: 'nmeaMessage', callback: Callback\<string>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function off(type: 'nmeaMessage', callback?: Callback\<string>): void;<br>差异内容：function off(type: 'nmeaMessage', callback?: Callback\<string>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function on(type: 'gnssFenceStatusChange', request: GeofenceRequest, want: WantAgent): void;<br>差异内容：function on(type: 'gnssFenceStatusChange', request: GeofenceRequest, want: WantAgent): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function off(type: 'gnssFenceStatusChange', request: GeofenceRequest, want: WantAgent): void;<br>差异内容：function off(type: 'gnssFenceStatusChange', request: GeofenceRequest, want: WantAgent): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function on(type: 'countryCodeChange', callback: Callback\<CountryCode>): void;<br>差异内容：function on(type: 'countryCodeChange', callback: Callback\<CountryCode>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function off(type: 'countryCodeChange', callback?: Callback\<CountryCode>): void;<br>差异内容：function off(type: 'countryCodeChange', callback?: Callback\<CountryCode>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function getCurrentLocation(request: CurrentLocationRequest, callback: AsyncCallback\<Location>): void;<br>差异内容：function getCurrentLocation(request: CurrentLocationRequest, callback: AsyncCallback\<Location>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function getCurrentLocation(callback: AsyncCallback\<Location>): void;<br>差异内容：function getCurrentLocation(callback: AsyncCallback\<Location>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function getCurrentLocation(request?: CurrentLocationRequest): Promise\<Location>;<br>差异内容：function getCurrentLocation(request?: CurrentLocationRequest): Promise\<Location>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function getLastLocation(): Location;<br>差异内容：function getLastLocation(): Location;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function isLocationEnabled(): boolean;<br>差异内容：function isLocationEnabled(): boolean;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function getAddressesFromLocation(request: ReverseGeoCodeRequest, callback: AsyncCallback\<Array\<GeoAddress>>): void;<br>差异内容：function getAddressesFromLocation(request: ReverseGeoCodeRequest, callback: AsyncCallback\<Array\<GeoAddress>>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function getAddressesFromLocation(request: ReverseGeoCodeRequest): Promise\<Array\<GeoAddress>>;<br>差异内容：function getAddressesFromLocation(request: ReverseGeoCodeRequest): Promise\<Array\<GeoAddress>>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function getAddressesFromLocationName(request: GeoCodeRequest, callback: AsyncCallback\<Array\<GeoAddress>>): void;<br>差异内容：function getAddressesFromLocationName(request: GeoCodeRequest, callback: AsyncCallback\<Array\<GeoAddress>>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function getAddressesFromLocationName(request: GeoCodeRequest): Promise\<Array\<GeoAddress>>;<br>差异内容：function getAddressesFromLocationName(request: GeoCodeRequest): Promise\<Array\<GeoAddress>>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function isGeocoderAvailable(): boolean;<br>差异内容：function isGeocoderAvailable(): boolean;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function getCachedGnssLocationsSize(callback: AsyncCallback\<number>): void;<br>差异内容：function getCachedGnssLocationsSize(callback: AsyncCallback\<number>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function getCachedGnssLocationsSize(): Promise\<number>;<br>差异内容：function getCachedGnssLocationsSize(): Promise\<number>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function flushCachedGnssLocations(callback: AsyncCallback\<void>): void;<br>差异内容：function flushCachedGnssLocations(callback: AsyncCallback\<void>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function flushCachedGnssLocations(): Promise\<void>;<br>差异内容：function flushCachedGnssLocations(): Promise\<void>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function sendCommand(command: LocationCommand, callback: AsyncCallback\<void>): void;<br>差异内容：function sendCommand(command: LocationCommand, callback: AsyncCallback\<void>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function sendCommand(command: LocationCommand): Promise\<void>;<br>差异内容：function sendCommand(command: LocationCommand): Promise\<void>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function getCountryCode(callback: AsyncCallback\<CountryCode>): void;<br>差异内容：function getCountryCode(callback: AsyncCallback\<CountryCode>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function getCountryCode(): Promise\<CountryCode>;<br>差异内容：function getCountryCode(): Promise\<CountryCode>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface SatelliteStatusInfo<br>差异内容：export interface SatelliteStatusInfo|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteStatusInfo；<br>API声明：satellitesNumber: number;<br>差异内容：satellitesNumber: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteStatusInfo；<br>API声明：satelliteIds: Array\<number>;<br>差异内容：satelliteIds: Array\<number>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteStatusInfo；<br>API声明：carrierToNoiseDensitys: Array\<number>;<br>差异内容：carrierToNoiseDensitys: Array\<number>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteStatusInfo；<br>API声明：altitudes: Array\<number>;<br>差异内容：altitudes: Array\<number>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteStatusInfo；<br>API声明：azimuths: Array\<number>;<br>差异内容：azimuths: Array\<number>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteStatusInfo；<br>API声明：carrierFrequencies: Array\<number>;<br>差异内容：carrierFrequencies: Array\<number>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface CachedGnssLocationsRequest<br>差异内容：export interface CachedGnssLocationsRequest|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：CachedGnssLocationsRequest；<br>API声明：reportingPeriodSec: number;<br>差异内容：reportingPeriodSec: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：CachedGnssLocationsRequest；<br>API声明：wakeUpCacheQueueFull: boolean;<br>差异内容：wakeUpCacheQueueFull: boolean;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface GeofenceRequest<br>差异内容：export interface GeofenceRequest|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeofenceRequest；<br>API声明：scenario: LocationRequestScenario;<br>差异内容：scenario: LocationRequestScenario;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeofenceRequest；<br>API声明：geofence: Geofence;<br>差异内容：geofence: Geofence;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface Geofence<br>差异内容：export interface Geofence|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Geofence；<br>API声明：latitude: number;<br>差异内容：latitude: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Geofence；<br>API声明：longitude: number;<br>差异内容：longitude: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Geofence；<br>API声明：radius: number;<br>差异内容：radius: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Geofence；<br>API声明：expiration: number;<br>差异内容：expiration: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface ReverseGeoCodeRequest<br>差异内容：export interface ReverseGeoCodeRequest|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：ReverseGeoCodeRequest；<br>API声明：locale?: string;<br>差异内容：locale?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：ReverseGeoCodeRequest；<br>API声明：latitude: number;<br>差异内容：latitude: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：ReverseGeoCodeRequest；<br>API声明：longitude: number;<br>差异内容：longitude: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：ReverseGeoCodeRequest；<br>API声明：maxItems?: number;<br>差异内容：maxItems?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface GeoCodeRequest<br>差异内容：export interface GeoCodeRequest|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoCodeRequest；<br>API声明：locale?: string;<br>差异内容：locale?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoCodeRequest；<br>API声明：description: string;<br>差异内容：description: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoCodeRequest；<br>API声明：maxItems?: number;<br>差异内容：maxItems?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoCodeRequest；<br>API声明：minLatitude?: number;<br>差异内容：minLatitude?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoCodeRequest；<br>API声明：minLongitude?: number;<br>差异内容：minLongitude?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoCodeRequest；<br>API声明：maxLatitude?: number;<br>差异内容：maxLatitude?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoCodeRequest；<br>API声明：maxLongitude?: number;<br>差异内容：maxLongitude?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface GeoAddress<br>差异内容：export interface GeoAddress|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：latitude?: number;<br>差异内容：latitude?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：longitude?: number;<br>差异内容：longitude?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：locale?: string;<br>差异内容：locale?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：placeName?: string;<br>差异内容：placeName?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：countryCode?: string;<br>差异内容：countryCode?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：countryName?: string;<br>差异内容：countryName?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：administrativeArea?: string;<br>差异内容：administrativeArea?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：subAdministrativeArea?: string;<br>差异内容：subAdministrativeArea?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：locality?: string;<br>差异内容：locality?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：subLocality?: string;<br>差异内容：subLocality?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：roadName?: string;<br>差异内容：roadName?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：subRoadName?: string;<br>差异内容：subRoadName?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：premises?: string;<br>差异内容：premises?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：postalCode?: string;<br>差异内容：postalCode?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：phoneNumber?: string;<br>差异内容：phoneNumber?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：addressUrl?: string;<br>差异内容：addressUrl?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：descriptions?: Array\<string>;<br>差异内容：descriptions?: Array\<string>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoAddress；<br>API声明：descriptionsSize?: number;<br>差异内容：descriptionsSize?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface LocationRequest<br>差异内容：export interface LocationRequest|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationRequest；<br>API声明：priority?: LocationRequestPriority;<br>差异内容：priority?: LocationRequestPriority;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationRequest；<br>API声明：scenario?: LocationRequestScenario;<br>差异内容：scenario?: LocationRequestScenario;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationRequest；<br>API声明：timeInterval?: number;<br>差异内容：timeInterval?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationRequest；<br>API声明：distanceInterval?: number;<br>差异内容：distanceInterval?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationRequest；<br>API声明：maxAccuracy?: number;<br>差异内容：maxAccuracy?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface CurrentLocationRequest<br>差异内容：export interface CurrentLocationRequest|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：CurrentLocationRequest；<br>API声明：priority?: LocationRequestPriority;<br>差异内容：priority?: LocationRequestPriority;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：CurrentLocationRequest；<br>API声明：scenario?: LocationRequestScenario;<br>差异内容：scenario?: LocationRequestScenario;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：CurrentLocationRequest；<br>API声明：maxAccuracy?: number;<br>差异内容：maxAccuracy?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：CurrentLocationRequest；<br>API声明：timeoutMs?: number;<br>差异内容：timeoutMs?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface Location<br>差异内容：export interface Location|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：latitude: number;<br>差异内容：latitude: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：longitude: number;<br>差异内容：longitude: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：altitude: number;<br>差异内容：altitude: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：accuracy: number;<br>差异内容：accuracy: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：speed: number;<br>差异内容：speed: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：timeStamp: number;<br>差异内容：timeStamp: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：direction: number;<br>差异内容：direction: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：timeSinceBoot: number;<br>差异内容：timeSinceBoot: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：additions?: Array\<string>;<br>差异内容：additions?: Array\<string>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：additionSize?: number;<br>差异内容：additionSize?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export enum LocationRequestPriority<br>差异内容：export enum LocationRequestPriority|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationRequestPriority；<br>API声明：UNSET = 0x200<br>差异内容：UNSET = 0x200|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationRequestPriority；<br>API声明：ACCURACY<br>差异内容：ACCURACY|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationRequestPriority；<br>API声明：LOW_POWER<br>差异内容：LOW_POWER|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationRequestPriority；<br>API声明：FIRST_FIX<br>差异内容：FIRST_FIX|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export enum LocationRequestScenario<br>差异内容：export enum LocationRequestScenario|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationRequestScenario；<br>API声明：UNSET = 0x300<br>差异内容：UNSET = 0x300|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationRequestScenario；<br>API声明：NAVIGATION<br>差异内容：NAVIGATION|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationRequestScenario；<br>API声明：TRAJECTORY_TRACKING<br>差异内容：TRAJECTORY_TRACKING|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationRequestScenario；<br>API声明：CAR_HAILING<br>差异内容：CAR_HAILING|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationRequestScenario；<br>API声明：DAILY_LIFE_SERVICE<br>差异内容：DAILY_LIFE_SERVICE|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationRequestScenario；<br>API声明：NO_POWER<br>差异内容：NO_POWER|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface LocationCommand<br>差异内容：export interface LocationCommand|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationCommand；<br>API声明：scenario: LocationRequestScenario;<br>差异内容：scenario: LocationRequestScenario;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationCommand；<br>API声明：command: string;<br>差异内容：command: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface CountryCode<br>差异内容：export interface CountryCode|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：CountryCode；<br>API声明：country: string;<br>差异内容：country: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：CountryCode；<br>API声明：type: CountryCodeType;<br>差异内容：type: CountryCodeType;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export enum CountryCodeType<br>差异内容：export enum CountryCodeType|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：CountryCodeType；<br>API声明：COUNTRY_CODE_FROM_LOCALE = 1<br>差异内容：COUNTRY_CODE_FROM_LOCALE = 1|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：CountryCodeType；<br>API声明：COUNTRY_CODE_FROM_SIM<br>差异内容：COUNTRY_CODE_FROM_SIM|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：CountryCodeType；<br>API声明：COUNTRY_CODE_FROM_LOCATION<br>差异内容：COUNTRY_CODE_FROM_LOCATION|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：CountryCodeType；<br>API声明：COUNTRY_CODE_FROM_NETWORK<br>差异内容：COUNTRY_CODE_FROM_NETWORK|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface GeolocationResponse<br>差异内容：export interface GeolocationResponse|api/@system.geolocation.d.ts|
|新增API|NA|类名：GeolocationResponse；<br>API声明：longitude: number;<br>差异内容：longitude: number;|api/@system.geolocation.d.ts|
|新增API|NA|类名：GeolocationResponse；<br>API声明：latitude: number;<br>差异内容：latitude: number;|api/@system.geolocation.d.ts|
|新增API|NA|类名：GeolocationResponse；<br>API声明：altitude: number;<br>差异内容：altitude: number;|api/@system.geolocation.d.ts|
|新增API|NA|类名：GeolocationResponse；<br>API声明：accuracy: number;<br>差异内容：accuracy: number;|api/@system.geolocation.d.ts|
|新增API|NA|类名：GeolocationResponse；<br>API声明：time: number;<br>差异内容：time: number;|api/@system.geolocation.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface GetLocationOption<br>差异内容：export interface GetLocationOption|api/@system.geolocation.d.ts|
|新增API|NA|类名：GetLocationOption；<br>API声明：timeout?: number;<br>差异内容：timeout?: number;|api/@system.geolocation.d.ts|
|新增API|NA|类名：GetLocationOption；<br>API声明：coordType?: string;<br>差异内容：coordType?: string;|api/@system.geolocation.d.ts|
|新增API|NA|类名：GetLocationOption；<br>API声明：success?: (data: GeolocationResponse) => void;<br>差异内容：success?: (data: GeolocationResponse) => void;|api/@system.geolocation.d.ts|
|新增API|NA|类名：GetLocationOption；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.geolocation.d.ts|
|新增API|NA|类名：GetLocationOption；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.geolocation.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface GetLocationTypeResponse<br>差异内容：export interface GetLocationTypeResponse|api/@system.geolocation.d.ts|
|新增API|NA|类名：GetLocationTypeResponse；<br>API声明：types: Array\<string>;<br>差异内容：types: Array\<string>;|api/@system.geolocation.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface GetLocationTypeOption<br>差异内容：export interface GetLocationTypeOption|api/@system.geolocation.d.ts|
|新增API|NA|类名：GetLocationTypeOption；<br>API声明：success?: (data: GetLocationTypeResponse) => void;<br>差异内容：success?: (data: GetLocationTypeResponse) => void;|api/@system.geolocation.d.ts|
|新增API|NA|类名：GetLocationTypeOption；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.geolocation.d.ts|
|新增API|NA|类名：GetLocationTypeOption；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.geolocation.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SubscribeLocationOption<br>差异内容：export interface SubscribeLocationOption|api/@system.geolocation.d.ts|
|新增API|NA|类名：SubscribeLocationOption；<br>API声明：coordType?: string;<br>差异内容：coordType?: string;|api/@system.geolocation.d.ts|
|新增API|NA|类名：SubscribeLocationOption；<br>API声明：success: (data: GeolocationResponse) => void;<br>差异内容：success: (data: GeolocationResponse) => void;|api/@system.geolocation.d.ts|
|新增API|NA|类名：SubscribeLocationOption；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.geolocation.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class Geolocation<br>差异内容：export default class Geolocation|api/@system.geolocation.d.ts|
|新增API|NA|类名：Geolocation；<br>API声明：static getLocation(options?: GetLocationOption): void;<br>差异内容：static getLocation(options?: GetLocationOption): void;|api/@system.geolocation.d.ts|
|新增API|NA|类名：Geolocation；<br>API声明：static getLocationType(options?: GetLocationTypeOption): void;<br>差异内容：static getLocationType(options?: GetLocationTypeOption): void;|api/@system.geolocation.d.ts|
|新增API|NA|类名：Geolocation；<br>API声明：static subscribe(options: SubscribeLocationOption): void;<br>差异内容：static subscribe(options: SubscribeLocationOption): void;|api/@system.geolocation.d.ts|
|新增API|NA|类名：Geolocation；<br>API声明：static unsubscribe(): void;<br>差异内容：static unsubscribe(): void;|api/@system.geolocation.d.ts|
|新增API|NA|类名：Geolocation；<br>API声明：static getSupportedCoordTypes(): Array\<string>;<br>差异内容：static getSupportedCoordTypes(): Array\<string>;|api/@system.geolocation.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.geolocation.d.ts<br>差异内容：LocationKit|api/@ohos.geolocation.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.geoLocationManager.d.ts<br>差异内容：LocationKit|api/@ohos.geoLocationManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@system.geolocation.d.ts<br>差异内容：LocationKit|api/@system.geolocation.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.LocationKit.d.ts<br>差异内容：LocationKit|kits/@kit.LocationKit.d.ts|
