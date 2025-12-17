# Multimedia Subsystem Changelog

## cl.multimedia.1 HEIF Format Change for Image APIs

**Access Level**

Public API

**Reason for Change**

During HEIF encoding with the camera, the encoding fails with the standard-defined **image/heic** parameter. The current version of Image defines the format parameter as **image/heif**, which does not comply with the standard definition. To improve adherence to standards, the **mimeType** parameter for HEIF images is changed to **image/heic**.

**Impact of the Change**

1.  The parameter type for the HEIF format in **OH_PackingOptions_SetMimeType()** is changed. This change involves application adaptation.
      Before change: The **mimeType** parameter for HEIF images is **image/heif**.
      After change: The **mimeType** parameter for HEIF images is **image/heic**.
     
 2. The return value type for the HEIF format in **OH_PackingOptions_GetMimeType()** is changed. This change involves application adaptation.
      Before change: The **mimeType** parameter for HEIF images is **image/heif**.
      After change: The **mimeType** parameter for HEIF images is **image/heic**.
      
 3. The return value type of the **supportedFormats** API provided by the ImageSource instance for querying the decoding formats supported by the device has changed. This change involves application adaptation.
     Before change: The return value of the decoding type supported by the device for HEIF images is **image/heif**.
     After change: The return value of the decoding type supported by the device for HEIF images is **image/heic**.
     
 4. The return value type of the **supportedFormats** API provided by the ImagePacker instance for querying the encoding formats supported by the device has changed. This change involves application adaptation.
     Before change: The return value of the encoding type supported by the device for HEIF images is **image/heif**.
     After change: The return value of the encoding type supported by the device for HEIF images is **image/heic**.
     
 5. The HEIF encoding parameters in the image.PackingOption struct are changed. This change does not involve application adaptation.
     Before change: The **mimeType** parameter for HEIF encoding is **image/heif**.
     After change: The **mimeType** parameter for HEIF encoding is **image/heic**.
     
 6. The HEIF encoding parameters in the OH_PackingOptions struct are changed. This change does not involve application adaptation.
     Before change: The **mimeType** parameter for HEIF encoding is **image/heif**.
     After change: The **mimeType** parameter for HEIF encoding is **image/heic**.

**Start API Level**

10

**Change Since**

OpenHarmony 5.0.0.53

**Key API/Component Changes**

| API Type| d.ts File/Header File| API| Start API Level|
|--|--|--|--|
| C API | image_packer_native.h | Image_ErrorCode OH_PackingOptions_SetMimeType(OH_PackingOptions *options, Image_MimeType *format) | 12 |
| C API | image_packer_native.h | Image_ErrorCode OH_PackingOptions_GetMimeType(OH_PackingOptions *options, Image_MimeType *format) | 12 |
| ArkTS API | @ohos.multimedia.image.d.ts |  imagePacker.supportedFormats: Array\<string> | 10 |
| ArkTS API | @ohos.multimedia.image.d.ts |  imageSource.supportedFormats: Array\<string> | 10 |
| ArkTS API | @ohos.multimedia.image.d.ts | image.PackingOption | 11 |
| C API | image_packer_native.h | struct OH_PackingOptions | 12 |

**Adaptation Guide**

1. When **OH_PackingOptions_SetMimeType(OH_PackingOptions *options, Image_MimeType *format)** is called to set **mimeType** for HEIF images, **format** must be **image/heic**.

2. When **OH_PackingOptions_GetMimeType(OH_PackingOptions *options, Image_MimeType *format)** is called to obtain **mimeType** of HEIF images, **format** in the return value is **image/heic**. You need to review the sample project of the application and modify the format based on service requirements.

3. When supportedFormats of ImageSource is used to obtain the decoding type of a device, the calling behavior remains unchanged. If the device supports HEIF, the return value is changed from **image/heif** to **image/heic**.

4. When supportedFormats of ImagePacker is used to obtain the encoding type of a device, the calling behavior remains unchanged. If the device supports HEIF, the return value is changed from **image/heif** to **image/heic**.

5. When **image.PackingOption** is used to encode HEIF images, the **image/heif** or **image/heic** type can be used.

6. When **OH_PackingOptions** is used to encode HEIF images, the **image/heif** or **image/heic** type can be used.
