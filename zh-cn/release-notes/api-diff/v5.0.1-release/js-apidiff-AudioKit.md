| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：audio；<br>API声明：enum DeviceBlockStatus<br>差异内容：enum DeviceBlockStatus|api/@ohos.multimedia.audio.d.ts|
|新增API|NA|类名：DeviceBlockStatus；<br>API声明：UNBLOCKED = 0<br>差异内容：UNBLOCKED = 0|api/@ohos.multimedia.audio.d.ts|
|新增API|NA|类名：DeviceBlockStatus；<br>API声明：BLOCKED = 1<br>差异内容：BLOCKED = 1|api/@ohos.multimedia.audio.d.ts|
|新增API|NA|类名：audio；<br>API声明：interface DeviceBlockStatusInfo<br>差异内容：interface DeviceBlockStatusInfo|api/@ohos.multimedia.audio.d.ts|
|新增API|NA|类名：DeviceBlockStatusInfo；<br>API声明：blockStatus: DeviceBlockStatus;<br>差异内容：blockStatus: DeviceBlockStatus;|api/@ohos.multimedia.audio.d.ts|
|新增API|NA|类名：DeviceBlockStatusInfo；<br>API声明：devices: AudioDeviceDescriptors;<br>差异内容：devices: AudioDeviceDescriptors;|api/@ohos.multimedia.audio.d.ts|
|新增API|NA|类名：AudioRoutingManager；<br>API声明：isMicBlockDetectionSupported(): Promise\<boolean>;<br>差异内容：isMicBlockDetectionSupported(): Promise\<boolean>;|api/@ohos.multimedia.audio.d.ts|
|新增API|NA|类名：AudioRoutingManager；<br>API声明：on(type: 'micBlockStatusChanged', callback: Callback\<DeviceBlockStatusInfo>): void;<br>差异内容：on(type: 'micBlockStatusChanged', callback: Callback\<DeviceBlockStatusInfo>): void;|api/@ohos.multimedia.audio.d.ts|
|新增API|NA|类名：AudioRoutingManager；<br>API声明：off(type: 'micBlockStatusChanged', callback?: Callback\<DeviceBlockStatusInfo>): void;<br>差异内容：off(type: 'micBlockStatusChanged', callback?: Callback\<DeviceBlockStatusInfo>): void;|api/@ohos.multimedia.audio.d.ts|
|新增API|NA|类名：SourceType；<br>API声明：SOURCE_TYPE_CAMCORDER = 13<br>差异内容：SOURCE_TYPE_CAMCORDER = 13|api/@ohos.multimedia.audio.d.ts|
