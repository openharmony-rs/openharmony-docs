| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: global;<br>API declaration: declare namespace geolocation<br>Differences: declare namespace geolocation|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function on(type: 'locationChange', request: LocationRequest, callback: Callback\<Location>): void;<br>Differences: function on(type: 'locationChange', request: LocationRequest, callback: Callback\<Location>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function off(type: 'locationChange', callback?: Callback\<Location>): void;<br>Differences: function off(type: 'locationChange', callback?: Callback\<Location>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function on(type: 'locationServiceState', callback: Callback\<boolean>): void;<br>Differences: function on(type: 'locationServiceState', callback: Callback\<boolean>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function off(type: 'locationServiceState', callback?: Callback\<boolean>): void;<br>Differences: function off(type: 'locationServiceState', callback?: Callback\<boolean>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function on(type: 'cachedGnssLocationsReporting', request: CachedGnssLocationsRequest, callback: Callback\<Array\<Location>>): void;<br>Differences: function on(type: 'cachedGnssLocationsReporting', request: CachedGnssLocationsRequest, callback: Callback\<Array\<Location>>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function off(type: 'cachedGnssLocationsReporting', callback?: Callback\<Array\<Location>>): void;<br>Differences: function off(type: 'cachedGnssLocationsReporting', callback?: Callback\<Array\<Location>>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function on(type: 'gnssStatusChange', callback: Callback\<SatelliteStatusInfo>): void;<br>Differences: function on(type: 'gnssStatusChange', callback: Callback\<SatelliteStatusInfo>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function off(type: 'gnssStatusChange', callback?: Callback\<SatelliteStatusInfo>): void;<br>Differences: function off(type: 'gnssStatusChange', callback?: Callback\<SatelliteStatusInfo>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function on(type: 'nmeaMessageChange', callback: Callback\<string>): void;<br>Differences: function on(type: 'nmeaMessageChange', callback: Callback\<string>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function off(type: 'nmeaMessageChange', callback?: Callback\<string>): void;<br>Differences: function off(type: 'nmeaMessageChange', callback?: Callback\<string>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function on(type: 'fenceStatusChange', request: GeofenceRequest, want: WantAgent): void;<br>Differences: function on(type: 'fenceStatusChange', request: GeofenceRequest, want: WantAgent): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function off(type: 'fenceStatusChange', request: GeofenceRequest, want: WantAgent): void;<br>Differences: function off(type: 'fenceStatusChange', request: GeofenceRequest, want: WantAgent): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function getCurrentLocation(request: CurrentLocationRequest, callback: AsyncCallback\<Location>): void;<br>Differences: function getCurrentLocation(request: CurrentLocationRequest, callback: AsyncCallback\<Location>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function getCurrentLocation(callback: AsyncCallback\<Location>): void;<br>Differences: function getCurrentLocation(callback: AsyncCallback\<Location>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function getCurrentLocation(request?: CurrentLocationRequest): Promise\<Location>;<br>Differences: function getCurrentLocation(request?: CurrentLocationRequest): Promise\<Location>;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function getLastLocation(callback: AsyncCallback\<Location>): void;<br>Differences: function getLastLocation(callback: AsyncCallback\<Location>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function getLastLocation(): Promise\<Location>;<br>Differences: function getLastLocation(): Promise\<Location>;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function isLocationEnabled(callback: AsyncCallback\<boolean>): void;<br>Differences: function isLocationEnabled(callback: AsyncCallback\<boolean>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function isLocationEnabled(): Promise\<boolean>;<br>Differences: function isLocationEnabled(): Promise\<boolean>;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function requestEnableLocation(callback: AsyncCallback\<boolean>): void;<br>Differences: function requestEnableLocation(callback: AsyncCallback\<boolean>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function requestEnableLocation(): Promise\<boolean>;<br>Differences: function requestEnableLocation(): Promise\<boolean>;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function getAddressesFromLocation(request: ReverseGeoCodeRequest, callback: AsyncCallback\<Array\<GeoAddress>>): void;<br>Differences: function getAddressesFromLocation(request: ReverseGeoCodeRequest, callback: AsyncCallback\<Array\<GeoAddress>>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function getAddressesFromLocation(request: ReverseGeoCodeRequest): Promise\<Array\<GeoAddress>>;<br>Differences: function getAddressesFromLocation(request: ReverseGeoCodeRequest): Promise\<Array\<GeoAddress>>;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function getAddressesFromLocationName(request: GeoCodeRequest, callback: AsyncCallback\<Array\<GeoAddress>>): void;<br>Differences: function getAddressesFromLocationName(request: GeoCodeRequest, callback: AsyncCallback\<Array\<GeoAddress>>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function getAddressesFromLocationName(request: GeoCodeRequest): Promise\<Array\<GeoAddress>>;<br>Differences: function getAddressesFromLocationName(request: GeoCodeRequest): Promise\<Array\<GeoAddress>>;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function isGeoServiceAvailable(callback: AsyncCallback\<boolean>): void;<br>Differences: function isGeoServiceAvailable(callback: AsyncCallback\<boolean>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function isGeoServiceAvailable(): Promise\<boolean>;<br>Differences: function isGeoServiceAvailable(): Promise\<boolean>;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function getCachedGnssLocationsSize(callback: AsyncCallback\<number>): void;<br>Differences: function getCachedGnssLocationsSize(callback: AsyncCallback\<number>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function getCachedGnssLocationsSize(): Promise\<number>;<br>Differences: function getCachedGnssLocationsSize(): Promise\<number>;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function flushCachedGnssLocations(callback: AsyncCallback\<boolean>): void;<br>Differences: function flushCachedGnssLocations(callback: AsyncCallback\<boolean>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function flushCachedGnssLocations(): Promise\<boolean>;<br>Differences: function flushCachedGnssLocations(): Promise\<boolean>;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function sendCommand(command: LocationCommand, callback: AsyncCallback\<boolean>): void;<br>Differences: function sendCommand(command: LocationCommand, callback: AsyncCallback\<boolean>): void;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: function sendCommand(command: LocationCommand): Promise\<boolean>;<br>Differences: function sendCommand(command: LocationCommand): Promise\<boolean>;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: export interface SatelliteStatusInfo<br>Differences: export interface SatelliteStatusInfo|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: SatelliteStatusInfo;<br>API declaration: satellitesNumber: number;<br>Differences: satellitesNumber: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: SatelliteStatusInfo;<br>API declaration: satelliteIds: Array\<number>;<br>Differences: satelliteIds: Array\<number>;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: SatelliteStatusInfo;<br>API declaration: carrierToNoiseDensitys: Array\<number>;<br>Differences: carrierToNoiseDensitys: Array\<number>;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: SatelliteStatusInfo;<br>API declaration: altitudes: Array\<number>;<br>Differences: altitudes: Array\<number>;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: SatelliteStatusInfo;<br>API declaration: azimuths: Array\<number>;<br>Differences: azimuths: Array\<number>;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: SatelliteStatusInfo;<br>API declaration: carrierFrequencies: Array\<number>;<br>Differences: carrierFrequencies: Array\<number>;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: export interface CachedGnssLocationsRequest<br>Differences: export interface CachedGnssLocationsRequest|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: CachedGnssLocationsRequest;<br>API declaration: reportingPeriodSec: number;<br>Differences: reportingPeriodSec: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: CachedGnssLocationsRequest;<br>API declaration: wakeUpCacheQueueFull: boolean;<br>Differences: wakeUpCacheQueueFull: boolean;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: export interface GeofenceRequest<br>Differences: export interface GeofenceRequest|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeofenceRequest;<br>API declaration: priority: LocationRequestPriority;<br>Differences: priority: LocationRequestPriority;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeofenceRequest;<br>API declaration: scenario: LocationRequestScenario;<br>Differences: scenario: LocationRequestScenario;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeofenceRequest;<br>API declaration: geofence: Geofence;<br>Differences: geofence: Geofence;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: export interface Geofence<br>Differences: export interface Geofence|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: Geofence;<br>API declaration: latitude: number;<br>Differences: latitude: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: Geofence;<br>API declaration: longitude: number;<br>Differences: longitude: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: Geofence;<br>API declaration: radius: number;<br>Differences: radius: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: Geofence;<br>API declaration: expiration: number;<br>Differences: expiration: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: export interface ReverseGeoCodeRequest<br>Differences: export interface ReverseGeoCodeRequest|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: ReverseGeoCodeRequest;<br>API declaration: locale?: string;<br>Differences: locale?: string;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: ReverseGeoCodeRequest;<br>API declaration: latitude: number;<br>Differences: latitude: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: ReverseGeoCodeRequest;<br>API declaration: longitude: number;<br>Differences: longitude: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: ReverseGeoCodeRequest;<br>API declaration: maxItems?: number;<br>Differences: maxItems?: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: export interface GeoCodeRequest<br>Differences: export interface GeoCodeRequest|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoCodeRequest;<br>API declaration: locale?: string;<br>Differences: locale?: string;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoCodeRequest;<br>API declaration: description: string;<br>Differences: description: string;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoCodeRequest;<br>API declaration: maxItems?: number;<br>Differences: maxItems?: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoCodeRequest;<br>API declaration: minLatitude?: number;<br>Differences: minLatitude?: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoCodeRequest;<br>API declaration: minLongitude?: number;<br>Differences: minLongitude?: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoCodeRequest;<br>API declaration: maxLatitude?: number;<br>Differences: maxLatitude?: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoCodeRequest;<br>API declaration: maxLongitude?: number;<br>Differences: maxLongitude?: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: export interface GeoAddress<br>Differences: export interface GeoAddress|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: latitude?: number;<br>Differences: latitude?: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: longitude?: number;<br>Differences: longitude?: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: locale?: string;<br>Differences: locale?: string;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: placeName?: string;<br>Differences: placeName?: string;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: countryCode?: string;<br>Differences: countryCode?: string;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: countryName?: string;<br>Differences: countryName?: string;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: administrativeArea?: string;<br>Differences: administrativeArea?: string;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: subAdministrativeArea?: string;<br>Differences: subAdministrativeArea?: string;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: locality?: string;<br>Differences: locality?: string;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: subLocality?: string;<br>Differences: subLocality?: string;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: roadName?: string;<br>Differences: roadName?: string;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: subRoadName?: string;<br>Differences: subRoadName?: string;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: premises?: string;<br>Differences: premises?: string;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: postalCode?: string;<br>Differences: postalCode?: string;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: phoneNumber?: string;<br>Differences: phoneNumber?: string;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: addressUrl?: string;<br>Differences: addressUrl?: string;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: descriptions?: Array\<string>;<br>Differences: descriptions?: Array\<string>;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: descriptionsSize?: number;<br>Differences: descriptionsSize?: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: export interface LocationRequest<br>Differences: export interface LocationRequest|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationRequest;<br>API declaration: priority?: LocationRequestPriority;<br>Differences: priority?: LocationRequestPriority;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationRequest;<br>API declaration: scenario?: LocationRequestScenario;<br>Differences: scenario?: LocationRequestScenario;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationRequest;<br>API declaration: timeInterval?: number;<br>Differences: timeInterval?: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationRequest;<br>API declaration: distanceInterval?: number;<br>Differences: distanceInterval?: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationRequest;<br>API declaration: maxAccuracy?: number;<br>Differences: maxAccuracy?: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: export interface CurrentLocationRequest<br>Differences: export interface CurrentLocationRequest|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: CurrentLocationRequest;<br>API declaration: priority?: LocationRequestPriority;<br>Differences: priority?: LocationRequestPriority;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: CurrentLocationRequest;<br>API declaration: scenario?: LocationRequestScenario;<br>Differences: scenario?: LocationRequestScenario;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: CurrentLocationRequest;<br>API declaration: maxAccuracy?: number;<br>Differences: maxAccuracy?: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: CurrentLocationRequest;<br>API declaration: timeoutMs?: number;<br>Differences: timeoutMs?: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: export interface Location<br>Differences: export interface Location|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: Location;<br>API declaration: latitude: number;<br>Differences: latitude: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: Location;<br>API declaration: longitude: number;<br>Differences: longitude: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: Location;<br>API declaration: altitude: number;<br>Differences: altitude: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: Location;<br>API declaration: accuracy: number;<br>Differences: accuracy: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: Location;<br>API declaration: speed: number;<br>Differences: speed: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: Location;<br>API declaration: timeStamp: number;<br>Differences: timeStamp: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: Location;<br>API declaration: direction: number;<br>Differences: direction: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: Location;<br>API declaration: timeSinceBoot: number;<br>Differences: timeSinceBoot: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: Location;<br>API declaration: additions?: Array\<string>;<br>Differences: additions?: Array\<string>;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: Location;<br>API declaration: additionSize?: number;<br>Differences: additionSize?: number;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: export enum LocationRequestPriority<br>Differences: export enum LocationRequestPriority|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationRequestPriority;<br>API declaration: UNSET = 0x200<br>Differences: UNSET = 0x200|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationRequestPriority;<br>API declaration: ACCURACY<br>Differences: ACCURACY|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationRequestPriority;<br>API declaration: LOW_POWER<br>Differences: LOW_POWER|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationRequestPriority;<br>API declaration: FIRST_FIX<br>Differences: FIRST_FIX|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: export enum LocationRequestScenario<br>Differences: export enum LocationRequestScenario|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationRequestScenario;<br>API declaration: UNSET = 0x300<br>Differences: UNSET = 0x300|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationRequestScenario;<br>API declaration: NAVIGATION<br>Differences: NAVIGATION|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationRequestScenario;<br>API declaration: TRAJECTORY_TRACKING<br>Differences: TRAJECTORY_TRACKING|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationRequestScenario;<br>API declaration: CAR_HAILING<br>Differences: CAR_HAILING|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationRequestScenario;<br>API declaration: DAILY_LIFE_SERVICE<br>Differences: DAILY_LIFE_SERVICE|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationRequestScenario;<br>API declaration: NO_POWER<br>Differences: NO_POWER|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: export enum GeoLocationErrorCode<br>Differences: export enum GeoLocationErrorCode|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoLocationErrorCode;<br>API declaration: INPUT_PARAMS_ERROR<br>Differences: INPUT_PARAMS_ERROR|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoLocationErrorCode;<br>API declaration: REVERSE_GEOCODE_ERROR<br>Differences: REVERSE_GEOCODE_ERROR|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoLocationErrorCode;<br>API declaration: GEOCODE_ERROR<br>Differences: GEOCODE_ERROR|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoLocationErrorCode;<br>API declaration: LOCATOR_ERROR<br>Differences: LOCATOR_ERROR|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoLocationErrorCode;<br>API declaration: LOCATION_SWITCH_ERROR<br>Differences: LOCATION_SWITCH_ERROR|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoLocationErrorCode;<br>API declaration: LAST_KNOWN_LOCATION_ERROR<br>Differences: LAST_KNOWN_LOCATION_ERROR|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: GeoLocationErrorCode;<br>API declaration: LOCATION_REQUEST_TIMEOUT_ERROR<br>Differences: LOCATION_REQUEST_TIMEOUT_ERROR|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: export enum LocationPrivacyType<br>Differences: export enum LocationPrivacyType|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationPrivacyType;<br>API declaration: OTHERS = 0<br>Differences: OTHERS = 0|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationPrivacyType;<br>API declaration: STARTUP<br>Differences: STARTUP|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationPrivacyType;<br>API declaration: CORE_LOCATION<br>Differences: CORE_LOCATION|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: geolocation;<br>API declaration: export interface LocationCommand<br>Differences: export interface LocationCommand|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationCommand;<br>API declaration: scenario: LocationRequestScenario;<br>Differences: scenario: LocationRequestScenario;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: LocationCommand;<br>API declaration: command: string;<br>Differences: command: string;|api/@ohos.geolocation.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace geoLocationManager<br>Differences: declare namespace geoLocationManager|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function on(type: 'locationChange', request: LocationRequest, callback: Callback\<Location>): void;<br>Differences: function on(type: 'locationChange', request: LocationRequest, callback: Callback\<Location>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function off(type: 'locationChange', callback?: Callback\<Location>): void;<br>Differences: function off(type: 'locationChange', callback?: Callback\<Location>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function on(type: 'locationEnabledChange', callback: Callback\<boolean>): void;<br>Differences: function on(type: 'locationEnabledChange', callback: Callback\<boolean>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function off(type: 'locationEnabledChange', callback?: Callback\<boolean>): void;<br>Differences: function off(type: 'locationEnabledChange', callback?: Callback\<boolean>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function on(type: 'cachedGnssLocationsChange', request: CachedGnssLocationsRequest, callback: Callback\<Array\<Location>>): void;<br>Differences: function on(type: 'cachedGnssLocationsChange', request: CachedGnssLocationsRequest, callback: Callback\<Array\<Location>>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function off(type: 'cachedGnssLocationsChange', callback?: Callback\<Array\<Location>>): void;<br>Differences: function off(type: 'cachedGnssLocationsChange', callback?: Callback\<Array\<Location>>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function on(type: 'satelliteStatusChange', callback: Callback\<SatelliteStatusInfo>): void;<br>Differences: function on(type: 'satelliteStatusChange', callback: Callback\<SatelliteStatusInfo>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function off(type: 'satelliteStatusChange', callback?: Callback\<SatelliteStatusInfo>): void;<br>Differences: function off(type: 'satelliteStatusChange', callback?: Callback\<SatelliteStatusInfo>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function on(type: 'nmeaMessage', callback: Callback\<string>): void;<br>Differences: function on(type: 'nmeaMessage', callback: Callback\<string>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function off(type: 'nmeaMessage', callback?: Callback\<string>): void;<br>Differences: function off(type: 'nmeaMessage', callback?: Callback\<string>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function on(type: 'gnssFenceStatusChange', request: GeofenceRequest, want: WantAgent): void;<br>Differences: function on(type: 'gnssFenceStatusChange', request: GeofenceRequest, want: WantAgent): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function off(type: 'gnssFenceStatusChange', request: GeofenceRequest, want: WantAgent): void;<br>Differences: function off(type: 'gnssFenceStatusChange', request: GeofenceRequest, want: WantAgent): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function on(type: 'countryCodeChange', callback: Callback\<CountryCode>): void;<br>Differences: function on(type: 'countryCodeChange', callback: Callback\<CountryCode>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function off(type: 'countryCodeChange', callback?: Callback\<CountryCode>): void;<br>Differences: function off(type: 'countryCodeChange', callback?: Callback\<CountryCode>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function getCurrentLocation(request: CurrentLocationRequest, callback: AsyncCallback\<Location>): void;<br>Differences: function getCurrentLocation(request: CurrentLocationRequest, callback: AsyncCallback\<Location>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function getCurrentLocation(callback: AsyncCallback\<Location>): void;<br>Differences: function getCurrentLocation(callback: AsyncCallback\<Location>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function getCurrentLocation(request?: CurrentLocationRequest): Promise\<Location>;<br>Differences: function getCurrentLocation(request?: CurrentLocationRequest): Promise\<Location>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function getLastLocation(): Location;<br>Differences: function getLastLocation(): Location;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function isLocationEnabled(): boolean;<br>Differences: function isLocationEnabled(): boolean;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function getAddressesFromLocation(request: ReverseGeoCodeRequest, callback: AsyncCallback\<Array\<GeoAddress>>): void;<br>Differences: function getAddressesFromLocation(request: ReverseGeoCodeRequest, callback: AsyncCallback\<Array\<GeoAddress>>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function getAddressesFromLocation(request: ReverseGeoCodeRequest): Promise\<Array\<GeoAddress>>;<br>Differences: function getAddressesFromLocation(request: ReverseGeoCodeRequest): Promise\<Array\<GeoAddress>>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function getAddressesFromLocationName(request: GeoCodeRequest, callback: AsyncCallback\<Array\<GeoAddress>>): void;<br>Differences: function getAddressesFromLocationName(request: GeoCodeRequest, callback: AsyncCallback\<Array\<GeoAddress>>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function getAddressesFromLocationName(request: GeoCodeRequest): Promise\<Array\<GeoAddress>>;<br>Differences: function getAddressesFromLocationName(request: GeoCodeRequest): Promise\<Array\<GeoAddress>>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function isGeocoderAvailable(): boolean;<br>Differences: function isGeocoderAvailable(): boolean;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function getCachedGnssLocationsSize(callback: AsyncCallback\<number>): void;<br>Differences: function getCachedGnssLocationsSize(callback: AsyncCallback\<number>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function getCachedGnssLocationsSize(): Promise\<number>;<br>Differences: function getCachedGnssLocationsSize(): Promise\<number>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function flushCachedGnssLocations(callback: AsyncCallback\<void>): void;<br>Differences: function flushCachedGnssLocations(callback: AsyncCallback\<void>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function flushCachedGnssLocations(): Promise\<void>;<br>Differences: function flushCachedGnssLocations(): Promise\<void>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function sendCommand(command: LocationCommand, callback: AsyncCallback\<void>): void;<br>Differences: function sendCommand(command: LocationCommand, callback: AsyncCallback\<void>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function sendCommand(command: LocationCommand): Promise\<void>;<br>Differences: function sendCommand(command: LocationCommand): Promise\<void>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function getCountryCode(callback: AsyncCallback\<CountryCode>): void;<br>Differences: function getCountryCode(callback: AsyncCallback\<CountryCode>): void;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: function getCountryCode(): Promise\<CountryCode>;<br>Differences: function getCountryCode(): Promise\<CountryCode>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export interface SatelliteStatusInfo<br>Differences: export interface SatelliteStatusInfo|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: SatelliteStatusInfo;<br>API declaration: satellitesNumber: number;<br>Differences: satellitesNumber: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: SatelliteStatusInfo;<br>API declaration: satelliteIds: Array\<number>;<br>Differences: satelliteIds: Array\<number>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: SatelliteStatusInfo;<br>API declaration: carrierToNoiseDensitys: Array\<number>;<br>Differences: carrierToNoiseDensitys: Array\<number>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: SatelliteStatusInfo;<br>API declaration: altitudes: Array\<number>;<br>Differences: altitudes: Array\<number>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: SatelliteStatusInfo;<br>API declaration: azimuths: Array\<number>;<br>Differences: azimuths: Array\<number>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: SatelliteStatusInfo;<br>API declaration: carrierFrequencies: Array\<number>;<br>Differences: carrierFrequencies: Array\<number>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export interface CachedGnssLocationsRequest<br>Differences: export interface CachedGnssLocationsRequest|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: CachedGnssLocationsRequest;<br>API declaration: reportingPeriodSec: number;<br>Differences: reportingPeriodSec: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: CachedGnssLocationsRequest;<br>API declaration: wakeUpCacheQueueFull: boolean;<br>Differences: wakeUpCacheQueueFull: boolean;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export interface GeofenceRequest<br>Differences: export interface GeofenceRequest|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeofenceRequest;<br>API declaration: scenario: LocationRequestScenario;<br>Differences: scenario: LocationRequestScenario;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeofenceRequest;<br>API declaration: geofence: Geofence;<br>Differences: geofence: Geofence;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export interface Geofence<br>Differences: export interface Geofence|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Geofence;<br>API declaration: latitude: number;<br>Differences: latitude: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Geofence;<br>API declaration: longitude: number;<br>Differences: longitude: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Geofence;<br>API declaration: radius: number;<br>Differences: radius: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Geofence;<br>API declaration: expiration: number;<br>Differences: expiration: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export interface ReverseGeoCodeRequest<br>Differences: export interface ReverseGeoCodeRequest|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: ReverseGeoCodeRequest;<br>API declaration: locale?: string;<br>Differences: locale?: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: ReverseGeoCodeRequest;<br>API declaration: latitude: number;<br>Differences: latitude: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: ReverseGeoCodeRequest;<br>API declaration: longitude: number;<br>Differences: longitude: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: ReverseGeoCodeRequest;<br>API declaration: maxItems?: number;<br>Differences: maxItems?: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export interface GeoCodeRequest<br>Differences: export interface GeoCodeRequest|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoCodeRequest;<br>API declaration: locale?: string;<br>Differences: locale?: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoCodeRequest;<br>API declaration: description: string;<br>Differences: description: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoCodeRequest;<br>API declaration: maxItems?: number;<br>Differences: maxItems?: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoCodeRequest;<br>API declaration: minLatitude?: number;<br>Differences: minLatitude?: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoCodeRequest;<br>API declaration: minLongitude?: number;<br>Differences: minLongitude?: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoCodeRequest;<br>API declaration: maxLatitude?: number;<br>Differences: maxLatitude?: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoCodeRequest;<br>API declaration: maxLongitude?: number;<br>Differences: maxLongitude?: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export interface GeoAddress<br>Differences: export interface GeoAddress|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: latitude?: number;<br>Differences: latitude?: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: longitude?: number;<br>Differences: longitude?: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: locale?: string;<br>Differences: locale?: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: placeName?: string;<br>Differences: placeName?: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: countryCode?: string;<br>Differences: countryCode?: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: countryName?: string;<br>Differences: countryName?: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: administrativeArea?: string;<br>Differences: administrativeArea?: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: subAdministrativeArea?: string;<br>Differences: subAdministrativeArea?: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: locality?: string;<br>Differences: locality?: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: subLocality?: string;<br>Differences: subLocality?: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: roadName?: string;<br>Differences: roadName?: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: subRoadName?: string;<br>Differences: subRoadName?: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: premises?: string;<br>Differences: premises?: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: postalCode?: string;<br>Differences: postalCode?: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: phoneNumber?: string;<br>Differences: phoneNumber?: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: addressUrl?: string;<br>Differences: addressUrl?: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: descriptions?: Array\<string>;<br>Differences: descriptions?: Array\<string>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: GeoAddress;<br>API declaration: descriptionsSize?: number;<br>Differences: descriptionsSize?: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export interface LocationRequest<br>Differences: export interface LocationRequest|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: LocationRequest;<br>API declaration: priority?: LocationRequestPriority;<br>Differences: priority?: LocationRequestPriority;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: LocationRequest;<br>API declaration: scenario?: LocationRequestScenario;<br>Differences: scenario?: LocationRequestScenario;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: LocationRequest;<br>API declaration: timeInterval?: number;<br>Differences: timeInterval?: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: LocationRequest;<br>API declaration: distanceInterval?: number;<br>Differences: distanceInterval?: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: LocationRequest;<br>API declaration: maxAccuracy?: number;<br>Differences: maxAccuracy?: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export interface CurrentLocationRequest<br>Differences: export interface CurrentLocationRequest|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: CurrentLocationRequest;<br>API declaration: priority?: LocationRequestPriority;<br>Differences: priority?: LocationRequestPriority;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: CurrentLocationRequest;<br>API declaration: scenario?: LocationRequestScenario;<br>Differences: scenario?: LocationRequestScenario;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: CurrentLocationRequest;<br>API declaration: maxAccuracy?: number;<br>Differences: maxAccuracy?: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: CurrentLocationRequest;<br>API declaration: timeoutMs?: number;<br>Differences: timeoutMs?: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export interface Location<br>Differences: export interface Location|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Location;<br>API declaration: latitude: number;<br>Differences: latitude: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Location;<br>API declaration: longitude: number;<br>Differences: longitude: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Location;<br>API declaration: altitude: number;<br>Differences: altitude: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Location;<br>API declaration: accuracy: number;<br>Differences: accuracy: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Location;<br>API declaration: speed: number;<br>Differences: speed: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Location;<br>API declaration: timeStamp: number;<br>Differences: timeStamp: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Location;<br>API declaration: direction: number;<br>Differences: direction: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Location;<br>API declaration: timeSinceBoot: number;<br>Differences: timeSinceBoot: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Location;<br>API declaration: additions?: Array\<string>;<br>Differences: additions?: Array\<string>;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: Location;<br>API declaration: additionSize?: number;<br>Differences: additionSize?: number;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export enum LocationRequestPriority<br>Differences: export enum LocationRequestPriority|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: LocationRequestPriority;<br>API declaration: UNSET = 0x200<br>Differences: UNSET = 0x200|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: LocationRequestPriority;<br>API declaration: ACCURACY<br>Differences: ACCURACY|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: LocationRequestPriority;<br>API declaration: LOW_POWER<br>Differences: LOW_POWER|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: LocationRequestPriority;<br>API declaration: FIRST_FIX<br>Differences: FIRST_FIX|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export enum LocationRequestScenario<br>Differences: export enum LocationRequestScenario|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: LocationRequestScenario;<br>API declaration: UNSET = 0x300<br>Differences: UNSET = 0x300|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: LocationRequestScenario;<br>API declaration: NAVIGATION<br>Differences: NAVIGATION|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: LocationRequestScenario;<br>API declaration: TRAJECTORY_TRACKING<br>Differences: TRAJECTORY_TRACKING|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: LocationRequestScenario;<br>API declaration: CAR_HAILING<br>Differences: CAR_HAILING|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: LocationRequestScenario;<br>API declaration: DAILY_LIFE_SERVICE<br>Differences: DAILY_LIFE_SERVICE|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: LocationRequestScenario;<br>API declaration: NO_POWER<br>Differences: NO_POWER|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export interface LocationCommand<br>Differences: export interface LocationCommand|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: LocationCommand;<br>API declaration: scenario: LocationRequestScenario;<br>Differences: scenario: LocationRequestScenario;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: LocationCommand;<br>API declaration: command: string;<br>Differences: command: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export interface CountryCode<br>Differences: export interface CountryCode|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: CountryCode;<br>API declaration: country: string;<br>Differences: country: string;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: CountryCode;<br>API declaration: type: CountryCodeType;<br>Differences: type: CountryCodeType;|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: geoLocationManager;<br>API declaration: export enum CountryCodeType<br>Differences: export enum CountryCodeType|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: CountryCodeType;<br>API declaration: COUNTRY_CODE_FROM_LOCALE = 1<br>Differences: COUNTRY_CODE_FROM_LOCALE = 1|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: CountryCodeType;<br>API declaration: COUNTRY_CODE_FROM_SIM<br>Differences: COUNTRY_CODE_FROM_SIM|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: CountryCodeType;<br>API declaration: COUNTRY_CODE_FROM_LOCATION<br>Differences: COUNTRY_CODE_FROM_LOCATION|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: CountryCodeType;<br>API declaration: COUNTRY_CODE_FROM_NETWORK<br>Differences: COUNTRY_CODE_FROM_NETWORK|api/@ohos.geoLocationManager.d.ts|
|New API |NA|Class name: global;<br>API declaration: export interface GeolocationResponse<br>Differences: export interface GeolocationResponse|api/@system.geolocation.d.ts|
|New API |NA|Class name: GeolocationResponse;<br>API declaration: longitude: number;<br>Differences: longitude: number;|api/@system.geolocation.d.ts|
|New API |NA|Class name: GeolocationResponse;<br>API declaration: latitude: number;<br>Differences: latitude: number;|api/@system.geolocation.d.ts|
|New API |NA|Class name: GeolocationResponse;<br>API declaration: altitude: number;<br>Differences: altitude: number;|api/@system.geolocation.d.ts|
|New API |NA|Class name: GeolocationResponse;<br>API declaration: accuracy: number;<br>Differences: accuracy: number;|api/@system.geolocation.d.ts|
|New API |NA|Class name: GeolocationResponse;<br>API declaration: time: number;<br>Differences: time: number;|api/@system.geolocation.d.ts|
|New API |NA|Class name: global;<br>API declaration: export interface GetLocationOption<br>Differences: export interface GetLocationOption|api/@system.geolocation.d.ts|
|New API |NA|Class name: GetLocationOption;<br>API declaration: timeout?: number;<br>Differences: timeout?: number;|api/@system.geolocation.d.ts|
|New API |NA|Class name: GetLocationOption;<br>API declaration: coordType?: string;<br>Differences: coordType?: string;|api/@system.geolocation.d.ts|
|New API |NA|Class name: GetLocationOption;<br>API declaration: success?: (data: GeolocationResponse) => void;<br>Differences: success?: (data: GeolocationResponse) => void;|api/@system.geolocation.d.ts|
|New API |NA|Class name: GetLocationOption;<br>API declaration: fail?: (data: string, code: number) => void;<br>Differences: fail?: (data: string, code: number) => void;|api/@system.geolocation.d.ts|
|New API |NA|Class name: GetLocationOption;<br>API declaration: complete?: () => void;<br>Differences: complete?: () => void;|api/@system.geolocation.d.ts|
|New API |NA|Class name: global;<br>API declaration: export interface GetLocationTypeResponse<br>Differences: export interface GetLocationTypeResponse|api/@system.geolocation.d.ts|
|New API |NA|Class name: GetLocationTypeResponse;<br>API declaration: types: Array\<string>;<br>Differences: types: Array\<string>;|api/@system.geolocation.d.ts|
|New API |NA|Class name: global;<br>API declaration: export interface GetLocationTypeOption<br>Differences: export interface GetLocationTypeOption|api/@system.geolocation.d.ts|
|New API |NA|Class name: GetLocationTypeOption;<br>API declaration: success?: (data: GetLocationTypeResponse) => void;<br>Differences: success?: (data: GetLocationTypeResponse) => void;|api/@system.geolocation.d.ts|
|New API |NA|Class name: GetLocationTypeOption;<br>API declaration: fail?: (data: string, code: number) => void;<br>Differences: fail?: (data: string, code: number) => void;|api/@system.geolocation.d.ts|
|New API |NA|Class name: GetLocationTypeOption;<br>API declaration: complete?: () => void;<br>Differences: complete?: () => void;|api/@system.geolocation.d.ts|
|New API |NA|Class name: global;<br>API declaration: export interface SubscribeLocationOption<br>Differences: export interface SubscribeLocationOption|api/@system.geolocation.d.ts|
|New API |NA|Class name: SubscribeLocationOption;<br>API declaration: coordType?: string;<br>Differences: coordType?: string;|api/@system.geolocation.d.ts|
|New API |NA|Class name: SubscribeLocationOption;<br>API declaration: success: (data: GeolocationResponse) => void;<br>Differences: success: (data: GeolocationResponse) => void;|api/@system.geolocation.d.ts|
|New API |NA|Class name: SubscribeLocationOption;<br>API declaration: fail?: (data: string, code: number) => void;<br>Differences: fail?: (data: string, code: number) => void;|api/@system.geolocation.d.ts|
|New API |NA|Class name: global;<br>API declaration: export default class Geolocation<br>Differences: export default class Geolocation|api/@system.geolocation.d.ts|
|New API |NA|Class name: Geolocation;<br>API declaration: static getLocation(options?: GetLocationOption): void;<br>Differences: static getLocation(options?: GetLocationOption): void;|api/@system.geolocation.d.ts|
|New API |NA|Class name: Geolocation;<br>API declaration: static getLocationType(options?: GetLocationTypeOption): void;<br>Differences: static getLocationType(options?: GetLocationTypeOption): void;|api/@system.geolocation.d.ts|
|New API |NA|Class name: Geolocation;<br>API declaration: static subscribe(options: SubscribeLocationOption): void;<br>Differences: static subscribe(options: SubscribeLocationOption): void;|api/@system.geolocation.d.ts|
|New API |NA|Class name: Geolocation;<br>API declaration: static unsubscribe(): void;<br>Differences: static unsubscribe(): void;|api/@system.geolocation.d.ts|
|New API |NA|Class name: Geolocation;<br>API declaration: static getSupportedCoordTypes(): Array\<string>;<br>Differences: static getSupportedCoordTypes(): Array\<string>;|api/@system.geolocation.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.geolocation.d.ts<br>Differences: LocationKit|api/@ohos.geolocation.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.geoLocationManager.d.ts<br>Differences: LocationKit|api/@ohos.geoLocationManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@system.geolocation.d.ts<br>Differences: LocationKit|api/@system.geolocation.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.LocationKit.d.ts<br>Differences: LocationKit|kits/@kit.LocationKit.d.ts|
