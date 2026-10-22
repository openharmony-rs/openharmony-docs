# photo_native.h

## 概述

声明相机照片的概念。

**库：** libohcamera.so

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 12

**相关模块：** [OH_Camera](capi-oh-camera.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_PhotoNative](capi-oh-camera-oh-photonative.md) | OH_PhotoNative | 相机照片对象。<br> 全质量图对象。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [Camera_ErrorCode OH_PhotoNative_GetMainImage(OH_PhotoNative* photo, OH_ImageNative** mainImage)](#oh_photonative_getmainimage) | 获取全质量图。 |
| [Camera_ErrorCode OH_PhotoNative_GetUncompressedImage(OH_PhotoNative* photo, OH_PictureNative** picture)](#oh_photonative_getuncompressedimage) | 获取非压缩图片。 |
| [Camera_ErrorCode OH_PhotoNative_GetAuxiliaryImage(const OH_PhotoNative* photo, OH_Camera_AuxiliaryPhotoType type, OH_ImageNative** outImage)](#oh_photonative_getauxiliaryimage) | 获取指定类型的辅助图。 <br> <br>使用场景：使用本接口前需先通过OH_PhotoOutput_SetAutoAuxiliaryPhotosDeliveryEnabled() 开启指定类型辅助图的自动回传功能，拍照获得的OH_PhotoNative 对象中才会包含辅助图，并通过本接口按类型获取辅助图，用于后续分析处理。支持的辅助图类型及各自用途请参考 [OH_Camera_AuxiliaryPhotoType](capi-camera-h.md#oh_camera_auxiliaryphototype)。 |
| [Camera_ErrorCode OH_PhotoNative_GetUncompressedAuxiliaryImage(const OH_PhotoNative* photo, OH_Camera_AuxiliaryPhotoType type, OH_PictureNative** outImage)](#oh_photonative_getuncompressedauxiliaryimage) | 获取指定类型的未压缩辅助图。 <br> <br>使用场景：使用本接口前需先通过OH_PhotoOutput_SetAutoAuxiliaryPhotosDeliveryEnabled() 开启指定类型辅助图的自动回传功能，拍照获得的OH_PhotoNative 对象中才会包含辅助图，并通过本接口按类型获取辅助图，用于后续分析处理。支持的辅助图类型及各自用途请参考 [OH_Camera_AuxiliaryPhotoType](capi-camera-h.md#oh_camera_auxiliaryphototype)。 |
| [Camera_ErrorCode OH_PhotoNative_Release(OH_PhotoNative* photo)](#oh_photonative_release) | 释放全质量图实例。 |
| [Camera_ErrorCode OH_PhotoNative_ReleasePicture(OH_PictureNative* picture)](#oh_photonative_releasepicture) | 释放OH_PictureNative实例。 |
| [Camera_ErrorCode OH_PhotoNative_ReleaseImage(OH_ImageNative* image)](#oh_photonative_releaseimage) | 释放OH_ImageNative实例。 |

## 函数说明

### OH_PhotoNative_GetMainImage()

```c
Camera_ErrorCode OH_PhotoNative_GetMainImage(OH_PhotoNative* photo, OH_ImageNative** mainImage)
```

**描述：**

获取全质量图。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PhotoNative](capi-oh-camera-oh-photonative.md)* photo | OH_PhotoNative实例。 |
| [OH_ImageNative](../../apis-image-kit/c-apis/capi-image-nativemodule-oh-imagenative.md)** mainImage | 用于获取全质量图的OH_ImageNative。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功。<br>CAMERA_INVALID_ARGUMENT：参数丢失或参数类型不正确。 |

### OH_PhotoNative_GetUncompressedImage()

```c
Camera_ErrorCode OH_PhotoNative_GetUncompressedImage(OH_PhotoNative* photo, OH_PictureNative** picture)
```

**描述：**

获取非压缩图片。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PhotoNative](capi-oh-camera-oh-photonative.md)* photo | OH_PhotoNative实例。 |
| [OH_PictureNative](../../apis-image-kit/c-apis/capi-image-nativemodule-oh-picturenative.md)** picture | 用于获取非压缩图片的OH_PictureNative。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功。<br>CAMERA_INVALID_ARGUMENT：参数丢失或参数类型不正确。 |

### OH_PhotoNative_GetAuxiliaryImage()

```c
Camera_ErrorCode OH_PhotoNative_GetAuxiliaryImage(const OH_PhotoNative* photo, OH_Camera_AuxiliaryPhotoType type, OH_ImageNative** outImage)
```

**描述：**

获取指定类型的辅助图。 <br> <br>使用场景：使用本接口前需先通过OH_PhotoOutput_SetAutoAuxiliaryPhotosDeliveryEnabled() 开启指定类型辅助图的自动回传功能，拍照获得的OH_PhotoNative 对象中才会包含辅助图，并通过本接口按类型获取辅助图，用于后续分析处理。支持的辅助图类型及各自用途请参考 [OH_Camera_AuxiliaryPhotoType](capi-camera-h.md#oh_camera_auxiliaryphototype)。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 26.0.1

**资源释放：** OH_PhotoNative_ReleaseImage {outImage}

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_PhotoNative](capi-oh-camera-oh-photonative.md)* photo | 指向OH_PhotoNative实例的指针。 |
| [OH_Camera_AuxiliaryPhotoType](capi-camera-h.md#oh_camera_auxiliaryphototype) type | 辅助图类型。 |
| [OH_ImageNative](../../apis-image-kit/c-apis/capi-image-nativemodule-oh-imagenative.md)** outImage | 指向OH_ImageNative实例的双重指针，用于接收获取的辅助图。调用成功时，指向有效的辅助图实例；调用失败时，该参数返回NULL。 该实例由调用方管理，使用完成后应调用OH_PhotoNative_ReleaseImage()释放。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | <ul> <br><li>CAMERA_OK: 操作成功。</li> <br><li>CAMERA_INVALID_ARGUMENT: 缺少参数或参数类型不正确。</li> <br><li>CAMERA_ERROR_PARAM_OUT_OF_RANGE: 参数超出范围。</li> <br></ul> |

### OH_PhotoNative_GetUncompressedAuxiliaryImage()

```c
Camera_ErrorCode OH_PhotoNative_GetUncompressedAuxiliaryImage(const OH_PhotoNative* photo, OH_Camera_AuxiliaryPhotoType type, OH_PictureNative** outImage)
```

**描述：**

获取指定类型的未压缩辅助图。 <br> <br>使用场景：使用本接口前需先通过OH_PhotoOutput_SetAutoAuxiliaryPhotosDeliveryEnabled() 开启指定类型辅助图的自动回传功能，拍照获得的OH_PhotoNative 对象中才会包含辅助图，并通过本接口按类型获取辅助图，用于后续分析处理。支持的辅助图类型及各自用途请参考 [OH_Camera_AuxiliaryPhotoType](capi-camera-h.md#oh_camera_auxiliaryphototype)。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 26.0.1

**资源释放：** OH_PhotoNative_ReleasePicture {outImage}

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_PhotoNative](capi-oh-camera-oh-photonative.md)* photo | 指向OH_PhotoNative实例的指针。 |
| [OH_Camera_AuxiliaryPhotoType](capi-camera-h.md#oh_camera_auxiliaryphototype) type | 辅助图类型。 |
| [OH_PictureNative](../../apis-image-kit/c-apis/capi-image-nativemodule-oh-picturenative.md)** outImage | 指向OH_PictureNative实例的双重指针，用于接收获取的未压缩辅助图。调用成功时，指向有效的辅助图实例；调用失败时，该参数返回NULL。 该实例由调用方管理，使用完成后应调用OH_PhotoNative_ReleasePicture()释放。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | <ul> <br><li>CAMERA_OK: 操作成功。</li> <br><li>CAMERA_INVALID_ARGUMENT: 缺少参数或参数类型不正确。</li> <br><li>CAMERA_ERROR_PARAM_OUT_OF_RANGE: 参数超出范围。</li> <br></ul> |

### OH_PhotoNative_Release()

```c
Camera_ErrorCode OH_PhotoNative_Release(OH_PhotoNative* photo)
```

**描述：**

释放全质量图实例。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PhotoNative](capi-oh-camera-oh-photonative.md)* photo | 要被释放的OH_PhotoNative实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功。<br>CAMERA_INVALID_ARGUMENT：参数丢失或参数类型不正确。 |

### OH_PhotoNative_ReleasePicture()

```c
Camera_ErrorCode OH_PhotoNative_ReleasePicture(OH_PictureNative* picture)
```

**描述：**

释放OH_PictureNative实例。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureNative](../../apis-image-kit/c-apis/capi-image-nativemodule-oh-picturenative.md)* picture | 指向要释放的OH_PictureNative实例的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | <ul> <br><li>CAMERA_OK: 操作成功。</li> <br><li>CAMERA_INVALID_ARGUMENT: 缺少参数或参数类型不正确。</li> <br></ul> |

### OH_PhotoNative_ReleaseImage()

```c
Camera_ErrorCode OH_PhotoNative_ReleaseImage(OH_ImageNative* image)
```

**描述：**

释放OH_ImageNative实例。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageNative](../../apis-image-kit/c-apis/capi-image-nativemodule-oh-imagenative.md)* image | 指向要释放的OH_ImageNative实例的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | <ul> <br><li>CAMERA_OK: 操作成功。</li> <br><li>CAMERA_INVALID_ARGUMENT: 缺少参数或参数类型不正确。</li> <br></ul> |


