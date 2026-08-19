# PhotoSelectOptions

图库选择选项子类，继承于BaseSelectOptions。用于拉起对应userId空间的picker。

**继承/实现关系：** PhotoSelectOptions extends [BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md)

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-class PhotoSelectOptions--><!--Device-photoAccessHelper-class PhotoSelectOptions-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## completeButtonText

```TypeScript
completeButtonText?: CompleteButtonText
```

完成按钮显示的内容。 完成按钮指在界面右下方，用户点击表示图片选择已完成的按钮。

**类型：** [CompleteButtonText](arkts-medialibrary-photoaccesshelper-completebuttontext-e.md)

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectOptions-completeButtonText?: CompleteButtonText--><!--Device-PhotoSelectOptions-completeButtonText?: CompleteButtonText-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## contextRecoveryInfo

```TypeScript
contextRecoveryInfo?: ContextRecoveryInfo
```

用于恢复上次退出时PhotoPicker现场的信息。 上次完成选择时photoPicker将返回contextRecoveryInfo给应用，应用可使用返回的contextRecoveryInfo，在下次启动时恢复上次使用picker，最后浏览的宫格界面。

**类型：** [ContextRecoveryInfo](arkts-medialibrary-photoaccesshelper-contextrecoveryinfo-c.md)

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectOptions-contextRecoveryInfo?: ContextRecoveryInfo--><!--Device-PhotoSelectOptions-contextRecoveryInfo?: ContextRecoveryInfo-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isDestroyedWithNavigation

```TypeScript
isDestroyedWithNavigation?: boolean
```

是否支持跟随[Navigation](../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigation-1)销毁，true 表示支持，false表示不支持，默认为false。 **模型约束**： 此接口仅可在Stage模型下使用。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectOptions-isDestroyedWithNavigation?: boolean--><!--Device-PhotoSelectOptions-isDestroyedWithNavigation?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isEditSupported

```TypeScript
isEditSupported?: boolean
```

是否支持编辑照片，true表示支持，false表示不支持，默认为true。

**类型：** boolean

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectOptions-isEditSupported?: boolean--><!--Device-PhotoSelectOptions-isEditSupported?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isOriginalSupported

```TypeScript
isOriginalSupported?: boolean
```

是否显示选择原图按钮，true表示显示，false表示不显示，默认为false。

**类型：** boolean

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectOptions-isOriginalSupported?: boolean--><!--Device-PhotoSelectOptions-isOriginalSupported?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isReturnToPhotoBrowserEnabled

```TypeScript
isReturnToPhotoBrowserEnabled?: boolean
```

在单选模式下，拍完照是否能自动跳转到大图预览模式，true表示支持，false表示不支持，默认为false。 **注意：** 该参数配置为true时仅在[SingleSelectionMode](arkts-medialibrary-photoaccesshelper-singleselectionmode-e.md)为BROWSER_MODE（大图预览模式）或者 BROWSER_AND_SELECT_MODE（兼容模式）并且 [BaseSelectOptions.isPreviewForSingleSelectionSupported](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md)参数为true时生效。 **模型约束**： 此接口仅可在Stage模型下使用。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectOptions-isReturnToPhotoBrowserEnabled?: boolean--><!--Device-PhotoSelectOptions-isReturnToPhotoBrowserEnabled?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isSelectionNumberVisible

```TypeScript
isSelectionNumberVisible?: boolean
```

是否支持选择序号。true表示支持，false表示不支持，默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectOptions-isSelectionNumberVisible?: boolean--><!--Device-PhotoSelectOptions-isSelectionNumberVisible?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isSelectionOrderAdjustable

```TypeScript
isSelectionOrderAdjustable?: boolean
```

是否支持调整选择顺序。true表示支持，false表示不支持，默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectOptions-isSelectionOrderAdjustable?: boolean--><!--Device-PhotoSelectOptions-isSelectionOrderAdjustable?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxPhotoSelectNumber

```TypeScript
maxPhotoSelectNumber?: int
```

支持设置的图片最大的选择数量。单位：个。 受到最大选择总数的限制，最大值为500。默认为500。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectOptions-maxPhotoSelectNumber?: int--><!--Device-PhotoSelectOptions-maxPhotoSelectNumber?: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxVideoSelectNumber

```TypeScript
maxVideoSelectNumber?: int
```

支持设置的视频最大的选择数量。单位：个。 受到系统中所有媒体文件最大选择总数的限制，最大值为500。默认为500。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectOptions-maxVideoSelectNumber?: int--><!--Device-PhotoSelectOptions-maxVideoSelectNumber?: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## pickerColorMode

```TypeScript
pickerColorMode?: PickerColorMode
```

选择器颜色模式。Picker上其他组件的深色/浅色模式（不包括背景色）。 包括搜索框、摄像头入口、使用图库的安全提示、推荐气泡等。 属性通常与**backgroundColor**配合使用。默认值为**PickerColorMode.AUTO**。 遵循系统的深色/浅色模式。 设置此属性时，请避免使用**PickerColorMode.LIGHT**与深色背景颜色搭配使用，因为这样可能会使 组件或难以看到的文本。避免使用**PickerColorMode.DARK**与浅色背景颜色相同 理由。

**类型：** [PickerColorMode](arkts-medialibrary-photoaccesshelper-pickercolormode-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectOptions-pickerColorMode?: PickerColorMode--><!--Device-PhotoSelectOptions-pickerColorMode?: PickerColorMode-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## subWindowName

```TypeScript
subWindowName?: string
```

子窗口名称。

**类型：** string

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectOptions-subWindowName?: string--><!--Device-PhotoSelectOptions-subWindowName?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

