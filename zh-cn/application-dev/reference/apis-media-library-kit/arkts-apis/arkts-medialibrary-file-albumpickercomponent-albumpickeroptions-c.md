# AlbumPickerOptions

```TypeScript
export declare class AlbumPickerOptions
```

Album Picker配置选项。

**起始版本：** 12

<!--Device-unnamed-export declare class AlbumPickerOptions--><!--Device-unnamed-export declare class AlbumPickerOptions-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { AlbumPickerComponent, AlbumPickerOptions, AlbumInfo, EmptyAreaClickCallback, AlbumPickerController } from '@kit.MediaLibraryKit';
```

## filterType

```TypeScript
filterType?: photoAccessHelper.PhotoViewMIMETypes
```

相册组件过滤参数，可筛选只显示图片、视频或者图片和视频。若未配置此参数，则相册组件显示图片和视频类型的所有资源。

**类型：** [photoAccessHelper.PhotoViewMIMETypes](arkts-medialibrary-photoaccesshelper-photoviewmimetypes-e.md)

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

<!--Device-AlbumPickerOptions-filterType?: photoAccessHelper.PhotoViewMIMETypes--><!--Device-AlbumPickerOptions-filterType?: photoAccessHelper.PhotoViewMIMETypes-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## fontSize

```TypeScript
fontSize?: number | string
```

字体大小，取值范围参考[fontSize](../../apis-arkui/arkts-components/arkts-arkui-text-comp-attribute.md#fontsize)。若未设置此参数，则使用系统默认字体大小。也可通过[AlbumPickerController](arkts-medialibrary-file-albumpickercomponent-albumpickercontroller-c.md).setFontSize动态设置字体大小。

**类型：** number &#124; string

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-AlbumPickerOptions-fontSize?: number | string--><!--Device-AlbumPickerOptions-fontSize?: number | string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## themeColorMode

```TypeScript
themeColorMode?: PickerColorMode
```

相册列表主题颜色，包括跟随系统、浅色模式以及深色模式，默认为跟随系统。

**类型：** [PickerColorMode](arkts-medialibrary-file-photopickercomponent-pickercolormode-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AlbumPickerOptions-themeColorMode?: PickerColorMode--><!--Device-AlbumPickerOptions-themeColorMode?: PickerColorMode-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
