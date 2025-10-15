# Multimedia Subsystem Changelog

## cl.multimedia.1 Changed the System Capability of the desiredAuxiliaryPictures Property in Image.ImageSource.DecodingOptionsForPicture

**Access Level**

Public API

**Reason for Change**

The system capability of **desiredAuxiliaryPictures** is inconsistent with that of **DecodingOptionsForPicture**, which affects the judgment of the system capability supported. Therefore, the system capability of **desiredAuxiliaryPictures** is changed from SystemCapability.Multimedia.Image.Core to SystemCapability.Multimedia.Image.ImageSource.

**Impact of the Change**

This change is a non-compatible change.

The system capability of the property is changed. The change does not affect the usage of the property.

Before change: The system capability of **DecodingOptionsForPicture** is SystemCapability.Multimedia.Image.Core.

After change: The system capability of **DecodingOptionsForPicture** is SystemCapability.Multimedia.Image.ImageSource.

**Start API Level**

13

**Change Since**

OpenHarmony 5.0.0.57

**Key API/Component Changes**

The following property in @ohos.multimedia.image are involved:

| API| API Description| Property| Property Description|
| -------- | -------- | -------- | -------- |
|image.ImageSource.DecodingOptionsForPicture|Describes the image decoding options.|desiredAuxiliaryPictures|Auxiliary picture type. By default, all auxiliary picture types are decoded.|


**Adaptation Guide**

The value of **SystemCapability** for a property in an API must be the same as that of the API. If the **canIUse()** API is called in your code to check whether the system capability required for the involved API is supported, change the system capability passed. Specifically, to check whether the device supports the capability for image source decoding and parsing, call **canIUse("SystemCapability.Multimedia.Image.ImageSource")**.

## cl.multimedia.2 Changed the Behavior of image.Component.OH_AuxiliaryPictureNative_SetInfo()

**Access Level**

Public API

**Reason for Change**

When **OH_AuxiliaryPictureNative_SetInfo** is called to set auxiliary image information, the size and pixel format in the auxiliary image information is synchronized to ImageInfo of the PixelMap. The size and pixel format should be verified to prevent out-of-bounds access to the PixelMap data.

**Impact of the Change**

This change is a non-compatible change.

Before change: When **OH_AuxiliaryPictureNative_SetInfo()** is called to set auxiliary image information, the pixel format passed is not verified.

After change: When **OH_AuxiliaryPictureNative_SetInfo()** is used to set auxiliary image information, the setting fails and error code 401 is returned if the number of bytes for storing pixels is increased. For example, if the API is called to set **pixelFormat** from RGBA_8888 to RGBA_F16, the error code is reported.

**Start API Level**

13

**Change Since**

OpenHarmony 5.0.0.57

**Key API/Component Changes**

| API Type| Header File| API| Start API Level|
|--|--|--|--|
| C API | picture_native.h | Image_ErrorCode OH_AuxiliaryPictureNative_SetInfo(OH_AuxiliaryPictureNative *auxiliaryPicture, OH_AuxiliaryPictureInfo *info) | 13 |

**Adaptation Guide**

If the number of bytes for storing pixels is increased when setting auxiliary image information, the setting fails and error code 401 is returned.

