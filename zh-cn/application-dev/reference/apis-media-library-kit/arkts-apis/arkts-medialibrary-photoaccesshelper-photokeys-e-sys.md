# PhotoKeys

枚举，图片和视频文件关键信息。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DATE_TRASHED

```TypeScript
DATE_TRASHED = 'date_trashed'
```

删除日期（删除文件时间距1970年1月1日的秒数值）。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## HIDDEN

```TypeScript
HIDDEN = 'hidden'
```

文件的隐藏状态。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## USER_COMMENT

```TypeScript
USER_COMMENT = 'user_comment'
```

用户注释信息。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## CAMERA_SHOT_KEY

```TypeScript
CAMERA_SHOT_KEY = 'camera_shot_key'
```

锁屏相机拍照或录像的标记字段（仅开放给系统相机,其key值由系统相机定义）。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## DATE_YEAR

```TypeScript
DATE_YEAR = 'date_year'
```

创建文件的年份。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## DATE_MONTH

```TypeScript
DATE_MONTH = 'date_month'
```

创建文件的月份。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## DATE_DAY

```TypeScript
DATE_DAY = 'date_day'
```

创建文件的日期。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## PENDING

```TypeScript
PENDING = 'pending'
```

pending状态。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## DATE_TRASHED_MS

```TypeScript
DATE_TRASHED_MS = 'date_trashed_ms'
```

删除日期（删除文件时间距1970年1月1日的毫秒数值）。  
**注意：** 查询照片时，不支持基于该字段排序。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## MOVING_PHOTO_EFFECT_MODE

```TypeScript
MOVING_PHOTO_EFFECT_MODE = 'moving_photo_effect_mode'
```

动态照片效果模式。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## THUMBNAIL_READY

```TypeScript
THUMBNAIL_READY = 'thumbnail_ready'
```

缩略图生成标识。

**起始版本：** 13

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## CE_AVAILABLE

```TypeScript
CE_AVAILABLE = 'ce_available'
```

云增强任务标识。

**起始版本：** 13

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## SUPPORTED_WATERMARK_TYPE

```TypeScript
SUPPORTED_WATERMARK_TYPE = 'supported_watermark_type'
```

水印可编辑标识。

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## THUMBNAIL_VISIBLE

```TypeScript
THUMBNAIL_VISIBLE = 'thumbnail_visible'
```

缩略图可见标识。

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## IS_CE_AUTO

```TypeScript
IS_CE_AUTO = 'is_auto'
```

是否支持自动云增强。

**起始版本：** 18

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## IS_RECENT_SHOW

```TypeScript
IS_RECENT_SHOW = 'is_recent_show'
```

是否设置为最近显示。

**起始版本：** 18

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## SUM_SIZE

```TypeScript
SUM_SIZE = 'sum(size)'
```

文件大小总和。在fetchColumns中填入SUM_SIZE属性时，仅获取到第一个资产，并且属性中带有所有资产的总大小。

**起始版本：** 19

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## EXIF_ROTATE

```TypeScript
EXIF_ROTATE = 'exif_rotate'
```

文件的旋转角度信息。

**起始版本：** 21

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## HAS_APPLINK

```TypeScript
HAS_APPLINK = 'has_applink'
```

文件记忆链接的状态信息。

**起始版本：** 21

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## APPLINK

```TypeScript
APPLINK = 'applink'
```

I文件记忆链接的信息。

**起始版本：** 21

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## HDR_MODE

```TypeScript
HDR_MODE = 'hdr_mode'
```

文件的HDR模式。

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## COMPOSITE_DISPLAY_STATUS

```TypeScript
COMPOSITE_DISPLAY_STATUS = 'composite_display_status'
```

复合图资产显示状态。

**起始版本：** 23

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## ASSET_SOURCE_TYPE

```TypeScript
ASSET_SOURCE_TYPE = 'file_source_type'
```

Source type of assets, read only

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## FUSION_ASSET_STORAGE_PATH

```TypeScript
FUSION_ASSET_STORAGE_PATH = 'storage_path'
```

Storage path of fusion assets, read only

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## CLOUD_ID

```TypeScript
CLOUD_ID = 'cloud_id'
```

文件在云端的唯一标识。

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## EXIST_COMPATIBLE_DUPLICATE

```TypeScript
EXIST_COMPATIBLE_DUPLICATE = 'exist_compatible_duplicate'
```

兼容副本的状态信息。

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## VIDEO_MODE

```TypeScript
VIDEO_MODE = 'video_mode'
```

视频文件的log模式。

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## EDIT_DATA_EXIST

```TypeScript
EDIT_DATA_EXIST = 'edit_data_exist'
```

资产的编辑数据已存在。

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## PACKAGE_NAME

```TypeScript
PACKAGE_NAME = 'package_name'
```

文件的包名信息。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## PHOTO_RISK_STATUS

```TypeScript
PHOTO_RISK_STATUS = 'photo_risk_status'
```

图片风控状态。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## DATE_ADDED_YEAR

```TypeScript
DATE_ADDED_YEAR = 'date_added_year'
```

资产添加时间的年份。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## DATE_ADDED_MONTH

```TypeScript
DATE_ADDED_MONTH = 'date_added_month'
```

资产添加时间的月份。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## DATE_ADDED_DAY

```TypeScript
DATE_ADDED_DAY = 'date_added_day'
```

资产添加时间的日期。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## LIVEPHOTO_4D_STATUS

```TypeScript
LIVEPHOTO_4D_STATUS = 'livephoto_4d_status'
```

子弹时间动图

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## UNIQUE_ID

```TypeScript
UNIQUE_ID = 'unique_id'
```

资产的unique id

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## THUMB_STATUS

```TypeScript
THUMB_STATUS = 'thumb_status'
```

缩略图状态标识。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## LCD_FILE_SIZE

```TypeScript
LCD_FILE_SIZE = 'lcd_file_size'
```

LCD图大小。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## FILE_HIDDEN

```TypeScript
FILE_HIDDEN = 'file_hidden'
```

文件的隐藏状态。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## HIDDEN_TIME

```TypeScript
HIDDEN_TIME = 'hidden_time'
```

文件隐藏时间（隐藏文件时间距1970年1月1日的毫秒数值）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## ATTACHMENT_SIZE

```TypeScript
ATTACHMENT_SIZE = 'attachment_size'
```

附件文件的大小。单位为字节（Byte）。  
- 默认值为0，表示尚未识别的附件文件大小或附件文件大小为0。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
