# Enums

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## PhotoType

枚举，媒体文件类型。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

| 名称  |  值 |  说明 |
| ----- |  ---- |  ---- |
| IMAGE |  1 |  图片。 |
| VIDEO |  2 |  视频。 |

## PhotoSubtype<sup>12+</sup>

PhotoSubtype是不同[PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)类型的枚举。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

| 名称  |  值 |  说明 |
| ----- |  ---- |  ---- |
| DEFAULT |  0 |  默认照片类型。 |
| MOVING_PHOTO |  3 |  动态照片文件类型。 |
| BURST |  4 |  连拍照片文件类型。 |

## DynamicRangeType<sup>12+</sup>

枚举，媒体文件的动态范围类型。

**系统能力**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

| 名称  |  值 |  说明 |
| ----- |  ---- |  ---- |
| SDR |  0 |  标准动态范围类型。|
| HDR |  1 |  高动态范围类型。  |

## AlbumType

枚举，相册类型，表示是用户相册还是系统预置相册。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

| 名称 | 值    | 说明      |
| --------| ---- | ------------|
| USER                | 0    | 用户相册。   |
| SYSTEM              | 1024 | 系统预置相册。 |

## AlbumSubtype

枚举，相册子类型，表示具体的相册类型。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

| 名称     | 值          | 说明   |
| ----- | ---------- | --- |
| USER\_GENERIC   | 1          | 用户相册。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20|
| FAVORITE        | 1025       | 收藏夹。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20 |
| VIDEO  | 1026       | 视频相册。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20|
| IMAGE<sup>12+</sup>               | 1031       | 图片相册。<br/>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 20|
| ANY    | 2147483647 | 任意相册。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20|

## PositionType<sup>16+</sup>

枚举，文件位置，表示文件在本地或云端。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 16

**ArkTS-Sta起始版本：** 20

| 名称  |  值 |  说明 |
| ----- |  ---- |  ---- |
| LOCAL |  1  |  文件只存在于本端设备。 |
| CLOUD |  2  |  文件只存在于云端。 |
| LOCAL_AND_CLOUD |  3  |  文件存在于本端设备和云端。 |

## PhotoKeys

枚举，图片和视频文件关键信息。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

