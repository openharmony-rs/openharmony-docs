# DataType

```TypeScript
export declare enum DataType
```

枚举，PickerController向picker组件发送数据的数据类型。

**起始版本：** 12

<!--Device-unnamed-export declare enum DataType--><!--Device-unnamed-export declare enum DataType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## SET_ALBUM_URI

```TypeScript
SET_ALBUM_URI = 2
```

发送已选择相册，通知图片选择器组件刷新相册，需要传入string类型。

例如：应用在自己的页面中选择相册后，需要把已选择的相册URI通过setData接口通知到图片选择器组件，从而触发图片选择器组件刷新相册数据。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-DataType-SET_ALBUM_URI = 2--><!--Device-DataType-SET_ALBUM_URI = 2-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## SET_BADGE_CONFIGS

```TypeScript
SET_BADGE_CONFIGS = 4
```

发送需要显示角标的配置，类型为[BadgeConfig](arkts-medialibrary-file-photopickercomponent-badgeconfig-c.md)，包含角标的类型和对应文件URI的数据列表。配置后，对应文件会显示配置类型的角标。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务中使用。

<!--Device-DataType-SET_BADGE_CONFIGS = 4--><!--Device-DataType-SET_BADGE_CONFIGS = 4-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## SET_ITEM_CLICK_RESULT

```TypeScript
SET_ITEM_CLICK_RESULT = 5
```

发送点击后的结果，类型为[ClickResult](arkts-medialibrary-file-photopickercomponent-clickresult-c.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-DataType-SET_ITEM_CLICK_RESULT = 5--><!--Device-DataType-SET_ITEM_CLICK_RESULT = 5-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## SET_SELECTED_INFO

```TypeScript
SET_SELECTED_INFO = 3
```

发送已选择的文件URI以及选中的图片选择器组件序号。当图片选择器组件序号与参数中的图片选择器组件序号匹配时，已选择文件支持在当前图片选择器组件里自动选中。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务中使用。

<!--Device-DataType-SET_SELECTED_INFO = 3--><!--Device-DataType-SET_SELECTED_INFO = 3-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## SET_SELECTED_URIS

```TypeScript
SET_SELECTED_URIS = 1
```

发送已选择的数据列表，通知图片选择器组件勾选状态刷新，需要传入string数组类型。

例如：应用在自己的页面中删除某张图片后，需要把剩下的已选择的数据列表通过setData接口通知到图片选择器组件，从而触发图片选择器组件勾选框状态刷新正确。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-DataType-SET_SELECTED_URIS = 1--><!--Device-DataType-SET_SELECTED_URIS = 1-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
