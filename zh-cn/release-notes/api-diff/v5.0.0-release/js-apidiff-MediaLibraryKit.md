| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API跨平台权限变更|类名：global；<br>API声明：declare namespace photoAccessHelper<br>差异内容：NA|类名：global；<br>API声明：declare namespace photoAccessHelper<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：photoAccessHelper；<br>API声明：function getPhotoAccessHelper(context: Context): PhotoAccessHelper;<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：function getPhotoAccessHelper(context: Context): PhotoAccessHelper;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：photoAccessHelper；<br>API声明：enum PhotoType<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：enum PhotoType<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoType；<br>API声明：IMAGE = 1<br>差异内容：NA|类名：PhotoType；<br>API声明：IMAGE = 1<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoType；<br>API声明：VIDEO<br>差异内容：NA|类名：PhotoType；<br>API声明：VIDEO<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：photoAccessHelper；<br>API声明：type MemberType = number \| string \| boolean;<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：type MemberType = number \| string \| boolean;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：photoAccessHelper；<br>API声明：interface PhotoAsset<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：interface PhotoAsset<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoAsset；<br>API声明：readonly uri: string;<br>差异内容：NA|类名：PhotoAsset；<br>API声明：readonly uri: string;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoAsset；<br>API声明：readonly photoType: PhotoType;<br>差异内容：NA|类名：PhotoAsset；<br>API声明：readonly photoType: PhotoType;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoAsset；<br>API声明：readonly displayName: string;<br>差异内容：NA|类名：PhotoAsset；<br>API声明：readonly displayName: string;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoAsset；<br>API声明：get(member: string): MemberType;<br>差异内容：NA|类名：PhotoAsset；<br>API声明：get(member: string): MemberType;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：photoAccessHelper；<br>API声明：enum PhotoKeys<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：enum PhotoKeys<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoKeys；<br>API声明：URI = 'uri'<br>差异内容：NA|类名：PhotoKeys；<br>API声明：URI = 'uri'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoKeys；<br>API声明：PHOTO_TYPE = 'media_type'<br>差异内容：NA|类名：PhotoKeys；<br>API声明：PHOTO_TYPE = 'media_type'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoKeys；<br>API声明：DISPLAY_NAME = 'display_name'<br>差异内容：NA|类名：PhotoKeys；<br>API声明：DISPLAY_NAME = 'display_name'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoKeys；<br>API声明：SIZE = 'size'<br>差异内容：NA|类名：PhotoKeys；<br>API声明：SIZE = 'size'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoKeys；<br>API声明：DATE_ADDED = 'date_added'<br>差异内容：NA|类名：PhotoKeys；<br>API声明：DATE_ADDED = 'date_added'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoKeys；<br>API声明：DATE_MODIFIED = 'date_modified'<br>差异内容：NA|类名：PhotoKeys；<br>API声明：DATE_MODIFIED = 'date_modified'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoKeys；<br>API声明：DURATION = 'duration'<br>差异内容：NA|类名：PhotoKeys；<br>API声明：DURATION = 'duration'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoKeys；<br>API声明：WIDTH = 'width'<br>差异内容：NA|类名：PhotoKeys；<br>API声明：WIDTH = 'width'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoKeys；<br>API声明：HEIGHT = 'height'<br>差异内容：NA|类名：PhotoKeys；<br>API声明：HEIGHT = 'height'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoKeys；<br>API声明：DATE_TAKEN = 'date_taken'<br>差异内容：NA|类名：PhotoKeys；<br>API声明：DATE_TAKEN = 'date_taken'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoKeys；<br>API声明：ORIENTATION = 'orientation'<br>差异内容：NA|类名：PhotoKeys；<br>API声明：ORIENTATION = 'orientation'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoKeys；<br>API声明：FAVORITE = 'is_favorite'<br>差异内容：NA|类名：PhotoKeys；<br>API声明：FAVORITE = 'is_favorite'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoKeys；<br>API声明：TITLE = 'title'<br>差异内容：NA|类名：PhotoKeys；<br>API声明：TITLE = 'title'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：photoAccessHelper；<br>API声明：enum AlbumKeys<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：enum AlbumKeys<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：AlbumKeys；<br>API声明：URI = 'uri'<br>差异内容：NA|类名：AlbumKeys；<br>API声明：URI = 'uri'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：AlbumKeys；<br>API声明：ALBUM_NAME = 'album_name'<br>差异内容：NA|类名：AlbumKeys；<br>API声明：ALBUM_NAME = 'album_name'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：photoAccessHelper；<br>API声明：interface FetchOptions<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：interface FetchOptions<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：FetchOptions；<br>API声明：fetchColumns: Array\<string>;<br>差异内容：NA|类名：FetchOptions；<br>API声明：fetchColumns: Array\<string>;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：FetchOptions；<br>API声明：predicates: dataSharePredicates.DataSharePredicates;<br>差异内容：NA|类名：FetchOptions；<br>API声明：predicates: dataSharePredicates.DataSharePredicates;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：photoAccessHelper；<br>API声明：interface FetchResult<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：interface FetchResult<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：FetchResult；<br>API声明：getCount(): number;<br>差异内容：NA|类名：FetchResult；<br>API声明：getCount(): number;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：FetchResult；<br>API声明：isAfterLast(): boolean;<br>差异内容：NA|类名：FetchResult；<br>API声明：isAfterLast(): boolean;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：FetchResult；<br>API声明：getFirstObject(callback: AsyncCallback\<T>): void;<br>差异内容：NA|类名：FetchResult；<br>API声明：getFirstObject(callback: AsyncCallback\<T>): void;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：FetchResult；<br>API声明：getFirstObject(): Promise\<T>;<br>差异内容：NA|类名：FetchResult；<br>API声明：getFirstObject(): Promise\<T>;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：FetchResult；<br>API声明：getNextObject(callback: AsyncCallback\<T>): void;<br>差异内容：NA|类名：FetchResult；<br>API声明：getNextObject(callback: AsyncCallback\<T>): void;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：FetchResult；<br>API声明：getNextObject(): Promise\<T>;<br>差异内容：NA|类名：FetchResult；<br>API声明：getNextObject(): Promise\<T>;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：FetchResult；<br>API声明：getLastObject(callback: AsyncCallback\<T>): void;<br>差异内容：NA|类名：FetchResult；<br>API声明：getLastObject(callback: AsyncCallback\<T>): void;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：FetchResult；<br>API声明：getLastObject(): Promise\<T>;<br>差异内容：NA|类名：FetchResult；<br>API声明：getLastObject(): Promise\<T>;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：FetchResult；<br>API声明：getObjectByPosition(index: number, callback: AsyncCallback\<T>): void;<br>差异内容：NA|类名：FetchResult；<br>API声明：getObjectByPosition(index: number, callback: AsyncCallback\<T>): void;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：FetchResult；<br>API声明：getObjectByPosition(index: number): Promise\<T>;<br>差异内容：NA|类名：FetchResult；<br>API声明：getObjectByPosition(index: number): Promise\<T>;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：FetchResult；<br>API声明：getAllObjects(callback: AsyncCallback\<Array\<T>>): void;<br>差异内容：NA|类名：FetchResult；<br>API声明：getAllObjects(callback: AsyncCallback\<Array\<T>>): void;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：FetchResult；<br>API声明：getAllObjects(): Promise\<Array\<T>>;<br>差异内容：NA|类名：FetchResult；<br>API声明：getAllObjects(): Promise\<Array\<T>>;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：FetchResult；<br>API声明：close(): void;<br>差异内容：NA|类名：FetchResult；<br>API声明：close(): void;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：photoAccessHelper；<br>API声明：enum AlbumType<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：enum AlbumType<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：AlbumType；<br>API声明：USER = 0<br>差异内容：NA|类名：AlbumType；<br>API声明：USER = 0<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：AlbumType；<br>API声明：SYSTEM = 1024<br>差异内容：NA|类名：AlbumType；<br>API声明：SYSTEM = 1024<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：photoAccessHelper；<br>API声明：enum AlbumSubtype<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：enum AlbumSubtype<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：AlbumSubtype；<br>API声明：USER_GENERIC = 1<br>差异内容：NA|类名：AlbumSubtype；<br>API声明：USER_GENERIC = 1<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：AlbumSubtype；<br>API声明：FAVORITE = 1025<br>差异内容：NA|类名：AlbumSubtype；<br>API声明：FAVORITE = 1025<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：AlbumSubtype；<br>API声明：VIDEO<br>差异内容：NA|类名：AlbumSubtype；<br>API声明：VIDEO<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：AlbumSubtype；<br>API声明：ANY = 2147483647<br>差异内容：NA|类名：AlbumSubtype；<br>API声明：ANY = 2147483647<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：photoAccessHelper；<br>API声明：interface AbsAlbum<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：interface AbsAlbum<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：AbsAlbum；<br>API声明：readonly albumType: AlbumType;<br>差异内容：NA|类名：AbsAlbum；<br>API声明：readonly albumType: AlbumType;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：AbsAlbum；<br>API声明：readonly albumSubtype: AlbumSubtype;<br>差异内容：NA|类名：AbsAlbum；<br>API声明：readonly albumSubtype: AlbumSubtype;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：AbsAlbum；<br>API声明：albumName: string;<br>差异内容：NA|类名：AbsAlbum；<br>API声明：albumName: string;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：AbsAlbum；<br>API声明：readonly albumUri: string;<br>差异内容：NA|类名：AbsAlbum；<br>API声明：readonly albumUri: string;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：AbsAlbum；<br>API声明：readonly count: number;<br>差异内容：NA|类名：AbsAlbum；<br>API声明：readonly count: number;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：AbsAlbum；<br>API声明：getAssets(options: FetchOptions, callback: AsyncCallback\<FetchResult\<PhotoAsset>>): void;<br>差异内容：NA|类名：AbsAlbum；<br>API声明：getAssets(options: FetchOptions, callback: AsyncCallback\<FetchResult\<PhotoAsset>>): void;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：AbsAlbum；<br>API声明：getAssets(options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：NA|类名：AbsAlbum；<br>API声明：getAssets(options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：photoAccessHelper；<br>API声明：interface Album<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：interface Album<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：Album；<br>API声明：readonly imageCount?: number;<br>差异内容：NA|类名：Album；<br>API声明：readonly imageCount?: number;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：Album；<br>API声明：readonly videoCount?: number;<br>差异内容：NA|类名：Album；<br>API声明：readonly videoCount?: number;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：photoAccessHelper；<br>API声明：interface PhotoAccessHelper<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：interface PhotoAccessHelper<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoAccessHelper；<br>API声明：getAssets(options: FetchOptions, callback: AsyncCallback\<FetchResult\<PhotoAsset>>): void;<br>差异内容：NA|类名：PhotoAccessHelper；<br>API声明：getAssets(options: FetchOptions, callback: AsyncCallback\<FetchResult\<PhotoAsset>>): void;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoAccessHelper；<br>API声明：getAssets(options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：NA|类名：PhotoAccessHelper；<br>API声明：getAssets(options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoAccessHelper；<br>API声明：getAlbums(type: AlbumType, subtype: AlbumSubtype, options: FetchOptions, callback: AsyncCallback\<FetchResult\<Album>>): void;<br>差异内容：NA|类名：PhotoAccessHelper；<br>API声明：getAlbums(type: AlbumType, subtype: AlbumSubtype, options: FetchOptions, callback: AsyncCallback\<FetchResult\<Album>>): void;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoAccessHelper；<br>API声明：getAlbums(type: AlbumType, subtype: AlbumSubtype, callback: AsyncCallback\<FetchResult\<Album>>): void;<br>差异内容：NA|类名：PhotoAccessHelper；<br>API声明：getAlbums(type: AlbumType, subtype: AlbumSubtype, callback: AsyncCallback\<FetchResult\<Album>>): void;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoAccessHelper；<br>API声明：getAlbums(type: AlbumType, subtype: AlbumSubtype, options?: FetchOptions): Promise\<FetchResult\<Album>>;<br>差异内容：NA|类名：PhotoAccessHelper；<br>API声明：getAlbums(type: AlbumType, subtype: AlbumSubtype, options?: FetchOptions): Promise\<FetchResult\<Album>>;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：photoAccessHelper；<br>API声明：export enum PhotoViewMIMETypes<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：export enum PhotoViewMIMETypes<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoViewMIMETypes；<br>API声明：IMAGE_TYPE = 'image/*'<br>差异内容：NA|类名：PhotoViewMIMETypes；<br>API声明：IMAGE_TYPE = 'image/*'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoViewMIMETypes；<br>API声明：VIDEO_TYPE = 'video/*'<br>差异内容：NA|类名：PhotoViewMIMETypes；<br>API声明：VIDEO_TYPE = 'video/*'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoViewMIMETypes；<br>API声明：IMAGE_VIDEO_TYPE = '*/*'<br>差异内容：NA|类名：PhotoViewMIMETypes；<br>API声明：IMAGE_VIDEO_TYPE = '*/*'<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：photoAccessHelper；<br>API声明：class PhotoSelectOptions<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：class PhotoSelectOptions<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：photoAccessHelper；<br>API声明：class PhotoSelectResult<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：class PhotoSelectResult<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoSelectResult；<br>API声明：photoUris: Array\<string>;<br>差异内容：NA|类名：PhotoSelectResult；<br>API声明：photoUris: Array\<string>;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoSelectResult；<br>API声明：isOriginalPhoto: boolean;<br>差异内容：NA|类名：PhotoSelectResult；<br>API声明：isOriginalPhoto: boolean;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：photoAccessHelper；<br>API声明：class PhotoViewPicker<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：class PhotoViewPicker<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoViewPicker；<br>API声明：select(option?: PhotoSelectOptions): Promise\<PhotoSelectResult>;<br>差异内容：NA|类名：PhotoViewPicker；<br>API声明：select(option?: PhotoSelectOptions): Promise\<PhotoSelectResult>;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoViewPicker；<br>API声明：select(option: PhotoSelectOptions, callback: AsyncCallback\<PhotoSelectResult>): void;<br>差异内容：NA|类名：PhotoViewPicker；<br>API声明：select(option: PhotoSelectOptions, callback: AsyncCallback\<PhotoSelectResult>): void;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|API跨平台权限变更|类名：PhotoViewPicker；<br>API声明：select(callback: AsyncCallback\<PhotoSelectResult>): void;<br>差异内容：NA|类名：PhotoViewPicker；<br>API声明：select(callback: AsyncCallback\<PhotoSelectResult>): void;<br>差异内容：crossplatform|api/@ohos.file.photoAccessHelper.d.ts|
|函数变更|类名：MediaAssetDataHandler；<br>API声明：onDataPrepared(data: T): void;<br>差异内容：NA|类名：MediaAssetDataHandler；<br>API声明：onDataPrepared(data: T, map?: Map\<string, string>): void;<br>差异内容：map?: Map\<string, string>|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare struct AlbumPickerComponent<br>差异内容：export declare struct AlbumPickerComponent|api/@ohos.file.AlbumPickerComponent.d.ets|
|新增API|NA|类名：AlbumPickerComponent；<br>API声明：albumPickerOptions?: AlbumPickerOptions;<br>差异内容：albumPickerOptions?: AlbumPickerOptions;|api/@ohos.file.AlbumPickerComponent.d.ets|
|新增API|NA|类名：AlbumPickerComponent；<br>API声明：onAlbumClick?: (albumInfo: AlbumInfo) => boolean;<br>差异内容：onAlbumClick?: (albumInfo: AlbumInfo) => boolean;|api/@ohos.file.AlbumPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare class AlbumPickerOptions<br>差异内容：export declare class AlbumPickerOptions|api/@ohos.file.AlbumPickerComponent.d.ets|
|新增API|NA|类名：AlbumPickerOptions；<br>API声明：themeColorMode?: PickerColorMode;<br>差异内容：themeColorMode?: PickerColorMode;|api/@ohos.file.AlbumPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare class AlbumInfo<br>差异内容：export declare class AlbumInfo|api/@ohos.file.AlbumPickerComponent.d.ets|
|新增API|NA|类名：AlbumInfo；<br>API声明：uri?: string;<br>差异内容：uri?: string;|api/@ohos.file.AlbumPickerComponent.d.ets|
|新增API|NA|类名：AlbumInfo；<br>API声明：albumName?: string;<br>差异内容：albumName?: string;|api/@ohos.file.AlbumPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare struct PhotoPickerComponent<br>差异内容：export declare struct PhotoPickerComponent|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PhotoPickerComponent；<br>API声明：pickerOptions?: PickerOptions;<br>差异内容：pickerOptions?: PickerOptions;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PhotoPickerComponent；<br>API声明：onSelect?: (uri: string) => void;<br>差异内容：onSelect?: (uri: string) => void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PhotoPickerComponent；<br>API声明：onDeselect?: (uri: string) => void;<br>差异内容：onDeselect?: (uri: string) => void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PhotoPickerComponent；<br>API声明：onItemClicked?: (itemInfo: ItemInfo, clickType: ClickType) => boolean;<br>差异内容：onItemClicked?: (itemInfo: ItemInfo, clickType: ClickType) => boolean;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PhotoPickerComponent；<br>API声明：onEnterPhotoBrowser?: (photoBrowserInfo: PhotoBrowserInfo) => boolean;<br>差异内容：onEnterPhotoBrowser?: (photoBrowserInfo: PhotoBrowserInfo) => boolean;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PhotoPickerComponent；<br>API声明：onExitPhotoBrowser?: (photoBrowserInfo: PhotoBrowserInfo) => boolean;<br>差异内容：onExitPhotoBrowser?: (photoBrowserInfo: PhotoBrowserInfo) => boolean;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PhotoPickerComponent；<br>API声明：onPickerControllerReady?: () => void;<br>差异内容：onPickerControllerReady?: () => void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PhotoPickerComponent；<br>API声明：onPhotoBrowserChanged?: (browserItemInfo: BaseItemInfo) => boolean;<br>差异内容：onPhotoBrowserChanged?: (browserItemInfo: BaseItemInfo) => boolean;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PhotoPickerComponent；<br>API声明：@ObjectLink<br>    pickerController: PickerController;<br>差异内容：@ObjectLink<br>    pickerController: PickerController;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PhotoPickerComponent；<br>API声明：build(): void;<br>差异内容：build(): void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare class PickerController<br>差异内容：export declare class PickerController|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerController；<br>API声明：setData(dataType: DataType, data: Object): void;<br>差异内容：setData(dataType: DataType, data: Object): void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerController；<br>API声明：setMaxSelected(maxSelected: MaxSelected): void;<br>差异内容：setMaxSelected(maxSelected: MaxSelected): void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerController；<br>API声明：setPhotoBrowserItem(uri: string, photoBrowserRange?: PhotoBrowserRange): void;<br>差异内容：setPhotoBrowserItem(uri: string, photoBrowserRange?: PhotoBrowserRange): void;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare class PickerOptions<br>差异内容：export declare class PickerOptions|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerOptions；<br>API声明：checkBoxColor?: string;<br>差异内容：checkBoxColor?: string;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerOptions；<br>API声明：backgroundColor?: string;<br>差异内容：backgroundColor?: string;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerOptions；<br>API声明：isRepeatSelectSupported?: boolean;<br>差异内容：isRepeatSelectSupported?: boolean;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerOptions；<br>API声明：checkboxTextColor?: string;<br>差异内容：checkboxTextColor?: string;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerOptions；<br>API声明：photoBrowserBackgroundColorMode?: PickerColorMode;<br>差异内容：photoBrowserBackgroundColorMode?: PickerColorMode;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerOptions；<br>API声明：maxSelectedReminderMode?: ReminderMode;<br>差异内容：maxSelectedReminderMode?: ReminderMode;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerOptions；<br>API声明：orientation?: PickerOrientation;<br>差异内容：orientation?: PickerOrientation;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerOptions；<br>API声明：selectMode?: SelectMode;<br>差异内容：selectMode?: SelectMode;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerOptions；<br>API声明：maxPhotoSelectNumber?: number;<br>差异内容：maxPhotoSelectNumber?: number;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerOptions；<br>API声明：maxVideoSelectNumber?: number;<br>差异内容：maxVideoSelectNumber?: number;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare class BaseItemInfo<br>差异内容：export declare class BaseItemInfo|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：BaseItemInfo；<br>API声明：uri?: string;<br>差异内容：uri?: string;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：BaseItemInfo；<br>API声明：mimeType?: string;<br>差异内容：mimeType?: string;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：BaseItemInfo；<br>API声明：width?: number;<br>差异内容：width?: number;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：BaseItemInfo；<br>API声明：height?: number;<br>差异内容：height?: number;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：BaseItemInfo；<br>API声明：size?: number;<br>差异内容：size?: number;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：BaseItemInfo；<br>API声明：duration?: number;<br>差异内容：duration?: number;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare class ItemInfo<br>差异内容：export declare class ItemInfo|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：ItemInfo；<br>API声明：itemType?: ItemType;<br>差异内容：itemType?: ItemType;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare class PhotoBrowserInfo<br>差异内容：export declare class PhotoBrowserInfo|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PhotoBrowserInfo；<br>API声明：animatorParams?: AnimatorParams;<br>差异内容：animatorParams?: AnimatorParams;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare class AnimatorParams<br>差异内容：export declare class AnimatorParams|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：AnimatorParams；<br>API声明：duration?: number;<br>差异内容：duration?: number;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：AnimatorParams；<br>API声明：curve?: Curve \| ICurve \| string;<br>差异内容：curve?: Curve \| ICurve \| string;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare class MaxSelected<br>差异内容：export declare class MaxSelected|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：MaxSelected；<br>API声明：data?: Map\<MaxCountType, number>;<br>差异内容：data?: Map\<MaxCountType, number>;|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum DataType<br>差异内容：export declare enum DataType|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：DataType；<br>API声明：SET_SELECTED_URIS = 1<br>差异内容：SET_SELECTED_URIS = 1|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：DataType；<br>API声明：SET_ALBUM_URI = 2<br>差异内容：SET_ALBUM_URI = 2|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum ItemType<br>差异内容：export declare enum ItemType|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：ItemType；<br>API声明：THUMBNAIL = 0<br>差异内容：THUMBNAIL = 0|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：ItemType；<br>API声明：CAMERA = 1<br>差异内容：CAMERA = 1|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum ClickType<br>差异内容：export declare enum ClickType|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：ClickType；<br>API声明：SELECTED = 0<br>差异内容：SELECTED = 0|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：ClickType；<br>API声明：DESELECTED = 1<br>差异内容：DESELECTED = 1|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum PickerOrientation<br>差异内容：export declare enum PickerOrientation|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerOrientation；<br>API声明：VERTICAL = 0<br>差异内容：VERTICAL = 0|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerOrientation；<br>API声明：HORIZONTAL = 1<br>差异内容：HORIZONTAL = 1|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum SelectMode<br>差异内容：export declare enum SelectMode|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：SelectMode；<br>API声明：SINGLE_SELECT = 0<br>差异内容：SINGLE_SELECT = 0|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：SelectMode；<br>API声明：MULTI_SELECT = 1<br>差异内容：MULTI_SELECT = 1|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum PickerColorMode<br>差异内容：export declare enum PickerColorMode|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerColorMode；<br>API声明：AUTO = 0<br>差异内容：AUTO = 0|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerColorMode；<br>API声明：LIGHT = 1<br>差异内容：LIGHT = 1|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PickerColorMode；<br>API声明：DARK = 2<br>差异内容：DARK = 2|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum ReminderMode<br>差异内容：export declare enum ReminderMode|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：ReminderMode；<br>API声明：NONE = 0<br>差异内容：NONE = 0|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：ReminderMode；<br>API声明：TOAST = 1<br>差异内容：TOAST = 1|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：ReminderMode；<br>API声明：MASK = 2<br>差异内容：MASK = 2|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum MaxCountType<br>差异内容：export declare enum MaxCountType|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：MaxCountType；<br>API声明：TOTAL_MAX_COUNT = 0<br>差异内容：TOTAL_MAX_COUNT = 0|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：MaxCountType；<br>API声明：PHOTO_MAX_COUNT = 1<br>差异内容：PHOTO_MAX_COUNT = 1|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：MaxCountType；<br>API声明：VIDEO_MAX_COUNT = 2<br>差异内容：VIDEO_MAX_COUNT = 2|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum PhotoBrowserRange<br>差异内容：export declare enum PhotoBrowserRange|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PhotoBrowserRange；<br>API声明：ALL = 0<br>差异内容：ALL = 0|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：PhotoBrowserRange；<br>API声明：SELECTED_ONLY = 1<br>差异内容：SELECTED_ONLY = 1|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare struct RecentPhotoComponent<br>差异内容：export declare struct RecentPhotoComponent|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：RecentPhotoComponent；<br>API声明：recentPhotoOptions?: RecentPhotoOptions;<br>差异内容：recentPhotoOptions?: RecentPhotoOptions;|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：RecentPhotoComponent；<br>API声明：onRecentPhotoCheckResult?: RecentPhotoCheckResultCallback;<br>差异内容：onRecentPhotoCheckResult?: RecentPhotoCheckResultCallback;|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：RecentPhotoComponent；<br>API声明：onRecentPhotoClick: RecentPhotoClickCallback;<br>差异内容：onRecentPhotoClick: RecentPhotoClickCallback;|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export type RecentPhotoCheckResultCallback = (recentPhotoExists: boolean) => void;<br>差异内容：export type RecentPhotoCheckResultCallback = (recentPhotoExists: boolean) => void;|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export type RecentPhotoClickCallback = (recentPhotoInfo: BaseItemInfo) => boolean;<br>差异内容：export type RecentPhotoClickCallback = (recentPhotoInfo: BaseItemInfo) => boolean;|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare class RecentPhotoOptions<br>差异内容：export declare class RecentPhotoOptions|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：RecentPhotoOptions；<br>API声明：period?: number;<br>差异内容：period?: number;|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：RecentPhotoOptions；<br>API声明：MIMEType?: photoAccessHelper.PhotoViewMIMETypes;<br>差异内容：MIMEType?: photoAccessHelper.PhotoViewMIMETypes;|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：RecentPhotoOptions；<br>API声明：photoSource?: PhotoSource;<br>差异内容：photoSource?: PhotoSource;|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum PhotoSource<br>差异内容：export declare enum PhotoSource|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：PhotoSource；<br>API声明：ALL = 0<br>差异内容：ALL = 0|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：PhotoSource；<br>API声明：CAMERA = 1<br>差异内容：CAMERA = 1|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：PhotoSource；<br>API声明：SCREENSHOT = 2<br>差异内容：SCREENSHOT = 2|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：declare namespace sendablePhotoAccessHelper<br>差异内容：declare namespace sendablePhotoAccessHelper|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：sendablePhotoAccessHelper；<br>API声明：function getPhotoAccessHelper(context: Context): PhotoAccessHelper;<br>差异内容：function getPhotoAccessHelper(context: Context): PhotoAccessHelper;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：sendablePhotoAccessHelper；<br>API声明：const enum PhotoType<br>差异内容：const enum PhotoType|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoType；<br>API声明：IMAGE = 1<br>差异内容：IMAGE = 1|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoType；<br>API声明：VIDEO<br>差异内容：VIDEO|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：sendablePhotoAccessHelper；<br>API声明：interface PhotoAsset<br>差异内容：interface PhotoAsset|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoAsset；<br>API声明：readonly uri: string;<br>差异内容：readonly uri: string;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoAsset；<br>API声明：readonly photoType: PhotoType;<br>差异内容：readonly photoType: PhotoType;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoAsset；<br>API声明：readonly displayName: string;<br>差异内容：readonly displayName: string;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoAsset；<br>API声明：get(member: string): photoAccessHelper.MemberType;<br>差异内容：get(member: string): photoAccessHelper.MemberType;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoAsset；<br>API声明：set(member: string, value: string): void;<br>差异内容：set(member: string, value: string): void;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoAsset；<br>API声明：commitModify(): Promise\<void>;<br>差异内容：commitModify(): Promise\<void>;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoAsset；<br>API声明：getThumbnail(size?: image.Size): Promise\<image.PixelMap>;<br>差异内容：getThumbnail(size?: image.Size): Promise\<image.PixelMap>;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoAsset；<br>API声明：convertToPhotoAsset(): photoAccessHelper.PhotoAsset;<br>差异内容：convertToPhotoAsset(): photoAccessHelper.PhotoAsset;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：sendablePhotoAccessHelper；<br>API声明：interface FetchResult<br>差异内容：interface FetchResult|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：FetchResult；<br>API声明：getCount(): number;<br>差异内容：getCount(): number;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：FetchResult；<br>API声明：isAfterLast(): boolean;<br>差异内容：isAfterLast(): boolean;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：FetchResult；<br>API声明：getFirstObject(): Promise\<T>;<br>差异内容：getFirstObject(): Promise\<T>;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：FetchResult；<br>API声明：getNextObject(): Promise\<T>;<br>差异内容：getNextObject(): Promise\<T>;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：FetchResult；<br>API声明：getLastObject(): Promise\<T>;<br>差异内容：getLastObject(): Promise\<T>;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：FetchResult；<br>API声明：getObjectByPosition(index: number): Promise\<T>;<br>差异内容：getObjectByPosition(index: number): Promise\<T>;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：FetchResult；<br>API声明：getAllObjects(): Promise\<Array\<T>>;<br>差异内容：getAllObjects(): Promise\<Array\<T>>;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：FetchResult；<br>API声明：close(): void;<br>差异内容：close(): void;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：sendablePhotoAccessHelper；<br>API声明：const enum AlbumType<br>差异内容：const enum AlbumType|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：AlbumType；<br>API声明：USER = 0<br>差异内容：USER = 0|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：AlbumType；<br>API声明：SYSTEM = 1024<br>差异内容：SYSTEM = 1024|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：sendablePhotoAccessHelper；<br>API声明：const enum AlbumSubtype<br>差异内容：const enum AlbumSubtype|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：AlbumSubtype；<br>API声明：USER_GENERIC = 1<br>差异内容：USER_GENERIC = 1|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：AlbumSubtype；<br>API声明：FAVORITE = 1025<br>差异内容：FAVORITE = 1025|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：AlbumSubtype；<br>API声明：VIDEO<br>差异内容：VIDEO|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：AlbumSubtype；<br>API声明：IMAGE = 1031<br>差异内容：IMAGE = 1031|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：AlbumSubtype；<br>API声明：ANY = 2147483647<br>差异内容：ANY = 2147483647|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：sendablePhotoAccessHelper；<br>API声明：interface AbsAlbum<br>差异内容：interface AbsAlbum|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：AbsAlbum；<br>API声明：readonly albumType: AlbumType;<br>差异内容：readonly albumType: AlbumType;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：AbsAlbum；<br>API声明：readonly albumSubtype: AlbumSubtype;<br>差异内容：readonly albumSubtype: AlbumSubtype;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：AbsAlbum；<br>API声明：albumName: string;<br>差异内容：albumName: string;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：AbsAlbum；<br>API声明：readonly albumUri: string;<br>差异内容：readonly albumUri: string;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：AbsAlbum；<br>API声明：readonly count: number;<br>差异内容：readonly count: number;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：AbsAlbum；<br>API声明：readonly coverUri: string;<br>差异内容：readonly coverUri: string;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：AbsAlbum；<br>API声明：getAssets(options: photoAccessHelper.FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：getAssets(options: photoAccessHelper.FetchOptions): Promise\<FetchResult\<PhotoAsset>>;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：sendablePhotoAccessHelper；<br>API声明：interface Album<br>差异内容：interface Album|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：Album；<br>API声明：readonly imageCount?: number;<br>差异内容：readonly imageCount?: number;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：Album；<br>API声明：readonly videoCount?: number;<br>差异内容：readonly videoCount?: number;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：Album；<br>API声明：commitModify(): Promise\<void>;<br>差异内容：commitModify(): Promise\<void>;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：Album；<br>API声明：convertToPhotoAlbum(): photoAccessHelper.Album;<br>差异内容：convertToPhotoAlbum(): photoAccessHelper.Album;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：sendablePhotoAccessHelper；<br>API声明：interface PhotoAccessHelper<br>差异内容：interface PhotoAccessHelper|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：getAssets(options: photoAccessHelper.FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：getAssets(options: photoAccessHelper.FetchOptions): Promise\<FetchResult\<PhotoAsset>>;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：getBurstAssets(burstKey: string, options: photoAccessHelper.FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：getBurstAssets(burstKey: string, options: photoAccessHelper.FetchOptions): Promise\<FetchResult\<PhotoAsset>>;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：createAsset(photoType: PhotoType, extension: string, options?: photoAccessHelper.CreateOptions): Promise\<string>;<br>差异内容：createAsset(photoType: PhotoType, extension: string, options?: photoAccessHelper.CreateOptions): Promise\<string>;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：getAlbums(options: photoAccessHelper.FetchOptions): Promise\<FetchResult\<Album>>;<br>差异内容：getAlbums(options: photoAccessHelper.FetchOptions): Promise\<FetchResult\<Album>>;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：getAlbums(type: AlbumType, subtype: AlbumSubtype, options?: photoAccessHelper.FetchOptions): Promise\<FetchResult\<Album>>;<br>差异内容：getAlbums(type: AlbumType, subtype: AlbumSubtype, options?: photoAccessHelper.FetchOptions): Promise\<FetchResult\<Album>>;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：release(): Promise\<void>;<br>差异内容：release(): Promise\<void>;|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增API|NA|类名：global；<br>API声明：declare interface MovingPhotoViewOptions<br>差异内容：declare interface MovingPhotoViewOptions|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：MovingPhotoViewOptions；<br>API声明：movingPhoto: photoAccessHelper.MovingPhoto;<br>差异内容：movingPhoto: photoAccessHelper.MovingPhoto;|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：MovingPhotoViewOptions；<br>API声明：controller?: MovingPhotoViewController;<br>差异内容：controller?: MovingPhotoViewController;|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：global；<br>API声明：interface MovingPhotoViewInterface<br>差异内容：interface MovingPhotoViewInterface|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type MovingPhotoViewEventCallback = () => void;<br>差异内容：declare type MovingPhotoViewEventCallback = () => void;|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class MovingPhotoViewAttribute<br>差异内容：declare class MovingPhotoViewAttribute|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：MovingPhotoViewAttribute；<br>API声明：muted(isMuted: boolean): MovingPhotoViewAttribute;<br>差异内容：muted(isMuted: boolean): MovingPhotoViewAttribute;|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：MovingPhotoViewAttribute；<br>API声明：objectFit(value: ImageFit): MovingPhotoViewAttribute;<br>差异内容：objectFit(value: ImageFit): MovingPhotoViewAttribute;|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：MovingPhotoViewAttribute；<br>API声明：onStart(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute;<br>差异内容：onStart(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute;|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：MovingPhotoViewAttribute；<br>API声明：onStop(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute;<br>差异内容：onStop(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute;|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：MovingPhotoViewAttribute；<br>API声明：onPause(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute;<br>差异内容：onPause(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute;|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：MovingPhotoViewAttribute；<br>API声明：onFinish(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute;<br>差异内容：onFinish(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute;|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：MovingPhotoViewAttribute；<br>API声明：onError(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute;<br>差异内容：onError(callback: MovingPhotoViewEventCallback): MovingPhotoViewAttribute;|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：global；<br>API声明：export class MovingPhotoViewController<br>差异内容：export class MovingPhotoViewController|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：MovingPhotoViewController；<br>API声明：startPlayback();<br>差异内容：startPlayback();|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：MovingPhotoViewController；<br>API声明：stopPlayback();<br>差异内容：stopPlayback();|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const MovingPhotoView: MovingPhotoViewInterface;<br>差异内容：declare const MovingPhotoView: MovingPhotoViewInterface;|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const MovingPhotoViewInstance: MovingPhotoViewAttribute;<br>差异内容：declare const MovingPhotoViewInstance: MovingPhotoViewAttribute;|api/@ohos.multimedia.movingphotoview.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：enum PhotoSubtype<br>差异内容：enum PhotoSubtype|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoSubtype；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoSubtype；<br>API声明：MOVING_PHOTO = 3<br>差异内容：MOVING_PHOTO = 3|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoSubtype；<br>API声明：BURST = 4<br>差异内容：BURST = 4|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：enum DynamicRangeType<br>差异内容：enum DynamicRangeType|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：DynamicRangeType；<br>API声明：SDR = 0<br>差异内容：SDR = 0|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：DynamicRangeType；<br>API声明：HDR = 1<br>差异内容：HDR = 1|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：RecommendationType；<br>API声明：PASSPORT = 6<br>差异内容：PASSPORT = 6|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：RecommendationType；<br>API声明：BANK_CARD = 7<br>差异内容：BANK_CARD = 7|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：RecommendationType；<br>API声明：DRIVER_LICENSE = 8<br>差异内容：DRIVER_LICENSE = 8|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：RecommendationType；<br>API声明：DRIVING_LICENSE = 9<br>差异内容：DRIVING_LICENSE = 9|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：RecommendationType；<br>API声明：FEATURED_SINGLE_PORTRAIT = 10<br>差异内容：FEATURED_SINGLE_PORTRAIT = 10|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetManager；<br>API声明：static requestMovingPhoto(context: Context, asset: PhotoAsset, requestOptions: RequestOptions, dataHandler: MediaAssetDataHandler\<MovingPhoto>): Promise\<string>;<br>差异内容：static requestMovingPhoto(context: Context, asset: PhotoAsset, requestOptions: RequestOptions, dataHandler: MediaAssetDataHandler\<MovingPhoto>): Promise\<string>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetManager；<br>API声明：static cancelRequest(context: Context, requestId: string): Promise\<void>;<br>差异内容：static cancelRequest(context: Context, requestId: string): Promise\<void>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetManager；<br>API声明：static requestVideoFile(context: Context, asset: PhotoAsset, requestOptions: RequestOptions, fileUri: string, dataHandler: MediaAssetDataHandler\<boolean>): Promise\<string>;<br>差异内容：static requestVideoFile(context: Context, asset: PhotoAsset, requestOptions: RequestOptions, fileUri: string, dataHandler: MediaAssetDataHandler\<boolean>): Promise\<string>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetManager；<br>API声明：static loadMovingPhoto(context: Context, imageFileUri: string, videoFileUri: string): Promise\<MovingPhoto>;<br>差异内容：static loadMovingPhoto(context: Context, imageFileUri: string, videoFileUri: string): Promise\<MovingPhoto>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：DATE_ADDED_MS = 'date_added_ms'<br>差异内容：DATE_ADDED_MS = 'date_added_ms'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：DATE_MODIFIED_MS = 'date_modified_ms'<br>差异内容：DATE_MODIFIED_MS = 'date_modified_ms'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：PHOTO_SUBTYPE = 'subtype'<br>差异内容：PHOTO_SUBTYPE = 'subtype'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：DYNAMIC_RANGE_TYPE = 'dynamic_range_type'<br>差异内容：DYNAMIC_RANGE_TYPE = 'dynamic_range_type'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：COVER_POSITION = 'cover_position'<br>差异内容：COVER_POSITION = 'cover_position'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：BURST_KEY = 'burst_key'<br>差异内容：BURST_KEY = 'burst_key'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：LCD_SIZE = 'lcd_size'<br>差异内容：LCD_SIZE = 'lcd_size'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoKeys；<br>API声明：THM_SIZE = 'thm_size'<br>差异内容：THM_SIZE = 'thm_size'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：interface PhotoCreationConfig<br>差异内容：interface PhotoCreationConfig|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoCreationConfig；<br>API声明：title?: string;<br>差异内容：title?: string;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoCreationConfig；<br>API声明：fileNameExtension: string;<br>差异内容：fileNameExtension: string;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoCreationConfig；<br>API声明：photoType: PhotoType;<br>差异内容：photoType: PhotoType;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoCreationConfig；<br>API声明：subtype?: PhotoSubtype;<br>差异内容：subtype?: PhotoSubtype;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：CreateOptions；<br>API声明：subtype?: PhotoSubtype;<br>差异内容：subtype?: PhotoSubtype;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：AlbumSubtype；<br>API声明：IMAGE = 1031<br>差异内容：IMAGE = 1031|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：getBurstAssets(burstKey: string, options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;<br>差异内容：getBurstAssets(burstKey: string, options: FetchOptions): Promise\<FetchResult\<PhotoAsset>>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：showAssetsCreationDialog(srcFileUris: Array\<string>, photoCreationConfigs: Array\<PhotoCreationConfig>): Promise\<Array\<string>>;<br>差异内容：showAssetsCreationDialog(srcFileUris: Array\<string>, photoCreationConfigs: Array\<PhotoCreationConfig>): Promise\<Array\<string>>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoAccessHelper；<br>API声明：createAssetWithShortTermPermission(photoCreationConfig: PhotoCreationConfig): Promise\<string>;<br>差异内容：createAssetWithShortTermPermission(photoCreationConfig: PhotoCreationConfig): Promise\<string>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoViewMIMETypes；<br>API声明：MOVING_PHOTO_IMAGE_TYPE = 'image/movingPhoto'<br>差异内容：MOVING_PHOTO_IMAGE_TYPE = 'image/movingPhoto'|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：class BaseSelectOptions<br>差异内容：class BaseSelectOptions|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：BaseSelectOptions；<br>API声明：isPreviewForSingleSelectionSupported?: boolean;<br>差异内容：isPreviewForSingleSelectionSupported?: boolean;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoSelectOptions；<br>API声明：isOriginalSupported?: boolean;<br>差异内容：isOriginalSupported?: boolean;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：PhotoSelectOptions；<br>API声明：subWindowName?: string;<br>差异内容：subWindowName?: string;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：RecommendationOptions；<br>API声明：textContextInfo?: TextContextInfo;<br>差异内容：textContextInfo?: TextContextInfo;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：interface TextContextInfo<br>差异内容：interface TextContextInfo|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：TextContextInfo；<br>API声明：text?: string;<br>差异内容：text?: string;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetChangeRequest；<br>API声明：saveCameraPhoto(): void;<br>差异内容：saveCameraPhoto(): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MediaAssetChangeRequest；<br>API声明：discardCameraPhoto(): void;<br>差异内容：discardCameraPhoto(): void;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：photoAccessHelper；<br>API声明：interface MovingPhoto<br>差异内容：interface MovingPhoto|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MovingPhoto；<br>API声明：requestContent(imageFileUri: string, videoFileUri: string): Promise\<void>;<br>差异内容：requestContent(imageFileUri: string, videoFileUri: string): Promise\<void>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MovingPhoto；<br>API声明：requestContent(resourceType: ResourceType, fileUri: string): Promise\<void>;<br>差异内容：requestContent(resourceType: ResourceType, fileUri: string): Promise\<void>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MovingPhoto；<br>API声明：requestContent(resourceType: ResourceType): Promise\<ArrayBuffer>;<br>差异内容：requestContent(resourceType: ResourceType): Promise\<ArrayBuffer>;|api/@ohos.file.photoAccessHelper.d.ts|
|新增API|NA|类名：MovingPhoto；<br>API声明：getUri(): string;<br>差异内容：getUri(): string;|api/@ohos.file.photoAccessHelper.d.ts|
|删除API|类名：global；<br>API声明：declare namespace mediaLibrary<br>差异内容：declare namespace mediaLibrary|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：mediaLibrary；<br>API声明：function getMediaLibrary(): MediaLibrary;<br>差异内容：function getMediaLibrary(): MediaLibrary;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：mediaLibrary；<br>API声明：function getMediaLibrary(context: Context): MediaLibrary;<br>差异内容：function getMediaLibrary(context: Context): MediaLibrary;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：mediaLibrary；<br>API声明：enum MediaType<br>差异内容：enum MediaType|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaType；<br>API声明：FILE = 0<br>差异内容：FILE = 0|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaType；<br>API声明：IMAGE<br>差异内容：IMAGE|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaType；<br>API声明：VIDEO<br>差异内容：VIDEO|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaType；<br>API声明：AUDIO<br>差异内容：AUDIO|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：mediaLibrary；<br>API声明：interface MediaAssetOption<br>差异内容：interface MediaAssetOption|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaAssetOption；<br>API声明：src: string;<br>差异内容：src: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaAssetOption；<br>API声明：mimeType: string;<br>差异内容：mimeType: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaAssetOption；<br>API声明：relativePath?: string;<br>差异内容：relativePath?: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：mediaLibrary；<br>API声明：interface MediaSelectOption<br>差异内容：interface MediaSelectOption|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaSelectOption；<br>API声明：type: 'image' \| 'video' \| 'media';<br>差异内容：type: 'image' \| 'video' \| 'media';|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaSelectOption；<br>API声明：count: number;<br>差异内容：count: number;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：mediaLibrary；<br>API声明：interface FileAsset<br>差异内容：interface FileAsset|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：readonly id: number;<br>差异内容：readonly id: number;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：readonly uri: string;<br>差异内容：readonly uri: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：readonly mimeType: string;<br>差异内容：readonly mimeType: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：readonly mediaType: MediaType;<br>差异内容：readonly mediaType: MediaType;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：displayName: string;<br>差异内容：displayName: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：title: string;<br>差异内容：title: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：relativePath: string;<br>差异内容：relativePath: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：readonly parent: number;<br>差异内容：readonly parent: number;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：readonly size: number;<br>差异内容：readonly size: number;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：readonly dateAdded: number;<br>差异内容：readonly dateAdded: number;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：readonly dateModified: number;<br>差异内容：readonly dateModified: number;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：readonly dateTaken: number;<br>差异内容：readonly dateTaken: number;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：readonly artist: string;<br>差异内容：readonly artist: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：readonly audioAlbum: string;<br>差异内容：readonly audioAlbum: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：readonly width: number;<br>差异内容：readonly width: number;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：readonly height: number;<br>差异内容：readonly height: number;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：orientation: number;<br>差异内容：orientation: number;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：readonly duration: number;<br>差异内容：readonly duration: number;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：readonly albumId: number;<br>差异内容：readonly albumId: number;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：readonly albumUri: string;<br>差异内容：readonly albumUri: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：readonly albumName: string;<br>差异内容：readonly albumName: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：isDirectory(callback: AsyncCallback\<boolean>): void;<br>差异内容：isDirectory(callback: AsyncCallback\<boolean>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：isDirectory(): Promise\<boolean>;<br>差异内容：isDirectory(): Promise\<boolean>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：commitModify(callback: AsyncCallback\<void>): void;<br>差异内容：commitModify(callback: AsyncCallback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：commitModify(): Promise\<void>;<br>差异内容：commitModify(): Promise\<void>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：open(mode: string, callback: AsyncCallback\<number>): void;<br>差异内容：open(mode: string, callback: AsyncCallback\<number>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：open(mode: string): Promise\<number>;<br>差异内容：open(mode: string): Promise\<number>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：close(fd: number, callback: AsyncCallback\<void>): void;<br>差异内容：close(fd: number, callback: AsyncCallback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：close(fd: number): Promise\<void>;<br>差异内容：close(fd: number): Promise\<void>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：getThumbnail(callback: AsyncCallback\<image.PixelMap>): void;<br>差异内容：getThumbnail(callback: AsyncCallback\<image.PixelMap>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：getThumbnail(size: Size, callback: AsyncCallback\<image.PixelMap>): void;<br>差异内容：getThumbnail(size: Size, callback: AsyncCallback\<image.PixelMap>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：getThumbnail(size?: Size): Promise\<image.PixelMap>;<br>差异内容：getThumbnail(size?: Size): Promise\<image.PixelMap>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：favorite(isFavorite: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：favorite(isFavorite: boolean, callback: AsyncCallback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：favorite(isFavorite: boolean): Promise\<void>;<br>差异内容：favorite(isFavorite: boolean): Promise\<void>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：isFavorite(callback: AsyncCallback\<boolean>): void;<br>差异内容：isFavorite(callback: AsyncCallback\<boolean>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：isFavorite(): Promise\<boolean>;<br>差异内容：isFavorite(): Promise\<boolean>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：trash(isTrash: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：trash(isTrash: boolean, callback: AsyncCallback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：trash(isTrash: boolean): Promise\<void>;<br>差异内容：trash(isTrash: boolean): Promise\<void>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：isTrash(callback: AsyncCallback\<boolean>): void;<br>差异内容：isTrash(callback: AsyncCallback\<boolean>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileAsset；<br>API声明：isTrash(): Promise\<boolean>;<br>差异内容：isTrash(): Promise\<boolean>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：mediaLibrary；<br>API声明：enum FileKey<br>差异内容：enum FileKey|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：ID = "file_id"<br>差异内容：ID = "file_id"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：RELATIVE_PATH = "relative_path"<br>差异内容：RELATIVE_PATH = "relative_path"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：DISPLAY_NAME = "display_name"<br>差异内容：DISPLAY_NAME = "display_name"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：PARENT = "parent"<br>差异内容：PARENT = "parent"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：MIME_TYPE = "mime_type"<br>差异内容：MIME_TYPE = "mime_type"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：MEDIA_TYPE = "media_type"<br>差异内容：MEDIA_TYPE = "media_type"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：SIZE = "size"<br>差异内容：SIZE = "size"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：DATE_ADDED = "date_added"<br>差异内容：DATE_ADDED = "date_added"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：DATE_MODIFIED = "date_modified"<br>差异内容：DATE_MODIFIED = "date_modified"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：DATE_TAKEN = "date_taken"<br>差异内容：DATE_TAKEN = "date_taken"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：TITLE = "title"<br>差异内容：TITLE = "title"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：ARTIST = "artist"<br>差异内容：ARTIST = "artist"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：AUDIOALBUM = "audio_album"<br>差异内容：AUDIOALBUM = "audio_album"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：DURATION = "duration"<br>差异内容：DURATION = "duration"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：WIDTH = "width"<br>差异内容：WIDTH = "width"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：HEIGHT = "height"<br>差异内容：HEIGHT = "height"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：ORIENTATION = "orientation"<br>差异内容：ORIENTATION = "orientation"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：ALBUM_ID = "bucket_id"<br>差异内容：ALBUM_ID = "bucket_id"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FileKey；<br>API声明：ALBUM_NAME = "bucket_display_name"<br>差异内容：ALBUM_NAME = "bucket_display_name"|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：mediaLibrary；<br>API声明：interface MediaFetchOptions<br>差异内容：interface MediaFetchOptions|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaFetchOptions；<br>API声明：selections: string;<br>差异内容：selections: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaFetchOptions；<br>API声明：selectionArgs: Array\<string>;<br>差异内容：selectionArgs: Array\<string>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaFetchOptions；<br>API声明：order?: string;<br>差异内容：order?: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaFetchOptions；<br>API声明：uri?: string;<br>差异内容：uri?: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaFetchOptions；<br>API声明：networkId?: string;<br>差异内容：networkId?: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaFetchOptions；<br>API声明：extendArgs?: string;<br>差异内容：extendArgs?: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：mediaLibrary；<br>API声明：interface FetchFileResult<br>差异内容：interface FetchFileResult|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FetchFileResult；<br>API声明：getCount(): number;<br>差异内容：getCount(): number;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FetchFileResult；<br>API声明：isAfterLast(): boolean;<br>差异内容：isAfterLast(): boolean;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FetchFileResult；<br>API声明：close(): void;<br>差异内容：close(): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FetchFileResult；<br>API声明：getFirstObject(callback: AsyncCallback\<FileAsset>): void;<br>差异内容：getFirstObject(callback: AsyncCallback\<FileAsset>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FetchFileResult；<br>API声明：getFirstObject(): Promise\<FileAsset>;<br>差异内容：getFirstObject(): Promise\<FileAsset>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FetchFileResult；<br>API声明：getNextObject(callback: AsyncCallback\<FileAsset>): void;<br>差异内容：getNextObject(callback: AsyncCallback\<FileAsset>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FetchFileResult；<br>API声明：getNextObject(): Promise\<FileAsset>;<br>差异内容：getNextObject(): Promise\<FileAsset>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FetchFileResult；<br>API声明：getLastObject(callback: AsyncCallback\<FileAsset>): void;<br>差异内容：getLastObject(callback: AsyncCallback\<FileAsset>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FetchFileResult；<br>API声明：getLastObject(): Promise\<FileAsset>;<br>差异内容：getLastObject(): Promise\<FileAsset>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FetchFileResult；<br>API声明：getPositionObject(index: number, callback: AsyncCallback\<FileAsset>): void;<br>差异内容：getPositionObject(index: number, callback: AsyncCallback\<FileAsset>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FetchFileResult；<br>API声明：getPositionObject(index: number): Promise\<FileAsset>;<br>差异内容：getPositionObject(index: number): Promise\<FileAsset>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FetchFileResult；<br>API声明：getAllObject(callback: AsyncCallback\<Array\<FileAsset>>): void;<br>差异内容：getAllObject(callback: AsyncCallback\<Array\<FileAsset>>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：FetchFileResult；<br>API声明：getAllObject(): Promise\<Array\<FileAsset>>;<br>差异内容：getAllObject(): Promise\<Array\<FileAsset>>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：mediaLibrary；<br>API声明：interface Album<br>差异内容：interface Album|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：Album；<br>API声明：readonly albumId: number;<br>差异内容：readonly albumId: number;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：Album；<br>API声明：albumName: string;<br>差异内容：albumName: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：Album；<br>API声明：readonly albumUri: string;<br>差异内容：readonly albumUri: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：Album；<br>API声明：readonly dateModified: number;<br>差异内容：readonly dateModified: number;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：Album；<br>API声明：readonly count: number;<br>差异内容：readonly count: number;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：Album；<br>API声明：readonly relativePath: string;<br>差异内容：readonly relativePath: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：Album；<br>API声明：readonly coverUri: string;<br>差异内容：readonly coverUri: string;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：Album；<br>API声明：commitModify(callback: AsyncCallback\<void>): void;<br>差异内容：commitModify(callback: AsyncCallback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：Album；<br>API声明：commitModify(): Promise\<void>;<br>差异内容：commitModify(): Promise\<void>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：Album；<br>API声明：getFileAssets(callback: AsyncCallback\<FetchFileResult>): void;<br>差异内容：getFileAssets(callback: AsyncCallback\<FetchFileResult>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：Album；<br>API声明：getFileAssets(options: MediaFetchOptions, callback: AsyncCallback\<FetchFileResult>): void;<br>差异内容：getFileAssets(options: MediaFetchOptions, callback: AsyncCallback\<FetchFileResult>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：Album；<br>API声明：getFileAssets(options?: MediaFetchOptions): Promise\<FetchFileResult>;<br>差异内容：getFileAssets(options?: MediaFetchOptions): Promise\<FetchFileResult>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：mediaLibrary；<br>API声明：enum DirectoryType<br>差异内容：enum DirectoryType|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：DirectoryType；<br>API声明：DIR_CAMERA = 0<br>差异内容：DIR_CAMERA = 0|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：DirectoryType；<br>API声明：DIR_VIDEO<br>差异内容：DIR_VIDEO|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：DirectoryType；<br>API声明：DIR_IMAGE<br>差异内容：DIR_IMAGE|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：DirectoryType；<br>API声明：DIR_AUDIO<br>差异内容：DIR_AUDIO|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：DirectoryType；<br>API声明：DIR_DOCUMENTS<br>差异内容：DIR_DOCUMENTS|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：DirectoryType；<br>API声明：DIR_DOWNLOAD<br>差异内容：DIR_DOWNLOAD|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：mediaLibrary；<br>API声明：interface MediaLibrary<br>差异内容：interface MediaLibrary|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：getPublicDirectory(type: DirectoryType, callback: AsyncCallback\<string>): void;<br>差异内容：getPublicDirectory(type: DirectoryType, callback: AsyncCallback\<string>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：getPublicDirectory(type: DirectoryType): Promise\<string>;<br>差异内容：getPublicDirectory(type: DirectoryType): Promise\<string>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：getFileAssets(options: MediaFetchOptions, callback: AsyncCallback\<FetchFileResult>): void;<br>差异内容：getFileAssets(options: MediaFetchOptions, callback: AsyncCallback\<FetchFileResult>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：getFileAssets(options: MediaFetchOptions): Promise\<FetchFileResult>;<br>差异内容：getFileAssets(options: MediaFetchOptions): Promise\<FetchFileResult>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;<br>差异内容：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;<br>差异内容：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;<br>差异内容：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;<br>差异内容：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;<br>差异内容：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;<br>差异内容：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;<br>差异内容：on(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback: Callback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;<br>差异内容：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;<br>差异内容：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;<br>差异内容：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;<br>差异内容：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;<br>差异内容：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;<br>差异内容：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;<br>差异内容：off(type: 'deviceChange' \| 'albumChange' \| 'imageChange' \| 'audioChange' \| 'videoChange' \| 'fileChange' \| 'remoteFileChange', callback?: Callback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：createAsset(mediaType: MediaType, displayName: string, relativePath: string, callback: AsyncCallback\<FileAsset>): void;<br>差异内容：createAsset(mediaType: MediaType, displayName: string, relativePath: string, callback: AsyncCallback\<FileAsset>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：createAsset(mediaType: MediaType, displayName: string, relativePath: string): Promise\<FileAsset>;<br>差异内容：createAsset(mediaType: MediaType, displayName: string, relativePath: string): Promise\<FileAsset>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：getAlbums(options: MediaFetchOptions, callback: AsyncCallback\<Array\<Album>>): void;<br>差异内容：getAlbums(options: MediaFetchOptions, callback: AsyncCallback\<Array\<Album>>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：getAlbums(options: MediaFetchOptions): Promise\<Array\<Album>>;<br>差异内容：getAlbums(options: MediaFetchOptions): Promise\<Array\<Album>>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：storeMediaAsset(option: MediaAssetOption, callback: AsyncCallback\<string>): void;<br>差异内容：storeMediaAsset(option: MediaAssetOption, callback: AsyncCallback\<string>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：storeMediaAsset(option: MediaAssetOption): Promise\<string>;<br>差异内容：storeMediaAsset(option: MediaAssetOption): Promise\<string>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：startImagePreview(images: Array\<string>, index: number, callback: AsyncCallback\<void>): void;<br>差异内容：startImagePreview(images: Array\<string>, index: number, callback: AsyncCallback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：startImagePreview(images: Array\<string>, callback: AsyncCallback\<void>): void;<br>差异内容：startImagePreview(images: Array\<string>, callback: AsyncCallback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：startImagePreview(images: Array\<string>, index?: number): Promise\<void>;<br>差异内容：startImagePreview(images: Array\<string>, index?: number): Promise\<void>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：startMediaSelect(option: MediaSelectOption, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：startMediaSelect(option: MediaSelectOption, callback: AsyncCallback\<Array\<string>>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：startMediaSelect(option: MediaSelectOption): Promise\<Array\<string>>;<br>差异内容：startMediaSelect(option: MediaSelectOption): Promise\<Array\<string>>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：release(callback: AsyncCallback\<void>): void;<br>差异内容：release(callback: AsyncCallback\<void>): void;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：MediaLibrary；<br>API声明：release(): Promise\<void>;<br>差异内容：release(): Promise\<void>;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：mediaLibrary；<br>API声明：interface Size<br>差异内容：interface Size|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：Size；<br>API声明：width: number;<br>差异内容：width: number;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|删除API|类名：Size；<br>API声明：height: number;<br>差异内容：height: number;|NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|成员由子类迁移至父类|类名：PhotoSelectOptions；<br>API声明：MIMEType?: PhotoViewMIMETypes;<br>差异内容：MIMEType?: PhotoViewMIMETypes;|类名：BaseSelectOptions；<br>API声明：MIMEType?: PhotoViewMIMETypes;<br>差异内容：MIMEType?: PhotoViewMIMETypes;|api/@ohos.file.photoAccessHelper.d.ts|
|成员由子类迁移至父类|类名：PhotoSelectOptions；<br>API声明：maxSelectNumber?: number;<br>差异内容：maxSelectNumber?: number;|类名：BaseSelectOptions；<br>API声明：maxSelectNumber?: number;<br>差异内容：maxSelectNumber?: number;|api/@ohos.file.photoAccessHelper.d.ts|
|成员由子类迁移至父类|类名：PhotoSelectOptions；<br>API声明：isSearchSupported?: boolean;<br>差异内容：isSearchSupported?: boolean;|类名：BaseSelectOptions；<br>API声明：isSearchSupported?: boolean;<br>差异内容：isSearchSupported?: boolean;|api/@ohos.file.photoAccessHelper.d.ts|
|成员由子类迁移至父类|类名：PhotoSelectOptions；<br>API声明：isPhotoTakingSupported?: boolean;<br>差异内容：isPhotoTakingSupported?: boolean;|类名：BaseSelectOptions；<br>API声明：isPhotoTakingSupported?: boolean;<br>差异内容：isPhotoTakingSupported?: boolean;|api/@ohos.file.photoAccessHelper.d.ts|
|成员由子类迁移至父类|类名：PhotoSelectOptions；<br>API声明：recommendationOptions?: RecommendationOptions;<br>差异内容：recommendationOptions?: RecommendationOptions;|类名：BaseSelectOptions；<br>API声明：recommendationOptions?: RecommendationOptions;<br>差异内容：recommendationOptions?: RecommendationOptions;|api/@ohos.file.photoAccessHelper.d.ts|
|成员由子类迁移至父类|类名：PhotoSelectOptions；<br>API声明：preselectedUris?: Array\<string>;<br>差异内容：preselectedUris?: Array\<string>;|类名：BaseSelectOptions；<br>API声明：preselectedUris?: Array\<string>;<br>差异内容：preselectedUris?: Array\<string>;|api/@ohos.file.photoAccessHelper.d.ts|
|删除kit|类名：global；<br>API声明：api\@ohos.multimedia.mediaLibrary.d.ts<br>差异内容：MediaLibraryKit|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.multimedia.mediaLibrary.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.file.AlbumPickerComponent.d.ets<br>差异内容：MediaLibraryKit|api/@ohos.file.AlbumPickerComponent.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.file.PhotoPickerComponent.d.ets<br>差异内容：MediaLibraryKit|api/@ohos.file.PhotoPickerComponent.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.file.RecentPhotoComponent.d.ets<br>差异内容：MediaLibraryKit|api/@ohos.file.RecentPhotoComponent.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.file.sendablePhotoAccessHelper.d.ets<br>差异内容：MediaLibraryKit|api/@ohos.file.sendablePhotoAccessHelper.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.multimedia.movingphotoview.d.ts<br>差异内容：MediaLibraryKit|api/@ohos.multimedia.movingphotoview.d.ts|
|API从不支持元服务到支持元服务|类名：photoAccessHelper；<br>API声明：enum RecommendationType<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：enum RecommendationType<br>差异内容：atomicservice|api/@ohos.file.photoAccessHelper.d.ts|
|API从不支持元服务到支持元服务|类名：photoAccessHelper；<br>API声明：interface PhotoAsset<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：interface PhotoAsset<br>差异内容：atomicservice|api/@ohos.file.photoAccessHelper.d.ts|
|API从不支持元服务到支持元服务|类名：PhotoAsset；<br>API声明：readonly uri: string;<br>差异内容：NA|类名：PhotoAsset；<br>API声明：readonly uri: string;<br>差异内容：atomicservice|api/@ohos.file.photoAccessHelper.d.ts|
|API从不支持元服务到支持元服务|类名：MediaAssetChangeRequest；<br>API声明：static createImageAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest;<br>差异内容：NA|类名：MediaAssetChangeRequest；<br>API声明：static createImageAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest;<br>差异内容：atomicservice|api/@ohos.file.photoAccessHelper.d.ts|
|API从不支持元服务到支持元服务|类名：MediaAssetChangeRequest；<br>API声明：getAsset(): PhotoAsset;<br>差异内容：NA|类名：MediaAssetChangeRequest；<br>API声明：getAsset(): PhotoAsset;<br>差异内容：atomicservice|api/@ohos.file.photoAccessHelper.d.ts|
|API从不支持元服务到支持元服务|类名：MediaAssetChangeRequest；<br>API声明：setTitle(title: string): void;<br>差异内容：NA|类名：MediaAssetChangeRequest；<br>API声明：setTitle(title: string): void;<br>差异内容：atomicservice|api/@ohos.file.photoAccessHelper.d.ts|
|新增继承父类|类名：photoAccessHelper；<br>API声明：class PhotoSelectOptions<br>差异内容：NA|类名：photoAccessHelper；<br>API声明：class PhotoSelectOptions<br>差异内容：class PhotoSelectOptions|api/@ohos.file.photoAccessHelper.d.ts|
