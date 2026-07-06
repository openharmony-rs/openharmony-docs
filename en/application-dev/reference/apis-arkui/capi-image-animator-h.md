# image_animator.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines **ImageAnimator** node types for **NativeNode** APIs.

**File to include:** <arkui/node_attributes/image_animator.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample**: <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md) | ArkUI_ImageAnimatorFrameInfo | Defines the image animation frame information.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_AnimationStatus](#arkui_animationstatus) | ArkUI_AnimationStatus | Enumerates the playback states of the frame-by-frame animation.|

### Functions

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo* OH_ArkUI_ImageAnimatorFrameInfo_CreateFromString(char* src)](#oh_arkui_imageanimatorframeinfo_createfromstring) | Creates an image frame information object based on an image path, with the image format being SVG, PNG, or JPG. Both relative and absolute paths in the application sandbox are supported.|
| [ArkUI_ImageAnimatorFrameInfo* OH_ArkUI_ImageAnimatorFrameInfo_CreateFromDrawableDescriptor(ArkUI_DrawableDescriptor* drawable)](#oh_arkui_imageanimatorframeinfo_createfromdrawabledescriptor) | Creates an image frame information object based on a **DrawableDescriptor** object, with the image format being Resource or PixelMap.|
| [void OH_ArkUI_ImageAnimatorFrameInfo_Dispose(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_dispose) | Disposes of the pointer to an image frame information object.|
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetWidth(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t width)](#oh_arkui_imageanimatorframeinfo_setwidth) | Sets the image width.|
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetWidth(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_getwidth) | Obtains the image width.|
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetHeight(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t height)](#oh_arkui_imageanimatorframeinfo_setheight) | Sets the image height.|
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetHeight(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_getheight) | Obtains the image height.|
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetTop(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t top)](#oh_arkui_imageanimatorframeinfo_settop) | Sets the vertical coordinate of an image relative to the upper left corner of the component.|
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetTop(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_gettop) | Obtains the vertical coordinate of an image relative to the upper left corner of the component.|
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetLeft(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t left)](#oh_arkui_imageanimatorframeinfo_setleft) | Sets the horizontal coordinate of an image relative to the upper left corner of the component.|
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetLeft(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_getleft) | Obtains the horizontal coordinate of an image relative to the upper left corner of the component.|
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetDuration(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t duration)](#oh_arkui_imageanimatorframeinfo_setduration) | Sets the playback duration of an image.|
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetDuration(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_getduration) | Obtains the playback duration of an image.|

## Enumeration Description

### ArkUI_AnimationStatus

```c
enum ArkUI_AnimationStatus
```

**Description**

Enumerates the playback states of the frame-by-frame animation.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_ANIMATION_STATUS_INITIAL = 0 | The animation is in the initial state.|
| ARKUI_ANIMATION_STATUS_RUNNING = 1 | The animation is being played.|
| ARKUI_ANIMATION_STATUS_PAUSED = 2 | The animation is paused.|
| ARKUI_ANIMATION_STATUS_STOPPED = 3 | The animation is stopped.|

## Function Description

### OH_ArkUI_ImageAnimatorFrameInfo_CreateFromString()

```c
ArkUI_ImageAnimatorFrameInfo* OH_ArkUI_ImageAnimatorFrameInfo_CreateFromString(char* src)
```

**Description**

Creates an image frame information object based on an image path, with the image format being SVG, PNG, or JPG. Both relative and absolute paths in the application sandbox are supported.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| char* src | Pointer to the image path, which can be a relative or absolute path in the application sandbox.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* | Pointer to the image frame information object.|

### OH_ArkUI_ImageAnimatorFrameInfo_CreateFromDrawableDescriptor()

```c
ArkUI_ImageAnimatorFrameInfo* OH_ArkUI_ImageAnimatorFrameInfo_CreateFromDrawableDescriptor(ArkUI_DrawableDescriptor* drawable)
```

**Description**

Creates an image frame information object based on an [[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md) object, with the image format being Resource or PixelMap.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawable | Pointer to an **ArkUI_DrawableDescriptor** object created using Resource or PixelMap.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* | Pointer to the image frame information object.|

### OH_ArkUI_ImageAnimatorFrameInfo_Dispose()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_Dispose(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**Description**

Disposes of the pointer to an image frame information object.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|

### OH_ArkUI_ImageAnimatorFrameInfo_SetWidth()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetWidth(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t width)
```

**Description**

Sets the image width.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|
| int32_t width | Image width, in px.|

### OH_ArkUI_ImageAnimatorFrameInfo_GetWidth()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetWidth(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**Description**

Obtains the image width.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Image width, in px. If **imageInfo** is a null pointer, **0** is returned.|

### OH_ArkUI_ImageAnimatorFrameInfo_SetHeight()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetHeight(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t height)
```

**Description**

Sets the image height.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|
| int32_t height | Image height, in px.|

### OH_ArkUI_ImageAnimatorFrameInfo_GetHeight()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetHeight(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**Description**

Obtains the image height.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Image height, in px. If **imageInfo** is a null pointer, **0** is returned.|

### OH_ArkUI_ImageAnimatorFrameInfo_SetTop()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetTop(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t top)
```

**Description**

Sets the vertical coordinate of an image relative to the upper left corner of the component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|
| int32_t top | Vertical coordinate of the image relative to the upper left corner of the component, in px.|

### OH_ArkUI_ImageAnimatorFrameInfo_GetTop()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetTop(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**Description**

Obtains the vertical coordinate of an image relative to the upper left corner of the component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Vertical coordinate of the image relative to the upper left corner of the component, in px. If **imageInfo** is a null pointer, **0** is returned.|

### OH_ArkUI_ImageAnimatorFrameInfo_SetLeft()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetLeft(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t left)
```

**Description**

Sets the horizontal coordinate of an image relative to the upper left corner of the component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|
| int32_t left | Horizontal coordinate of the image relative to the upper left corner of the component, in px.|

### OH_ArkUI_ImageAnimatorFrameInfo_GetLeft()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetLeft(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**Description**

Obtains the horizontal coordinate of an image relative to the upper left corner of the component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Horizontal coordinate of the image relative to the upper left corner of the component, in px. If **imageInfo** is a null pointer, **0** is returned.|

### OH_ArkUI_ImageAnimatorFrameInfo_SetDuration()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetDuration(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t duration)
```

**Description**

Sets the playback duration of an image.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|
| int32_t duration | Playback duration of an image, in ms.|

### OH_ArkUI_ImageAnimatorFrameInfo_GetDuration()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetDuration(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**Description**

Obtains the playback duration of an image.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Playback duration of the image, in milliseconds. If **imageInfo** is a null pointer, **0** is returned.|
