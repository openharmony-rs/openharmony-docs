| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：AlbumPickerComponent；<br>API声明：onEmptyAreaClick?: EmptyAreaClickCallback;<br>差异内容：onEmptyAreaClick?: EmptyAreaClickCallback;|api/@ohos.file.AlbumPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export type EmptyAreaClickCallback = () => void;<br>差异内容：export type EmptyAreaClickCallback = () => void;|api/@ohos.file.AlbumPickerComponent.d.ets|
|新增API|NA|类名：AlbumPickerOptions；<br>API声明：filterType?: photoAccessHelper.PhotoViewMIMETypes;<br>差异内容：filterType?: photoAccessHelper.PhotoViewMIMETypes;|api/@ohos.file.AlbumPickerComponent.d.ets|
|新增API|NA|类名：PhotoPickerComponent；<br>API声明：onSelectedItemsDeleted?: ItemsDeletedCallback;<br>差异内容：onSelectedItemsDeleted?: ItemsDeletedCallback;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PhotoPickerComponent；<br>API声明：onExceedMaxSelected?: ExceedMaxSelectedCallback;<br>差异内容：onExceedMaxSelected?: ExceedMaxSelectedCallback;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PhotoPickerComponent；<br>API声明：onCurrentAlbumDeleted?: CurrentAlbumDeletedCallback;<br>差异内容：onCurrentAlbumDeleted?: CurrentAlbumDeletedCallback;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export type ItemsDeletedCallback = (baseItemInfos: Array\<BaseItemInfo>) => void;<br>差异内容：export type ItemsDeletedCallback = (baseItemInfos: Array\<BaseItemInfo>) => void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export type ExceedMaxSelectedCallback = (exceedMaxCountType: MaxCountType) => void;<br>差异内容：export type ExceedMaxSelectedCallback = (exceedMaxCountType: MaxCountType) => void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export type CurrentAlbumDeletedCallback = () => void;<br>差异内容：export type CurrentAlbumDeletedCallback = () => void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerController；<br>API声明：exitPhotoBrowser(): void;<br>差异内容：exitPhotoBrowser(): void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerController；<br>API声明：setPhotoBrowserUIElementVisibility(elements: Array\<PhotoBrowserUIElement>, isVisible: boolean): void;<br>差异内容：setPhotoBrowserUIElementVisibility(elements: Array\<PhotoBrowserUIElement>, isVisible: boolean): void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerOptions；<br>API声明：isSlidingSelectionSupported?: boolean;<br>差异内容：isSlidingSelectionSupported?: boolean;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerOptions；<br>API声明：photoBrowserCheckboxPosition?: [<br>        number,<br>        number<br>    ];<br>差异内容：photoBrowserCheckboxPosition?: [<br>        number,<br>        number<br>    ];|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum PhotoBrowserUIElement<br>差异内容：export declare enum PhotoBrowserUIElement|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PhotoBrowserUIElement；<br>API声明：CHECKBOX = 0<br>差异内容：CHECKBOX = 0|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PhotoBrowserUIElement；<br>API声明：BACK_BUTTON = 1<br>差异内容：BACK_BUTTON = 1|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：RecentPhotoComponent；<br>API声明：onRecentPhotoCheckInfo?: RecentPhotoCheckInfoCallback;<br>差异内容：onRecentPhotoCheckInfo?: RecentPhotoCheckInfoCallback;|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export type RecentPhotoCheckInfoCallback = (recentPhotoExists: boolean, info: RecentPhotoInfo) => void;<br>差异内容：export type RecentPhotoCheckInfoCallback = (recentPhotoExists: boolean, info: RecentPhotoInfo) => void;|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare class RecentPhotoInfo<br>差异内容：export declare class RecentPhotoInfo|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：RecentPhotoInfo；<br>API声明：dateTaken?: number;<br>差异内容：dateTaken?: number;|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：RecentPhotoInfo；<br>API声明：identifier?: string;<br>差异内容：identifier?: string;|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：MediaAssetChangeRequest；<br>API声明：saveCameraPhoto(imageFileType: ImageFileType): void;<br>差异内容：saveCameraPhoto(imageFileType: ImageFileType): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：interface QuickImageDataHandler<br>差异内容：interface QuickImageDataHandler|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：QuickImageDataHandler；<br>API声明：onDataPrepared(data: T, imageSource: image.ImageSource, map: Map\<string, string>): void;<br>差异内容：onDataPrepared(data: T, imageSource: image.ImageSource, map: Map\<string, string>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetManager；<br>API声明：static quickRequestImage(context: Context, asset: PhotoAsset, requestOptions: RequestOptions, dataHandler: QuickImageDataHandler\<image.Picture>): Promise\<string>;<br>差异内容：static quickRequestImage(context: Context, asset: PhotoAsset, requestOptions: RequestOptions, dataHandler: QuickImageDataHandler\<image.Picture>): Promise\<string>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：DETAIL_TIME = 'detail_time'<br>差异内容：DETAIL_TIME = 'detail_time'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：DATE_TAKEN_MS = 'date_taken_ms'<br>差异内容：DATE_TAKEN_MS = 'date_taken_ms'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：enum ImageFileType<br>差异内容：enum ImageFileType|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：ImageFileType；<br>API声明：JPEG = 1<br>差异内容：JPEG = 1|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：ImageFileType；<br>API声明：HEIF = 2<br>差异内容：HEIF = 2|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MovingPhotoViewAttribute；<br>API声明：onComplete(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute;<br>差异内容：onComplete(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute;|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：MovingPhotoViewAttribute；<br>API声明：autoPlayPeriod(startTime: number, endTime: number): MovingPhotoViewAttribute;<br>差异内容：autoPlayPeriod(startTime: number, endTime: number): MovingPhotoViewAttribute;|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：MovingPhotoViewAttribute；<br>API声明：autoPlay(isAutoPlay: boolean): MovingPhotoViewAttribute;<br>差异内容：autoPlay(isAutoPlay: boolean): MovingPhotoViewAttribute;|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：MovingPhotoViewAttribute；<br>API声明：repeatPlay(isRepeatPlay: boolean): MovingPhotoViewAttribute;<br>差异内容：repeatPlay(isRepeatPlay: boolean): MovingPhotoViewAttribute;|api/@ohos.multimedia.movingphotoview.d.ts|
|新增导出符号|类名：global；<br>API声明：export type EmptyAreaClickCallback = () => void;<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export type EmptyAreaClickCallback = () => void;|api/@ohos.file.AlbumPickerComponent.d.ets|
|新增导出符号|类名：global；<br>API声明：export type ItemsDeletedCallback = (baseItemInfos: Array\<BaseItemInfo>) => void;<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export type ItemsDeletedCallback = (baseItemInfos: Array\<BaseItemInfo>) => void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增导出符号|类名：global；<br>API声明：export type ExceedMaxSelectedCallback = (exceedMaxCountType: MaxCountType) => void;<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export type ExceedMaxSelectedCallback = (exceedMaxCountType: MaxCountType) => void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增导出符号|类名：global；<br>API声明：export type CurrentAlbumDeletedCallback = () => void;<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export type CurrentAlbumDeletedCallback = () => void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增导出符号|类名：global；<br>API声明：export declare enum PhotoBrowserUIElement<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export declare enum PhotoBrowserUIElement|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增导出符号|类名：global；<br>API声明：export type RecentPhotoCheckInfoCallback = (recentPhotoExists: boolean, info: RecentPhotoInfo) => void;<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export type RecentPhotoCheckInfoCallback = (recentPhotoExists: boolean, info: RecentPhotoInfo) => void;|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增导出符号|类名：global；<br>API声明：export declare class RecentPhotoInfo<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export declare class RecentPhotoInfo|api/@ohos.file.RecentPhotoComponent.d.ets|
