| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：PhotoPickerComponent；<br>API声明：onVideoPlayStateChanged?: videoPlayStateChangedCallback;<br>差异内容：onVideoPlayStateChanged?: videoPlayStateChangedCallback;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export type videoPlayStateChangedCallback = (state: VideoPlayerState) => void;<br>差异内容：export type videoPlayStateChangedCallback = (state: VideoPlayerState) => void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerOptions；<br>API声明：gridMargin?: Margin;<br>差异内容：gridMargin?: Margin;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerOptions；<br>API声明：photoBrowserMargin?: Margin;<br>差异内容：photoBrowserMargin?: Margin;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum VideoPlayerState<br>差异内容：export declare enum VideoPlayerState|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：VideoPlayerState；<br>API声明：PLAYING = 0<br>差异内容：PLAYING = 0|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：VideoPlayerState；<br>API声明：PAUSED = 1<br>差异内容：PAUSED = 1|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：VideoPlayerState；<br>API声明：STOPPED = 2<br>差异内容：STOPPED = 2|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：VideoPlayerState；<br>API声明：SEEK_START = 3<br>差异内容：SEEK_START = 3|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：VideoPlayerState；<br>API声明：SEEK_FINISH = 4<br>差异内容：SEEK_FINISH = 4|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：photoAccessHelper；<br>API声明：enum CompleteButtonText<br>差异内容：enum CompleteButtonText|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：CompleteButtonText；<br>API声明：TEXT_DONE = 0<br>差异内容：TEXT_DONE = 0|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：CompleteButtonText；<br>API声明：TEXT_SEND = 1<br>差异内容：TEXT_SEND = 1|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：CompleteButtonText；<br>API声明：TEXT_ADD = 2<br>差异内容：TEXT_ADD = 2|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAsset；<br>API声明：clone(title: string): Promise\<PhotoAsset>;<br>差异内容：clone(title: string): Promise\<PhotoAsset>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：requestPhotoUrisReadPermission(srcFileUris: Array\<string>): Promise\<Array\<string>>;<br>差异内容：requestPhotoUrisReadPermission(srcFileUris: Array\<string>): Promise\<Array\<string>>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoSelectOptions；<br>API声明：completeButtonText?: CompleteButtonText;<br>差异内容：completeButtonText?: CompleteButtonText;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：sendablePhotoAccessHelper；<br>API声明：enum PhotoSubtype<br>差异内容：enum PhotoSubtype|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoSubtype；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoSubtype；<br>API声明：MOVING_PHOTO = 3<br>差异内容：MOVING_PHOTO = 3|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoSubtype；<br>API声明：BURST = 4<br>差异内容：BURST = 4|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：sendablePhotoAccessHelper；<br>API声明：enum DynamicRangeType<br>差异内容：enum DynamicRangeType|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：DynamicRangeType；<br>API声明：SDR = 0<br>差异内容：SDR = 0|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：DynamicRangeType；<br>API声明：HDR = 1<br>差异内容：HDR = 1|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|API从不支持元服务到支持元服务|类名：photoAccessHelper；<br>API声明：class MediaAssetManager<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：class MediaAssetManager<br>差异内容：atomicservice|api/@ohos.file.photoAccessHelper.d.ts|
|API从不支持元服务到支持元服务|类名：MediaAssetManager；<br>API声明：static loadMovingPhoto(context: Context, imageFileUri: string, videoFileUri: string): Promise\<MovingPhoto>;<br>差异内容：NA|类名：MediaAssetManager；<br>API声明：static loadMovingPhoto(context: Context, imageFileUri: string, videoFileUri: string): Promise\<MovingPhoto>;<br>差异内容：atomicservice|api/@ohos.file.photoAccessHelper.d.ts|
|新增导出符号|类名：global；<br>API声明：export type videoPlayStateChangedCallback = (state: VideoPlayerState) => void;<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export type videoPlayStateChangedCallback = (state: VideoPlayerState) => void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增导出符号|类名：global；<br>API声明：export declare enum VideoPlayerState<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export declare enum VideoPlayerState|api/@ohos.file.PhotoPickerComponent.d.ets|
