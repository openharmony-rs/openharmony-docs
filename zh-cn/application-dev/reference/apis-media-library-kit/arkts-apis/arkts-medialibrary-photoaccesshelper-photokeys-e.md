# PhotoKeys

枚举，图片和视频文件关键信息。

**起始版本：** 23

<!--Device-photoAccessHelper-enum PhotoKeys--><!--Device-photoAccessHelper-enum PhotoKeys-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## URI

```TypeScript
URI = 'uri'
```

文件uri。 **注意：** 查询照片时，该字段仅支持使用 [DataSharePredicates.equalTo](../../apis-arkdata/arkts-apis/arkts-arkdata-datasharepredicates-datasharepredicates-c.md#equalto) 谓词。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-URI = 'uri'--><!--Device-PhotoKeys-URI = 'uri'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## PHOTO_TYPE

```TypeScript
PHOTO_TYPE = 'media_type'
```

媒体文件类型。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-PHOTO_TYPE = 'media_type'--><!--Device-PhotoKeys-PHOTO_TYPE = 'media_type'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DISPLAY_NAME

```TypeScript
DISPLAY_NAME = 'display_name'
```

显示名字。规格为： - 应包含有效文件主名和图片或视频扩展名。 - 文件名字符串长度的取值范围为[1, 255]。 - 文件主名中不允许出现的非法英文字符，包括：. .. \ / : * ? " ' ` &lt; &gt; | { } [ ]。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-DISPLAY_NAME = 'display_name'--><!--Device-PhotoKeys-DISPLAY_NAME = 'display_name'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## SIZE

```TypeScript
SIZE = 'size'
```

文件大小（单位：字节）。动态照片的size包括图片和视频的总大小。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-SIZE = 'size'--><!--Device-PhotoKeys-SIZE = 'size'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DATE_ADDED

```TypeScript
DATE_ADDED = 'date_added'
```

文件创建时的Unix时间戳（单位：秒）。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-DATE_ADDED = 'date_added'--><!--Device-PhotoKeys-DATE_ADDED = 'date_added'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DATE_MODIFIED

```TypeScript
DATE_MODIFIED = 'date_modified'
```

文件修改时的Unix时间戳（单位：秒）。修改文件名不会改变此值，当文件内容发生修改时才会更新。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-DATE_MODIFIED = 'date_modified'--><!--Device-PhotoKeys-DATE_MODIFIED = 'date_modified'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DURATION

```TypeScript
DURATION = 'duration'
```

持续时间（单位：毫秒）。 在API version 23之前，动态照片的duration将返回0； 在API version 23及之后，返回动态照片附带视频片段的时长，异常场景返回-1。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-DURATION = 'duration'--><!--Device-PhotoKeys-DURATION = 'duration'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## WIDTH

```TypeScript
WIDTH = 'width'
```

图片宽度（单位：像素）。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-WIDTH = 'width'--><!--Device-PhotoKeys-WIDTH = 'width'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## HEIGHT

```TypeScript
HEIGHT = 'height'
```

图片高度（单位：像素）。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-HEIGHT = 'height'--><!--Device-PhotoKeys-HEIGHT = 'height'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DATE_TAKEN

```TypeScript
DATE_TAKEN = 'date_taken'
```

拍摄时的Unix时间戳（单位：秒）。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-DATE_TAKEN = 'date_taken'--><!--Device-PhotoKeys-DATE_TAKEN = 'date_taken'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## ORIENTATION

```TypeScript
ORIENTATION = 'orientation'
```

文件的旋转角度，单位为度。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-ORIENTATION = 'orientation'--><!--Device-PhotoKeys-ORIENTATION = 'orientation'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## FAVORITE

```TypeScript
FAVORITE = 'is_favorite'
```

收藏。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-FAVORITE = 'is_favorite'--><!--Device-PhotoKeys-FAVORITE = 'is_favorite'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## TITLE

```TypeScript
TITLE = 'title'
```

文件标题。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-TITLE = 'title'--><!--Device-PhotoKeys-TITLE = 'title'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DATE_ADDED_MS

```TypeScript
DATE_ADDED_MS = 'date_added_ms'
```

文件创建时的Unix时间戳（单位：毫秒）。 **注意：** 查询照片时，不支持基于该字段排序。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-DATE_ADDED_MS = 'date_added_ms'--><!--Device-PhotoKeys-DATE_ADDED_MS = 'date_added_ms'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DATE_MODIFIED_MS

```TypeScript
DATE_MODIFIED_MS = 'date_modified_ms'
```

文件修改时的Unix时间戳（单位：毫秒）。修改文件名不会改变此值，当文件内容发生修改时才会更新。 **注意：** 查询照片时，不支持基于该字段排序。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-DATE_MODIFIED_MS = 'date_modified_ms'--><!--Device-PhotoKeys-DATE_MODIFIED_MS = 'date_modified_ms'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## PHOTO_SUBTYPE

```TypeScript
PHOTO_SUBTYPE = 'subtype'
```

媒体文件的子类型。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-PHOTO_SUBTYPE = 'subtype'--><!--Device-PhotoKeys-PHOTO_SUBTYPE = 'subtype'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DYNAMIC_RANGE_TYPE

```TypeScript
DYNAMIC_RANGE_TYPE = 'dynamic_range_type'
```

媒体文件的动态范围类型。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-DYNAMIC_RANGE_TYPE = 'dynamic_range_type'--><!--Device-PhotoKeys-DYNAMIC_RANGE_TYPE = 'dynamic_range_type'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## COVER_POSITION

```TypeScript
COVER_POSITION = 'cover_position'
```

动态照片的封面位置，具体表示封面帧所对应的视频时间戳（单位：微秒）。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-COVER_POSITION = 'cover_position'--><!--Device-PhotoKeys-COVER_POSITION = 'cover_position'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## BURST_KEY

```TypeScript
BURST_KEY = 'burst_key'
```

一组连拍照片的唯一标识：uuid。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-BURST_KEY = 'burst_key'--><!--Device-PhotoKeys-BURST_KEY = 'burst_key'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## LCD_SIZE

```TypeScript
LCD_SIZE = 'lcd_size'
```

LCD图片的宽高，值为width:height拼接而成的字符串。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-LCD_SIZE = 'lcd_size'--><!--Device-PhotoKeys-LCD_SIZE = 'lcd_size'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## THM_SIZE

```TypeScript
THM_SIZE = 'thm_size'
```

THUMB图片的宽高，值为width:height拼接而成的字符串。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-THM_SIZE = 'thm_size'--><!--Device-PhotoKeys-THM_SIZE = 'thm_size'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DETAIL_TIME

```TypeScript
DETAIL_TIME = 'detail_time'
```

大图浏览时间，值为拍摄时对应时区的时间的字符串，不会跟随时区变化。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-DETAIL_TIME = 'detail_time'--><!--Device-PhotoKeys-DETAIL_TIME = 'detail_time'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DATE_TAKEN_MS

```TypeScript
DATE_TAKEN_MS = 'date_taken_ms'
```

拍摄时的Unix时间戳（单位：毫秒）。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoKeys-DATE_TAKEN_MS = 'date_taken_ms'--><!--Device-PhotoKeys-DATE_TAKEN_MS = 'date_taken_ms'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## MEDIA_SUFFIX

```TypeScript
MEDIA_SUFFIX = 'media_suffix'
```

文件的后缀名。

**起始版本：** 23

<!--Device-PhotoKeys-MEDIA_SUFFIX = 'media_suffix'--><!--Device-PhotoKeys-MEDIA_SUFFIX = 'media_suffix'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## CHANGE_TIME

```TypeScript
CHANGE_TIME = 'change_time'
```

照片的更改时间（单位：秒）。

**起始版本：** 23

<!--Device-PhotoKeys-CHANGE_TIME = 'change_time'--><!--Device-PhotoKeys-CHANGE_TIME = 'change_time'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## ASPECT_RATIO

```TypeScript
ASPECT_RATIO = 'aspect_ratio'
```

图片和视频的宽高比。 ​

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoKeys-ASPECT_RATIO = 'aspect_ratio'--><!--Device-PhotoKeys-ASPECT_RATIO = 'aspect_ratio'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## LOCAL_ASSET_SIZE

```TypeScript
LOCAL_ASSET_SIZE = 'local_asset_size'
```

本地文件的实际大小（单位：字节）。 - 该属性仅表示本地文件大小，默认值为0表示纯云文件或尚未识别的本地文件大小。 - 当本地文件为动态照片且模式发生变化时，该属性会发生变化。例如：当图库中的动态照片处于“关闭动态”状态时，该属性仅表示封面帧大小。 ​

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoKeys-LOCAL_ASSET_SIZE = 'local_asset_size'--><!--Device-PhotoKeys-LOCAL_ASSET_SIZE = 'local_asset_size'-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

