| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace photoAccessHelper<br>差异内容：declare namespace photoAccessHelper|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：function getPhotoAccessHelper(context: Context): PhotoAccessHelper;<br>差异内容：function getPhotoAccessHelper(context: Context): PhotoAccessHelper;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：enum PhotoType<br>差异内容：enum PhotoType|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoType；<br>API声明：IMAGE = 1<br>差异内容：IMAGE = 1|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoType；<br>API声明：VIDEO<br>差异内容：VIDEO|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：enum RecommendationType<br>差异内容：enum RecommendationType|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：RecommendationType；<br>API声明：QR_OR_BAR_CODE = 1<br>差异内容：QR_OR_BAR_CODE = 1|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：RecommendationType；<br>API声明：QR_CODE = 2<br>差异内容：QR_CODE = 2|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：RecommendationType；<br>API声明：BAR_CODE = 3<br>差异内容：BAR_CODE = 3|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：RecommendationType；<br>API声明：ID_CARD = 4<br>差异内容：ID_CARD = 4|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：RecommendationType；<br>API声明：PROFILE_PICTURE = 5<br>差异内容：PROFILE_PICTURE = 5|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：enum DeliveryMode<br>差异内容：enum DeliveryMode|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：DeliveryMode；<br>API声明：FAST_MODE = 0<br>差异内容：FAST_MODE = 0|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：DeliveryMode；<br>API声明：HIGH_QUALITY_MODE = 1<br>差异内容：HIGH_QUALITY_MODE = 1|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：DeliveryMode；<br>API声明：BALANCE_MODE = 2<br>差异内容：BALANCE_MODE = 2|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：interface RequestOptions<br>差异内容：interface RequestOptions|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：RequestOptions；<br>API声明：deliveryMode: DeliveryMode;<br>差异内容：deliveryMode: DeliveryMode;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：interface MediaAssetDataHandler<br>差异内容：interface MediaAssetDataHandler|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetDataHandler；<br>API声明：onDataPrepared(data: T): void;<br>差异内容：onDataPrepared(data: T): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：class MediaAssetManager<br>差异内容：class MediaAssetManager|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetManager；<br>API声明：static requestImage(context: Context, asset: PhotoAsset, requestOptions: RequestOptions, dataHandler: MediaAssetDataHandler\<image.ImageSource>): Promise\<string>;<br>差异内容：static requestImage(context: Context, asset: PhotoAsset, requestOptions: RequestOptions, dataHandler: MediaAssetDataHandler\<image.ImageSource>): Promise\<string>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetManager；<br>API声明：static requestImageData(context: Context, asset: PhotoAsset, requestOptions: RequestOptions, dataHandler: MediaAssetDataHandler\<ArrayBuffer>): Promise\<string>;<br>差异内容：static requestImageData(context: Context, asset: PhotoAsset, requestOptions: RequestOptions, dataHandler: MediaAssetDataHandler\<ArrayBuffer>): Promise\<string>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：type MemberType = number \| string \| boolean;<br>差异内容：type MemberType = number \| string \| boolean;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：interface PhotoAsset<br>差异内容：interface PhotoAsset|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAsset；<br>API声明：readonly uri: string;<br>差异内容：readonly uri: string;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAsset；<br>API声明：readonly photoType: PhotoType;<br>差异内容：readonly photoType: PhotoType;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAsset；<br>API声明：readonly displayName: string;<br>差异内容：readonly displayName: string;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAsset；<br>API声明：get(member: string): MemberType;<br>差异内容：get(member: string): MemberType;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAsset；<br>API声明：set(member: string, value: string): void;<br>差异内容：set(member: string, value: string): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAsset；<br>API声明：commitModify(callback: AsyncCallback\<void>): void;<br>差异内容：commitModify(callback: AsyncCallback\<void>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAsset；<br>API声明：commitModify(): Promise\<void>;<br>差异内容：commitModify(): Promise\<void>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAsset；<br>API声明：getReadOnlyFd(callback: AsyncCallback\<number>): void;<br>差异内容：getReadOnlyFd(callback: AsyncCallback\<number>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAsset；<br>API声明：getReadOnlyFd(): Promise\<number>;<br>差异内容：getReadOnlyFd(): Promise\<number>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAsset；<br>API声明：close(fd: number, callback: AsyncCallback\<void>): void;<br>差异内容：close(fd: number, callback: AsyncCallback\<void>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAsset；<br>API声明：close(fd: number): Promise\<void>;<br>差异内容：close(fd: number): Promise\<void>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAsset；<br>API声明：getThumbnail(callback: AsyncCallback\<image.PixelMap>): void;<br>差异内容：getThumbnail(callback: AsyncCallback\<image.PixelMap>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAsset；<br>API声明：getThumbnail(size: image.Size, callback: AsyncCallback\<image.PixelMap>): void;<br>差异内容：getThumbnail(size: image.Size, callback: AsyncCallback\<image.PixelMap>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAsset；<br>API声明：getThumbnail(size?: image.Size): Promise\<image.PixelMap>;<br>差异内容：getThumbnail(size?: image.Size): Promise\<image.PixelMap>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：enum PhotoKeys<br>差异内容：enum PhotoKeys|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：URI = 'uri'<br>差异内容：URI = 'uri'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：PHOTO_TYPE = 'media_type'<br>差异内容：PHOTO_TYPE = 'media_type'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：DISPLAY_NAME = 'display_name'<br>差异内容：DISPLAY_NAME = 'display_name'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：SIZE = 'size'<br>差异内容：SIZE = 'size'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：DATE_ADDED = 'date_added'<br>差异内容：DATE_ADDED = 'date_added'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：DATE_MODIFIED = 'date_modified'<br>差异内容：DATE_MODIFIED = 'date_modified'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：DURATION = 'duration'<br>差异内容：DURATION = 'duration'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：WIDTH = 'width'<br>差异内容：WIDTH = 'width'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：HEIGHT = 'height'<br>差异内容：HEIGHT = 'height'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：DATE_TAKEN = 'date_taken'<br>差异内容：DATE_TAKEN = 'date_taken'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：ORIENTATION = 'orientation'<br>差异内容：ORIENTATION = 'orientation'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：FAVORITE = 'is_favorite'<br>差异内容：FAVORITE = 'is_favorite'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：TITLE = 'title'<br>差异内容：TITLE = 'title'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：enum AlbumKeys<br>差异内容：enum AlbumKeys|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：AlbumKeys；<br>API声明：URI = 'uri'<br>差异内容：URI = 'uri'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：AlbumKeys；<br>API声明：ALBUM_NAME = 'album_name'<br>差异内容：ALBUM_NAME = 'album_name'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：interface FetchOptions<br>差异内容：interface FetchOptions|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：FetchOptions；<br>API声明：fetchColumns: Array\<string>;<br>差异内容：fetchColumns: Array\<string>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：FetchOptions；<br>API声明：predicates: dataSharePredicates.DataSharePredicates;<br>差异内容：predicates: dataSharePredicates.DataSharePredicates;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：interface CreateOptions<br>差异内容：interface CreateOptions|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：CreateOptions；<br>API声明：title?: string;<br>差异内容：title?: string;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：interface FetchResult<br>差异内容：interface FetchResult|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：FetchResult；<br>API声明：getCount(): number;<br>差异内容：getCount(): number;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：FetchResult；<br>API声明：isAfterLast(): boolean;<br>差异内容：isAfterLast(): boolean;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：FetchResult；<br>API声明：getFirstObject(callback: AsyncCallback\<T>): void;<br>差异内容：getFirstObject(callback: AsyncCallback\<T>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：FetchResult；<br>API声明：getFirstObject(): Promise\<T>;<br>差异内容：getFirstObject(): Promise\<T>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：FetchResult；<br>API声明：getNextObject(callback: AsyncCallback\<T>): void;<br>差异内容：getNextObject(callback: AsyncCallback\<T>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：FetchResult；<br>API声明：getNextObject(): Promise\<T>;<br>差异内容：getNextObject(): Promise\<T>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：FetchResult；<br>API声明：getLastObject(callback: AsyncCallback\<T>): void;<br>差异内容：getLastObject(callback: AsyncCallback\<T>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：FetchResult；<br>API声明：getLastObject(): Promise\<T>;<br>差异内容：getLastObject(): Promise\<T>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：FetchResult；<br>API声明：getObjectByPosition(index: number, callback: AsyncCallback\<T>): void;<br>差异内容：getObjectByPosition(index: number, callback: AsyncCallback\<T>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：FetchResult；<br>API声明：getObjectByPosition(index: number): Promise\<T>;<br>差异内容：getObjectByPosition(index: number): Promise\<T>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：FetchResult；<br>API声明：getAllObjects(callback: AsyncCallback\<Array\<T>>): void;<br>差异内容：getAllObjects(callback: AsyncCallback\<Array\<T>>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：FetchResult；<br>API声明：getAllObjects(): Promise\<Array\<T>>;<br>差异内容：getAllObjects(): Promise\<Array\<T>>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：FetchResult；<br>API声明：close(): void;<br>差异内容：close(): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：enum AlbumType<br>差异内容：enum AlbumType|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：AlbumType；<br>API声明：USER = 0<br>差异内容：USER = 0|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：AlbumType；<br>API声明：SYSTEM = 1024<br>差异内容：SYSTEM = 1024|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：enum AlbumSubtype<br>差异内容：enum AlbumSubtype|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：AlbumSubtype；<br>API声明：USER_GENERIC = 1<br>差异内容：USER_GENERIC = 1|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：AlbumSubtype；<br>API声明：FAVORITE = 1025<br>差异内容：FAVORITE = 1025|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：AlbumSubtype；<br>API声明：VIDEO<br>差异内容：VIDEO|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：AlbumSubtype；<br>API声明：ANY = 2147483647<br>差异内容：ANY = 2147483647|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：interface AbsAlbum<br>差异内容：interface AbsAlbum|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：AbsAlbum；<br>API声明：readonly albumType: AlbumType;<br>差异内容：readonly albumType: AlbumType;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：AbsAlbum；<br>API声明：readonly albumSubtype: AlbumSubtype;<br>差异内容：readonly albumSubtype: AlbumSubtype;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：AbsAlbum；<br>API声明：albumName: string;<br>差异内容：albumName: string;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：AbsAlbum；<br>API声明：readonly albumUri: string;<br>差异内容：readonly albumUri: string;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：AbsAlbum；<br>API声明：readonly count: number;<br>差异内容：readonly count: number;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：AbsAlbum；<br>API声明：readonly coverUri: string;<br>差异内容：readonly coverUri: string;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：AbsAlbum；<br>API声明：getAssets(options: FetchOptions, callback: AsyncCallback\<FetchResult\<PhotoAsset>>): void;<br>差异内容：getAssets(options: FetchOptions, callback: AsyncCallback\<FetchResult\<PhotoAsset>>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：AbsAlbum；<br>API声明：getAssets(options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：getAssets(options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：interface Album<br>差异内容：interface Album|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：Album；<br>API声明：readonly imageCount?: number;<br>差异内容：readonly imageCount?: number;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：Album；<br>API声明：readonly videoCount?: number;<br>差异内容：readonly videoCount?: number;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：Album；<br>API声明：commitModify(callback: AsyncCallback\<void>): void;<br>差异内容：commitModify(callback: AsyncCallback\<void>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：Album；<br>API声明：commitModify(): Promise\<void>;<br>差异内容：commitModify(): Promise\<void>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：Album；<br>API声明：addAssets(assets: Array\<PhotoAsset>, callback: AsyncCallback\<void>): void;<br>差异内容：addAssets(assets: Array\<PhotoAsset>, callback: AsyncCallback\<void>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：Album；<br>API声明：addAssets(assets: Array\<PhotoAsset>): Promise\<void>;<br>差异内容：addAssets(assets: Array\<PhotoAsset>): Promise\<void>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：Album；<br>API声明：removeAssets(assets: Array\<PhotoAsset>, callback: AsyncCallback\<void>): void;<br>差异内容：removeAssets(assets: Array\<PhotoAsset>, callback: AsyncCallback\<void>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：Album；<br>API声明：removeAssets(assets: Array\<PhotoAsset>): Promise\<void>;<br>差异内容：removeAssets(assets: Array\<PhotoAsset>): Promise\<void>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：interface PhotoAccessHelper<br>差异内容：interface PhotoAccessHelper|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：getAssets(options: FetchOptions, callback: AsyncCallback\<FetchResult\<PhotoAsset>>): void;<br>差异内容：getAssets(options: FetchOptions, callback: AsyncCallback\<FetchResult\<PhotoAsset>>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：getAssets(options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：getAssets(options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：createAsset(photoType: PhotoType, extension: string, options: CreateOptions, callback: AsyncCallback\<string>): void;<br>差异内容：createAsset(photoType: PhotoType, extension: string, options: CreateOptions, callback: AsyncCallback\<string>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：createAsset(photoType: PhotoType, extension: string, callback: AsyncCallback\<string>): void;<br>差异内容：createAsset(photoType: PhotoType, extension: string, callback: AsyncCallback\<string>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：createAsset(photoType: PhotoType, extension: string, options?: CreateOptions): Promise\<string>;<br>差异内容：createAsset(photoType: PhotoType, extension: string, options?: CreateOptions): Promise\<string>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：getAlbums(type: AlbumType, subtype: AlbumSubtype, options: FetchOptions, callback: AsyncCallback\<FetchResult\<Album>>): void;<br>差异内容：getAlbums(type: AlbumType, subtype: AlbumSubtype, options: FetchOptions, callback: AsyncCallback\<FetchResult\<Album>>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：getAlbums(type: AlbumType, subtype: AlbumSubtype, callback: AsyncCallback\<FetchResult\<Album>>): void;<br>差异内容：getAlbums(type: AlbumType, subtype: AlbumSubtype, callback: AsyncCallback\<FetchResult\<Album>>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：getAlbums(type: AlbumType, subtype: AlbumSubtype, options?: FetchOptions): Promise\<FetchResult\<Album>>;<br>差异内容：getAlbums(type: AlbumType, subtype: AlbumSubtype, options?: FetchOptions): Promise\<FetchResult\<Album>>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：registerChange(uri: string, forChildUris: boolean, callback: Callback\<ChangeData>): void;<br>差异内容：registerChange(uri: string, forChildUris: boolean, callback: Callback\<ChangeData>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：unRegisterChange(uri: string, callback?: Callback\<ChangeData>): void;<br>差异内容：unRegisterChange(uri: string, callback?: Callback\<ChangeData>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：createDeleteRequest(uriList: Array\<string>, callback: AsyncCallback\<void>): void;<br>差异内容：createDeleteRequest(uriList: Array\<string>, callback: AsyncCallback\<void>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：createDeleteRequest(uriList: Array\<string>): Promise\<void>;<br>差异内容：createDeleteRequest(uriList: Array\<string>): Promise\<void>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：release(callback: AsyncCallback\<void>): void;<br>差异内容：release(callback: AsyncCallback\<void>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：release(): Promise\<void>;<br>差异内容：release(): Promise\<void>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：applyChanges(mediaChangeRequest: MediaChangeRequest): Promise\<void>;<br>差异内容：applyChanges(mediaChangeRequest: MediaChangeRequest): Promise\<void>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：enum NotifyType<br>差异内容：enum NotifyType|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：NotifyType；<br>API声明：NOTIFY_ADD<br>差异内容：NOTIFY_ADD|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：NotifyType；<br>API声明：NOTIFY_UPDATE<br>差异内容：NOTIFY_UPDATE|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：NotifyType；<br>API声明：NOTIFY_REMOVE<br>差异内容：NOTIFY_REMOVE|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：NotifyType；<br>API声明：NOTIFY_ALBUM_ADD_ASSET<br>差异内容：NOTIFY_ALBUM_ADD_ASSET|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：NotifyType；<br>API声明：NOTIFY_ALBUM_REMOVE_ASSET<br>差异内容：NOTIFY_ALBUM_REMOVE_ASSET|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：enum DefaultChangeUri<br>差异内容：enum DefaultChangeUri|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：DefaultChangeUri；<br>API声明：DEFAULT_PHOTO_URI = 'file://media/Photo'<br>差异内容：DEFAULT_PHOTO_URI = 'file://media/Photo'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：DefaultChangeUri；<br>API声明：DEFAULT_ALBUM_URI = 'file://media/PhotoAlbum'<br>差异内容：DEFAULT_ALBUM_URI = 'file://media/PhotoAlbum'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：interface ChangeData<br>差异内容：interface ChangeData|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：ChangeData；<br>API声明：type: NotifyType;<br>差异内容：type: NotifyType;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：ChangeData；<br>API声明：uris: Array\<string>;<br>差异内容：uris: Array\<string>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：ChangeData；<br>API声明：extraUris: Array\<string>;<br>差异内容：extraUris: Array\<string>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：export enum PhotoViewMIMETypes<br>差异内容：export enum PhotoViewMIMETypes|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoViewMIMETypes；<br>API声明：IMAGE_TYPE = 'image/*'<br>差异内容：IMAGE_TYPE = 'image/*'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoViewMIMETypes；<br>API声明：VIDEO_TYPE = 'video/*'<br>差异内容：VIDEO_TYPE = 'video/*'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoViewMIMETypes；<br>API声明：IMAGE_VIDEO_TYPE = '*/*'<br>差异内容：IMAGE_VIDEO_TYPE = '*/*'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：class PhotoSelectOptions<br>差异内容：class PhotoSelectOptions|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoSelectOptions；<br>API声明：MIMEType?: PhotoViewMIMETypes;<br>差异内容：MIMEType?: PhotoViewMIMETypes;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoSelectOptions；<br>API声明：maxSelectNumber?: number;<br>差异内容：maxSelectNumber?: number;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoSelectOptions；<br>API声明：isSearchSupported?: boolean;<br>差异内容：isSearchSupported?: boolean;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoSelectOptions；<br>API声明：isPhotoTakingSupported?: boolean;<br>差异内容：isPhotoTakingSupported?: boolean;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoSelectOptions；<br>API声明：isEditSupported?: boolean;<br>差异内容：isEditSupported?: boolean;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoSelectOptions；<br>API声明：recommendationOptions?: RecommendationOptions;<br>差异内容：recommendationOptions?: RecommendationOptions;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoSelectOptions；<br>API声明：preselectedUris?: Array\<string>;<br>差异内容：preselectedUris?: Array\<string>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：class RecommendationOptions<br>差异内容：class RecommendationOptions|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：RecommendationOptions；<br>API声明：recommendationType?: RecommendationType;<br>差异内容：recommendationType?: RecommendationType;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：class PhotoSelectResult<br>差异内容：class PhotoSelectResult|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoSelectResult；<br>API声明：photoUris: Array\<string>;<br>差异内容：photoUris: Array\<string>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoSelectResult；<br>API声明：isOriginalPhoto: boolean;<br>差异内容：isOriginalPhoto: boolean;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：class PhotoViewPicker<br>差异内容：class PhotoViewPicker|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoViewPicker；<br>API声明：select(option?: PhotoSelectOptions): Promise\<PhotoSelectResult>;<br>差异内容：select(option?: PhotoSelectOptions): Promise\<PhotoSelectResult>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoViewPicker；<br>API声明：select(option: PhotoSelectOptions, callback: AsyncCallback\<PhotoSelectResult>): void;<br>差异内容：select(option: PhotoSelectOptions, callback: AsyncCallback\<PhotoSelectResult>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoViewPicker；<br>API声明：select(callback: AsyncCallback\<PhotoSelectResult>): void;<br>差异内容：select(callback: AsyncCallback\<PhotoSelectResult>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：enum ResourceType<br>差异内容：enum ResourceType|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：ResourceType；<br>API声明：IMAGE_RESOURCE = 1<br>差异内容：IMAGE_RESOURCE = 1|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：ResourceType；<br>API声明：VIDEO_RESOURCE = 2<br>差异内容：VIDEO_RESOURCE = 2|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：interface MediaChangeRequest<br>差异内容：interface MediaChangeRequest|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：class MediaAssetChangeRequest<br>差异内容：class MediaAssetChangeRequest|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetChangeRequest；<br>API声明：static createImageAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest;<br>差异内容：static createImageAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetChangeRequest；<br>API声明：static createVideoAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest;<br>差异内容：static createVideoAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetChangeRequest；<br>API声明：static createAssetRequest(context: Context, photoType: PhotoType, extension: string, options?: CreateOptions): MediaAssetChangeRequest;<br>差异内容：static createAssetRequest(context: Context, photoType: PhotoType, extension: string, options?: CreateOptions): MediaAssetChangeRequest;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetChangeRequest；<br>API声明：static deleteAssets(context: Context, assets: Array\<PhotoAsset>): Promise\<void>;<br>差异内容：static deleteAssets(context: Context, assets: Array\<PhotoAsset>): Promise\<void>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetChangeRequest；<br>API声明：static deleteAssets(context: Context, uriList: Array\<string>): Promise\<void>;<br>差异内容：static deleteAssets(context: Context, uriList: Array\<string>): Promise\<void>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetChangeRequest；<br>API声明：getAsset(): PhotoAsset;<br>差异内容：getAsset(): PhotoAsset;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetChangeRequest；<br>API声明：setTitle(title: string): void;<br>差异内容：setTitle(title: string): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetChangeRequest；<br>API声明：getWriteCacheHandler(): Promise\<number>;<br>差异内容：getWriteCacheHandler(): Promise\<number>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetChangeRequest；<br>API声明：addResource(type: ResourceType, fileUri: string): void;<br>差异内容：addResource(type: ResourceType, fileUri: string): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetChangeRequest；<br>API声明：addResource(type: ResourceType, data: ArrayBuffer): void;<br>差异内容：addResource(type: ResourceType, data: ArrayBuffer): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：class MediaAlbumChangeRequest<br>差异内容：class MediaAlbumChangeRequest|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAlbumChangeRequest；<br>API声明：getAlbum(): Album;<br>差异内容：getAlbum(): Album;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAlbumChangeRequest；<br>API声明：setAlbumName(name: string): void;<br>差异内容：setAlbumName(name: string): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAlbumChangeRequest；<br>API声明：addAssets(assets: Array\<PhotoAsset>): void;<br>差异内容：addAssets(assets: Array\<PhotoAsset>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAlbumChangeRequest；<br>API声明：removeAssets(assets: Array\<PhotoAsset>): void;<br>差异内容：removeAssets(assets: Array\<PhotoAsset>): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace mediaLibrary<br>差异内容：declare namespace mediaLibrary|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：mediaLibrary；<br>API声明：function getMediaLibrary(): MediaLibrary;<br>差异内容：function getMediaLibrary(): MediaLibrary;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：mediaLibrary；<br>API声明：function getMediaLibrary(context: Context): MediaLibrary;<br>差异内容：function getMediaLibrary(context: Context): MediaLibrary;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：mediaLibrary；<br>API声明：enum MediaType<br>差异内容：enum MediaType|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaType；<br>API声明：FILE = 0<br>差异内容：FILE = 0|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaType；<br>API声明：IMAGE<br>差异内容：IMAGE|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaType；<br>API声明：VIDEO<br>差异内容：VIDEO|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaType；<br>API声明：AUDIO<br>差异内容：AUDIO|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：mediaLibrary；<br>API声明：interface MediaAssetOption<br>差异内容：interface MediaAssetOption|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaAssetOption；<br>API声明：src: string;<br>差异内容：src: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaAssetOption；<br>API声明：mimeType: string;<br>差异内容：mimeType: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaAssetOption；<br>API声明：relativePath?: string;<br>差异内容：relativePath?: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：mediaLibrary；<br>API声明：interface MediaSelectOption<br>差异内容：interface MediaSelectOption|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaSelectOption；<br>API声明：type: 'image' \| 'video' \| 'media';<br>差异内容：type: 'image' \| 'video' \| 'media';|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaSelectOption；<br>API声明：count: number;<br>差异内容：count: number;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：mediaLibrary；<br>API声明：interface FileAsset<br>差异内容：interface FileAsset|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：readonly id: number;<br>差异内容：readonly id: number;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：readonly uri: string;<br>差异内容：readonly uri: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：readonly mimeType: string;<br>差异内容：readonly mimeType: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：readonly mediaType: MediaType;<br>差异内容：readonly mediaType: MediaType;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：displayName: string;<br>差异内容：displayName: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：title: string;<br>差异内容：title: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：relativePath: string;<br>差异内容：relativePath: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：readonly parent: number;<br>差异内容：readonly parent: number;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：readonly size: number;<br>差异内容：readonly size: number;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：readonly dateAdded: number;<br>差异内容：readonly dateAdded: number;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：readonly dateModified: number;<br>差异内容：readonly dateModified: number;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：readonly dateTaken: number;<br>差异内容：readonly dateTaken: number;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：readonly artist: string;<br>差异内容：readonly artist: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：readonly audioAlbum: string;<br>差异内容：readonly audioAlbum: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：readonly width: number;<br>差异内容：readonly width: number;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：readonly height: number;<br>差异内容：readonly height: number;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：orientation: number;<br>差异内容：orientation: number;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：readonly duration: number;<br>差异内容：readonly duration: number;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：readonly albumId: number;<br>差异内容：readonly albumId: number;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：readonly albumUri: string;<br>差异内容：readonly albumUri: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：readonly albumName: string;<br>差异内容：readonly albumName: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：isDirectory(callback: AsyncCallback\<boolean>): void;<br>差异内容：isDirectory(callback: AsyncCallback\<boolean>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：isDirectory(): Promise\<boolean>;<br>差异内容：isDirectory(): Promise\<boolean>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：commitModify(callback: AsyncCallback\<void>): void;<br>差异内容：commitModify(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：commitModify(): Promise\<void>;<br>差异内容：commitModify(): Promise\<void>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：open(mode: string, callback: AsyncCallback\<number>): void;<br>差异内容：open(mode: string, callback: AsyncCallback\<number>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：open(mode: string): Promise\<number>;<br>差异内容：open(mode: string): Promise\<number>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：close(fd: number, callback: AsyncCallback\<void>): void;<br>差异内容：close(fd: number, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：close(fd: number): Promise\<void>;<br>差异内容：close(fd: number): Promise\<void>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：getThumbnail(callback: AsyncCallback\<image.PixelMap>): void;<br>差异内容：getThumbnail(callback: AsyncCallback\<image.PixelMap>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：getThumbnail(size: Size, callback: AsyncCallback\<image.PixelMap>): void;<br>差异内容：getThumbnail(size: Size, callback: AsyncCallback\<image.PixelMap>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：getThumbnail(size?: Size): Promise\<image.PixelMap>;<br>差异内容：getThumbnail(size?: Size): Promise\<image.PixelMap>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：favorite(isFavorite: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：favorite(isFavorite: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：favorite(isFavorite: boolean): Promise\<void>;<br>差异内容：favorite(isFavorite: boolean): Promise\<void>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：isFavorite(callback: AsyncCallback\<boolean>): void;<br>差异内容：isFavorite(callback: AsyncCallback\<boolean>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：isFavorite(): Promise\<boolean>;<br>差异内容：isFavorite(): Promise\<boolean>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：trash(isTrash: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：trash(isTrash: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：trash(isTrash: boolean): Promise\<void>;<br>差异内容：trash(isTrash: boolean): Promise\<void>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：isTrash(callback: AsyncCallback\<boolean>): void;<br>差异内容：isTrash(callback: AsyncCallback\<boolean>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileAsset；<br>API声明：isTrash(): Promise\<boolean>;<br>差异内容：isTrash(): Promise\<boolean>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：mediaLibrary；<br>API声明：enum FileKey<br>差异内容：enum FileKey|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：ID = "file_id"<br>差异内容：ID = "file_id"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：RELATIVE_PATH = "relative_path"<br>差异内容：RELATIVE_PATH = "relative_path"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：DISPLAY_NAME = "display_name"<br>差异内容：DISPLAY_NAME = "display_name"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：PARENT = "parent"<br>差异内容：PARENT = "parent"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：MIME_TYPE = "mime_type"<br>差异内容：MIME_TYPE = "mime_type"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：MEDIA_TYPE = "media_type"<br>差异内容：MEDIA_TYPE = "media_type"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：SIZE = "size"<br>差异内容：SIZE = "size"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：DATE_ADDED = "date_added"<br>差异内容：DATE_ADDED = "date_added"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：DATE_MODIFIED = "date_modified"<br>差异内容：DATE_MODIFIED = "date_modified"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：DATE_TAKEN = "date_taken"<br>差异内容：DATE_TAKEN = "date_taken"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：TITLE = "title"<br>差异内容：TITLE = "title"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：ARTIST = "artist"<br>差异内容：ARTIST = "artist"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：AUDIOALBUM = "audio_album"<br>差异内容：AUDIOALBUM = "audio_album"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：DURATION = "duration"<br>差异内容：DURATION = "duration"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：WIDTH = "width"<br>差异内容：WIDTH = "width"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：HEIGHT = "height"<br>差异内容：HEIGHT = "height"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：ORIENTATION = "orientation"<br>差异内容：ORIENTATION = "orientation"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：ALBUM_ID = "bucket_id"<br>差异内容：ALBUM_ID = "bucket_id"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FileKey；<br>API声明：ALBUM_NAME = "bucket_display_name"<br>差异内容：ALBUM_NAME = "bucket_display_name"|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：mediaLibrary；<br>API声明：interface MediaFetchOptions<br>差异内容：interface MediaFetchOptions|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaFetchOptions；<br>API声明：selections: string;<br>差异内容：selections: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaFetchOptions；<br>API声明：selectionArgs: Array\<string>;<br>差异内容：selectionArgs: Array\<string>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaFetchOptions；<br>API声明：order?: string;<br>差异内容：order?: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaFetchOptions；<br>API声明：uri?: string;<br>差异内容：uri?: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaFetchOptions；<br>API声明：networkId?: string;<br>差异内容：networkId?: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaFetchOptions；<br>API声明：extendArgs?: string;<br>差异内容：extendArgs?: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：mediaLibrary；<br>API声明：interface FetchFileResult<br>差异内容：interface FetchFileResult|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FetchFileResult；<br>API声明：getCount(): number;<br>差异内容：getCount(): number;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FetchFileResult；<br>API声明：isAfterLast(): boolean;<br>差异内容：isAfterLast(): boolean;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FetchFileResult；<br>API声明：close(): void;<br>差异内容：close(): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FetchFileResult；<br>API声明：getFirstObject(callback: AsyncCallback\<FileAsset>): void;<br>差异内容：getFirstObject(callback: AsyncCallback\<FileAsset>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FetchFileResult；<br>API声明：getFirstObject(): Promise\<FileAsset>;<br>差异内容：getFirstObject(): Promise\<FileAsset>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FetchFileResult；<br>API声明：getNextObject(callback: AsyncCallback\<FileAsset>): void;<br>差异内容：getNextObject(callback: AsyncCallback\<FileAsset>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FetchFileResult；<br>API声明：getNextObject(): Promise\<FileAsset>;<br>差异内容：getNextObject(): Promise\<FileAsset>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FetchFileResult；<br>API声明：getLastObject(callback: AsyncCallback\<FileAsset>): void;<br>差异内容：getLastObject(callback: AsyncCallback\<FileAsset>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FetchFileResult；<br>API声明：getLastObject(): Promise\<FileAsset>;<br>差异内容：getLastObject(): Promise\<FileAsset>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FetchFileResult；<br>API声明：getPositionObject(index: number, callback: AsyncCallback\<FileAsset>): void;<br>差异内容：getPositionObject(index: number, callback: AsyncCallback\<FileAsset>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FetchFileResult；<br>API声明：getPositionObject(index: number): Promise\<FileAsset>;<br>差异内容：getPositionObject(index: number): Promise\<FileAsset>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FetchFileResult；<br>API声明：getAllObject(callback: AsyncCallback\<Array\<FileAsset>>): void;<br>差异内容：getAllObject(callback: AsyncCallback\<Array\<FileAsset>>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：FetchFileResult；<br>API声明：getAllObject(): Promise\<Array\<FileAsset>>;<br>差异内容：getAllObject(): Promise\<Array\<FileAsset>>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：mediaLibrary；<br>API声明：interface Album<br>差异内容：interface Album|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：Album；<br>API声明：readonly albumId: number;<br>差异内容：readonly albumId: number;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：Album；<br>API声明：albumName: string;<br>差异内容：albumName: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：Album；<br>API声明：readonly albumUri: string;<br>差异内容：readonly albumUri: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：Album；<br>API声明：readonly dateModified: number;<br>差异内容：readonly dateModified: number;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：Album；<br>API声明：readonly count: number;<br>差异内容：readonly count: number;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：Album；<br>API声明：readonly relativePath: string;<br>差异内容：readonly relativePath: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：Album；<br>API声明：readonly coverUri: string;<br>差异内容：readonly coverUri: string;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：Album；<br>API声明：commitModify(callback: AsyncCallback\<void>): void;<br>差异内容：commitModify(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：Album；<br>API声明：commitModify(): Promise\<void>;<br>差异内容：commitModify(): Promise\<void>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：Album；<br>API声明：getFileAssets(callback: AsyncCallback\<FetchFileResult>): void;<br>差异内容：getFileAssets(callback: AsyncCallback\<FetchFileResult>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：Album；<br>API声明：getFileAssets(options: MediaFetchOptions, callback: AsyncCallback\<FetchFileResult>): void;<br>差异内容：getFileAssets(options: MediaFetchOptions, callback: AsyncCallback\<FetchFileResult>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：Album；<br>API声明：getFileAssets(options?: MediaFetchOptions): Promise\<FetchFileResult>;<br>差异内容：getFileAssets(options?: MediaFetchOptions): Promise\<FetchFileResult>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：mediaLibrary；<br>API声明：enum DirectoryType<br>差异内容：enum DirectoryType|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：DirectoryType；<br>API声明：DIR_CAMERA = 0<br>差异内容：DIR_CAMERA = 0|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：DirectoryType；<br>API声明：DIR_VIDEO<br>差异内容：DIR_VIDEO|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：DirectoryType；<br>API声明：DIR_IMAGE<br>差异内容：DIR_IMAGE|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：DirectoryType；<br>API声明：DIR_AUDIO<br>差异内容：DIR_AUDIO|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：DirectoryType；<br>API声明：DIR_DOCUMENTS<br>差异内容：DIR_DOCUMENTS|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：DirectoryType；<br>API声明：DIR_DOWNLOAD<br>差异内容：DIR_DOWNLOAD|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：mediaLibrary；<br>API声明：interface MediaLibrary<br>差异内容：interface MediaLibrary|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：getPublicDirectory(type: DirectoryType, callback: AsyncCallback\<string>): void;<br>差异内容：getPublicDirectory(type: DirectoryType, callback: AsyncCallback\<string>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：getPublicDirectory(type: DirectoryType): Promise\<string>;<br>差异内容：getPublicDirectory(type: DirectoryType): Promise\<string>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：getFileAssets(options: MediaFetchOptions, callback: AsyncCallback\<FetchFileResult>): void;<br>差异内容：getFileAssets(options: MediaFetchOptions, callback: AsyncCallback\<FetchFileResult>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：getFileAssets(options: MediaFetchOptions): Promise\<FetchFileResult>;<br>差异内容：getFileAssets(options: MediaFetchOptions): Promise\<FetchFileResult>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;<br>差异内容：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;<br>差异内容：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;<br>差异内容：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;<br>差异内容：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;<br>差异内容：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;<br>差异内容：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;<br>差异内容：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;<br>差异内容：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;<br>差异内容：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;<br>差异内容：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;<br>差异内容：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;<br>差异内容：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;<br>差异内容：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;<br>差异内容：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：createAsset(mediaType: MediaType, displayName: string, relativePath: string, callback: AsyncCallback\<FileAsset>): void;<br>差异内容：createAsset(mediaType: MediaType, displayName: string, relativePath: string, callback: AsyncCallback\<FileAsset>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：createAsset(mediaType: MediaType, displayName: string, relativePath: string): Promise\<FileAsset>;<br>差异内容：createAsset(mediaType: MediaType, displayName: string, relativePath: string): Promise\<FileAsset>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：getAlbums(options: MediaFetchOptions, callback: AsyncCallback\<Array\<Album>>): void;<br>差异内容：getAlbums(options: MediaFetchOptions, callback: AsyncCallback\<Array\<Album>>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：getAlbums(options: MediaFetchOptions): Promise\<Array\<Album>>;<br>差异内容：getAlbums(options: MediaFetchOptions): Promise\<Array\<Album>>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：storeMediaAsset(option: MediaAssetOption, callback: AsyncCallback\<string>): void;<br>差异内容：storeMediaAsset(option: MediaAssetOption, callback: AsyncCallback\<string>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：storeMediaAsset(option: MediaAssetOption): Promise\<string>;<br>差异内容：storeMediaAsset(option: MediaAssetOption): Promise\<string>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：startImagePreview(images: Array\<string>, index: number, callback: AsyncCallback\<void>): void;<br>差异内容：startImagePreview(images: Array\<string>, index: number, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：startImagePreview(images: Array\<string>, callback: AsyncCallback\<void>): void;<br>差异内容：startImagePreview(images: Array\<string>, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：startImagePreview(images: Array\<string>, index?: number): Promise\<void>;<br>差异内容：startImagePreview(images: Array\<string>, index?: number): Promise\<void>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：startMediaSelect(option: MediaSelectOption, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：startMediaSelect(option: MediaSelectOption, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：startMediaSelect(option: MediaSelectOption): Promise\<Array\<string>>;<br>差异内容：startMediaSelect(option: MediaSelectOption): Promise\<Array\<string>>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：release(callback: AsyncCallback\<void>): void;<br>差异内容：release(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：MediaLibrary；<br>API声明：release(): Promise\<void>;<br>差异内容：release(): Promise\<void>;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：mediaLibrary；<br>API声明：interface Size<br>差异内容：interface Size|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：Size；<br>API声明：width: number;<br>差异内容：width: number;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增API|NA|类名：Size；<br>API声明：height: number;<br>差异内容：height: number;|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.file.photoAccessHelper.d.ts<br>差异内容：MediaLibraryKit|api/@ohos.file.photoAccessHelper.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.multimedia.mediaLibrary.d.ts<br>差异内容：MediaLibraryKit|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.MediaLibraryKit.d.ts<br>差异内容：MediaLibraryKit|kits/@kit.MediaLibraryKit.d.ts|
