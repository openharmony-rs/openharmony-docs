| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace mechanicManager<br>差异内容：declare namespace mechanicManager|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：mechanicManager；<br>API声明：function on(type: 'attachStateChange', callback: Callback\<AttachStateChangeInfo>): void;<br>差异内容：function on(type: 'attachStateChange', callback: Callback\<AttachStateChangeInfo>): void;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：mechanicManager；<br>API声明：function off(type: 'attachStateChange', callback?: Callback\<AttachStateChangeInfo>): void;<br>差异内容：function off(type: 'attachStateChange', callback?: Callback\<AttachStateChangeInfo>): void;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：mechanicManager；<br>API声明：function getAttachedMechDevices(): MechInfo[];<br>差异内容：function getAttachedMechDevices(): MechInfo[];|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：mechanicManager；<br>API声明：function setCameraTrackingEnabled(isEnabled: boolean): void;<br>差异内容：function setCameraTrackingEnabled(isEnabled: boolean): void;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：mechanicManager；<br>API声明：function getCameraTrackingEnabled(): boolean;<br>差异内容：function getCameraTrackingEnabled(): boolean;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：mechanicManager；<br>API声明：function on(type: 'trackingStateChange', callback: Callback\<TrackingEventInfo>): void;<br>差异内容：function on(type: 'trackingStateChange', callback: Callback\<TrackingEventInfo>): void;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：mechanicManager；<br>API声明：function off(type: 'trackingStateChange', callback?: Callback\<TrackingEventInfo>): void;<br>差异内容：function off(type: 'trackingStateChange', callback?: Callback\<TrackingEventInfo>): void;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：mechanicManager；<br>API声明：function getCameraTrackingLayout(): CameraTrackingLayout;<br>差异内容：function getCameraTrackingLayout(): CameraTrackingLayout;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：mechanicManager；<br>API声明：export interface MechInfo<br>差异内容：export interface MechInfo|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：MechInfo；<br>API声明：mechId: number;<br>差异内容：mechId: number;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：MechInfo；<br>API声明：mechDeviceType: MechDeviceType;<br>差异内容：mechDeviceType: MechDeviceType;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：MechInfo；<br>API声明：mechName: string;<br>差异内容：mechName: string;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：mechanicManager；<br>API声明：export interface TrackingEventInfo<br>差异内容：export interface TrackingEventInfo|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：TrackingEventInfo；<br>API声明：event: TrackingEvent;<br>差异内容：event: TrackingEvent;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：mechanicManager；<br>API声明：export interface AttachStateChangeInfo<br>差异内容：export interface AttachStateChangeInfo|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：AttachStateChangeInfo；<br>API声明：state: AttachState;<br>差异内容：state: AttachState;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：AttachStateChangeInfo；<br>API声明：mechInfo: MechInfo;<br>差异内容：mechInfo: MechInfo;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：mechanicManager；<br>API声明：export enum TrackingEvent<br>差异内容：export enum TrackingEvent|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：TrackingEvent；<br>API声明：CAMERA_TRACKING_USER_ENABLED = 0<br>差异内容：CAMERA_TRACKING_USER_ENABLED = 0|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：TrackingEvent；<br>API声明：CAMERA_TRACKING_USER_DISABLED = 1<br>差异内容：CAMERA_TRACKING_USER_DISABLED = 1|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：TrackingEvent；<br>API声明：CAMERA_TRACKING_LAYOUT_CHANGED = 2<br>差异内容：CAMERA_TRACKING_LAYOUT_CHANGED = 2|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：mechanicManager；<br>API声明：export enum MechDeviceType<br>差异内容：export enum MechDeviceType|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：MechDeviceType；<br>API声明：GIMBAL_DEVICE = 0<br>差异内容：GIMBAL_DEVICE = 0|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：mechanicManager；<br>API声明：export enum AttachState<br>差异内容：export enum AttachState|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：AttachState；<br>API声明：ATTACHED = 0<br>差异内容：ATTACHED = 0|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：AttachState；<br>API声明：DETACHED = 1<br>差异内容：DETACHED = 1|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：mechanicManager；<br>API声明：export enum CameraTrackingLayout<br>差异内容：export enum CameraTrackingLayout|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：CameraTrackingLayout；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：CameraTrackingLayout；<br>API声明：LEFT = 1<br>差异内容：LEFT = 1|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：CameraTrackingLayout；<br>API声明：MIDDLE = 2<br>差异内容：MIDDLE = 2|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增API|NA|类名：CameraTrackingLayout；<br>API声明：RIGHT = 3<br>差异内容：RIGHT = 3|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.distributedHardware.mechanicManager.d.ts<br>差异内容：MechanicKit|api/@ohos.distributedHardware.mechanicManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.MechanicKit.d.ts<br>差异内容：MechanicKit|kits/@kit.MechanicKit.d.ts|
