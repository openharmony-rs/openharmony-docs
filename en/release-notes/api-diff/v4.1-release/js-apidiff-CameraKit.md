| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API|NA|Class name: global;<br>API declaration: declare namespace camera<br>Differences: declare namespace camera|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: function getCameraManager(context: Context): CameraManager;<br>Differences: function getCameraManager(context: Context): CameraManager;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: enum CameraStatus<br>Differences: enum CameraStatus|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraStatus;<br>API declaration: CAMERA_STATUS_APPEAR = 0<br>Differences: CAMERA_STATUS_APPEAR = 0|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraStatus;<br>API declaration: CAMERA_STATUS_DISAPPEAR = 1<br>Differences: CAMERA_STATUS_DISAPPEAR = 1|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraStatus;<br>API declaration: CAMERA_STATUS_AVAILABLE = 2<br>Differences: CAMERA_STATUS_AVAILABLE = 2|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraStatus;<br>API declaration: CAMERA_STATUS_UNAVAILABLE = 3<br>Differences: CAMERA_STATUS_UNAVAILABLE = 3|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface Profile<br>Differences: interface Profile|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Profile;<br>API declaration: readonly format: CameraFormat;<br>Differences: readonly format: CameraFormat;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Profile;<br>API declaration: readonly size: Size;<br>Differences: readonly size: Size;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface FrameRateRange<br>Differences: interface FrameRateRange|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: FrameRateRange;<br>API declaration: readonly min: number;<br>Differences: readonly min: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: FrameRateRange;<br>API declaration: readonly max: number;<br>Differences: readonly max: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface VideoProfile<br>Differences: interface VideoProfile|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoProfile;<br>API declaration: readonly frameRateRange: FrameRateRange;<br>Differences: readonly frameRateRange: FrameRateRange;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface CameraOutputCapability<br>Differences: interface CameraOutputCapability|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraOutputCapability;<br>API declaration: readonly previewProfiles: Array\<Profile>;<br>Differences: readonly previewProfiles: Array\<Profile>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraOutputCapability;<br>API declaration: readonly photoProfiles: Array\<Profile>;<br>Differences: readonly photoProfiles: Array\<Profile>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraOutputCapability;<br>API declaration: readonly videoProfiles: Array\<VideoProfile>;<br>Differences: readonly videoProfiles: Array\<VideoProfile>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraOutputCapability;<br>API declaration: readonly supportedMetadataObjectTypes: Array\<MetadataObjectType>;<br>Differences: readonly supportedMetadataObjectTypes: Array\<MetadataObjectType>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: enum CameraErrorCode<br>Differences: enum CameraErrorCode|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraErrorCode;<br>API declaration: INVALID_ARGUMENT = 7400101<br>Differences: INVALID_ARGUMENT = 7400101|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraErrorCode;<br>API declaration: OPERATION_NOT_ALLOWED = 7400102<br>Differences: OPERATION_NOT_ALLOWED = 7400102|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraErrorCode;<br>API declaration: SESSION_NOT_CONFIG = 7400103<br>Differences: SESSION_NOT_CONFIG = 7400103|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraErrorCode;<br>API declaration: SESSION_NOT_RUNNING = 7400104<br>Differences: SESSION_NOT_RUNNING = 7400104|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraErrorCode;<br>API declaration: SESSION_CONFIG_LOCKED = 7400105<br>Differences: SESSION_CONFIG_LOCKED = 7400105|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraErrorCode;<br>API declaration: DEVICE_SETTING_LOCKED = 7400106<br>Differences: DEVICE_SETTING_LOCKED = 7400106|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraErrorCode;<br>API declaration: CONFLICT_CAMERA = 7400107<br>Differences: CONFLICT_CAMERA = 7400107|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraErrorCode;<br>API declaration: DEVICE_DISABLED = 7400108<br>Differences: DEVICE_DISABLED = 7400108|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraErrorCode;<br>API declaration: DEVICE_PREEMPTED = 7400109<br>Differences: DEVICE_PREEMPTED = 7400109|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraErrorCode;<br>API declaration: SERVICE_FATAL_ERROR = 7400201<br>Differences: SERVICE_FATAL_ERROR = 7400201|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface CameraManager<br>Differences: interface CameraManager|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: getSupportedCameras(): Array\<CameraDevice>;<br>Differences: getSupportedCameras(): Array\<CameraDevice>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: getSupportedOutputCapability(camera: CameraDevice): CameraOutputCapability;<br>Differences: getSupportedOutputCapability(camera: CameraDevice): CameraOutputCapability;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: getSupportedOutputCapability(camera: CameraDevice, mode: SceneMode): CameraOutputCapability;<br>Differences: getSupportedOutputCapability(camera: CameraDevice, mode: SceneMode): CameraOutputCapability;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: getSupportedSceneModes(camera: CameraDevice): Array\<SceneMode>;<br>Differences: getSupportedSceneModes(camera: CameraDevice): Array\<SceneMode>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: isCameraMuted(): boolean;<br>Differences: isCameraMuted(): boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: createCameraInput(camera: CameraDevice): CameraInput;<br>Differences: createCameraInput(camera: CameraDevice): CameraInput;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: createCameraInput(position: CameraPosition, type: CameraType): CameraInput;<br>Differences: createCameraInput(position: CameraPosition, type: CameraType): CameraInput;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: createPreviewOutput(profile: Profile, surfaceId: string): PreviewOutput;<br>Differences: createPreviewOutput(profile: Profile, surfaceId: string): PreviewOutput;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: createPhotoOutput(profile: Profile, surfaceId: string): PhotoOutput;<br>Differences: createPhotoOutput(profile: Profile, surfaceId: string): PhotoOutput;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: createPhotoOutput(profile: Profile): PhotoOutput;<br>Differences: createPhotoOutput(profile: Profile): PhotoOutput;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: createVideoOutput(profile: VideoProfile, surfaceId: string): VideoOutput;<br>Differences: createVideoOutput(profile: VideoProfile, surfaceId: string): VideoOutput;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: createMetadataOutput(metadataObjectTypes: Array\<MetadataObjectType>): MetadataOutput;<br>Differences: createMetadataOutput(metadataObjectTypes: Array\<MetadataObjectType>): MetadataOutput;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: createCaptureSession(): CaptureSession;<br>Differences: createCaptureSession(): CaptureSession;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: createSession\<T extends Session>(mode: SceneMode): T;<br>Differences: createSession\<T extends Session>(mode: SceneMode): T;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: on(type: 'cameraStatus', callback: AsyncCallback\<CameraStatusInfo>): void;<br>Differences: on(type: 'cameraStatus', callback: AsyncCallback\<CameraStatusInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: off(type: 'cameraStatus', callback?: AsyncCallback\<CameraStatusInfo>): void;<br>Differences: off(type: 'cameraStatus', callback?: AsyncCallback\<CameraStatusInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: isTorchSupported(): boolean;<br>Differences: isTorchSupported(): boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: isTorchModeSupported(mode: TorchMode): boolean;<br>Differences: isTorchModeSupported(mode: TorchMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: getTorchMode(): TorchMode;<br>Differences: getTorchMode(): TorchMode;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: setTorchMode(mode: TorchMode): void;<br>Differences: setTorchMode(mode: TorchMode): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: on(type: 'torchStatusChange', callback: AsyncCallback\<TorchStatusInfo>): void;<br>Differences: on(type: 'torchStatusChange', callback: AsyncCallback\<TorchStatusInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraManager;<br>API declaration: off(type: 'torchStatusChange', callback?: AsyncCallback\<TorchStatusInfo>): void;<br>Differences: off(type: 'torchStatusChange', callback?: AsyncCallback\<TorchStatusInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface TorchStatusInfo<br>Differences: interface TorchStatusInfo|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: TorchStatusInfo;<br>API declaration: readonly isTorchAvailable: boolean;<br>Differences: readonly isTorchAvailable: boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: TorchStatusInfo;<br>API declaration: readonly isTorchActive: boolean;<br>Differences: readonly isTorchActive: boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: TorchStatusInfo;<br>API declaration: readonly torchLevel: number;<br>Differences: readonly torchLevel: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: enum TorchMode<br>Differences: enum TorchMode|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: TorchMode;<br>API declaration: OFF = 0<br>Differences: OFF = 0|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: TorchMode;<br>API declaration: ON = 1<br>Differences: ON = 1|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: TorchMode;<br>API declaration: AUTO = 2<br>Differences: AUTO = 2|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface CameraStatusInfo<br>Differences: interface CameraStatusInfo|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraStatusInfo;<br>API declaration: camera: CameraDevice;<br>Differences: camera: CameraDevice;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraStatusInfo;<br>API declaration: status: CameraStatus;<br>Differences: status: CameraStatus;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: enum CameraPosition<br>Differences: enum CameraPosition|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraPosition;<br>API declaration: CAMERA_POSITION_UNSPECIFIED = 0<br>Differences: CAMERA_POSITION_UNSPECIFIED = 0|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraPosition;<br>API declaration: CAMERA_POSITION_BACK = 1<br>Differences: CAMERA_POSITION_BACK = 1|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraPosition;<br>API declaration: CAMERA_POSITION_FRONT = 2<br>Differences: CAMERA_POSITION_FRONT = 2|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraPosition;<br>API declaration: CAMERA_POSITION_FOLD_INNER = 3<br>Differences: CAMERA_POSITION_FOLD_INNER = 3|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: enum CameraType<br>Differences: enum CameraType|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraType;<br>API declaration: CAMERA_TYPE_DEFAULT = 0<br>Differences: CAMERA_TYPE_DEFAULT = 0|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraType;<br>API declaration: CAMERA_TYPE_WIDE_ANGLE = 1<br>Differences: CAMERA_TYPE_WIDE_ANGLE = 1|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraType;<br>API declaration: CAMERA_TYPE_ULTRA_WIDE = 2<br>Differences: CAMERA_TYPE_ULTRA_WIDE = 2|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraType;<br>API declaration: CAMERA_TYPE_TELEPHOTO = 3<br>Differences: CAMERA_TYPE_TELEPHOTO = 3|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraType;<br>API declaration: CAMERA_TYPE_TRUE_DEPTH = 4<br>Differences: CAMERA_TYPE_TRUE_DEPTH = 4|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: enum ConnectionType<br>Differences: enum ConnectionType|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: ConnectionType;<br>API declaration: CAMERA_CONNECTION_BUILT_IN = 0<br>Differences: CAMERA_CONNECTION_BUILT_IN = 0|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: ConnectionType;<br>API declaration: CAMERA_CONNECTION_USB_PLUGIN = 1<br>Differences: CAMERA_CONNECTION_USB_PLUGIN = 1|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: ConnectionType;<br>API declaration: CAMERA_CONNECTION_REMOTE = 2<br>Differences: CAMERA_CONNECTION_REMOTE = 2|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface CameraDevice<br>Differences: interface CameraDevice|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraDevice;<br>API declaration: readonly cameraId: string;<br>Differences: readonly cameraId: string;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraDevice;<br>API declaration: readonly cameraPosition: CameraPosition;<br>Differences: readonly cameraPosition: CameraPosition;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraDevice;<br>API declaration: readonly cameraType: CameraType;<br>Differences: readonly cameraType: CameraType;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraDevice;<br>API declaration: readonly connectionType: ConnectionType;<br>Differences: readonly connectionType: ConnectionType;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface Size<br>Differences: interface Size|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Size;<br>API declaration: height: number;<br>Differences: height: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Size;<br>API declaration: width: number;<br>Differences: width: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface Point<br>Differences: interface Point|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Point;<br>API declaration: x: number;<br>Differences: x: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Point;<br>API declaration: y: number;<br>Differences: y: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface CameraInput<br>Differences: interface CameraInput|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraInput;<br>API declaration: open(callback: AsyncCallback\<void>): void;<br>Differences: open(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraInput;<br>API declaration: open(): Promise\<void>;<br>Differences: open(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraInput;<br>API declaration: close(callback: AsyncCallback\<void>): void;<br>Differences: close(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraInput;<br>API declaration: close(): Promise\<void>;<br>Differences: close(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraInput;<br>API declaration: on(type: 'error', camera: CameraDevice, callback: ErrorCallback): void;<br>Differences: on(type: 'error', camera: CameraDevice, callback: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraInput;<br>API declaration: off(type: 'error', camera: CameraDevice, callback?: ErrorCallback): void;<br>Differences: off(type: 'error', camera: CameraDevice, callback?: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: enum SceneMode<br>Differences: enum SceneMode|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: SceneMode;<br>API declaration: NORMAL_PHOTO = 1<br>Differences: NORMAL_PHOTO = 1|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: SceneMode;<br>API declaration: NORMAL_VIDEO = 2<br>Differences: NORMAL_VIDEO = 2|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: enum CameraFormat<br>Differences: enum CameraFormat|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraFormat;<br>API declaration: CAMERA_FORMAT_RGBA_8888 = 3<br>Differences: CAMERA_FORMAT_RGBA_8888 = 3|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraFormat;<br>API declaration: CAMERA_FORMAT_YUV_420_SP = 1003<br>Differences: CAMERA_FORMAT_YUV_420_SP = 1003|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraFormat;<br>API declaration: CAMERA_FORMAT_JPEG = 2000<br>Differences: CAMERA_FORMAT_JPEG = 2000|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraFormat;<br>API declaration: CAMERA_FORMAT_YCBCR_P010<br>Differences: CAMERA_FORMAT_YCBCR_P010|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraFormat;<br>API declaration: CAMERA_FORMAT_YCRCB_P010<br>Differences: CAMERA_FORMAT_YCRCB_P010|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: enum FlashMode<br>Differences: enum FlashMode|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: FlashMode;<br>API declaration: FLASH_MODE_CLOSE = 0<br>Differences: FLASH_MODE_CLOSE = 0|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: FlashMode;<br>API declaration: FLASH_MODE_OPEN = 1<br>Differences: FLASH_MODE_OPEN = 1|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: FlashMode;<br>API declaration: FLASH_MODE_AUTO = 2<br>Differences: FLASH_MODE_AUTO = 2|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: FlashMode;<br>API declaration: FLASH_MODE_ALWAYS_OPEN = 3<br>Differences: FLASH_MODE_ALWAYS_OPEN = 3|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface Flash<br>Differences: interface Flash|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Flash;<br>API declaration: hasFlash(): boolean;<br>Differences: hasFlash(): boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Flash;<br>API declaration: isFlashModeSupported(flashMode: FlashMode): boolean;<br>Differences: isFlashModeSupported(flashMode: FlashMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Flash;<br>API declaration: getFlashMode(): FlashMode;<br>Differences: getFlashMode(): FlashMode;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Flash;<br>API declaration: setFlashMode(flashMode: FlashMode): void;<br>Differences: setFlashMode(flashMode: FlashMode): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: enum ExposureMode<br>Differences: enum ExposureMode|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: ExposureMode;<br>API declaration: EXPOSURE_MODE_LOCKED = 0<br>Differences: EXPOSURE_MODE_LOCKED = 0|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: ExposureMode;<br>API declaration: EXPOSURE_MODE_AUTO = 1<br>Differences: EXPOSURE_MODE_AUTO = 1|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: ExposureMode;<br>API declaration: EXPOSURE_MODE_CONTINUOUS_AUTO = 2<br>Differences: EXPOSURE_MODE_CONTINUOUS_AUTO = 2|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface AutoExposure<br>Differences: interface AutoExposure|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: AutoExposure;<br>API declaration: isExposureModeSupported(aeMode: ExposureMode): boolean;<br>Differences: isExposureModeSupported(aeMode: ExposureMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: AutoExposure;<br>API declaration: getExposureMode(): ExposureMode;<br>Differences: getExposureMode(): ExposureMode;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: AutoExposure;<br>API declaration: setExposureMode(aeMode: ExposureMode): void;<br>Differences: setExposureMode(aeMode: ExposureMode): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: AutoExposure;<br>API declaration: getMeteringPoint(): Point;<br>Differences: getMeteringPoint(): Point;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: AutoExposure;<br>API declaration: setMeteringPoint(point: Point): void;<br>Differences: setMeteringPoint(point: Point): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: AutoExposure;<br>API declaration: getExposureBiasRange(): Array\<number>;<br>Differences: getExposureBiasRange(): Array\<number>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: AutoExposure;<br>API declaration: setExposureBias(exposureBias: number): void;<br>Differences: setExposureBias(exposureBias: number): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: AutoExposure;<br>API declaration: getExposureValue(): number;<br>Differences: getExposureValue(): number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: enum FocusMode<br>Differences: enum FocusMode|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: FocusMode;<br>API declaration: FOCUS_MODE_MANUAL = 0<br>Differences: FOCUS_MODE_MANUAL = 0|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: FocusMode;<br>API declaration: FOCUS_MODE_CONTINUOUS_AUTO = 1<br>Differences: FOCUS_MODE_CONTINUOUS_AUTO = 1|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: FocusMode;<br>API declaration: FOCUS_MODE_AUTO = 2<br>Differences: FOCUS_MODE_AUTO = 2|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: FocusMode;<br>API declaration: FOCUS_MODE_LOCKED = 3<br>Differences: FOCUS_MODE_LOCKED = 3|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: enum FocusState<br>Differences: enum FocusState|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: FocusState;<br>API declaration: FOCUS_STATE_SCAN = 0<br>Differences: FOCUS_STATE_SCAN = 0|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: FocusState;<br>API declaration: FOCUS_STATE_FOCUSED = 1<br>Differences: FOCUS_STATE_FOCUSED = 1|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: FocusState;<br>API declaration: FOCUS_STATE_UNFOCUSED = 2<br>Differences: FOCUS_STATE_UNFOCUSED = 2|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface Focus<br>Differences: interface Focus|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Focus;<br>API declaration: isFocusModeSupported(afMode: FocusMode): boolean;<br>Differences: isFocusModeSupported(afMode: FocusMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Focus;<br>API declaration: getFocusMode(): FocusMode;<br>Differences: getFocusMode(): FocusMode;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Focus;<br>API declaration: setFocusMode(afMode: FocusMode): void;<br>Differences: setFocusMode(afMode: FocusMode): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Focus;<br>API declaration: setFocusPoint(point: Point): void;<br>Differences: setFocusPoint(point: Point): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Focus;<br>API declaration: getFocusPoint(): Point;<br>Differences: getFocusPoint(): Point;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Focus;<br>API declaration: getFocalLength(): number;<br>Differences: getFocalLength(): number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: enum SmoothZoomMode<br>Differences: enum SmoothZoomMode|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: SmoothZoomMode;<br>API declaration: NORMAL = 0<br>Differences: NORMAL = 0|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface SmoothZoomInfo<br>Differences: interface SmoothZoomInfo|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: SmoothZoomInfo;<br>API declaration: duration: number;<br>Differences: duration: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface Zoom<br>Differences: interface Zoom|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Zoom;<br>API declaration: getZoomRatioRange(): Array\<number>;<br>Differences: getZoomRatioRange(): Array\<number>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Zoom;<br>API declaration: getZoomRatio(): number;<br>Differences: getZoomRatio(): number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Zoom;<br>API declaration: setZoomRatio(zoomRatio: number): void;<br>Differences: setZoomRatio(zoomRatio: number): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Zoom;<br>API declaration: setSmoothZoom(targetRatio: number, mode?: SmoothZoomMode): void;<br>Differences: setSmoothZoom(targetRatio: number, mode?: SmoothZoomMode): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: enum VideoStabilizationMode<br>Differences: enum VideoStabilizationMode|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoStabilizationMode;<br>API declaration: OFF = 0<br>Differences: OFF = 0|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoStabilizationMode;<br>API declaration: LOW = 1<br>Differences: LOW = 1|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoStabilizationMode;<br>API declaration: MIDDLE = 2<br>Differences: MIDDLE = 2|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoStabilizationMode;<br>API declaration: HIGH = 3<br>Differences: HIGH = 3|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoStabilizationMode;<br>API declaration: AUTO = 4<br>Differences: AUTO = 4|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface Stabilization<br>Differences: interface Stabilization|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Stabilization;<br>API declaration: isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean;<br>Differences: isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Stabilization;<br>API declaration: getActiveVideoStabilizationMode(): VideoStabilizationMode;<br>Differences: getActiveVideoStabilizationMode(): VideoStabilizationMode;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Stabilization;<br>API declaration: setVideoStabilizationMode(mode: VideoStabilizationMode): void;<br>Differences: setVideoStabilizationMode(mode: VideoStabilizationMode): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface Session<br>Differences: interface Session|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Session;<br>API declaration: beginConfig(): void;<br>Differences: beginConfig(): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Session;<br>API declaration: commitConfig(callback: AsyncCallback\<void>): void;<br>Differences: commitConfig(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Session;<br>API declaration: commitConfig(): Promise\<void>;<br>Differences: commitConfig(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Session;<br>API declaration: canAddInput(cameraInput: CameraInput): boolean;<br>Differences: canAddInput(cameraInput: CameraInput): boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Session;<br>API declaration: addInput(cameraInput: CameraInput): void;<br>Differences: addInput(cameraInput: CameraInput): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Session;<br>API declaration: removeInput(cameraInput: CameraInput): void;<br>Differences: removeInput(cameraInput: CameraInput): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Session;<br>API declaration: canAddOutput(cameraOutput: CameraOutput): boolean;<br>Differences: canAddOutput(cameraOutput: CameraOutput): boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Session;<br>API declaration: addOutput(cameraOutput: CameraOutput): void;<br>Differences: addOutput(cameraOutput: CameraOutput): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Session;<br>API declaration: removeOutput(cameraOutput: CameraOutput): void;<br>Differences: removeOutput(cameraOutput: CameraOutput): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Session;<br>API declaration: start(callback: AsyncCallback\<void>): void;<br>Differences: start(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Session;<br>API declaration: start(): Promise\<void>;<br>Differences: start(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Session;<br>API declaration: stop(callback: AsyncCallback\<void>): void;<br>Differences: stop(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Session;<br>API declaration: stop(): Promise\<void>;<br>Differences: stop(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Session;<br>API declaration: release(callback: AsyncCallback\<void>): void;<br>Differences: release(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Session;<br>API declaration: release(): Promise\<void>;<br>Differences: release(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface CaptureSession<br>Differences: interface CaptureSession|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: beginConfig(): void;<br>Differences: beginConfig(): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: commitConfig(callback: AsyncCallback\<void>): void;<br>Differences: commitConfig(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: commitConfig(): Promise\<void>;<br>Differences: commitConfig(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: addInput(cameraInput: CameraInput): void;<br>Differences: addInput(cameraInput: CameraInput): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: removeInput(cameraInput: CameraInput): void;<br>Differences: removeInput(cameraInput: CameraInput): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: addOutput(cameraOutput: CameraOutput): void;<br>Differences: addOutput(cameraOutput: CameraOutput): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: removeOutput(cameraOutput: CameraOutput): void;<br>Differences: removeOutput(cameraOutput: CameraOutput): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: start(callback: AsyncCallback\<void>): void;<br>Differences: start(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: start(): Promise\<void>;<br>Differences: start(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: stop(callback: AsyncCallback\<void>): void;<br>Differences: stop(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: stop(): Promise\<void>;<br>Differences: stop(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: release(callback: AsyncCallback\<void>): void;<br>Differences: release(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: release(): Promise\<void>;<br>Differences: release(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: hasFlash(): boolean;<br>Differences: hasFlash(): boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: isFlashModeSupported(flashMode: FlashMode): boolean;<br>Differences: isFlashModeSupported(flashMode: FlashMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: getFlashMode(): FlashMode;<br>Differences: getFlashMode(): FlashMode;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: setFlashMode(flashMode: FlashMode): void;<br>Differences: setFlashMode(flashMode: FlashMode): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: isExposureModeSupported(aeMode: ExposureMode): boolean;<br>Differences: isExposureModeSupported(aeMode: ExposureMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: getExposureMode(): ExposureMode;<br>Differences: getExposureMode(): ExposureMode;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: setExposureMode(aeMode: ExposureMode): void;<br>Differences: setExposureMode(aeMode: ExposureMode): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: getMeteringPoint(): Point;<br>Differences: getMeteringPoint(): Point;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: setMeteringPoint(point: Point): void;<br>Differences: setMeteringPoint(point: Point): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: getExposureBiasRange(): Array\<number>;<br>Differences: getExposureBiasRange(): Array\<number>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: setExposureBias(exposureBias: number): void;<br>Differences: setExposureBias(exposureBias: number): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: getExposureValue(): number;<br>Differences: getExposureValue(): number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: isFocusModeSupported(afMode: FocusMode): boolean;<br>Differences: isFocusModeSupported(afMode: FocusMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: getFocusMode(): FocusMode;<br>Differences: getFocusMode(): FocusMode;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: setFocusMode(afMode: FocusMode): void;<br>Differences: setFocusMode(afMode: FocusMode): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: setFocusPoint(point: Point): void;<br>Differences: setFocusPoint(point: Point): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: getFocusPoint(): Point;<br>Differences: getFocusPoint(): Point;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: getFocalLength(): number;<br>Differences: getFocalLength(): number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: getZoomRatioRange(): Array\<number>;<br>Differences: getZoomRatioRange(): Array\<number>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: getZoomRatio(): number;<br>Differences: getZoomRatio(): number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: setZoomRatio(zoomRatio: number): void;<br>Differences: setZoomRatio(zoomRatio: number): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean;<br>Differences: isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: getActiveVideoStabilizationMode(): VideoStabilizationMode;<br>Differences: getActiveVideoStabilizationMode(): VideoStabilizationMode;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: setVideoStabilizationMode(mode: VideoStabilizationMode): void;<br>Differences: setVideoStabilizationMode(mode: VideoStabilizationMode): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: on(type: 'focusStateChange', callback: AsyncCallback\<FocusState>): void;<br>Differences: on(type: 'focusStateChange', callback: AsyncCallback\<FocusState>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: off(type: 'focusStateChange', callback?: AsyncCallback\<FocusState>): void;<br>Differences: off(type: 'focusStateChange', callback?: AsyncCallback\<FocusState>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureSession;<br>API declaration: off(type: 'error', callback?: ErrorCallback): void;<br>Differences: off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface PhotoSession<br>Differences: interface PhotoSession|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoSession;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoSession;<br>API declaration: off(type: 'error', callback?: ErrorCallback): void;<br>Differences: off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoSession;<br>API declaration: on(type: 'focusStateChange', callback: AsyncCallback\<FocusState>): void;<br>Differences: on(type: 'focusStateChange', callback: AsyncCallback\<FocusState>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoSession;<br>API declaration: off(type: 'focusStateChange', callback?: AsyncCallback\<FocusState>): void;<br>Differences: off(type: 'focusStateChange', callback?: AsyncCallback\<FocusState>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoSession;<br>API declaration: on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback\<SmoothZoomInfo>): void;<br>Differences: on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback\<SmoothZoomInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoSession;<br>API declaration: off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback\<SmoothZoomInfo>): void;<br>Differences: off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback\<SmoothZoomInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface VideoSession<br>Differences: interface VideoSession|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoSession;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoSession;<br>API declaration: off(type: 'error', callback?: ErrorCallback): void;<br>Differences: off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoSession;<br>API declaration: on(type: 'focusStateChange', callback: AsyncCallback\<FocusState>): void;<br>Differences: on(type: 'focusStateChange', callback: AsyncCallback\<FocusState>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoSession;<br>API declaration: off(type: 'focusStateChange', callback?: AsyncCallback\<FocusState>): void;<br>Differences: off(type: 'focusStateChange', callback?: AsyncCallback\<FocusState>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoSession;<br>API declaration: on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback\<SmoothZoomInfo>): void;<br>Differences: on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback\<SmoothZoomInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoSession;<br>API declaration: off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback\<SmoothZoomInfo>): void;<br>Differences: off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback\<SmoothZoomInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface CameraOutput<br>Differences: interface CameraOutput|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraOutput;<br>API declaration: release(callback: AsyncCallback\<void>): void;<br>Differences: release(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CameraOutput;<br>API declaration: release(): Promise\<void>;<br>Differences: release(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface PreviewOutput<br>Differences: interface PreviewOutput|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PreviewOutput;<br>API declaration: start(callback: AsyncCallback\<void>): void;<br>Differences: start(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PreviewOutput;<br>API declaration: start(): Promise\<void>;<br>Differences: start(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PreviewOutput;<br>API declaration: stop(callback: AsyncCallback\<void>): void;<br>Differences: stop(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PreviewOutput;<br>API declaration: stop(): Promise\<void>;<br>Differences: stop(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PreviewOutput;<br>API declaration: on(type: 'frameStart', callback: AsyncCallback\<void>): void;<br>Differences: on(type: 'frameStart', callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PreviewOutput;<br>API declaration: off(type: 'frameStart', callback?: AsyncCallback\<void>): void;<br>Differences: off(type: 'frameStart', callback?: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PreviewOutput;<br>API declaration: on(type: 'frameEnd', callback: AsyncCallback\<void>): void;<br>Differences: on(type: 'frameEnd', callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PreviewOutput;<br>API declaration: off(type: 'frameEnd', callback?: AsyncCallback\<void>): void;<br>Differences: off(type: 'frameEnd', callback?: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PreviewOutput;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PreviewOutput;<br>API declaration: off(type: 'error', callback?: ErrorCallback): void;<br>Differences: off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: enum ImageRotation<br>Differences: enum ImageRotation|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: ImageRotation;<br>API declaration: ROTATION_0 = 0<br>Differences: ROTATION_0 = 0|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: ImageRotation;<br>API declaration: ROTATION_90 = 90<br>Differences: ROTATION_90 = 90|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: ImageRotation;<br>API declaration: ROTATION_180 = 180<br>Differences: ROTATION_180 = 180|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: ImageRotation;<br>API declaration: ROTATION_270 = 270<br>Differences: ROTATION_270 = 270|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface Location<br>Differences: interface Location|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Location;<br>API declaration: latitude: number;<br>Differences: latitude: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Location;<br>API declaration: longitude: number;<br>Differences: longitude: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Location;<br>API declaration: altitude: number;<br>Differences: altitude: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: enum QualityLevel<br>Differences: enum QualityLevel|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: QualityLevel;<br>API declaration: QUALITY_LEVEL_HIGH = 0<br>Differences: QUALITY_LEVEL_HIGH = 0|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: QualityLevel;<br>API declaration: QUALITY_LEVEL_MEDIUM = 1<br>Differences: QUALITY_LEVEL_MEDIUM = 1|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: QualityLevel;<br>API declaration: QUALITY_LEVEL_LOW = 2<br>Differences: QUALITY_LEVEL_LOW = 2|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface PhotoCaptureSetting<br>Differences: interface PhotoCaptureSetting|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoCaptureSetting;<br>API declaration: quality?: QualityLevel;<br>Differences: quality?: QualityLevel;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoCaptureSetting;<br>API declaration: rotation?: ImageRotation;<br>Differences: rotation?: ImageRotation;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoCaptureSetting;<br>API declaration: location?: Location;<br>Differences: location?: Location;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoCaptureSetting;<br>API declaration: mirror?: boolean;<br>Differences: mirror?: boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface Photo<br>Differences: interface Photo|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Photo;<br>API declaration: main: image.Image;<br>Differences: main: image.Image;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Photo;<br>API declaration: release(): Promise\<void>;<br>Differences: release(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface PhotoOutput<br>Differences: interface PhotoOutput|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoOutput;<br>API declaration: capture(callback: AsyncCallback\<void>): void;<br>Differences: capture(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoOutput;<br>API declaration: capture(): Promise\<void>;<br>Differences: capture(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoOutput;<br>API declaration: capture(setting: PhotoCaptureSetting, callback: AsyncCallback\<void>): void;<br>Differences: capture(setting: PhotoCaptureSetting, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoOutput;<br>API declaration: capture(setting: PhotoCaptureSetting): Promise\<void>;<br>Differences: capture(setting: PhotoCaptureSetting): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoOutput;<br>API declaration: on(type: 'photoAvailable', callback: AsyncCallback\<Photo>): void;<br>Differences: on(type: 'photoAvailable', callback: AsyncCallback\<Photo>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoOutput;<br>API declaration: off(type: 'photoAvailable', callback?: AsyncCallback\<Photo>): void;<br>Differences: off(type: 'photoAvailable', callback?: AsyncCallback\<Photo>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoOutput;<br>API declaration: isMirrorSupported(): boolean;<br>Differences: isMirrorSupported(): boolean;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoOutput;<br>API declaration: on(type: 'captureStart', callback: AsyncCallback\<number>): void;<br>Differences: on(type: 'captureStart', callback: AsyncCallback\<number>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoOutput;<br>API declaration: off(type: 'captureStart', callback?: AsyncCallback\<number>): void;<br>Differences: off(type: 'captureStart', callback?: AsyncCallback\<number>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoOutput;<br>API declaration: on(type: 'captureStartWithInfo', callback: AsyncCallback\<CaptureStartInfo>): void;<br>Differences: on(type: 'captureStartWithInfo', callback: AsyncCallback\<CaptureStartInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoOutput;<br>API declaration: off(type: 'captureStartWithInfo', callback?: AsyncCallback\<CaptureStartInfo>): void;<br>Differences: off(type: 'captureStartWithInfo', callback?: AsyncCallback\<CaptureStartInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoOutput;<br>API declaration: on(type: 'frameShutter', callback: AsyncCallback\<FrameShutterInfo>): void;<br>Differences: on(type: 'frameShutter', callback: AsyncCallback\<FrameShutterInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoOutput;<br>API declaration: off(type: 'frameShutter', callback?: AsyncCallback\<FrameShutterInfo>): void;<br>Differences: off(type: 'frameShutter', callback?: AsyncCallback\<FrameShutterInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoOutput;<br>API declaration: on(type: 'captureEnd', callback: AsyncCallback\<CaptureEndInfo>): void;<br>Differences: on(type: 'captureEnd', callback: AsyncCallback\<CaptureEndInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoOutput;<br>API declaration: off(type: 'captureEnd', callback?: AsyncCallback\<CaptureEndInfo>): void;<br>Differences: off(type: 'captureEnd', callback?: AsyncCallback\<CaptureEndInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoOutput;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: PhotoOutput;<br>API declaration: off(type: 'error', callback?: ErrorCallback): void;<br>Differences: off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface FrameShutterInfo<br>Differences: interface FrameShutterInfo|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: FrameShutterInfo;<br>API declaration: captureId: number;<br>Differences: captureId: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: FrameShutterInfo;<br>API declaration: timestamp: number;<br>Differences: timestamp: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface CaptureStartInfo<br>Differences: interface CaptureStartInfo|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureStartInfo;<br>API declaration: captureId: number;<br>Differences: captureId: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureStartInfo;<br>API declaration: time: number;<br>Differences: time: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface CaptureEndInfo<br>Differences: interface CaptureEndInfo|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureEndInfo;<br>API declaration: captureId: number;<br>Differences: captureId: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: CaptureEndInfo;<br>API declaration: frameCount: number;<br>Differences: frameCount: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface VideoOutput<br>Differences: interface VideoOutput|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoOutput;<br>API declaration: start(callback: AsyncCallback\<void>): void;<br>Differences: start(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoOutput;<br>API declaration: start(): Promise\<void>;<br>Differences: start(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoOutput;<br>API declaration: stop(callback: AsyncCallback\<void>): void;<br>Differences: stop(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoOutput;<br>API declaration: stop(): Promise\<void>;<br>Differences: stop(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoOutput;<br>API declaration: on(type: 'frameStart', callback: AsyncCallback\<void>): void;<br>Differences: on(type: 'frameStart', callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoOutput;<br>API declaration: off(type: 'frameStart', callback?: AsyncCallback\<void>): void;<br>Differences: off(type: 'frameStart', callback?: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoOutput;<br>API declaration: on(type: 'frameEnd', callback: AsyncCallback\<void>): void;<br>Differences: on(type: 'frameEnd', callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoOutput;<br>API declaration: off(type: 'frameEnd', callback?: AsyncCallback\<void>): void;<br>Differences: off(type: 'frameEnd', callback?: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoOutput;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: VideoOutput;<br>API declaration: off(type: 'error', callback?: ErrorCallback): void;<br>Differences: off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: enum MetadataObjectType<br>Differences: enum MetadataObjectType|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: MetadataObjectType;<br>API declaration: FACE_DETECTION = 0<br>Differences: FACE_DETECTION = 0|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface Rect<br>Differences: interface Rect|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Rect;<br>API declaration: topLeftX: number;<br>Differences: topLeftX: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Rect;<br>API declaration: topLeftY: number;<br>Differences: topLeftY: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Rect;<br>API declaration: width: number;<br>Differences: width: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: Rect;<br>API declaration: height: number;<br>Differences: height: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface MetadataObject<br>Differences: interface MetadataObject|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: MetadataObject;<br>API declaration: readonly type: MetadataObjectType;<br>Differences: readonly type: MetadataObjectType;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: MetadataObject;<br>API declaration: readonly timestamp: number;<br>Differences: readonly timestamp: number;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: MetadataObject;<br>API declaration: readonly boundingBox: Rect;<br>Differences: readonly boundingBox: Rect;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: camera;<br>API declaration: interface MetadataOutput<br>Differences: interface MetadataOutput|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: MetadataOutput;<br>API declaration: start(callback: AsyncCallback\<void>): void;<br>Differences: start(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: MetadataOutput;<br>API declaration: start(): Promise\<void>;<br>Differences: start(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: MetadataOutput;<br>API declaration: stop(callback: AsyncCallback\<void>): void;<br>Differences: stop(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: MetadataOutput;<br>API declaration: stop(): Promise\<void>;<br>Differences: stop(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: MetadataOutput;<br>API declaration: on(type: 'metadataObjectsAvailable', callback: AsyncCallback\<Array\<MetadataObject>>): void;<br>Differences: on(type: 'metadataObjectsAvailable', callback: AsyncCallback\<Array\<MetadataObject>>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: MetadataOutput;<br>API declaration: off(type: 'metadataObjectsAvailable', callback?: AsyncCallback\<Array\<MetadataObject>>): void;<br>Differences: off(type: 'metadataObjectsAvailable', callback?: AsyncCallback\<Array\<MetadataObject>>): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: MetadataOutput;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: MetadataOutput;<br>API declaration: off(type: 'error', callback?: ErrorCallback): void;<br>Differences: off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace cameraPicker<br>Differences: declare namespace cameraPicker|api/@ohos.multimedia.cameraPicker.d.ts|
|New API|NA|Class name: cameraPicker;<br>API declaration: class PickerProfile<br>Differences: class PickerProfile|api/@ohos.multimedia.cameraPicker.d.ts|
|New API|NA|Class name: PickerProfile;<br>API declaration: cameraPosition: camera.CameraPosition;<br>Differences: cameraPosition: camera.CameraPosition;|api/@ohos.multimedia.cameraPicker.d.ts|
|New API|NA|Class name: PickerProfile;<br>API declaration: saveUri?: string;<br>Differences: saveUri?: string;|api/@ohos.multimedia.cameraPicker.d.ts|
|New API|NA|Class name: PickerProfile;<br>API declaration: videoDuration?: number;<br>Differences: videoDuration?: number;|api/@ohos.multimedia.cameraPicker.d.ts|
|New API|NA|Class name: cameraPicker;<br>API declaration: enum PickerMediaType<br>Differences: enum PickerMediaType|api/@ohos.multimedia.cameraPicker.d.ts|
|New API|NA|Class name: PickerMediaType;<br>API declaration: PHOTO = 'photo'<br>Differences: PHOTO = 'photo'|api/@ohos.multimedia.cameraPicker.d.ts|
|New API|NA|Class name: PickerMediaType;<br>API declaration: VIDEO = 'video'<br>Differences: VIDEO = 'video'|api/@ohos.multimedia.cameraPicker.d.ts|
|New API|NA|Class name: cameraPicker;<br>API declaration: class PickerResult<br>Differences: class PickerResult|api/@ohos.multimedia.cameraPicker.d.ts|
|New API|NA|Class name: PickerResult;<br>API declaration: resultCode: number;<br>Differences: resultCode: number;|api/@ohos.multimedia.cameraPicker.d.ts|
|New API|NA|Class name: PickerResult;<br>API declaration: resultUri: string;<br>Differences: resultUri: string;|api/@ohos.multimedia.cameraPicker.d.ts|
|New API|NA|Class name: PickerResult;<br>API declaration: mediaType: PickerMediaType;<br>Differences: mediaType: PickerMediaType;|api/@ohos.multimedia.cameraPicker.d.ts|
|New API|NA|Class name: cameraPicker;<br>API declaration: function pick(context: Context, mediaTypes: Array\<PickerMediaType>, pickerProfile: PickerProfile): Promise\<PickerResult>;<br>Differences: function pick(context: Context, mediaTypes: Array\<PickerMediaType>, pickerProfile: PickerProfile): Promise\<PickerResult>;|api/@ohos.multimedia.cameraPicker.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.multimedia.camera.d.ts<br>Differences: CameraKit|api/@ohos.multimedia.camera.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.multimedia.cameraPicker.d.ts<br>Differences: CameraKit|api/@ohos.multimedia.cameraPicker.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.CameraKit.d.ts<br>Differences: CameraKit|kits/@kit.CameraKit.d.ts|
