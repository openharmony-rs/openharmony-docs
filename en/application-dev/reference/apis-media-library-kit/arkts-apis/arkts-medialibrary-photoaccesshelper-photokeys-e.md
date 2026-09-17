# PhotoKeys

Defines the key information about an image or video file.

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## URI

```TypeScript
URI = 'uri'
```

URI of the file.

**Note:** 

Only the [DataSharePredicates.equalTo](../../apis-arkdata/arkts-apis/arkts-arkdata-datasharepredicates-datasharepredicates-c.md#equalto) predicate can be used for this field during photo query.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## PHOTO_TYPE

```TypeScript
PHOTO_TYPE = 'media_type'
```

Type of the file.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DISPLAY_NAME

```TypeScript
DISPLAY_NAME = 'display_name'
```

File name displayed. The file name must meet the following requirements:

- A valid file name must include a base name and a supported image or video extension.  
- The file name length ranges from 1 to 255.  
- The base name must not contain any invalid characters, which are:.. \ / : * ? " ' ` &lt; &gt; | { } [ ]

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## SIZE

```TypeScript
SIZE = 'size'
```

File size, in bytes. The size of a moving photo includes the total size of the image and video.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DATE_ADDED

```TypeScript
DATE_ADDED = 'date_added'
```

Unix timestamp when the file was created, in seconds.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DATE_MODIFIED

```TypeScript
DATE_MODIFIED = 'date_modified'
```

Unix timestamp when the file content (not the file name) was last modified, in seconds. This value is updated when the file content is modified, but not when the file name is modified.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DURATION

```TypeScript
DURATION = 'duration'
```

Duration, in ms.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## WIDTH

```TypeScript
WIDTH = 'width'
```

Image width, in pixels.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## HEIGHT

```TypeScript
HEIGHT = 'height'
```

Image height, in pixels.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DATE_TAKEN

```TypeScript
DATE_TAKEN = 'date_taken'
```

Unix timestamp when the photo was taken, in seconds.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## ORIENTATION

```TypeScript
ORIENTATION = 'orientation'
```

Orientation of the file, in degrees.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## FAVORITE

```TypeScript
FAVORITE = 'is_favorite'
```

Whether the file is marked as favorites.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## TITLE

```TypeScript
TITLE = 'title'
```

Title of the file.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## POSITION

```TypeScript
POSITION = 'position'
```

File location type.

**Since:** 16

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DATE_ADDED_MS

```TypeScript
DATE_ADDED_MS = 'date_added_ms'
```

Unix timestamp when the file was created, in milliseconds.

**Note:** 

The photos queried cannot be sorted based on this field.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DATE_MODIFIED_MS

```TypeScript
DATE_MODIFIED_MS = 'date_modified_ms'
```

Unix timestamp when the file was modified, in milliseconds. This value is updated when the file content is modified, but not when the file name is modified.

**Note:** 

The photos queried cannot be sorted based on this field.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## PHOTO_SUBTYPE

```TypeScript
PHOTO_SUBTYPE = 'subtype'
```

Subtype of the media file.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DYNAMIC_RANGE_TYPE

```TypeScript
DYNAMIC_RANGE_TYPE = 'dynamic_range_type'
```

Dynamic range type of the media asset.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## COVER_POSITION

```TypeScript
COVER_POSITION = 'cover_position'
```

Position of the moving photo cover, which is the video timestamp (in μs) corresponding to the cover frame.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## BURST_KEY

```TypeScript
BURST_KEY = 'burst_key'
```

Unique ID of a group of burst photos.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## LCD_SIZE

```TypeScript
LCD_SIZE = 'lcd_size'
```

Width and height of an LCD image, in the format of a **width:height** string.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## THM_SIZE

```TypeScript
THM_SIZE = 'thm_size'
```

Width and height of a thumbnail image, in the format of a **width:height** string.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DETAIL_TIME

```TypeScript
DETAIL_TIME = 'detail_time'
```

Detailed time. The value is a string of time when the image or video was taken in the time zone and does not change with the time zone.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DATE_TAKEN_MS

```TypeScript
DATE_TAKEN_MS = 'date_taken_ms'
```

Unix timestamp when the image was captured, in milliseconds.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## OWNER_ALBUM_ID

```TypeScript
OWNER_ALBUM_ID = 'owner_album_id'
```

ID of the album to which the photo belongs.

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## MEDIA_SUFFIX

```TypeScript
MEDIA_SUFFIX = 'media_suffix'
```

File name extension.

**Since:** 18

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## ASPECT_RATIO

```TypeScript
ASPECT_RATIO = 'aspect_ratio'
```

Aspect ratio of the image or video.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## CHANGE_TIME

```TypeScript
CHANGE_TIME = 'change_time'
```

Time when the photo is changed.

**Since:** 23

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## LOCAL_ASSET_SIZE

```TypeScript
LOCAL_ASSET_SIZE = 'local_asset_size'
```

Size of local asset, which well matched the content read by the application.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
