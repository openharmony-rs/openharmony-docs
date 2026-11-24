# image_effect_errors.h

## Overview

Defines the error code used in ImageEffect.

**Library**: libimage_effect.so

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Related module**: [ImageEffect](capi-image-kit-imageeffect.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ImageEffect_ErrorCode](#imageeffect_errorcode) | ImageEffect_ErrorCode | Effect error code |

## Enum type description

### ImageEffect_ErrorCode

```c
enum ImageEffect_ErrorCode
```

**Description**

Effect error code

<!--Device-enum ImageEffect_ErrorCode--><!--Device-enum ImageEffect_ErrorCode-End-->

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| EFFECT_SUCCESS = 0 | The operation completed successfully.<br><!--Device-EFFECT_SUCCESS = 0--><!--Device-EFFECT_SUCCESS = 0-End--> |
| EFFECT_ERROR_PERMISSION_DENIED = 201 | Permission denied.<br><!--Device-EFFECT_ERROR_PERMISSION_DENIED = 201--><!--Device-EFFECT_ERROR_PERMISSION_DENIED = 201-End--> |
| EFFECT_ERROR_PARAM_INVALID = 401 | Invalid parameter.<br><!--Device-EFFECT_ERROR_PARAM_INVALID = 401--><!--Device-EFFECT_ERROR_PARAM_INVALID = 401-End--> |
| EFFECT_BUFFER_SIZE_NOT_MATCH = 29000001 | Warning code if input and output buffer size is not match, it will be rendered through output buffer size.<br><!--Device-EFFECT_BUFFER_SIZE_NOT_MATCH = 29000001--><!--Device-EFFECT_BUFFER_SIZE_NOT_MATCH = 29000001-End--> |
| EFFECT_COLOR_SPACE_NOT_MATCH = 29000002 | Warning code if input and output color space is not match, it will be rendered by modifying the color space of output image.<br><!--Device-EFFECT_COLOR_SPACE_NOT_MATCH = 29000002--><!--Device-EFFECT_COLOR_SPACE_NOT_MATCH = 29000002-End--> |
| EFFECT_INPUT_OUTPUT_NOT_MATCH = 29000101 | The input and output image type is not match. For example, set input OH_Pixelmap and set output NativeBuffer.<br><!--Device-EFFECT_INPUT_OUTPUT_NOT_MATCH = 29000101--><!--Device-EFFECT_INPUT_OUTPUT_NOT_MATCH = 29000101-End--> |
| EFFECT_EFFECT_NUMBER_LIMITED = 29000102 | Over the max number of the filters that can be added.<br><!--Device-EFFECT_EFFECT_NUMBER_LIMITED = 29000102--><!--Device-EFFECT_EFFECT_NUMBER_LIMITED = 29000102-End--> |
| EFFECT_INPUT_OUTPUT_NOT_SUPPORTED = 29000103 | The input or output image type is not supported. For example, the pixel format beyond the current definition.<br><!--Device-EFFECT_INPUT_OUTPUT_NOT_SUPPORTED = 29000103--><!--Device-EFFECT_INPUT_OUTPUT_NOT_SUPPORTED = 29000103-End--> |
| EFFECT_ALLOCATE_MEMORY_FAILED = 29000104 | Allocate memory fail. For example, over sized image resource.<br><!--Device-EFFECT_ALLOCATE_MEMORY_FAILED = 29000104--><!--Device-EFFECT_ALLOCATE_MEMORY_FAILED = 29000104-End--> |
| EFFECT_PARAM_ERROR = 29000121 | Parameter error. For example, the invalid value set for filter.<br><!--Device-EFFECT_PARAM_ERROR = 29000121--><!--Device-EFFECT_PARAM_ERROR = 29000121-End--> |
| EFFECT_KEY_ERROR = 29000122 | Key error. For example, the invalid key set for filter.<br><!--Device-EFFECT_KEY_ERROR = 29000122--><!--Device-EFFECT_KEY_ERROR = 29000122-End--> |
| EFFECT_UNKNOWN = 29000199 | Unknown error.<br><!--Device-EFFECT_UNKNOWN = 29000199--><!--Device-EFFECT_UNKNOWN = 29000199-End--> |


