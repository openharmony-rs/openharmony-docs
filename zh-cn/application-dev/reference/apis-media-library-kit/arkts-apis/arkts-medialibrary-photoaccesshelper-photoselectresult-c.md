# PhotoSelectResult

返回图库选择后的结果集。

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-class PhotoSelectResult--><!--Device-photoAccessHelper-class PhotoSelectResult-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## contextRecoveryInfo

```TypeScript
contextRecoveryInfo: ContextRecoveryInfo
```

当用户完成选择时返回的photoSelectResult将包含退出picker的上下文信息contextRecoveryInfo，支持应用下次启动PhotoPicker时设置给PhotoSelectOptions用于上次退出时 现场的恢复。

**类型：** [ContextRecoveryInfo](arkts-medialibrary-photoaccesshelper-contextrecoveryinfo-c.md)

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectResult-contextRecoveryInfo: ContextRecoveryInfo--><!--Device-PhotoSelectResult-contextRecoveryInfo: ContextRecoveryInfo-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isOriginalPhoto

```TypeScript
isOriginalPhoto: boolean
```

返回图库选择后的媒体文件是否为原图。true表示是原图，false表示不是原图，默认值是false。

**类型：** boolean

**起始版本：** 26.0.0

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectResult-isOriginalPhoto: boolean--><!--Device-PhotoSelectResult-isOriginalPhoto: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## movingPhotoBadgeStates

```TypeScript
movingPhotoBadgeStates: Array<MovingPhotoBadgeStateType>
```

返回图库选择的媒体文件动态照片状态数组。 当isMovingPhotoBadgeShown为true时，movingPhotoBadgeStates携带动态照片状态，反之为空。

**类型：** Array&lt;[MovingPhotoBadgeStateType](arkts-medialibrary-photoaccesshelper-movingphotobadgestatetype-e.md)&gt;

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectResult-movingPhotoBadgeStates: Array<MovingPhotoBadgeStateType>--><!--Device-PhotoSelectResult-movingPhotoBadgeStates: Array<MovingPhotoBadgeStateType>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoUris

```TypeScript
photoUris: Array<string>
```

返回图库选择后的媒体文件的URI数组。 此URI数组只能通过临时授权的方式调用 [photoAccessHelper.getAssets](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#getassets) 接口去使用，具体使用方式请参考[媒体文件URI的使用方式](../../../file-management/user-file-uri-intro.md#媒体文件uri的使用方式)。 **注意：** 当资源为连拍照片类型时，则返回该连拍组的所有资源，判断是否为连拍图的方式请参考 [通过URI判断连拍图资源](../../../media/medialibrary/medialibrary-faqs/medialibrary-asset-judgment-faq.md#通过uri判断连拍图资源)。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectResult-photoUris: Array<string>--><!--Device-PhotoSelectResult-photoUris: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

