# AlbumPickerOptions

```TypeScript
export declare class AlbumPickerOptions
```

Represents the **AlbumPicker** configuration.

**Since:** 12

<!--Device-unnamed-export declare class AlbumPickerOptions--><!--Device-unnamed-export declare class AlbumPickerOptions-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { AlbumPickerComponent, AlbumPickerOptions, AlbumInfo, EmptyAreaClickCallback, AlbumPickerController } from '@kit.MediaLibraryKit';
```

## filterType

```TypeScript
filterType?: photoAccessHelper.PhotoViewMIMETypes
```

Type of the filter. You can use it to display images, videos, or both. If this parameter is not specified, the album component displays all image and video resources.

**Type:** [photoAccessHelper.PhotoViewMIMETypes](arkts-medialibrary-photoaccesshelper-photoviewmimetypes-e.md)

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-AlbumPickerOptions-filterType?: photoAccessHelper.PhotoViewMIMETypes--><!--Device-AlbumPickerOptions-filterType?: photoAccessHelper.PhotoViewMIMETypes-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## fontSize

```TypeScript
fontSize?: number | string
```

Font size. For details about the value range, see [fontSize](../../apis-arkui/arkts-components/arkts-arkui-text-comp-attribute.md#fontsize). If this parameter is not set, the default font size is used. You can also dynamically set the font size using [AlbumPickerController](arkts-medialibrary-file-albumpickercomponent-albumpickercontroller-c.md).setFontSize.

**Type:** number &#124; string

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-AlbumPickerOptions-fontSize?: number | string--><!--Device-AlbumPickerOptions-fontSize?: number | string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## themeColorMode

```TypeScript
themeColorMode?: PickerColorMode
```

Theme color of the album list. The options are **AUTO**, **Light**, and **Dark**. The default value is **AUTO**.

**Type:** [PickerColorMode](arkts-medialibrary-file-photopickercomponent-pickercolormode-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AlbumPickerOptions-themeColorMode?: PickerColorMode--><!--Device-AlbumPickerOptions-themeColorMode?: PickerColorMode-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
