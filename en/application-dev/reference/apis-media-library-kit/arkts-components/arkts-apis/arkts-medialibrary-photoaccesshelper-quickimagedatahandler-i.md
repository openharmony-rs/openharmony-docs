# QuickImageDataHandler

QuickImageDataHandler is a media asset handler used to customize the media asset processing logic in **onDataPrepared**.

**Since:** 13

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## onDataPrepared

```TypeScript
onDataPrepared(data: T, imageSource: image.ImageSource, map: Map<string, string>): void
```

Called when the requested image is ready. If an error occurs, **data** returned by the callback is **undefined**.

Information returned by **map**:

| Map Key | **Description**|  
|----------|-------|  
| 'quality' | Image quality. The value **high** means high quality, and **low** means poor quality.|

**Since:** 13

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | T | Yes | Data of the image asset that is ready. It is of the generic type and supports the [Picture](../../apis-image-kit/arkts-apis/arkts-image-image-picture-i.md) type. |
| imageSource | [image.ImageSource](../../apis-image-kit/arkts-apis/arkts-image-image-imagesource-i.md) | Yes | Data of the image asset that is ready. |
| map | Map&lt;string, string&gt; | Yes | Additional information about the image asset, such as the image quality. Currently, only **quality** is supported. |
