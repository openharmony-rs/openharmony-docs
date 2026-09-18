# FileAsset (System API)

Provides APIs for encapsulating file asset attributes.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [PhotoAsset](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userFileManager } from '@kit.CoreFileKit';
```

## close

```TypeScript
close(fd: number, callback: AsyncCallback<void>): void
```

Closes a file. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** close

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | File descriptor of the file to close. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## close

```TypeScript
close(fd: number): Promise<void>
```

Closes this file. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** close

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | File descriptor of the file to close. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## commitModify

```TypeScript
commitModify(callback: AsyncCallback<void>): void
```

Commits the modification on the file metadata to the database. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [commitModify](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#commitmodify)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.WRITE_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## commitModify

```TypeScript
commitModify(): Promise<void>
```

Commits the modification on the file metadata to the database. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [commitModify](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#commitmodify)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.WRITE_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## favorite

```TypeScript
favorite(isFavorite: boolean, callback: AsyncCallback<void>): void
```

Favorites or unfavorites a file. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [setFavorite](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md#setfavorite)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.WRITE_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isFavorite | boolean | Yes | Whether to favorite or unfavorite the file. The value **true** means to favorite the file; the value **false** means the opposite. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## favorite

```TypeScript
favorite(isFavorite: boolean): Promise<void>
```

Favorites or unfavorites this file asset. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [setFavorite](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md#setfavorite)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.WRITE_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isFavorite | boolean | Yes | Whether to favorite or unfavorite the file. The value **true** means to favorite the file; the value **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [favorite](#favorite)

## get

```TypeScript
get(member: string): MemberType
```

Obtains the value of a **FileAsset** parameter.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [get](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#get)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| member | string | Yes | Member parameter name, for example, **ImageVideoKey.DISPLAY_NAME**. You need to set **PhotoKeys** to be obtained in **fetchColumns** for all attributes except **uri**, **photoType**, and **displayName**. For example, **fetchColumns: ['title']**. |

**Return value:**

| Type | Description |
| --- | --- |
| [MemberType](arkts-corefile-userfilemanager-membertype-t-sys.md) | Returns the member parameter. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## getExif

```TypeScript
getExif(callback: AsyncCallback<string>): void
```

Obtains the EXIF data from a JPG image and returns a JSON string. This API uses an asynchronous callback to return the result.

For details about the EXIF tags, see [image.PropertyKey](../../apis-image-kit/arkts-apis/arkts-image-image-propertykey-e.md).

| Key Value | Description |  
| --------------------------------------- | ----------------- |  
| BitsPerSample | Number of bits per sample.|
| Orientation | Image orientation.|
| ImageLength | Image length.|
| ImageWidth | Image width.|
| GPSLatitude | GPS latitude of the image.|
| GPSLongitude | GPS longitude of the image.|
| GPSLatitudeRef | Longitude reference, for example, W or E.|
| GPSLongitudeRef | Latitude reference, for example, N or S.|
| DateTimeOriginal | Shooting time.|
| ExposureTime | Exposure time.|
| [SceneType](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-scenetype-e.md) | Scene type.|
| ISOSpeedRatings | ISO sensitivity or speed.|
| FNumber | f-number.|
| DateTime | Modification time.|
| GPSTimeStamp | GPS timestamp.|
| GPSDateStamp | GPS date stamp.|
| ImageDescription | Image description.|
| Make | Manufacturer.|
| MakeNote | Manufacturer.|
| [Model](../../apis-mind-spore-lite-kit/arkts-apis/arkts-mindsporelite-mindsporelite-model-i.md) | Model.|
| PhotoMode | Photo mode.|
| SensitivityType | Sensitivity type.|
| StandardOutputSensitivity | Standard output sensitivity.|
| RecommendedExposureIndex | Recommended exposure index.|
| ApertureValue | Aperture value.|
| MeteringMode | Metering mode.|
| [LightSource](../../apis-arkui/arkts-components/arkts-arkui-lightsource-i-sys.md) | Light source.|
| [Flash](../../apis-camera-kit/arkts-apis/arkts-camera-camera-flash-i.md) | Flash status.|
| FocalLength | Focal length.|
| UserComment | User comments.|
| PixelXDimension | Pixel X dimension.|
| PixelYDimension | Pixel Y dimension.|
| [WhiteBalance](../../apis-camera-kit/arkts-apis/arkts-camera-camera-whitebalance-i.md) | White balance.|
| FocalLengthIn35mmFilm | Focal length in 35 mm film.|
| ExposureBiasValue | Exposure compensation.|

> **NOTE:** 
> 
> This API returns a JSON string that contains EXIF tags. The complete Exif information consists of all_exif and
> [ImageVideoKey](arkts-corefile-userfilemanager-imagevideokey-e-sys.md).USER_COMMENT. The two fields need to be passed to
> **fetchColumns**.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [getExif](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i-sys.md#getexif)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback that returns the EXIF data, in JSON strings. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## getExif

```TypeScript
getExif(): Promise<string>
```

Obtains the EXIF data from a JPG image and returns a JSON string. This API uses a promise to return the result.

For details about the EXIF tags, see [image.PropertyKey](../../apis-image-kit/arkts-apis/arkts-image-image-propertykey-e.md).

| Key Value | Description |  
| --------------------------------------- | ----------------- |  
| BitsPerSample | Number of bits per sample.|
| Orientation | Image orientation.|
| ImageLength | Image length.|
| ImageWidth | Image width.|
| GPSLatitude | GPS latitude of the image.|
| GPSLongitude | GPS longitude of the image.|
| GPSLatitudeRef | Longitude reference, for example, W or E.|
| GPSLongitudeRef | Latitude reference, for example, N or S.|
| DateTimeOriginal | Shooting time.|
| ExposureTime | Exposure time.|
| [SceneType](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-scenetype-e.md) | Scene type.|
| ISOSpeedRatings | ISO sensitivity or speed.|
| FNumber | f-number.|
| DateTime | Modification time.|
| GPSTimeStamp | GPS timestamp.|
| GPSDateStamp | GPS date stamp.|
| ImageDescription | Image description.|
| Make | Manufacturer.|
| MakeNote | Manufacturer.|
| [Model](../../apis-mind-spore-lite-kit/arkts-apis/arkts-mindsporelite-mindsporelite-model-i.md) | Model.|
| PhotoMode | Photo mode.|
| SensitivityType | Sensitivity type.|
| StandardOutputSensitivity | Standard output sensitivity.|
| RecommendedExposureIndex | Recommended exposure index.|
| ApertureValue | Aperture value.|
| MeteringMode | Metering mode.|
| [LightSource](../../apis-arkui/arkts-components/arkts-arkui-lightsource-i-sys.md) | Light source.|
| [Flash](../../apis-camera-kit/arkts-apis/arkts-camera-camera-flash-i.md) | Flash status.|
| FocalLength | Focal length.|
| UserComment | User comments.|
| PixelXDimension | Pixel X dimension.|
| PixelYDimension | Pixel Y dimension.|
| [WhiteBalance](../../apis-camera-kit/arkts-apis/arkts-camera-camera-whitebalance-i.md) | White balance.|
| FocalLengthIn35mmFilm | Focal length in 35 mm film.|
| ExposureBiasValue | Exposure compensation.|

> **NOTE:** 
> 
> This API returns a JSON string that contains EXIF tags. The complete Exif information consists of all_exif and
> [ImageVideoKey](arkts-corefile-userfilemanager-imagevideokey-e-sys.md).USER_COMMENT. The two fields need to be passed to
> **fetchColumns**.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [getExif](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i-sys.md#getexif)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise that returns the EXIF data, in JSON strings. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |

**Examples**

See [getExif](#getexif)

## getThumbnail

```TypeScript
getThumbnail(callback: AsyncCallback<image.PixelMap>): void
```

Obtains the thumbnail of a file. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getThumbnail](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#getthumbnail)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO or ohos.permission.READ_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Yes | Callback used to return the PixelMap of the thumbnail. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## getThumbnail

```TypeScript
getThumbnail(size: image.Size, callback: AsyncCallback<image.PixelMap>): void
```

Obtains the file thumbnail of the given size. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getThumbnail](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#getthumbnail)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO or ohos.permission.READ_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | [image.Size](../../apis-image-kit/arkts-apis/arkts-image-image-size-i.md) | Yes | Size of the thumbnail. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Yes | Callback used to return the PixelMap of the thumbnail. |

**Examples**

See [getThumbnail](#getthumbnail)

## getThumbnail

```TypeScript
getThumbnail(size?: image.Size): Promise<image.PixelMap>
```

Obtains the file thumbnail of the given size. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getThumbnail](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#getthumbnail)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO or ohos.permission.READ_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | [image.Size](../../apis-image-kit/arkts-apis/arkts-image-image-size-i.md) | No | Size of the thumbnail. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise that returns the PixelMap of the thumbnail. |

**Examples**

See [getThumbnail](#getthumbnail)

## open

```TypeScript
open(mode: string, callback: AsyncCallback<number>): void
```

Opens this file asset. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The write operations are mutually exclusive. After a write operation is complete, you must call **close** to
> close the file.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** open

**Required permissions:** ohos.permission.READ_IMAGEVIDEO or ohos.permission.READ_AUDIO or ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.WRITE_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | string | Yes | Mode of opening the file, for example, **'r'** (read-only), **'w'** (write-only), and **'rw'** (read-write). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the file descriptor of the file opened. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## open

```TypeScript
open(mode: string): Promise<number>
```

Opens this file asset. This API uses a promise to return the result.

> **NOTE:** 
> 
> The write operations are mutually exclusive. After a write operation is complete, you must call **close** to
> close the file.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** open

**Required permissions:** ohos.permission.READ_IMAGEVIDEO or ohos.permission.READ_AUDIO or ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.WRITE_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | string | Yes | File open mode, which can be **r** (read-only), **w** (write-only), or **rw** (read- write). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise that returns the file descriptor of the file opened. |

**Examples**

See [open](#open)

## set

```TypeScript
set(member: string, value: string): void
```

Sets a **FileAsset** parameter.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [set](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#set)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| member | string | Yes | Member parameter name, for example, **ImageVideoKey.DISPLAY_NAME**. |
| value | string | Yes | Value to set. Only the values of **DISPLAY_NAME** and **TITLE** can be changed. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## setHidden

```TypeScript
setHidden(hiddenState: boolean, callback: AsyncCallback<void>): void
```

Sets a file to hidden state. This API uses an asynchronous callback to return the result.

The private files set to hidden state are located in the private album (in hidden state) and are not open to third-party applications. After obtaining private files from the private album, users can set **hiddenState** to **false** to remove them from the private album.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [setHidden](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md#sethidden)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hiddenState | boolean | Yes | Whether to hide the file. The value **true** means to hide the file; the value **false** means the opposite. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| 13900020 | if parameter is invalid |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## setHidden

```TypeScript
setHidden(hiddenState: boolean): Promise<void>
```

Sets this file asset to the hidden state. This API uses a promise to return the result.

The private files set to hidden state are located in the private album (in hidden state) and are not open to third-party applications. After obtaining private files from the private album, users can set **hiddenState** to **false** to remove them from the private album.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [setHidden](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md#sethidden)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hiddenState | boolean | Yes | Whether to hide the file. The value **true** means to hide the file; the value **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| 13900020 | if parameter is invalid |

**Examples**

See [setHidden](#sethidden)

## setUserComment

```TypeScript
setUserComment(userComment: string, callback: AsyncCallback<void>): void
```

Sets user comment information of an image or video. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API can only be used to set user comment information of an image or video.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [setUserComment](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md#setusercomment)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userComment | string | Yes | User comment information to set, which cannot exceed 140 characters. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## setUserComment

```TypeScript
setUserComment(userComment: string): Promise<void>
```

Sets user comment information of an image or video. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API can only be used to set user comment information of an image or video.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [setUserComment](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md#setusercomment)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userComment | string | Yes | User comment information to set, which cannot exceed 140 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |

**Examples**

See [setUserComment](#setusercomment)

## displayName

```TypeScript
displayName: string
```

File name, including the file name extension, to display.

**Type:** string

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [displayName](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#displayname)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## fileType

```TypeScript
readonly fileType: FileType
```

Type of the file.

**Type:** [FileType](arkts-corefile-userfilemanager-filetype-e-sys.md)

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [photoType](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#phototype)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## uri

```TypeScript
readonly uri: string
```

Media asset URI, for example, **file://media/Photo/1/IMG_datetime_0001/displayName.jpg**. For details, see [Media File URI](../../../file-management/user-file-uri-intro.md#media-file-uri).

**Type:** string

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [uri](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#uri)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.
