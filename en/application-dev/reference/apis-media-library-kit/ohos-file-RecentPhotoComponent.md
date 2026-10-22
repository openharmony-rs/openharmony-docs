# @ohos.file.RecentPhotoComponent (RecentPhotoComponent)
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xuchangda-->
<!--Designer: @guxinggang-->
<!--Tester: @wangbeibei-->
<!--Adviser: @w_Machine_cc-->

**RecentPhotoComponent** is a UI component that allows an application to access the latest photo/video in the user directory without the required permission. This component grants the application only the read permission. This component is applicable to scenarios where the latest photos or videos need to be quickly displayed or selected, such as sending photos in a chat app or quickly sharing photos in a social app.

Note that the recent photo component does not support nesting. Additionally, prevent overlaying components with the **overlay** attribute or of higher levels on top the component, as this will prevent it from receiving gesture events.

> **NOTE**
>
> - This component is supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This component does not support [same-layer rendering](../../../application-dev/web/web-same-layer.md).

## Modules to Import

```ts
// In versions earlier than API version 23, you need to use the "import { api1, api2, ... } from '@ohos.file.RecentPhotoComponent'" import mode.
import {
  RecentPhotoComponent, RecentPhotoOptions, RecentPhotoCheckResultCallback, RecentPhotoInfo, RecentPhotoCheckInfoCallback,
  RecentPhotoClickCallback, PhotoSource
} from '@kit.MediaLibraryKit';
```

## Properties

The [universal properties](../apis-arkui/arkui-ts/ts-component-general-attributes.md) are supported.

## RecentPhotoComponent

RecentPhotoComponent({ recentPhotoOptions?: RecentPhotoOptions, onRecentPhotoCheckResult?: RecentPhotoCheckResultCallback, onRecentPhotoClick: RecentPhotoClickCallback, onRecentPhotoCheckInfo?: RecentPhotoCheckInfoCallback, })

Allows an app to access the latest photo or video file in the public directory The app can access media assets based on parameters without requesting the permissions.

