| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API跨平台权限变更|类名：AlbumKeys；<br>API声明：URI = 'uri'<br>差异内容：NA|类名：AlbumKeys；<br>API声明：URI = 'uri'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|新增错误码|类名：FetchResult；<br>API声明：getCount(): number;<br>差异内容：NA|类名：FetchResult；<br>API声明：getCount(): number;<br>差异内容：401|api/@ohos.file.photoAccessHelper.d.ts|
|新增错误码|类名：FetchResult；<br>API声明：isAfterLast(): boolean;<br>差异内容：NA|类名：FetchResult；<br>API声明：isAfterLast(): boolean;<br>差异内容：401|api/@ohos.file.photoAccessHelper.d.ts|
|新增错误码|类名：FetchResult；<br>API声明：getFirstObject(callback: AsyncCallback\<T>): void;<br>差异内容：NA|类名：FetchResult；<br>API声明：getFirstObject(callback: AsyncCallback\<T>): void;<br>差异内容：401|api/@ohos.file.photoAccessHelper.d.ts|
|新增错误码|类名：FetchResult；<br>API声明：getFirstObject(): Promise\<T>;<br>差异内容：NA|类名：FetchResult；<br>API声明：getFirstObject(): Promise\<T>;<br>差异内容：401|api/@ohos.file.photoAccessHelper.d.ts|
|新增错误码|类名：FetchResult；<br>API声明：getNextObject(callback: AsyncCallback\<T>): void;<br>差异内容：NA|类名：FetchResult；<br>API声明：getNextObject(callback: AsyncCallback\<T>): void;<br>差异内容：401|api/@ohos.file.photoAccessHelper.d.ts|
|新增错误码|类名：FetchResult；<br>API声明：getNextObject(): Promise\<T>;<br>差异内容：NA|类名：FetchResult；<br>API声明：getNextObject(): Promise\<T>;<br>差异内容：401|api/@ohos.file.photoAccessHelper.d.ts|
|新增错误码|类名：FetchResult；<br>API声明：getLastObject(callback: AsyncCallback\<T>): void;<br>差异内容：NA|类名：FetchResult；<br>API声明：getLastObject(callback: AsyncCallback\<T>): void;<br>差异内容：401|api/@ohos.file.photoAccessHelper.d.ts|
|新增错误码|类名：FetchResult；<br>API声明：getLastObject(): Promise\<T>;<br>差异内容：NA|类名：FetchResult；<br>API声明：getLastObject(): Promise\<T>;<br>差异内容：401|api/@ohos.file.photoAccessHelper.d.ts|
|新增错误码|类名：FetchResult；<br>API声明：getObjectByPosition(index: number, callback: AsyncCallback\<T>): void;<br>差异内容：NA|类名：FetchResult；<br>API声明：getObjectByPosition(index: number, callback: AsyncCallback\<T>): void;<br>差异内容：401|api/@ohos.file.photoAccessHelper.d.ts|
|新增错误码|类名：FetchResult；<br>API声明：getObjectByPosition(index: number): Promise\<T>;<br>差异内容：NA|类名：FetchResult；<br>API声明：getObjectByPosition(index: number): Promise\<T>;<br>差异内容：401|api/@ohos.file.photoAccessHelper.d.ts|
|新增错误码|类名：FetchResult；<br>API声明：getAllObjects(callback: AsyncCallback\<Array\<T>>): void;<br>差异内容：NA|类名：FetchResult；<br>API声明：getAllObjects(callback: AsyncCallback\<Array\<T>>): void;<br>差异内容：401|api/@ohos.file.photoAccessHelper.d.ts|
|新增错误码|类名：FetchResult；<br>API声明：getAllObjects(): Promise\<Array\<T>>;<br>差异内容：NA|类名：FetchResult；<br>API声明：getAllObjects(): Promise\<Array\<T>>;<br>差异内容：401|api/@ohos.file.photoAccessHelper.d.ts|
|新增错误码|类名：FetchResult；<br>API声明：close(): void;<br>差异内容：NA|类名：FetchResult；<br>API声明：close(): void;<br>差异内容：401|api/@ohos.file.photoAccessHelper.d.ts|
|新增错误码|类名：PhotoAccessHelper；<br>API声明：getAssets(options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：NA|类名：PhotoAccessHelper；<br>API声明：getAssets(options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：13900012,401|api/@ohos.file.photoAccessHelper.d.ts|
|新增错误码|类名：PhotoAccessHelper；<br>API声明：getBurstAssets(burstKey: string, options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：NA|类名：PhotoAccessHelper；<br>API声明：getBurstAssets(burstKey: string, options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：401|api/@ohos.file.photoAccessHelper.d.ts|
|删除错误码|类名：MediaAssetManager；<br>API声明：static requestMovingPhoto(context: Context, asset: PhotoAsset, requestOptions: RequestOptions, dataHandler: MediaAssetDataHandler\<MovingPhoto>): Promise\<string>;<br>差异内容：801|类名：MediaAssetManager；<br>API声明：static requestMovingPhoto(context: Context, asset: PhotoAsset, requestOptions: RequestOptions, dataHandler: MediaAssetDataHandler\<MovingPhoto>): Promise\<string>;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除错误码|类名：PhotoAccessHelper；<br>API声明：getAssets(options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：201|类名：PhotoAccessHelper；<br>API声明：getAssets(options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：PhotoAsset；<br>API声明：commitModify(callback: AsyncCallback\<void>): void;<br>差异内容：13900020,14000001,14000011,201,401|类名：PhotoAsset；<br>API声明：commitModify(callback: AsyncCallback\<void>): void;<br>差异内容：13900012,13900020,14000001,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：PhotoAsset；<br>API声明：commitModify(): Promise\<void>;<br>差异内容：13900020,14000001,14000011,201,401|类名：PhotoAsset；<br>API声明：commitModify(): Promise\<void>;<br>差异内容：13900012,13900020,14000001,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：PhotoAsset；<br>API声明：getReadOnlyFd(callback: AsyncCallback\<number>): void;<br>差异内容：13900020,14000011,201,401|类名：PhotoAsset；<br>API声明：getReadOnlyFd(callback: AsyncCallback\<number>): void;<br>差异内容：13900012,13900020,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：PhotoAsset；<br>API声明：getReadOnlyFd(): Promise\<number>;<br>差异内容：13900020,14000011,201,401|类名：PhotoAsset；<br>API声明：getReadOnlyFd(): Promise\<number>;<br>差异内容：13900012,13900020,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：AbsAlbum；<br>API声明：getAssets(options: FetchOptions, callback: AsyncCallback\<FetchResult\<PhotoAsset>>): void;<br>差异内容：13900020,14000011,201,401|类名：AbsAlbum；<br>API声明：getAssets(options: FetchOptions, callback: AsyncCallback\<FetchResult\<PhotoAsset>>): void;<br>差异内容：13900012,13900020,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：AbsAlbum；<br>API声明：getAssets(options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：13900020,14000011,201,401|类名：AbsAlbum；<br>API声明：getAssets(options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：13900012,13900020,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：Album；<br>API声明：commitModify(callback: AsyncCallback\<void>): void;<br>差异内容：13900020,14000011,201,401|类名：Album；<br>API声明：commitModify(callback: AsyncCallback\<void>): void;<br>差异内容：13900012,13900020,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：Album；<br>API声明：commitModify(): Promise\<void>;<br>差异内容：13900020,14000011,201,401|类名：Album；<br>API声明：commitModify(): Promise\<void>;<br>差异内容：13900012,13900020,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：Album；<br>API声明：addAssets(assets: Array\<PhotoAsset>, callback: AsyncCallback\<void>): void;<br>差异内容：13900020,14000011,201,401|类名：Album；<br>API声明：addAssets(assets: Array\<PhotoAsset>, callback: AsyncCallback\<void>): void;<br>差异内容：13900012,13900020,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：Album；<br>API声明：addAssets(assets: Array\<PhotoAsset>): Promise\<void>;<br>差异内容：13900020,14000011,201,401|类名：Album；<br>API声明：addAssets(assets: Array\<PhotoAsset>): Promise\<void>;<br>差异内容：13900012,13900020,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：Album；<br>API声明：removeAssets(assets: Array\<PhotoAsset>, callback: AsyncCallback\<void>): void;<br>差异内容：13900020,14000011,201,401|类名：Album；<br>API声明：removeAssets(assets: Array\<PhotoAsset>, callback: AsyncCallback\<void>): void;<br>差异内容：13900012,13900020,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：Album；<br>API声明：removeAssets(assets: Array\<PhotoAsset>): Promise\<void>;<br>差异内容：13900020,14000011,201,401|类名：Album；<br>API声明：removeAssets(assets: Array\<PhotoAsset>): Promise\<void>;<br>差异内容：13900012,13900020,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：PhotoAccessHelper；<br>API声明：getAssets(options: FetchOptions, callback: AsyncCallback\<FetchResult\<PhotoAsset>>): void;<br>差异内容：13900020,14000011,201,401|类名：PhotoAccessHelper；<br>API声明：getAssets(options: FetchOptions, callback: AsyncCallback\<FetchResult\<PhotoAsset>>): void;<br>差异内容：13900012,13900020,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：PhotoAccessHelper；<br>API声明：createAsset(photoType: PhotoType, extension: string, options: CreateOptions, callback: AsyncCallback\<string>): void;<br>差异内容：13900020,14000011,201,401|类名：PhotoAccessHelper；<br>API声明：createAsset(photoType: PhotoType, extension: string, options: CreateOptions, callback: AsyncCallback\<string>): void;<br>差异内容：13900012,13900020,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：PhotoAccessHelper；<br>API声明：createAsset(photoType: PhotoType, extension: string, callback: AsyncCallback\<string>): void;<br>差异内容：13900020,14000011,201,401|类名：PhotoAccessHelper；<br>API声明：createAsset(photoType: PhotoType, extension: string, callback: AsyncCallback\<string>): void;<br>差异内容：13900012,13900020,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：PhotoAccessHelper；<br>API声明：createAsset(photoType: PhotoType, extension: string, options?: CreateOptions): Promise\<string>;<br>差异内容：13900020,14000011,201,401|类名：PhotoAccessHelper；<br>API声明：createAsset(photoType: PhotoType, extension: string, options?: CreateOptions): Promise\<string>;<br>差异内容：13900012,13900020,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：PhotoAccessHelper；<br>API声明：getAlbums(type: AlbumType, subtype: AlbumSubtype, options: FetchOptions, callback: AsyncCallback\<FetchResult\<Album>>): void;<br>差异内容：13900020,14000011,201,401|类名：PhotoAccessHelper；<br>API声明：getAlbums(type: AlbumType, subtype: AlbumSubtype, options: FetchOptions, callback: AsyncCallback\<FetchResult\<Album>>): void;<br>差异内容：13900012,13900020,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：PhotoAccessHelper；<br>API声明：getAlbums(type: AlbumType, subtype: AlbumSubtype, callback: AsyncCallback\<FetchResult\<Album>>): void;<br>差异内容：13900020,14000011,201,401|类名：PhotoAccessHelper；<br>API声明：getAlbums(type: AlbumType, subtype: AlbumSubtype, callback: AsyncCallback\<FetchResult\<Album>>): void;<br>差异内容：13900012,13900020,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|错误码变更|类名：PhotoAccessHelper；<br>API声明：getAlbums(type: AlbumType, subtype: AlbumSubtype, options?: FetchOptions): Promise\<FetchResult\<Album>>;<br>差异内容：13900020,14000011,201,401|类名：PhotoAccessHelper；<br>API声明：getAlbums(type: AlbumType, subtype: AlbumSubtype, options?: FetchOptions): Promise\<FetchResult\<Album>>;<br>差异内容：13900012,13900020,14000011,401|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PickerOptions；<br>API声明：gridStartOffset?: number;<br>差异内容：gridStartOffset?: number;|NA|api/@ohos.file.PhotoPickerComponent.d.ets|
|删除API|类名：PickerOptions；<br>API声明：gridEndOffset?: number;<br>差异内容：gridEndOffset?: number;|NA|api/@ohos.file.PhotoPickerComponent.d.ets|
|删除API|类名：PickerOptions；<br>API声明：singleLineConfig?: SingleLineConfig;<br>差异内容：singleLineConfig?: SingleLineConfig;|NA|api/@ohos.file.PhotoPickerComponent.d.ets|
|删除API|类名：PickerOptions；<br>API声明：uiComponentColorMode?: PickerColorMode;<br>差异内容：uiComponentColorMode?: PickerColorMode;|NA|api/@ohos.file.PhotoPickerComponent.d.ets|
|删除API|类名：global；<br>API声明：export declare class SingleLineConfig<br>差异内容：export declare class SingleLineConfig|NA|api/@ohos.file.PhotoPickerComponent.d.ets|
|删除API|类名：SingleLineConfig；<br>API声明：itemDisplayRatio?: ItemDisplayRatio;<br>差异内容：itemDisplayRatio?: ItemDisplayRatio;|NA|api/@ohos.file.PhotoPickerComponent.d.ets|
|删除API|类名：SingleLineConfig；<br>API声明：itemBorderRadius?: Length \| BorderRadiuses \| LocalizedBorderRadiuses;<br>差异内容：itemBorderRadius?: Length \| BorderRadiuses \| LocalizedBorderRadiuses;|NA|api/@ohos.file.PhotoPickerComponent.d.ets|
|删除API|类名：SingleLineConfig；<br>API声明：itemGap?: Length;<br>差异内容：itemGap?: Length;|NA|api/@ohos.file.PhotoPickerComponent.d.ets|
|删除API|类名：global；<br>API声明：export declare enum ItemDisplayRatio<br>差异内容：export declare enum ItemDisplayRatio|NA|api/@ohos.file.PhotoPickerComponent.d.ets|
|删除API|类名：ItemDisplayRatio；<br>API声明：SQUARE_RATIO = 0<br>差异内容：SQUARE_RATIO = 0|NA|api/@ohos.file.PhotoPickerComponent.d.ets|
|删除API|类名：ItemDisplayRatio；<br>API声明：ORIGINAL_SIZE_RATIO = 1<br>差异内容：ORIGINAL_SIZE_RATIO = 1|NA|api/@ohos.file.PhotoPickerComponent.d.ets|
|删除API|类名：AlbumPickerComponent；<br>API声明：albumPickerController?: AlbumPickerController;<br>差异内容：albumPickerController?: AlbumPickerController;|NA|api/@ohos.file.AlbumPickerComponent.d.ets|
|删除API|类名：AlbumPickerOptions；<br>API声明：fontSize?: number \| string;<br>差异内容：fontSize?: number \| string;|NA|api/@ohos.file.AlbumPickerComponent.d.ets|
|删除API|类名：global；<br>API声明：export declare class AlbumPickerController<br>差异内容：export declare class AlbumPickerController|NA|api/@ohos.file.AlbumPickerComponent.d.ets|
|删除API|类名：AlbumPickerController；<br>API声明：setFontSize(fontSize: number \| string): void;<br>差异内容：setFontSize(fontSize: number \| string): void;|NA|api/@ohos.file.AlbumPickerComponent.d.ets|
|删除API|类名：photoAccessHelper；<br>API声明：enum PositionType<br>差异内容：enum PositionType|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PositionType；<br>API声明：LOCAL = 1<br>差异内容：LOCAL = 1|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PositionType；<br>API声明：CLOUD = 2<br>差异内容：CLOUD = 2|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PositionType；<br>API声明：LOCAL_AND_CLOUD = 3<br>差异内容：LOCAL_AND_CLOUD = 3|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoKeys；<br>API声明：POSITION = 'position'<br>差异内容：POSITION = 'position'|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoKeys；<br>API声明：MEDIA_SUFFIX = 'media_suffix'<br>差异内容：MEDIA_SUFFIX = 'media_suffix'|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：photoAccessHelper；<br>API声明：enum NotifyChangeType<br>差异内容：enum NotifyChangeType|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：NotifyChangeType；<br>API声明：NOTIFY_CHANGE_ADD = 0<br>差异内容：NOTIFY_CHANGE_ADD = 0|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：NotifyChangeType；<br>API声明：NOTIFY_CHANGE_UPDATE = 1<br>差异内容：NOTIFY_CHANGE_UPDATE = 1|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：NotifyChangeType；<br>API声明：NOTIFY_CHANGE_REMOVE = 2<br>差异内容：NOTIFY_CHANGE_REMOVE = 2|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoAccessHelper；<br>API声明：getSupportedPhotoFormats(photoType: PhotoType): Promise\<Array\<string>>;<br>差异内容：getSupportedPhotoFormats(photoType: PhotoType): Promise\<Array\<string>>;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoAccessHelper；<br>API声明：on(type: 'photoChange', callback: Callback\<PhotoAssetChangeInfos>): void;<br>差异内容：on(type: 'photoChange', callback: Callback\<PhotoAssetChangeInfos>): void;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoAccessHelper；<br>API声明：off(type: 'photoChange', callback?: Callback\<PhotoAssetChangeInfos>): void;<br>差异内容：off(type: 'photoChange', callback?: Callback\<PhotoAssetChangeInfos>): void;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoAccessHelper；<br>API声明：on(type: 'photoAlbumChange', callback: Callback\<AlbumChangeInfos>): void;<br>差异内容：on(type: 'photoAlbumChange', callback: Callback\<AlbumChangeInfos>): void;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoAccessHelper；<br>API声明：off(type: 'photoAlbumChange', callback?: Callback\<AlbumChangeInfos>): void;<br>差异内容：off(type: 'photoAlbumChange', callback?: Callback\<AlbumChangeInfos>): void;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoAccessHelper；<br>API声明：getPhotoPickerComponentDefaultAlbumName(): Promise\<string>;<br>差异内容：getPhotoPickerComponentDefaultAlbumName(): Promise\<string>;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoAccessHelper；<br>API声明：getRecentPhotoInfo(options?: RecentPhotoOptions): Promise\<RecentPhotoInfo>;<br>差异内容：getRecentPhotoInfo(options?: RecentPhotoOptions): Promise\<RecentPhotoInfo>;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：photoAccessHelper；<br>API声明：export class RecentPhotoOptions<br>差异内容：export class RecentPhotoOptions|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：RecentPhotoOptions；<br>API声明：period?: number;<br>差异内容：period?: number;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：RecentPhotoOptions；<br>API声明：MIMEType?: photoAccessHelper.PhotoViewMIMETypes;<br>差异内容：MIMEType?: photoAccessHelper.PhotoViewMIMETypes;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：RecentPhotoOptions；<br>API声明：photoSource?: PhotoSource;<br>差异内容：photoSource?: PhotoSource;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：photoAccessHelper；<br>API声明：export class RecentPhotoInfo<br>差异内容：export class RecentPhotoInfo|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：RecentPhotoInfo；<br>API声明：dateTaken?: number;<br>差异内容：dateTaken?: number;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：RecentPhotoInfo；<br>API声明：identifier?: string;<br>差异内容：identifier?: string;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：photoAccessHelper；<br>API声明：export enum PhotoSource<br>差异内容：export enum PhotoSource|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoSource；<br>API声明：ALL = 0<br>差异内容：ALL = 0|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoSource；<br>API声明：CAMERA = 1<br>差异内容：CAMERA = 1|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoSource；<br>API声明：SCREENSHOT = 2<br>差异内容：SCREENSHOT = 2|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：photoAccessHelper；<br>API声明：interface PhotoAssetChangeInfos<br>差异内容：interface PhotoAssetChangeInfos|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoAssetChangeInfos；<br>API声明：type: NotifyChangeType;<br>差异内容：type: NotifyChangeType;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoAssetChangeInfos；<br>API声明：assetChangeDatas: PhotoAssetChangeData[] \| null;<br>差异内容：assetChangeDatas: PhotoAssetChangeData[] \| null;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoAssetChangeInfos；<br>API声明：isForRecheck: boolean;<br>差异内容：isForRecheck: boolean;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：photoAccessHelper；<br>API声明：interface PhotoAssetChangeData<br>差异内容：interface PhotoAssetChangeData|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoAssetChangeData；<br>API声明：assetBeforeChange: PhotoAssetChangeInfo \| null;<br>差异内容：assetBeforeChange: PhotoAssetChangeInfo \| null;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoAssetChangeData；<br>API声明：assetAfterChange: PhotoAssetChangeInfo \| null;<br>差异内容：assetAfterChange: PhotoAssetChangeInfo \| null;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoAssetChangeData；<br>API声明：isContentChanged: boolean;<br>差异内容：isContentChanged: boolean;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoAssetChangeData；<br>API声明：isDeleted: boolean;<br>差异内容：isDeleted: boolean;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：photoAccessHelper；<br>API声明：interface PhotoAssetChangeInfo<br>差异内容：interface PhotoAssetChangeInfo|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoAssetChangeInfo；<br>API声明：uri: string;<br>差异内容：uri: string;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoAssetChangeInfo；<br>API声明：mediaType: PhotoType;<br>差异内容：mediaType: PhotoType;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoAssetChangeInfo；<br>API声明：albumUri: string;<br>差异内容：albumUri: string;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：photoAccessHelper；<br>API声明：interface AlbumChangeInfos<br>差异内容：interface AlbumChangeInfos|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：AlbumChangeInfos；<br>API声明：type: NotifyChangeType;<br>差异内容：type: NotifyChangeType;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：AlbumChangeInfos；<br>API声明：albumChangeDatas: AlbumChangeData[] \| null;<br>差异内容：albumChangeDatas: AlbumChangeData[] \| null;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：AlbumChangeInfos；<br>API声明：isForRecheck: boolean;<br>差异内容：isForRecheck: boolean;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：photoAccessHelper；<br>API声明：interface AlbumChangeData<br>差异内容：interface AlbumChangeData|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：AlbumChangeData；<br>API声明：albumBeforeChange: AlbumChangeInfo \| null;<br>差异内容：albumBeforeChange: AlbumChangeInfo \| null;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：AlbumChangeData；<br>API声明：albumAfterChange: AlbumChangeInfo \| null;<br>差异内容：albumAfterChange: AlbumChangeInfo \| null;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：photoAccessHelper；<br>API声明：interface AlbumChangeInfo<br>差异内容：interface AlbumChangeInfo|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：AlbumChangeInfo；<br>API声明：albumType: AlbumType;<br>差异内容：albumType: AlbumType;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：AlbumChangeInfo；<br>API声明：albumSubtype: AlbumSubtype;<br>差异内容：albumSubtype: AlbumSubtype;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：AlbumChangeInfo；<br>API声明：albumName: string;<br>差异内容：albumName: string;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：AlbumChangeInfo；<br>API声明：albumUri: string;<br>差异内容：albumUri: string;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：AlbumChangeInfo；<br>API声明：imageCount: number;<br>差异内容：imageCount: number;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：AlbumChangeInfo；<br>API声明：videoCount: number;<br>差异内容：videoCount: number;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：AlbumChangeInfo；<br>API声明：count: number;<br>差异内容：count: number;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：AlbumChangeInfo；<br>API声明：coverUri: string;<br>差异内容：coverUri: string;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：photoAccessHelper；<br>API声明：export enum FilterOperator<br>差异内容：export enum FilterOperator|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：FilterOperator；<br>API声明：EQUAL_TO = 0<br>差异内容：EQUAL_TO = 0|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：FilterOperator；<br>API声明：NOT_EQUAL_TO = 1<br>差异内容：NOT_EQUAL_TO = 1|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：FilterOperator；<br>API声明：MORE_THAN = 2<br>差异内容：MORE_THAN = 2|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：FilterOperator；<br>API声明：LESS_THAN = 3<br>差异内容：LESS_THAN = 3|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：FilterOperator；<br>API声明：MORE_THAN_OR_EQUAL_TO = 4<br>差异内容：MORE_THAN_OR_EQUAL_TO = 4|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：FilterOperator；<br>API声明：LESS_THAN_OR_EQUAL_TO = 5<br>差异内容：LESS_THAN_OR_EQUAL_TO = 5|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：FilterOperator；<br>API声明：BETWEEN = 6<br>差异内容：BETWEEN = 6|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：photoAccessHelper；<br>API声明：export enum SingleSelectionMode<br>差异内容：export enum SingleSelectionMode|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：SingleSelectionMode；<br>API声明：BROWSER_MODE = 0<br>差异内容：BROWSER_MODE = 0|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：SingleSelectionMode；<br>API声明：SELECT_MODE = 1<br>差异内容：SELECT_MODE = 1|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：SingleSelectionMode；<br>API声明：BROWSER_AND_SELECT_MODE = 2<br>差异内容：BROWSER_AND_SELECT_MODE = 2|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：BaseSelectOptions；<br>API声明：singleSelectionMode?: SingleSelectionMode;<br>差异内容：singleSelectionMode?: SingleSelectionMode;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：BaseSelectOptions；<br>API声明：mimeTypeFilter?: MimeTypeFilter;<br>差异内容：mimeTypeFilter?: MimeTypeFilter;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：BaseSelectOptions；<br>API声明：fileSizeFilter?: FileSizeFilter;<br>差异内容：fileSizeFilter?: FileSizeFilter;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：BaseSelectOptions；<br>API声明：videoDurationFilter?: VideoDurationFilter;<br>差异内容：videoDurationFilter?: VideoDurationFilter;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：BaseSelectOptions；<br>API声明：combinedMediaTypeFilter?: Array\<string>;<br>差异内容：combinedMediaTypeFilter?: Array\<string>;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：BaseSelectOptions；<br>API声明：photoViewMimeTypeFileSizeFilters?: Array\<PhotoViewMimeTypeFileSizeFilter>;<br>差异内容：photoViewMimeTypeFileSizeFilters?: Array\<PhotoViewMimeTypeFileSizeFilter>;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：photoAccessHelper；<br>API声明：class MimeTypeFilter<br>差异内容：class MimeTypeFilter|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：MimeTypeFilter；<br>API声明：mimeTypeArray: Array\<string>;<br>差异内容：mimeTypeArray: Array\<string>;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：photoAccessHelper；<br>API声明：class FileSizeFilter<br>差异内容：class FileSizeFilter|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：FileSizeFilter；<br>API声明：filterOperator: FilterOperator;<br>差异内容：filterOperator: FilterOperator;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：FileSizeFilter；<br>API声明：fileSize: number;<br>差异内容：fileSize: number;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：FileSizeFilter；<br>API声明：extraFileSize?: number;<br>差异内容：extraFileSize?: number;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：photoAccessHelper；<br>API声明：class VideoDurationFilter<br>差异内容：class VideoDurationFilter|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：VideoDurationFilter；<br>API声明：filterOperator: FilterOperator;<br>差异内容：filterOperator: FilterOperator;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：VideoDurationFilter；<br>API声明：videoDuration: number;<br>差异内容：videoDuration: number;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：VideoDurationFilter；<br>API声明：extraVideoDuration?: number;<br>差异内容：extraVideoDuration?: number;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：photoAccessHelper；<br>API声明：class PhotoViewMimeTypeFileSizeFilter<br>差异内容：class PhotoViewMimeTypeFileSizeFilter|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoViewMimeTypeFileSizeFilter；<br>API声明：photoViewMimeType: PhotoViewMIMETypes;<br>差异内容：photoViewMimeType: PhotoViewMIMETypes;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：PhotoViewMimeTypeFileSizeFilter；<br>API声明：sizeFilter: FileSizeFilter;<br>差异内容：sizeFilter: FileSizeFilter;|NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：RecentPhotoOptions；<br>API声明：isAutoRefreshSupported?: boolean;<br>差异内容：isAutoRefreshSupported?: boolean;|NA|api/@ohos.file.RecentPhotoComponent.d.ets|
|删除API|类名：RecentPhotoOptions；<br>API声明：colorMode?: PickerColorMode;<br>差异内容：colorMode?: PickerColorMode;|NA|api/@ohos.file.RecentPhotoComponent.d.ets|
|删除API|类名：MovingPhotoViewOptions；<br>API声明：imageAIOptions?: ImageAIOptions;<br>差异内容：imageAIOptions?: ImageAIOptions;|NA|api/@ohos.multimedia.movingphotoview.d.ts|
|删除API|类名：MovingPhotoViewAttribute；<br>API声明：onPrepared(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute;<br>差异内容：onPrepared(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute;|NA|api/@ohos.multimedia.movingphotoview.d.ts|
|删除API|类名：MovingPhotoViewAttribute；<br>API声明：enableAnalyzer(enabled: boolean): MovingPhotoViewAttribute;<br>差异内容：enableAnalyzer(enabled: boolean): MovingPhotoViewAttribute;|NA|api/@ohos.multimedia.movingphotoview.d.ts|
|删除API|类名：MovingPhotoViewController；<br>API声明：refreshMovingPhoto();<br>差异内容：refreshMovingPhoto();|NA|api/@ohos.multimedia.movingphotoview.d.ts|
|起始版本有变化|类名：photoAccessHelper；<br>API声明：enum PhotoSubtype<br>差异内容：12|类名：photoAccessHelper；<br>API声明：enum PhotoSubtype<br>差异内容：10|api/@ohos.file.photoAccessHelper.d.ts|
|起始版本有变化|类名：PhotoSubtype；<br>API声明：DEFAULT = 0<br>差异内容：12|类名：PhotoSubtype；<br>API声明：DEFAULT = 0<br>差异内容：10|api/@ohos.file.photoAccessHelper.d.ts|
|起始版本有变化|类名：AlbumSubtype；<br>API声明：IMAGE = 1031<br>差异内容：12|类名：AlbumSubtype；<br>API声明：IMAGE = 1031<br>差异内容：11|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoAsset；<br>API声明：readonly photoType: PhotoType;<br>差异内容：atomicservice|类名：PhotoAsset；<br>API声明：readonly photoType: PhotoType;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoAsset；<br>API声明：readonly displayName: string;<br>差异内容：atomicservice|类名：PhotoAsset；<br>API声明：readonly displayName: string;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoAsset；<br>API声明：get(member: string): MemberType;<br>差异内容：atomicservice|类名：PhotoAsset；<br>API声明：get(member: string): MemberType;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：photoAccessHelper；<br>API声明：enum PhotoKeys<br>差异内容：atomicservice|类名：photoAccessHelper；<br>API声明：enum PhotoKeys<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：URI = 'uri'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：URI = 'uri'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：PHOTO_TYPE = 'media_type'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：PHOTO_TYPE = 'media_type'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：DISPLAY_NAME = 'display_name'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：DISPLAY_NAME = 'display_name'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：SIZE = 'size'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：SIZE = 'size'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：DATE_ADDED = 'date_added'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：DATE_ADDED = 'date_added'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：DATE_MODIFIED = 'date_modified'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：DATE_MODIFIED = 'date_modified'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：DURATION = 'duration'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：DURATION = 'duration'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：WIDTH = 'width'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：WIDTH = 'width'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：HEIGHT = 'height'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：HEIGHT = 'height'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：DATE_TAKEN = 'date_taken'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：DATE_TAKEN = 'date_taken'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：ORIENTATION = 'orientation'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：ORIENTATION = 'orientation'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：FAVORITE = 'is_favorite'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：FAVORITE = 'is_favorite'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：TITLE = 'title'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：TITLE = 'title'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：DATE_ADDED_MS = 'date_added_ms'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：DATE_ADDED_MS = 'date_added_ms'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：DATE_MODIFIED_MS = 'date_modified_ms'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：DATE_MODIFIED_MS = 'date_modified_ms'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：PHOTO_SUBTYPE = 'subtype'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：PHOTO_SUBTYPE = 'subtype'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：DYNAMIC_RANGE_TYPE = 'dynamic_range_type'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：DYNAMIC_RANGE_TYPE = 'dynamic_range_type'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：COVER_POSITION = 'cover_position'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：COVER_POSITION = 'cover_position'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：BURST_KEY = 'burst_key'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：BURST_KEY = 'burst_key'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：LCD_SIZE = 'lcd_size'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：LCD_SIZE = 'lcd_size'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：THM_SIZE = 'thm_size'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：THM_SIZE = 'thm_size'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：DETAIL_TIME = 'detail_time'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：DETAIL_TIME = 'detail_time'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoKeys；<br>API声明：DATE_TAKEN_MS = 'date_taken_ms'<br>差异内容：atomicservice|类名：PhotoKeys；<br>API声明：DATE_TAKEN_MS = 'date_taken_ms'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：AlbumKeys；<br>API声明：URI = 'uri'<br>差异内容：atomicservice|类名：AlbumKeys；<br>API声明：URI = 'uri'<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：photoAccessHelper；<br>API声明：interface FetchOptions<br>差异内容：atomicservice|类名：photoAccessHelper；<br>API声明：interface FetchOptions<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：FetchOptions；<br>API声明：fetchColumns: Array\<string>;<br>差异内容：atomicservice|类名：FetchOptions；<br>API声明：fetchColumns: Array\<string>;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：FetchOptions；<br>API声明：predicates: dataSharePredicates.DataSharePredicates;<br>差异内容：atomicservice|类名：FetchOptions；<br>API声明：predicates: dataSharePredicates.DataSharePredicates;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：photoAccessHelper；<br>API声明：interface FetchResult<br>差异内容：atomicservice|类名：photoAccessHelper；<br>API声明：interface FetchResult<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：FetchResult；<br>API声明：getCount(): number;<br>差异内容：atomicservice|类名：FetchResult；<br>API声明：getCount(): number;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：FetchResult；<br>API声明：isAfterLast(): boolean;<br>差异内容：atomicservice|类名：FetchResult；<br>API声明：isAfterLast(): boolean;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：FetchResult；<br>API声明：getFirstObject(callback: AsyncCallback\<T>): void;<br>差异内容：atomicservice|类名：FetchResult；<br>API声明：getFirstObject(callback: AsyncCallback\<T>): void;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：FetchResult；<br>API声明：getFirstObject(): Promise\<T>;<br>差异内容：atomicservice|类名：FetchResult；<br>API声明：getFirstObject(): Promise\<T>;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：FetchResult；<br>API声明：getNextObject(callback: AsyncCallback\<T>): void;<br>差异内容：atomicservice|类名：FetchResult；<br>API声明：getNextObject(callback: AsyncCallback\<T>): void;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：FetchResult；<br>API声明：getNextObject(): Promise\<T>;<br>差异内容：atomicservice|类名：FetchResult；<br>API声明：getNextObject(): Promise\<T>;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：FetchResult；<br>API声明：getLastObject(callback: AsyncCallback\<T>): void;<br>差异内容：atomicservice|类名：FetchResult；<br>API声明：getLastObject(callback: AsyncCallback\<T>): void;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：FetchResult；<br>API声明：getLastObject(): Promise\<T>;<br>差异内容：atomicservice|类名：FetchResult；<br>API声明：getLastObject(): Promise\<T>;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：FetchResult；<br>API声明：getObjectByPosition(index: number, callback: AsyncCallback\<T>): void;<br>差异内容：atomicservice|类名：FetchResult；<br>API声明：getObjectByPosition(index: number, callback: AsyncCallback\<T>): void;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：FetchResult；<br>API声明：getObjectByPosition(index: number): Promise\<T>;<br>差异内容：atomicservice|类名：FetchResult；<br>API声明：getObjectByPosition(index: number): Promise\<T>;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：FetchResult；<br>API声明：getAllObjects(callback: AsyncCallback\<Array\<T>>): void;<br>差异内容：atomicservice|类名：FetchResult；<br>API声明：getAllObjects(callback: AsyncCallback\<Array\<T>>): void;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：FetchResult；<br>API声明：getAllObjects(): Promise\<Array\<T>>;<br>差异内容：atomicservice|类名：FetchResult；<br>API声明：getAllObjects(): Promise\<Array\<T>>;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：FetchResult；<br>API声明：close(): void;<br>差异内容：atomicservice|类名：FetchResult；<br>API声明：close(): void;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：AbsAlbum；<br>API声明：getAssets(options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：atomicservice|类名：AbsAlbum；<br>API声明：getAssets(options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoAccessHelper；<br>API声明：getAssets(options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：atomicservice|类名：PhotoAccessHelper；<br>API声明：getAssets(options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|API从支持元服务到不支持元服务|类名：PhotoAccessHelper；<br>API声明：getBurstAssets(burstKey: string, options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：atomicservice|类名：PhotoAccessHelper；<br>API声明：getBurstAssets(burstKey: string, options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：NA|api/@ohos.file.photoAccessHelper.d.ts|
|删除导出符号|类名：global；<br>API声明：export declare class SingleLineConfig<br>差异内容：export declare class SingleLineConfig|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.file.PhotoPickerComponent.d.ets|
|删除导出符号|类名：global；<br>API声明：export declare enum ItemDisplayRatio<br>差异内容：export declare enum ItemDisplayRatio|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.file.PhotoPickerComponent.d.ets|