| 名称          | 值              | 说明                                                       |
| ------------- | ------------------- | ---------------------------------------------------------- |
| URI           | 'uri'                 | 文件uri。<br>**注意：** 查询照片时，该字段仅支持使用[DataSharePredicates.equalTo](../apis-arkdata/js-apis-data-dataSharePredicates.md#equalto10)谓词。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20            |
| PHOTO_TYPE    | 'media_type'           | 媒体文件类型。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20  |
| DISPLAY_NAME  | 'display_name'        | 显示名字。规格为：<br>- 应包含有效文件主名和图片或视频扩展名。<br>- 文件名字符串长度为1~255。<br>- 文件主名中不允许出现的非法英文字符。<br>- 不允许出现非法字符，包括：. .. \ / : * ? " ' ` < > \| { } [ ]。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20      |
| SIZE          | 'size'                | 文件大小（单位：字节）。动态照片的size包括图片和视频的总大小。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20    |
| DATE_ADDED    | 'date_added'          | 文件创建时的Unix时间戳（单位：秒）。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20         |
| DATE_MODIFIED | 'date_modified'       | 文件修改时的Unix时间戳（单位：秒）。修改文件名不会改变此值，当文件内容发生修改时才会更新。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20 |
| DURATION      | 'duration'            | 持续时间（单位：毫秒）。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20            |
| WIDTH         | 'width'               | 图片宽度（单位：像素）。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20                                    |
| HEIGHT        | 'height'              | 图片高度（单位：像素）。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20               |
| DATE_TAKEN    | 'date_taken'          | 拍摄时的Unix时间戳（单位：秒）。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20           |
| ORIENTATION   | 'orientation'         | 文件的旋转角度，单位为度。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20  |
| FAVORITE      | 'is_favorite'            | 收藏。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20                 |
| TITLE         | 'title'               | 文件标题。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20                 |
| DATE_ADDED_MS<sup>12+</sup>  | 'date_added_ms'          | 文件创建时的Unix时间戳（单位：毫秒）。<br>**注意：** 查询照片时，不支持基于该字段排序。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 20      |
| DATE_MODIFIED_MS<sup>12+</sup>  | 'date_modified_ms'    | 文件修改时的Unix时间戳（单位：毫秒）。修改文件名不会改变此值，当文件内容发生修改时才会更新。<br>**注意：** 查询照片时，不支持基于该字段排序。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 20           |
| PHOTO_SUBTYPE<sup>12+</sup>   | 'subtype'               | 媒体文件的子类型。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 20     |
| DYNAMIC_RANGE_TYPE<sup>12+</sup>   | 'dynamic_range_type'               | 媒体文件的动态范围类型。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 20           |
| COVER_POSITION<sup>12+</sup>   | 'cover_position'               | 动态照片的封面位置，具体表示封面帧所对应的视频时间戳（单位：微秒）。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 20        |
| BURST_KEY<sup>12+</sup>   | 'burst_key'               | 一组连拍照片的唯一标识：uuid。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 20 |
| LCD_SIZE<sup>12+</sup>  | 'lcd_size'  | LCD图片的宽高，值为width:height拼接而成的字符串。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 20|
| THM_SIZE<sup>12+</sup>  | 'thm_size'  | THUMB图片的宽高，值为width:height拼接而成的字符串。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 20       |
| DETAIL_TIME<sup>13+</sup>  | 'detail_time'  | 大图浏览时间，值为拍摄时对应时区的时间的字符串，不会跟随时区变化。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 13<br/>**ArkTS-Sta起始版本：** 20       |
| DATE_TAKEN_MS<sup>13+</sup>  | 'date_taken_ms'  | 拍摄时的Unix时间戳（单位：毫秒）。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 13<br/>**ArkTS-Sta起始版本：** 20   |
| POSITION<sup>16+</sup>  | 'position'            | 文件位置类型。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 16<br/>**ArkTS-Sta起始版本：** 20        |
| MEDIA_SUFFIX<sup>18+</sup>  | 'media_suffix'            | 文件的后缀名。<br/>**ArkTS-Dyn起始版本：** 18<br/>**ArkTS-Sta起始版本：** 20                               |

## AlbumKeys

枚举，相册关键信息。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

| 名称          | 值              | 说明                                                       |
| ------------- | ------------------- | ---------------------------------------------------------- |
| URI           | 'uri'                 | 相册uri。                                                   |
| ALBUM_NAME    | 'album_name'          | 相册名字。                                                   |

## ResourceType<sup>11+</sup>

枚举，写入资源的类型。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 20

| 名称  |  值 |  说明 |
| ----- |  ---- |  ---- |
| IMAGE_RESOURCE |  1 |  表示图片资源。 |
| VIDEO_RESOURCE |  2 |  表示视频资源。 |

## ImageFileType<sup>13+</sup>

枚举，图片保存类型。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 20

| 名称  |  值 |  说明 |
| ----- |  ---- |  ---- |
| JPEG  |  1 |  表示jpeg图片类型。 |
| HEIF  |  2 |  表示heif图片类型。 |

## NotifyType

枚举，通知事件的类型。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

| 名称                      | 值   | 说明                             |
| ------------------------- | ---- | -------------------------------- |
| NOTIFY_ADD                | 0    | 添加文件集或相册通知的类型。     |
| NOTIFY_UPDATE             | 1    | 文件集或相册的更新通知类型。     |
| NOTIFY_REMOVE             | 2    | 删除文件集或相册的通知类型。     |
| NOTIFY_ALBUM_ADD_ASSET    | 3    | 在相册中添加的文件集的通知类型。 |
| NOTIFY_ALBUM_REMOVE_ASSET | 4    | 在相册中删除的文件集的通知类型。 |

## DefaultChangeUri

枚举，DefaultChangeUri子类型。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

| 名称              | 值                      | 说明                                                         |
| ----------------- | ----------------------- | ------------------------------------------------------------ |
| DEFAULT_PHOTO_URI | 'file://media/Photo'      | 默认PhotoAsset的uri，与forSubUri{true}一起使用，将接收所有PhotoAsset的更改通知。 |
| DEFAULT_ALBUM_URI | 'file://media/PhotoAlbum' | 默认相册的uri，与forSubUri{true}一起使用，将接收所有相册的更改通知。 |

## PhotoViewMIMETypes

枚举，可选择的媒体文件类型。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

| 名称                                    |  值 | 说明       |
|---------------------------------------|  ---- |----------|
| IMAGE_TYPE                            |  'image/*' | 图片类型。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20    |
| VIDEO_TYPE                            |  'video/*' | 视频类型。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20    |
| IMAGE_VIDEO_TYPE                      |  '\*/*' | 图片和视频类型。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 20 |
| MOVING_PHOTO_IMAGE_TYPE<sup>12+</sup> |  'image/movingPhoto' | 动态照片类型。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 20  |

## RecommendationType<sup>11+</sup>

枚举，推荐的图片类型。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

| 名称  |  值 |  说明 |
| ----- |  ---- | ---- |
| QR_OR_BAR_CODE  |  1 | 二维码或条码。<br/>**ArkTS-Dyn起始版本：** 11<br/>**ArkTS-Sta起始版本：** 20 |
| QR_CODE |  2 | 二维码。<br/>**ArkTS-Dyn起始版本：** 11<br/>**ArkTS-Sta起始版本：** 20 |
| BAR_CODE |  3 | 条码。<br/>**ArkTS-Dyn起始版本：** 11<br/>**ArkTS-Sta起始版本：** 20 |
| ID_CARD |  4 | 身份证。<br/>**ArkTS-Dyn起始版本：** 11<br/>**ArkTS-Sta起始版本：** 20 |
| PROFILE_PICTURE |  5 | 头像。<br/>**ArkTS-Dyn起始版本：** 11<br/>**ArkTS-Sta起始版本：** 20 |
| PASSPORT<sup>12+</sup> |  6 | 护照。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 20 |
| BANK_CARD<sup>12+</sup> |  7 | 银行卡。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 20 |
| DRIVER_LICENSE<sup>12+</sup> |  8 | 驾驶证。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 20 |
| DRIVING_LICENSE<sup>12+</sup> |  9 | 行驶证。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 20 |
| FEATURED_SINGLE_PORTRAIT<sup>12+</sup> |  10 | 推荐人像。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 20 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let recommendOptions: photoAccessHelper.RecommendationOptions = {
      recommendationType: photoAccessHelper.RecommendationType.ID_CARD
    }
    let options: photoAccessHelper.PhotoSelectOptions = {
      MIMEType: photoAccessHelper.PhotoViewMIMETypes.IMAGE_TYPE,
      maxSelectNumber: 1,
      recommendationOptions: recommendOptions
    }
    let photoPicker = new photoAccessHelper.PhotoViewPicker();
    photoPicker.select(options).then((PhotoSelectResult: photoAccessHelper.PhotoSelectResult) => {
      console.info('PhotoViewPicker.select successfully, PhotoSelectResult uri: ' + JSON.stringify(PhotoSelectResult));
    }).catch((err: BusinessError) => {
      console.error(`PhotoViewPicker.select failed with err: ${err.code}, ${err.message}`);
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`PhotoViewPicker failed with err: ${err.code}, ${err.message}`);
  }
}
```

## SingleSelectionMode<sup>18+</sup>

枚举，单选模式类型。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 24

| 名称                                    |  值 | 说明       |
|---------------------------------------|  ---- |----------|
| BROWSER_MODE                          |  0 | 大图预览模式。    |
| SELECT_MODE                           |  1 | 直接选中模式。    |
| BROWSER_AND_SELECT_MODE               |  2 | 兼容模式，点击右下角区域为直接选中模式，点击其他区域进入大图预览模式。 |

## FilterOperator<sup>19+</sup>

枚举，支持进行过滤的操作符。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 24

| 名称  |  值 |  说明 |
| ----- |  ---- |  ---- |
| EQUAL_TO |  0 |  等于。 |
| NOT_EQUAL_TO |  1 |  不等于。 |
| MORE_THAN |  2 |  大于。 |
| LESS_THAN |  3 |  小于。 |
| MORE_THAN_OR_EQUAL_TO |  4 |  大于等于。 |
| LESS_THAN_OR_EQUAL_TO |  5 |  小于等于。 |
| BETWEEN |  6 |  在指定范围内。 |

## DeliveryMode<sup>11+</sup>

枚举，资源分发模式。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 20

| 名称  |  值 |  说明 |
| ----- |  ---- |  ---- |
| FAST_MODE |  0 |  快速模式。 |
| HIGH_QUALITY_MODE |  1 |  高质量模式。 |
| BALANCE_MODE |  2 |  均衡模式。 |

## CompatibleMode<sup>15+</sup>

配置转码模式。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 20

| 名称  |  值 |  说明 |
| ----- | ---- | ---- |
| ORIGINAL_FORMAT_MODE |  0 |  原视频资源内容模式。  |
| COMPATIBLE_FORMAT_MODE    |  1 |  兼容模式，从HDR视频资源转换为SDR视频资源。    |

## CompleteButtonText<sup>14+</sup>

配置完成按钮显示内容。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 14

**ArkTS-Sta起始版本：** 20

| 名称  |  值 |  说明 |
| ----- | ---- | ---- |
| TEXT_DONE<sup>14+</sup> |  0 |  显示“完成”。 <br>**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。 |
| TEXT_SEND<sup>14+</sup>    |  1 |  显示“发送”。 <br>**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。 |
| TEXT_ADD<sup>14+</sup> |  2 |  显示“添加”。<br>**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。  |

## NotifyChangeType<sup>20+</sup>

枚举，媒体资产（图片/视频）或相册变更事件的通知类型。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 14

**ArkTS-Sta起始版本：** 23

| 名称                      | 值   | 说明                             |
| ------------------------- | ---- | -------------------------------- |
| NOTIFY_CHANGE_ADD         | 0    | 媒体资产（图片/视频）或相册已经创建。     |
| NOTIFY_CHANGE_UPDATE      | 1    | 媒体资产（图片/视频）或相册已经修改。     |
| NOTIFY_CHANGE_REMOVE      | 2    | 媒体资产（图片/视频）或相册已经删除。     |

## PhotoSource<sup>20+</sup>

枚举，图片或者视频数据的来源类型。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 24

| 名称                | 值   | 说明                                                                                                                 |
|-------------------|-----|--------------------------------------------------------------------------------------------------------------------|
| ALL | 0   | 所有来源的图片、视频。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。 |
| CAMERA | 1   | 仅相机拍摄的图片、视频。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。 |
| SCREENSHOT | 2   | 截屏图片或者录屏视频。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。 |

## MovingPhotoBadgeStateType<sup>22+</sup>

枚举，动态照片状态。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 24

| 名称                | 值   | 说明             |
|------------------- |--------|----------------------|
| NOT_MOVING_PHOTO   | 0      | 非动态照片。 |
| MOVING_PHOTO_ENABLED | 1    | 打开动态照片效果。 |
| MOVING_PHOTO_DISABLED | 2   | 关闭动态照片效果。 |

## SceneType<sup>23+</sup>

枚举，动态照片播放的场景。

**模型约束**：此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 24

| 名称                | 值   | 说明             |
|------------------- |--------|----------------------|
| GRID_TO_PHOTO_BROWSER   | 0      | 从宫格点击进入大图。 |
| PHOTO_BROWSER_SWIPE | 1    | 在大图场景左右滑动。 |

## PlayMode<sup>23+</sup>

枚举，是否支持动态照片自动播放。

**模型约束**：此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 24

| 名称                | 值   | 说明             |
|------------------- |--------|----------------------|
| DEFAULT   | 0      | 不支持动态照片自动播放。 |
| AUTO_PLAY | 1    | 支持动态照片自动播放。 |

## VideoMode<sup>22+</sup>

枚举，视频文件的log模式。

**系统能力**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

| 名称  |  值 |  说明 |
| ----- |  ---- |  ---- |
| DEFAULT |  0 |  默认类型。<br>取值为0表示当前视频非log模式或未判断类型，后续部分视频判断后字段会更新为1，因此不建议使用此字段进行查询。|
| LOG_VIDEO |  1 |  log模式视频的文件类型。  |

## OperationType<sup>22+</sup>

表示各类谓词的枚举。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 24

| 名称                    | 值 | 说明                          |
| -----------------------|---- | -------------------------------- |
| EQUAL_TO    | 1  | 等于，取value数组的第一个元素与谓词匹配。超出长度取第1个。 |
| NOT_EQUAL_TO    | 2   | 不等于，取value数组的第一个元素与谓词匹配。超出长度取第1个。 |
| GREATER_THAN    | 3   | 大于，取value数组的第一个元素与谓词匹配。 超出长度取第1个。|
| LESS_THAN    | 4   | 小于，取value数组的第一个元素与谓词匹配。超出长度取第1个。 |
| GREATER_THAN_OR_EQUAL_TO    | 5   | 大于等于，取value数组的第一个元素与谓词匹配。超出长度取第1个。 |
| LESS_THAN_OR_EQUAL_TO    | 6   | 小于等于，取value数组的第一个元素与谓词匹配。超出长度取第1个。 |
| AND    | 7   | 逻辑'与'，相当于数据库查询语句的'and'。无需传入field和value。 |
| OR    | 8  | 逻辑'或'，相当于数据库查询语句的'or'。无需传入field和value。 |
| IN    | 9   | 匹配在指定范围内的字段，value长度限制10个。 |
| NOT_IN    | 10   | 匹配不在指定范围内的字段，value长度限制10个。 |
| BEGIN_WRAP    | 11   | 用于向谓词添加英文左括号，相当于数据库查询语句的"("，必须和英文右括号一起使用。无需传入field和value。 |
| END_WRAP    | 12   | 用于向谓词添加英文右括号，相当于数据库查询语句的")"，必须和英文左括号一起使用。无需传入field和value。 |
| BETWEEN    | 13   | 匹配指定范围内的字段。<br>包含两端边界值，为左闭右闭区间。取value数组的前两个元素与谓词匹配，超出长度取前2个，分别表示左右边界。例如：[1, 2, 3, 4]中取前两个，1表示左边界，2表示右边界。 |
| NOT_BETWEEN    | 14   | 匹配超出指定范围内的字段。<br>不包含两端边界值，为左开右开区间。取value数组的前两个元素与谓词匹配，超出长度取前2个，分别表示左右边界。例如：[1, 2, 3, 4]中取前两个，1表示左边界，2表示右边界。 |

## GridLevel<sup>23+</sup>
 	  	 
枚举类型，用于设置拉起picker后的宫格列数档位。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。
 	
**模型约束**： 此接口仅可在Stage模型下使用。

**系统能力**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 24
    
| 名称  |  值 |  说明 |
| ----- |  ---- |  ---- |
| SPACIOUS |  0 |  宽松宫格档位。该挡位为标准宫格的列数减1。|
| STANDARD |  1 |  标准宫格档位。不同设备尺寸对应的标准宫格列数各不相同，当未配置标准宫格列数时，系统将使用默认列数。|
| COMPACT |  2 |  紧密宫格档位。该挡位为标准宫格的列数加1。 |

## GridPinchModeType<sup>23+</sup>
    
枚举，宫格捏合模式类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。
    
**模型约束**： 此接口仅可在Stage模型下使用。

**系统能力**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 24
    
| 名称  |  值 |  说明 |
| ----- |  ---- |  ---- |
| FULL_FUNCTION_GRID | 0 | 宫格支持捏合，捏合后支持选中、点击进大图操纵。|