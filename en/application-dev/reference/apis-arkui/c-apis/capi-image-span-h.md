# image_span.h

## Overview

Defines enumerations related to **ImageSpan**, which are used to embed images in rich text and control the alignment between images and text. Multiple alignment modes are supported for mixed image-text layout scenarios, enabling precise alignment of images with text and improving the display of rich text.

**File to Include**: <arkui/image_span.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ImageSpanAlignment](#arkui_imagespanalignment) | ArkUI_ImageSpanAlignment | Enumerates image alignment modes based on text. |

## Enum type description

### ArkUI_ImageSpanAlignment

```c
enum ArkUI_ImageSpanAlignment
```

**Description**

Enumerates image alignment modes based on text.

<!--Device-enum ArkUI_ImageSpanAlignment--><!--Device-enum ArkUI_ImageSpanAlignment-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_IMAGE_SPAN_ALIGNMENT_BASELINE = 0 | The image is bottom aligned with the text baseline.<br><!--Device-ARKUI_IMAGE_SPAN_ALIGNMENT_BASELINE = 0--><!--Device-ARKUI_IMAGE_SPAN_ALIGNMENT_BASELINE = 0-End--> |
| ARKUI_IMAGE_SPAN_ALIGNMENT_BOTTOM | The image is bottom aligned with the text.<br><!--Device-ARKUI_IMAGE_SPAN_ALIGNMENT_BOTTOM--><!--Device-ARKUI_IMAGE_SPAN_ALIGNMENT_BOTTOM-End--> |
| ARKUI_IMAGE_SPAN_ALIGNMENT_CENTER | The image is centered aligned with the text.<br><!--Device-ARKUI_IMAGE_SPAN_ALIGNMENT_CENTER--><!--Device-ARKUI_IMAGE_SPAN_ALIGNMENT_CENTER-End--> |
| ARKUI_IMAGE_SPAN_ALIGNMENT_TOP | The image is top aligned with the text.<br><!--Device-ARKUI_IMAGE_SPAN_ALIGNMENT_TOP--><!--Device-ARKUI_IMAGE_SPAN_ALIGNMENT_TOP-End--> |
| ARKUI_IMAGE_SPAN_ALIGNMENT_FOLLOW_PARAGRAPH | The image alignment mode follows the text component's alignment mode.<br>**Since**: 20<br><!--Device-ARKUI_IMAGE_SPAN_ALIGNMENT_FOLLOW_PARAGRAPH--><!--Device-ARKUI_IMAGE_SPAN_ALIGNMENT_FOLLOW_PARAGRAPH-End--> |


