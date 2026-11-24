# OhosImageSourceProperty

```c
struct OhosImageSourceProperty {...}
```

## Overview

Defines the property string (in key-value format) of the image source. It is used in [OH_ImageSource_GetImageProperty](capi-image-source-mdk-h.md#oh_imagesource_getimageproperty) and [OH_ImageSource_ModifyImageProperty](capi-image-source-mdk-h.md#oh_imagesource_modifyimageproperty).

<!--Device-struct OhosImageSourceProperty {...}--><!--Device-struct OhosImageSourceProperty {...}-End-->

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Related module**: [Image](capi-image-kit-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* value = nullptr | Image source property key and value string head.<br>**Since**: 10<br><!--Device-char* value = nullptr--><!--Device-char* value = nullptr-End--> |
| size_t size = 0 | Image source property key and value string size.<br>**Since**: 10<br><!--Device-size_t size = 0--><!--Device-size_t size = 0-End--> |
| char* value | Image source property key and value string head.<br>**Since**: 10<br><!--Device-char* value--><!--Device-char* value-End--> |
| size_t size | Image source property key and value string size.<br>**Since**: 10<br><!--Device-size_t size--><!--Device-size_t size-End--> |


