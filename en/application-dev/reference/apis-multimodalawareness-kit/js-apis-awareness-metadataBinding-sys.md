# @ohos.multimodalAwareness.metadataBinding (Metadata Binding) (System API)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: Msdp-->
<!--Owner: @codexu62-->
<!--Designer: @yuxiaoyang-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=c1a62f522b0781bacc654afa2e6ddc8bc5fd9dfc translatedAt=2026-09-14T01:56:35.662Z pushedAt=2026-09-14T10:03:33.574Z -->

This module provides metadata binding capability invocation for embedding metadata into images and parsing metadata from images to implement information transfer. It applies to scenarios where metadata needs to be stored in and transferred through images, such as anti-counterfeiting and copyright protection, providing you with a flexible mechanism for embedding and parsing information.

> **NOTE**
>
> The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.


## Modules to Import
```ts
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
```

## metadataBinding.encodeImage
encodeImage(srcImage: image.PixelMap, metadata: string): Promise&lt;image.PixelMap&gt;

Embeds information into an image. This API embeds metadata into the image using a specific encoding algorithm. The encoding process has minimal impact on the visual presentation of the image, and the embedded information can be parsed through the **decodeImage** API. It can be used in scenarios such as anti-counterfeiting and copyright protection. This API uses a promise to return the result asynchronously.

**System capability**: SystemCapability.MultimodalAwareness.metadataBinding

**System API**: This is a system API.

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| srcImage     | [PixelMap](https://developer.huawei.com/consumer/en/doc/harmonyos-references/arkts-apis-image-pixelmap)                        | Yes   | Original image to be encoded, used to embed metadata.     |
| metadata     | string | Yes | Information to be embedded. The string encoding format is recommended to be UTF-8, the length should not exceed 128 bytes, and non-printable characters should be avoided. |

**Return value**

  | Type                          | Description        |
  | ---------------------------- | ---------- |
  | Promise&lt;image.PixelMap&gt; | Promise object, which is used to return the image with encoded metadata.|

**Error Code**

For details about the error codes, see [Metadata Binding Error Codes](errorcode-metadataBinding.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
|   202    | Permission check failed. A non-system application uses the system API. |
| 32100001 | Internal handling failed. |
| 32100002 | Encode process fail. Possible causes: 1. Image processing error; 2. Channel coding error. |

**Example**

```ts
import { image } from '@kit.ImageKit';
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';

let encodedImage: image.PixelMap | undefined = undefined;
let metadata: string = '';
// Obtain a valid PixelMap object for srcImage through the APIs in image.
let srcImage: image.PixelMap | undefined = undefined;
metadataBinding.encodeImage(srcImage, metadata).then((pixelMap: image.PixelMap) => {
  encodedImage = pixelMap;
}).catch((error: BusinessError) => {
  console.error(`Failed to encode image. Code: ${error.code}, message: ${error.message}`);
});
```

## metadataBinding.decodeImage
decodeImage(encodedImage: image.PixelMap): Promise&lt;string&gt;

Parses the information carried in an image. This API extracts the embedded metadata from the image using the corresponding decoding algorithm. This API uses a promise to return the result asynchronously.

**System capability**: SystemCapability.MultimodalAwareness.metadataBinding

**System API**: This is a system API.

**Parameters** 

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| encodedImage     | [PixelMap](https://developer.huawei.com/consumer/en/doc/harmonyos-references/arkts-apis-image-pixelmap)                           | Yes   | Image carrying information, which must be an encoded image processed by the **encodeImage** API. |

**Return value**

  | Type                          | Description        |
  | ---------------------------- | ---------- |
  | Promise&lt;string&gt; | Promise object, which is used to return the encoded metadata of the image.|

**Error codes** 

For details about the error codes, see [Metadata Binding Error Codes](errorcode-metadataBinding.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
|   202    | Permission check failed. A non-system application uses the system API. |
| 32100001 | Internal handling failed. |
| 32100003 | Decode process fail. Possible causes: 1. Image is not an encoded Image; 2. Image destroyed, decoding failed. |

**Example** 
```ts
import { image } from '@kit.ImageKit';
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';

// encodedImage must be obtained from an image processed by the encodeImage API.
let encodedImage: image.PixelMap | undefined = undefined;
let captureMetadata: string = '';
metadataBinding.decodeImage(encodedImage).then((metadata: string) => {
  // Save the metadata parsed from the image to the captureMetadata variable for later use.
  captureMetadata = metadata;
}).catch((error: BusinessError) => {
  console.error(`Failed to decode image. Code: ${error.code}, message: ${error.message}`);
}); 
```

## metadataBinding.notifyMetadataBindingEvent
notifyMetadataBindingEvent(bundleName: string): Promise&lt;string&gt;

Pushes the metadata to be embedded to the application or service that calls the encoding API. The system pushes the information to the application with the specified bundle name and returns the applink information of the current page for subsequent encoding. This API uses a promise to return the result asynchronously.

**System capability**: SystemCapability.MultimodalAwareness.metadataBinding

**System API**: This is a system API.

**Parameters** 

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
|bundleName|string|Yes|Application bundle name, which must be the bundle name of an installed application.|

**Return value**

| Type                         | Description       |
| ---------------------------- | ---------- |
| Promise&lt;string&gt; | Promise used to return the appLink information of the current page. |

**Error Code**

For details about the error codes, see [Metadata Binding Error Codes](errorcode-metadataBinding.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
|   202    | Permission check failed. A non-system application uses the system API. |
| 32100001 | Internal handling failed. |

**Example**

```ts
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';

// bundleName must be the bundle name of an installed application.
let bundleName: string = '';
metadataBinding.notifyMetadataBindingEvent(bundleName).then((appLink:string) => {
  console.info('notify metadata:' + appLink);
}).catch((error: BusinessError) => {
  console.error(`Failed to notify metadata. Code: ${error.code}, message: ${error.message}`);
});
```