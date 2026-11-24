# image_effect_errors.h

## 概述

声明图片效果器错误码。

**库：** libimage_effect.so

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12

**相关模块：** [ImageEffect](capi-image-kit-imageeffect.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ImageEffect_ErrorCode](#imageeffect_errorcode) | ImageEffect_ErrorCode | 效果器错误码。 |

## 枚举类型说明

### ImageEffect_ErrorCode

```c
enum ImageEffect_ErrorCode
```

**描述：**

效果器错误码。

<!--Device-enum ImageEffect_ErrorCode--><!--Device-enum ImageEffect_ErrorCode-End-->

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| EFFECT_SUCCESS = 0 | 操作成功。<br><!--Device-EFFECT_SUCCESS = 0--><!--Device-EFFECT_SUCCESS = 0-End--> |
| EFFECT_ERROR_PERMISSION_DENIED = 201 | 权限校验失败。<br><!--Device-EFFECT_ERROR_PERMISSION_DENIED = 201--><!--Device-EFFECT_ERROR_PERMISSION_DENIED = 201-End--> |
| EFFECT_ERROR_PARAM_INVALID = 401 | 参数检查失败。<br><!--Device-EFFECT_ERROR_PARAM_INVALID = 401--><!--Device-EFFECT_ERROR_PARAM_INVALID = 401-End--> |
| EFFECT_BUFFER_SIZE_NOT_MATCH = 29000001 | 输出buffer尺寸不匹配。<br><!--Device-EFFECT_BUFFER_SIZE_NOT_MATCH = 29000001--><!--Device-EFFECT_BUFFER_SIZE_NOT_MATCH = 29000001-End--> |
| EFFECT_COLOR_SPACE_NOT_MATCH = 29000002 | 输入输出色彩空间不匹配。<br><!--Device-EFFECT_COLOR_SPACE_NOT_MATCH = 29000002--><!--Device-EFFECT_COLOR_SPACE_NOT_MATCH = 29000002-End--> |
| EFFECT_INPUT_OUTPUT_NOT_MATCH = 29000101 | 输入输出配置不一致。比如：输入Surface，输出Pixelmap。<br><!--Device-EFFECT_INPUT_OUTPUT_NOT_MATCH = 29000101--><!--Device-EFFECT_INPUT_OUTPUT_NOT_MATCH = 29000101-End--> |
| EFFECT_EFFECT_NUMBER_LIMITED = 29000102 | 超出管线最大规格。<br><!--Device-EFFECT_EFFECT_NUMBER_LIMITED = 29000102--><!--Device-EFFECT_EFFECT_NUMBER_LIMITED = 29000102-End--> |
| EFFECT_INPUT_OUTPUT_NOT_SUPPORTED = 29000103 | 输入、输出配置不支持。<br><!--Device-EFFECT_INPUT_OUTPUT_NOT_SUPPORTED = 29000103--><!--Device-EFFECT_INPUT_OUTPUT_NOT_SUPPORTED = 29000103-End--> |
| EFFECT_ALLOCATE_MEMORY_FAILED = 29000104 | 申请内存失败。<br><!--Device-EFFECT_ALLOCATE_MEMORY_FAILED = 29000104--><!--Device-EFFECT_ALLOCATE_MEMORY_FAILED = 29000104-End--> |
| EFFECT_PARAM_ERROR = 29000121 | 参数值错误。 例如：滤镜无效的参数值。<br><!--Device-EFFECT_PARAM_ERROR = 29000121--><!--Device-EFFECT_PARAM_ERROR = 29000121-End--> |
| EFFECT_KEY_ERROR = 29000122 | 参数错误。例如：滤镜无效的参数。<br><!--Device-EFFECT_KEY_ERROR = 29000122--><!--Device-EFFECT_KEY_ERROR = 29000122-End--> |
| EFFECT_UNKNOWN = 29000199 | 未定义错误。<br><!--Device-EFFECT_UNKNOWN = 29000199--><!--Device-EFFECT_UNKNOWN = 29000199-End--> |