**Decorator**: @Component

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name                      | Type                                                               | Mandatory| Description                      |
|--------------------------|-------------------------------------------------------------------|------|----------------------------|
| recentPhotoOptions       | [RecentPhotoOptions](#recentphotooptions)                         | No | Configuration of the recent image or video. Set this parameter when you need to customize the display configuration (such as the time segment, file type, and source) of the recent image or video component. If this parameter is not set, the default configuration is used to display the recent image or video.<br> **Atomic service API**: This API can be used in atomic services since API version 12.               |
| onRecentPhotoCheckResult | [RecentPhotoCheckResultCallback](#recentphotocheckresultcallback) | No | Callback used to return the query result of the recent image or video. Configure this callback to check whether a recent image or video exists. If this parameter is not set, the component can still be displayed properly, but the app cannot obtain the existence status of the recent image or video.<br> **Atomic service API**: This API can be used in atomic services since API version 12.             |
| onRecentPhotoClick       | [RecentPhotoClickCallback](#recentphotoclickcallback)             | Yes | Callback to be invoked when the recent image or video is selected.<br> **Atomic service API**: This API can be used in atomic services since API version 12.               |
| onRecentPhotoCheckInfo<sup>13+</sup>   | [RecentPhotoCheckInfoCallback](#recentphotocheckinfocallback13)   | No | Callback used to return information about the recent image or video obtained. Configure this callback to check whether a recent image or video exists and obtain its details. If this parameter is not set, the component can still be displayed properly, but the app cannot obtain the image or video details.<br> **Atomic service API**: This API can be used in atomic services since API version 13.|

## RecentPhotoOptions

Represents the configuration of the recent image or video.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name                   | Type                                                                                     | Read-Only| Optional | Description  |
|-------------------------|-----------------------------------------------------------------------------------------|-------|-------|--------|
| period                  | number                                                                                  | No| Yes   | Time period for displaying the latest photo or video sorted by creation time, in seconds. The value range is (0, 86400]. The longest duration you can set is 1 day (86400s).<br>If the value is less than or equal to 0, greater than 86400, or not set, the latest photos or videos within one day are displayed by default. If there is no photo or video in the specified period, the component is not displayed.<br> **Note:**<br>When **isAutoRefreshSupported** is set to **true**, the **period** field becomes invalid.<br> **Atomic service API**: This API can be used in atomic services since API version 12.|
| MIMEType                | [photoAccessHelper.PhotoViewMIMETypes](arkts-apis-photoAccessHelper-e.md#photoviewmimetypes) | No   | Yes| Types of the file displayed. The options include **IMAGE_TYPE** (only images are displayed), **VIDEO_TYPE** (only videos are displayed), and **IMAGE_VIDEO_TYPE** (both images and videos are displayed). The default value is **IMAGE_VIDEO_TYPE**.<br> **Atomic service API**: This API can be used in atomic services since API version 12.                        |
| photoSource             | [PhotoSource](#photosource)                                                             | No   | Yes| Source of the recent photo or video, for example, image or video taken by the camera or screenshot. By default, the source is not restricted.<br>**Note:** This field is still valid when **isAutoRefreshSupported** is set to **true**.<br> **Atomic service API**: This API can be used in atomic services since API version 12.                              |
| isAutoRefreshSupported<sup>20+</sup>  | boolean                                                                                 | No   | Yes| Whether the **RecentPhotoComponent** automatically refreshes when there are changes (including additions, deletions, or modifications) to the recent photos or videos that meet the requirements.<br>If the component's originally displayed photo or video is deleted and there are no other photos or videos that meet the requirements, a placeholder is displayed and the component does not automatically close. The placeholder color mode can be configured using **colorMode**.<br>The default value is **false**, indicating that automatic refresh is not supported.<br>If this parameter is set to **true**, all photos or videos that meet the filter criteria are displayed. This parameters is still specified by **photoSource** and **MIMEType**, but not by **period**.<br>The **period** field becomes invalid.<br> **Note:** If automatic refresh is enabled, media library changes are listened for. It is recommended that this function be used in scenarios where real-time updates are required to avoid frequent refreshes that may affect performance.<br> **Atomic service API:** This API can be used in atomic services since API version 20.|
| colorMode<sup>20+</sup>               | [PickerColorMode](ohos-file-PhotoPickerComponent.md#pickercolormode)                                                      | No   | Yes| Color mode of the placeholder.<br>This setting is used when **isAutoRefreshSupported** is set to **true** and no recent photo or video meets the requirements, showing a placeholder instead. The **colorMode** field takes effect.<br>By default, it follows the system's dark/light color mode.<br> **Atomic service API:** This API can be used in atomic services since API version 20.|

## RecentPhotoInfo<sup>13+</sup>

Represents information about the recent image or video.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name        | Type    | Read-Only| Optional | Description                                                       |
|------------|--------|-------|-------|-----------------------------------------------------------|
| dateTaken  | number | No| Yes   | Time when the recent photo or video is taken, in ms. The value is the number of milliseconds elapsed since the Unix epoch (00:00:00 UTC on January 1, 1970).                    |
| identifier | string | No| Yes   | Hash value of the name of the recent photo or video, which is used to help the application determine whether the image or video to be displayed is the same as the one displayed before.|

## RecentPhotoCheckResultCallback

type RecentPhotoCheckResultCallback = (recentPhotoExists: boolean) => void

Called to return the query result of the recent image or video.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| recentPhotoExists | boolean | Yes| Whether the recent image or video exists. **true** if it exists, and **false** otherwise.|

## RecentPhotoClickCallback

type RecentPhotoClickCallback = (recentPhotoInfo: BaseItemInfo) => boolean

Describes the callback invoked when a user taps the recent photo component. The return value is meaningless and can be either **true** or **false**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| recentPhotoInfo | [BaseItemInfo](ohos-file-PhotoPickerComponent.md#baseiteminfo) | Yes| Information about the recent image or video.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Processing result of the recent image or video. The value **true** means that the processing is complete.|

## RecentPhotoCheckInfoCallback<sup>13+</sup>

type RecentPhotoCheckInfoCallback = (recentPhotoExists: boolean, info: RecentPhotoInfo) => void

Called to return whether the recent image or video exists and the information about it.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name              | Type                                   | Mandatory| Description         |
|-------------------|---------------------------------------| -------- |-------------|
| recentPhotoExists | boolean                               | Yes| Whether the recent image or video exists. **true** if it exists, and **false** otherwise.|
| info              | [RecentPhotoInfo](#recentphotoinfo13) | Yes| Information about the recent image or video.  |

## PhotoSource

Enumerates the sources of the image or video data.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name               | Value  | Description                                                                                                                |
|-------------------|-----|--------------------------------------------------------------------------------------------------------------------|
| ALL | 0   | Image or video from all sources.|
| CAMERA | 1   | Image or video taken by the camera.|
| SCREENSHOT | 2   | Screenshot or screen capture video.|

## Example

```ts
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
      console.info('The photo exists.');
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