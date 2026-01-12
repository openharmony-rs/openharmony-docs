| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New error code|Class name: CameraManager;<br>API declaration: createSession\<T extends Session>(mode: SceneMode): T;<br>Differences: NA|Class name: CameraManager;<br>API declaration: createSession\<T extends Session>(mode: SceneMode): T;<br>Differences: 401|api/@ohos.multimedia.camera.d.ts|
|New error code|Class name: CameraInput;<br>API declaration: open(): Promise\<void>;<br>Differences: NA|Class name: CameraInput;<br>API declaration: open(): Promise\<void>;<br>Differences: 7400102|api/@ohos.multimedia.camera.d.ts|
|New API |NA|Class name: CameraFormat;<br>API declaration: CAMERA_FORMAT_HEIC = 2003<br>Differences: CAMERA_FORMAT_HEIC = 2003|api/@ohos.multimedia.camera.d.ts|
|New API |NA|Class name: camera;<br>API declaration: interface AutoDeviceSwitchQuery<br>Differences: interface AutoDeviceSwitchQuery|api/@ohos.multimedia.camera.d.ts|
|New API |NA|Class name: AutoDeviceSwitchQuery;<br>API declaration: isAutoDeviceSwitchSupported(): boolean;<br>Differences: isAutoDeviceSwitchSupported(): boolean;|api/@ohos.multimedia.camera.d.ts|
|New API |NA|Class name: camera;<br>API declaration: interface AutoDeviceSwitch<br>Differences: interface AutoDeviceSwitch|api/@ohos.multimedia.camera.d.ts|
|New API |NA|Class name: AutoDeviceSwitch;<br>API declaration: enableAutoDeviceSwitch(enabled: boolean): void;<br>Differences: enableAutoDeviceSwitch(enabled: boolean): void;|api/@ohos.multimedia.camera.d.ts|
|New API |NA|Class name: camera;<br>API declaration: interface AutoDeviceSwitchStatus<br>Differences: interface AutoDeviceSwitchStatus|api/@ohos.multimedia.camera.d.ts|
|New API |NA|Class name: AutoDeviceSwitchStatus;<br>API declaration: readonly isDeviceSwitched: boolean;<br>Differences: readonly isDeviceSwitched: boolean;|api/@ohos.multimedia.camera.d.ts|
|New API |NA|Class name: AutoDeviceSwitchStatus;<br>API declaration: readonly isDeviceCapabilityChanged: boolean;<br>Differences: readonly isDeviceCapabilityChanged: boolean;|api/@ohos.multimedia.camera.d.ts|
|New API |NA|Class name: PhotoSession;<br>API declaration: on(type: 'autoDeviceSwitchStatusChange', callback: AsyncCallback\<AutoDeviceSwitchStatus>): void;<br>Differences: on(type: 'autoDeviceSwitchStatusChange', callback: AsyncCallback\<AutoDeviceSwitchStatus>): void;|api/@ohos.multimedia.camera.d.ts|
|New API |NA|Class name: PhotoSession;<br>API declaration: off(type: 'autoDeviceSwitchStatusChange', callback?: AsyncCallback\<AutoDeviceSwitchStatus>): void;<br>Differences: off(type: 'autoDeviceSwitchStatusChange', callback?: AsyncCallback\<AutoDeviceSwitchStatus>): void;|api/@ohos.multimedia.camera.d.ts|
|New API |NA|Class name: VideoSession;<br>API declaration: on(type: 'autoDeviceSwitchStatusChange', callback: AsyncCallback\<AutoDeviceSwitchStatus>): void;<br>Differences: on(type: 'autoDeviceSwitchStatusChange', callback: AsyncCallback\<AutoDeviceSwitchStatus>): void;|api/@ohos.multimedia.camera.d.ts|
|New API |NA|Class name: VideoSession;<br>API declaration: off(type: 'autoDeviceSwitchStatusChange', callback?: AsyncCallback\<AutoDeviceSwitchStatus>): void;<br>Differences: off(type: 'autoDeviceSwitchStatusChange', callback?: AsyncCallback\<AutoDeviceSwitchStatus>): void;|api/@ohos.multimedia.camera.d.ts|
|New API |NA|Class name: camera;<br>API declaration: enum VideoCodecType<br>Differences: enum VideoCodecType|api/@ohos.multimedia.camera.d.ts|
|New API |NA|Class name: VideoCodecType;<br>API declaration: AVC = 0<br>Differences: AVC = 0|api/@ohos.multimedia.camera.d.ts|
|New API |NA|Class name: VideoCodecType;<br>API declaration: HEVC = 1<br>Differences: HEVC = 1|api/@ohos.multimedia.camera.d.ts|
|New API |NA|Class name: PhotoOutput;<br>API declaration: getSupportedMovingPhotoVideoCodecTypes(): Array\<VideoCodecType>;<br>Differences: getSupportedMovingPhotoVideoCodecTypes(): Array\<VideoCodecType>;|api/@ohos.multimedia.camera.d.ts|
|New API |NA|Class name: PhotoOutput;<br>API declaration: setMovingPhotoVideoCodecType(codecType: VideoCodecType): void;<br>Differences: setMovingPhotoVideoCodecType(codecType: VideoCodecType): void;|api/@ohos.multimedia.camera.d.ts|
|New API |NA|Class name: PhotoOutput;<br>API declaration: enableMirror(enabled: boolean): void;<br>Differences: enableMirror(enabled: boolean): void;|api/@ohos.multimedia.camera.d.ts|
