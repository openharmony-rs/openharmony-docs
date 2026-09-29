# OH_ArkUI_ImageAttachment

```c
typedef struct OH_ArkUI_ImageAttachment OH_ArkUI_ImageAttachment
```

## Overview

Defines an image object used to embed image content in a styled string. As a component of the styled string, the image can be attached to the styled string to implement mixed text and image layout after the image source and style attributes are set.<br> Call [OH_ArkUI_ImageAttachment_Create](capi-styled-string-h.md#oh_arkui_imageattachment_create) to create an image style object.<br> Call [OH_ArkUI_ImageAttachment_Destroy](capi-styled-string-h.md#oh_arkui_imageattachment_destroy) to destroy the image style object.<br> After the object is created, call the <b>OH_ArkUI_ImageAttachment_SetXXX</b> series APIs to set style attributes, for example, call [OH_ArkUI_ImageAttachment_SetPixelMap](capi-styled-string-h.md#oh_arkui_imageattachment_setpixelmap) to set the image source.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)

