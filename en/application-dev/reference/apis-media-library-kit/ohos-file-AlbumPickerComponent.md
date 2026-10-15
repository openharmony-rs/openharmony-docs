# @ohos.file.AlbumPickerComponent (AlbumPickerComponent)
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xuchangda-->
<!--Designer: @guxinggang-->
<!--Tester: @wangbeibei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=d6145bea4a142c09a826c29ca9c2965691c35544 translatedAt=2026-10-08T03:13:25.987Z pushedAt=2026-10-15T06:24:23.648Z -->

The **AlbumPickerComponent** displays a list of albums in an app for users to select an album to browse images or videos. For example, in a social media app, users can select an album to upload photos. With this component, apps can access the album list in the public directory without requesting the album access permission. This simplifies the permission request process, reduces development costs, and improves user experience.

The album picker component must be used together with the photo picker component. When a user selects an album, the system triggers the **onAlbumClick** callback and passes **AlbumInfo** (including the album URI and name) to the app. The app needs to pass the URI to the photo picker component through the **PickerController** to refresh the images and videos in the selected album. For details about the collaboration mechanism, see [@ohos.file.PhotoPickerComponent (PhotoPickerComponent)](ohos-file-PhotoPickerComponent.md).

Note that the album picker component does not support nesting. Additionally, prevent overlaying components with the **overlay** attribute or of higher levels on top the component, as this will prevent it from receiving gesture events.

> **NOTE**
>
> - This component is supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This component does not support [same-layer rendering](../../../application-dev/web/web-same-layer.md).

## Modules to Import

```ts
import { AlbumPickerComponent, AlbumPickerOptions, AlbumInfo, PickerColorMode, photoAccessHelper, EmptyAreaClickCallback } from '@kit.MediaLibraryKit';
```

## Attributes

The [universal attributes](../apis-arkui/arkui-ts/ts-component-general-attributes.md) are supported.

## AlbumPickerComponent

AlbumPickerComponent({albumPickerOptions?: AlbumPickerOptions, onAlbumClick?: (albumInfo: AlbumInfo) => boolean, onEmptyAreaClick?: EmptyAreaClickCallback, albumPickerController?: AlbumPickerController })

The album picker component embedded in the UI of an application allows the application to access the albums in the user directory without any permission.

**Decorator:** @Component

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name                | Type                                                 | Mandatory | Description                             |
|--------------------|-----------------------------------------------------|-----|---------------------------------|
| albumPickerOptions | [AlbumPickerOptions](#albumpickeroptions)           | No   | **AlbumPicker** configuration. If this parameter is not passed, the default configuration is used.<br> **Atomic Service API:** Since API version 12, this API is supported in atomic services.              |
| onAlbumClick       | (albumInfo: [AlbumInfo](#albuminfo)) => boolean     | No   | Callback used to return the album information (**AlbumInfo**) when an album is selected by a user. The album information includes the URI and **albumName**. The app can use this callback to notify the photo picker component to refresh. If this parameter is not passed, the album selection event will not be listened for. The return value is meaningless and can be either **true** or **false**.<br> **Atomic Service API:** Since API version 12, this API is supported in atomic services.    |
| onEmptyAreaClick<sup>13+</sup>   | [EmptyAreaClickCallback](#emptyareaclickcallback13) | No   | Callback to be invoked when the blank area of the **AlbumPickerComponent** is tapped, which is used to notify the app of the tap. If this parameter is not passed, the tap event of the blank area will not be listened for.<br> **Atomic Service API:** Since API version 13, this API is supported in atomic services. |
| albumPickerController<sup>20+</sup>   | [AlbumPickerController](#albumpickercontroller20) | No   | A controller that enables apps to send data to the **AlbumPickerComponent**. The **AlbumPickerController** instance must be passed when the album selection component is created. If this parameter is not passed, the component cannot be controlled through the controller.<br> **Atomic Service API:** Since API version 20, this API is supported in atomic services. |

## AlbumPickerOptions

Represents the **AlbumPicker** configuration.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name            | Type | Read-Only| Optional | Description                                                         |
|----------------|-------|-----|-----|-------------------------------------------------------------|
| themeColorMode | [PickerColorMode](ohos-file-PhotoPickerComponent.md#pickercolormode) | No | Yes | Theme color of the album list. The options are **AUTO**, **Light**, and **Dark**. The default value is **AUTO**. <br> **Atomic Service API:** Since API version 12, this API is supported in atomic services. |
| filterType<sup>13+</sup> | [photoAccessHelper.PhotoViewMIMETypes](arkts-apis-photoAccessHelper-e.md#photoviewmimetypes) | No | Yes | Type of the filter. You can use it to display images, videos, or both. If this parameter is not specified, the album component displays all image and video resources.<br> **Atomic Service API:** Since API version 13, this API is supported in atomic services. |
| fontSize<sup>20+</sup> | number \| string | No | Yes | Font size. For details about the value range, see [fontSize](../apis-arkui/arkui-ts/ts-basic-components-text.md#fontsize). If this parameter is not set, the default font size is used. You can also dynamically set the font size using [AlbumPickerController](#albumpickercontroller20).setFontSize.<br> **Atomic Service API:** Since API version 20, this API is supported in atomic services. |

## EmptyAreaClickCallback<sup>13+</sup>

type EmptyAreaClickCallback = () => void

Called when the blank area of the **AlbumPickerComponent** is tapped.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

## AlbumInfo

Represents album information.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name | Type |Read-Only| Optional | Description   |
|------|------|-----|-----|---------|
| uri  | string | No| Yes | Album URI.|
| albumName  | string | No| Yes | Album name.|

## AlbumPickerController<sup>20+</sup>

A controller that enables applications to send data to the **AlbumPickerComponent**.

**Decorator:** @Observed

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

### setFontSize<sup>20+</sup>

setFontSize(fontSize: number | string): void

Sets the font size of the album list. The **albumPickerController** parameter needs to be passed when the album picker component is created.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

|  Name       | Type                                   | Mandatory | Description |
| ------------------------- | ------------------ | ----- | --------------- |
| fontSize | number \| string | Yes| Font size. For details about the value range, see [fontSize](../apis-arkui/arkui-ts/ts-basic-components-text.md#fontsize).|

## Example

```ts
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