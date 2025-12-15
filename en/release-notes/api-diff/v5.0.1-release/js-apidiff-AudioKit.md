| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: audio;<br>API declaration: enum DeviceBlockStatus<br>Differences: enum DeviceBlockStatus|api/@ohos.multimedia.audio.d.ts|
|New API |NA|Class name: DeviceBlockStatus;<br>API declaration: UNBLOCKED = 0<br>Differences: UNBLOCKED = 0|api/@ohos.multimedia.audio.d.ts|
|New API |NA|Class name: DeviceBlockStatus;<br>API declaration: BLOCKED = 1<br>Differences: BLOCKED = 1|api/@ohos.multimedia.audio.d.ts|
|New API |NA|Class name: audio;<br>API declaration: interface DeviceBlockStatusInfo<br>Differences: interface DeviceBlockStatusInfo|api/@ohos.multimedia.audio.d.ts|
|New API |NA|Class name: DeviceBlockStatusInfo;<br>API declaration: blockStatus: DeviceBlockStatus;<br>Differences: blockStatus: DeviceBlockStatus;|api/@ohos.multimedia.audio.d.ts|
|New API |NA|Class name: DeviceBlockStatusInfo;<br>API declaration: devices: AudioDeviceDescriptors;<br>Differences: devices: AudioDeviceDescriptors;|api/@ohos.multimedia.audio.d.ts|
|New API |NA|Class name: AudioRoutingManager;<br>API declaration: isMicBlockDetectionSupported(): Promise\<boolean>;<br>Differences: isMicBlockDetectionSupported(): Promise\<boolean>;|api/@ohos.multimedia.audio.d.ts|
|New API |NA|Class name: AudioRoutingManager;<br>API declaration: on(type: 'micBlockStatusChanged', callback: Callback\<DeviceBlockStatusInfo>): void;<br>Differences: on(type: 'micBlockStatusChanged', callback: Callback\<DeviceBlockStatusInfo>): void;|api/@ohos.multimedia.audio.d.ts|
|New API |NA|Class name: AudioRoutingManager;<br>API declaration: off(type: 'micBlockStatusChanged', callback?: Callback\<DeviceBlockStatusInfo>): void;<br>Differences: off(type: 'micBlockStatusChanged', callback?: Callback\<DeviceBlockStatusInfo>): void;|api/@ohos.multimedia.audio.d.ts|
|New API |NA|Class name: SourceType;<br>API declaration: SOURCE_TYPE_CAMCORDER = 13<br>Differences: SOURCE_TYPE_CAMCORDER = 13|api/@ohos.multimedia.audio.d.ts|
