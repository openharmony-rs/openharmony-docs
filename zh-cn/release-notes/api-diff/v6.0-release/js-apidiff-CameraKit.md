| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|删除错误码|类名：CameraManager；<br>API声明：setTorchMode(mode: TorchMode): void;<br>差异内容：7400101|类名：CameraManager；<br>API声明：setTorchMode(mode: TorchMode): void;<br>差异内容：NA|api/@ohos.multimedia.camera.d.ts|
|删除错误码|类名：Zoom；<br>API声明：setSmoothZoom(targetRatio: number, mode?: SmoothZoomMode): void;<br>差异内容：7400103|类名：Zoom；<br>API声明：setSmoothZoom(targetRatio: number, mode?: SmoothZoomMode): void;<br>差异内容：NA|api/@ohos.multimedia.camera.d.ts|
|删除错误码|类名：ColorManagementQuery；<br>API声明：getSupportedColorSpaces(): Array\<colorSpaceManager.ColorSpace>;<br>差异内容：7400103|类名：ColorManagementQuery；<br>API声明：getSupportedColorSpaces(): Array\<colorSpaceManager.ColorSpace>;<br>差异内容：NA|api/@ohos.multimedia.camera.d.ts|
|删除错误码|类名：AutoDeviceSwitchQuery；<br>API声明：isAutoDeviceSwitchSupported(): boolean;<br>差异内容：7400103|类名：AutoDeviceSwitchQuery；<br>API声明：isAutoDeviceSwitchSupported(): boolean;<br>差异内容：NA|api/@ohos.multimedia.camera.d.ts|
|删除错误码|类名：Session；<br>API声明：addInput(cameraInput: CameraInput): void;<br>差异内容：7400103|类名：Session；<br>API声明：addInput(cameraInput: CameraInput): void;<br>差异内容：NA|api/@ohos.multimedia.camera.d.ts|
|删除错误码|类名：Session；<br>API声明：removeInput(cameraInput: CameraInput): void;<br>差异内容：7400103|类名：Session；<br>API声明：removeInput(cameraInput: CameraInput): void;<br>差异内容：NA|api/@ohos.multimedia.camera.d.ts|
|删除错误码|类名：Session；<br>API声明：addOutput(cameraOutput: CameraOutput): void;<br>差异内容：7400103|类名：Session；<br>API声明：addOutput(cameraOutput: CameraOutput): void;<br>差异内容：NA|api/@ohos.multimedia.camera.d.ts|
|删除错误码|类名：Session；<br>API声明：removeOutput(cameraOutput: CameraOutput): void;<br>差异内容：7400103|类名：Session；<br>API声明：removeOutput(cameraOutput: CameraOutput): void;<br>差异内容：NA|api/@ohos.multimedia.camera.d.ts|
|删除错误码|类名：SecureSession；<br>API声明：addSecureOutput(previewOutput: PreviewOutput): void;<br>差异内容：7400103|类名：SecureSession；<br>API声明：addSecureOutput(previewOutput: PreviewOutput): void;<br>差异内容：NA|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraInput；<br>API声明：open(type: CameraConcurrentType): Promise\<void>;<br>差异内容：open(type: CameraConcurrentType): Promise\<void>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：getCameraDevice(position: CameraPosition, type: CameraType): CameraDevice;<br>差异内容：getCameraDevice(position: CameraPosition, type: CameraType): CameraDevice;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraManager；<br>API声明：getCameraConcurrentInfos(cameras: Array\<CameraDevice>): Array\<CameraConcurrentInfo>;<br>差异内容：getCameraConcurrentInfos(cameras: Array\<CameraDevice>): Array\<CameraConcurrentInfo>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum CameraConcurrentType<br>差异内容：enum CameraConcurrentType|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraConcurrentType；<br>API声明：CAMERA_LIMITED_CAPABILITY = 0<br>差异内容：CAMERA_LIMITED_CAPABILITY = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraConcurrentType；<br>API声明：CAMERA_FULL_CAPABILITY = 1<br>差异内容：CAMERA_FULL_CAPABILITY = 1|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface CameraConcurrentInfo<br>差异内容：interface CameraConcurrentInfo|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraConcurrentInfo；<br>API声明：readonly device: CameraDevice;<br>差异内容：readonly device: CameraDevice;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraConcurrentInfo；<br>API声明：readonly type: CameraConcurrentType;<br>差异内容：readonly type: CameraConcurrentType;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraConcurrentInfo；<br>API声明：readonly modes: Array\<SceneMode>;<br>差异内容：readonly modes: Array\<SceneMode>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraConcurrentInfo；<br>API声明：readonly outputCapabilities: Array\<CameraOutputCapability>;<br>差异内容：readonly outputCapabilities: Array\<CameraOutputCapability>;|api/@ohos.multimedia.camera.d.ts|
|起始版本有变化|类名：camera；<br>API声明：enum HostDeviceType<br>差异内容：10|类名：camera；<br>API声明：enum HostDeviceType<br>差异内容：15|api/@ohos.multimedia.camera.d.ts|
|起始版本有变化|类名：HostDeviceType；<br>API声明：UNKNOWN_TYPE = 0<br>差异内容：10|类名：HostDeviceType；<br>API声明：UNKNOWN_TYPE = 0<br>差异内容：15|api/@ohos.multimedia.camera.d.ts|
|起始版本有变化|类名：HostDeviceType；<br>API声明：PHONE = 0x0E<br>差异内容：10|类名：HostDeviceType；<br>API声明：PHONE = 0x0E<br>差异内容：15|api/@ohos.multimedia.camera.d.ts|
|起始版本有变化|类名：HostDeviceType；<br>API声明：TABLET = 0x11<br>差异内容：10|类名：HostDeviceType；<br>API声明：TABLET = 0x11<br>差异内容：15|api/@ohos.multimedia.camera.d.ts|
|起始版本有变化|类名：CameraDevice；<br>API声明：readonly hostDeviceName: string;<br>差异内容：10|类名：CameraDevice；<br>API声明：readonly hostDeviceName: string;<br>差异内容：15|api/@ohos.multimedia.camera.d.ts|
|起始版本有变化|类名：CameraDevice；<br>API声明：readonly hostDeviceType: HostDeviceType;<br>差异内容：10|类名：CameraDevice；<br>API声明：readonly hostDeviceType: HostDeviceType;<br>差异内容：15|api/@ohos.multimedia.camera.d.ts|
|起始版本有变化|类名：VideoOutput；<br>API声明：isMirrorSupported(): boolean;<br>差异内容：12|类名：VideoOutput；<br>API声明：isMirrorSupported(): boolean;<br>差异内容：15|api/@ohos.multimedia.camera.d.ts|
|起始版本有变化|类名：VideoOutput；<br>API声明：enableMirror(enabled: boolean): void;<br>差异内容：12|类名：VideoOutput；<br>API声明：enableMirror(enabled: boolean): void;<br>差异内容：15|api/@ohos.multimedia.camera.d.ts|
