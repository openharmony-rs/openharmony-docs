| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: global;<br>API declaration: declare namespace mechanicManager<br>DIfferences: declare namespace mechanicManager|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: mechanicManager;<br>API declaration: function on(type: 'attachStateChange', callback: Callback\<AttachStateChangeInfo>): void;<br>DIfferences: function on(type: 'attachStateChange', callback: Callback\<AttachStateChangeInfo>): void;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: mechanicManager;<br>API declaration: function off(type: 'attachStateChange', callback?: Callback\<AttachStateChangeInfo>): void;<br>DIfferences: function off(type: 'attachStateChange', callback?: Callback\<AttachStateChangeInfo>): void;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: mechanicManager;<br>API declaration: function getAttachedMechDevices(): MechInfo[];<br>DIfferences: function getAttachedMechDevices(): MechInfo[];|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: mechanicManager;<br>API declaration: function setCameraTrackingEnabled(isEnabled: boolean): void;<br>DIfferences: function setCameraTrackingEnabled(isEnabled: boolean): void;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: mechanicManager;<br>API declaration: function getCameraTrackingEnabled(): boolean;<br>DIfferences: function getCameraTrackingEnabled(): boolean;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: mechanicManager;<br>API declaration: function on(type: 'trackingStateChange', callback: Callback\<TrackingEventInfo>): void;<br>DIfferences: function on(type: 'trackingStateChange', callback: Callback\<TrackingEventInfo>): void;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: mechanicManager;<br>API declaration: function off(type: 'trackingStateChange', callback?: Callback\<TrackingEventInfo>): void;<br>DIfferences: function off(type: 'trackingStateChange', callback?: Callback\<TrackingEventInfo>): void;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: mechanicManager;<br>API declaration: function getCameraTrackingLayout(): CameraTrackingLayout;<br>DIfferences: function getCameraTrackingLayout(): CameraTrackingLayout;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: mechanicManager;<br>API declaration: export interface MechInfo<br>DIfferences: export interface MechInfo|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: MechInfo;<br>API declaration: mechId: number;<br>DIfferences: mechId: number;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: MechInfo;<br>API declaration: mechDeviceType: MechDeviceType;<br>DIfferences: mechDeviceType: MechDeviceType;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: MechInfo;<br>API declaration: mechName: string;<br>DIfferences: mechName: string;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: mechanicManager;<br>API declaration: export interface TrackingEventInfo<br>DIfferences: export interface TrackingEventInfo|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: TrackingEventInfo;<br>API declaration: event: TrackingEvent;<br>DIfferences: event: TrackingEvent;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: mechanicManager;<br>API declaration: export interface AttachStateChangeInfo<br>DIfferences: export interface AttachStateChangeInfo|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: AttachStateChangeInfo;<br>API declaration: state: AttachState;<br>DIfferences: state: AttachState;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: AttachStateChangeInfo;<br>API declaration: mechInfo: MechInfo;<br>DIfferences: mechInfo: MechInfo;|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: mechanicManager;<br>API declaration: export enum TrackingEvent<br>DIfferences: export enum TrackingEvent|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: TrackingEvent;<br>API declaration: CAMERA_TRACKING_USER_ENABLED = 0<br>DIfferences: CAMERA_TRACKING_USER_ENABLED = 0|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: TrackingEvent;<br>API declaration: CAMERA_TRACKING_USER_DISABLED = 1<br>DIfferences: CAMERA_TRACKING_USER_DISABLED = 1|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: TrackingEvent;<br>API declaration: CAMERA_TRACKING_LAYOUT_CHANGED = 2<br>DIfferences: CAMERA_TRACKING_LAYOUT_CHANGED = 2|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: mechanicManager;<br>API declaration: export enum MechDeviceType<br>DIfferences: export enum MechDeviceType|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: MechDeviceType;<br>API declaration: GIMBAL_DEVICE = 0<br>DIfferences: GIMBAL_DEVICE = 0|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: mechanicManager;<br>API declaration: export enum AttachState<br>DIfferences: export enum AttachState|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: AttachState;<br>API declaration: ATTACHED = 0<br>DIfferences: ATTACHED = 0|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: AttachState;<br>API declaration: DETACHED = 1<br>DIfferences: DETACHED = 1|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: mechanicManager;<br>API declaration: export enum CameraTrackingLayout<br>DIfferences: export enum CameraTrackingLayout|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: CameraTrackingLayout;<br>API declaration: DEFAULT = 0<br>DIfferences: DEFAULT = 0|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: CameraTrackingLayout;<br>API declaration: LEFT = 1<br>DIfferences: LEFT = 1|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: CameraTrackingLayout;<br>API declaration: MIDDLE = 2<br>DIfferences: MIDDLE = 2|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New API |NA|Class name: CameraTrackingLayout;<br>API declaration: RIGHT = 3<br>DIfferences: RIGHT = 3|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>DIfferences: NA|Class name: global;<br>API declaration: api\@ohos.distributedHardware.mechanicManager.d.ts<br>DIfferences: MechanicKit|api/@ohos.distributedHardware.mechanicManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>DIfferences: NA|Class name: global;<br>API declaration: kits\@kit.MechanicKit.d.ts<br>DIfferences: MechanicKit|kits/@kit.MechanicKit.d.ts|
