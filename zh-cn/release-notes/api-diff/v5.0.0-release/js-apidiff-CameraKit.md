| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API废弃版本变更|类名：CameraPosition；<br>API声明：CAMERA_POSITION_FOLD_INNER = 3<br>差异内容：NA|类名：CameraPosition；<br>API声明：CAMERA_POSITION_FOLD_INNER = 3<br>差异内容：12|api/@ohos.multimedia.camera.d.ts|
|新增错误码|类名：CameraManager；<br>API声明：createCameraInput(camera: CameraDevice): CameraInput;<br>差异内容：NA|类名：CameraManager；<br>API声明：createCameraInput(camera: CameraDevice): CameraInput;<br>差异内容：7400102,7400201|api/@ohos.multimedia.camera.d.ts|
|新增错误码|类名：CameraManager；<br>API声明：createCameraInput(position: CameraPosition, type: CameraType): CameraInput;<br>差异内容：NA|类名：CameraManager；<br>API声明：createCameraInput(position: CameraPosition, type: CameraType): CameraInput;<br>差异内容：7400102,7400201|api/@ohos.multimedia.camera.d.ts|
|新增错误码|类名：CameraManager；<br>API声明：createPreviewOutput(profile: Profile, surfaceId: string): PreviewOutput;<br>差异内容：NA|类名：CameraManager；<br>API声明：createPreviewOutput(profile: Profile, surfaceId: string): PreviewOutput;<br>差异内容：7400201|api/@ohos.multimedia.camera.d.ts|
|新增错误码|类名：CameraManager；<br>API声明：createPhotoOutput(profile: Profile): PhotoOutput;<br>差异内容：NA|类名：CameraManager；<br>API声明：createPhotoOutput(profile?: Profile): PhotoOutput;<br>差异内容：7400201|api/@ohos.multimedia.camera.d.ts|
|新增错误码|类名：CameraManager；<br>API声明：createVideoOutput(profile: VideoProfile, surfaceId: string): VideoOutput;<br>差异内容：NA|类名：CameraManager；<br>API声明：createVideoOutput(profile: VideoProfile, surfaceId: string): VideoOutput;<br>差异内容：7400201|api/@ohos.multimedia.camera.d.ts|
|新增错误码|类名：CameraManager；<br>API声明：createMetadataOutput(metadataObjectTypes: Array\<MetadataObjectType>): MetadataOutput;<br>差异内容：NA|类名：CameraManager；<br>API声明：createMetadataOutput(metadataObjectTypes: Array\<MetadataObjectType>): MetadataOutput;<br>差异内容：7400201|api/@ohos.multimedia.camera.d.ts|
|新增错误码|类名：CameraManager；<br>API声明：setTorchMode(mode: TorchMode): void;<br>差异内容：NA|类名：CameraManager；<br>API声明：setTorchMode(mode: TorchMode): void;<br>差异内容：7400102,7400201|api/@ohos.multimedia.camera.d.ts|
|新增错误码|类名：AutoExposure；<br>API声明：setExposureBias(exposureBias: number): void;<br>差异内容：NA|类名：AutoExposure；<br>API声明：setExposureBias(exposureBias: number): void;<br>差异内容：7400102|api/@ohos.multimedia.camera.d.ts|
|新增错误码|类名：Zoom；<br>API声明：getZoomRatio(): number;<br>差异内容：NA|类名：Zoom；<br>API声明：getZoomRatio(): number;<br>差异内容：7400201|api/@ohos.multimedia.camera.d.ts|
|新增错误码|类名：Session；<br>API声明：beginConfig(): void;<br>差异内容：NA|类名：Session；<br>API声明：beginConfig(): void;<br>差异内容：7400201|api/@ohos.multimedia.camera.d.ts|
|新增错误码|类名：Session；<br>API声明：addInput(cameraInput: CameraInput): void;<br>差异内容：NA|类名：Session；<br>API声明：addInput(cameraInput: CameraInput): void;<br>差异内容：7400201|api/@ohos.multimedia.camera.d.ts|
|新增错误码|类名：Session；<br>API声明：removeInput(cameraInput: CameraInput): void;<br>差异内容：NA|类名：Session；<br>API声明：removeInput(cameraInput: CameraInput): void;<br>差异内容：7400201|api/@ohos.multimedia.camera.d.ts|
|新增错误码|类名：Session；<br>API声明：addOutput(cameraOutput: CameraOutput): void;<br>差异内容：NA|类名：Session；<br>API声明：addOutput(cameraOutput: CameraOutput): void;<br>差异内容：7400201|api/@ohos.multimedia.camera.d.ts|
|新增错误码|类名：Session；<br>API声明：removeOutput(cameraOutput: CameraOutput): void;<br>差异内容：NA|类名：Session；<br>API声明：removeOutput(cameraOutput: CameraOutput): void;<br>差异内容：7400201|api/@ohos.multimedia.camera.d.ts|
|新增错误码|类名：Session；<br>API声明：start(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Session；<br>API声明：start(callback: AsyncCallback\<void>): void;<br>差异内容：7400102|api/@ohos.multimedia.camera.d.ts|
|新增错误码|类名：Session；<br>API声明：start(): Promise\<void>;<br>差异内容：NA|类名：Session；<br>API声明：start(): Promise\<void>;<br>差异内容：7400102|api/@ohos.multimedia.camera.d.ts|
|函数变更|类名：CameraManager；<br>API声明：createPhotoOutput(profile: Profile): PhotoOutput;<br>差异内容：profile: Profile|类名：CameraManager；<br>API声明：createPhotoOutput(profile?: Profile): PhotoOutput;<br>差异内容：profile?: Profile|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraInput；<br>API声明：open(isSecureEnabled: boolean): Promise\<bigint>;<br>差异内容：open(isSecureEnabled: boolean): Promise\<bigint>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum FoldStatus<br>差异内容：enum FoldStatus|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FoldStatus；<br>API声明：NON_FOLDABLE = 0<br>差异内容：NON_FOLDABLE = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FoldStatus；<br>API声明：EXPANDED = 1<br>差异内容：EXPANDED = 1|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FoldStatus；<br>API声明：FOLDED = 2<br>差异内容：FOLDED = 2|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraErrorCode；<br>API声明：UNRESOLVED_CONFLICTS_WITH_CURRENT_CONFIGURATIONS = 7400110<br>差异内容：UNRESOLVED_CONFLICTS_WITH_CURRENT_CONFIGURATIONS = 7400110|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：on(type: 'foldStatusChange', callback: AsyncCallback\<FoldStatusInfo>): void;<br>差异内容：on(type: 'foldStatusChange', callback: AsyncCallback\<FoldStatusInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：off(type: 'foldStatusChange', callback?: AsyncCallback\<FoldStatusInfo>): void;<br>差异内容：off(type: 'foldStatusChange', callback?: AsyncCallback\<FoldStatusInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface FoldStatusInfo<br>差异内容：interface FoldStatusInfo|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FoldStatusInfo；<br>API声明：readonly supportedCameras: Array\<CameraDevice>;<br>差异内容：readonly supportedCameras: Array\<CameraDevice>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FoldStatusInfo；<br>API声明：readonly foldStatus: FoldStatus;<br>差异内容：readonly foldStatus: FoldStatus;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraDevice；<br>API声明：readonly cameraOrientation: number;<br>差异内容：readonly cameraOrientation: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：SceneMode；<br>API声明：SECURE_PHOTO = 12<br>差异内容：SECURE_PHOTO = 12|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface FlashQuery<br>差异内容：interface FlashQuery|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface AutoExposureQuery<br>差异内容：interface AutoExposureQuery|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：AutoExposureQuery；<br>API声明：getExposureBiasRange(): Array\<number>;<br>差异内容：getExposureBiasRange(): Array\<number>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface FocusQuery<br>差异内容：interface FocusQuery|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface ZoomQuery<br>差异内容：interface ZoomQuery|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface StabilizationQuery<br>差异内容：interface StabilizationQuery|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface ColorManagementQuery<br>差异内容：interface ColorManagementQuery|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：ColorManagementQuery；<br>API声明：getSupportedColorSpaces(): Array\<colorSpaceManager.ColorSpace>;<br>差异内容：getSupportedColorSpaces(): Array\<colorSpaceManager.ColorSpace>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface ColorManagement<br>差异内容：interface ColorManagement|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：ColorManagement；<br>API声明：getActiveColorSpace(): colorSpaceManager.ColorSpace;<br>差异内容：getActiveColorSpace(): colorSpaceManager.ColorSpace;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：ColorManagement；<br>API声明：setColorSpace(colorSpace: colorSpaceManager.ColorSpace): void;<br>差异内容：setColorSpace(colorSpace: colorSpaceManager.ColorSpace): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum PreconfigType<br>差异内容：enum PreconfigType|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreconfigType；<br>API声明：PRECONFIG_720P = 0<br>差异内容：PRECONFIG_720P = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreconfigType；<br>API声明：PRECONFIG_1080P = 1<br>差异内容：PRECONFIG_1080P = 1|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreconfigType；<br>API声明：PRECONFIG_4K = 2<br>差异内容：PRECONFIG_4K = 2|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreconfigType；<br>API声明：PRECONFIG_HIGH_QUALITY = 3<br>差异内容：PRECONFIG_HIGH_QUALITY = 3|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum PreconfigRatio<br>差异内容：enum PreconfigRatio|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreconfigRatio；<br>API声明：PRECONFIG_RATIO_1_1 = 0<br>差异内容：PRECONFIG_RATIO_1_1 = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreconfigRatio；<br>API声明：PRECONFIG_RATIO_4_3 = 1<br>差异内容：PRECONFIG_RATIO_4_3 = 1|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreconfigRatio；<br>API声明：PRECONFIG_RATIO_16_9 = 2<br>差异内容：PRECONFIG_RATIO_16_9 = 2|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoSession；<br>API声明：canPreconfig(preconfigType: PreconfigType, preconfigRatio?: PreconfigRatio): boolean;<br>差异内容：canPreconfig(preconfigType: PreconfigType, preconfigRatio?: PreconfigRatio): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoSession；<br>API声明：preconfig(preconfigType: PreconfigType, preconfigRatio?: PreconfigRatio): void;<br>差异内容：preconfig(preconfigType: PreconfigType, preconfigRatio?: PreconfigRatio): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoSession；<br>API声明：canPreconfig(preconfigType: PreconfigType, preconfigRatio?: PreconfigRatio): boolean;<br>差异内容：canPreconfig(preconfigType: PreconfigType, preconfigRatio?: PreconfigRatio): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoSession；<br>API声明：preconfig(preconfigType: PreconfigType, preconfigRatio?: PreconfigRatio): void;<br>差异内容：preconfig(preconfigType: PreconfigType, preconfigRatio?: PreconfigRatio): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface SecureSession<br>差异内容：interface SecureSession|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：SecureSession；<br>API声明：addSecureOutput(previewOutput: PreviewOutput): void;<br>差异内容：addSecureOutput(previewOutput: PreviewOutput): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：SecureSession；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：SecureSession；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：SecureSession；<br>API声明：on(type: 'focusStateChange', callback: AsyncCallback\<FocusState>): void;<br>差异内容：on(type: 'focusStateChange', callback: AsyncCallback\<FocusState>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：SecureSession；<br>API声明：off(type: 'focusStateChange', callback?: AsyncCallback\<FocusState>): void;<br>差异内容：off(type: 'focusStateChange', callback?: AsyncCallback\<FocusState>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreviewOutput；<br>API声明：getSupportedFrameRates(): Array\<FrameRateRange>;<br>差异内容：getSupportedFrameRates(): Array\<FrameRateRange>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreviewOutput；<br>API声明：setFrameRate(minFps: number, maxFps: number): void;<br>差异内容：setFrameRate(minFps: number, maxFps: number): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreviewOutput；<br>API声明：getActiveFrameRate(): FrameRateRange;<br>差异内容：getActiveFrameRate(): FrameRateRange;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreviewOutput；<br>API声明：getActiveProfile(): Profile;<br>差异内容：getActiveProfile(): Profile;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreviewOutput；<br>API声明：getPreviewRotation(displayRotation: number): ImageRotation;<br>差异内容：getPreviewRotation(displayRotation: number): ImageRotation;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PreviewOutput；<br>API声明：setPreviewRotation(previewRotation: ImageRotation, isDisplayLocked?: boolean): void;<br>差异内容：setPreviewRotation(previewRotation: ImageRotation, isDisplayLocked?: boolean): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：on(type: 'photoAssetAvailable', callback: AsyncCallback\<photoAccessHelper.PhotoAsset>): void;<br>差异内容：on(type: 'photoAssetAvailable', callback: AsyncCallback\<photoAccessHelper.PhotoAsset>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：off(type: 'photoAssetAvailable', callback?: AsyncCallback\<photoAccessHelper.PhotoAsset>): void;<br>差异内容：off(type: 'photoAssetAvailable', callback?: AsyncCallback\<photoAccessHelper.PhotoAsset>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：on(type: 'frameShutterEnd', callback: AsyncCallback\<FrameShutterEndInfo>): void;<br>差异内容：on(type: 'frameShutterEnd', callback: AsyncCallback\<FrameShutterEndInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：off(type: 'frameShutterEnd', callback?: AsyncCallback\<FrameShutterEndInfo>): void;<br>差异内容：off(type: 'frameShutterEnd', callback?: AsyncCallback\<FrameShutterEndInfo>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：on(type: 'captureReady', callback: AsyncCallback\<void>): void;<br>差异内容：on(type: 'captureReady', callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：off(type: 'captureReady', callback?: AsyncCallback\<void>): void;<br>差异内容：off(type: 'captureReady', callback?: AsyncCallback\<void>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：on(type: 'estimatedCaptureDuration', callback: AsyncCallback\<number>): void;<br>差异内容：on(type: 'estimatedCaptureDuration', callback: AsyncCallback\<number>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：off(type: 'estimatedCaptureDuration', callback?: AsyncCallback\<number>): void;<br>差异内容：off(type: 'estimatedCaptureDuration', callback?: AsyncCallback\<number>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：getActiveProfile(): Profile;<br>差异内容：getActiveProfile(): Profile;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：isMovingPhotoSupported(): boolean;<br>差异内容：isMovingPhotoSupported(): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：enableMovingPhoto(enabled: boolean): void;<br>差异内容：enableMovingPhoto(enabled: boolean): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：getPhotoRotation(deviceDegree: number): ImageRotation;<br>差异内容：getPhotoRotation(deviceDegree: number): ImageRotation;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface FrameShutterEndInfo<br>差异内容：interface FrameShutterEndInfo|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：FrameShutterEndInfo；<br>API声明：captureId: number;<br>差异内容：captureId: number;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoOutput；<br>API声明：getSupportedFrameRates(): Array\<FrameRateRange>;<br>差异内容：getSupportedFrameRates(): Array\<FrameRateRange>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoOutput；<br>API声明：setFrameRate(minFps: number, maxFps: number): void;<br>差异内容：setFrameRate(minFps: number, maxFps: number): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoOutput；<br>API声明：getActiveFrameRate(): FrameRateRange;<br>差异内容：getActiveFrameRate(): FrameRateRange;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoOutput；<br>API声明：getVideoRotation(deviceDegree: number): ImageRotation;<br>差异内容：getVideoRotation(deviceDegree: number): ImageRotation;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoOutput；<br>API声明：getActiveProfile(): VideoProfile;<br>差异内容：getActiveProfile(): VideoProfile;|api/@ohos.multimedia.camera.d.ts|
|成员由子类迁移至父类|类名：Flash；<br>API声明：hasFlash(): boolean;<br>差异内容：hasFlash(): boolean;|类名：FlashQuery；<br>API声明：hasFlash(): boolean;<br>差异内容：hasFlash(): boolean;|api/@ohos.multimedia.camera.d.ts|
|成员由子类迁移至父类|类名：Flash；<br>API声明：isFlashModeSupported(flashMode: FlashMode): boolean;<br>差异内容：isFlashModeSupported(flashMode: FlashMode): boolean;|类名：FlashQuery；<br>API声明：isFlashModeSupported(flashMode: FlashMode): boolean;<br>差异内容：isFlashModeSupported(flashMode: FlashMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|成员由子类迁移至父类|类名：AutoExposure；<br>API声明：isExposureModeSupported(aeMode: ExposureMode): boolean;<br>差异内容：isExposureModeSupported(aeMode: ExposureMode): boolean;|类名：AutoExposureQuery；<br>API声明：isExposureModeSupported(aeMode: ExposureMode): boolean;<br>差异内容：isExposureModeSupported(aeMode: ExposureMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|成员由子类迁移至父类|类名：Focus；<br>API声明：isFocusModeSupported(afMode: FocusMode): boolean;<br>差异内容：isFocusModeSupported(afMode: FocusMode): boolean;|类名：FocusQuery；<br>API声明：isFocusModeSupported(afMode: FocusMode): boolean;<br>差异内容：isFocusModeSupported(afMode: FocusMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|成员由子类迁移至父类|类名：Zoom；<br>API声明：getZoomRatioRange(): Array\<number>;<br>差异内容：getZoomRatioRange(): Array\<number>;|类名：ZoomQuery；<br>API声明：getZoomRatioRange(): Array\<number>;<br>差异内容：getZoomRatioRange(): Array\<number>;|api/@ohos.multimedia.camera.d.ts|
|成员由子类迁移至父类|类名：Stabilization；<br>API声明：isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean;<br>差异内容：isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean;|类名：StabilizationQuery；<br>API声明：isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean;<br>差异内容：isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean;|api/@ohos.multimedia.camera.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace camera<br>差异内容：NA|类名：global；<br>API声明：declare namespace camera<br>差异内容：atomicservice|api/@ohos.multimedia.camera.d.ts|
|API从不支持元服务到支持元服务|类名：camera；<br>API声明：enum CameraPosition<br>差异内容：NA|类名：camera；<br>API声明：enum CameraPosition<br>差异内容：atomicservice|api/@ohos.multimedia.camera.d.ts|
|API从不支持元服务到支持元服务|类名：CameraPosition；<br>API声明：CAMERA_POSITION_UNSPECIFIED = 0<br>差异内容：NA|类名：CameraPosition；<br>API声明：CAMERA_POSITION_UNSPECIFIED = 0<br>差异内容：atomicservice|api/@ohos.multimedia.camera.d.ts|
|API从不支持元服务到支持元服务|类名：CameraPosition；<br>API声明：CAMERA_POSITION_BACK = 1<br>差异内容：NA|类名：CameraPosition；<br>API声明：CAMERA_POSITION_BACK = 1<br>差异内容：atomicservice|api/@ohos.multimedia.camera.d.ts|
|API从不支持元服务到支持元服务|类名：CameraPosition；<br>API声明：CAMERA_POSITION_FRONT = 2<br>差异内容：NA|类名：CameraPosition；<br>API声明：CAMERA_POSITION_FRONT = 2<br>差异内容：atomicservice|api/@ohos.multimedia.camera.d.ts|
|API从不支持元服务到支持元服务|类名：CameraPosition；<br>API声明：CAMERA_POSITION_FOLD_INNER = 3<br>差异内容：NA|类名：CameraPosition；<br>API声明：CAMERA_POSITION_FOLD_INNER = 3<br>差异内容：atomicservice|api/@ohos.multimedia.camera.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace cameraPicker<br>差异内容：NA|类名：global；<br>API声明：declare namespace cameraPicker<br>差异内容：atomicservice|api/@ohos.multimedia.cameraPicker.d.ts|
|API从不支持元服务到支持元服务|类名：cameraPicker；<br>API声明：class PickerProfile<br>差异内容：NA|类名：cameraPicker；<br>API声明：class PickerProfile<br>差异内容：atomicservice|api/@ohos.multimedia.cameraPicker.d.ts|
|API从不支持元服务到支持元服务|类名：PickerProfile；<br>API声明：cameraPosition: camera.CameraPosition;<br>差异内容：NA|类名：PickerProfile；<br>API声明：cameraPosition: camera.CameraPosition;<br>差异内容：atomicservice|api/@ohos.multimedia.cameraPicker.d.ts|
|API从不支持元服务到支持元服务|类名：PickerProfile；<br>API声明：saveUri?: string;<br>差异内容：NA|类名：PickerProfile；<br>API声明：saveUri?: string;<br>差异内容：atomicservice|api/@ohos.multimedia.cameraPicker.d.ts|
|API从不支持元服务到支持元服务|类名：PickerProfile；<br>API声明：videoDuration?: number;<br>差异内容：NA|类名：PickerProfile；<br>API声明：videoDuration?: number;<br>差异内容：atomicservice|api/@ohos.multimedia.cameraPicker.d.ts|
|API从不支持元服务到支持元服务|类名：cameraPicker；<br>API声明：enum PickerMediaType<br>差异内容：NA|类名：cameraPicker；<br>API声明：enum PickerMediaType<br>差异内容：atomicservice|api/@ohos.multimedia.cameraPicker.d.ts|
|API从不支持元服务到支持元服务|类名：PickerMediaType；<br>API声明：PHOTO = 'photo'<br>差异内容：NA|类名：PickerMediaType；<br>API声明：PHOTO = 'photo'<br>差异内容：atomicservice|api/@ohos.multimedia.cameraPicker.d.ts|
|API从不支持元服务到支持元服务|类名：PickerMediaType；<br>API声明：VIDEO = 'video'<br>差异内容：NA|类名：PickerMediaType；<br>API声明：VIDEO = 'video'<br>差异内容：atomicservice|api/@ohos.multimedia.cameraPicker.d.ts|
|API从不支持元服务到支持元服务|类名：cameraPicker；<br>API声明：class PickerResult<br>差异内容：NA|类名：cameraPicker；<br>API声明：class PickerResult<br>差异内容：atomicservice|api/@ohos.multimedia.cameraPicker.d.ts|
|API从不支持元服务到支持元服务|类名：PickerResult；<br>API声明：resultCode: number;<br>差异内容：NA|类名：PickerResult；<br>API声明：resultCode: number;<br>差异内容：atomicservice|api/@ohos.multimedia.cameraPicker.d.ts|
|API从不支持元服务到支持元服务|类名：PickerResult；<br>API声明：resultUri: string;<br>差异内容：NA|类名：PickerResult；<br>API声明：resultUri: string;<br>差异内容：atomicservice|api/@ohos.multimedia.cameraPicker.d.ts|
|API从不支持元服务到支持元服务|类名：PickerResult；<br>API声明：mediaType: PickerMediaType;<br>差异内容：NA|类名：PickerResult；<br>API声明：mediaType: PickerMediaType;<br>差异内容：atomicservice|api/@ohos.multimedia.cameraPicker.d.ts|
|API从不支持元服务到支持元服务|类名：cameraPicker；<br>API声明：function pick(context: Context, mediaTypes: Array\<PickerMediaType>, pickerProfile: PickerProfile): Promise\<PickerResult>;<br>差异内容：NA|类名：cameraPicker；<br>API声明：function pick(context: Context, mediaTypes: Array\<PickerMediaType>, pickerProfile: PickerProfile): Promise\<PickerResult>;<br>差异内容：atomicservice|api/@ohos.multimedia.cameraPicker.d.ts|
