# @ohos.file.AlbumPickerComponent(AlbumPickerComponent)

The **AlbumPickerComponent** embedded in the UI of an application allows the application to access the albums in the
 user directory without any permission.

Note that **AlbumPickerComponent** does not support nesting. Additionally, prevent overlaying components with the
 **overlay** attribute or of higher levels on top it, as this will prevent it from receiving gesture events.

This component must be used together with [PhotoPickerComponent](arkts-medialibrary-file-photopickercomponent-photopickercomponent-s.md). When a user
 selects an album by using the **AlbumPickerComponent**, the **PhotoPickerComponent** is instructed to update the
 images and videos in the album.

> **NOTE**
 >
 > - This component does not support [same-layer rendering](../../../web/web-same-layer.md).

## Attributes

The universal attributes are supported.

## Modules to Import

```TypeScript
import { AlbumPickerComponent, AlbumPickerOptions, AlbumInfo, EmptyAreaClickCallback, AlbumPickerController } from '@kit.MediaLibraryKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [AlbumInfo](arkts-medialibrary-file-albumpickercomponent-albuminfo-c.md) | Represents album information. |
| [AlbumPickerController](arkts-medialibrary-file-albumpickercomponent-albumpickercontroller-c.md) | A controller that enables applications to send data to the **AlbumPickerComponent**. |
| [AlbumPickerOptions](arkts-medialibrary-file-albumpickercomponent-albumpickeroptions-c.md) | Represents the **AlbumPicker** configuration. |

### Structs

| Name | Description |
| --- | --- |
| [AlbumPickerComponent](arkts-medialibrary-file-albumpickercomponent-albumpickercomponent-s.md) | AlbumPickerComponent( {albumPickerOptions?: AlbumPickerOptions, onAlbumClick?: (albumInfo: AlbumInfo) =&gt; boolean, onEmptyAreaClick?: EmptyAreaClickCallback, albumPickerController?: AlbumPickerController }) |

### Types

| Name | Description |
| --- | --- |
| [EmptyAreaClickCallback](arkts-medialibrary-emptyareaclickcallback-t.md) | Called when the blank area of the **AlbumPickerComponent** is tapped. |

## Examples

```TypeScript
// xxx.ets
import { AlbumPickerComponent, AlbumPickerOptions, AlbumInfo, PickerColorMode, photoAccessHelper, EmptyAreaClickCallback } from '@kit.MediaLibraryKit';

@Entry
@Component
struct PickerDemo {
  albumPickerOptions: AlbumPickerOptions = new AlbumPickerOptions();
  private emptyAreaClickCallback: EmptyAreaClickCallback = (): void => this.onEmptyAreaClick();

  aboutToAppear() {
    this.albumPickerOptions.themeColorMode = PickerColorMode.AUTO;
    this.albumPickerOptions.filterType = photoAccessHelper.PhotoViewMIMETypes.IMAGE_VIDEO_TYPE;
  }
  
  private onAlbumClick(albumInfo: AlbumInfo): boolean {
    if (albumInfo?.uri) {
      // pickerController instructs PhotoPickerComponent to refresh data.
    }
    if (albumInfo?.albumName) {
      // Perform subsequent processing based on the obtained albumName.
    }
    return true;
  }
  
  private onEmptyAreaClick(): void {
    // Callback when the blank area of the component is tapped.
  }

  build() {
    Stack() {
      AlbumPickerComponent({
        albumPickerOptions: this.albumPickerOptions,
        onAlbumClick:(albumInfo: AlbumInfo): boolean => this.onAlbumClick(albumInfo),
        onEmptyAreaClick: this.emptyAreaClickCallback,
      }).height('100%').width('100%')
    }
  }
}
```
