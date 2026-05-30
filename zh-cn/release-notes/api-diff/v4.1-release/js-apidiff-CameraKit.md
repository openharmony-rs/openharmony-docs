| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace camera<br>差异内容：declare namespace camera|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：function getCameraManager(context: Context): CameraManager;<br>差异内容：function getCameraManager(context: Context): CameraManager;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum CameraStatus<br>差异内容：enum CameraStatus|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraStatus；<br>API声明：CAMERA_STATUS_APPEAR = 0<br>差异内容：CAMERA_STATUS_APPEAR = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraStatus；<br>API声明：CAMERA_STATUS_DISAPPEAR = 1<br>差异内容：CAMERA_STATUS_DISAPPEAR = 1|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraStatus；<br>API声明：CAMERA_STATUS_AVAILABLE = 2<br>差异内容：CAMERA_STATUS_AVAILABLE = 2|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraStatus；<br>API声明：CAMERA_STATUS_UNAVAILABLE = 3<br>差异内容：CAMERA_STATUS_UNAVAILABLE = 3|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface Profile<br>差异内容：interface Profile|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Profile；<br>API声明：readonly format: CameraFormat;<br>差异内容：readonly format: CameraFormat;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Profile；<br>API声明：readonly size: Size;<br>差异内容：readonly size: Size;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface FrameRateRange<br>差异内容：interface FrameRateRange|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FrameRateRange；<br>API声明：readonly min: number;<br>差异内容：readonly min: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FrameRateRange；<br>API声明：readonly max: number;<br>差异内容：readonly max: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface VideoProfile<br>差异内容：interface VideoProfile|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoProfile；<br>API声明：readonly frameRateRange: FrameRateRange;<br>差异内容：readonly frameRateRange: FrameRateRange;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface CameraOutputCapability<br>差异内容：interface CameraOutputCapability|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraOutputCapability；<br>API声明：readonly previewProfiles: Array\<Profile>;<br>差异内容：readonly previewProfiles: Array\<Profile>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraOutputCapability；<br>API声明：readonly photoProfiles: Array\<Profile>;<br>差异内容：readonly photoProfiles: Array\<Profile>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraOutputCapability；<br>API声明：readonly videoProfiles: Array\<VideoProfile>;<br>差异内容：readonly videoProfiles: Array\<VideoProfile>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraOutputCapability；<br>API声明：readonly supportedMetadataObjectTypes: Array\<MetadataObjectType>;<br>差异内容：readonly supportedMetadataObjectTypes: Array\<MetadataObjectType>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum CameraErrorCode<br>差异内容：enum CameraErrorCode|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraErrorCode；<br>API声明：INVALID_ARGUMENT = 7400101<br>差异内容：INVALID_ARGUMENT = 7400101|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraErrorCode；<br>API声明：OPERATION_NOT_ALLOWED = 7400102<br>差异内容：OPERATION_NOT_ALLOWED = 7400102|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraErrorCode；<br>API声明：SESSION_NOT_CONFIG = 7400103<br>差异内容：SESSION_NOT_CONFIG = 7400103|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraErrorCode；<br>API声明：SESSION_NOT_RUNNING = 7400104<br>差异内容：SESSION_NOT_RUNNING = 7400104|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraErrorCode；<br>API声明：SESSION_CONFIG_LOCKED = 7400105<br>差异内容：SESSION_CONFIG_LOCKED = 7400105|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraErrorCode；<br>API声明：DEVICE_SETTING_LOCKED = 7400106<br>差异内容：DEVICE_SETTING_LOCKED = 7400106|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraErrorCode；<br>API声明：CONFLICT_CAMERA = 7400107<br>差异内容：CONFLICT_CAMERA = 7400107|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraErrorCode；<br>API声明：DEVICE_DISABLED = 7400108<br>差异内容：DEVICE_DISABLED = 7400108|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraErrorCode；<br>API声明：DEVICE_PREEMPTED = 7400109<br>差异内容：DEVICE_PREEMPTED = 7400109|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraErrorCode；<br>API声明：SERVICE_FATAL_ERROR = 7400201<br>差异内容：SERVICE_FATAL_ERROR = 7400201|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface CameraManager<br>差异内容：interface CameraManager|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：getSupportedCameras(): Array\<CameraDevice>;<br>差异内容：getSupportedCameras(): Array\<CameraDevice>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：getSupportedOutputCapability(camera: CameraDevice): CameraOutputCapability;<br>差异内容：getSupportedOutputCapability(camera: CameraDevice): CameraOutputCapability;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：getSupportedOutputCapability(camera: CameraDevice, mode: SceneMode): CameraOutputCapability;<br>差异内容：getSupportedOutputCapability(camera: CameraDevice, mode: SceneMode): CameraOutputCapability;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：getSupportedSceneModes(camera: CameraDevice): Array\<SceneMode>;<br>差异内容：getSupportedSceneModes(camera: CameraDevice): Array\<SceneMode>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：isCameraMuted(): boolean;<br>差异内容：isCameraMuted(): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：createCameraInput(camera: CameraDevice): CameraInput;<br>差异内容：createCameraInput(camera: CameraDevice): CameraInput;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：createCameraInput(position: CameraPosition, type: CameraType): CameraInput;<br>差异内容：createCameraInput(position: CameraPosition, type: CameraType): CameraInput;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：createPreviewOutput(profile: Profile, surfaceId: string): PreviewOutput;<br>差异内容：createPreviewOutput(profile: Profile, surfaceId: string): PreviewOutput;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：createPhotoOutput(profile: Profile, surfaceId: string): PhotoOutput;<br>差异内容：createPhotoOutput(profile: Profile, surfaceId: string): PhotoOutput;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：createPhotoOutput(profile: Profile): PhotoOutput;<br>差异内容：createPhotoOutput(profile: Profile): PhotoOutput;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：createVideoOutput(profile: VideoProfile, surfaceId: string): VideoOutput;<br>差异内容：createVideoOutput(profile: VideoProfile, surfaceId: string): VideoOutput;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：createMetadataOutput(metadataObjectTypes: Array\<MetadataObjectType>): MetadataOutput;<br>差异内容：createMetadataOutput(metadataObjectTypes: Array\<MetadataObjectType>): MetadataOutput;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：createCaptureSession(): CaptureSession;<br>差异内容：createCaptureSession(): CaptureSession;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：createSession\<T extends Session>(mode: SceneMode): T;<br>差异内容：createSession\<T extends Session>(mode: SceneMode): T;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：on(type: 'cameraStatus', callback: AsyncCallback\<CameraStatusInfo>): void;<br>差异内容：on(type: 'cameraStatus', callback: AsyncCallback\<CameraStatusInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：off(type: 'cameraStatus', callback?: AsyncCallback\<CameraStatusInfo>): void;<br>差异内容：off(type: 'cameraStatus', callback?: AsyncCallback\<CameraStatusInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：isTorchSupported(): boolean;<br>差异内容：isTorchSupported(): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：isTorchModeSupported(mode: TorchMode): boolean;<br>差异内容：isTorchModeSupported(mode: TorchMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：getTorchMode(): TorchMode;<br>差异内容：getTorchMode(): TorchMode;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：setTorchMode(mode: TorchMode): void;<br>差异内容：setTorchMode(mode: TorchMode): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：on(type: 'torchStatusChange', callback: AsyncCallback\<TorchStatusInfo>): void;<br>差异内容：on(type: 'torchStatusChange', callback: AsyncCallback\<TorchStatusInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：off(type: 'torchStatusChange', callback?: AsyncCallback\<TorchStatusInfo>): void;<br>差异内容：off(type: 'torchStatusChange', callback?: AsyncCallback\<TorchStatusInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface TorchStatusInfo<br>差异内容：interface TorchStatusInfo|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：TorchStatusInfo；<br>API声明：readonly isTorchAvailable: boolean;<br>差异内容：readonly isTorchAvailable: boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：TorchStatusInfo；<br>API声明：readonly isTorchActive: boolean;<br>差异内容：readonly isTorchActive: boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：TorchStatusInfo；<br>API声明：readonly torchLevel: number;<br>差异内容：readonly torchLevel: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum TorchMode<br>差异内容：enum TorchMode|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：TorchMode；<br>API声明：OFF = 0<br>差异内容：OFF = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：TorchMode；<br>API声明：ON = 1<br>差异内容：ON = 1|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：TorchMode；<br>API声明：AUTO = 2<br>差异内容：AUTO = 2|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface CameraStatusInfo<br>差异内容：interface CameraStatusInfo|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraStatusInfo；<br>API声明：camera: CameraDevice;<br>差异内容：camera: CameraDevice;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraStatusInfo；<br>API声明：status: CameraStatus;<br>差异内容：status: CameraStatus;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum CameraPosition<br>差异内容：enum CameraPosition|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraPosition；<br>API声明：CAMERA_POSITION_UNSPECIFIED = 0<br>差异内容：CAMERA_POSITION_UNSPECIFIED = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraPosition；<br>API声明：CAMERA_POSITION_BACK = 1<br>差异内容：CAMERA_POSITION_BACK = 1|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraPosition；<br>API声明：CAMERA_POSITION_FRONT = 2<br>差异内容：CAMERA_POSITION_FRONT = 2|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraPosition；<br>API声明：CAMERA_POSITION_FOLD_INNER = 3<br>差异内容：CAMERA_POSITION_FOLD_INNER = 3|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum CameraType<br>差异内容：enum CameraType|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraType；<br>API声明：CAMERA_TYPE_DEFAULT = 0<br>差异内容：CAMERA_TYPE_DEFAULT = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraType；<br>API声明：CAMERA_TYPE_WIDE_ANGLE = 1<br>差异内容：CAMERA_TYPE_WIDE_ANGLE = 1|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraType；<br>API声明：CAMERA_TYPE_ULTRA_WIDE = 2<br>差异内容：CAMERA_TYPE_ULTRA_WIDE = 2|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraType；<br>API声明：CAMERA_TYPE_TELEPHOTO = 3<br>差异内容：CAMERA_TYPE_TELEPHOTO = 3|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraType；<br>API声明：CAMERA_TYPE_TRUE_DEPTH = 4<br>差异内容：CAMERA_TYPE_TRUE_DEPTH = 4|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum ConnectionType<br>差异内容：enum ConnectionType|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：ConnectionType；<br>API声明：CAMERA_CONNECTION_BUILT_IN = 0<br>差异内容：CAMERA_CONNECTION_BUILT_IN = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：ConnectionType；<br>API声明：CAMERA_CONNECTION_USB_PLUGIN = 1<br>差异内容：CAMERA_CONNECTION_USB_PLUGIN = 1|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：ConnectionType；<br>API声明：CAMERA_CONNECTION_REMOTE = 2<br>差异内容：CAMERA_CONNECTION_REMOTE = 2|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface CameraDevice<br>差异内容：interface CameraDevice|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraDevice；<br>API声明：readonly cameraId: string;<br>差异内容：readonly cameraId: string;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraDevice；<br>API声明：readonly cameraPosition: CameraPosition;<br>差异内容：readonly cameraPosition: CameraPosition;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraDevice；<br>API声明：readonly cameraType: CameraType;<br>差异内容：readonly cameraType: CameraType;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraDevice；<br>API声明：readonly connectionType: ConnectionType;<br>差异内容：readonly connectionType: ConnectionType;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface Size<br>差异内容：interface Size|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Size；<br>API声明：height: number;<br>差异内容：height: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Size；<br>API声明：width: number;<br>差异内容：width: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface Point<br>差异内容：interface Point|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Point；<br>API声明：x: number;<br>差异内容：x: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Point；<br>API声明：y: number;<br>差异内容：y: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface CameraInput<br>差异内容：interface CameraInput|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraInput；<br>API声明：open(callback: AsyncCallback\<void>): void;<br>差异内容：open(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraInput；<br>API声明：open(): Promise\<void>;<br>差异内容：open(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraInput；<br>API声明：close(callback: AsyncCallback\<void>): void;<br>差异内容：close(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraInput；<br>API声明：close(): Promise\<void>;<br>差异内容：close(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraInput；<br>API声明：on(type: 'error', camera: CameraDevice, callback: ErrorCallback): void;<br>差异内容：on(type: 'error', camera: CameraDevice, callback: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraInput；<br>API声明：off(type: 'error', camera: CameraDevice, callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', camera: CameraDevice, callback?: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum SceneMode<br>差异内容：enum SceneMode|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：SceneMode；<br>API声明：NORMAL_PHOTO = 1<br>差异内容：NORMAL_PHOTO = 1|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：SceneMode；<br>API声明：NORMAL_VIDEO = 2<br>差异内容：NORMAL_VIDEO = 2|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum CameraFormat<br>差异内容：enum CameraFormat|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraFormat；<br>API声明：CAMERA_FORMAT_RGBA_8888 = 3<br>差异内容：CAMERA_FORMAT_RGBA_8888 = 3|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraFormat；<br>API声明：CAMERA_FORMAT_YUV_420_SP = 1003<br>差异内容：CAMERA_FORMAT_YUV_420_SP = 1003|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraFormat；<br>API声明：CAMERA_FORMAT_JPEG = 2000<br>差异内容：CAMERA_FORMAT_JPEG = 2000|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraFormat；<br>API声明：CAMERA_FORMAT_YCBCR_P010<br>差异内容：CAMERA_FORMAT_YCBCR_P010|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraFormat；<br>API声明：CAMERA_FORMAT_YCRCB_P010<br>差异内容：CAMERA_FORMAT_YCRCB_P010|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum FlashMode<br>差异内容：enum FlashMode|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FlashMode；<br>API声明：FLASH_MODE_CLOSE = 0<br>差异内容：FLASH_MODE_CLOSE = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FlashMode；<br>API声明：FLASH_MODE_OPEN = 1<br>差异内容：FLASH_MODE_OPEN = 1|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FlashMode；<br>API声明：FLASH_MODE_AUTO = 2<br>差异内容：FLASH_MODE_AUTO = 2|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FlashMode；<br>API声明：FLASH_MODE_ALWAYS_OPEN = 3<br>差异内容：FLASH_MODE_ALWAYS_OPEN = 3|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface Flash<br>差异内容：interface Flash|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Flash；<br>API声明：hasFlash(): boolean;<br>差异内容：hasFlash(): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Flash；<br>API声明：isFlashModeSupported(flashMode: FlashMode): boolean;<br>差异内容：isFlashModeSupported(flashMode: FlashMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Flash；<br>API声明：getFlashMode(): FlashMode;<br>差异内容：getFlashMode(): FlashMode;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Flash；<br>API声明：setFlashMode(flashMode: FlashMode): void;<br>差异内容：setFlashMode(flashMode: FlashMode): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum ExposureMode<br>差异内容：enum ExposureMode|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：ExposureMode；<br>API声明：EXPOSURE_MODE_LOCKED = 0<br>差异内容：EXPOSURE_MODE_LOCKED = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：ExposureMode；<br>API声明：EXPOSURE_MODE_AUTO = 1<br>差异内容：EXPOSURE_MODE_AUTO = 1|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：ExposureMode；<br>API声明：EXPOSURE_MODE_CONTINUOUS_AUTO = 2<br>差异内容：EXPOSURE_MODE_CONTINUOUS_AUTO = 2|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface AutoExposure<br>差异内容：interface AutoExposure|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：AutoExposure；<br>API声明：isExposureModeSupported(aeMode: ExposureMode): boolean;<br>差异内容：isExposureModeSupported(aeMode: ExposureMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：AutoExposure；<br>API声明：getExposureMode(): ExposureMode;<br>差异内容：getExposureMode(): ExposureMode;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：AutoExposure；<br>API声明：setExposureMode(aeMode: ExposureMode): void;<br>差异内容：setExposureMode(aeMode: ExposureMode): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：AutoExposure；<br>API声明：getMeteringPoint(): Point;<br>差异内容：getMeteringPoint(): Point;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：AutoExposure；<br>API声明：setMeteringPoint(point: Point): void;<br>差异内容：setMeteringPoint(point: Point): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：AutoExposure；<br>API声明：getExposureBiasRange(): Array\<number>;<br>差异内容：getExposureBiasRange(): Array\<number>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：AutoExposure；<br>API声明：setExposureBias(exposureBias: number): void;<br>差异内容：setExposureBias(exposureBias: number): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：AutoExposure；<br>API声明：getExposureValue(): number;<br>差异内容：getExposureValue(): number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum FocusMode<br>差异内容：enum FocusMode|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FocusMode；<br>API声明：FOCUS_MODE_MANUAL = 0<br>差异内容：FOCUS_MODE_MANUAL = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FocusMode；<br>API声明：FOCUS_MODE_CONTINUOUS_AUTO = 1<br>差异内容：FOCUS_MODE_CONTINUOUS_AUTO = 1|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FocusMode；<br>API声明：FOCUS_MODE_AUTO = 2<br>差异内容：FOCUS_MODE_AUTO = 2|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FocusMode；<br>API声明：FOCUS_MODE_LOCKED = 3<br>差异内容：FOCUS_MODE_LOCKED = 3|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum FocusState<br>差异内容：enum FocusState|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FocusState；<br>API声明：FOCUS_STATE_SCAN = 0<br>差异内容：FOCUS_STATE_SCAN = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FocusState；<br>API声明：FOCUS_STATE_FOCUSED = 1<br>差异内容：FOCUS_STATE_FOCUSED = 1|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FocusState；<br>API声明：FOCUS_STATE_UNFOCUSED = 2<br>差异内容：FOCUS_STATE_UNFOCUSED = 2|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface Focus<br>差异内容：interface Focus|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Focus；<br>API声明：isFocusModeSupported(afMode: FocusMode): boolean;<br>差异内容：isFocusModeSupported(afMode: FocusMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Focus；<br>API声明：getFocusMode(): FocusMode;<br>差异内容：getFocusMode(): FocusMode;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Focus；<br>API声明：setFocusMode(afMode: FocusMode): void;<br>差异内容：setFocusMode(afMode: FocusMode): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Focus；<br>API声明：setFocusPoint(point: Point): void;<br>差异内容：setFocusPoint(point: Point): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Focus；<br>API声明：getFocusPoint(): Point;<br>差异内容：getFocusPoint(): Point;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Focus；<br>API声明：getFocalLength(): number;<br>差异内容：getFocalLength(): number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum SmoothZoomMode<br>差异内容：enum SmoothZoomMode|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：SmoothZoomMode；<br>API声明：NORMAL = 0<br>差异内容：NORMAL = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface SmoothZoomInfo<br>差异内容：interface SmoothZoomInfo|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：SmoothZoomInfo；<br>API声明：duration: number;<br>差异内容：duration: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface Zoom<br>差异内容：interface Zoom|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Zoom；<br>API声明：getZoomRatioRange(): Array\<number>;<br>差异内容：getZoomRatioRange(): Array\<number>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Zoom；<br>API声明：getZoomRatio(): number;<br>差异内容：getZoomRatio(): number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Zoom；<br>API声明：setZoomRatio(zoomRatio: number): void;<br>差异内容：setZoomRatio(zoomRatio: number): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Zoom；<br>API声明：setSmoothZoom(targetRatio: number, mode?: SmoothZoomMode): void;<br>差异内容：setSmoothZoom(targetRatio: number, mode?: SmoothZoomMode): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum VideoStabilizationMode<br>差异内容：enum VideoStabilizationMode|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoStabilizationMode；<br>API声明：OFF = 0<br>差异内容：OFF = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoStabilizationMode；<br>API声明：LOW = 1<br>差异内容：LOW = 1|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoStabilizationMode；<br>API声明：MIDDLE = 2<br>差异内容：MIDDLE = 2|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoStabilizationMode；<br>API声明：HIGH = 3<br>差异内容：HIGH = 3|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoStabilizationMode；<br>API声明：AUTO = 4<br>差异内容：AUTO = 4|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface Stabilization<br>差异内容：interface Stabilization|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Stabilization；<br>API声明：isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean;<br>差异内容：isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Stabilization；<br>API声明：getActiveVideoStabilizationMode(): VideoStabilizationMode;<br>差异内容：getActiveVideoStabilizationMode(): VideoStabilizationMode;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Stabilization；<br>API声明：setVideoStabilizationMode(mode: VideoStabilizationMode): void;<br>差异内容：setVideoStabilizationMode(mode: VideoStabilizationMode): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface Session<br>差异内容：interface Session|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Session；<br>API声明：beginConfig(): void;<br>差异内容：beginConfig(): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Session；<br>API声明：commitConfig(callback: AsyncCallback\<void>): void;<br>差异内容：commitConfig(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Session；<br>API声明：commitConfig(): Promise\<void>;<br>差异内容：commitConfig(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Session；<br>API声明：canAddInput(cameraInput: CameraInput): boolean;<br>差异内容：canAddInput(cameraInput: CameraInput): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Session；<br>API声明：addInput(cameraInput: CameraInput): void;<br>差异内容：addInput(cameraInput: CameraInput): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Session；<br>API声明：removeInput(cameraInput: CameraInput): void;<br>差异内容：removeInput(cameraInput: CameraInput): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Session；<br>API声明：canAddOutput(cameraOutput: CameraOutput): boolean;<br>差异内容：canAddOutput(cameraOutput: CameraOutput): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Session；<br>API声明：addOutput(cameraOutput: CameraOutput): void;<br>差异内容：addOutput(cameraOutput: CameraOutput): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Session；<br>API声明：removeOutput(cameraOutput: CameraOutput): void;<br>差异内容：removeOutput(cameraOutput: CameraOutput): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Session；<br>API声明：start(callback: AsyncCallback\<void>): void;<br>差异内容：start(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Session；<br>API声明：start(): Promise\<void>;<br>差异内容：start(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Session；<br>API声明：stop(callback: AsyncCallback\<void>): void;<br>差异内容：stop(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Session；<br>API声明：stop(): Promise\<void>;<br>差异内容：stop(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Session；<br>API声明：release(callback: AsyncCallback\<void>): void;<br>差异内容：release(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Session；<br>API声明：release(): Promise\<void>;<br>差异内容：release(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface CaptureSession<br>差异内容：interface CaptureSession|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：beginConfig(): void;<br>差异内容：beginConfig(): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：commitConfig(callback: AsyncCallback\<void>): void;<br>差异内容：commitConfig(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：commitConfig(): Promise\<void>;<br>差异内容：commitConfig(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：addInput(cameraInput: CameraInput): void;<br>差异内容：addInput(cameraInput: CameraInput): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：removeInput(cameraInput: CameraInput): void;<br>差异内容：removeInput(cameraInput: CameraInput): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：addOutput(cameraOutput: CameraOutput): void;<br>差异内容：addOutput(cameraOutput: CameraOutput): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：removeOutput(cameraOutput: CameraOutput): void;<br>差异内容：removeOutput(cameraOutput: CameraOutput): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：start(callback: AsyncCallback\<void>): void;<br>差异内容：start(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：start(): Promise\<void>;<br>差异内容：start(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：stop(callback: AsyncCallback\<void>): void;<br>差异内容：stop(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：stop(): Promise\<void>;<br>差异内容：stop(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：release(callback: AsyncCallback\<void>): void;<br>差异内容：release(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：release(): Promise\<void>;<br>差异内容：release(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：hasFlash(): boolean;<br>差异内容：hasFlash(): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：isFlashModeSupported(flashMode: FlashMode): boolean;<br>差异内容：isFlashModeSupported(flashMode: FlashMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：getFlashMode(): FlashMode;<br>差异内容：getFlashMode(): FlashMode;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：setFlashMode(flashMode: FlashMode): void;<br>差异内容：setFlashMode(flashMode: FlashMode): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：isExposureModeSupported(aeMode: ExposureMode): boolean;<br>差异内容：isExposureModeSupported(aeMode: ExposureMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：getExposureMode(): ExposureMode;<br>差异内容：getExposureMode(): ExposureMode;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：setExposureMode(aeMode: ExposureMode): void;<br>差异内容：setExposureMode(aeMode: ExposureMode): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：getMeteringPoint(): Point;<br>差异内容：getMeteringPoint(): Point;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：setMeteringPoint(point: Point): void;<br>差异内容：setMeteringPoint(point: Point): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：getExposureBiasRange(): Array\<number>;<br>差异内容：getExposureBiasRange(): Array\<number>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：setExposureBias(exposureBias: number): void;<br>差异内容：setExposureBias(exposureBias: number): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：getExposureValue(): number;<br>差异内容：getExposureValue(): number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：isFocusModeSupported(afMode: FocusMode): boolean;<br>差异内容：isFocusModeSupported(afMode: FocusMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：getFocusMode(): FocusMode;<br>差异内容：getFocusMode(): FocusMode;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：setFocusMode(afMode: FocusMode): void;<br>差异内容：setFocusMode(afMode: FocusMode): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：setFocusPoint(point: Point): void;<br>差异内容：setFocusPoint(point: Point): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：getFocusPoint(): Point;<br>差异内容：getFocusPoint(): Point;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：getFocalLength(): number;<br>差异内容：getFocalLength(): number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：getZoomRatioRange(): Array\<number>;<br>差异内容：getZoomRatioRange(): Array\<number>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：getZoomRatio(): number;<br>差异内容：getZoomRatio(): number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：setZoomRatio(zoomRatio: number): void;<br>差异内容：setZoomRatio(zoomRatio: number): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean;<br>差异内容：isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：getActiveVideoStabilizationMode(): VideoStabilizationMode;<br>差异内容：getActiveVideoStabilizationMode(): VideoStabilizationMode;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：setVideoStabilizationMode(mode: VideoStabilizationMode): void;<br>差异内容：setVideoStabilizationMode(mode: VideoStabilizationMode): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：on(type: 'focusStateChange', callback: AsyncCallback\<FocusState>): void;<br>差异内容：on(type: 'focusStateChange', callback: AsyncCallback\<FocusState>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：off(type: 'focusStateChange', callback?: AsyncCallback\<FocusState>): void;<br>差异内容：off(type: 'focusStateChange', callback?: AsyncCallback\<FocusState>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureSession；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface PhotoSession<br>差异内容：interface PhotoSession|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoSession；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoSession；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoSession；<br>API声明：on(type: 'focusStateChange', callback: AsyncCallback\<FocusState>): void;<br>差异内容：on(type: 'focusStateChange', callback: AsyncCallback\<FocusState>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoSession；<br>API声明：off(type: 'focusStateChange', callback?: AsyncCallback\<FocusState>): void;<br>差异内容：off(type: 'focusStateChange', callback?: AsyncCallback\<FocusState>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoSession；<br>API声明：on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback\<SmoothZoomInfo>): void;<br>差异内容：on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback\<SmoothZoomInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoSession；<br>API声明：off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback\<SmoothZoomInfo>): void;<br>差异内容：off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback\<SmoothZoomInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface VideoSession<br>差异内容：interface VideoSession|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoSession；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoSession；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoSession；<br>API声明：on(type: 'focusStateChange', callback: AsyncCallback\<FocusState>): void;<br>差异内容：on(type: 'focusStateChange', callback: AsyncCallback\<FocusState>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoSession；<br>API声明：off(type: 'focusStateChange', callback?: AsyncCallback\<FocusState>): void;<br>差异内容：off(type: 'focusStateChange', callback?: AsyncCallback\<FocusState>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoSession；<br>API声明：on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback\<SmoothZoomInfo>): void;<br>差异内容：on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback\<SmoothZoomInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoSession；<br>API声明：off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback\<SmoothZoomInfo>): void;<br>差异内容：off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback\<SmoothZoomInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface CameraOutput<br>差异内容：interface CameraOutput|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraOutput；<br>API声明：release(callback: AsyncCallback\<void>): void;<br>差异内容：release(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraOutput；<br>API声明：release(): Promise\<void>;<br>差异内容：release(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface PreviewOutput<br>差异内容：interface PreviewOutput|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreviewOutput；<br>API声明：start(callback: AsyncCallback\<void>): void;<br>差异内容：start(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreviewOutput；<br>API声明：start(): Promise\<void>;<br>差异内容：start(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreviewOutput；<br>API声明：stop(callback: AsyncCallback\<void>): void;<br>差异内容：stop(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreviewOutput；<br>API声明：stop(): Promise\<void>;<br>差异内容：stop(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreviewOutput；<br>API声明：on(type: 'frameStart', callback: AsyncCallback\<void>): void;<br>差异内容：on(type: 'frameStart', callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreviewOutput；<br>API声明：off(type: 'frameStart', callback?: AsyncCallback\<void>): void;<br>差异内容：off(type: 'frameStart', callback?: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreviewOutput；<br>API声明：on(type: 'frameEnd', callback: AsyncCallback\<void>): void;<br>差异内容：on(type: 'frameEnd', callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreviewOutput；<br>API声明：off(type: 'frameEnd', callback?: AsyncCallback\<void>): void;<br>差异内容：off(type: 'frameEnd', callback?: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreviewOutput；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreviewOutput；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum ImageRotation<br>差异内容：enum ImageRotation|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：ImageRotation；<br>API声明：ROTATION_0 = 0<br>差异内容：ROTATION_0 = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：ImageRotation；<br>API声明：ROTATION_90 = 90<br>差异内容：ROTATION_90 = 90|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：ImageRotation；<br>API声明：ROTATION_180 = 180<br>差异内容：ROTATION_180 = 180|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：ImageRotation；<br>API声明：ROTATION_270 = 270<br>差异内容：ROTATION_270 = 270|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface Location<br>差异内容：interface Location|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Location；<br>API声明：latitude: number;<br>差异内容：latitude: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Location；<br>API声明：longitude: number;<br>差异内容：longitude: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Location；<br>API声明：altitude: number;<br>差异内容：altitude: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum QualityLevel<br>差异内容：enum QualityLevel|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：QualityLevel；<br>API声明：QUALITY_LEVEL_HIGH = 0<br>差异内容：QUALITY_LEVEL_HIGH = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：QualityLevel；<br>API声明：QUALITY_LEVEL_MEDIUM = 1<br>差异内容：QUALITY_LEVEL_MEDIUM = 1|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：QualityLevel；<br>API声明：QUALITY_LEVEL_LOW = 2<br>差异内容：QUALITY_LEVEL_LOW = 2|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface PhotoCaptureSetting<br>差异内容：interface PhotoCaptureSetting|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoCaptureSetting；<br>API声明：quality?: QualityLevel;<br>差异内容：quality?: QualityLevel;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoCaptureSetting；<br>API声明：rotation?: ImageRotation;<br>差异内容：rotation?: ImageRotation;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoCaptureSetting；<br>API声明：location?: Location;<br>差异内容：location?: Location;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoCaptureSetting；<br>API声明：mirror?: boolean;<br>差异内容：mirror?: boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface Photo<br>差异内容：interface Photo|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Photo；<br>API声明：main: image.Image;<br>差异内容：main: image.Image;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Photo；<br>API声明：release(): Promise\<void>;<br>差异内容：release(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface PhotoOutput<br>差异内容：interface PhotoOutput|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：capture(callback: AsyncCallback\<void>): void;<br>差异内容：capture(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：capture(): Promise\<void>;<br>差异内容：capture(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：capture(setting: PhotoCaptureSetting, callback: AsyncCallback\<void>): void;<br>差异内容：capture(setting: PhotoCaptureSetting, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：capture(setting: PhotoCaptureSetting): Promise\<void>;<br>差异内容：capture(setting: PhotoCaptureSetting): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：on(type: 'photoAvailable', callback: AsyncCallback\<Photo>): void;<br>差异内容：on(type: 'photoAvailable', callback: AsyncCallback\<Photo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：off(type: 'photoAvailable', callback?: AsyncCallback\<Photo>): void;<br>差异内容：off(type: 'photoAvailable', callback?: AsyncCallback\<Photo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：isMirrorSupported(): boolean;<br>差异内容：isMirrorSupported(): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：on(type: 'captureStart', callback: AsyncCallback\<number>): void;<br>差异内容：on(type: 'captureStart', callback: AsyncCallback\<number>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：off(type: 'captureStart', callback?: AsyncCallback\<number>): void;<br>差异内容：off(type: 'captureStart', callback?: AsyncCallback\<number>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：on(type: 'captureStartWithInfo', callback: AsyncCallback\<CaptureStartInfo>): void;<br>差异内容：on(type: 'captureStartWithInfo', callback: AsyncCallback\<CaptureStartInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：off(type: 'captureStartWithInfo', callback?: AsyncCallback\<CaptureStartInfo>): void;<br>差异内容：off(type: 'captureStartWithInfo', callback?: AsyncCallback\<CaptureStartInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：on(type: 'frameShutter', callback: AsyncCallback\<FrameShutterInfo>): void;<br>差异内容：on(type: 'frameShutter', callback: AsyncCallback\<FrameShutterInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：off(type: 'frameShutter', callback?: AsyncCallback\<FrameShutterInfo>): void;<br>差异内容：off(type: 'frameShutter', callback?: AsyncCallback\<FrameShutterInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：on(type: 'captureEnd', callback: AsyncCallback\<CaptureEndInfo>): void;<br>差异内容：on(type: 'captureEnd', callback: AsyncCallback\<CaptureEndInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：off(type: 'captureEnd', callback?: AsyncCallback\<CaptureEndInfo>): void;<br>差异内容：off(type: 'captureEnd', callback?: AsyncCallback\<CaptureEndInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface FrameShutterInfo<br>差异内容：interface FrameShutterInfo|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FrameShutterInfo；<br>API声明：captureId: number;<br>差异内容：captureId: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FrameShutterInfo；<br>API声明：timestamp: number;<br>差异内容：timestamp: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface CaptureStartInfo<br>差异内容：interface CaptureStartInfo|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureStartInfo；<br>API声明：captureId: number;<br>差异内容：captureId: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureStartInfo；<br>API声明：time: number;<br>差异内容：time: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface CaptureEndInfo<br>差异内容：interface CaptureEndInfo|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureEndInfo；<br>API声明：captureId: number;<br>差异内容：captureId: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CaptureEndInfo；<br>API声明：frameCount: number;<br>差异内容：frameCount: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface VideoOutput<br>差异内容：interface VideoOutput|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoOutput；<br>API声明：start(callback: AsyncCallback\<void>): void;<br>差异内容：start(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoOutput；<br>API声明：start(): Promise\<void>;<br>差异内容：start(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoOutput；<br>API声明：stop(callback: AsyncCallback\<void>): void;<br>差异内容：stop(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoOutput；<br>API声明：stop(): Promise\<void>;<br>差异内容：stop(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoOutput；<br>API声明：on(type: 'frameStart', callback: AsyncCallback\<void>): void;<br>差异内容：on(type: 'frameStart', callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoOutput；<br>API声明：off(type: 'frameStart', callback?: AsyncCallback\<void>): void;<br>差异内容：off(type: 'frameStart', callback?: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoOutput；<br>API声明：on(type: 'frameEnd', callback: AsyncCallback\<void>): void;<br>差异内容：on(type: 'frameEnd', callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoOutput；<br>API声明：off(type: 'frameEnd', callback?: AsyncCallback\<void>): void;<br>差异内容：off(type: 'frameEnd', callback?: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoOutput；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoOutput；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum MetadataObjectType<br>差异内容：enum MetadataObjectType|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：MetadataObjectType；<br>API声明：FACE_DETECTION = 0<br>差异内容：FACE_DETECTION = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface Rect<br>差异内容：interface Rect|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Rect；<br>API声明：topLeftX: number;<br>差异内容：topLeftX: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Rect；<br>API声明：topLeftY: number;<br>差异内容：topLeftY: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Rect；<br>API声明：width: number;<br>差异内容：width: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：Rect；<br>API声明：height: number;<br>差异内容：height: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface MetadataObject<br>差异内容：interface MetadataObject|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：MetadataObject；<br>API声明：readonly type: MetadataObjectType;<br>差异内容：readonly type: MetadataObjectType;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：MetadataObject；<br>API声明：readonly timestamp: number;<br>差异内容：readonly timestamp: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：MetadataObject；<br>API声明：readonly boundingBox: Rect;<br>差异内容：readonly boundingBox: Rect;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface MetadataOutput<br>差异内容：interface MetadataOutput|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：MetadataOutput；<br>API声明：start(callback: AsyncCallback\<void>): void;<br>差异内容：start(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：MetadataOutput；<br>API声明：start(): Promise\<void>;<br>差异内容：start(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：MetadataOutput；<br>API声明：stop(callback: AsyncCallback\<void>): void;<br>差异内容：stop(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：MetadataOutput；<br>API声明：stop(): Promise\<void>;<br>差异内容：stop(): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：MetadataOutput；<br>API声明：on(type: 'metadataObjectsAvailable', callback: AsyncCallback\<Array\<MetadataObject>>): void;<br>差异内容：on(type: 'metadataObjectsAvailable', callback: AsyncCallback\<Array\<MetadataObject>>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：MetadataOutput；<br>API声明：off(type: 'metadataObjectsAvailable', callback?: AsyncCallback\<Array\<MetadataObject>>): void;<br>差异内容：off(type: 'metadataObjectsAvailable', callback?: AsyncCallback\<Array\<MetadataObject>>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：MetadataOutput；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：MetadataOutput；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace cameraPicker<br>差异内容：declare namespace cameraPicker|api/@ohos.multimedia.cameraPicker.d.ts|
|新增API|NA|类名：cameraPicker；<br>API声明：class PickerProfile<br>差异内容：class PickerProfile|api/@ohos.multimedia.cameraPicker.d.ts|
|新增API|NA|类名：PickerProfile；<br>API声明：cameraPosition: camera.CameraPosition;<br>差异内容：cameraPosition: camera.CameraPosition;|api/@ohos.multimedia.cameraPicker.d.ts|
|新增API|NA|类名：PickerProfile；<br>API声明：saveUri?: string;<br>差异内容：saveUri?: string;|api/@ohos.multimedia.cameraPicker.d.ts|
|新增API|NA|类名：PickerProfile；<br>API声明：videoDuration?: number;<br>差异内容：videoDuration?: number;|api/@ohos.multimedia.cameraPicker.d.ts|
|新增API|NA|类名：cameraPicker；<br>API声明：enum PickerMediaType<br>差异内容：enum PickerMediaType|api/@ohos.multimedia.cameraPicker.d.ts|
|新增API|NA|类名：PickerMediaType；<br>API声明：PHOTO = 'photo'<br>差异内容：PHOTO = 'photo'|api/@ohos.multimedia.cameraPicker.d.ts|
|新增API|NA|类名：PickerMediaType；<br>API声明：VIDEO = 'video'<br>差异内容：VIDEO = 'video'|api/@ohos.multimedia.cameraPicker.d.ts|
|新增API|NA|类名：cameraPicker；<br>API声明：class PickerResult<br>差异内容：class PickerResult|api/@ohos.multimedia.cameraPicker.d.ts|
|新增API|NA|类名：PickerResult；<br>API声明：resultCode: number;<br>差异内容：resultCode: number;|api/@ohos.multimedia.cameraPicker.d.ts|
|新增API|NA|类名：PickerResult；<br>API声明：resultUri: string;<br>差异内容：resultUri: string;|api/@ohos.multimedia.cameraPicker.d.ts|
|新增API|NA|类名：PickerResult；<br>API声明：mediaType: PickerMediaType;<br>差异内容：mediaType: PickerMediaType;|api/@ohos.multimedia.cameraPicker.d.ts|
|新增API|NA|类名：cameraPicker；<br>API声明：function pick(context: Context, mediaTypes: Array\<PickerMediaType>, pickerProfile: PickerProfile): Promise\<PickerResult>;<br>差异内容：function pick(context: Context, mediaTypes: Array\<PickerMediaType>, pickerProfile: PickerProfile): Promise\<PickerResult>;|api/@ohos.multimedia.cameraPicker.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.multimedia.camera.d.ts<br>差异内容：CameraKit|api/@ohos.multimedia.camera.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.multimedia.cameraPicker.d.ts<br>差异内容：CameraKit|api/@ohos.multimedia.cameraPicker.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.CameraKit.d.ts<br>差异内容：CameraKit|kits/@kit.CameraKit.d.ts|
