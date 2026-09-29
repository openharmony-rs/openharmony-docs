# AlbumPickerComponent

```TypeScript
export declare struct AlbumPickerComponent
```

AlbumPickerComponent( {albumPickerOptions?: AlbumPickerOptions, onAlbumClick?: (albumInfo: AlbumInfo) =&gt; boolean, onEmptyAreaClick?: EmptyAreaClickCallback, albumPickerController?: AlbumPickerController })

The **AlbumPickerComponent** embedded in the UI of an application allows the application to access the albums in the user directory without any permission.

**Since:** 12

**Decorator:** @Component

<!--Device-unnamed-export declare struct AlbumPickerComponent--><!--Device-unnamed-export declare struct AlbumPickerComponent-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { AlbumPickerComponent, AlbumPickerOptions, AlbumInfo, EmptyAreaClickCallback, AlbumPickerController } from '@kit.MediaLibraryKit';
```

## onAlbumClick

```TypeScript
onAlbumClick?: (albumInfo: AlbumInfo) => boolean
```

Callback when select an album, will return album uri

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AlbumPickerComponent-onAlbumClick?: (albumInfo: AlbumInfo) => boolean--><!--Device-AlbumPickerComponent-onAlbumClick?: (albumInfo: AlbumInfo) => boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| albumInfo | [AlbumInfo](arkts-medialibrary-file-albumpickercomponent-albuminfo-c.md) | Yes |  |

## onEmptyAreaClick

```TypeScript
onEmptyAreaClick?: EmptyAreaClickCallback
```

Callback when click the empty area of the album component

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-AlbumPickerComponent-onEmptyAreaClick?: EmptyAreaClickCallback--><!--Device-AlbumPickerComponent-onEmptyAreaClick?: EmptyAreaClickCallback-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## albumPickerController

```TypeScript
albumPickerController?: AlbumPickerController
```

AlbumPickerController

**Type:** [AlbumPickerController](arkts-medialibrary-file-albumpickercomponent-albumpickercontroller-c.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-AlbumPickerComponent-albumPickerController?: AlbumPickerController--><!--Device-AlbumPickerComponent-albumPickerController?: AlbumPickerController-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## albumPickerOptions

```TypeScript
albumPickerOptions?: AlbumPickerOptions
```

AlbumPickerOptions

**Type:** [AlbumPickerOptions](arkts-medialibrary-file-albumpickercomponent-albumpickeroptions-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AlbumPickerComponent-albumPickerOptions?: AlbumPickerOptions--><!--Device-AlbumPickerComponent-albumPickerOptions?: AlbumPickerOptions-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
