| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|syscap change|Class name: global;<br>API declaration: declare namespace geoLocationManager<br>Differences: NA|Class name: global;<br>API declaration: declare namespace geoLocationManager<br>Differences: SystemCapability.Location.Location.Core|api/@ohos.geoLocationManager.d.ts|
|Function change|Class name: geoLocationManager;<br>API declaration: function on(type: 'locationChange', request: LocationRequest, callback: Callback\<Location>): void;<br>Differences: request: LocationRequest|Class name: geoLocationManager;<br>API declaration: function on(type: 'locationChange', request: LocationRequest \| ContinuousLocationRequest, callback: Callback\<Location>): void;<br>Differences: request: LocationRequest \| ContinuousLocationRequest|api/@ohos.geoLocationManager.d.ts|
|Function change|Class name: geoLocationManager;<br>API declaration: function getCurrentLocation(request: CurrentLocationRequest, callback: AsyncCallback\<Location>): void;<br>Differences: request: CurrentLocationRequest|Class name: geoLocationManager;<br>API declaration: function getCurrentLocation(request: CurrentLocationRequest \| SingleLocationRequest, callback: AsyncCallback\<Location>): void;<br>Differences: request: CurrentLocationRequest \| SingleLocationRequest|api/@ohos.geoLocationManager.d.ts|
|Function change|Class name: geoLocationManager;<br>API declaration: function getCurrentLocation(request?: CurrentLocationRequest): Promise\<Location>;<br>Differences: request?: CurrentLocationRequest|Class name: geoLocationManager;<br>API declaration: function getCurrentLocation(request?: CurrentLocationRequest \| SingleLocationRequest): Promise\<Location>;<br>Differences: request?: CurrentLocationRequest \| SingleLocationRequest|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: geoLocationManager;<br>API declaration: function on(type: 'locationError', callback: Callback\<LocationError>): void;<br>Differences: function on(type: 'locationError', callback: Callback\<LocationError>): void;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: geoLocationManager;<br>API declaration: function off(type: 'locationError', callback?: Callback\<LocationError>): void;<br>Differences: function off(type: 'locationError', callback?: Callback\<LocationError>): void;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: geoLocationManager;<br>API declaration: function addGnssGeofence(fenceRequest: GnssGeofenceRequest): Promise\<number>;<br>Differences: function addGnssGeofence(fenceRequest: GnssGeofenceRequest): Promise\<number>;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: geoLocationManager;<br>API declaration: function removeGnssGeofence(geofenceId: number): Promise\<void>;<br>Differences: function removeGnssGeofence(geofenceId: number): Promise\<void>;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: geoLocationManager;<br>API declaration: function getGeofenceSupportedCoordTypes(): Array\<CoordinateSystemType>;<br>Differences: function getGeofenceSupportedCoordTypes(): Array\<CoordinateSystemType>;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: SatelliteStatusInfo;<br>API declaration: satelliteConstellation?: Array\<SatelliteConstellationCategory>;<br>Differences: satelliteConstellation?: Array\<SatelliteConstellationCategory>;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: SatelliteStatusInfo;<br>API declaration: satelliteAdditionalInfo?: Array\<number>;<br>Differences: satelliteAdditionalInfo?: Array\<number>;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: geoLocationManager;<br>API declaration: export interface GnssGeofenceRequest<br>Differences: export interface GnssGeofenceRequest|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: GnssGeofenceRequest;<br>API declaration: geofence: Geofence;<br>Differences: geofence: Geofence;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: GnssGeofenceRequest;<br>API declaration: monitorTransitionEvents: Array\<GeofenceTransitionEvent>;<br>Differences: monitorTransitionEvents: Array\<GeofenceTransitionEvent>;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: GnssGeofenceRequest;<br>API declaration: notifications?: Array\<NotificationRequest>;<br>Differences: notifications?: Array\<NotificationRequest>;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: GnssGeofenceRequest;<br>API declaration: geofenceTransitionCallback: AsyncCallback\<GeofenceTransition>;<br>Differences: geofenceTransitionCallback: AsyncCallback\<GeofenceTransition>;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: Geofence;<br>API declaration: coordinateSystemType?: CoordinateSystemType;<br>Differences: coordinateSystemType?: CoordinateSystemType;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: ReverseGeoCodeRequest;<br>API declaration: country?: string;<br>Differences: country?: string;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: GeoCodeRequest;<br>API declaration: country?: string;<br>Differences: country?: string;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: geoLocationManager;<br>API declaration: export interface GeofenceTransition<br>Differences: export interface GeofenceTransition|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: GeofenceTransition;<br>API declaration: geofenceId: number;<br>Differences: geofenceId: number;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: GeofenceTransition;<br>API declaration: transitionEvent: GeofenceTransitionEvent;<br>Differences: transitionEvent: GeofenceTransitionEvent;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: geoLocationManager;<br>API declaration: export interface ContinuousLocationRequest<br>Differences: export interface ContinuousLocationRequest|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: ContinuousLocationRequest;<br>API declaration: interval: number;<br>Differences: interval: number;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: ContinuousLocationRequest;<br>API declaration: locationScenario: UserActivityScenario \| PowerConsumptionScenario;<br>Differences: locationScenario: UserActivityScenario \| PowerConsumptionScenario;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: geoLocationManager;<br>API declaration: export interface SingleLocationRequest<br>Differences: export interface SingleLocationRequest|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: SingleLocationRequest;<br>API declaration: locatingPriority: LocatingPriority;<br>Differences: locatingPriority: LocatingPriority;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: SingleLocationRequest;<br>API declaration: locatingTimeoutMs: number;<br>Differences: locatingTimeoutMs: number;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: Location;<br>API declaration: additionsMap?: Map\<string, string>;<br>Differences: additionsMap?: Map\<string, string>;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: Location;<br>API declaration: altitudeAccuracy?: number;<br>Differences: altitudeAccuracy?: number;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: Location;<br>API declaration: speedAccuracy?: number;<br>Differences: speedAccuracy?: number;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: Location;<br>API declaration: directionAccuracy?: number;<br>Differences: directionAccuracy?: number;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: Location;<br>API declaration: uncertaintyOfTimeSinceBoot?: number;<br>Differences: uncertaintyOfTimeSinceBoot?: number;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: Location;<br>API declaration: sourceType?: LocationSourceType;<br>Differences: sourceType?: LocationSourceType;|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: geoLocationManager;<br>API declaration: export enum LocationSourceType<br>Differences: export enum LocationSourceType|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: LocationSourceType;<br>API declaration: GNSS = 1<br>Differences: GNSS = 1|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: LocationSourceType;<br>API declaration: NETWORK = 2<br>Differences: NETWORK = 2|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: LocationSourceType;<br>API declaration: INDOOR = 3<br>Differences: INDOOR = 3|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: LocationSourceType;<br>API declaration: RTK = 4<br>Differences: RTK = 4|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: geoLocationManager;<br>API declaration: export enum CoordinateSystemType<br>Differences: export enum CoordinateSystemType|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: CoordinateSystemType;<br>API declaration: WGS84 = 1<br>Differences: WGS84 = 1|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: CoordinateSystemType;<br>API declaration: GCJ02 = 2<br>Differences: GCJ02 = 2|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: geoLocationManager;<br>API declaration: export enum LocationError<br>Differences: export enum LocationError|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: LocationError;<br>API declaration: LOCATING_FAILED_DEFAULT = -1<br>Differences: LOCATING_FAILED_DEFAULT = -1|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: LocationError;<br>API declaration: LOCATING_FAILED_LOCATION_PERMISSION_DENIED = -2<br>Differences: LOCATING_FAILED_LOCATION_PERMISSION_DENIED = -2|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: LocationError;<br>API declaration: LOCATING_FAILED_BACKGROUND_PERMISSION_DENIED = -3<br>Differences: LOCATING_FAILED_BACKGROUND_PERMISSION_DENIED = -3|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: LocationError;<br>API declaration: LOCATING_FAILED_LOCATION_SWITCH_OFF = -4<br>Differences: LOCATING_FAILED_LOCATION_SWITCH_OFF = -4|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: LocationError;<br>API declaration: LOCATING_FAILED_INTERNET_ACCESS_FAILURE = -5<br>Differences: LOCATING_FAILED_INTERNET_ACCESS_FAILURE = -5|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: geoLocationManager;<br>API declaration: export enum GeofenceTransitionEvent<br>Differences: export enum GeofenceTransitionEvent|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: GeofenceTransitionEvent;<br>API declaration: GEOFENCE_TRANSITION_EVENT_ENTER = 1<br>Differences: GEOFENCE_TRANSITION_EVENT_ENTER = 1|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: GeofenceTransitionEvent;<br>API declaration: GEOFENCE_TRANSITION_EVENT_EXIT = 2<br>Differences: GEOFENCE_TRANSITION_EVENT_EXIT = 2|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: GeofenceTransitionEvent;<br>API declaration: GEOFENCE_TRANSITION_EVENT_DWELL = 4<br>Differences: GEOFENCE_TRANSITION_EVENT_DWELL = 4|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: geoLocationManager;<br>API declaration: export enum SatelliteConstellationCategory<br>Differences: export enum SatelliteConstellationCategory|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: SatelliteConstellationCategory;<br>API declaration: CONSTELLATION_CATEGORY_UNKNOWN = 0<br>Differences: CONSTELLATION_CATEGORY_UNKNOWN = 0|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: SatelliteConstellationCategory;<br>API declaration: CONSTELLATION_CATEGORY_GPS = 1<br>Differences: CONSTELLATION_CATEGORY_GPS = 1|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: SatelliteConstellationCategory;<br>API declaration: CONSTELLATION_CATEGORY_SBAS = 2<br>Differences: CONSTELLATION_CATEGORY_SBAS = 2|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: SatelliteConstellationCategory;<br>API declaration: CONSTELLATION_CATEGORY_GLONASS = 3<br>Differences: CONSTELLATION_CATEGORY_GLONASS = 3|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: SatelliteConstellationCategory;<br>API declaration: CONSTELLATION_CATEGORY_QZSS = 4<br>Differences: CONSTELLATION_CATEGORY_QZSS = 4|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: SatelliteConstellationCategory;<br>API declaration: CONSTELLATION_CATEGORY_BEIDOU = 5<br>Differences: CONSTELLATION_CATEGORY_BEIDOU = 5|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: SatelliteConstellationCategory;<br>API declaration: CONSTELLATION_CATEGORY_GALILEO = 6<br>Differences: CONSTELLATION_CATEGORY_GALILEO = 6|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: SatelliteConstellationCategory;<br>API declaration: CONSTELLATION_CATEGORY_IRNSS = 7<br>Differences: CONSTELLATION_CATEGORY_IRNSS = 7|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: geoLocationManager;<br>API declaration: export enum SatelliteAdditionalInfo<br>Differences: export enum SatelliteAdditionalInfo|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: SatelliteAdditionalInfo;<br>API declaration: SATELLITES_ADDITIONAL_INFO_NULL = 0<br>Differences: SATELLITES_ADDITIONAL_INFO_NULL = 0|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: SatelliteAdditionalInfo;<br>API declaration: SATELLITES_ADDITIONAL_INFO_EPHEMERIS_DATA_EXIST = 1<br>Differences: SATELLITES_ADDITIONAL_INFO_EPHEMERIS_DATA_EXIST = 1|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: SatelliteAdditionalInfo;<br>API declaration: SATELLITES_ADDITIONAL_INFO_ALMANAC_DATA_EXIST = 2<br>Differences: SATELLITES_ADDITIONAL_INFO_ALMANAC_DATA_EXIST = 2|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: SatelliteAdditionalInfo;<br>API declaration: SATELLITES_ADDITIONAL_INFO_USED_IN_FIX = 4<br>Differences: SATELLITES_ADDITIONAL_INFO_USED_IN_FIX = 4|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: SatelliteAdditionalInfo;<br>API declaration: SATELLITES_ADDITIONAL_INFO_CARRIER_FREQUENCY_EXIST = 8<br>Differences: SATELLITES_ADDITIONAL_INFO_CARRIER_FREQUENCY_EXIST = 8|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: geoLocationManager;<br>API declaration: export enum UserActivityScenario<br>Differences: export enum UserActivityScenario|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: UserActivityScenario;<br>API declaration: NAVIGATION = 0x401<br>Differences: NAVIGATION = 0x401|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: UserActivityScenario;<br>API declaration: SPORT = 0x402<br>Differences: SPORT = 0x402|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: UserActivityScenario;<br>API declaration: TRANSPORT = 0x403<br>Differences: TRANSPORT = 0x403|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: UserActivityScenario;<br>API declaration: DAILY_LIFE_SERVICE = 0x404<br>Differences: DAILY_LIFE_SERVICE = 0x404|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: geoLocationManager;<br>API declaration: export enum LocatingPriority<br>Differences: export enum LocatingPriority|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: LocatingPriority;<br>API declaration: PRIORITY_ACCURACY = 0x501<br>Differences: PRIORITY_ACCURACY = 0x501|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: LocatingPriority;<br>API declaration: PRIORITY_LOCATING_SPEED = 0x502<br>Differences: PRIORITY_LOCATING_SPEED = 0x502|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: geoLocationManager;<br>API declaration: export enum PowerConsumptionScenario<br>Differences: export enum PowerConsumptionScenario|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: PowerConsumptionScenario;<br>API declaration: HIGH_POWER_CONSUMPTION = 0x601<br>Differences: HIGH_POWER_CONSUMPTION = 0x601|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: PowerConsumptionScenario;<br>API declaration: LOW_POWER_CONSUMPTION = 0x602<br>Differences: LOW_POWER_CONSUMPTION = 0x602|api/@ohos.geoLocationManager.d.ts|
|New API|NA|Class name: PowerConsumptionScenario;<br>API declaration: NO_POWER_CONSUMPTION = 0x603<br>Differences: NO_POWER_CONSUMPTION = 0x603|api/@ohos.geoLocationManager.d.ts|