```c++
#include <hilog/log.h>
#include <multimedia/image_framework/image/image_native.h>
#include <multimedia/image_framework/image/image_packer_native.h>
#include <multimedia/image_framework/image/image_source_native.h>
#include <multimedia/image_framework/image/picture_native.h>
Image_ErrorCode SetAuxiliaryPictureInfoTest() {
    size_t filePathSize = 1024;
    OH_ImageSourceNative* imageSource = nullptr;
    Image_ErrorCode image_ErrorCode = OH_ImageSourceNative_CreateFromUri("test.jpg", filePathSize, &imageSource);
    if (image_ErrorCode != Image_ErrorCode::IMAGE_SUCCESS || imageSource == nullptr) {
        OH_LOG_ERROR(LOG_APP, "OH_ImageSourceNative_CreateFromUri failed.");
    }
    OH_DecodingOptionsForPicture *opts = nullptr;
    OH_DecodingOptionsForPicture_Create(&opts);
    OH_PictureNative *picture = nullptr;
    image_ErrorCode = OH_ImageSourceNative_CreatePicture(imageSource, opts, &picture);
    OH_ImageSourceNative_Release(imageSource);
    OH_DecodingOptionsForPicture_Release(opts);
    if (image_ErrorCode != Image_ErrorCode::IMAGE_SUCCESS || picture == nullptr) {
        OH_LOG_ERROR(LOG_APP, "OH_ImageSourceNative_CreatePicture failed. image_ErrorCode=%{public}d", image_ErrorCode);
    }
    OH_AuxiliaryPictureNative *auxiliaryPicture = nullptr;
    image_ErrorCode = OH_PictureNative_GetAuxiliaryPicture(
        picture, Image_AuxiliaryPictureType::AUXILIARY_PICTURE_TYPE_FRAGMENT_MAP, &auxiliaryPicture);
    if (image_ErrorCode != Image_ErrorCode::IMAGE_SUCCESS || auxiliaryPicture == nullptr) {
       OH_LOG_ERROR(LOG_APP, "OH_PictureNative_GetAuxiliaryPicture failed. image_ErrorCode=%{public}d", image_ErrorCode);
    }
    OH_AuxiliaryPictureInfo *auxInfo = nullptr;
    image_ErrorCode = OH_AuxiliaryPictureNative_GetInfo(auxiliaryPicture, &auxInfo);
    PIXEL_FORMAT newPixelFormat = PIXEL_FORMAT_RGBA_F16;
    OH_AuxiliaryPictureInfo_SetPixelFormat(auxInfo, newPixelFormat);
    image_ErrorCode = OH_AuxiliaryPictureNative_SetInfo(auxiliaryPicture, auxInfo);
    if (image_ErrorCode != Image_ErrorCode::IMAGE_SUCCESS || auxInfo == nullptr) {
       OH_LOG_ERROR(LOG_APP, "OH_AuxiliaryPictureNative_SetInfo failed. image_ErrorCode=%{public}d", image_ErrorCode);
    }
    OH_AuxiliaryPictureInfo_Release(auxInfo);
    OH_AuxiliaryPictureNative_Release(auxiliaryPicture);
    return IMAGE_SUCCESS;
}
```

## cl.multimedia.3 Changed the Behavior of image.Component.setAuxiliaryPictureInfo

**Access Level**

Public API

**Reason for Change**

When **setAuxiliaryPictureInfo** is called to set auxiliary image information, the size and pixel format in the auxiliary image information is synchronized to ImageInfo of the PixelMap. The size and pixel format should be verified to prevent out-of-bounds access to the PixelMap data.

**Impact of the Change**

This change is a non-compatible change.

Before change: When **setAuxiliaryPictureInfo()** is called to set auxiliary image information, the pixel format passed is not verified.

After change: When **setAuxiliaryPictureInfo()** is used to set auxiliary image information, the setting fails and error code 401 is returned if the number of bytes for storing pixels is increased. For example, if the API is called to set **pixelFormat** from RGBA_8888 to RGBA_F16, the error code is reported.

**Start API Level**

13

**Change Since**

OpenHarmony 5.0.0.57

**Key API/Component Changes**

| API Type| d.ts File| API| Start API Level|
|--|--|--|--|
| ArkTS API | @ohos.multimedia.image.d.ts | setAuxiliaryPictureInfo(info: AuxiliaryPictureInfo): void | 13 |

**Adaptation Guide**

If the number of bytes for storing pixels is increased when setting auxiliary image information, the setting fails and error code 401 is returned.

```ts
import { image } from '@kit.ImageKit';
import { colorSpaceManager } from '@kit.ArkGraphics2D';

async function setAuxiliaryPitcutreInfo() {
  const array: ArrayBuffer = new ArrayBuffer(100);
  let imageSource: image.ImageSource = image.createImageSource(array);
  let options: image.DecodingOptionsForPicture = {
    desiredAuxiliaryPictures: [image.AuxiliaryPictureType.FRAGMENT_MAP]
  };
  try {
    let picture: image.Picture = await imageSource.createPicture(options);
    let auxiliaryPicture = picture.getAuxiliaryPicture(image.AuxiliaryPictureType.FRAGMENT_MAP);
    let originInfo = auxiliaryPicture?.getAuxiliaryPictureInfo();
    console.info("CreatePicture", 'originInfo = ' + JSON.stringify(originInfo));
    let changedInfo: image.AuxiliaryPictureInfo = {
      auxiliaryPictureType: image.AuxiliaryPictureType.FRAGMENT_MAP,
      size: { height: 410, width: 3072 },
      rowStride: 3072 * 8,
      pixelFormat: image.PixelMapFormat.RGBA_F16,
      colorSpace: colorSpaceManager.create(colorSpaceManager.ColorSpace.DCI_P3),
    };
    try {
      auxiliaryPicture?.setAuxiliaryPictureInfo(changedInfo);
      console.info("CreatePicture", `changedInfo us ${changedInfo}`);
    } catch (error) {
      console.error("CreatePicture", `setAuxiliaryPictureInfo, error.code is ${error.code}, error.message is ${error.message}`);
    }
  } catch (err) {
    console.error("CreatePicture", ' decode Picture failed !!!');
  }
}
```
