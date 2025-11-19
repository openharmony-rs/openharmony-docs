| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|syscap变更|类名：global；<br>API声明：declare namespace geoLocationManager<br>差异内容：NA|类名：global；<br>API声明：declare namespace geoLocationManager<br>差异内容：SystemCapability.Location.Location.Core|api/@ohos.geoLocationManager.d.ts|
|函数变更|类名：geoLocationManager；<br>API声明：function on(type: 'locationChange', request: LocationRequest, callback: Callback\<Location>): void;<br>差异内容：request: LocationRequest|类名：geoLocationManager；<br>API声明：function on(type: 'locationChange', request: LocationRequest \| ContinuousLocationRequest, callback: Callback\<Location>): void;<br>差异内容：request: LocationRequest \| ContinuousLocationRequest|api/@ohos.geoLocationManager.d.ts|
|函数变更|类名：geoLocationManager；<br>API声明：function getCurrentLocation(request: CurrentLocationRequest, callback: AsyncCallback\<Location>): void;<br>差异内容：request: CurrentLocationRequest|类名：geoLocationManager；<br>API声明：function getCurrentLocation(request: CurrentLocationRequest \| SingleLocationRequest, callback: AsyncCallback\<Location>): void;<br>差异内容：request: CurrentLocationRequest \| SingleLocationRequest|api/@ohos.geoLocationManager.d.ts|
|函数变更|类名：geoLocationManager；<br>API声明：function getCurrentLocation(request?: CurrentLocationRequest): Promise\<Location>;<br>差异内容：request?: CurrentLocationRequest|类名：geoLocationManager；<br>API声明：function getCurrentLocation(request?: CurrentLocationRequest \| SingleLocationRequest): Promise\<Location>;<br>差异内容：request?: CurrentLocationRequest \| SingleLocationRequest|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function on(type: 'locationError', callback: Callback\<LocationError>): void;<br>差异内容：function on(type: 'locationError', callback: Callback\<LocationError>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function off(type: 'locationError', callback?: Callback\<LocationError>): void;<br>差异内容：function off(type: 'locationError', callback?: Callback\<LocationError>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function addGnssGeofence(fenceRequest: GnssGeofenceRequest): Promise\<number>;<br>差异内容：function addGnssGeofence(fenceRequest: GnssGeofenceRequest): Promise\<number>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function removeGnssGeofence(geofenceId: number): Promise\<void>;<br>差异内容：function removeGnssGeofence(geofenceId: number): Promise\<void>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function getGeofenceSupportedCoordTypes(): Array\<CoordinateSystemType>;<br>差异内容：function getGeofenceSupportedCoordTypes(): Array\<CoordinateSystemType>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteStatusInfo；<br>API声明：satelliteConstellation?: Array\<SatelliteConstellationCategory>;<br>差异内容：satelliteConstellation?: Array\<SatelliteConstellationCategory>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteStatusInfo；<br>API声明：satelliteAdditionalInfo?: Array\<number>;<br>差异内容：satelliteAdditionalInfo?: Array\<number>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface GnssGeofenceRequest<br>差异内容：export interface GnssGeofenceRequest|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GnssGeofenceRequest；<br>API声明：geofence: Geofence;<br>差异内容：geofence: Geofence;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GnssGeofenceRequest；<br>API声明：monitorTransitionEvents: Array\<GeofenceTransitionEvent>;<br>差异内容：monitorTransitionEvents: Array\<GeofenceTransitionEvent>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GnssGeofenceRequest；<br>API声明：notifications?: Array\<NotificationRequest>;<br>差异内容：notifications?: Array\<NotificationRequest>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GnssGeofenceRequest；<br>API声明：geofenceTransitionCallback: AsyncCallback\<GeofenceTransition>;<br>差异内容：geofenceTransitionCallback: AsyncCallback\<GeofenceTransition>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Geofence；<br>API声明：coordinateSystemType?: CoordinateSystemType;<br>差异内容：coordinateSystemType?: CoordinateSystemType;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：ReverseGeoCodeRequest；<br>API声明：country?: string;<br>差异内容：country?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeoCodeRequest；<br>API声明：country?: string;<br>差异内容：country?: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface GeofenceTransition<br>差异内容：export interface GeofenceTransition|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeofenceTransition；<br>API声明：geofenceId: number;<br>差异内容：geofenceId: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeofenceTransition；<br>API声明：transitionEvent: GeofenceTransitionEvent;<br>差异内容：transitionEvent: GeofenceTransitionEvent;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface ContinuousLocationRequest<br>差异内容：export interface ContinuousLocationRequest|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：ContinuousLocationRequest；<br>API声明：interval: number;<br>差异内容：interval: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：ContinuousLocationRequest；<br>API声明：locationScenario: UserActivityScenario \| PowerConsumptionScenario;<br>差异内容：locationScenario: UserActivityScenario \| PowerConsumptionScenario;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface SingleLocationRequest<br>差异内容：export interface SingleLocationRequest|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SingleLocationRequest；<br>API声明：locatingPriority: LocatingPriority;<br>差异内容：locatingPriority: LocatingPriority;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SingleLocationRequest；<br>API声明：locatingTimeoutMs: number;<br>差异内容：locatingTimeoutMs: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：additionsMap?: Map\<string, string>;<br>差异内容：additionsMap?: Map\<string, string>;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：altitudeAccuracy?: number;<br>差异内容：altitudeAccuracy?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：speedAccuracy?: number;<br>差异内容：speedAccuracy?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：directionAccuracy?: number;<br>差异内容：directionAccuracy?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：uncertaintyOfTimeSinceBoot?: number;<br>差异内容：uncertaintyOfTimeSinceBoot?: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：sourceType?: LocationSourceType;<br>差异内容：sourceType?: LocationSourceType;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export enum LocationSourceType<br>差异内容：export enum LocationSourceType|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationSourceType；<br>API声明：GNSS = 1<br>差异内容：GNSS = 1|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationSourceType；<br>API声明：NETWORK = 2<br>差异内容：NETWORK = 2|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationSourceType；<br>API声明：INDOOR = 3<br>差异内容：INDOOR = 3|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationSourceType；<br>API声明：RTK = 4<br>差异内容：RTK = 4|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export enum CoordinateSystemType<br>差异内容：export enum CoordinateSystemType|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：CoordinateSystemType；<br>API声明：WGS84 = 1<br>差异内容：WGS84 = 1|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：CoordinateSystemType；<br>API声明：GCJ02 = 2<br>差异内容：GCJ02 = 2|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export enum LocationError<br>差异内容：export enum LocationError|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationError；<br>API声明：LOCATING_FAILED_DEFAULT = -1<br>差异内容：LOCATING_FAILED_DEFAULT = -1|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationError；<br>API声明：LOCATING_FAILED_LOCATION_PERMISSION_DENIED = -2<br>差异内容：LOCATING_FAILED_LOCATION_PERMISSION_DENIED = -2|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationError；<br>API声明：LOCATING_FAILED_BACKGROUND_PERMISSION_DENIED = -3<br>差异内容：LOCATING_FAILED_BACKGROUND_PERMISSION_DENIED = -3|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationError；<br>API声明：LOCATING_FAILED_LOCATION_SWITCH_OFF = -4<br>差异内容：LOCATING_FAILED_LOCATION_SWITCH_OFF = -4|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocationError；<br>API声明：LOCATING_FAILED_INTERNET_ACCESS_FAILURE = -5<br>差异内容：LOCATING_FAILED_INTERNET_ACCESS_FAILURE = -5|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export enum GeofenceTransitionEvent<br>差异内容：export enum GeofenceTransitionEvent|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeofenceTransitionEvent；<br>API声明：GEOFENCE_TRANSITION_EVENT_ENTER = 1<br>差异内容：GEOFENCE_TRANSITION_EVENT_ENTER = 1|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeofenceTransitionEvent；<br>API声明：GEOFENCE_TRANSITION_EVENT_EXIT = 2<br>差异内容：GEOFENCE_TRANSITION_EVENT_EXIT = 2|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：GeofenceTransitionEvent；<br>API声明：GEOFENCE_TRANSITION_EVENT_DWELL = 4<br>差异内容：GEOFENCE_TRANSITION_EVENT_DWELL = 4|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export enum SatelliteConstellationCategory<br>差异内容：export enum SatelliteConstellationCategory|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteConstellationCategory；<br>API声明：CONSTELLATION_CATEGORY_UNKNOWN = 0<br>差异内容：CONSTELLATION_CATEGORY_UNKNOWN = 0|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteConstellationCategory；<br>API声明：CONSTELLATION_CATEGORY_GPS = 1<br>差异内容：CONSTELLATION_CATEGORY_GPS = 1|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteConstellationCategory；<br>API声明：CONSTELLATION_CATEGORY_SBAS = 2<br>差异内容：CONSTELLATION_CATEGORY_SBAS = 2|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteConstellationCategory；<br>API声明：CONSTELLATION_CATEGORY_GLONASS = 3<br>差异内容：CONSTELLATION_CATEGORY_GLONASS = 3|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteConstellationCategory；<br>API声明：CONSTELLATION_CATEGORY_QZSS = 4<br>差异内容：CONSTELLATION_CATEGORY_QZSS = 4|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteConstellationCategory；<br>API声明：CONSTELLATION_CATEGORY_BEIDOU = 5<br>差异内容：CONSTELLATION_CATEGORY_BEIDOU = 5|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteConstellationCategory；<br>API声明：CONSTELLATION_CATEGORY_GALILEO = 6<br>差异内容：CONSTELLATION_CATEGORY_GALILEO = 6|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteConstellationCategory；<br>API声明：CONSTELLATION_CATEGORY_IRNSS = 7<br>差异内容：CONSTELLATION_CATEGORY_IRNSS = 7|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export enum SatelliteAdditionalInfo<br>差异内容：export enum SatelliteAdditionalInfo|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteAdditionalInfo；<br>API声明：SATELLITES_ADDITIONAL_INFO_NULL = 0<br>差异内容：SATELLITES_ADDITIONAL_INFO_NULL = 0|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteAdditionalInfo；<br>API声明：SATELLITES_ADDITIONAL_INFO_EPHEMERIS_DATA_EXIST = 1<br>差异内容：SATELLITES_ADDITIONAL_INFO_EPHEMERIS_DATA_EXIST = 1|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteAdditionalInfo；<br>API声明：SATELLITES_ADDITIONAL_INFO_ALMANAC_DATA_EXIST = 2<br>差异内容：SATELLITES_ADDITIONAL_INFO_ALMANAC_DATA_EXIST = 2|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteAdditionalInfo；<br>API声明：SATELLITES_ADDITIONAL_INFO_USED_IN_FIX = 4<br>差异内容：SATELLITES_ADDITIONAL_INFO_USED_IN_FIX = 4|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SatelliteAdditionalInfo；<br>API声明：SATELLITES_ADDITIONAL_INFO_CARRIER_FREQUENCY_EXIST = 8<br>差异内容：SATELLITES_ADDITIONAL_INFO_CARRIER_FREQUENCY_EXIST = 8|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export enum UserActivityScenario<br>差异内容：export enum UserActivityScenario|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：UserActivityScenario；<br>API声明：NAVIGATION = 0x401<br>差异内容：NAVIGATION = 0x401|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：UserActivityScenario；<br>API声明：SPORT = 0x402<br>差异内容：SPORT = 0x402|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：UserActivityScenario；<br>API声明：TRANSPORT = 0x403<br>差异内容：TRANSPORT = 0x403|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：UserActivityScenario；<br>API声明：DAILY_LIFE_SERVICE = 0x404<br>差异内容：DAILY_LIFE_SERVICE = 0x404|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export enum LocatingPriority<br>差异内容：export enum LocatingPriority|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocatingPriority；<br>API声明：PRIORITY_ACCURACY = 0x501<br>差异内容：PRIORITY_ACCURACY = 0x501|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：LocatingPriority；<br>API声明：PRIORITY_LOCATING_SPEED = 0x502<br>差异内容：PRIORITY_LOCATING_SPEED = 0x502|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export enum PowerConsumptionScenario<br>差异内容：export enum PowerConsumptionScenario|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：PowerConsumptionScenario；<br>API声明：HIGH_POWER_CONSUMPTION = 0x601<br>差异内容：HIGH_POWER_CONSUMPTION = 0x601|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：PowerConsumptionScenario；<br>API声明：LOW_POWER_CONSUMPTION = 0x602<br>差异内容：LOW_POWER_CONSUMPTION = 0x602|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：PowerConsumptionScenario；<br>API声明：NO_POWER_CONSUMPTION = 0x603<br>差异内容：NO_POWER_CONSUMPTION = 0x603|api/@ohos.geoLocationManager.d.ts|
