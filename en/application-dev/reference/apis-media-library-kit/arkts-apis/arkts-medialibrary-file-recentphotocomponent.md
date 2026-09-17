# @ohos.file.RecentPhotoComponent(RecentPhotoComponent)

The RecentPhotoComponent embedded in the UI of an application allows the application to access the recent image or
 video in the user directory without the required permission. This component grants the application only the read
 permission.

Note that **RecentPhotoComponent** does not support nesting. Additionally, prevent overlaying components with the
 **overlay** attribute or of higher levels on top it, as this will prevent it from receiving gesture events.

> **NOTE**
 >
 > - This component does not support [same-layer rendering](../../../web/web-same-layer.md).

## Properties

The universal properties are supported.

## Modules to Import

```TypeScript
import { RecentPhotoComponent, RecentPhotoCheckResultCallback, RecentPhotoInfo, RecentPhotoCheckInfoCallback, RecentPhotoClickCallback, RecentPhotoOptions, PhotoSource } from '@kit.MediaLibraryKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [RecentPhotoInfo](arkts-medialibrary-file-recentphotocomponent-recentphotoinfo-c.md) | Represents information about the recent image or video. |
| [RecentPhotoOptions](arkts-medialibrary-file-recentphotocomponent-recentphotooptions-c.md) | Represents the configuration of the recent image or video. |

### Structs

| Name | Description |
| --- | --- |
| [RecentPhotoComponent](arkts-medialibrary-file-recentphotocomponent-recentphotocomponent-s.md) | RecentPhotoComponent({ recentPhotoOptions?: RecentPhotoOptions, onRecentPhotoCheckResult?: RecentPhotoCheckResultCallback, onRecentPhotoClick: RecentPhotoClickCallback, onRecentPhotoCheckInfo?: RecentPhotoCheckInfoCallback, }) |

### Enums

| Name | Description |
| --- | --- |
| [PhotoSource](arkts-medialibrary-file-recentphotocomponent-photosource-e.md) | Enumerates the sources of the image or video data. |

### Types

| Name | Description |
| --- | --- |
| [RecentPhotoCheckInfoCallback](arkts-medialibrary-recentphotocheckinfocallback-t.md) | Called to return whether the recent image or video exists and the information about it. |
| [RecentPhotoCheckResultCallback](arkts-medialibrary-recentphotocheckresultcallback-t.md) | Called to return the query result of the recent image or video. |
| [RecentPhotoClickCallback](arkts-medialibrary-recentphotoclickcallback-t.md) | Called when the recent image or video is selected. No special processing is performed on the return value. |

## Examples

```TypeScript
// xxx.ets
// Since API version 23, you are advised to import required modules from '@kit.MediaLibraryKit'.
// In versions earlier than API version 23, you need to import the required modules separately.
// import { RecentPhotoComponent, RecentPhotoOptions, PhotoSource, RecentPhotoInfo, RecentPhotoCheckResultCallback, RecentPhotoClickCallback, RecentPhotoCheckInfoCallback } from '@ohos.file.RecentPhotoComponent';
// import { BaseItemInfo } from '@ohos.file.PhotoPickerComponent';
// import { photoAccessHelper } from '@ohos.file.photoAccessHelper';
import {
  photoAccessHelper,
  RecentPhotoComponent, 
  RecentPhotoOptions, 
  PhotoSource, 
  RecentPhotoInfo, 
  RecentPhotoCheckResultCallback, 
  RecentPhotoClickCallback, 
  RecentPhotoCheckInfoCallback,
  BaseItemInfo
} from '@kit.MediaLibraryKit';

@Entry
@Component
struct PickerDemo {
  private recentPhotoOptions: RecentPhotoOptions = new RecentPhotoOptions();
  private recentPhotoCheckResultCallback: RecentPhotoCheckResultCallback = (recentPhotoExists: boolean) => this.onRecentPhotoCheckResult(recentPhotoExists);
  private recentPhotoClickCallback: RecentPhotoClickCallback = (recentPhotoInfo: BaseItemInfo): boolean => this.onRecentPhotoClick(recentPhotoInfo);
  private recentPhotoCheckInfoCallback: RecentPhotoCheckInfoCallback = (recentPhotoExists: boolean, info: RecentPhotoInfo) => this.onRecentPhotoCheckInfo(recentPhotoExists, info);

  aboutToAppear() {
    this.recentPhotoOptions.MIMEType = photoAccessHelper.PhotoViewMIMETypes.IMAGE_VIDEO_TYPE;
    this.recentPhotoOptions.period = 30;
    this.recentPhotoOptions.photoSource = PhotoSource.ALL;
  }

  private onRecentPhotoCheckResult(recentPhotoExists: boolean): void {
    // Image or video that meets the search criteria exists.
    if (recentPhotoExists) {
      console.info('The photo is exist.');
    }
  }

  private onRecentPhotoClick(recentPhotoInfo: BaseItemInfo): boolean {
    // Return the image or video.
    if (recentPhotoInfo) {
      console.info('The photo uri is ' + recentPhotoInfo.uri);
      return true;
    }
    return true;
  }

  private onRecentPhotoCheckInfo(recentPhotoExists: boolean, info: RecentPhotoInfo): void {
    // Check whether an image or video that meets the conditions exists. If yes, obtain information about the image or video.
  }

  build() {
    Stack() {
      RecentPhotoComponent({
        recentPhotoOptions: this.recentPhotoOptions,
        onRecentPhotoCheckResult: this.recentPhotoCheckResultCallback,
        onRecentPhotoClick: this.recentPhotoClickCallback,
        onRecentPhotoCheckInfo: this.recentPhotoCheckInfoCallback,
      }).height('100%').width('100%')
    }
  }
}
```
