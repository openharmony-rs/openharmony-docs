| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增错误码|类名：CameraManager；<br>API声明：createSession\<T extends Session>(mode: SceneMode): T;<br>差异内容：NA|类名：CameraManager；<br>API声明：createSession\<T extends Session>(mode: SceneMode): T;<br>差异内容：401|api/@ohos.multimedia.camera.d.ts|
|新增错误码|类名：CameraInput；<br>API声明：open(): Promise\<void>;<br>差异内容：NA|类名：CameraInput；<br>API声明：open(): Promise\<void>;<br>差异内容：7400102|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：CameraFormat；<br>API声明：CAMERA_FORMAT_HEIC = 2003<br>差异内容：CAMERA_FORMAT_HEIC = 2003|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface AutoDeviceSwitchQuery<br>差异内容：interface AutoDeviceSwitchQuery|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：AutoDeviceSwitchQuery；<br>API声明：isAutoDeviceSwitchSupported(): boolean;<br>差异内容：isAutoDeviceSwitchSupported(): boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface AutoDeviceSwitch<br>差异内容：interface AutoDeviceSwitch|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：AutoDeviceSwitch；<br>API声明：enableAutoDeviceSwitch(enabled: boolean): void;<br>差异内容：enableAutoDeviceSwitch(enabled: boolean): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：interface AutoDeviceSwitchStatus<br>差异内容：interface AutoDeviceSwitchStatus|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：AutoDeviceSwitchStatus；<br>API声明：readonly isDeviceSwitched: boolean;<br>差异内容：readonly isDeviceSwitched: boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：AutoDeviceSwitchStatus；<br>API声明：readonly isDeviceCapabilityChanged: boolean;<br>差异内容：readonly isDeviceCapabilityChanged: boolean;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoSession；<br>API声明：on(type: 'autoDeviceSwitchStatusChange', callback: AsyncCallback\<AutoDeviceSwitchStatus>): void;<br>差异内容：on(type: 'autoDeviceSwitchStatusChange', callback: AsyncCallback\<AutoDeviceSwitchStatus>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoSession；<br>API声明：off(type: 'autoDeviceSwitchStatusChange', callback?: AsyncCallback\<AutoDeviceSwitchStatus>): void;<br>差异内容：off(type: 'autoDeviceSwitchStatusChange', callback?: AsyncCallback\<AutoDeviceSwitchStatus>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoSession；<br>API声明：on(type: 'autoDeviceSwitchStatusChange', callback: AsyncCallback\<AutoDeviceSwitchStatus>): void;<br>差异内容：on(type: 'autoDeviceSwitchStatusChange', callback: AsyncCallback\<AutoDeviceSwitchStatus>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoSession；<br>API声明：off(type: 'autoDeviceSwitchStatusChange', callback?: AsyncCallback\<AutoDeviceSwitchStatus>): void;<br>差异内容：off(type: 'autoDeviceSwitchStatusChange', callback?: AsyncCallback\<AutoDeviceSwitchStatus>): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：camera；<br>API声明：enum VideoCodecType<br>差异内容：enum VideoCodecType|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoCodecType；<br>API声明：AVC = 0<br>差异内容：AVC = 0|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：VideoCodecType；<br>API声明：HEVC = 1<br>差异内容：HEVC = 1|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：getSupportedMovingPhotoVideoCodecTypes(): Array\<VideoCodecType>;<br>差异内容：getSupportedMovingPhotoVideoCodecTypes(): Array\<VideoCodecType>;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：setMovingPhotoVideoCodecType(codecType: VideoCodecType): void;<br>差异内容：setMovingPhotoVideoCodecType(codecType: VideoCodecType): void;|api/@ohos.multimedia.camera.d.ts|
|新增API|NA|类名：PhotoOutput；<br>API声明：enableMirror(enabled: boolean): void;<br>差异内容：enableMirror(enabled: boolean): void;|api/@ohos.multimedia.camera.d.ts|
