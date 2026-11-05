# @ohos.file.AlbumPickerComponent(AlbumPickerComponent)

The **AlbumPickerComponent** displays a list of albums in an app for users to select an album to browse images or
 videos. For example, in a social media app, users can select an album to upload photos. With this component, apps can
 access the album list in the public directory without requesting the album access permission. This simplifies the
 permission request process, reduces development costs, and improves user experience.

The album picker component must be used together with the photo picker component. When a user selects an album, the
 system triggers the **onAlbumClick** callback and passes **AlbumInfo** (including the album URI and name) to the app.
 The app needs to pass the URI to the photo picker component through the **PickerController** to refresh the images
 and videos in the selected album. For details about the collaboration mechanism, see
 [@ohos.file.PhotoPickerComponent (PhotoPickerComponent)](arkts-medialibrary-file-photopickercomponent-photopickercomponent-s.md).

Note that the album picker component does not support nesting. Additionally, prevent overlaying components with the
 **overlay** attribute or of higher levels on top the component, as this will prevent it from receiving gesture
 events.

> **NOTE**
 >
 > - This component is supported since API version 12. Newly added APIs will be marked with a superscript to indicate
 > their
 >
 > - This component does not support [same-layer rendering](../../../web/web-same-layer.md).

## Attributes

The [universal attributes](../../apis-arkui/arkts-components/arkts-arkui-common-comp.md) are supported.

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
| [AlbumPickerComponent](arkts-medialibrary-file-albumpickercomponent-albumpickercomponent-s.md) | AlbumPickerComponent({albumPickerOptions?: AlbumPickerOptions, onAlbumClick?: (albumInfo: AlbumInfo) =&gt; boolean, onEmptyAreaClick?: EmptyAreaClickCallback, albumPickerController?: AlbumPickerController }) |

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
        onAlbumClick: (albumInfo: AlbumInfo): boolean => this.onAlbumClick(albumInfo),
        onEmptyAreaClick: this.emptyAreaClickCallback,
      }).height('100%').width('100%')
    }
  }
}
```
