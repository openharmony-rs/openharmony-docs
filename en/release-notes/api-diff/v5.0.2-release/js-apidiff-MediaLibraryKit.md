| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: PhotoPickerComponent;<br>API declaration: onVideoPlayStateChanged?: videoPlayStateChangedCallback;<br>DIfferences: onVideoPlayStateChanged?: videoPlayStateChangedCallback;|api/@ohos.file.PhotoPickerComponent.d.ets|
|New API |NA|Class name: global;<br>API declaration: export type videoPlayStateChangedCallback = (state: VideoPlayerState) => void;<br>DIfferences: export type videoPlayStateChangedCallback = (state: VideoPlayerState) => void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|New API |NA|Class name: PickerOptions;<br>API declaration: gridMargin?: Margin;<br>DIfferences: gridMargin?: Margin;|api/@ohos.file.PhotoPickerComponent.d.ets|
|New API |NA|Class name: PickerOptions;<br>API declaration: photoBrowserMargin?: Margin;<br>DIfferences: photoBrowserMargin?: Margin;|api/@ohos.file.PhotoPickerComponent.d.ets|
|New API |NA|Class name: global;<br>API declaration: export declare enum VideoPlayerState<br>DIfferences: export declare enum VideoPlayerState|api/@ohos.file.PhotoPickerComponent.d.ets|
|New API |NA|Class name: VideoPlayerState;<br>API declaration: PLAYING = 0<br>DIfferences: PLAYING = 0|api/@ohos.file.PhotoPickerComponent.d.ets|
|New API |NA|Class name: VideoPlayerState;<br>API declaration: PAUSED = 1<br>DIfferences: PAUSED = 1|api/@ohos.file.PhotoPickerComponent.d.ets|
|New API |NA|Class name: VideoPlayerState;<br>API declaration: STOPPED = 2<br>DIfferences: STOPPED = 2|api/@ohos.file.PhotoPickerComponent.d.ets|
|New API |NA|Class name: VideoPlayerState;<br>API declaration: SEEK_START = 3<br>DIfferences: SEEK_START = 3|api/@ohos.file.PhotoPickerComponent.d.ets|
|New API |NA|Class name: VideoPlayerState;<br>API declaration: SEEK_FINISH = 4<br>DIfferences: SEEK_FINISH = 4|api/@ohos.file.PhotoPickerComponent.d.ets|
|New API |NA|Class name: photoAccessHelper;<br>API declaration: enum CompleteButtonText<br>DIfferences: enum CompleteButtonText|api/@ohos.file.photoAccessHelper.d.ts|
|New API |NA|Class name: CompleteButtonText;<br>API declaration: TEXT_DONE = 0<br>DIfferences: TEXT_DONE = 0|api/@ohos.file.photoAccessHelper.d.ts|
|New API |NA|Class name: CompleteButtonText;<br>API declaration: TEXT_SEND = 1<br>DIfferences: TEXT_SEND = 1|api/@ohos.file.photoAccessHelper.d.ts|
|New API |NA|Class name: CompleteButtonText;<br>API declaration: TEXT_ADD = 2<br>DIfferences: TEXT_ADD = 2|api/@ohos.file.photoAccessHelper.d.ts|
|New API |NA|Class name: PhotoAsset;<br>API declaration: clone(title: string): Promise\<PhotoAsset>;<br>DIfferences: clone(title: string): Promise\<PhotoAsset>;|api/@ohos.file.photoAccessHelper.d.ts|
|New API |NA|Class name: PhotoAccessHelper;<br>API declaration: requestPhotoUrisReadPermission(srcFileUris: Array\<string>): Promise\<Array\<string>>;<br>DIfferences: requestPhotoUrisReadPermission(srcFileUris: Array\<string>): Promise\<Array\<string>>;|api/@ohos.file.photoAccessHelper.d.ts|
|New API |NA|Class name: PhotoSelectOptions;<br>API declaration: completeButtonText?: CompleteButtonText;<br>DIfferences: completeButtonText?: CompleteButtonText;|api/@ohos.file.photoAccessHelper.d.ts|
|New API |NA|Class name: sendablePhotoAccessHelper;<br>API declaration: enum PhotoSubtype<br>DIfferences: enum PhotoSubtype|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|New API |NA|Class name: PhotoSubtype;<br>API declaration: DEFAULT = 0<br>DIfferences: DEFAULT = 0|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|New API |NA|Class name: PhotoSubtype;<br>API declaration: MOVING_PHOTO = 3<br>DIfferences: MOVING_PHOTO = 3|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|New API |NA|Class name: PhotoSubtype;<br>API declaration: BURST = 4<br>DIfferences: BURST = 4|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|New API |NA|Class name: sendablePhotoAccessHelper;<br>API declaration: enum DynamicRangeType<br>DIfferences: enum DynamicRangeType|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|New API |NA|Class name: DynamicRangeType;<br>API declaration: SDR = 0<br>DIfferences: SDR = 0|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|New API |NA|Class name: DynamicRangeType;<br>API declaration: HDR = 1<br>DIfferences: HDR = 1|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|New support for atomic services|Class name: photoAccessHelper;<br>API declaration: class MediaAssetManager<br>DIfferences: NA|Class name: photoAccessHelper;<br>API declaration: class MediaAssetManager<br>DIfferences: atomicservice|api/@ohos.file.photoAccessHelper.d.ts|
|New support for atomic services|Class name: MediaAssetManager;<br>API declaration: static loadMovingPhoto(context: Context, imageFileUri: string, videoFileUri: string): Promise\<MovingPhoto>;<br>DIfferences: NA|Class name: MediaAssetManager;<br>API declaration: static loadMovingPhoto(context: Context, imageFileUri: string, videoFileUri: string): Promise\<MovingPhoto>;<br>DIfferences: atomicservice|api/@ohos.file.photoAccessHelper.d.ts|
|New export symbol|Class name: global;<br>API declaration: export type videoPlayStateChangedCallback = (state: VideoPlayerState) => void;<br>DIfferences: NA|Class name: global;<br>API declaration: <br>DIfferences: export type videoPlayStateChangedCallback = (state: VideoPlayerState) => void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|New export symbol|Class name: global;<br>API declaration: export declare enum VideoPlayerState<br>DIfferences: NA|Class name: global;<br>API declaration: <br>DIfferences: export declare enum VideoPlayerState|api/@ohos.file.PhotoPickerComponent.d.ets|
