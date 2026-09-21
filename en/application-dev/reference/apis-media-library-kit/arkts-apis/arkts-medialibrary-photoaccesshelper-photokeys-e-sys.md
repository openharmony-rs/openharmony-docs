# PhotoKeys

```TypeScript
enum PhotoKeys
```

Defines the key information about an image or video file.

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DATE_TRASHED

```TypeScript
DATE_TRASHED = 'date_trashed'
```

Date when the file was deleted. The value is the number of seconds elapsed since the Epoch time.

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## HIDDEN

```TypeScript
HIDDEN = 'hidden'
```

Whether the file is hidden.

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## USER_COMMENT

```TypeScript
USER_COMMENT = 'user_comment'
```

User comment information.

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## CAMERA_SHOT_KEY

```TypeScript
CAMERA_SHOT_KEY = 'camera_shot_key'
```

Key for the Ultra Snapshot feature, which allows the camera to take photos or record videos with the screen off. (This parameter is available only for the system camera, and the key value is defined by the system camera.)

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## DATE_YEAR

```TypeScript
DATE_YEAR = 'date_year'
```

Year when the file was created.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## DATE_MONTH

```TypeScript
DATE_MONTH = 'date_month'
```

Month when the file was created.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## DATE_DAY

```TypeScript
DATE_DAY = 'date_day'
```

Date when the file was created.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## PENDING

```TypeScript
PENDING = 'pending'
```

Pending state.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## DATE_TRASHED_MS

```TypeScript
DATE_TRASHED_MS = 'date_trashed_ms'
```

Date when the file was deleted. The value is the number of milliseconds elapsed since the Epoch time.

**NOTE:**  The photos queried cannot be sorted based on this field.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## MOVING_PHOTO_EFFECT_MODE

```TypeScript
MOVING_PHOTO_EFFECT_MODE = 'moving_photo_effect_mode'
```

Effect of the moving photo.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## THUMBNAIL_READY

```TypeScript
THUMBNAIL_READY = 'thumbnail_ready'
```

Whether a thumbnail is generated.

**Since:** 13

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## CE_AVAILABLE

```TypeScript
CE_AVAILABLE = 'ce_available'
```

Cloud enhancement identifier.

**Since:** 13

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## SUPPORTED_WATERMARK_TYPE

```TypeScript
SUPPORTED_WATERMARK_TYPE = 'supported_watermark_type'
```

Watermark type to set.

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## THUMBNAIL_VISIBLE

```TypeScript
THUMBNAIL_VISIBLE = 'thumbnail_visible'
```

Whether the thumbnail of the media asset is visible.

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## IS_CE_AUTO

```TypeScript
IS_CE_AUTO = 'is_auto'
```

Whether automatic cloud enhancement is supported.

**Since:** 18

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## IS_RECENT_SHOW

```TypeScript
IS_RECENT_SHOW = 'is_recent_show'
```

Whether the asset is displayed in the **Recent** list.

**Since:** 18

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## SUM_SIZE

```TypeScript
SUM_SIZE = 'sum(size)'
```

Total size of files. When **SUM_SIZE** is filled in **fetchColumns**, only the first asset is obtained, and the property includes the total size of all assets.

**Since:** 19

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## EXIF_ROTATE

```TypeScript
EXIF_ROTATE = 'exif_rotate'
```

Rotational angle of the file.

**Since:** 21

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## HAS_APPLINK

```TypeScript
HAS_APPLINK = 'has_applink'
```

Whether to enable or disable the app link association.

**Since:** 21

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## APPLINK

```TypeScript
APPLINK = 'applink'
```

Information about the app link association.

**Since:** 21

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## HDR_MODE

```TypeScript
HDR_MODE = 'hdr_mode'
```

HDR mode of the file.

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## CLOUD_ID

```TypeScript
CLOUD_ID = 'cloud_id'
```

Unique ID of the file on the cloud.

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## EXIST_COMPATIBLE_DUPLICATE

```TypeScript
EXIST_COMPATIBLE_DUPLICATE = 'exist_compatible_duplicate'
```

Whether a JPEG-compatible copy exists.

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## COMPOSITE_DISPLAY_STATUS

```TypeScript
COMPOSITE_DISPLAY_STATUS = 'composite_display_status'
```

Display status of the composite image asset.

**Since:** 23

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## VIDEO_MODE

```TypeScript
VIDEO_MODE = 'video_mode'
```

Log mode of a video file.

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## ASSET_SOURCE_TYPE

```TypeScript
ASSET_SOURCE_TYPE = 'file_source_type'
```

Source type of assets, read only

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## FUSION_ASSET_STORAGE_PATH

```TypeScript
FUSION_ASSET_STORAGE_PATH = 'storage_path'
```

Storage path of fusion assets, read only

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## EDIT_DATA_EXIST

```TypeScript
EDIT_DATA_EXIST = 'edit_data_exist'
```

Edit data for the asset already exists.

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## PACKAGE_NAME

```TypeScript
PACKAGE_NAME = 'package_name'
```

Package name of a file.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## PHOTO_RISK_STATUS

```TypeScript
PHOTO_RISK_STATUS = 'photo_risk_status'
```

Image risk control

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## DATE_ADDED_YEAR

```TypeScript
DATE_ADDED_YEAR = 'date_added_year'
```

Year when an asset is added.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## DATE_ADDED_MONTH

```TypeScript
DATE_ADDED_MONTH = 'date_added_month'
```

Month when an asset is added.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## DATE_ADDED_DAY

```TypeScript
DATE_ADDED_DAY = 'date_added_day'
```

Date when an asset is added.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## LIVEPHOTO_4D_STATUS

```TypeScript
LIVEPHOTO_4D_STATUS = 'livephoto_4d_status'
```

4d livephoto status.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## UNIQUE_ID

```TypeScript
UNIQUE_ID = 'unique_id'
```

Unique id of asset.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## HIDDEN_TIME

```TypeScript
HIDDEN_TIME = 'hidden_time'
```

hidden time of asset.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## THUMB_STATUS

```TypeScript
THUMB_STATUS = 'thumb_status'
```

Status of thumbnail, read only

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## LCD_FILE_SIZE

```TypeScript
LCD_FILE_SIZE = 'lcd_file_size'
```

Size of lcd file, read only

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## FILE_HIDDEN

```TypeScript
FILE_HIDDEN = 'file_hidden'
```

File hidden state of filemanager.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## ATTACHMENT_SIZE

```TypeScript
ATTACHMENT_SIZE = 'attachment_size'
```

Size of the asset attachment, in bytes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## SHARE_OWNER_INFO

```TypeScript
SHARE_OWNER_INFO = 'share_owner_info'
```

The asset owner in share album.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## SHARE_RISK_STATUS

```TypeScript
SHARE_RISK_STATUS = 'share_risk_status'
```

The risk status of share album asset.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## SHARE_RISK_TYPE

```TypeScript
SHARE_RISK_TYPE = 'share_risk_type'
```

The risk type of share album asset.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## PHOTO_VISIBILITY

```TypeScript
PHOTO_VISIBILITY = 'photo_visibility'
```

The photo visibility of photo asset.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## SHARE_GROUP

```TypeScript
SHARE_GROUP = 'share_group'
```

The share group of share album asset.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## SHARE_DATE_DAY

```TypeScript
SHARE_DATE_DAY = 'share_date_day'
```

The share date day of share album asset.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## MUSIC_MASTER_MODE

```TypeScript
MUSIC_MASTER_MODE = 'music_master_mode'
```

The mode of the music master.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
