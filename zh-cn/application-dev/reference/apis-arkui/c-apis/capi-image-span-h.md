# image_span.h

## 概述

Defines a set of ImageSpan enum and interface.

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_ImageSpanAlignment](#arkui_imagespanalignment) | ArkUI_ImageSpanAlignment | 定义图片基于文本的对齐方式。 |

## 枚举类型说明

### ArkUI_ImageSpanAlignment

```c
enum ArkUI_ImageSpanAlignment
```

**描述**

定义图片基于文本的对齐方式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_IMAGE_SPAN_ALIGNMENT_BASELINE = 0 | 图片下边沿与文本BaseLine对齐。 |
| ARKUI_IMAGE_SPAN_ALIGNMENT_BOTTOM | 图片下边沿与文本下边沿对齐。 |
| ARKUI_IMAGE_SPAN_ALIGNMENT_CENTER | 图片中间与文本中间对齐。 |
| ARKUI_IMAGE_SPAN_ALIGNMENT_TOP | 图片上边沿与文本上边沿对齐。 |
| ARKUI_IMAGE_SPAN_ALIGNMENT_FOLLOW_PARAGRAPH |  |


