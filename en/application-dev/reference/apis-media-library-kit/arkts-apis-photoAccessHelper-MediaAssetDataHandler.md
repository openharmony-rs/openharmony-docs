# Interface (MediaAssetDataHandler)
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=6a96f2b8f99f158608ec5045488b853b4cc6044f translatedAt=2026-11-03T07:03:42.640Z pushedAt=2026-11-04T03:11:19.955Z nl=1 -->

The media asset data handler interface, which allows customizing media asset processing logic by implementing the onDataPrepared method.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 11.

## Modules to Import

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## onDataPrepared<sup>11+</sup>

onDataPrepared(data: T, map?: Map<string, string>): void

Called when the requested media asset is ready. If an error occurs, **data** returned by the callback is **undefined**. Each media asset request corresponds to a callback.

Information returned by **map**:

| Map Key | Description|
|----------|-------|
| 'quality'  | Image quality. The value **high** means high quality, and **low** means poor quality.|

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name | Type| Mandatory| Description                                                                           |
|------|---| ---- |-------------------------------------------------------------------------------|
| data | T | Yes | Data of the prepared image/video asset.<br>If the asset fails to be prepared, this parameter is undefined.<br>Supports four data types: ArrayBuffer, [ImageSource](../apis-image-kit/arkts-apis-image-ImageSource.md), [MovingPhoto](arkts-apis-photoAccessHelper-MovingPhoto.md), and boolean.<br>When this parameter is of the boolean type, true indicates success, and false indicates failure. |
| map<sup>12+</sup> | Map<string, string> | No  | Additional information about the image asset, such as the image quality. Currently, only **quality** is supported.|

**Example**

```ts
import { image } from '@kit.ImageKit';

class MediaHandler implements photoAccessHelper.MediaAssetDataHandler<image.ImageSource> {
  onDataPrepared = (data: image.ImageSource, map: Map<string, string>) => {
    if (data === undefined) {
      console.error('Error occurred when preparing data');
      return;
    }
    // Customize the processing logic for ImageSource.
    console.info('on image data prepared, photo quality is ' + map.get('quality'));
  }
}

class MediaDataHandler implements photoAccessHelper.MediaAssetDataHandler<ArrayBuffer> {
  onDataPrepared = (data: ArrayBuffer, map: Map<string, string>) => {
    if (data === undefined) {
      console.error('Error occurred when preparing data');
      return;
    }
    // Customize the processing logic for ArrayBuffer.
    console.info('on image data prepared, photo quality is ' + map.get('quality'));
  }
}

class MovingPhotoHandler implements photoAccessHelper.MediaAssetDataHandler<photoAccessHelper.MovingPhoto> {
  onDataPrepared = (data: photoAccessHelper.MovingPhoto, map: Map<string, string>) => {
    if (data === undefined) {
      console.error('Error occurred when preparing data');
      return;
    }
    // Customize the processing logic for MovingPhoto.
    console.info('on image data prepared, photo quality is ' + map.get('quality'));
  }
}
```
